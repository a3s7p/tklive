# tklive

The TurnKey Live system based on upstream Debian tools: live-build, live-boot and d-i.

```shell
# APP=core # or any other appliance
# cd $APP
# make # build an .iso with fab first
# mkdir lb
# cd lb
# lb config --config=https://github.com/turnkeylinux/tklive
# lb build
```

The most useful artifact of the build is the `turnkey-$APP-amd64.hybrid.iso` iso which is both UEFI and legacy BIOS-bootable and has all the power of upstream d-i.

The resulting images are slightly (10s of MBs) bigger than fab-built since they include packages (udebs) for upstream d-i on the image root which were previously provided to di-live by the squashfs.

To run a `diffoscope` on the fab-built and the lb-built isos to see their differences, set `TKLIVE_DIFFOSCOPE=1`. The squashfs image used is identical so the differences are only in the .iso contents.
