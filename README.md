# 16n editor

The 16n editor allows you to edit the configuration of your 16n from within a web browser. It supports 16ns running firmware **2.0.0** and up.

The 16n editor is a Javascript app based around [Svelte](svelte).

## Build Requirements

- Node.js v8+

## Usage Requirements

- As a WebMIDI app, you need a client that can support it. That basically means Chrome right now.
- A 16n running firmware v2.0.0 or higher.

## Installation

    npm install

## Running the development environment

    npm run dev

This will run a development environment at `localhost:5000`, with live reloading enabled.

By default, the server will only respond to requests from localhost.

## Building and running in production mode

To create an optimised version of the app:

    npm run build

You can run the newly built app with `npm run start`. This uses [sirv](https://github.com/lukeed/sirv), which is included in your package.json's `dependencies` so that the app will work when you deploy to platforms like [Heroku](https://heroku.com).


## Code formatting

We use `prettier` for code formatting. From your local directory:

    npx prettier --write 'src'

will prettify the `src/` directory. Code that fails Prettier's formatting standards will block merge at Github.

We're using a similar approach to [the one Simon Willison describves here](https://til.simonwillison.net/github-actions/prettier-github-actions).

## Project Structure

* `src/App.Svelte` is quite dense, but is the main entrypoint for the application and contains the app's structure.
* `src/components` contains all components. Primarily UI, but `MidiContext` serves to wrap WebMidi and keep the various stores that describe the available Midi interfaces up-to-date.
* `src/Configuration.js` describes a class `ConfigurationObject`, that represents a single instance of a 16n configuration. These are what are passed around, diffed to work out if config has changed, and converted to Sysex to send to the device.
* `src/ImportExport.js` handles converting a Configuration to JSON, and back again.
* `src/OxionMidi.js` is some convenience classes for MIDI.

## Deployment

The built site is committed to a subdirectory on the 16n site, for now.

## Icons

Icons are from [FontAwesome](https://fontawesome.com/license/free). FA Code is MIT licensed; font files are licensed under the SIL Open Font License.

## Licensing

Editor code, like the rest of 16n sourcecode, is released under the MIT License; see `LICENSE` for more details.

