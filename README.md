<div align="center">
  <h1>ytmous</h1>
  <p>Anonymous Youtube Proxy</p>
</div>

### Search, Click, and watch
ytmous is an lightweight, and Anonymous Youtube Proxy. Designed for device with limited resource.

### There's no tracker and ads
Only with a simple UI, ready for you to watch some videos in a second

### Free and Open source
ytmous is licensed under BSD 3 Clause and it's code is free. You can also host your own ytmous server. <b>It's easy!</b>

### Customizeable
ytmous server owner could customize the frontend to what they would like. See [Customizing Frontend](#customizingfrontend)

**DISCLAIMER:** ytmous could fetch, stream or download videos from YouTube, even copyrighted ones. Please respect all copyright laws.

## Screenshots
![ytmous_homepage.png](https://raw.githubusercontent.com/Brandon421-ops/ytmous/nightly/screenshots/ytmous_homepage.png)
![ytmous_mobile_search.png](https://raw.githubusercontent.com/Brandon421-ops/ytmous/nightly/screenshots/ytmous_mobile_search.png)
![ytmous_mobile_channel.png](https://raw.githubusercontent.com/Brandon421-ops/ytmous/nightly/screenshots/ytmous_mobile_channel.png)
![ytmous_mobile_playlists.png](https://raw.githubusercontent.com/Brandon421-ops/ytmous/nightly/screenshots/ytmous_mobile_playlists.png)
![ytmous_mobile_watch.png](https://raw.githubusercontent.com/Brandon421-ops/ytmous/nightly/screenshots/ytmous_mobile_watch.png)
![ytmous_desktop_watch.png](https://raw.githubusercontent.com/Brandon421-ops/ytmous/nightly/screenshots/ytmous_desktop_watch.png)

## Server Requirement
- Node v16+ is advised.
- Fast server network connection with ability to reach YouTube

## Configuration
The code is reading the provided configuration from Environment Variable that comes from your system. These variable is **optional**.

- `GEOLOCATION`: YouTube Geolocation. Default is `US`.
- `USER_AGENT`: This variable is where we fake our user agent to request youtube.
- `DLCHUNKSIZE`: Download Chunk Size. Default is 10 MB (1024 * 1024 * 10)
- `NO_CLUSTERS`: Do not run ytmous with clusters. Useful for debugging
- `CLUSTERS`: Number of clusters to fork. By default is depending on `os.availableParallelism()` integer or `os.cpus().length`.
- `PORT`: Server port to listen to.

## Customizing frontend
You can customize your frontend by creating `local` directory to replace files from `views` or `public` directory.

- `local/views/` for backend rendering (`views`)
- `local/public/` for static page (`public`)

```
local
├── public
│   ├── Ubuntu-R.ttf
│   ├── css
│   │   ├── Toard.css
│   │   └── style.css
│   ├── index.html
│   └── robots.txt
└── views
    ├── channel.ejs
    ├── comments.ejs
    ├── error.ejs
    ├── playlist.ejs
    ├── search.ejs
    └── watch.ejs
```

# Deployment

Table of contents

- Quick & easy deployment
- Deployment configuration explaination
- how to use email OTP Verification mode
- Advanced Deployment
- Filesystem
- Works For School/Home Computers

## Quick & Easy Deployment Options

[![Deploy to Heroku](https://raw.githubusercontent.com/BinBashBanana/deploy-buttons/master/buttons/remade/heroku.svg)](https://heroku.com/deploy/?template=https://github.com/Brandon421-ops/ytmous)
<br>
[![Run on Replit](https://raw.githubusercontent.com/BinBashBanana/deploy-buttons/master/buttons/remade/replit.svg)](https://replit.com/github/Brandon421-ops/ytmous-diff-gui)
<br>
[![Deploy to IBM Cloud](https://raw.githubusercontent.com/BinBashBanana/deploy-buttons/master/buttons/remade/ibmcloud.svg)](https://cloud.ibm.com/devops/setup/deploy?repository=https://github.com/Brandon421-ops/ytmous)
<br>
[![Deploy to Amplify Console](https://raw.githubusercontent.com/BinBashBanana/deploy-buttons/master/buttons/remade/amplifyconsole.svg)](https://console.aws.amazon.com/amplify/home#/deploy?repo=https://github.com/Brandon421-ops/ytmous)
<br>
[![Run on Google Cloud](https://raw.githubusercontent.com/BinBashBanana/deploy-buttons/master/buttons/remade/googlecloud.svg)](https://deploy.cloud.run/?git_repo=https://github.com/Brandon421-ops/ytmous)
<br>
[![Deploy on Railway](https://binbashbanana.github.io/deploy-buttons/buttons/remade/railway.svg)](https://railway.app/new/template/pBzeiN)
<br>
[![Deploy To Koyeb](https://binbashbanana.github.io/deploy-buttons/buttons/remade/koyeb.svg)](https://app.koyeb.com/deploy?type=git&repository=github.com/Brandon421-ops/ytmous&branch=main&name=ytmous)
<br>
[![Deploy to Render](https://raw.githubusercontent.com/BinBashBanana/deploy-buttons/main/buttons/remade/render.svg)](https://render.com/deploy?repo=https://github.com/Brandon421-ops/ytmous)
<br>
[![Remix on Glitch](https://binbashbanana.github.io/deploy-buttons/buttons/remade/glitch.svg)](https://glitch.com/edit/#!/import/github/Brandon421-ops/ytmous-diff-gui)

## Starting the server
If this is your first time running this server, You may need to install it's dependencies first by executing `npm install`. 

Then, you can start the server by executing:
```sh
npm start
```
or
```
PORT=3000 npm start
```

## API endpoints
You can use ytmous API endpoints for your applications. The following endpoints are supported:

### `/api/search`
Endpoint to search videos.

#### Queries
- `q` (String) **(Required)**
  String to search with.

- `page` (Number)
  Next page listing.

### `/api/getPlaylistInfo/[playlistID]`
Endpoint to list videos from playlist / channel.

#### Parameters
- `playlistID` **(Required)**
  String of Playlist or Channel ID.

### `/api/getVideoInfo/[videoID]`
Endpoint to give information of an YouTube video.

#### Parameters
- `videoID` **(Required)**
  String of YouTube video ID

### `/api/getComments/[videoID]`
#### Parameters
- `videoID` **(Required)**
  String of YouTube video ID.

#### Queries
- `continuation` (String)
  Continuation ID of an Comments. Used to fetch the next comment section.

- `replyToken` (String)
  Reply token. Used to view an reply of a comment.
  To view continuation of an Reply comments, Put continuationID in `replyToken` query instead of `continuation`.
