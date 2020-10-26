# Spotify Reddit Music Bot

## Table of Contents

- [About](#about)
- [Getting Started](#getting_started)
    - [Prerequisites](#pres)
        - [Setting Up Your Script App](#script_app)
        - [Creating Post Flairs](#post_flairs)
        - [Environment Variables](#env_var)
- [Usage](#usage)
    - [Installing](#install)
    - [Running](#run)
- [Securing Your Client](#secure_client)


# About <a name = "about"></a>

# NOTE: This repo does not contain the code for this bot!

This bot will scrape tracks from the __Spotify Web API__ and post them as playable music to your subreddit.


# Getting Started <a name = "getting_started"></a>

These instructions will get you a copy of the project up and running on your local machine.

## Prerequisites <a name = "pres"></a>


The first step is to install the correct version of NodeJS for your system. You can find the official downloads here: https://nodejs.org/en/download/


## Setting Up Your Script App <a name = "script_app"></a>

You'll have to create a new account for your bot before you move any further.\
Once the account is created, log in, go to [reddit.com/prefs/apps](https://www.reddit.com/prefs/apps) to fill out the form to create a new script app.



<img src='https://i.imgur.com/yq8akJ7.png'>

## Creating Post Flairs <a name = "post_flairs"></a>

The bot will select a flair template id that you choose to make its posts stand out from other users. The steps to set this up are fairly straightforward:
First go to your Mod Dashboard by navigating to https://www.reddit.com/r/YOUR_SUB_NAME/about/modqueue
1. Click `ADD FLAIR`
<img src ="https://imgur.com/gcr6Vna.png">

2. Fill out the form:
    - The default text will be overwritten by the bot, but is required for you to enter before submitting
    - CSS class can be left blank
    - You may decide to make this a *Mod Only* flair, but you will need to add the bot as a mod to your server for it to work
    - Edit the background color and text color the way you like
    - You may choose to edit the post appearance.
    - Upload images, change the color of the post. Play around until you find something you like.
    - When you are finished editing the appearance, click `SAVE`
<img src ="https://imgur.com/EIaWseg.png">

3. Now `COPY ID` and you are going to paste this into your pw.env file, which is explained in the next step.
<img src="https://imgur.com/Ub3otHW.png">

## Environment Variables <a name = "env_var"></a>
Now that you've set up your bot account, granted it permissions (if nececary) on your subreddit, created a script app and gotten your flair id, it's time to download the source code and paste in your environment variables.

Download the .zip file containing the source code on this page. Unzip it and save it to your computer somewhere. Now open up the pw.envEXAMPLE file.\
Also have open reddit.com/prefs/apps as you'll need to copy/paste the items you'll find there.\
__USER_AGENT__ is just a name that the server will identify your bot by. It can be whatever you want.\
__CLIENT_ID__ and __CLIENT_SECRET__ are fround in prefs/apps.\
__REDDIT_USER__ is your bots username.\
__REDDIT_PASS__ is its password.\
__MASTER_SUB__ is the subreddit it will work on.\
__DEBUG_CODE__ and __DEBUG_NETWORK__ should be set to false unless any problems arise.\
__INTERVAL__ how often (in minutes) the bot will submit a new post.\
__PLAYLIST_NAME__ the name of the playlist to search for. The bot will find the closest match to a Public Spotify Playlist.\
__FLAIR_TEMPLATE_ID__ is obtained when you created your flair template in the __Mod Dashboard__.





USER_AGENT=''\
CLIENT_ID=''\
CLIENT_SECRET=''\
REDDIT_USER=''\
REDDIT_PASS=''\
MASTER_SUB=''\
DEBUG_CODE='false'\
DEBUG_NETWORK='false'\
INTERVAL='10'\
PLAYLIST_NAME=''\
FLAIR_TEMPLATE_ID=''
    


Once these fields are completely filled out, remove <i>EXAMPLE</i> from the end of the filename.

> pw.envEXAMPLE = pw.env




# Usage <a name = "usage"></a>

## Installing <a name="install"></a>

Once you've got your pw.env file correctly filled out and renamed, you may run the installer. 

Double-click __INSTALL.bat__ to run the isntaller script.

Once the installer is finished running, you may use __RUN.bat__ to run.

## Running <a name="run"></a>

To run the bot, double-click __RUN.bat__

The bot will: 
1. Search Spotify for the playlist you define in __pw.env__
2. Make a list of tracks from the playlist
3. Shuffle the playlist
4. Post each track to your subreddit at the interval you set in __pw.env__




# Securing your client <a name="secure_client"></a>
I have included a throwaway client for you to use. It is located in src/util/CLIENT.env.json.

You should either follow these steps to create your own client and replace the existing one, or visit [this url](https://developer.spotify.com/dashboard/applications/75bad5dd3570409bb513d61b74fb9398) with the username and password you have been given, and `RESET` the Client Secret on the page. Copy the new value and replace the old __"SECRET"__ value with the one you find there.

1. Go to the [Spotify Developer Console](https://developer.spotify.com/dashboard/applications) and click `CREATE AN APP`
<img src="https://imgur.com/MhY0Hx2.png">

2. Give it a name and agree to the terms.
<img src="https://imgur.com/UqfKvqW.png">

3. Now you have your `Client ID` and `CLIENT SECRET` and you can authenticate against the api.
Navigate to src/util/CLIENT.env.json and update the values before running your bot.
<img src="https://imgur.com/qaVBEou.png">

