# NMPB File Platform — Prototype (MPB Project 2)

Standalone, self-contained web prototype for the Nigerian Military Board file
tracking platform. Single `index.html`, zero dependencies, zero backend —
data persists in the browser's localStorage. Open it in any browser and demo.

## What it implements (from the client meeting)

1. **Data Entry** — digital registry replaces Excel; files keyed by service number.
2. **File Tracking** (top priority) — check-out / check-in between offices,
   automatic dwell-time "minuting", overdue flags (default >3 days),
   current holder always visible.
3. **Request → Signature Gate** — officers complete a request form; a Director
   must draw a signature before any file is released (hybrid: physical forms
   stay, mirrored digitally).
4. **Search** — by service number, title, office, status.
5. **Movement audit log** — every registration / request / signature /
   check-out / check-in timestamped, immutable.
6. **Reports** — files held per office, overdue counts, longest current hold,
   movements in last 7 days.

## Demo script (2 minutes)

1. Open `index.html` in a browser (Chrome/Edge). Fresh data seeds automatically.
2. **Dashboard** — point out overdue files and live position.
3. Role switch (header) → **Registry Officer** → Files → "Register new file".
4. Files → open `N-2761` → "Request this file" (act as Staff Officer).
5. Role → **Director** → Requests → "Approve & Sign" → draw signature.
6. Role → **Registry Officer** → Requests → "Check out" — dwell timer starts.
7. Open the file → "Check in (return)" → file back to Available, dwell closed.
8. **Movement Log** — show the complete audit trail. **Reports** — office summary.

## Reset demo data

DevTools console → `localStorage.removeItem('nmpb_proto_v1')` → reload.

## Constraints honored (from meeting)

- Standalone: no dependency on the legacy server or Excel.
- Hybrid: physical forms/signatures remain; the digital flow mirrors them.
- 3 Directors = approval tier before release.
- Physical file movement is still manual — the system records it, it doesn't
  move files.

## Next step toward production

- Real backend (PostgreSQL + API), auth with military-grade access control,
  email/notification hooks, Excel import for historical records,
  optional link to scanned file images on the legacy server.
