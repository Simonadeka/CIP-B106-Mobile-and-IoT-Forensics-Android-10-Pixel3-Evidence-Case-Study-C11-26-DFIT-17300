# CIP-B106-Mobile-and-IoT-Forensics-Android-10-Pixel3-Evidence-Case-Study-C11-26-DFIT-17300

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
