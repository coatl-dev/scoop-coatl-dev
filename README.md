# coatl.dev Scoop bucket

[![Tests](https://github.com/coatl-dev/scoop-coatl-dev/actions/workflows/ci.yml/badge.svg)](https://github.com/coatl-dev/scoop-coatl-dev/actions/workflows/ci.yml)

coatl-dev's bucket for [Scoop](https://scoop.sh), the Windows command-line installer.

## How do I install these manifests?

To add this bucket, run:

```powershell
scoop bucket add coatl-dev https://github.com/coatl-dev/scoop-coatl-dev
```

### `ignition`/`ignition81`

To be able to download the `ignition` or `ignition81` ZIP installer we must set
a [referer], so first we must edit our `scoop`'s `config.json`, which is
typically found at `%USERPROFILE%\.config\scoop\config.json`, and add or edit
the `private_hosts` section:

```json
{
  "lastUpdate": "2022-09-09T15:41:41.2176701-07:00",
  "SCOOP_REPO": "https://github.com/ScoopInstaller/Scoop",
  "SCOOP_BRANCH": "master",
  "private_hosts": [
    {
      "match": "https://files.inductiveautomation.com/*",
      "headers": "Referer=https://inductiveautomation.com/"
    }
  ]
}
```

To install:

```powershell
scoop install coatl-dev/ignition
```

Or

```powershell
scoop install coatl-dev/ignition81
```

To uninstall:

```powershell
scoop uninstall --purge ignition
```

Or

```powershell
scoop uninstall --purge ignition81
```

### `jython`

Since `jython` depends on Java, we recommend `java/zulu17-jre`, which can be installed by...

Adding the `java` bucket:

```powershell
scoop bucket add java
```

Then:

```powershell
scoop install zulu17-jre
```

And finally:

```powershell
scoop install coatl-dev/jython
```

To uninstall:

```powershell
scoop uninstall jython
```

### Python

```powershell
scoop install coatl-dev/python27
```

```powershell
scoop install coatl-dev/python312
```

```powershell
scoop install coatl-dev/python313
```

```powershell
scoop install coatl-dev/python314
```

## How do I contribute new manifests?

To make a new manifest contribution, please read the [Contributing Guide].

[Contributing Guide]: https://github.com/ScoopInstaller/.github/blob/main/.github/CONTRIBUTING.md
[referer]: https://learn.microsoft.com/en-us/dotnet/api/system.net.httpwebrequest.referer
