# Snap-Trash-Sync
Developers using Snap like VSCode or VSCodium when delete Snap moves user files from our space into snap trash space and unrecoverable without doing alot of digging.
I ran into an issue where I accidentally deleted a project file while in VSCodium and it said it moved it to my trash however I couldn't locate it. Discovered that
in all of Cononicals Wisdom I guess trash needs to be sandboxed as well as everything else I'm sure there is a security justification for this but I'm not sure how
that would with a code editor other than to be inconvient. Here is the fix.

Debian install
sudo apt install trash-cli
Move files to your ~/.local/bin/
chmod a+x ~/.local/bin/trash-list-snap
chmod a+x ~/.local/bin/sync-snap-trash
trash-list-snap # Will list out the files you currently have stored in your trash cans in snaps
sync-snap-trash # Meant to be used in a cronjob to move all snap trash files into user trash can

Create a cronjob I have mine set to run every ten minutes but you can run it manually with command sync-snap-trash if you need something immediatly.
crontab -e
*/10 * * * * /home/alex/.local/bin/sync-snap-trash
