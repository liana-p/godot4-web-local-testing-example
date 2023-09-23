# Godot 4 Web Export local server example (for local testing)

I was trying to run the Godot 4 web export and realised that it requires specific cors headers to be set on the server to run due to their usage of webGL2 and SharedArrayBuffer.

Godot links to a python script for it in their [exporting for web](https://docs.godotengine.org/en/stable/tutorials/export/exporting_for_web.html) documentation, but this script also didn't work for me.

I made a simple node.js server using Express which can serve an exported Godot game currently for local testing

## How it works

1. This repo is a Godot project, and the game gets exported to `export/public`.
2. The `export` folder contains a node.js server which will serve whatever is in the `public` folder with the right headers.
3. Running this node.js server allows you to view the exported game at `http://localhost:3000`

## How to use

1. Have [node.js](https://nodejs.org/en) installed
2. Either clone this repo, or create your own Godot project and set it up to export the web build to `export/public/index.html`, and to use a custom html shell (if you want to use one) in `export` (for example the included `export/export-template.html`)
3. Open the project in Godot, and export it so that it's in the `export/public` folder
4. Open a terminal in the `exports` folder
5. Run `npm install` (only needed the first time)
6. Run `npm start` to start the server
7. Open `http://localhost:3000` in your browser to view the game

## Setup on an existing project

The actual web server part of this is what's in the `export` folder. If you copy the `export` folder to your game, and create the `public` directory in it, you should be able to run this setup on an existing game.

1. Download or clone this repo somewhere
2. Copy the `export` folder to your Godot project
3. Create the `public` directory
4. Edit your Godot web export settings to export to `export/public/index.html`
5. Run the web server in `export` as explained above
