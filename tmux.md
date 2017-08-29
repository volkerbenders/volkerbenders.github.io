# Links regarding tmux

## What is it?

It's a tool to split your terminal into multiple screens (visible at the same time) and to make your session independent from the current login.

I always forget the cryptic shortcuts and i don't want to google them every time - that make me feel - uh - not so clever ;-)

## Controls

|Purpose | Command|
|---|---|
|Detach|^b d|
|List| ^b =|
|Buffer|^b <Page up / down>|
|Command |^b : <command>|
|||
|Copy|^b [ ... <space> ... <return>|

## Window Management

|Purpose | Command|
|---|---|
|List|^b w|
|Create| ^b c|
|Rename|^b , <name>|
|Command |^b : <command>|
|Last|^b l|
|Close|^b &|
|Goto #| ^b <0-9>|
|Next|^b n|
|Previous|^b p|

## Panes (Split Window)

|Purpose | Command|
|---|---|
|Show #|^b q|
|Split horizontal| ^b "|
|Split vertical| ^b %|
|Pane -> Window|^b !|
|Kill |^b x|

## Pane Movement

|Purpose | Command|
|---|---|
|Select|^b <arrow>|
|Previous| ^b {|
|Next| ^b }|  
|Switch| ^b o|
|Swap| ^b ^o|
|Last| ^b ;|
