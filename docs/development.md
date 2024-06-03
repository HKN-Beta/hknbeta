# Edit documentation

This documentation is written in Markdown, a simple markup language that is easy to read and write.  If you're not familiar with Markdown, you can find a guide [here](https://www.markdownguide.org/).

## Set up your environment

First, ensure that you have access to edit the `hknbeta` repository on GitHub.  If you don't have access, ask the current facilities/IT director to add you as a collaborator.

Clone the `hknbeta` repository to your local machine.  You can do this by running the following command in your terminal.  Use the SSH URL to make it easier on yourself to push changes.

```bash
git clone git@github.com:HKN-Beta/hknbeta
```

### Install `mkdocs` packages **(Optional for small changes)**

Install the `mkdocs` and `mkdocs-material` packages so that you can preview your changes locally.  You can do this by running the following command in your terminal.

```bash 
pip install mkdocs mkdocs-material
```

If you're on certain distributions of Linux that do not permit installing packages system-wide, you may need to first initialize a virtual environment.  You can do this by running the following command in your terminal.

```bash
python3 -m venv venv
source venv/bin/activate
# then install the packages
pip install mkdocs mkdocs-material
```

### Make your changes

Navigate to the `docs` directory in the `hknbeta` repository.  You can make changes to any of the Markdown files in this directory.  You can also add new files if you need to, including images or GIFs to embed into your Markdown.

### Preview your changes **(Optional for small changes)**

If you installed `mkdocs` and `mkdocs-material`, you can preview your changes by running the following command in your terminal.

```bash
mkdocs serve
```

This will start a local server that you can access by navigating to the URL that gets printed out.

### Push your changes

Once you're satisfied with your changes, you can push them to the `hknbeta` repository.  You can do this by running the following commands in your terminal.

```bash
git add .
git commit -m "A descriptive commit message here"
git push
```

### View your changes on the updated page

Once you've pushed your changes, you can navigate to the [HKN Beta website](https://hkn-beta.github.io/hknbeta/) to see your changes live.  If you don't see your changes, try refreshing the page.