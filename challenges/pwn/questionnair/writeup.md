# Challenge: Questionnair (Pwn)

## Approach

Follow the challenge questions — they guide you through the binary analysis step by step.

## Useful Tools

- [pwndbg](https://github.com/pwndbg/pwndbg) — a much more usable GDB wrapper

## Useful Commands

```sh
file <binary>
printf 'A%.0s' {1..30} | ./<binary>   # spike with 30 'A' characters to test for overflow
```
