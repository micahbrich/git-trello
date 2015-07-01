![GA](https://camo.githubusercontent.com/6ce15b81c1f06d716d753a61f5db22375fa684da/68747470733a2f2f67612d646173682e73332e616d617a6f6e6177732e636f6d2f70726f64756374696f6e2f6173736574732f6c6f676f2d39663838616536633963333837313639306533333238306663663535376633332e706e67)
# Git Trello - Baseline Resource Starter Tool

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

We'll need to configure your Trello API keys & tokens. There's a command to get it started.
```shell
$ git trello setup
```

It'll create a `~/.trellorc` file for you, with the following format:

```yaml
- name: Baseline Git Tool
  key: <key>
  secret: <secret>
  token: <token>
```

It should also give you this exact instructions, but they're here, too – to authorize Trello, follow these steps:

1. Visit https://trello.com/app-key, copy & paste key & secret into `~/.trellorc` in the format above
2. Modify this url: 
``https://trello.com/1/authorize?key=YOURKEY&response_type=token&scope=read,write&expiration=never&name=Baseline%20Git%20Tool`` to use your key, and paste it into your browser
3. Authorize it in the OAuth dialog
4. Copy & paste the token it gives back into the appropriate `~/.trellorc` key

If your `~/.trellorc` is filled out, it should be all set.

## Usage

Once you're all set up, inside our `wdi` folder, just type:

```
$ git trello https://trello.com/c/BoScVvVA/209-intro-to-ruby-data-types-variables
```

- Running that without any arguments will warn you that you need a URL. 
- Running that with a URL that isn't a Trello card will warn you that you need a valid URL. 
- Running it in a repo that isn't our `wdi` repo will also warn you that you're not in the right repo.
- If for some reason you're running it from a branch other than `master`, it'll checkout `master` first (but not stash any changes, so keep that in mind)

That's really it. I just figured the labor of creating branches & folders and manually copy & pasting from Trello & our templates could be probably be done better with a little script.

## Issues

Make an issue if anything doesn't work or gets wonky.
