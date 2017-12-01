# monero-meetup-kit

This repository contains the files of the Monero Meetup Kit that need to be translated

## What to translate

Some documents in this repository need to be localized in as many languages as possible. Right now the priority is the Flyer. You can find it in this repository in three different versions. Please make sure tyour version is the same as the one [on Taiga](https://taiga.getmonero.org/project/sgp-monero-meetup-kit/wiki/flyers) (You will always find the last version on Taiga)

## How

This repository is synchronized with [the Taiga instance](https://taiga.getmonero.org/project/erciccione-monero-localization) of the localization team, all issues opened here will be opened on there as well. For an optimal use and coordination, a task should be opened on Taiga before committing to the repository (this is because GitHub can only modify tasks not create one). You have three ways to do this:
- Join us on Taiga, so you can open a new issue by yourself, you only need to give us an email address (contact the project on Taiga)
- Open an issue in this repository specifying what you're going to do (eg. "updating Italian translation of the flyer"). A task will be added and the number of this will be communicated to you (we'll see why later)
- contact /u/ErCiccione on reddit or on Freenode (#monero-translations)

1. Clone the repository
2. Add a subfolder for your language ([check existing folders](https://github.com/erciccione/monero-meetup-kit/tree/master/translations))
3. Get a copy of the file you want to translate.
If you want to translate the flyer, you can choose between 3 files:
- `moneromeetup_kitflyer_v*.pdf` - The full flyer 
- `moneromeetup_kitflyer_v*_nomarks.pdf` - no marks
- `translate_v40.rtf` - Only text
(`*` is the last version)
4. Translate

**important:** Remember, this repository is linked to Taiga (and only this repository, for now). Please add a little string at the end of your commit referring to the Taiga Issue. For example, if the number of the issue on Taiga is 420, the end of your commit should be something like `text of the commit TG-420`. If you want to communicate the status of your work (to make reviews and contributions easier), you can use Taiga statuses (new, in-progress, ready-for-test, closed. All explained below), e.g. `text of the commit TG-420 #ready-for-test`.    
*Note:* Changes on GitHub are pushed to Taiga only once they get merged to the code, this means Taiga will get automatically synchronized **only** when the maintainer merge the commits to the repository. The synchronization Taiga-GitHub can be done manually by the contributor or the maintainer. The only automatic one happens when the Pull Request get merged (so, when the maintainer apply the status on the merge commit)

5. When done, upload your translation in the correct folder (e.g. if it's a Spanish translation, it will go under /es/ , if the subfolder doesn't exist, make one. Your translation file will result, for example:
`/translations/es/moneromeetup_kitflyer_v*.pdf`)
6. push your changes to your remote repository and/or open a Pull Request

## Workflow and Examples
We use 4 statuses for our tasks:
- *new* - For new tasks (you don't need to use this)
- *in-progress* - you don't need to use this on GitHub
- *ready-for-test* - When you are done and only need reviews 
- *closed* - This will be used by who will merge your Pull Request


All this is much easier than it might seem, check the following example:

- I want to add a Japanese version of the flyer and nobody is working on it right now 
- I don't want a Taiga account, so I open an issue asking to open a new task, who will be named something like 'Japanese translation of the flyer'
- I get the number of my task: #5
- now I have to put the reference to the taiga issue in, at least, one commit. My review has a couple of commits, so the last one will be `fix typos and grammar TG-5 #ready-for-test`
- I push my commits and open a Pull Request
- Once the PR has been reviewed, the maintainer will merge it to the code, applying a status to the merge commit.    
eg. `fix typos and grammar TG-5 #closed`. This will tell Taiga to automatically close the task.

*note:* for now, only this repository is integrated with Taiga, for all the other translations, just use GitHub or contact us.

For support and suggestions: Open an issue in this repository, come chat on`#monero-translations` on Freenode, or message us on [Taiga](https://taiga.getmonero.org/project/erciccione-monero-localization/)
