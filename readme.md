![GA](https://camo.githubusercontent.com/6ce15b81c1f06d716d753a61f5db22375fa684da/68747470733a2f2f67612d646173682e73332e616d617a6f6e6177732e636f6d2f70726f64756374696f6e2f6173736574732f6c6f676f2d39663838616536633963333837313639306533333238306663663535376633332e706e67)
# Git Trello Material Setup Tool

This is just a tiny little git tool that will take a Trello card and craft a new branch & folder structure that mimicks our styleguide. It makes starting a new material go a bunch faster.

It does the following for you:

- **Creates and checks out a new branch** with a slugified version of the title + the type (lab/lesson/homework)
- **Creates folders named after the lesson + type** in the appropriate core competency folder, based on Trello labels
- **Creates `starter-code` and `solution-code` folders**, which will be ignored by git unless you put something in them
- **Copies the appropriate lesson/lab template**, renames it `readme.md`
- **Fills in the title, type, competencies, and learning objectives** in the `readme.md`

![results](https://cloud.githubusercontent.com/assets/25366/8445587/f9ae1cdc-1f53-11e5-99fd-b80a37f688aa.png)

## Installation

```bash
gem install ruby-trello # this is a dependency to talk to the Trello API

brew tap micahbrich/tap # this loads my custom homebrew packages
brew install git-trello # this installs the binary
```

That's it.

## Trello Setup

It's an extension to git, though first we'll need to configure your Trello API keys & tokens. Make a `~/.trellorc` file, and we'll store some info in it.

```shell
$ touch ~/.trellorc
```

It'll end up a YAML file with no extension that looks like this:

```yaml
- name: Baseline Git Tool
  key: <key>
  secret: <secret>
  token: <token>
```

To fill those in & authorize Trello, follow these steps:

1. Visit https://trello.com/app-key, copy & paste key & secret into `~/.trellorc` in the format above
2. Modify this url: 
``https://trello.com/1/authorize?key=YOURKEY&response_type=token&scope=read,write&expiration=never&name=Baseline%20Git%20Tool`` to use your key, and paste it into your browser
3. Authorize it in the OAuth dialog
4. Copy & paste the token it gives back into the appropriate `~/.trellorc` key

If your `~/.trellorc` is filled out, it should be all set.

## Usage

Once you're all done, it'll tell you the real command:

```
$ git trello <trello card url>
```

Running that without any arguments will warn you that you need a URL. 

That's really it. Make sure you're in the WDI folder, it's pretty specifically intended for making new baseline materials.

But hopefully it's a little quicker just to get set up when you need to create a new resource. Booooom.

## Issues

Make an issue if anything doesn't work or gets wonky.
