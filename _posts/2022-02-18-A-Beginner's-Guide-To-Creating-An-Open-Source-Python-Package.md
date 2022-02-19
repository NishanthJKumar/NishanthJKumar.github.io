A while ago, I had the opportunity to develop and release a new open-source Python library: [PGMax](https://github.com/vicariousinc/PGMax). Since this was to be my first open-source library release, I spent a lot of time figuring out a good set of developer tools to speed up development and enable (hopefully) lots of people to use and contribute to the project in the future. While there are already [so](https://towardsdatascience.com/build-your-first-open-source-python-project-53471c9942a7) [many](https://d39l7znklsxxzt.cloudfront.net/zh/blog/2021/01/19/publishing-a-proprietary-python-package-on-pypi-using-poetry/) [different](https://www.martinmcbride.org/post/2021/creating-python-oss-project/) [articles](https://medium.com/free-code-camp/from-a-python-project-to-an-open-source-package-an-a-to-z-guide-c34cb7139a22), blog posts and resources on setting up open-source Python packages, none of them really presented a good integrated suite of tools for the various pieces (dependency management, documentation generation, continuous integration, etc.) that a well-engineered open-source project might want. So, I thought I would describe PGMax's setup in the hopes that it might help others interested in setting up their own open-source library.

Before I dive into describing all the packages and tools I used, I want to mention 2 things:
1. This article assumes you're planning to use GitHub to host your project's repository. A lot of the tools used should integrate well with some other version control setup, but might not because it wasn't written with any other setup in mind.
1. There are a *lot* of different tools and libraries covered in this post, and quite a few of them might be overkill for your needs. Feel free to pick and choose specific pieces based on your use-case!

Alright, let's get started!

---

## Dependency Management and Packaging with poetry
Almost every useful Python package relies on a plethora of other, existing Python packages. While there are many popular tools like [pip](https://pypi.org/project/pip/) and [conda](https://docs.conda.io/en/latest/) that help manage and maintain all the various packages and dependencies you might need to prevent the dreaded `ImportError`, most of these are intended for personal use and don't seamlessly support all the needs that arise when building an open-source package that will (hopefully) be used and contributed to by hundreds of people. This is where [poetry](https://python-poetry.org/) comes in.

Poetry is an easy-to-install tool that seamlessly handles pretty much all the use-cases you might have with developing an open-source package. It also has an intuitive CLI and some nice bells and whistles (one of my favorite: you can specify separate dependencies for developers and users and use these to make separate `virtualenvs`!). Head over to [this page](https://python-poetry.org/docs/#installation) and follow the instructions to install and setup poetry. Then, look under the "Project Setup" heading at [this page](https://python-poetry.org/docs/basic-usage/) to generate a `pyproject.toml` file which poetry treats as a one-stop-shop to manage your project. You can read [this page](https://python-poetry.org/docs/basic-usage/) to understand all the basic usecases, and [this page](https://python-poetry.org/docs/cli/) to see everything you can do with the CLI, but the general idea of how to use poetry is as follows:
- Activate your poetry environment for development with `poetry shell`
- Whenever you want to add a new dependency/import a new library as part of development, do `poetry add -D <library-name>`. If this will be needed for project users (not just developers) as well, simply do `poetry add <library-name>` (you can also optionally specify particular versions of requirements, and even the source from which to get a specific library).
- If someone else wants to start developing and contributing to your project, they can simply download the project repository and run `poetry shell` followed by `poetry install`, and they should have a nice, clean `virtualenv` with everything needed to run and develop the code (ta-da!).
    - If someone just wants to use your package and isn't interested in developing, they can run `poetry shell` followed by `poetry install --no-dev`.

### Publishing your poetry package to PyPI
One of Poetry's nicest features is its ability to easily publish packages to [PyPI](https://pypi.org/) so users can install the package painlessly with a simple `pip install <package_name>`. Before actually publishing your package though, it's probably a good idea to test that it builds correctly and will upload to PyPI seamlessly. 

#### Testing your package build and upload with Test PyPI
1. If you haven't already, add some miscellaneous, relevant fields to your `pyproject.toml` file. Such nice-to-have fields might include a license, a list of package authors and maintainers, a link to a homepage website, etc. You can see the full list of possible fields [here](https://python-poetry.org/docs/pyproject/); and as a sample, PGMax's `pyproject.toml` file can be found [here](https://github.com/vicariousinc/PGMax/blob/master/pyproject.toml).
1. Also, if you haven't already, make an account on [Test PyPI](https://test.pypi.org/). Note that this will be entirely separate from any PyPI account you may have registered for with the same username.
1. Go ahead and build your package with the command: `poetry build`. This should create a `dist` folder with a `.whl` and `.tar.gz` file. Note that it's probably a good idea to add this `dist` folder to your `.gitignore`.
1. Try to install this `.whl` file in a fresh environment (e.g. [create a new Conda environment](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) or [venv](https://docs.python.org/3/library/venv.html)) with the command: `pip install dist/<name_of_.whl_file>`. If there are any dependency/other issues with this install, fix them now.
    1. If your package has any tests/example code, try to run these to verify that the install really worked.
1. Add Test PyPI as an alternate package repository to publish to: `poetry config repositories.testpypi https://test.pypi.org/legacy/`
1. Now, publish your package to Test PyPI: `poetry publish -r testpypi`. You will need your account credentials for this. If there are any dependency errors, etc. with this resolve them now.
1. To verify that the upload looks good and works as intended, you can view it on [Test PyPI](https://test.pypi.org/) and then additionally try to install it in a fresh environment with the command: `pip install --index-url https://test.pypi.org/simple/ --extra-index-url https://pypi.org/simple <your_package_name>` (see [this StackOverflow answer](https://stackoverflow.com/questions/34514703/pip-install-from-pypi-works-but-from-testpypi-fails-cannot-find-requirements) if you're curious about what this command does.)
    1. Again, run any test/example code to verify that this install is all good.

If this works, then congrats! You're now ready to upload your package to PyPI and can be assured that everything will work seamlessly!

#### Uploading your package to PyPI
1. If you haven't already, then [register for a PyPI account](https://pypi.org/account/register/). Note that this is entirely separate from any account you may have on Test PyPI.
1. Publish your package with a simple `poetry publish` command. You will need your PyPI account credentials.

Ta-da! Now you have a shiny new package on PyPI, ready for anyone to install with a simple `pip install <package-name>` command!


## Code Formatting, Linting and other nice-to-haves
While these things are relatively minor, they can save you (and people who want to use your project) from significant headaches in the future. Since these things are straightforward to setup and become increasingly important as your project grows, I recommend setting them up right at the outset. Specifically, I recommend using:
- [black](https://black.readthedocs.io/en/stable/) for code formatting
- [isort](https://pycqa.github.io/isort/) to sort imports and make sure they're always in the same order (this is extremely useful when reviewing changes on GitHub)
- [flake8](https://flake8.pycqa.org/en/latest/) for linting
- [mypy](https://mypy.readthedocs.io/en/stable/) for type-checking all your code. This might be somewhat annoying during development, but is useful to keep-around because it can help catch some extremely subtle type bugs (plus, you can make it ignore files/functions/lines you don't want it to look at).


### Enforcing Code Formatting with pre-commit hooks
Now, it can be somewhat painful to install and use all these formatting and type-checking tools together. Fortunately, the [pre-commit](https://pre-commit.com/) tool can bundle and run all of these tools (and more) for you! What's more, you can set this up to run whenever a `git commit` command is executed. To do this, simply:
1. Install pre-commit by following [these instructions](https://pre-commit.com/#installation)
    1. If you're using poetry (which I hope you are!) be sure to add `pre-commit` as a developer dependency and do this installation (preferably via pip) *within* your poetry shell. You can accomplish all of this by running `poetry add -D pre-commit` after having activated your poetry env with `poetry shell`.
    1. Verify your installation by checking whether the `pre-commit --version` command runs 
1. Add a `.pre-commit-config.yaml` file to specify the tools you want `pre-commit` to run
    1. You can have the terminal spit out a sample `.pre-commit-config.yaml` using the command `pre-commit sample-config`. Copy pase the output of this command into `.pre-commit-config.yaml`
    1. If you want you'd like to use all the nice tools specified above (black, isort, flake8 and mypy), copy paste the below into your `.pre-commit-config.yaml` file

        ```
        repos:
        -   repo: https://github.com/PyCQA/isort
            rev: 5.8.0
            hooks:
            -   id: isort

        -   repo: https://github.com/ambv/black
            rev:  21.6b0
            hooks:
            -   id: black
                language_version: python3.7

        -   repo: https://github.com/pre-commit/pre-commit-hooks
            rev: v4.0.1
            hooks:
            -   id: check-added-large-files
                args: ['--maxkb=5120']
            -   id: trailing-whitespace
                files: (\.py|\.rst|\.yaml|)$
            -   id: check-merge-conflict

        -   repo: https://gitlab.com/pycqa/flake8
            rev: 3.9.2
            hooks:
            -   id: flake8
                # To turn this into an error, remove --exit-zero below
                args: ['--config', '.flake8.config','--exit-zero']
                verbose: true

        -   repo: https://github.com/pre-commit/mirrors-mypy
            rev: 'v0.902'  # Use the sha / tag you want to point at
            hooks:
            -   id: mypy
                additional_dependencies: [tokenize-rt==3.2.0]
        ```
        
    1. Setup `pre-commit` to run whenever you commit to GitHub by running the `pre-commit install` command
        1. If you're using poetry, be sure to run this command within your poetry shell. Alternatively, you can run `poetry run pre-commit install`.
    1. (Optional) Integrate `pre-commit` with your IDE so you can run these checks for any file on save, etc. ([VSCode extension](https://marketplace.visualstudio.com/items?itemName=MarkLarah.pre-commit-vscode), [IntelliJ Plugin](https://plugins.jetbrains.com/plugin/9278-pre-commit-hook-plugin))
        1. You can also just run the command `pre-commit run --files <path-to-your-files>` to selectively run these tools on specific files. If you're like me and don't enjoy typing all this out, you can make a bash alias by adding the below lines to the end of your `~/.bashrc` file.

            ```
            pc ()
            {
                pre-commit run --files "$1"
            }
            ```
            Now, you can simply run `pc <path-to-yourfile>`.


## Managing Jupyter Notebooks with jupytext
Jupyter Notebooks are better than plain old Python scripts for a variety of different purposes. Unfortunately, version control isn't one of them. Keeping Jupyter Notebooks as part of your project can make code review and management an absolute nightmare. Fortunately, there is a solution: [Jupytext](https://github.com/mwouts/jupytext).

Jupytext essentially creates a text version of your notebook and updates this version whenever you update the notebook (or vice-versa, so you can edit your notebook just by editing the jupytext-produced text file!). This way, you can just commit these text files (that are amenable to version control) to your repo and then generate + edit the corresponding Jupyter notebooks if and when they're needed. Here's how to integrate Jupytext into your repo:

1. Add `*.ipynb` to your `.gitignore` file within your GitHub repo
1. Install Jupytext by following the instructions from [here](https://github.com/mwouts/jupytext#install)
    1. If you're using poetry (which I hope you are!) be sure to add jupytext as a developer dependency and do this installation (preferably via pip) *within* your poetry shell!
1. Pair all your notebooks with a file in text format by following the instructions [here](https://github.com/mwouts/jupytext#paired-notebooks).

And that's it! Be sure to commit the paired text files to GitHub's version control.


## Testing with pytest
Having a good test suite is absolutely essential for any open-source library that expects to be widely adopted and improve with time. As of this writing, pytest is arguably the most popular choice for a python testing library because of its ease-of-use coupled with exhaustive features.

Installing and setting up PyTest is super easy: simmply follow the [steps from the official documentation](https://docs.pytest.org/en/6.2.x/getting-started.html#install-pytest). If you're using Poetry (which I hope you are!), make pytest a dependency of your project and install it within your poetry environment by running `poetry add pytest` within your poetry shell.

You're now ready to begin writing tests! To get started, follow the [guide from the official documentation](https://docs.pytest.org/en/6.2.x/getting-started.html#install-pytest).

As you're thinking about how to structure and organize your tests, I'd highly recommend checking out [this set of best practices](https://docs.pytest.org/en/6.2.x/goodpractices.html). Ensuring that your tests follow as many of these pointers as is reasonable will save you a *lot* of headache down the line.


## Generating documentation with Sphinx
If you've ever experienced the abject horror of having to make changes to a sprawling codebase with no comments or documentation *after* when everyone that's worked on it is unavailable, you understand why documentation is important. Now of course, there's a reason most people don't like writing documentation: it's an annoying overhead (especially when you're just starting to work on your project). Fortunately, there are tools to make writing and maintaining documentation significantly *less* annoying (and even quite a delight). Enter Sphinx.

[Sphinx](https://www.sphinx-doc.org/en/master/index.html) helps you turn documentation files into a beautiful website that makes it easy for users to navigate through your (potentially massive and sprawling) codebase and understand how different pieces work. What's more, [Read the Docs](https://docs.readthedocs.io/en/stable/index.html) hosts this website (generally for FREE!) and can be configured to update it whenever you push changes to your repo on GitHub. This way, your documentation is always up-to-date, and accessible to anyone on the Internet (which makes it *much* more likely that people will want to use and help improve your library!).

Unfortunately, as of this writing, Sphinx can be a bit annoying and tricky to setup well, especially if you'd like to do non-default things to make your documentation look better. There are *a lot* of different ways to configure Sphinx to build a great-looking website; I'll describe the one I settled on for PGMax, which was inspired by the structure and setup of the [JAX documentation](https://jax.readthedocs.io/en/latest/). In particular, this setup generates a separate page in the documentation for every function, class and exception in your codebase (which looks much nicer than cramming everything into a few pages).

### Writing DocStrings
For Sphinx to actually do it's magic, your code needs to have 'docstrings'. If you haven't heard of these before, the name is fairly self-explanatory: they're strings placed throughout the codebase that document everything from a general description of each class to the input/output of a specific function. Docstrings have a specific structure and style to make them easily parseable, and there are 2 major styles to choose from: [the Google Style](https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html) and [the NumPy Style](https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_numpy.html#example-numpy). PGMax chose to go the Google route, but there's no significant reason to choose one over the other. Whatever you do choose, make sure to write docstrings for all applicable parts of your code!

### Configuring Sphinx
To get started, follow [these instructions](https://docs.readthedocs.io/en/stable/intro/getting-started-with-sphinx.html#quick-start) to install Sphinx and walk through a setup process to create a documentation folder for you project. PGMax uses the [readthedocs theme](https://sphinx-rtd-theme.readthedocs.io/en/stable/installing.html) to format documentation, so I'd certainly recommend installing this as well. Once you've completed this, follow [this StackOverflow answer](https://stackoverflow.com/a/62613202/12014259) to setup your repo to use the `autosummary` directive correctly (which generates separate pages for each module in your documentation). Feel free to look at [PGMax's documentation folder](https://github.com/vicariousinc/PGMax/tree/master/docs) for reference. If all is now setup correctly, then if you navigate to your project's documentation folder and run `make html` command, you should see a `build` directory get created containing html pages with your documentation. If you open these pages with your browser, you should be able to view what your documentation pages look like! Be sure to click through most if not all of you pages to make sure everything has been generated correctly.

### Setting up Read the Docs with GitHub Integration
Now that you have Sphinx building your documentation correctly locally, you can make your own website on [readthedocs.io](https://readthedocs.org/) to host and continuously update your documentation so any users can easily access it. To do this, simply follow [these instructions](https://docs.readthedocs.io/en/stable/tutorial/index.html#sign-up-for-read-the-docs) (though adapted to your project instead of their tutorial example). Importantly, this integration should automatically update the documentation upon new pull-requests, so all you need to do whenever you update code and documentation is simply make a PR!


## Automating things with Continuous Integration via GitHub Actions
If you've setup everything up till this point, then you should have a nice development environment and workflow ready-to-go. This is great, but there's one subtle problem: what if you (or someone contributing to your open-source project) mess up? Suppose for example that you forget to run your pre-commit hooks before pushing to GitHub, or even worse, you forget to run all your tests with PyTest before a major change. There's currently nothing that prevents you from doing any of these things, and while some of them (like forgetting to lint) might not matter as much, other slip-ups (like forgetting to test and thereby accidentally breaking things) could be extremely annoying and even costly to fix. Enter GitHub Actions.

[GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/introduction-to-github-actions) essentially allow you to do various things (run tests, lint, publish the package, etc.) upon "triggers" like committing, pushing or opening a Pull Request (PR) on GitHub. There are *a lot* of [useful, interesting and awesome GitHub Actions](https://github.com/sdras/awesome-actions) out there, but I'm going to try to keep things simple and focus on the ones that dovetail well with the tools described above. Specifically, whenever someone pushes a commit, an action should enforce all our pre-commit hooks on any changed code. And whenever someone opens a PR, various actions should:
- Enforce all pre-commit hooks
- Try to install all the Poetry dependencies and make sure it works
- Run all tests with PyTest
- Test that all documentation can be generated, then publish this documentation after PR approval

Additionally, after a new "release" of the repo is made, we want to automatically publish this new version to PyPi.

PGMax uses two different files within its `.github/workflows` folder: [ci.yaml](https://github.com/vicariousinc/PGMax/blob/master/.github/workflows/ci.yaml) and [publish.yaml](https://github.com/vicariousinc/PGMax/blob/master/.github/workflows/publish.yaml). Our `ci.yaml` file specifies all the actions that are run on push and pull-request events, whereas the `publish.yaml` file specifies actions to be run when a new release is made. Both files are fairly simple and reading their comments along with some of the [official GitHub Actions docs](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions) should be sufficient to enable you to understand what each part of each file does (if that's not the case, feel free to post a comment or shoot me a message and I'm happy to help clarify things!). The only piece of setup that's needed to get these actions to run in any other repo is the creation of a [GitHub Secret](https://docs.github.com/en/actions/reference/encrypted-secrets) that enables GitHub to access my PyPI account when it needs to publish a new release of the package. To do this, simply [create an API token](https://pypi.org/help/#apitoken) on PyPI and then [crete a new GitHub Secret](https://docs.github.com/en/actions/reference/encrypted-secrets#creating-encrypted-secrets-for-a-repository) named `PYPI_TOKEN` and paste your PyPI API token as the "value" of the secret.

Feel free to directly use PGMax's YAML files for your own GitHub actions, or pick and choose specific sections adapted to your project's needs!

Pro Tip: To make your GitHub repo look super professional, you can add a shiny badge to your README to display the status of your tests, documentation builds, etc. To do this, follow [these steps](https://docs.github.com/en/actions/managing-workflow-runs/adding-a-workflow-status-badge).

---

That's all folks! I hope these tips and links are helpful, and that you don't have to spend as much time as I did on figuring out how to setup your shiny new open-source Python library. If you do end up using this guide for your open-source library, do let me know; I'm excited to see what you build!