# Sketch Sandbox

A small library to get around sandbox issues in Sketch.

## Why?

I'll write a real explanation when I have the time, but if you don't know why you need this, this is definitely not for you :)

The library is not heavily tested, so please [file an issue](https://github.com/bomberstudios/sketch-sandbox/issues) if it doesn't work for you :)

## Usage

- include the 'sandbox.js' library in your plugin, using `#import 'sandbox.js'`
- ask the user to authorize a path, like this:

        new AppSandbox().authorize(path, callback)

  where `path` is an absolute path to a folder, and `callback` is a JavaScript function that will be executed if the user authorizes the operation.

## Notes

- Once a user authorizes a folder, you'll be able to write to its subfolders.

## Example

This is my personal favorite way of dealing with sandboxing issues: just ask the user for permission to write to her $HOME folder:

    var home_folder = "/Users/" + NSUserName()
    new AppSandbox().authorize(home_folder, function(){
      // do whatever you need to do here
    })

This is probably overkill, unsafe, and unreasonable to ask. But on the other hand, you'll only need the user to authorize Sketch once (regardless of the plugin, authorization is per-app, not per-plugin :). As explained in the Notes section, once the user authorizes its $HOME folder, you'll be able to read & write from its subfolders (including the 'Documents' and 'Dropbox' folders :)
