# ReviveUSB

ReviveUSB is a free Windows tool for a USB drive or external disk that Windows suddenly asks you to format, shows as RAW, or will not open. It gets your files back first, then makes the drive usable again. Recovery only reads from the drive.

Website and full help (11 languages): https://barbellsoft.com

This repository hosts the release builds and their checksums. It is a beta: please report problems (see below).

## Download

Get `ReviveUSB.exe` from the [Releases](../../releases) page. Each release lists the SHA-256 checksum of the file.

The program is not code-signed yet, so Windows SmartScreen or your antivirus may show a warning. Before you run it, check the file against the published checksum. In PowerShell:

```powershell
Get-FileHash .\ReviveUSB.exe -Algorithm SHA256
```

If the hashes match, choose More info, then Run anyway. Reading a raw disk needs administrator rights, so the program asks for them.

## How to use

1. Run `ReviveUSB.exe`, click **Refresh**, and select your drive in the list. If Windows asks to format the drive, choose Cancel.
2. Optional but safer for a failing drive: **Back up to image** and save the image on a different drive.
3. Click **Recover files (names/paths)**. Choose **Yes** to read the selected drive, or **No** to recover from an image. Save to a folder on a healthy drive. If nothing comes back, use **Recover files (signature)**.
4. Only after your files are safe, repair the drive with **Full rebuild** (or **Format** / **Check (chkdsk)**). Repair erases the drive.
5. Run **Test drive**, then **Copy files back** to put your files on the repaired drive. Each copied file is read back and compared.

## What it can and cannot do

- Reads NTFS, FAT32 and exFAT, including drives whose boot sector or partition table is damaged (it uses the backup copies that Windows and GPT keep).
- Brings back deleted files and files from a quick-formatted drive (by file signature: photos, PDFs, Office files, videos).
- Warns when a recovered file may be wrong inside, for example when a deleted file was overwritten later.
- Cannot revive a drive whose controller has failed (it shows up as "No Media" or 0 bytes). The program tells you when that is the case.

## Report a problem

Open an issue in this repository. Include your Windows version, the drive's name and size, and the text from the log window (or the **Copy diagnosis** button).

## License

Copyright (c) 2026 Barbellsoft. All rights reserved.

Anyone, including companies and organizations, may use ReviveUSB free of charge on any number of computers. You may redistribute the original, unmodified `ReviveUSB.exe` free of charge, including on software download sites and on storage media. Don't modify it, wrap it in another installer or download manager, bundle it with other software or offers, or charge for it.

## Disclaimer

ReviveUSB is provided as is, with no warranty of any kind. Recovery is never guaranteed, and the repair commands erase data permanently. You use the program at your own risk. The author is not liable for data loss or any other damage that results from using it. Keep backups of anything important.
