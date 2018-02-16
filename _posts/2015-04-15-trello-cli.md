---
layout: post
title:  "How to create Trello Cards from the Command Line (with a ~10 minute set-up)"
date:   2015-04-15
---

1. This is quick and dirty and not terribly maintainable. But it's very useful for creating quick cards from the terminal. Requires familiarity with Trello and a basic understanding of bash.
2. Log-in to [Trello](https://trello.com/).
3. [Generate a key](https://trello.com/1/appKey/generate)
4. Make note of your key. Replace any mention of `YourTrelloKey` with this key.
5. [Create a token](https://trello.com/1/authorize?key=YourTrelloKey&name=SimpleBASHScript&expiration=never&response_type=token&scope=read,write)
6. Make note of the token. Replace any mention of `YourTrelloToken` with this looong hash.
7. Pick a reasonable number of the most popular boards you use. Grab the URLs of those boards. At the same time, think of short, one-word, easy-to-remember names for each board (e.g., work, projects, wedding).
8. Grab the board IDs of the boards you previously chose. It'll be the ~8 character hash-like string in the URL. E.g., for `https://trello.com/b/aWsGTrsD/work` the ID is `aWsGTrsD`
9. One by one, plug those IDs into the following API call: [https://trello.com/1/boards/insertBOARDIDhere/lists?key=YourTrelloKey](https://trello.com/1/boards/insertBOARDIDhere/lists?key=YourTrelloKey) (via browser or cURL)
10. Look at the resulting json, and, for each board, decide on the list (e.g, bullpen, doing, To Be Done) where you would most likely put a quick placeholder card (the list won't be dynamic, only the board). Make note of the 'id' property for each chosen list (one per board).
11. Make note of your new values that pair short board name with list id property. E.g. -- `work => wjeh18ehdkqwjeh7y1987`
12. Take all this info and insert it into this bash script template: [https://gist.github.com/CrookedNumber/8857003](https://gist.github.com/CrookedNumber/8857003)
13. Name the file something like `trello`
14. Make sure your new script is executable and in a sensible location, like `/usr/local/bin`
15. Adding a ticket should now be as easy as: `trello wedding "Taste cakes"`
16. Read much more about the Trello API at: [https://trello.com/docs](https://trello.com/docs)