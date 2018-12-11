# SOM60-Release-Packages
SOM60 Developer Kit and Source Releases

Laird SOM source build instructions
===================================

Preparation
-----------

Laird does development on Ubuntu 16.04 LTS currently. It is highly recommended to use Ubuntu 16.04 for development of your customized SOM60 image.

To use to pull and build a specific project or version, you first need the program Repo from the Android project. You can install it on Ubuntu using:

    sudo apt install repo

You can also get it by following the instructions here:

https://source.android.com/source/downloading.html#installing-repo

Getting the SOM60 project
----------------------

First step, pick which release you want. Odds are you want the most recent of your release. 

Next, use Repo to initalize and fetch your release. This is a two-step process: first you tell Repo which manifest to use and then you tell it to fetch everything.

    mkdir som60_6.0.0.122_source
    cd som60_6.0.0.122_source
    repo init -u git@github.com:LairdCP/SOM60-Release-Packages.git -m som60_6.0.0.122.xml
    repo sync

_Note: Repo will initialize a .repo directory and then place all files directly in the directory that you are in when you run the `repo` command. So we recommend making a subdirectory and working in there._

Buildroot cache
---------------------

In order to speed up builds, set up a Buildroot cache to store sources that Buildroot will download. Off your home directory:

    mkdir ~/.br2_dl_dir

Then add it to your build environment:

    export BR2_DL_DIR="${HOME}/.br2_dl_dir"

Building the SOM60 project
-----------------------

There's more to go into about this, but for the sake of quick-start:

    cd wb
    make som60sd


