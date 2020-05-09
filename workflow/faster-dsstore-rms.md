
Today we were cleaning up files, and one of my buddies used this:

```bash
find . -name .DS_Store -type f -print0 | xargs -0 -n25 rm -f
```
The `-n25` stood out to me, and what it does is _execute the command with 25 parameters_, which effectively does batch `rm`s and saves a bundle on `exec()` calls.
