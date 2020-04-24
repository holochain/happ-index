# Holochain App Index
This repository serves as a central point for listing and referencing existing hApps that are ready to be installed through [Holoscape](https://github.com/holochain/holoscape).
It is meant to function as a short term interim solution until the decentralized hApp store - which is a Holochain app itself - is up and running.

## hApp Store in Holoscape
[Holoscape](https://github.com/holochain/holoscape) downloads the file [index.json](index.json) to acquire the full list of hApps and renders a card with description and screenshot for each.
Chooses the user to install a hApp, Holoscape also downloads the `bundle.toml` file from the hApp's resources directory in this repository which has links to all the hApp's assets (i.e. DNA files and zipped UIs).

## A note on versions

We tag commits in this repo that are compatible for particular version of holochain like this: `hc-v0.0.47-alpha1` and, in the short term attempt to make sure that hApps in the index work with the given version of holochain (and the holoscape version that includes that holochain version), but please note that we can't guarantee that all the hApps work perfectly with the given version.

## Publishing a hApp
If you want to make your hApp available to the public during this alpha phase for testing, you can do so by creating a pull-request to this repository.
Once it's merged it will appear in the list of hApps inside Holoscape.

The main ingredient you will need for this is a [hApp bundle file](https://github.com/holochain/holoscape/tree/master/example-bundles).
This file is like a manifest for your hApp. It describes what DNA(s) and UI(s) your hApp consists of, and what their internal relationships (i.e. bridges and references/handles) are.

You can test your hApp bundles with Holoscape by installing it manually ("from file") inside Holoscape before adding them to this repository.
hApp bundles can reference DNA and UI files either locally via `file://` or any remote resource via `http://`.
In order to keep this repository small, please host those binary assets either on your own server or publish them as a release in your Github repository, and then link to those files from your bundle.
Holoscape will download the DNA and UI directly from there during install.



### What should go in your PR?

1. Add an element to the array in [index.json](index.json) like so:
    ```
    {
        "name": "Peer Chat",
        "directory": "peer-chat",
        "github": "https://github.com/holochain/peer-chat",
        "icon": null,
        "screenshot": "https://raw.githubusercontent.com/holochain/peer-chat/develop/doc/screen.png",
        "description": "A simple chat app designed to get new users up, running and developing on Holochain"
    }
    ```
    `name`, `screenshot` and `description` get displayed inside Holoscape.
    `directory` is the name of the sub-directory that you add in step 2.
2. Add a directory under [happ-resources](happ-resources) with the name of your happ.
   Inside that sub-directory, add your hApp bundle file with the file name `bundle.toml`

That's it! Once your PR gets approved and merged, your hApp can be installed with just a few clicks and used by others for testing purposes.
