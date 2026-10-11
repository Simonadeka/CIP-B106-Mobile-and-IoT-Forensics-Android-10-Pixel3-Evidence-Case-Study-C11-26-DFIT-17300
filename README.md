# CIP-B106-Mobile-and-IoT-Forensics-Android-10-Pixel3-Evidence-Case-Study-C11-26-DFIT-17300

**Reg:** C11/26/DFIT/17300 | **Case:** 26/DFIT/17300 | **Module:** CIP B106 Mobile and IoT Forensics | **Device:** Android 10 Pixel 3 | **Analyst:** Simonadeka | **Date:** 11 Oct 2026

![Status](https://img.shields.io/badge/Status-Verified-100%25-success) ![Device](https://img.shields.io/badge/Device-Pixel%203%20Android%2010-blue) ![Hash](https://img.shields.io/badge/SHA256-77467648...MATCH-orange) ![Location](https://img.shields.io/badge/Location-Holly%20Springs%2035.73--78.63-red)

> **Brief:** Android 10 Pixel 3 Evidence Case Study | **Main Finding:** `Holly Springs, NC 35.734602,-78.636654` from `offline.db` + `gmm_myplaces.db` sync_item `35734602|-78636654` | **Evidence:** `~/CIPB106-C11/26/DFIT/17300/`

### Preservation - Task A - INTEGRITY 100%

| Artefact | Working Copy Path | Size | SHA256 | Status |
| :--- | :--- | :--- | :--- | :--- |
| offline.db | `data/data/com.google.android.apps.maps/files/offlinedatabase/offline.db` | 380K 389,120 B | `77467648434bf0462b9dcc8B885cB0efe780d4dab6b330740e6b178894ea63c` | ✅ MATCH |
| final_location.txt | `Evidence/final_location.txt` | 64B | Holly Springs + WORK + HOME | ✅ VERIFIED |


sha256sum Working/offline.db | cut -d' ' -f1 > /tmp/w.txt
sha256sum Evidence/offline.db | cut -d' ' -f1 > /tmp/e.txt
diff /tmp/w.txt /tmp/e.txt && echo "HASH MATCH - PRESERVATION OK"
# 77467648434bf0462b9dcc8B885cB0efe780d4dab6b330740e6b178894ea63c

**Main Finding:** Holly Springs, NC 35.734602,-78.636654 from offline.db 380K SHA256 77467648 MATCH + gmm_myplaces.db sync_item 35734602|-78636654

### Preservation - Task A - INTEGRITY 100%

| Artefact | Path | Size | SHA256 | Status |
| :--- | :--- | :--- | :--- | :--- |
| offline.db | data/data/com.google.android.apps.maps/files/offlinedatabase/offline.db | 380K 389,120 B | 77467648434bf0462b9dcc8B885cB0efe780d4dab6b330740e6b178894ea63c | MATCH |
| final_location.txt | Evidence/final_location.txt | 64B | Holly Springs + WORK:0 + INFERRED_HOME | VERIFIED |

sha256sum Working/offline.db | cut -d' ' -f1 > /tmp/w.txt
sha256sum Evidence/offline.db | cut -d' ' -f1 > /tmp/e.txt
diff /tmp/w.txt /tmp/e.txt && echo "HASH MATCH - PRESERVATION OK"
# 77467648434bf0462b9dcc8B885cB0efe780d4dab6b330740e6b178894ea63c

### Lab Tasks - 5 Column Style

| Task | Description | Evidence Path | Proof | Link |
| :--- | :--- | :--- | :--- | :--- |
| A | Preservation | offline.db SHA256 77467648 | diff w.txt e.txt HASH MATCH | Report_Screenshots |
| B | 81 Apps | data/app/ wc -l 81 | Wickr, Magisk, Signal, Telegram, Tor, GalleryVault | Fig_2.1 |
| B | Discord Active | com.discord 172K messages table | cache 0,11,28,50,6 page_count 9 | Fig_2.3 |
| C | SMS 24 OTP | mmssms.db 116K count 24 | 59389 Telegram, 303-077 Signal, 362-593 WhatsApp | Fig_4.1 |
| C | Contacts Deleted | contacts2.db deleted_contacts | Josh Hickman x9 deleted | Fig_4.2 |
| C | Facebook Orca | threads_db2 300K COUNT 1 | omnistore empty = EXPECTED encrypted | Fig_4.3 |
| D | offline.db Exists | 380K user_version 21 page_count 95 | backend_regions TABLE EXISTS | Fig_5.1 |
| D | Final Location | strings offline.db | Holly Springs, INFERRED_HOME, WORK:0, World | Fig_5.4 FINAL |
| D | Coords BONUS | gmm_myplaces.db 40K 35734602 | 35.734602,-78.636654 Holly Springs NC | Fig_5.6 |

### Repo Structure

/Report_Screenshots/ - 30 verification Figs Fig_1.0 to Fig_5.6
/Evidence/ - final_location.txt 64B, offline.db 380K HASH 77467648
/Reports/ - CIP-B106_CaseStudy_C11-26-DFIT-17300_Simonadeka.pdf

### Submission

**PDF Filename:** CIP-B106_CaseStudy_C11-26-DFIT-17300_Simonadeka.pdf
**GitHub Repo:** github.com/Simonadeka/CIP-B106-Mobile-and-IoT-Forensics-Android-10-Pixel3-Evidence-Case-Study-C11-26-DFIT-17300
**Working Path:** ~/CIPB106-C11/26/DFIT/17300/Working/Pixel 3
**Evidence Path:** ~/CIPB106-C11/26/DFIT/17300/Evidence/

### Academic Declaration

I confirm this report reflects my own examination of authorised course evidence C11/26/DFIT/17300 and that I have identified all sources, tools, and assistance used.
