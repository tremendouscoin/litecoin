Building Tremendouscoin on Windows
---------

You are basically following [the instructions from litecoin](../doc/build-windows.md)

### HINT 1:

However you may have trouble unless you have run this command:

```
PATH=$(echo "$PATH" | sed -e 's/:\/mnt.*//g') # strip out problematic Windows %PATH% imported var
```

... slightly before you run this command ```make HOST=x86_64-w64-mingw32```

(kind of as per @ https://github.com/bitcoin/bitcoin/blob/0.15/doc/build-windows.md)

### HINT 2:

Ridiculously enough, you may need to manually (as a human) click the "OK" button on your PC
when a "conftest.exe - System Error" box appears in the middle of your compiling
(while it's on the "clock_gettime_monotonic") step.
No biggie, just do it!
