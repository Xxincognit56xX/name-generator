# name-generator

A tiny command-line tool that generates random, bot usernames like:

```
PacificPoet1057
SneakyWaffle4821
CosmicOtter2390
```

Each name is built from **an adjective + a noun + a 4-digit number**.

## Features

- **1,000 adjectives × 1,000 nouns × 9,000 numbers** — about **9 billion** possible combinations
- Readable, PascalCase names that look like real usernames
- Generate one name or thousands in a single run
- Confirmation prompts before generating large batches (100+ and 10,000+)
- No dependencies — uses only the Python standard library

## Requirements

- Python **3.10 or newer** (the script uses `match` statements)

## Usage

You'll be asked how many names to generate:

```
How many names should the CLI generate?
5
BraveFalcon7312
GroovyNoodle1094
ArcaneSphinx5567
MellowKoala2208
TurboPenguin9901
```

If you ask for 100 or more names, the script asks you to confirm. Type `Y` (capital) to continue; anything else cancels.

### Saving names to a file

Redirect the output to save the names. Because the script reads the count from standard input, you can pipe it in too:

```bash
echo 50 | python main.py > names.txt
```

> The first line of the file will be the prompt text. For counts of 100 or more, also send the confirmation: `printf "500\nY\n" | python main.py > names.txt`

## How it works

`main.py` holds two word lists, `adjectives` and `nouns`. The `generate_name()` function picks one word from each at random and appends a number from 1000 to 9999:

```python
random.choice(adjectives) + random.choice(nouns) + str(random.randint(1000, 9999))
```

Names are random, not guaranteed unique. Duplicates are very unlikely but possible in large batches.

## Customizing

- **Add or remove words:** edit the `adjectives` or `nouns` lists in `main.py`.
- **Change the number range:** adjust the `random.randint(1000, 9999)` call in `generate_name()`.
- **Use it in your own code:** copy `generate_name()` along with the two word lists.

## Contributing

Pull requests are welcome, especially new words. Keep entries capitalized, one word, and family-friendly.
