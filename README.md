
installs and configure `scanbd` on **my** RasPi.




## build from source

### build errors


```
scanbd.c: In function 'main':
scanbd.c:354:5: error: 'strncpy' specified bound 4096 equals destination size [-Werror=stringop-truncation]
     strncpy(prog_path, argv[0], PATH_MAX);
```
```
config.c: In function 'cfg_do_parse':
config.c:117:5: error: 'strncpy' specified bound 4096 equals destination size [-Werror=stringop-truncation]
     strncpy(config_file, config_file_name, PATH_MAX);
```
```
slog.c: In function 'slog_init':
slog.c:33:5: error: 'strncpy' specified bound 2048 equals destination size [-Werror=stringop-truncation]
     strncpy(lpre, string, LINE_MAX);
```

```
src/scanbd/scanbd.c:354:

- strncpy(prog_path, argv[0], PATH_MAX);
+ strncpy(prog_path, argv[0], PATH_MAX -1);
```

```
src/scanbd/config.c:117:

- strncpy(config_file, config_file_name, PATH_MAX);
+ strncpy(config_file, config_file_name, PATH_MAX -1);
```

```
src/scanbd/slog.c:33:

- strncpy(lpre, string, LINE_MAX);
+ strncpy(lpre, string, LINE_MAX -1);
```
