
Drastically reduce of compilation speed then use tsconfig.json target  >ES6 and zod 3.20.6
It also reduce speed of autocompletion in VSCode.



```bash
# TARGET ES6
yarn tsc -P tsconfig.json

# Files:               30
# Lines:            27142
# Identifiers:      47488
# Symbols:          46494
# Types:           212482
# Instantiations:   32801
# Memory used:    161617K
# I/O read:         0.00s
# I/O write:        0.00s
# Parse time:       0.28s
# Bind time:        0.11s
# Check time:       1.92s
# Emit time:        0.01s
# Total time:       2.31s

```

change target  to ESNext

```bash
# TARGET ESNext
yarn tsc -P tsconfig.json

# Files:               73
# Lines:            30504
# Identifiers:      49821
# Symbols:          48523
# Types:           259144
# Instantiations:   32813
# Memory used:    164531K
# I/O read:         0.00s
# I/O write:        0.00s
# Parse time:       0.31s
# Bind time:        0.12s
# Check time:       2.71s
# Emit time:        0.01s
# Total time:       3.15s

```

change target  to ES5

```bash
# TARGET ES5
yarn tsc -P tsconfig.json

# Files:               19
# Lines:            24743
# Identifiers:      44395
# Symbols:          43392
# Types:           125049
# Instantiations:   32768
# Memory used:    121242K
# I/O read:         0.00s
# I/O write:        0.00s
# Parse time:       0.26s
# Bind time:        0.10s
# Check time:       0.94s
# Emit time:        0.01s
# Total time:       1.30s

# ~60% faster than target ES6, ~119% faster than target ESNext

```



If we downgrade zod to version 3.19.1 



```bash
# TARGET ES6

yarn tsc -P tsconfig.json

# Files:              30
# Lines:           26929
# Identifiers:     47028
# Symbols:         38733
# Types:            4935
# Instantiations:  14029
# Memory used:    67795K
# I/O read:        0.00s
# I/O write:       0.00s
# Parse time:      0.28s
# Bind time:       0.11s
# Check time:      0.15s
# Emit time:       0.01s
# Total time:      0.55s
# about 0.65 seconds on my hardware

```

```bash
# TARGET ESNext

yarn tsc -P tsconfig.json

# Files:              73
# Lines:           30291
# Identifiers:     49361
# Symbols:         40325
# Types:            4945
# Instantiations:  14037
# Memory used:    72181K
# I/O read:        0.00s
# I/O write:       0.00s
# Parse time:      0.32s
# Bind time:       0.12s
# Check time:      0.15s
# Emit time:       0.01s
# Total time:      0.60s

```

```bash
# TARGET ES5

yarn tsc -P tsconfig.json

# Files:              19
# Lines:           24530
# Identifiers:     43935
# Symbols:         36612
# Types:            4919
# Instantiations:  14005
# Memory used:    65507K
# I/O read:        0.00s
# I/O write:       0.00s
# Parse time:      0.26s
# Bind time:       0.10s
# Check time:      0.15s
# Emit time:       0.01s
# Total time:      0.52s

```

almost no difference and increase speed compare to latest version

