#Adding local repo to github

* go to github profile and create/copy personal token My Account → Settings → Developer settings → Personal access tokens → Generate new token.
* follow steps and copy the token (IT WILL ONLY APPEAR THERE make sure to copy)

* Create new repo without initializing
* copy repo address
* Go to local project root
* `git init`
* `git add .`
* `git commit -m "1st commit"`
* `git remote add origin [repo url]`
* `git remote -v`
* `git push origin master`

>>> Enter username when prompted
>>> Paste personal token obtained on the previous step
