[GitHub Pages](https://pages.github.com/) is great for building a personal or project website. It'll default to _http://username.github.io_, or you can even [use your own custom domain name](https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages/) from services like [Namecheap](https://www.namecheap.com/), which I will write about in another post soon.

So you set up your GitHub Page for yourself or project, but what if you want to show off some of your other projects you are working on. You can go the poor man's route, and simply just copy everything from another repository into a folder in your _username.github.io_ repository, commit and push the changes to GitHub, and you'll be able to navigate to _http://username.github.io/project_.

But this comes with some seriously inconvienent and non-conventional drawbacks, such as duplication of code across repositories and manually copy/paste-ing everytime changes are made to update your hosted codebase. Good luck maintaining that.

The other, more elegant solution is to use [Git Submodules](http://www.git-scm.com/book/en/v2/Git-Tools-Submodules). These will allow us to pull in other repositories and have them sit as a "repository within a repository" [cue _Inception_ sound effect](http://inception.davepedu.com/noflash.php).

The process is as follows:

1. Via the command line, navigate to your repository
  
  `cd path/to/your/repository.github.io`

2. Add a submodule
  
  `git submodule add https://github.com/username/otherrepository`
    
    note: It must be the `https://` address

3. Add/commit your new files
  
  `git add .gitmodules`
  
  `git add otherrepository/`
  
  `git commit -m "Added otherrepository submodule"`

4. Push your changes
  
  `git push origin master`

5. navigate to _http://username.github.io/otherrepository_

Now if you start making changes to your other repository, you'll need to update your GitHub Pages repository to reflect those changes:

1. Via the command line, navigate to your GitHub Pages repository
  
  `cd path/to/your/repository.github.io`

2. Navigate into your submodule
  
  `cd otherrepository/`

3. Pull from you master

  `git pull origin master`
  
4. Navigate back up to your GitHub Pages repository

  `cd ..`

5. Add/commit your updated files
  
  `git add .gitmodules`
  
  `git add otherrepository/`
  
  `git commit -m "Updated otherrepository submodule"`

6. Push your changes
  
  `git push origin master`

And now your changes should be reflected online.
