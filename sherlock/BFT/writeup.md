# Sherlock: BFT

## Overview

This Sherlock is about analyzing the MFT (Master File Table) used by the NTFS filesystem on Windows. Best done on a Windows VM.

Required tools: [Eric Zimmerman Tools](https://ericzimmerman.github.io/#!index.md)

## Workflow

1. Use `MFTCmd` to parse the `$MFT` file into a `.csv` document
2. Load the `.csv` into Timeline Explorer
3. Use filters to narrow down the data

## Answering the Questions

The first three tasks can be solved by filtering on:
- Date
- File extension (`.zip`)
- Directory (Downloads folder)

To compute the byte offset of a `*.bat` file: each MFT entry is 1024 bytes, so multiply the entry number by 1024. Convert the result to hex (Windows Calculator works well for this) and use it to navigate in a hex editor.
