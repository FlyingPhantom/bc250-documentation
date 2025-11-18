# FAQ based on Official BC250 Community discord server

# List of potential questions:

## HElp! How dO I make card work???
- Fully read the BC250 Documentation before asking any questions, many questions are already answered there.

## Has anyone tried spoofing the ID of a different GPU to get Windows to work?
- Yes, it doesn't work. Why? Its more complicated then just spoofing your GPU if your GPU cant actually talk to the OS its essentially useless.

## Has anybody tried SteamOS/Bazzite/Whateverthefuck?
-  Yes, Bazzite does work use the script by [vietsman](https://github.com/vietsman).
   - curl -s https://raw.githubusercontent.com/vietsman/bc250-documentation/refs/heads/main/oberon-setup.sh | sudo sh 

## I get a black screen when attempting to install my linux distro!
- These APUs have display issues when booting without gpu drivers installed, nomodeset must be set in the kernel command line in order to display a picture, then removed after gpu drivers are installed to enable gpu acceleration. On Fedora, booting with basic graphics mode will enable nomodeset for you.

## How do i set *nomodset* on my distro?
- It depends on your distro and bootloader the example used here will be grub because its most known and most used but for other distros use your browser and find the info that way.
  - First, open the grub default config its usually at */etc/default/grub* but if you use a different configure in different directory use that one.
  - Second, run *sudo nano /etc/default/grub* to open the config if you use a different text editor use that one.
  - Find, the line that starts with *GRUB_CMDLINE_LINUX=* and add your parameter(s) inside the quotes.
  - Third, add nomodset paramter at the end of the line. So for example if it said *GRUB_CMDLINE_LINE="quiet splash"* after the change it should look like *GRUB_CMDLINE_LINE="quiet splash nomodset"*.
  - Forth, use this knoweldge to remove the nomodset if neccesery or to use other kernel parameters.

## Can I attach a GPU to the BC-250 to upgrade it?
- Not really. The PCIe 2x2 slot will severely bottleneck any GPU attached, severing any cost efficiency that may be gained by attaching an external GPU. A GPU can be installed nonetheless, and it has been done before, but know that it is in no way efficient or wise to do so as these boards are mostly CPU bound.

## Can the RAM be upgraded?
- No. GDDR6 chips larger than what is already installed on these cards simply do not exist.
- Technically its not RAM in the first place its VRAM thats being shared with the GPU and the CPU.
- Technically it would be possible to solder higher capacity modules. But has not been tested yet or proven to work in current stage its only a hypothetical.

## Can the disabled cores on these APUs be reenabled?
- No. While it isn't confirmed (no one has cracked one open and looked at it under a microscope), it is highly likely that the cores are fused off physically, preventing us from ever using them.

## I need help with GPU Mining.
- Seek help elsewhere. I dont give enough of a fuck.

## Can these cards be overclocked beyond 2000MHz?
- Yes they can, a kernel patch can allow overclocking up to 2230MHz. Bazzite currently has this patch by default, while other distros need to be patched manually.
- This has already been dicussed in the main documentation.

## My question isn't listed here, where can I get help?
- Create a issue on the github and if the issue seems to be happening a lot of times and its **NOT** a user error it will be added here.

## Im having issues with KDE Plasma.
- Update your kernel. The RDSEED instruction is broken on the BC250, but a kernel update fixes this issue.

## I'm not getting audio out of the DP port/all audio is pitched down.
- Audio over DP is broken on these boards, although some passive DP to HDMI adapters resolves this issue.

## How do i cool my BC-250?
- Theres multiple ways of how you can cool it and which you choose is up to you but directions can be given.
  - Water cooling can be possible but too complicated so not recommended
  - If possible use liquid metal and be carefull how you apply it otherwise it can make a short circut and kill the motherboard.

## Are these boards energy efficient for server use?
- Not really. These boards don't really idle properly due to this APU being largely a GPU with a CPU attached rather than a CPU with a GPU attached like most APUs. They can consume upwards of 70 Watts at idle depending on voltage set, lacks IOMMU.
   - Note: Hardware encoding with zink needs to be further tested

## How do I flash the BIOS without a hardware flasher?
- See [⁠BIOS update/flasher program](https://github.com/FlyingPhantom/bc250-documentation/blob/main/4U12G%20BIOS%20Update(2).zip). Instructions are included in the zip file, but the included Robin5.00 BIOS file is a stock, unmodified BIOS. To flash a modded BIOS, you must replace this file with a modded BIOS file. Make sure the new BIOS file has the same name as the stock one, then follow the instructions in the zip. After flashing, make sure IOMMU is disabled in BIOS! It sometimes enables itself after flashing and causes issues.
- The file originaly provided by TG2 on discord.

## What is the relative performance of this card?
- It is about equivalent to an RX 6600 paired with a R5 2600.

## Can you swap the APU on these boards with a PS5 APU to get more cores?
- No. The AMD PSP would prevent this. 

## What PSU is recommended? 
- Its generally recommend a PSU that can do a minimum of 300 Watts on a single 12V rail (Volts * Amps = Watts), or 400 Watts if you plan on overclocking to the max 2230MHz GPU speed. 

## Can you overclock the cpu or the gpu?
- Yes, both can be overclocked.

## Can you undervolt the cpu or the gpu?
- Yes, both can be undervolted.

## How do i overclock or undervolt the cpu or the gpu?
- Check the main documentaion where the topic is dicussed further.

## Which distro should i use?
- For general users its recommended to use Bazzite as its closest to SteamOS.
- For more advanced users Arch would be more appealing.

## Should i use a custom kernel?
- That depends on who you are, if you wanna use a kernel with a different scheduler or different features then yes you should or even if you wanna try to improve performance but for a normal user no you shouldnt use a custom kernel.
- A custom kernel im reffering to is the one you make yourself rather then the one thats shipped with the distro.

## Should i use 8/8, 4/12 or 512/15.5 VRAM-RAM configuration?
- It depends on your use case, if you wanna play games 512gb vram and 15.5 gb of ram is probabbly your choice but other stuff its up to your prefference.

## Should i buy or 3d print a case?
- Wether you should buy a case or 3d print one depends on your situation and circumstances.

## Should i do virtualization?
- Unless you plan on to use it for heavy workloads no you should not use virtualization because you cannot get full performance.
- Why you cant get full performance? Because IOMMU dosent work and even if it did work you would need the drivers for a OS thats not even supported in the first place.

## Should i buy this?
- Wether you buy a bc-250 entirely depends on you situation,cirucumstance and need.
- If you think you need it then buy one, otherwise dont.

## Who should and shouldnt use this?
- People who should use this are the ones that can read the documenation and ask for support nicely and provide necceserey info.
- And people who shouldnt are ones that do not read the documentation cannot ask nicely and are unable to provide the context and the neccesery info.


# Credits:

## BC-250 Community discord server
## Everybody else mentioned in the FAQ-
