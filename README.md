# dev-setup
A guide to setting up a development environment on and all useful software.
- [iTerm](https://www.iterm2.com/)
- [Homebew](https://brew.sh/)
- [Cask](https://caskroom.github.io/)
- [Oh my zsh](http://ohmyz.sh/)
- [Ruby and RVM](https://get.rvm.io)
- [Node.js](https://nodejs.org/en/)
- [Atom](https://atom.io/)
- [Git](https://git-scm.com/)
- Git alias
- [Dropbox](https://www.dropbox.com/downloading)
- [Fetch](https://fetchsoftworks.com/)
- [Spectacle](https://www.spectacleapp.com/)
- [Flux](https://justgetflux.com/)
- [1password](https://1password.com/)
- [Slack](https://slack.com/)
- [Figma](https://www.figma.com/)
- [Sketch](https://www.sketchapp.com/)

System update
-
First thing you need to do, on any OS actually, is update the system! For that: **Apple Icon > Software Update...**

System preferences
-
If this is a new computer, there are a couple tweaks I like to make to the System Preferences. Feel free to follow these, or to ignore them, depending on your personal preferences.

In **Apple Icon > System Preferences:**

* Trackpad > Tap to click
* Keyboard > Key Repeat > Fast (all the way to the right)
* Keyboard > Delay Until Repeat > Short (all the way to the right)
* Dock > Automatically hide and show the Dock


[iTerm](https://www.iterm2.com/)
-
Since we're going to be spending a lot of time in the command-line, let's install a better terminal than the default one.

Let's just quickly change some preferences. In **iTerm > Preferences...**, under the tab **General**, uncheck **Confirm closing multiple sessions** and **Confirm "Quit iTerm2 (Cmd+Q)" command** under the section **Closing**.

In the tab **Profiles**, create a new one with the "+" icon, and rename it to your first name for example. Then, select **Other Actions... > Set as Default**. Finally, under the section **Window**, change the size to something better, like **Columns: 125** and **Rows: 35**.

When done, hit the red "X" in the upper left (saving is automatic in OS X preference panes). Close the window and open a new one to see the size change.

[Homebrew](https://brew.sh/)
-
Package managers make it so much easier to install and update applications (for Operating Systems) or libraries (for programming languages). The most popular one for OS X is Homebrew.

### Install
An important dependency before Homebrew can work is the **Command Line Tools** for **Xcode**. These include compilers that will allow you to build things from source.

Now, Xcode weights something like 2GB, and you don't need it unless you're developing iPhone or Mac apps. Good news is Apple provides a way to install only the Command Line Tools, without Xcode. To do this you need to go to http://developer.apple.com/downloads, and sign in with your Apple ID (the same one you use for iTunes and app purchases). Unfortunately, you're greeted by a rather annoying questionnaire. All questions are required, so feel free to answer at random.

Once you reach the downloads page, search for "command line tools", and download the latest **Command Line Tools (OS X Mountain Lion) for Xcode**. Open the **.dmg** file once it's done downloading, and double-click on the **.mpkg** installer to launch the installation. When it's done, you can unmount the disk in Finder.

**Note:** If you are running **OS X 10.9 Mavericks**, then you can install the Xcode Command Line Tools directly from the command line with `$ xcode-select --install`, and you don't have to go through the download page and the questionnaire.

Finally, we can install Hombrew! In the terminal paste the following line (without the `$`), hit **Enter**, and follow the steps on the screen:
```
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
One thing we need to do is tell the system to use programs installed by Hombrew (`in /usr/local/bin`) rather than the OS default if it exists. We do this by adding `/usr/local/bin` to your `$PATH` environment variable:
```
$ echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.bash_profile
```
Open a new terminal tab with **Cmd+T** (you should also close the old one), then run the following command to make sure everything works:
```
$ brew doctor
```
### Usage

To install a package (or **Formula** in Homebrew vocabulary) simply type:
```
$ brew install <formula>
```
To update Homebrew's directory of formulae, run:
```
$ brew update
```
Note: I've seen that command fail sometimes because of a bug. If that ever happens, run the following (when you have Git installed):
```
$ cd /usr/local
$ git fetch origin
$ git reset --hard origin/master
```
To see if any of your packages need to be updated:
```
$ brew outdated
```
To update a package:
```
$ brew upgrade <formula>
```
Homebrew keeps older versions of packages installed, in case you want to roll back. That rarely is necessary, so you can do some cleanup to get rid of those old versions:
```
$ brew cleanup
```
To see what you have installed (with their version numbers):
```
$ brew list --versions
```

[Cask](https://caskroom.github.io/)
-
Homebrew-Cask extends Homebrew and brings its elegance, simplicity, and speed to the installation and management of GUI macOS applications such as Google Chrome and Adium.
To install Cask formula simply type:
```
$ brew tap caskroom/cask
```

[Oh my zsh](http://ohmyz.sh/)
-
Once installed, your terminal shell will become the talk of the town or your money back! With each keystroke in your command prompt, you'll take advantage of the hundreds of powerful plugins and beautiful themes. Strangers will come up to you in cafés and ask you, "that is amazing! are you some sort of genius?"

Install Oh my zsh with cURL:
```
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

[Ruby and RVM](https://get.rvm.io)
-
Like Python, Ruby is already installed on Unix systems. But we don't want to mess around with that installation. More importantly, we want to be able to use the latest version of Ruby.

### Install

When installing Ruby, best practice is to use RVM (Ruby Version Manager) which allows you to manage multiple versions of Ruby on the same machine. Installing RVM, as well as the latest version of Ruby, is very easy. Just run:
```
$ curl -L https://get.rvm.io | bash -s stable --ruby
```
When it is done, both RVM and a fresh version of Ruby 2.0 are installed. The following line was also automatically added to your .bash_profile:
```
[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm" # Load RVM into a shell session *as a function*
```
I prefer to move that line to the .extra file, keeping my .bash_profile clean. I suggest you do the same.

After that, start a new terminal and run:
```
$ type rvm | head -1
```
You should get the output `rvm is a function`.

### Usage

The following command will show you which versions of Ruby you have installed:
```
$ rvm list
```
The one that was just installed, Ruby 2.0, should be set as default. When managing multiple versions, you switch between them with:
```
$ rvm use system # Switch back to system install (1.8)
$ rvm use 2.0.0 --default # Switch to 2.0.0 and sets it as default
```
Run the following to make sure the version you want is being used (in our case, the just-installed Ruby 1.9.3):
```
$ which ruby
$ ruby --version
```
You can install another version with:
```
$ rvm install 1.9.3
```
To update RVM itself, use:
```
$ rvm get stable
```
RubyGems, the Ruby package manager, was also installed:
```
$ which gem
```
Update to its latest version with:
```
$ gem update --system
```
To install a "gem" (Ruby package), run:
```
$ gem install <gemname>
```
To install without generating the documentation for each gem (faster):
```
$ gem install <gemname> --no-document
```
To see what gems you have installed:
```
$ gem list
```
To check if any installed gems are outdated:
```
$ gem outdated
```
To update all gems or a particular gem:
```
$ gem update [<gemname>]
```
RubyGems keeps old versions of gems, so feel free to do come cleaning after updating:
```
$ gem cleanup
```

[Node.js](https://nodejs.org/en/)
-
Install Node.js with Homebrew:
```
$ brew update
$ brew install node
```
The formula also installs the npm package manager. However, as suggested by the Homebrew output, we need to add `/usr/local/share/npm/bin` to our path so that npm-installed modules with executables will have them picked up.

To do so, add this line to your `~/.path` file, before the export `PATH` line:
```
PATH=/usr/local/share/npm/bin:$PATH
```
Open a new terminal for the `$PATH` changes to take effect.
We also need to tell npm where to find the Xcode Command Line Tools, by running:
```
$ sudo xcode-select -switch /usr/bin
```

### Npm usage
Node modules are installed locally in the node_modules folder of each project by default if you don't install them globally.

To install a package:
```
$ npm install <package> # Install locally
$ npm install -g <package> # Install globally
```
To install a package and save it in your project's package.json file:
```
$ npm install <package> --save
```
To see what's installed:
```
$ npm list # Local
$ npm list -g # Global
```
To find outdated packages (locally or globally):
```
$ npm outdated [-g]
```
To upgrade all or a particular package:
```
$ npm update [<package>]
```
To uninstall a package:
```
$ npm uninstall <package>
```

### JSHint

JSHint is a JavaScript developer's best friend.

Install JSHint via npm (global install preferred)
```
$ npm install -g jshint
```
Follow additional instructions on the [JSHint](http://jshint.com/docs/) website.

[Atom](https://atom.io/)
-
Atom is a text editor that's modern, approachable, yet hackable to the core—a tool you can customize to do anything but also use productively without ever touching a config file.
###### Atom packages and settings
- [Atom Sync](https://atom.io/packages/atom-sync)
- [JSHint](https://atom.io/packages/atom-jshint)
- [Synced Sidebar](https://atom.io/packages/synced-sidebar)
- [Pigments](https://atom.io/packages/pigments)
- [File Icons](https://atom.io/packages/file-icons)
- [Solarized Dark](https://atom.io/themes/solarized-dark-syntax)
- [Solarized Light](https://atom.io/themes/solarized-light-syntax)
1. [x] Install Shell Commands
2. [x] Scroll Past End
3. [x] Show Indent Line
4. [x] Show Invisible

[Git](https://git-scm.com/)
-
Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

To install, simply run:

```
$ brew install git
```
When done, to test that it installed fine you can run:

```
$ git --version
```
And $ which git should output /usr/local/bin/git.

Let's set up some basic configuration. Add this to your `.gitconfig` file. 
1. `cd ~`
2. `open .gitconfig`
```
[alias]
  st = status
  ci = commit
  co = checkout
  br = branch
  unstage = reset HEAD --
  last = log -1 HEAD
```

Next, we'll define your Git user (should be the same name and email you use for GitHub and Heroku):

```
$ git config --global user.name "Your Name Here"
$ git config --global user.email "your_email@youremail.com"
```
They will get added to your .gitconfig file.

To push code to your GitHub repositories, we're going to use the recommended HTTPS method (versus SSH). So you don't have to type your username and password everytime, let's enable Git password caching as described here:

```
$ git config --global credential.helper osxkeychain
```
Note: On a Mac, it is important to remember to add .DS_Store (a hidden OS X system file that's put in folders) to your .gitignore files. You can take a look at this repository's [.gitignore](https://github.com/nicolashery/mac-dev-setup/blob/master/.gitignore) file for inspiration.

Projects folder
-
This really depends on how you want to organize your files, but I like to put all my version-controlled projects in `~/Projects`. Other documents I may have, or things not yet under version control, I like to put in `~/Dropbox` (if you have Dropbox installed), or `~/Documents`.

Apps
-
* [Dropbox](https://www.dropbox.com/downloading): Bring your photos, docs, and videos anywhere and keep your files safe.

* [Fetch](https://fetchsoftworks.com/): Fetch is a reliable, full-featured file transfer client for the Apple Macintosh whose user interface emphasizes simplicity and ease of use.

* [Spectacle](https://www.spectacleapp.com/): Move and resize windows with ease. Window control with simple and customizable keyboard shortcuts.
  - Fullscreen: `control + ⌥ Option + ⌘ Cmd + ↑` 
  - Right Half: `⌥ Option + ⌘ Cmd + →` 
  - Left Half: `⌥ Option + ⌘ Cmd + ←`
  - Next Display: `control + ⌥ Option + ⌘ Cmd + →`
  - Previous Display: `control + ⌥ Option + ⌘ Cmd + ←`

* [Flux](https://justgetflux.com/): f.lux makes your computer screen look like the room you're in, all the time. When the sun sets, it makes your computer look like your indoor lights. In the morning, it makes things look like sunlight again.

* [1Password](https://1password.com/): All your other passwords and important information are protected behind your Master Password, which only you know.

* [Slack](https://slack.com/): Whatever work means for you, Slack brings all the pieces and people you need together so you can actually get things done.

* [Figma](https://www.figma.com/): Figma is the first interface design tool based in the browser, making it easier for teams to create software.

* [Sketch](https://www.sketchapp.com/): Sketch gives you the power, flexibility and speed you always wanted in a lightweight and easy-to-use package. Finally you can focus on what you do best: Design.

#### Credit to: 
[nicolashery](https://github.com/nicolashery/mac-dev-setup) for comming up with original list and documentation.
