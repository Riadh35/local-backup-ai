# Local Backup AI

Sauvegarde et restauration de fichiers **100 % locale**, sans cloud et sans compte. Application Windows native (WPF), en français.

Ce dépôt distribue uniquement le **programme d'installation compilé** — le code source n'est pas publié.

## Télécharger

Allez dans l'onglet **[Releases](../../releases/latest)** et téléchargez `LocalBackupAI-Setup.msi`.

## Fonctionnalités

- **Sauvegarde de fichiers** : archives `.lbk` (manifeste versionné, blocs compressés Zstandard, empreintes SHA-256).
- **Restauration** : restauration complète ou fichier par fichier, jamais d'écrasement des fichiers existants.
- **Vérification d'intégrité** : recalcul et comparaison des empreintes SHA-256 à la demande.
- **Disques et volumes** : inventaire Windows en lecture seule (aucune modification des partitions).
- **Clonage** : disque complet, partition, ou disque virtuel VHD/VHDX (mode expérimental, disques secondaires hors ligne).
- **Média de secours WinPE** : construit une clé USB/DVD de démarrage pour ouvrir et vérifier une archive `.lbk` même si Windows ne démarre plus (nécessite le Windows ADK).
- **Assistant local** : répond aux questions sur l'usage de l'application via un modèle Ollama installé en local (optionnel, 100 % local, n'agit jamais sur vos données).
- **Historique** : suivi des opérations de sauvegarde, restauration et clonage.

## Prérequis

- Windows 10/11 (64 bits).
- Droits administrateur recommandés pour VSS, l'inventaire disque et le clonage.
- Windows ADK + add-on WinPE (optionnel, uniquement pour construire un média de secours).
- [Ollama](https://ollama.com) (optionnel, uniquement pour l'assistant local).

## Confidentialité

Aucune donnée n'est envoyée sur un serveur distant. Toutes les opérations (sauvegarde, restauration, clonage, assistant local) s'exécutent entièrement sur votre machine.

## Soutenir le projet

[paypal.me/ryad36](https://paypal.me/ryad36)

---

Créé par Riadh BEN KHALED.
