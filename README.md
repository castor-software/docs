# CASTOR Mirroring service

The castor-software organization hosts a number of repository mirrors that are relevant for CASTOR, yet mainly hosted within other organizations.
Here we discuss the steps you need to follow in order to mirror an existing repo.

## Steps to create a mirror

To create a castor mirror of your repository `your-organization/your-repo`

 * Fork your github repo as `castor-software`. That should create the repo `castor-software/your-repo`.
 * Change the name of `castor-software/your-repo` to `castor-software/your-repo-mirror`, to avoid confusion. And add "Mirror of `https://github.com/your-organization/your-repo` to the description.
 * grant write access in this new repo to @castor-bot
 * add to [mirror-list.json](mirror-list.json) an entry like:
```json
{"src": "your-organization/your-repo", "mirrors": ["castor-software/your-repo"]}
```
This file will be use to periodically update your mirror with commit pushed on `your-organization/your-repo`.

Note that if the mirror is not hosted on `castor-software`, it won't be updated if `castor-software` does not have the write access on the mirror.

## Execution

The mirroring task is executed on tray.csc.kth.se, by Cron, every day at midnight. It pushes the commits with the SSH key of user @castor-bot.

## Authors

Nicolas Harrand @nharrand
Martin Monperrus @monperrus


