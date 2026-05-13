# Challenge: Red Miners (Forensics)

## Solution

No need to read every line of the script — scanning for `base64 -d` statements and decoding them reveals the flag parts:

```sh
echo -n cGFydDE9IkhUQnttMW4xbmciCg== | base64 -d   # part1="HTB{m1n1ng"
echo "cGFydDI9Il90aDMxcl93NHkiCg==" | base64 -d    # part2="_th31r_w4y"
echo "X3QwX200cnN9Cg==" | base64 -d                 # _t0_m4rs}
echo "ZXhwb3J0IHBhcnQ0PSJfdGgzX3IzZF9wbDRuM3R9Ig==" | base64 -d  # part4="_th3_r3d_pl4n3t}"
```

Flag: `HTB{m1n1ng_th31r_w4y_t0_m4rs_th3_r3d_pl4n3t}`

**Tip:** Search for `base64` or `==` (common base64 padding) to quickly find all encoded strings.
