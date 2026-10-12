# 🛡️ Home SOC Lab — Journal de progression

**Élève :** Heritier Lengelo Fundji
**Mentor :** Gracias 🦊 (SOC Senior / Enquêteur Numérique)
**Objectif :** Analyste SOC Junior + Enquêteur Virtuel — certification **BTL1 (Blue Team Level 1)**
**Format :** 1 h / jour → 45 min pratique + 15 min débrief + note

---

## 🖥️ Architecture du labo (validée Jour 1)

| Rôle | VM | OS | Rôle SOC |
|---|---|---|---|
| SIEM / Manager (cerveau) | `SOC-ROCKY-SIEM` | Rocky Linux | Collecte + corrélation + alertes |
| Endpoint supervisé (victime) | `SOC-WIN-VICTIM` | Windows 10/11 + Sysmon | Télémétrie à analyser |
| Attaquant | `SOC-KALI-ATTACK` | Kali Linux | Génère du trafic malveillant |

**Réseau :** `Internal Network` isolé (zéro Internet) + carte `Host-Only` si besoin.
❌ **Interdit :** NAT / Bridged pour Kali et Windows (danger réel).
→ Rocky : 2e carte NAT **temporaire** uniquement pour télécharger Wazuh, puis coupée.

**Matériel hôte :** Windows / Core i7 24 cœurs / 64 GB RAM / 900 GB libre / VirtualBox

---

## 📅 Progression

### Mois 1 — Installation & architecture

| Jour | Date | Sujet | Note | Statut |
|:---:|:---:|---|:---:|:---:|
| 1 | 2026-10-12 | Installation & architecture du Home Lab SOC | **14/20** | ✅ |

---

### 📓 Détail Jour 1 — 2026-10-12

**Objectif :** poser les fondations / architecture réseau.

**Acquis :**
- ✅ Risque offensif : Kali sur le vrai réseau = un faux pas frappe les vraies machines.
- ✅ Réseau plat = pas de cloison → une attaque se propage à toutes les machines. Il faut **segmenter**.
- ✅ Windows infecté + Internet = double menace (sortant C2 / entrant prise de contrôle) → exfiltration de données.
- ✅ Découpage des rôles : Rocky = SIEM, Kali = attaquant, Windows = victime.

**À revoir :**
- Vocabulaire : **SIEM**, **segmentation**, **NAT / Bridged / Host-Only / Internal**.
- Orthographe : *réseau* (avec é).
- Retourner proprement la phrase 2 (double menace Windows).

**Défi → Jour 2 :** créer et nommer les 3 VMs, en justifiant **RAM/CPU** et **type de réseau** de chacune AVANT de cliquer « Create ».

**QCM entrevue Jour 1 :**
1. SIEM = Security Information and Event Management
2. Réseau segmenté > plat : confinement / pas de propagation
3. Mode à bannir pour Kali : NAT (et surtout Bridged)
4. Faux : Wazuh Manager → Rocky Linux (stable, serveur), pas Kali (offensif).

---

## 🔑 Vocabulaire clé (à maîtriser en entrevue)

- **SIEM** : Security Information and Event Management — collecte, corrèle et alerte.
- **Sysmon** : endpoint Windows, télémétrie riche (process, réseau, fichiers).
- **Segmentation réseau** : cloisonner pour confiner une attaque.
- **Flat network** : tout communique librement → l'ennemi du SOC.
- **C2 (Command & Control)** : serveur qui pilote un malware.
- **Wazuh** : SIEM + HIDS open source.
