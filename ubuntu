### how_to_remove_all_ubuntu_packages
#### Save the script as remove.py

```
#!/usr/bin/python3

import apt

cache = apt.cache.Cache()
for package in cache:
    if (package.is_installed and
        package.candidate.priority not in ("required", "important")):
        print(package.name, end=" ")
print()
```
#### Execute as follows:
`python3 remove.py | sudo xargs apt-get remove -y`
