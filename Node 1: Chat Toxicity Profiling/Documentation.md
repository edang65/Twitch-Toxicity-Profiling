# Node 1: Chat Toxicity Profiling

### Abstract
The goal of Node 1: Chat Toxicity Profiling is to start simple, using basic sentiment analysis to measure general sentiment of Twitch Chat experiences across different streamers on Twitch. Each Twitch stream develops its own culture and community around the broadcaster, so I'd like to start with a simple quantification of general sentiment of different Twitch Chat experiences across different broadcasters' communities. 

### Implementation 
I used ReChatTool, a command line tool developed by github user jdpurcell, to pull unstructured chat log data from various Twitch VODs in a CSV file, with each chat message on a single line formatted as follows: 
[TIMESTAMP] USERNAME: MESSAGE
https://github.com/jdpurcell/RechatTool

From there, I'm just cleaning the raw comment file, running it through VADER sentiment analyzer, and formatting results into a DataFrame. Unfortunately there are plenty of limitations that exist due to the nature of Twitch chat, however the purpose of this node was simply to provide very high-level analysis to begin quantifying general positive/negative sentiment across Twitch. 

### Findings
Across 10 streamers, each analyzing 5 long VODs' chat logs, I've determined the general overall sentiment of a few communities on Twitch across to guage general sentiment across the platform.

###### Limitations:
- Downloading chat data from VODs misses out on <deleted messages> that are typically classified as "Rulebreaking" comments, likely containing hate speech or other rule-breaking profanities.
- Much of Twitch chat culture is reliant on various Twitch-specific emoticons (i.e. PogChamp, LUL, etc.) that are excluded from sentiment analysis.
- Typos, chat spam, and harmless banter are often mishandled in the naive pre-packaged sentiment analysis approach

###### Future Improvements: 
- Scrape live chat logs to collect the text behind <deleted messages> that are typically classified as "Rulebreaking" comments.
- Implement Twitch emote sentiment/quantify sentiment behind popular Twitch-specific emoticons (i.e. Pog = positive)
