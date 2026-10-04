# Archive storage / Stockage des archives

## English

A `.lbk` archive is a **directory**, not a ZIP or a disk image:

```text
backup-<date>-<id>.lbk/
  manifest.json
  blocks/
    <sha256>.zst
```

Keep the whole directory together. The manifest describes relative paths, sizes, modification times, file hashes and ordered block references. Blocks contain Zstandard-compressed file data. SHA-256 hashes refer to the uncompressed content.

The reader accepts supported version-1 manifests marked `Verified`. That marker records a previous verification; run verification again to check the current state. Missing or corrupted blocks can prevent restoration.

History is stored separately: an archive can be opened without its original history database. Restore into a new directory using **Restaurer**. Do not edit the manifest manually.

The format is not encrypted. Paths, source information and contents may be sensitive. Hashes detect mismatches but do not protect against replacement of both the manifest and data. Restoration does not promise preservation of all NTFS metadata.

The source code is not public and this overview is not an independent recovery implementation. Keep a copy of the compatible installer with your backups and periodically test restoration. This document does not promise future compatibility or indefinite software availability.

## Français

Une archive `.lbk` est un **dossier**, pas un ZIP ni une image disque. Conservez ensemble `manifest.json` et le sous-dossier `blocks` illustrés ci-dessus.

Le manifeste décrit chemins relatifs, tailles, dates, empreintes des fichiers et références ordonnées des blocs. Les blocs sont compressés avec Zstandard ; SHA-256 porte sur les données décompressées.

Le lecteur accepte les manifestes version 1 pris en charge et marqués `Verified`. Cet état atteste d'une vérification passée : relancez la vérification pour connaître l'état actuel. Un bloc absent ou endommagé peut empêcher la restauration.

Le catalogue d'historique est indépendant : ouvrez directement une archive sans son historique d'origine, puis utilisez **Restaurer** vers un nouveau dossier. Ne modifiez pas manuellement le manifeste.

Le format n'est pas chiffré : chemins, informations de source et contenu peuvent être sensibles. Les empreintes ne protègent pas contre le remplacement simultané des données et du manifeste. La conservation de toutes les métadonnées NTFS n'est pas garantie.

Le code source n'est pas public ; cet aperçu n'est pas un outil de récupération indépendant. Gardez l'installeur compatible et testez régulièrement une restauration. Aucune compatibilité future ou disponibilité perpétuelle du logiciel n'est promise ici.
