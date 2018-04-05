# monero-meetup-kit

This repository contains the files of the Monero Meetup Kit that need to be translated in as many languages as possible. Right now the priority is the Flyer.

## How

This repository is synchronized with [the Taiga instance](https://taiga.getmonero.org/project/erciccione-monero-localization) of the localization team, all issues opened here will be opened on there as well. For an optimal use and coordination, a task should be opened on Taiga before committing to the repository (this is because GitHub can only modify tasks not create one). You have three ways to do this:
- Join us on Taiga, so you can open a new issue by yourself, you only need to give us an email address (contact the project on Taiga)
- Open an issue in this repository specifying what you're going to do (eg. "updating Italian translation of the flyer"). A task will be added and the number of this will be communicated to you (we'll see why later)
- contact /u/ErCiccione on reddit or on Freenode (#monero-translations)

### Translating the Flyer

1. Fork this repository, so you have your own version on GitHub, then clone your fork locally using `git clone --recursive https://github.com/erciccione/monero-meetup-kit-localization.git`
2. Add a subfolder for your language ([check existing folders](https://github.com/erciccione/monero-meetup-kit/tree/master/translations))
3. [download Scribus](https://www.scribus.net/downloads/stable-branch/), an open source tool for document publishing.
4. After you installed Scribus, go in the folder `flyer-scribus-files` and double click on the file `flyer.sla`. A window will pop up, asking to replace the missing `arial regular` font. Substitute this one with `Open Sans Regular` and click ok.
5. Replace the english strings with the ones in your languages
6. When your file is ready, we need to compile it to transform it into a PDF. To do so click on the `File` Menu -> `Export` -> `Save as PDF` -> `Save`
7. Done! now move the resulting pdf inside the folder you created on step 2, push your changes to your remote repository and open a pull request (pointing to master)


## Workflow and Examples

- I want to add a Japanese version of the flyer and nobody is working on it right now 
- I don't want a Taiga account, so I open an issue asking to open a new task
- I push my commits and open a Pull Request
- Once the PR has been reviewed, the maintainer will merge it to the code,.


For support and suggestions: Open an issue in this repository, come chat on`#monero-translations` on Freenode, or message us on [Taiga](https://taiga.getmonero.org/project/erciccione-monero-localization/)
