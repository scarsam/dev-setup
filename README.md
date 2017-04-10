# dev-setup
A guide to setting up a development environment on and all useful software.
- [Homebew](https://brew.sh/)
- [Cask](https://caskroom.github.io/)
- [iTerm](https://www.iterm2.com/)
- [Oh my zsh](http://ohmyz.sh/)
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

[Homebrew](https://brew.sh/)
-
Package managers make it so much easier to install and update applications (for Operating Systems) or libraries (for programming languages). The most popular one for OS X is Homebrew.

[Cask](https://caskroom.github.io/)
-
Homebrew-Cask extends Homebrew and brings its elegance, simplicity, and speed to the installation and management of GUI macOS applications such as Google Chrome and Adium.

[iTerm](https://www.iterm2.com/)
-
iTerm2 is a replacement for Terminal and the successor to iTerm. It works on Macs with macOS 10.8 or newer. iTerm2 brings the terminal into the modern age with features you never knew you always wanted.

[Oh my zsh](http://ohmyz.sh/)
-
Once installed, your terminal shell will become the talk of the town or your money back! With each keystroke in your command prompt, you'll take advantage of the hundreds of powerful plugins and beautiful themes. Strangers will come up to you in cafés and ask you, "that is amazing! are you some sort of genius?"

[Node.js](https://nodejs.org/en/)
-
Install Node.js with Homebrew:
```
$ brew update
$ brew install node
```
The formula also installs the npm package manager. However, as suggested by the Homebrew output, we need to add /usr/local/share/npm/bin to our path so that npm-installed modules with executables will have them picked up.

To do so, add this line to your ~/.path file, before the export PATH line:
```
PATH=/usr/local/share/npm/bin:$PATH
```
Open a new terminal for the $PATH changes to take effect.
We also need to tell npm where to find the Xcode Command Line Tools, by running:
```
$ sudo xcode-select -switch /usr/bin
```

[Atom](https://atom.io/)
-
Atom is a text editor that's modern, approachable, yet hackable to the core—a tool you can customize to do anything but also use productively without ever touching a config file.
###### Atom packages and settings
[Atom Sync](https://atom.io/packages/atom-sync)
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

Apps
-
* [Dropbox](https://www.dropbox.com/downloading): Bring your photos, docs, and videos anywhere and keep your files safe.

* [Fetch](https://fetchsoftworks.com/): Fetch is a reliable, full-featured file transfer client for the Apple Macintosh whose user interface emphasizes simplicity and ease of use.

* [Spectacle](https://www.spectacleapp.com/): Move and resize windows with ease. Window control with simple and customizable keyboard shortcuts.
  - ###### Spectacle shortcuts
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

