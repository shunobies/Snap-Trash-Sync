# Snap-Trash-Sync

## Overview

When using snapped versions of VSCode or VSCodium, deleted files are moved to a sandboxed trash directory that is difficult to access. If you accidentally delete a file, you may struggle to locate it in the snap trash space without extensive manual searching.

Snap implements sandboxed storage for security reasons, but this approach is inconvenient for development workflows. This tool provides an easy way to recover files by syncing snap trash to your system trash.

## Installation

First, install `trash-cli`:

```bash
sudo apt install trash-cli
```

Copy the script files to your local bin directory:

- `trash-list-snap`
- `sync-snap-trash`

Make both scripts executable:

```bash
chmod a+x ~/.local/bin/trash-list-snap
chmod a+x ~/.local/bin/sync-snap-trash
```

## Usage

List files in your snap trash:

```bash
trash-list-snap
```

Sync snap trash files to your system trash:

```bash
sync-snap-trash
```

## Automate with Cron

Set up a cron job to automatically sync snap trash at regular intervals. For example, to run every ten minutes:

```bash
crontab -e
```

Add the following line:

```bash
*/10 * * * * /home/alex/.local/bin/sync-snap-trash
```

Adjust the path to match your home directory and modify the interval as needed. Run `sync-snap-trash` manually whenever you need to recover a file immediately.
