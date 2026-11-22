# tp-securite-systemes# 🛡️ TP Sécurité des Systèmes — Administration & Durcissement Windows / Linux

Travaux pratiques réalisés dans le cadre de l'UE **Cybersécurité et Cryptographie (CSE 1304)** — ISI Dakar.
Objectif du carnet : apprendre à **administrer et sécuriser** un poste Windows et un serveur Linux, de la cartographie initiale jusqu'à la supervision centralisée.

**Auteur :** Mouhamed LO — étudiant en cybersécurité, ISI Dakar

---

## 📍 TP 1.1 — Cartographie de sécurité

Audit initial d'un **poste Windows 11 Pro** et d'un **serveur Ubuntu 26.04 LTS** sur réseau isolé.
Inventaire technique et posture de sécurité, en distinguant **faits observés**, **risques** et **recommandations**.

📄 **[Lire le rapport complet (PDF)](Rapport_TP1.1_Cartographie_Securite.pdf)** · [Version Word](Rapport_TP1.1_Cartographie_Securite.docx)

### Missions couvertes
| # | Mission | Outils / Commandes |
|---|---------|--------------------|
| 1 | Identification des systèmes | `systeminfo`, `Get-NetIPConfiguration`, `hostnamectl`, `lscpu`, `/etc/os-release` |
| 2 | Comptes et privilèges | `whoami /all`, `Get-LocalUser/Group`, `id`, `getent`, `sudo -l` |
| 3 | Services et ports | `Get-Service`, `Get-NetTCPConnection`, `Get-NetUDPEndpoint`, `systemctl`, `ss -tulnp` |
| 4 | Mécanismes de sécurité | Defender, BitLocker, UFW, `sshd -T`, `apt list --upgradable` |
| 5 | Journaux | `Get-WinEvent`, `journalctl`, `/var/log/auth.log` |

### Principaux constats
- 🔴 **Ubuntu** : pare-feu **UFW inactif** alors que **SSH (22)** est exposé → à activer en priorité.
- 🟠 **Ubuntu** : 6 paquets en attente de mise à jour.
- 🟠 **Windows** : ports **SMB/NetBIOS/RPC** (135, 137-139, 445) exposés ; disque **C: non chiffré**.
- 🟢 Points positifs : **root verrouillé**, **Defender** et **AppArmor** actifs, journalisation opérationnelle, réseau isolé confirmé.

---

## 🗂️ Prochains TP (à venir)
- **TP 1.2** — Identification des vulnérabilités
- **TP 1.3** — Durcissement (hardening)
- **TP 1.4** — Audit de conformité
- **TP 1.5** — Supervision centralisée (SIEM / Wazuh)

---

## ⚙️ Environnement de laboratoire
- **Hyperviseur :** VMware Workstation Pro 17
- **Poste :** Windows 11 Pro 24H2 — `192.168.1.1/24`
- **Serveur :** Ubuntu Server 26.04 LTS — `192.168.1.2/24`
- **Réseau :** Hôte uniquement (VMnet1), **isolé d'Internet**

> ⚠️ Toutes les manipulations sont réalisées sur des machines virtuelles, sur un réseau isolé, à des fins strictement pédagogiques.
