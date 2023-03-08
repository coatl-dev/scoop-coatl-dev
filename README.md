# coatl.dev Scoop bucket

[![Tests](https://github.com/coatl-dev/scoop-coatl-dev/actions/workflows/ci.yml/badge.svg)](https://github.com/coatl-dev/scoop-coatl-dev/actions/workflows/ci.yml)
[![Excavator](https://github.com/coatl-dev/scoop-coatl-dev/actions/workflows/excavator.yml/badge.svg)](https://github.com/coatl-dev/scoop-coatl-dev/actions/workflows/excavator.yml)

Template bucket for [Scoop](https://scoop.sh), the Windows command-line installer.

## How do I install these manifests?

To add this bucket, run:

```powershell
scoop bucket add scoop-coatl-dev https://github.com/coatl-dev/scoop-coatl-dev
```

### `ignition`

To be able to download the `ignition` ZIP installer we must set a referer[^1],
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

[^1]: [HttpWebRequest.Referer Property (System.Net)](https://learn.microsoft.com/en-us/dotnet/api/system.net.httpwebrequest.referer)
