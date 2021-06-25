# Default Commits

### Stopping them (from [here](https://glitch.com/edit/#!/stop-default-commits?path=README.md%3A1%3A0))

Here's the script if the project gets deleted or hit with many requests.

```bash
echo '#!/bin/sh
#       if the prepared commit message ends with "Checkpoint", abort the commit
if grep -q "Checkpoint$" "$1"; then
        echo "Skipping default commit" >> /tmp/message
        exit 1
fi' > /app/.git/hooks/prepare-commit-msg && chmod +x /app/.git/hooks/prepare-commit-msg
```

### Re-enabling them

```bash
rm -rf /app/.git/hooks/prepare-commit-msg
```
