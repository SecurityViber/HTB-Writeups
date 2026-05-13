# Challenge: SPG (Crypto)

## Description

After successfully joining the academy, you attempt to log in to eclass but your browser crashes and all your files get encrypted. The only artifact provided is a password generator script. Crack it to decrypt your files.

## Solution

See [solution.py](solution.py) for the full implementation. In summary:

1. The `generatePassword` function can be reversed to recover the Master Key
2. With the Master Key recovered, decrypting the cipher is straightforward
