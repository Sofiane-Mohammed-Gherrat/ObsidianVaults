
# Redirection

>**Direct the channels of a proc** or **feed into the stdin** channel

```Shell
proc 1> file.txt
proc 2> file.txt
proc < file.txt
```
## Each process (Program) has 3 Channels:

```SQL
stdin  -> 0
stdout -> 1
stderr -> 2
```

# Piping

>A way of **chaining processes**

```Shell
proc1 | proc2 | proc3
```

```Shell
ps aux | less   # makes the output dynamicly scrollable 

# a -> list all usr
# u -> convert usr id to usr names
# x -> show ttys
```

# && ( Logical AND )

```Shell
proc1 && proc2
```

>If proc1 is **True exec** proc2

---
# Examples
## Cut command 

```Shell
-> cat cuttest.txt
name:sofiane
age:23
uni:Xiamen
```

```Shell
-> cat cuttest.txt | cut -d: -f2
sofiane
23
Xiamen
```

---
# Some Commands 

```Shell
-> sort
-> cat cuttes.txt | sort -bf 
```

```Shell
-> wc   # word count
```

```Shell
-> grep
-> cat cuttest.txt | grep name
-> grep name ./* | cut -d: -f1
```

