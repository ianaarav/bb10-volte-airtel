# bb10-volte-airtel

A draft **Airtel India** profile for the [BB10 VoLTE addon](https://bb10.root.sx/blog/volte) by bb10root.

> **Status: untested.** I couldn't try it on a live Airtel SIM (my Z10's SIM slot is broken).
> If you have a working BB10 and an Airtel SIM, please test it. See [CHECKLIST.md](CHECKLIST.md).

## What's here

| File | What it is |
|---|---|
| `carrier-402-volte.xml` | The profile. Goes in `/var/addons/volte/data/` on the phone. |
| `volte-airtel-test.zip` | The original addon plus this profile, installable with `/var/rootdata/installer`. |
| `CHECKLIST.md` | Step-by-step test sheet. |

## Details

- Airtel is carrier ID **402** in `/base/etc/carrier/ids/carrierIds.xml`. Every Airtel India network code listed there (MCC 404 and 405) maps to that one ID, so a single file should cover all circles.
- `carrierIds.xml` lists two vendor IDs for this carrier, 611 and 149. The profile uses 611. Which one matters, if either does, is unknown.
- The IMS section (APN `ims`, IPv4v6, P-CSCF via PCO) is identical to the China Mobile and China Unicom profiles from the addon.
- Data APN is `airtelgprs.com`.
- **MMS values are from memory and unverified.** Compare them with your own APN settings.
- Emergency numbers (100, 101, 102, 108, 112) and UI flags follow the Vodafone Ukraine sample.

## Known unknowns

- Airtel may refuse devices it doesn't recognise, regardless of this profile.
- Nobody has registered VoLTE with this file yet.
- Editing carrier config can affect cellular connectivity. Note your original APN settings first.

## Results so far

| Tester | Phone / OS | Airtel circle | `check` output | Calls work? |
|---|---|---|---|---|
| (me) Z10 | no working SIM slot | n/a | `COMPATIBLE`, then `SIM_UNSUPPORTED` | untestable |

Add yours by opening an issue.

## Credits and license

All the real work is by the [BB10 VoLTE addon](https://github.com/bb10root/bb10-volte) author, and by Qin Yu ([BB10DeviceVoLTEResearch](https://github.com/imqinyu/BB10DeviceVoLTEResearch)) and Hazematman, whose research it builds on. This repo only adds an Airtel profile and bundles the addon files from the original release.

The addon is GPL-3.0, so this repo is too.
