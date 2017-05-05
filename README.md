# NPM

This image holds NPM.

[![](https://badge.imagelayers.io/existenz/npm:latest.svg)](https://imagelayers.io/?images=existenz/npm:latest 'Get your own badge on imagelayers.io')

It makes use of the runas functionality found in [my base image](https://hub.docker.com/r/existenz/base/) so the node_modules directory on your system will be owned by you, not root.

## Usage

Running NPM as the current logged in user can be done like this:

```
docker run --rm -i -t \
-e UID=$(id -u) \
-v $(pwd):/cwd \
existenz/npm
```

Of course, it's much easier to put the above in an alias like so: alias npm="docker command goes here"

Now you can just run `npm install`, `npm update`, etc. It's magic!

## Limitations

Installing NPM packages globally will fail because this is going to be done globally inside the container, not on your own system.

This wouldn't have worked anyway because NPM is running with the same user ID as your current logged in user, because of said runas functionality, and runs into permission problems.

## Bugs, questions, and improvements

If you found a bug or have a question, please open an issue on the GitHub Issue tracker. Improvements can be sent by a Pull Request against the develop branch and are greatly appreciated!
