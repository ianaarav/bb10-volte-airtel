# Airtel India VoLTE test checklist (BB10)

*Untested draft profile for carrier ID 402 (Bharti Airtel).*

## Before you start
- [ ] BlackBerry 10 phone on OS 10.3.x with AutoRoot v4 or newer
- [ ] Airtel SIM in the phone, VoLTE switched on for your Airtel account
- [ ] Term49 installed
- [ ] `volte-airtel-test.zip` from this repo
- [ ] Your original APN settings written down

## Install
1. [ ] Copy the zip into the phone's Downloads folder (USB cable, or `scp` over Wi-Fi)
2. [ ] In Term49, check it arrived: `ls -l /accounts/1000/shared/downloads/`
3. [ ] Become root: `__root` (the prompt changes from `$` to `#`)
4. [ ] `/var/rootdata/installer /accounts/1000/shared/downloads/volte-airtel-test.zip`
5. [ ] Look for "Installation completed successfully" and no line starting with "Error"
6. [ ] Leave root: `exit`
7. [ ] Restart the phone

## Check
- [ ] Run `/var/addons/volte/init/ims_manager -a check -v` (if permission is denied, run `__root` first)
- [ ] Look for a VoLTE icon next to the signal bars
- [ ] Call another phone: does it connect, with sound both ways?

## What the check lines mean
- `COMPATIBLE`: the phone itself passes the addon's test.
- `SIM_UNSUPPORTED`: no SIM was matched to a profile. A phone with no working SIM prints this.
- `SIM_LTE_OK` and `SIM_NOT_READY` also appear in the program. `SIM_LTE_OK` is probably the good result, but that's a guess; nobody has reported seeing it yet.

## Report back (open an issue)
- Full output of the `check` command
- Whether the icon showed and whether the call worked
- OS version and Airtel circle (the MNC of your SIM, if you know it)
- Anything in `/var/tmp/bb10-volte`, if it exists
