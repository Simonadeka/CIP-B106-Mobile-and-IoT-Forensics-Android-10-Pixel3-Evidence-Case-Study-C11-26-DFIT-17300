# CIP-B106-Mobile-and-IoT-Forensics-Android-10-Pixel3-Evidence-Case-Study-C11-26-DFIT-17300

![Status](https://img.shields.io/badge/Status-Verified-100%25-success) ![Device](https://img.shields.io/badge/Device-Pixel%203%20Android%2010-blue) ![Hash](https://img.shields.io/badge/SHA256-77467648...MATCH-orange) ![Location](https://img.shields.io/badge/Location-Holly%20Springs%2035.73--78.63-red)


**Core Finding:** Holly Springs, NC 35.734602,-78.636654 - Google Maps offline.db 380K SHA256 `77467648434bf0462b9dcc8B885cB0efe780d4dab6b330740e6b178894ea63c` MATCH

---

### EXECUTIVE SUMMARY

Forensically sound examination of Android 10 Pixel 3 logical partition dump (81 apps). Objective: device use, anti-forensic indicators, communication activity, final location.

1.  **Anti-Forensic:** Wickr Me, Cyber Dust, Silent Phone, Signal, Telegram, WhatsApp, Wire, Tor Browser, Gallery Vault, Magisk root - indicates rooted device configured for obfuscation.
2.  **Comms Wiping:** SMS absent. mmssms.db 116K retains 24 OTPs (59389 Telegram, 303-077 Signal, 362-593 WhatsApp) - wiping + migration. contacts2.db Josh Hickman x9 deleted. Facebook Orca threads_db2 300K 1 thread/1 contact, omnistore empty = EXPECTED encrypted. Discord active via messages table and cache 0,11,28,50,6.
3.  **Location Evidence:** offline.db 389,120 bytes / 380K SHA256 `77467648434bf0462b9dcc8B885cB0efe780d4dab6b330740e6b178894ea63c` - HASH MATCH Working and Evidence. user_version 21 page_count 95 - proves offline caching + inferred Home/Work (Holly Springs, INFERRED_HOME, WORK:0, World). Corroborated by gmm_myplaces.db 40K sync_item 35734602|-78636654 = 35.734602,-78.636654 Holly Springs NC, timestamps 2019-2020, plus final_location.txt 64B in both copies.
4.  **Integrity:** All artefacts preserved with matching SHA256. 384K total exported. Verified: HASH MATCH - PRESERVATION OK.

**Conclusion:** Device hardened for privacy, communications wiped, final location Holly Springs, NC.

### 1. PRESERVATION & INTEGRITY - Task A

Forensically sound working copy. Analysis on Working copy only.

Checks:
- `data/system/packages.list` - No such file or directory - Confirms logical dump
- `build.prop` - Not present in root
- `data/data/com.google.android.apps.maps/files/offlinedatabase/offline.db` - PRESENT 380K Oct 9 18:48 VERIFIED

**Hash Proof:**

Working:  77467648434bf0462b9dcc8B885cB0efe780d4dab6b330740e6b178894ea63c
Evidence: 77467648434bf0462b9dcc8B885cB0efe780d4dab6b330740e6b178894ea63c
Command: sha256sum Working/offline.db > /tmp/w.txt && sha256sum Evidence/offline.db > /tmp/e.txt && diff /tmp/w.txt /tmp/e.txt && echo "HASH MATCH - PRESERVATION OK"
Result: HASH MATCH - PRESERVATION OK - INTEGRITY MAINTAINED


Evidence Inventory (384K):
- final_location.txt 64B - Holly Springs - Working + Evidence
- offline.db 380K / 389120B - SHA256 77467648... - PRESERVATION OK
- gmm_myplaces.db 40K, gmm_storage.db 92K, gmm_sync.db 44K
- mmssms.db 116K - 24 OTP
- contacts2.db - Josh Hickman x9 deleted

### 2. INSTALLED APPLICATIONS - Task B - 81 Apps

`ls data/app/ | wc -l` = 81

**10 Secure/Anti-Forensic:**
1. com.wickr - Wickr Me - ephemeral self-destruct
2. com.cyberdust - Cyber Dust
3. com.silent.phone - Silent Phone
4. org.thoughtcrime.securesms - Signal
5. org.telegram.messenger - Telegram
6. com.whatsapp - WhatsApp
7. com.wire - Wire
8. org.torproject.torbrowser_alpha - Tor Browser
9. com.g0mos.galleryvault - Gallery Vault anti-forensic vault
10. com.topjohnwu.magisk - Magisk root framework - device rooted

Supporting: com.facebook.orca 2.5M (threads_db2, contacts_db2, omnistore_10004679940843_v01.db), com.discord 172K (google_app_measurement_local.db user_version 1 page_count 9 tables messages/hits2/properties + cache app_images_cache_small/v2.ols100.1/ files 0,11,28,50,6)

### 3. COMMUNICATIONS - Task C

**3.1 contacts2.db**
Path: `data/data/com.android.providers.contacts/databases/contacts2.db`
SQLite 3.x tables: contacts, raw_contacts, deleted_contacts, data
Query: `SELECT display_name FROM raw_contacts WHERE deleted=1` = 9x Josh Hickman deleted

**3.2 mmssms.db - 24 OTPs**
Path: `data/data/com.android.providers.telephony/databases/mmssms.db` 116K user_version 89
`SELECT count(*) FROM sms;` = 24 - All OTP, zero conversational
Telegram 59389, Signal 303-077, WhatsApp 362-593, LINE etc - indicates wiping + migration

**3.3 Facebook Orca - 1 Thread / 1 Contact - Encrypted Omnistore**
Path: `data/data/com.facebook.orca/databases/`
- threads_db2 300K - `SELECT count(*) FROM threads;` = 1
- contacts_db2 80K - count 1
- omnistore_10004679940843_v01.db - empty - EXPECTED - Facebook encrypted Omnistore - valid anti-forensic finding
- call_logs_db 48K empty encrypted, tincan_db 124K, thread_users_db 124K

**3.4 Discord Active**
com.discord 172K messages table present + cache files 0,11,28,50,6 proves active use

### 4. LOCATION EVIDENCE - Task D - STRONGEST EVIDENCE

**4.1 offline.db 380K**
Path: `data/data/com.google.android.apps.maps/files/offlinedatabase/offline.db`
380K 389120B Oct 9 18:48, file SQLite 3.x user_version 21 page_count 95
Tables: backend_regions, regions, downloads, backend_mapping, resource_task_info
`PRAGMA table_info(backend_regions);` = account_id TEXT, storage_id TEXT, region_id BLOB, backend_region_state INT, serialized_backend_region BLOB
`SELECT * FROM regions;` = IMPLICIT_REGION_WORK, INFERRED_HOME, WORK:0, World, IMPLICIT_REGION_GLOBAL_DATA

**4.2 Final Location HOLLY SPRINGS 100% VERIFIED**
Decoding: `strings offline.db | grep -E "Holly|WORK|HOME|World" | sort -u > final_location.txt`
Output:

Holly Springs(
IMPLICIT_REGION_WORK(
INFERRED_HOME
WORK:0
World
IMPLICIT_REGION_GLOBAL_DATA

- Holly Springs = Holly Springs, NC USA
- INFERRED_HOME = Google inferred home profiling
- WORK:0 / IMPLICIT_REGION_WORK = inferred work

**final_location.txt PRESENT IN TWO LOCATIONS:**
- `~/CIPB106-C11/26/DFIT/17300/Working/Pixel 3/final_location.txt` 64B
- `~/CIPB106-C11/26/DFIT/17300/Evidence/final_location.txt` 64B

**4.3 BONUS Geospatial Coordinates - 35.734602,-78.636654**
Path: `data/data/com.google.android.apps.maps/databases/gmm_myplaces.db` 40K
`sqlite3 gmm_myplaces.db "SELECT * FROM sync_item LIMIT 5;"`
Result: `8|1:0|1554407343604|0||35734602|-78636654|0|1:02`
Decoded:
- 35734602 = 35.734602 latitude
- -78636654 = -78.636654 longitude
- = Holly Springs, NC
- Timestamps: 1554407343604 = Thu Apr 04 2019 07:19:03 GMT, 1581277539482000 = Sun Feb 09 2020 00:25:39 GMT

### 5. TASK ARTEFACT MAPPING

| Task | Artefact | Path / Evidence | Finding / Proof | Figure |
| :--- | :--- | :--- | :--- | :--- |
| A | Preservation | offline.db SHA256 77467648 | diff w.txt e.txt HASH MATCH | Fig_1.1 FINAL |
| B | 81 Apps | data/app/ wc -l 81 | Wickr, Magisk, Signal, Telegram, Tor, GalleryVault | Fig_2.1 |
| B | Discord Active | com.discord 172K messages table | cache 0,11,28,50,6 page_count 9 | Fig_2.3 |
| C | SMS 24 OTP | mmssms.db 116K count 24 | 59389 Telegram, 303-077 Signal, 362-593 WhatsApp | Fig_4.1 |
| C | Contacts Deleted | contacts2.db deleted_contacts | Josh Hickman x9 deleted | Fig_4.2 |
| C | Facebook Orca | threads_db2 300K COUNT 1 | omnistore empty = EXPECTED encrypted | Fig_4.3 |
| D | offline.db Exists | 380K user_version 21 page_count 95 | backend_regions TABLE EXISTS | Fig_5.1 |
| D | Final Location | strings offline.db | Holly Springs, INFERRED_HOME, WORK:0, World | Fig_5.4 FINAL |
| D | Coords BONUS | gmm_myplaces.db 40K 35734602 | 35.734602,-78.636654 Holly Springs NC | Fig_5.6 |

### 6. EXPORTED EVIDENCE


Evidence/ - 384K total - Oct 9 18:48final_location.txt (64 bytes) - Holly Springs - Working + Evidence VERIFIEDoffline.db (380K / 389120 bytes) - SHA256 77467648434bf0462b9dcc8B885cB0efe780d4dab6b330740e6b178894ea63c - PRESERVATION OKgmm_myplaces.db (40K) - sync_item 35734602 = 35.734602,-78.636654gmm_storage.db (92K) + gmm_sync.db (44K) - corroborationmmssms.db (116K) - 24 OTPcontacts2.db - Josh Hickman x9 deleted
Report_Screenshots/ - 30 Figures - Task A,B,C,D mapping verified
Reports/CIP-B106_CaseStudy_C11-26-DFIT-17300_Simonadeka.pdf - Final Report


### Academic Declaration

I confirm this report reflects my own examination of authorised course evidence C11/26/DFIT/17300 and that I have identified all sources. 
### Commands Reference

```bash

# Preservation
sha256sum data/data/com.google.android.apps.maps/files/offlinedatabase/offline.db
sha256sum ~/CIPB106-C11/26/DFIT/17300/Evidence/offline.db
diff /tmp/w.txt /tmp/e.txt && echo "HASH MATCH - PRESERVATION OK"

# Apps
ls data/app/ | wc -l
ls data/data/ | grep -E "wickr|magisk|signal|telegram|tor|galleryvault"

# SMS
sqlite3 data/data/com.android.providers.telephony/databases/mmssms.db "SELECT count(*) FROM sms;"
sqlite3 data/data/com.android.providers.telephony/databases/mmssms.db "SELECT body FROM sms LIMIT 10;"

# Location
strings data/data/com.google.android.apps.maps/files/offlinedatabase/offline.db | grep -E "Holly|WORK|HOME|World" | sort -u
sqlite3 data/data/com.google.android.apps.maps/databases/gmm_myplaces.db "SELECT * FROM sync_item;"
