# Local Backup AI

**Back up and restore your files on Windows. No cloud. No account.**

[Download for Windows x64](https://github.com/Riadh35/local-backup-ai/releases/latest/download/LocalBackupAI-Setup.msi) · [Français](README.fr.md) · [Test results](VALIDATION.md) · [Report a problem](https://github.com/Riadh35/local-backup-ai/issues)

Native Windows application with a **French interface**. English documentation is available; an English application interface is not included in v0.1.0. The optional AI assistant is not required for backup or restore.

This repository distributes the compiled installer and documentation. **The application source code is not published.**

<p align="center"><img src="screenshots/1-vue-ensemble.png" width="90%" alt="Local Backup AI dashboard in French" /></p>

## Try a small backup and restore

1. Open the [latest release](https://github.com/Riadh35/local-backup-ai/releases/latest) and download **LocalBackupAI-Setup.msi** from Assets. The automatically generated source ZIP is not the application.
2. Install on Windows 10/11, 64-bit. The current MSI is **not digitally signed**; Windows may show an unknown-publisher or reputation warning. Follow your organization's security policy.
3. In **Sauvegarder** (Back up), add a small folder of sample files, choose a destination outside that folder, then select **Créer la sauvegarde**.
4. In **Restaurer** (Restore), open the resulting `.lbk` folder and select **Vérifier l’intégrité**.
5. Restore into a new folder and compare with your samples before relying on the application for important files.

Keep backups on a separate physical device. Preserve the **whole `.lbk` directory**, not only its manifest. See [archive storage and recovery](ARCHIVE_FORMAT.md).

## Features and boundaries

| Feature | Scope |
|---|---|
| File backup | Local `.lbk` directories, versioned manifest, Zstandard blocks, SHA-256 checks |
| Restore | All files or one selected file into a new directory, without overwriting existing files |
| Integrity verification | Re-read archive data and compare hashes on demand |
| Disk inventory | Read-only Windows disk and volume information |
| VHD/VHDX copying | Copy a standalone, offline, unmounted container to a new file and verify its hash |
| VSS | Experimental snapshots for open files; elevation required; a snapshot failure stops that backup |
| Physical disk / partition cloning | Experimental; destroys the selected destination's contents, secondary offline disks only, explicit confirmation required |
| WinPE recovery media | Build a bootable ISO using Windows ADK + WinPE add-on; does not directly write a USB drive |
| Local assistant | Optional Ollama-based help; cannot execute backup, restore or clone operations |

This is not an active Windows system-image backup or migration tool. Scheduling and encryption are not available. File backup does not promise preservation of NTFS permissions, alternate data streams or links. Integrity hashes are not encryption or proof of authenticity.

The [validation report](VALIDATION.md) distinguishes actual operations from simulated integrations. Evaluate experimental features on disposable data.

## Screenshots

<p align="center">
  <img src="screenshots/2-sauvegarder.png" width="45%" alt="File backup screen" />
  <img src="screenshots/3-disques.png" width="45%" alt="Read-only disk inventory" />
</p>
<p align="center">
  <img src="screenshots/4-clonage.png" width="45%" alt="Cloning options" />
  <img src="screenshots/5-media-secours.png" width="45%" alt="WinPE ISO builder" />
</p>

## Requirements and privacy

- Windows 10/11 x64. See the validation report for environments actually tested.
- Administrator approval for installation and features requiring elevated Windows access, including VSS and physical cloning.
- Windows ADK + WinPE add-on only for building recovery media.
- [Ollama](https://ollama.com) and a downloaded model only for the optional assistant.

Backup, verification, restore and cloning run locally. The optional assistant communicates with local Ollama. Installing optional tools and downloading a model require Internet access; external links open those services separately.

## Installer integrity

For **v0.1.0**, `LocalBackupAI-Setup.msi` is 66,519,559 bytes. SHA-256:

```text
518ddb827f02a87c1117c3f280d7f2d2ec5589ef98bc3065adb730c1d5f5ce7c
```

Check with `Get-FileHash .\LocalBackupAI-Setup.msi -Algorithm SHA256`. A matching hash confirms the file matches this release; it does not replace code signing or a security audit.

## Feedback and support

[Open an issue](https://github.com/Riadh35/local-backup-ai/issues) with your Windows version, application version, steps to reproduce and error message. Remove personal paths and sensitive data from logs and screenshots. English and French reports are welcome.

Created by **Riadh BEN KHALED**. [Support development](https://paypal.me/ryad36).
