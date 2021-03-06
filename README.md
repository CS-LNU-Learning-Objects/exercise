# Exercises

This is the repo for the Javascript exercises in the course. The virtual machine (hashicorp/precise32) will have the following (relevant) packages installed:

From start:
* node.js (Latest stable)
* npm
* git
* browserify (watchify)
* http-server
* nodemon
* phantomjs (testing)
* casperjs (testing)
* mocha (testing)

Some quirks to make the machine work out of the box in Windows.

Exercises are constantly updated and added. You will find those as branches in this repo. 

## Install
Make sure you have the following installed on your system:
* Virtual Box [https://www.virtualbox.org/](https://www.virtualbox.org/)
* Vagrant [https://www.vagrantup.com/](https://www.vagrantup.com/)

Now, do:
1. Clone your exercise repo on the course organization. (`git clone https://github.com/[COURSE-CODE]/[STUDENT-ID]-exercises`)

2. Enter the repo (`cd [STUDENT-ID]-exercises`)
3. Make a remote pointing to the exercises (`git remote add exercises https://github.com/CS-LNU-Learning-Objects/client-side-javascript-exercise`)
4. Pull (`git pull exercises`) into your existing excersise repo. Make sure you are in the root of your repo. (This will fetch all exercise branches)
5. Merge the exercise-repost master branch into your master branch. `git merge exercises/master --allow-unrelated-histories`

6. Start a new terminal window (you need two open, one for git and one for vagrant)

7. Navigate to the the repo (`cd [STUDENT-ID]-exercises`)

8. Start the virtual machine using `vagrant up` (May take 10-30 minutes this first time. Ignore red command line statements and warnings.)

9. `vagrant ssh` to connect to the machine.

## In the first terminal window (git)
1. checkout the exercise bransh you want to work with. (Ex: `git checkout lnu-it`)

## In the vagrant terminal (after `vagrant ssh`)
1. Make sure you are located in the folder `/vagrant/exercise/` at all times.
2. Do `npm run debug`. The following will happen:
  * A process will start watching files in the folder `source/` for changes. When a change is detected the file will be copied to the debug-folder as follows:
    * `source/image/` -> `debug/image` .jpeg, .jpg, .png, .gif, .svg are copied
    * `source/js/app.js` -> `debug/javascript/build.js` app.js and it dependencies are browserified to build.js
    * `source/*.html` -> `debug/*.html` .html-files are copied
    * `source/css/*.css` -> `debug/*.css` .css-files are copied
  * A webserver is started and if you browse to `http://localhost:3000` you will see the html-page `debug/index.html`.

## In the Git-bash or terminal on your local computer
You should have multiple terminals open at the same time. One running the `npm run debug`  in the vagrant-terminal, and one terminal not ssh:ed to vagrant. In the terminal on your local machine you could to tasks like committing and pushing to GitHub.

## Local IDE
1. Start up your IDE (WebStorm) and open a new project pointing to the folder "exercise"
2. Start editing your site in the `source`-folder. **(NEVER EDIT FILES IN THE DEBUG FOLDER.)** When you save a change look at the "vagrant terminal". You should see that the files are rebuilt.
3. Refresh the webpage `localhost:3000` and this should reflect your changes.
4. When you debug your application you should to this in the browser, not in the IDE. A simple method is to write `debugger;` in your js-source code where you want to stop the debugger and refresh the browser.
