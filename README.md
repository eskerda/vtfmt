# vtfmt: quick and friendly terminal colors for bash

`vtfmt` is yet another helper to output ANSI escape codes for colors/graphic
mode on terminals.  It can both be used as a standalone tool or directly sourced
from your bash scripts.

<img src="https://user-images.githubusercontent.com/208952/146025087-4a0e8fb7-08e4-4b55-bba4-ef8eabc72451.png" width="600">

## Usage

```bash
#!/usr/bin/env bash

source vtfmt

# direct output
echo -en "$(vtfmt bg:light-magenta fg:black bold) vtfmt $(vtfmt reset) "
echo -e "This utility is by no means $(vtfmt fg:green)feature $(vtfmt underline)complete.$(vtfmt reset) "
echo -e "And yet it can do quite some things considering how $(vtfmt bold)small$(vtfmt normal) it is!"
echo ""
declare -f vtfmt
echo ""

# or basically anywhere to compose different color modes
WARN_C="$(vtfmt bg:yellow fg:black) WARN $(vtfmt reverse) %s$(vtfmt reset)\n"
INF_C="$(vtfmt bg:green fg:black) INFO $(vtfmt reverse) %s$(vtfmt reset)\n"
ERR_C="$(vtfmt bg:red fg:black)  ERR $(vtfmt reverse) %s$(vtfmt reset)\n"

function inf  { printf "$INF_C" "$*" ; }
function err  { printf "$ERR_C" "$*" ; }
function warn { printf "$WARN_C" "$*" ; }

inf "some info"
warn "you have been warned"
err "such an error"
```
