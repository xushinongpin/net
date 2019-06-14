编辑 /usr/bin/google-chrome

```
在
exec -a "$0" "$HERE/chrome" "$@"
后面添加  --user-data-dir --no-sandbox
exec -a "$0" "$HERE/chrome" "$@" --user-data-dir --no-sandbox
```



