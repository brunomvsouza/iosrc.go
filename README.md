## iOS restriction password recoverer

[![Pipeline status](https://lab.bmvs.io/bs/iosrc.go/badges/master/pipeline.svg)](https://lab.bmvs.io/bs/iosrc.go/commits/master) [![Pipeline status](https://ci.appveyor.com/api/projects/status/yd76vgs1tl80v4g3/branch/master?svg=true)](https://ci.appveyor.com/project/brunomvsouza/iosrc-go/branch/master) [![Coverage Status](https://lab.bmvs.io/bs/iosrc.go/badges/master/coverage.svg)](https://lab.bmvs.io/bs/iosrc.go/commits/master) [![Go Report Card](https://goreportcard.com/badge/lab.bmvs.io/bs/iosrc.go)](https://goreportcard.com/report/lab.bmvs.io/bs/iosrc.go) [![GoDoc Reference](https://godoc.org/go.bmvs.io/iosrc?status.svg)](http://godoc.org/go.bmvs.io/iosrc)

### Step 1: Create a backup

Make sure you have an **unencrypted** backup of you device.

### Step 2: Find restriction `key` and `salt` on the created backup

You'll be able to find the values for `key` and `salt` on the file below
```
~/Library/Application\ Support/MobileSync/Backup/<BACKUP_HASH>/398bc9c2aeeab4cb0c12ada0f52eea12cf14f40b
```

It will look something like:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>RestrictionsPasswordKey</key>
	<data>
	aI9gkP3NEG+LLL8UPyAT1ehRd7g=
	</data>
	<key>RestrictionsPasswordSalt</key>
	<data>
	hpOLll==
	</data>
</dict>
</plist>
```

### Step 3: Execute the password cracker

```bash
# example for the example file below would be
./cli -key aI9gkP3NEG+LLL8UPyAT1ehRd7g= -salt hpOLll==
```

### Disclaimer

This repo is 100% inspired on http://ios7hash.derson.us. It was created because
I needed to recover an iPad restriction password and the implementation of the
original author wasn't fast enough (even for this small key space) due to running
on browsers.
