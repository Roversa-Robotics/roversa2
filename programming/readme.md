# Roversa firmware

## Current version: 3.1.3 (released 2026-11-04)

**Download: [roversa-latest.hex](https://github.com/Roversa-Robotics/roversa2/raw/main/programming/roversa-latest.hex)**

For installation instructions, see the Roversa Classroom firmware page:
https://sites.google.com/roversa.com/roversa-classroom/troubleshooting/firmware

## What's in this folder

| File | What it is |
|------|------------|
| `roversa-latest.hex` | Always the current release. This link never changes. |
| `20261104-roversa-3.2.0.hex` | The same file, named with its release date and version. |
| `Older/` | Earlier releases, kept for reference. |

Files are named `YYYYMMDD-roversa-x.y.z.hex` (release date, then firmware version), so they sort in release order.

`Older/` may also include versions with extra diagnostics (with `-diag`) as part of the filename.

## Publishing a new release (maintainers)

1. Move the current versioned file into `Older/`. If it's already there, just remove the old file at the root.
2. Add the new build as `YYYYMMDD-roversa-x.y.z.hex` at the root and add it to the `Older/` folder as well. If there is a `diag` build, include it in the `Older/` directory.
3. Copy the new build over `roversa-latest.hex`.
4. Update the version and date at the top of this readme.
5. Do the same in the [Google Drive firmware folder](https://drive.google.com/drive/folders/1-W_BqKJKGeO4LVFnP4krqnvFep8YKf_V). You can update roversa-latest.hex there without changing its URL by using Google's Manage Versions function off the context menu. Also put the main build and the diag build in the all-versions folder there.
6. Make sure the links at https://sites.google.com/roversa.com/roversa-classroom/troubleshooting/firmware still resolve and download the correct version.

*PROTIP:* You can use this command (on a mac) to dump the version number from a roversa-latest.hex file if you're not sure what version it is...
```
python3 -c "import sys,re;d=b''.join(bytes.fromhex(l[9:-2]) for l in open(sys.argv[1]).read().split() if l[7:9]=='00');m=re.search(rb'ROVERSA,fw=([\w.+-]+)',d);print(m.group(1).decode() if m else 'no version found')" roversa-latest.hex
```