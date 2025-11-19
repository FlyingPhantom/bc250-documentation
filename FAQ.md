# BC-250 FAQ – Based on the Official Community Discord Server

## Help! How do I make the card work???
- Fully read the BC-250 Documentation before asking any questions. Most issues are already covered there.

## Has anyone tried spoofing the GPU ID to get Windows working?
- Yes, it doesn’t work. It’s far more complicated than just changing the ID. If the GPU can’t actually communicate with the driver, it’s useless.

## Has anybody tried SteamOS / Bazzite / etc.?
- Yes, Bazzite works well. Use the script by vietsman:  
  ```
  curl -s https://raw.githubusercontent.com/vietsman/bc250-documentation/refs/heads/main/oberon-setup.sh | sudo bash
  ```
## I get a black screen when trying to install my Linux distro!

- These APUs have no display output until GPU drivers load. Add nomodeset to the kernel command line during installation, then remove it afterwards to enable acceleration. On Fedora, selecting “Basic graphics mode” at boot does this automatically.

## How do I set nomodeset on my distro?

- Depends on your bootloader, but here’s the GRUB example (most common):
   - 1.Edit /etc/default/grub
   - 2.Find the line GRUB_CMDLINE_LINUX="..."
   - 3.Add nomodeset inside the quotes → GRUB_CMDLINE_LINUX="quiet splash nomodeset"
   - 4.Run sudo grub-mkconfig -o /boot/grub/grub.cfg (or sudo update-grub) and reboot
   - 5.Google “add kernel parameter <your distro>” for systemd-boot, rEFInd, etc.


## Can I attach an external GPU to the BC-250?

- Technically yes, but the PCIe 2.0 ×2 slot bottlenecks everything hard. It kills any cost/performance benefit. These boards are mostly CPU-bound anyway.

## Can the RAM be upgraded?

- No. The 16 GB GDDR6 is soldered and shared as VRAM/system RAM. Larger GDDR6 dies don’t exist.
- Soldering higher-capacity chips is theoretically possible but completely untested and extremely risky.

## Can the disabled CPU cores be re-enabled?

- No. They are almost certainly physically fused off at the factory.

## I need help with GPU mining.

Ask somewhere else. I don't give a fuck.

## Can these cards be overclocked beyond 2000 MHz?

- Yes, up to ~2230 MHz with a small kernel patch. Bazzite includes it by default; other distros need it applied manually (see main docs).

## My question isn’t listed here, where do I get help?

- Open a GitHub issue. If it’s a common problem and not user error, it’ll get added to the FAQ.

## I’m having issues with KDE Plasma

- Update your kernel. The RDSEED instruction is broken on this silicon; newer kernels include the fix.

## I’m not getting audio (or it’s pitched down) over DisplayPort

- DP audio is broken on these boards. Some passive DP→HDMI adapters fix it.

## How do I cool my BC-250?

- Good air cooler is the simplest and most reliable.
- Liquid metal works but is extremely risky – one mistake and you short the board.
- Custom water loops exist but are overkill.

## Are these boards energy-efficient for server use?

- No. Idle power is terrible (60–80 W) because it’s a GPU-first design with poor C-states and no working IOMMU.

## How do I flash the BIOS without a hardware programmer?

- Download [here](https://github.com/FlyingPhantom/bc250-documentation/blob/main/4U12G%20BIOS%20Update(2).zip)
- Instructions are inside. Replace the included Robin5.00 file with any modded BIOS (keep the same filename). After flashing, disable IOMMU in BIOS – it sometimes re-enables itself.

## What is the relative performance of this card?

- Roughly equivalent to an RX 6600 + Ryzen 5 2600.

## Can you swap the APU for a full PS5 APU to get more cores?

- No. The AMD PSP will refuse to boot it.

## What PSU is recommended?

- Minimum 300 W on a single 12 V rail. 400 W+ if you plan to push 2230 MHz overclocks.

## Can you overclock the CPU or GPU?

- Yes, both.

## Can you undervolt the CPU or GPU?

- Yes, both.

## How do I overclock or undervolt the CPU/GPU?

- See the main documentation – it’s covered in detail there.

## Which distro should I use?

- General/gaming users → Bazzite (closest to SteamOS)
- Advanced users → Arch

## Should I use a custom kernel?

- Only if you want specific schedulers or extra features. Normal users should stick to the distro-shipped kernel.

## Should I use 8/8, 4/12, or 512 MB / 15.5 GB VRAM-RAM split?

- Depends on workload. Gaming → 512 MB VRAM + 15.5 GB RAM. Everything else is personal preference.

## Should I buy or 3D-print a case?

- Depends on your budget, skills, and aesthetics. Both work fine.

## Should I do virtualization?

- Not recommended for performance-critical stuff. No working IOMMU and driver support is limited anyway.

## Should I buy a BC-250?

- Entirely up to your needs, budget, and tolerance for jank. If you’ve read the docs and still want one, go for it.

## Who should and shouldn’t use this?

- Should: People who read the documentation, ask politely, and provide logs/context.
- Shouldn’t: People who don’t read, spam “help it no work”, or refuse to give details.

## Credits

- BC-250 Community Discord server
- Everyone mentioned in the FAQ / documentation
