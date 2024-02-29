# docker-lichess-bridge
A docker image to make your own engine available as a Lichess bot.  
This image is a ready to use integration of [lichess-bot](https://github.com/lichess-bot-devs/lichess-bot), the official bridge between [Lichess Bot API](https://lichess.org/api#tag/Bot) and bots.

# How to use this image

First, if you don't already have one, you should [create a Lichess OAuth token](https://github.com/lichess-bot-devs/lichess-bot/wiki/How-to-create-a-Lichess-OAuth-token).

Then, on your docker host, create a folder where you will put your engine configuration file, and, possibly, the program that runs your engine.  
The configuration file should be named ```config.yml```  
You can see an example of this file using the following command: ```docker run --rm --entrypoint=cat fathzer/lichess-bridge config.yml.default```. You can also find documentation about the latest lichess release (maybe not the one in this image) [here](https://github.com/lichess-bot-devs/lichess-bot/wiki/Configure-lichess-bot).

Once your configuration file is ready, let say in */home/me/myEngine* folder, run the following command:
```docker run -d /home/me/myEngine:/engine fathzer/lichess-bridge```

That's all!

If you need, you can see the lichess release information using the following command: ```docker run --rm --entrypoint=cat fathzer/lichess-bridge lib/versioning.yml```

## What if my engine requires some software installation
This image is based on [Alpine](https://www.alpinelinux.org/). You can install new software using the ```apk``` command.  
For example to install java 11, the docker file would look like:  
```
FROM fathzer/lichess-bridge

RUN apk add --no-cache openjdk11-jre
```


# How to build the image:
```docker build . -t fathzer/lichess-bridge```


