# discord-image-autoposter

Posts images from configured data sources into discord channels at set intervals. All of which can be configured via text commands.

## Questions to answer

How do we handle secrets in AWS?

## Messy Design Doc
We are writing it in Python because I like Python. Suck it JS.

### Code design?

It's a discord bot it can't be that complicated.... I don't do this design process when I'm at work!

#### Classes
##### Configuration (Abstract)
Idk how we want to store the configuration. Perhaps in the beginning we start simple and just have it stored as a JSON file on disk. Maybe in the future we put it in a database or something. Just have a configuration class so that the bots logic doesn't have to worry about *how* the configuration is stored, it just cares that it *is* stored somewhere.

##### DataSource (Abstract)
So the bot needs to get images from somewhere, perhaps in the future we might want to add different data sources.
###### Link
Inherits from DataSource, the default way of getting an image. Probably the only way we will want but... SOLID DESIGN PRINCIPLES.

##### Command
At least we have `argparse`. I hate command parsing. I don't want to write this. 
If we have it as a single module then we can have a common place to check for shite like having the correct permissions and parsing. 

### Storing bot configuration

The bot can be configured via text commands and its configuration needs to be stored somewhere. The configration must be *persistent*, it cannot be lost for any reason.

### Deployment

The bot should be deployable in a docker container. We need to take into consideration how secrets are managed by our cloud deloyment option.
