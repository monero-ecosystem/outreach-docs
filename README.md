# monero-meetup-kit

This repository contains the files of the Monero Meetup Kit that need to be translated

## What to translate

Some documents in this repository need to be localized in as many languages as possible. Right now the priority is the Flyer. You can find it in this repository in three different versions. Please make sure that the version in this repository is the same as the one [on Taiga](https://taiga.getmonero.org/project/sgp-monero-meetup-kit/wiki/flyers) (You will always find the last version on Taiga)

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

**important:** Remember, this repository is linked to Taiga (and only this repository, for now), you need to add a little string at the end of your commit to make GitHub and Taiga communicate. For example, if the number of the issue on Taiga is 420, the end of your commit would be something like `text of the commit TG-420 #ready-for-test`. This will tell Taiga to move the story/task 420 from the previous status to `ready-for-test`, this means you are done and only waiting for reviews (more examples at the bottom of this document).

5. When done, upload your translation in the correct folder (e.g. if it's a spanish translation, it will go under /es/ , if the subfolder doesn't exist, make one. Your translation file will result, for example:
`/translations/es/moneromeetup_kitflyer_v*.pdf`)
6. push your changes to your remote repository and/or open a Pull Request

## Workflow and Examples
We use 4 statuses for our tasks:
- *new* - For new tasks (you don't need to use this)
- *in-progress* - This is the one you should use when opening a task if you are still working on it
- *ready-for-test* - When you are done and only need reviews 
- *closed* - This will be used by who will merge your Pull Request


All this is much easier than it might seem, check the following example:

- I want to add a Japanese version of the flyer and nobody is working on it right now 
- I don't want a Taiga account, so I open an issue asking to open a new task, who will be named something like 'Japanese translation of the flyer'
- I get the number of my task: #5
- now I have to put the reference to the taiga issue in, at least, one commit. My review has a couple of commits, so the last one will be `"fix typos and grammar TG-5 #ready-for-test"`
- I push my commits and open a Pull Request

Let's make another example:

- let's pretend [the task 44](https://taiga.getmonero.org/project/erciccione-monero-localization/us/13?milestone=19), 'French translation of the Flyer', has the status "new", because somebody just opened it for us.
- we have a lot of fixes to make, hopefully with some help, so this is going to be a WIP (work in progress).
- I start editing the file and my first commit will be named "starting cleaning all obsolete lines TG-44 #in-progress".
- The task's status now is "Work in progress"
- after some time the work is done, in my last commit I add at the end `TG-44 #ready-for-test"`
- now it is ready to be reviewed

*note:* for now, only this repository is integrated with Taiga, for all the other translations, just use GitHub or contact us.

For support and suggestions: Open an issue in this repository, come chat on`#monero-translations` on Freenode, or message us on [Taiga](https://taiga.getmonero.org/project/erciccione-monero-localization/)
