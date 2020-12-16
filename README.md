# HaugeBot
A Twitch Bot for channel DerHauge. 

### Vote Bot

Checks every chat message for the following beginnings:

results in | trigger
--- | ---
neutral | `+-` `-+` `+/-` `-/+` `haugeNeutral`  
plus | `+` `haugePlus`  
minus | `-` `haugeMinus`  

Posts an interim result every 20 seconds and an end result after 5 seconds of no additional votes.

Checks if more than 10 votes have been added before posting any result.


### Pipi Bot

Offers commands to count the number of chat users who need to go to the toilet.

    !pipi -> To mention, that you need to go to the toilet
    !warpipi -> To mention, that you have been to the toilet before a break was announced
    !zuspät -> Mention, that is now too late, and you had an accident
    !pipimeter [mod-only] -> Get the current count of users that need to go to toilet
    !pause [mod-only] -> Announce a break and reset the counter
    !reset [mod-only] -> Resets all pipi-votes
    
### Giveaway Bot

Offers some commands to control a giveaway:

    !giveaway-open [mod-only] -> Resets the entry-list and open the giveaway
    !giveaway-close [mod-only] -> Close the giveaway - from now nobody can enter
    !giveaway-reopen [mod-only] -> Open the giveaway without resetting the entrylist
    !giveaway-draw [mod-only] -> Draw a winner and remove them from the list of participants
    !giveaway-reset [mod-only] -> Clear the entry-list
    !giveaway -> take part at the giveaway


### Installation

Clone this repository, create a venv and install dependencies using `pip` and the `requirements.txt`


### Configuration

Configuration of this bot is done by a `.env` file that is placed in the same directory 
as the `hausgeist.py` file. This file must look like this:

    # General
    IRC_TOKEN=<OAuth Token to be used for login. Can be generated by using https://twitchapps.com/tmi/>
    CLIENT_ID=<Client ID that can be created by creating a twitch app at https://dev.twitch.tv/console/apps/create>
    CLIENT_SECRET=<Client Secret that can be created by creating a twitch app at https://dev.twitch.tv/console/apps/create>
    NICK=<Nick of the user the OAuth Token was generated for>
    CHANNEL=<Channel that should be entered>
    PREFIX=<Prefix for commands. In this case it is !>
    
    # Info Bot
    INFO_JSON=<Path to json file that contains info array>
    INFO_LOOP=<Number of minutes, when an information is dropped into the chat (only of the stream is live>
    INFO_COLOR=<Color, info messages should be shown at>
    
    # Pipi Bot
    PIPI_DELAY=<Delay in seconds as spam protection. This is the number of seconds between two chat announcements>
    PIPI_THRESHOLD_1=<First Threshold. Used to change color and show, it is a bit more urgent>
    PIPI_THRESHOLD_2=<Second Threshold. Used to change color and show, that it is really urgent>
    PIPIMETER_LOOP=<Number of minutes, when the current pipi count should get sent into the chat, when the stream is life>
    PIPI_RESET_THRESHOLD=<Number of minutes, the stream had to be offline, when it turns live, to reset the pipi count>
    PIPI_COLOR_0=<Neutral color used for !pause command, and if pipi vote counter is 0>
    PIPI_COLOR_1=<Color used when pipi vote is at least one, and less than PIPI_THRESHOLD_1>
    PIPI_COLOR_2=<Color used when pipi vote is at least PIPI_THRESHOLD_1, and less than PIPI_THRESHOLD_2>
    PIPI_COLOR_3=<Color used when pipi vote is above PIPI_THRESHOLD_3>
    
    # Vote Bot
    VOTE_DELAY_END=<Number of seconds withoug a vote getting count. If this delay is reached, the vote is closed.>
    VOTE_DELAY_INTERIM=<Number of seconds between two announcements of the current vote count. Also used as delay between two votes.>
    VOTE_MIN_VOTES=<Number of votes to be announced at all. A vote with less users votings will not be announced at all.>
    VOTE_COLOR=<Chat Color that is used to announce voting results>
    VOTE_PLUS=<Positive Chate Emote>
    VOTE_MINUS=<Negative Chat Emote>
    VOTE_NEUTRAL=<Neutral Chat Emote>
    
    # Giveaway Bot
    GIVEAWAY_BOT=<Chat Color that is used to send giveaway messages>
    
    # Redis Server
    REDIS_HOST=<IP of the Redis-Server>
    REDIS_PORT=<Port of the Redis-Server>
    REDIS_DB=<Index of the Database>
    REDIS_PW=<Password for the Redis-Server>
