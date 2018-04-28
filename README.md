# AutoVolatility

AutoVolatility is a script made to run reveral volatility plugins at the same time

## How to use

AutoVolatility will create a new folder in the output directory for each plugin executed.

You can run the "main" volatility plugins doing

```python
python autoVolatility.py -f MEMFILE -d OUT_DIRECTORY
``` 

Be default autoVolatility tries to execute `volatility`. If you do not have volatility executable in path or with this name, you can set where your volatility executable is using the option `-e`

```python
python autoVolatility.py -f MEMFILE -d OUT_DIRECTORY -e /home/user/tools/volatility/vol.py
```

AutoVolatility will use the plugin "imageinfo" to figure out the profile to use. But if you know the profile, you can set it using the option `-p`

```python
python autoVolatility.py -f MEMFILE -d OUT_DIRECTORY -p WinXPSP2x86
```

If you want to run almos all the default plugins that comes with volatility you can use the option `-a`

```python
python autoVolatility.py -f MEMFILE -d OUT_DIRECTORY -a
```

By default autoVolatility uses 8 threads, but you can change it with the option `-t`

```python
python autoVolatility.py -f MEMFILE -d OUT_DIRECTORY -t 16 # 16 threads
```

If want autoVolatility to run other plugins, you can do so using the option `-c`

```python
python autoVolatility.py -f MEMFILE -d OUT_DIRECTORY -c amcache,auditpol,cachedump,clipboard,cmdline,cmdscan # Only these plugins will be executed
```

The plugins executed by default are:

```python

dump_plugins = ["dumpcerts", "dumpregistry", "dumpfiles", "dumpregistry"]

plugins = ["amcache", "auditpol", "cachedump", "clipboard", "cmdline", "cmdscan", "connections", "connscan", "consoles", "deskscan", "devicetree", "dlllist",
            "envars", "getservicesids", "handles", "hashdump", "hibinfo", "hivelist", "hivescan", "iehistory", "ldrmodules", "lsadump", "malfind", "mbrparser", "memmap", "mftparser", "modules", "notepad", 
            "privs", "pslist", "psscan", "pstree", "psxview", "qemuinfo", "servicediff", "sessions", "sockets", "sockscan", "ssdt", "strings", "svcscan", "symlinkscan", "thrdscan", "verinfo", "windows", "wintree"]
```

The plugins executed using the option `-a` are:

```python
dump_plugins = ["dumpcerts", "dumpregistry", "dumpfiles", "dumpregistry"]


plugins_all = ["amcache", "apihooks", "atoms", "atomscan", "auditpol", "bigpools", "bioskbd", "cachedump", "callbacks", "clipboard", "cmdline", "cmdscan", "connections", "connscan", "consoles", "crashinfo",
                "deskscan", "devicetree", "dlldump", "dlllist", "driverirp", "drivermodule", "driverscan", "editbox", "envars", "eventhooks", "evtlogs", "filescan", 
                "gahti", "gditimers", "gdt", "getservicesids", "getsids", "handles", "hashdump", "hibinfo", "hivelist", "hivescan", "hpakextract", "hpakinfo", "idt", "iehistory", "imagecopy", "imageinfo",
                "joblinks", "kdbgscan", "kpcrscan", "ldrmodules", "lsadump", "malfind", "mbrparser", "memdump", "memmap", "messagehooks", "mftparser", "moddump", "modscan", "modules", "multiscan", "mutantscan",
                "notepad", "objtypescan", "patcher", "printkey", "privs", "procdump", "pslist", "psscan", "pstree", "psxview", "qemuinfo", "raw2dmp", "screenshot", "servicediff", "sessions", "shellbags", "shimcache",
                "shutdowntime", "sockets", "sockscan", "ssdt", "strings", "svcscan", "symlinkscan", "thrdscan", "threads", "timeliner", "timers", "truecryptmaster", "truecryptpassphrase", "truecryptsummary",
                "unloadedmodules", "userassist", "userhandles", "vaddump", "vadinfo", "vadtree", "vadwalk", "vboxinfo", "verinfo", "vmwareinfo", "volshell", "windows", "wintree", "wndscan"]


```