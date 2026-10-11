**Reg:** C11/26/DFIT/17300 | **Case:** 26/DFIT/17300 | **Module:** CIP B106 Mobile and IoT Forensics | **Device:** Android 10 Pixel 3 | **Analyst:** Simonadeka | **Date:** 11 Oct 2026

![Status](https://img.shields.io/badge/Status-Verified-100%25-success) ![Device](https://img.shields.io/badge/Device-Pixel%203%20Android%2010-blue) ![Hash](https://img.shields.io/badge/SHA256-77467648...MATCH-orange) ![Location](https://img.shields.io/badge/Location-Holly%20Springs%2035.73--78.63-red)

> **Brief:** Android 10 Pixel 3 Evidence Case Study | **Main Finding:** `Holly Springs, NC 35.734602,-78.636654` from `offline.db` + `gmm_myplaces.db` sync_item `35734602|-78636654` | **Evidence:** `~/CIPB106-C11/26/DFIT/17300/`

### Preservation - Task A - INTEGRITY 100%

| Artefact | Working Copy Path | Size | SHA256 | Status |
| :--- | :--- | :--- | :--- | :--- |
| offline.db | `data/data/com.google.android.apps.maps/files/offlinedatabase/offline.db` | 380K 389,120 B | `77467648434bf0462b9dcc8B885cB0efe780d4dab6b330740e6b178894ea63c` | ✅ MATCH |
| final_location.txt | `Evidence/final_location.txt` | 64B | Holly Springs + WORK + HOME | ✅ VERIFIED |

```bash
sha256sum Working/offline.db | cut -d' ' -f1 > /tmp/w.txt
sha256sum Evidence/offline.db | cut -d' ' -f1 > /tmp/e.txt
diff /tmp/w.txt /tmp/e.txt && echo "HASH MATCH - PRESERVATION OK"
# 77467648434bf0462b9dcc8B885cB0efe780d4dab6b330740e6b178894ea63c
### Lab Tasks - Same 5-column style you fixed for Day 13
Task | Description | Evidence Path | Proof | Status
**A** | Preservation | `offline.db` SHA256 `77467648...` | `diff w.txt e.txt` HASH MATCH | [Link](./Report_Screenshots/Fig_1.1_FINAL_TaskA_HASH_MATCH_PRESERVATION_OK_77467648_VERIFIED_100_PERCENT.png) | ✅
**B** | App Inventory 81 Apps | `data/app/ wc -l = 81` | Wickr, CyberDust, Silent, Signal, Telegram, WhatsApp, Wire, Tor, GalleryVault, Magisk root | [Link](./Report_Screenshots/Fig_2.1_TaskB_App_Inventory_81_Apps.png) | ✅
**B** | Discord Active Use | `com.discord/databases/google_app_measurement_local.db` 172K | `messages` table page_count 9 + cache `0,11,28,50,6` | [Link](./Report_Screenshots/Fig_2.3_TaskB_Discord_Google_Analytics_Tables.png) | ✅
**C** | SMS 24 OTPs | `mmssms.db` 116K `SELECT count(*) = 24` | 59389 Telegram, 303-077 Signal, 362-593 WhatsApp | [Link](./Report_Screenshots/Fig_4.1_TaskC_SMS_Count_24_mmssms_db.png) | ✅
**C** | Contacts Deleted | `contacts2.db` `deleted_contacts` | Josh Hickman x9 deleted | [Link](./Report_Screenshots/Fig_4.2_TaskC_Contacts2_db_Deleted_Raw_Contacts_Josh_Hickman_9x_deleted.png) | ✅
**C** | Facebook Orca | `com.facebook.orca` 2.5M `threads_db2` 300K COUNT=1 | `omnistore: empty` = EXPECTED encrypted | [Link](./Report_Screenshots/Fig_4.3_TaskC_Social_Media_DBs_Facebook_Orca_Discord_Maps_offline_db_SQLite_VERIFIED.png) | ✅
**D** | Location http://offline.db | `maps/.../offline.db` 380K user_version 21 page_count 95 | `backend_regions` TABLE EXISTS | [Link](./Report_Screenshots/Fig_5.1_TaskD_Maps_offline_db_380K_Oct9_1848_VERIFIED.png) | ✅
**D** | Final Location | `strings offline.db \| grep Holly` | `Holly Springs(` `INFERRED_HOME` `IMPLICIT_REGION_WORK` `WORK:0` `World` | [Link](./Report_Screenshots/Fig_5.4_TaskD_Holly_Springs_FINAL_WORK_HOME_WORLD_VERIFIED_100_PERCENT_COMPLETE.png) | ✅
**D** | Coordinates BONUS | `gmm_myplaces.db` 40K `sync_item` | `35734602\|-78636654 = 35.734602,-78.636654` | [Link](./Report_Screenshots/Fig_5.6_BONUS_gmm_myplaces_sync_item_35734602_-78636654_35.73_-78.63_Holly_Springs_LAT_LONG.png) | ✅
### Repo Structure - Same as iOS13 repo
/Report_Screenshots/ - 30 verification Figs (Fig_1.0 to Fig_5.6)
/Evidence/ - final_location.txt 64B, offline.db 380K HASH 77467648
/Reports/ - CIP-B106_CaseStudy_C11-26-DFIT-17300_Simonadeka.pdf
README.md
### Submission
*PDF Filename:* `CIP-B106_CaseStudy_C11-26-DFIT-17300_Simonadeka.pdf` (Reg with hyphens, no slashes)
*GitHub:* `github.com/Simonadeka/CIP-B106-Mobile-and-IoT-Forensics-Android-10-Pixel3-Evidence-Case-Study-C11-26-DFIT-17300`

### Academic Declaration
I confirm this report reflects my own examination of authorised course evidence C11/26/DFIT/17300 and that I have identified all sources, tools, and assistance used.

*Reg:* C11/26/DFIT/17300 | *Signed:* Simonadeka | *Date:* 11 Oct 2026
*Hash:* `77467648434bf0462b9dcc8B885cB0efe780d4dab6b330740e6b178894ea63c`

3. Scroll down -> **Commit changes** -> **Commit directly to main branch** -> Commit

After that, click `Add file -> Upload files` -> Drag your `Report_Screenshots` folder with 30 images.

Ready to paste?
