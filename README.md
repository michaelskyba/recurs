# Recurs
A loose successor to tunnel? SM-2 had already died a long time ago...

This time we're relying on an external library for the actual algorithm:
[py-fsrs](https://github.com/open-spaced-repetition/py-fsrs). Recurs just
handles the slop of the storage and user interaction.

### Deck format
A deck file consists of comments and cards.

A card is a tab-separated value entry, with columns:
1. Front
2. Back
3. Card ID

When manually creating cards, you leave the card ID blank, and then use
`init_cards` to receive IDs. You can give it an additional numeric argument to
limit how many new cards to create, which is helpful if your deck is large.

```sh
$ echo "This is my deck" > main.deck
$ echo "According to the canon, who was it that Claude loved?\tAsara" >> main.deck
$ cat main.deck
This is my deck
According to the canon, who was it that Claude loved?	Asara
$ ./init_cards main.deck
Line 2: Created card 17289698279672662
main.deck: Created 1 new cards
$ cat main.deck
This is my deck
According to the canon, who was it that Claude loved?	Asara	17289698279672662
$ cat ~/.local/share/recurs/scheduling/17289698279672662.json
{
    "due": "2024-10-15T05:23:47.967279+00:00",
    "stability": 0,
    "difficulty": 0,
    "elapsed_days": 0,
    "scheduled_days": 0,
    "reps": 0,
    "lapses": 0,
    "state": 0
}
```
