# Gist

[![Build Status](https://travis-ci.org/condemil/Gist.svg?branch=master)](https://travis-ci.org/condemil/Gist)
[![Coverage Status](https://coveralls.io/repos/github/condemil/Gist/badge.svg)](https://coveralls.io/github/condemil/Gist)
[![Package Control](https://img.shields.io/packagecontrol/dt/Gist.svg)](https://packagecontrol.io/packages/Gist)


A [Sublime Text 3](http://www.sublimetext.com/3) plugin for creating and editing Gists.


## Installation

### By Package Control

1. Download & Install **`Sublime Text 3`** (https://www.sublimetext.com/3)
1. Go to the menu **`Tools -> Install Package Control`**, then,
    wait few seconds until the installation finishes up
1. Now,
    Go to the menu **`Preferences -> Package Control`**
1. Type **`Add Channel`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    input the following address and press <kbd>Enter</kbd>
    ```
    https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
    ```
1. Go to the menu **`Tools -> Command Palette...
    (Ctrl+Shift+P)`**
1. Type **`Preferences:
    Package Control Settings – User`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    find the following setting on your **`Package Control.sublime-settings`** file:
    ```js
    "channels":
    [
        "https://packagecontrol.io/channel_v3.json",
        "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
    ],
    ```
1. And,
    change it to the following, i.e.,
    put the **`https://raw.githubusercontent...`** line as first:
    ```js
    "channels":
    [
        "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
        "https://packagecontrol.io/channel_v3.json",
    ],
    ```
    * The **`https://raw.githubusercontent...`** line must to be added before the **`https://packagecontrol.io...`** one, otherwise,
      you will not install this forked version of the package,
      but the original available on the Package Control default channel **`https://packagecontrol.io...`**
    > [!WARNING]
    > Placing this custom channel before the default channel changes Package Control's resolution globally.
    > Packages from this channel with the same name will override versions from the default channel.
    >
    > You can review the channel contents here:
    > https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
1. Now,
    go to the menu **`Preferences -> Package Control`**
1. Type **`Install Package`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    search for **`Gist`** and press <kbd>Enter</kbd>

See also:

1. [ITE - Integrated Toolset Environment](https://github.com/evandrocoan/ITE)
1. [Package control docs](https://packagecontrol.io/docs/usage) for details.


# Generating Access Token

As of [2013-05-16](https://github.com/blog/1509-personal-api-tokens), you can generate API Access Tokens via the Web UI or via the GitHub API.
**All other authorization methods is deprecated.**

## Web
* Account Settings -> [Personal access tokens](https://github.com/settings/tokens)
* "Generate new token" under "Personal access tokens"
* For "Token description" you should give it a meaningful name, Example: sublime gist
* Under "Select scopes" you can just select gist

Paste the token in the settings section under the token option.

## API

Here's a command you can run from your terminal to generate a token via curl:

    curl -v -u USERNAME -X POST https://api.github.com/authorizations --data "{\"scopes\":[\"gist\"], \"note\": \"SublimeText 2/3 Gist plugin\"}"

Where USERNAME is your Github username. Save the token generated and paste it in the settings section under the token option.

If OTP is enabled on your account, this will return 401 error code, use:

    curl -v -u USERNAME -H "X-GitHub-OTP: OTPCODE" -X POST https://api.github.com/authorizations --data "{\"scopes\":[\"gist\"], \"note\": \"SublimeText 2/3 Gist plugin\"}"

Where OTPCODE is the code your authenticator app shows you.


# Options

Edit the settings file (it should open automatically the first time you use a Gist command) to specify either token.

*   `"token": ""`

    You must enter your GitHub token here

*   `"https_proxy": http://user:pass@proxy:port`

    You can enter https proxy here
    Format: "http://user:pass@proxy:port"

*   `"api_url": ""`

    Set the url of the enterprise version of github you want to use. Defaults to github.com

*   `"max_gists": 100`

    Set the maximum number of Gists that can will fetched by the plugin. It can't be higher than 100, because of GitHub API limitations.

* `"gist_prefix": ""`

    Limit the Gists displayed in the `Open Gist` list by prefix. Leave blank to display all Gists. Example: `"gist_prefix": "Snippet:"` will only list Gists with names starting with the text **Snippet:**.

* `"save-update-hook": true`

    Set the on-save behaviour of a loaded Gist. True implies that when the Gist is saved, it'll update the online Gist. False implies that it'll bring up a save dialog for the Gist to be saved to disk.


# Usage

All functionality of the plugin is available in the `Tools` / `Gist` menu and in the command pallette.

## Creating Gists

Use the `Gist` / `Create Public Gist` or `Gist` / `Create Private Gist` commands. If you don't have anything selected, a Gist will be created with contents of current file, URL of that Gist will be copied to the clipboard and then the file will switch to Gist editing mode. If you have selected some text, a Gist will be created using only that text and then immediately opened for editing. In case of multiple selections, you'll get one Gist with multiple files.

## Editing existing Gists

Use the `Gist` / `Open Gist` command to see a list of your Gists. Selecting one will open the files from that Gist in new tabs. You can then edit the files normally and save to update the Gist, or use other commands to change Gist description, remove or rename files, or delete the Gist.


## Adding new files to existing Gists

Use the `Gist` / `Add File To Gist` command to see a list of your Gists. Selecting one will add contents of current file as a new file to that Gist and switch the file to Gist editing mode.


# Default key bindings:

## Create Public Gist

* Windows and Linux: `Ctrl+K` `Ctrl+I`
* OS X: `Super+K` `Super+I`

## Create Private Gist

* Windows and Linux: `Ctrl+K` `Ctrl+P`
* OS X: `Super+K` `Super+P`

## Update File

* Windows and Linux: `Ctrl+K` `Ctrl+S`
* OS X: `Super+K` `Super+S`

## Open Gist

* Windows and Linux: `Ctrl+K` `Ctrl+O`
* OS X: `Super+K` `Super+O`

## Insert Gist

* Windows and Linux: `Ctrl+K` `Ctrl+[`
* OS X: `Super+K` `Super+[`

## Add File

* Windows and Linux: `Ctrl+K` `Ctrl+]`
* OS X: `Super+K` `Super+]`

# Information

Source: https://github.com/condemil/Gist

Authors: [Dmitry Budaev](https://github.com/condemil/), [Alexey Ermakov](https://github.com/technocoreai)

## License
See the `LICENSE` file under this repository.

