# coatl.dev Scoop bucket

[![Tests](https://github.com/coatl-dev/scoop-coatl-dev/actions/workflows/ci.yml/badge.svg)](https://github.com/coatl-dev/scoop-coatl-dev/actions/workflows/ci.yml)

Template bucket for [Scoop](https://scoop.sh), the Windows command-line installer.

## How do I install these manifests?

To add this bucket, run:

```powershell
scoop bucket add scoop-coatl-dev https://github.com/coatl-dev/scoop-coatl-dev
```

### `coatl310`

Windows installer for Python 3.10.12 and beyond.

>According to the release calendar specified in [PEP 619], Python 3.10 is now in
>the "security fixes only" stage of its life cycle: 3.10 branch only accepts
>security fixes and releases of those are made irregularly in source-only form
>until October 2026. Python 3.10 isn't receiving regular bug fixes anymore, and
>binary installers are no longer provided for it.

To install:

```powershell
scoop install coatl310
```

To uninstall:

```powershell
scoop uninstall --purge coatl310
```

### `ignition`

To be able to download the `ignition` ZIP installer we must set a [referer],
so first we must edit our `scoop`'s `config.json`, which is typically found at
`%USERPROFILE%\.config\scoop\config.json`, and add or edit the `private_hosts`
section:

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

Finally:

```powershell
scoop install ignition
```

To uninstall:

```powershell
scoop uninstall --purge ignition
```

### `jython`

Since `jython` depends on Java, we recommend `java/zulu11-jre`, which can be installed by...

Adding the `java` bucket:

```powershell
scoop bucket add java
```

Then:

```powershell
scoop install zulu11-jre
```

And finally:

```powershell
scoop install jython
```

To uninstall:

```powershell
scoop uninstall jython
```

## How do I contribute new manifests?

To make a new manifest contribution, please read the [Contributing Guide](https://github.com/ScoopInstaller/.github/blob/main/.github/CONTRIBUTING.md).

[referer]: https://learn.microsoft.com/en-us/dotnet/api/system.net.httpwebrequest.referer
[PEP 619]: https://www.python.org/dev/peps/pep-0619/
