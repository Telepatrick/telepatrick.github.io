GitHub Pages is great for building a personal or project website. It'll default to http://username.github.io, or you can even use your own custom domain name from services like Namecheap, which I will write about in another post soon.

So you set up your GitHub Page for yourself or project, but what if you want to show off some of your other projects you are working on. You can go the poor man's route, and simply just copy everything from another repository into a folder in your username.github.io repository, commit and push the changes to GitHub, and you'll be able to navigate to http://username.github.io/project.

But this comes with some seriously inconvienent and non-conventional drawbacks, such as duplication of code across repositories and manually copy/paste-ing everytime changes are made to update your hosted codebase. Good luck maintaining that.

The other, more elegant solution is to use Git Submodules. These will allow us to pull in other repositories and have them sit as a "repository within a repository" cue Inception sound effect.

The process is as follows:

Via the command line, navigate to your repository
cd path/to/your/repository.github.io

Add a submodule
git submodule add https://github.com/username/otherrepository

note: It must be the `https://` address
Add/commit your new files
git add .gitmodules

git add otherrepository/

git commit -m "Added otherrepository submodule"

Push your changes
git push origin master

navigate to http://username.github.io/otherrepository
Now if you start making changes to your other repository, you'll need to update your GitHub Pages repository to reflect those changes:

Via the command line, navigate to your GitHub Pages repository
cd path/to/your/repository.github.io

Navigate into your submodule
cd otherrepository/

Pull from you master
git pull origin master

Navigate back up to your GitHub Pages repository
cd ..

Add/commit your updated files
git add .gitmodules

git add otherrepository/

git commit -m "Updated otherrepository submodule"

Push your changes
git push origin master

And now your changes should be reflected online.
