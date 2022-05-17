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



### How to remove all packages installed after a certain date/time?

##### specific date %yyyy-%mm-%dd replace on here, %yyyy-%mm-%dd

grep "2015-12-19.*.install " /var/log/dpkg.log | awk '{ print $4 }' | cut -d: -f1

##### You get a list of packages

##### Append them to the list of Apt command arguments with xargs:
grep "2015-12-19.*.install " /var/log/dpkg.log | awk '{ print $4 }' | cut -d: -f1 | xargs sudo apt-get --yes purge

