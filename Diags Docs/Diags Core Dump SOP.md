---
author:
   name: Anna Ning
   email: Anna.Ning@quantacn.com
date: 2020-2-12
title: Diags Core Dump SOP
---

![docDingDong300](Diags_Core_Dump_SOP/img/docDingDong300.png)

# Collection steps

1. Enter astris in local terminal 

```
   MCA9060168:~ sda$ astris
   astris v2.6.7 [Astris-1506.40.3~3 (bridgeOSJazzB tools)]

   Probe address: ChimpSWD-30B0D9
   Probe type: chimp
   Probe firmware: 0.68
   Probe tckrate: 12000000

   Listening on port 8000 for CPU0, CPU1
   Listening on port 8002 for SIO
   Listening on port 8003 for SEP
   Listening on port 8004 for PMP
   Listening on port 8005 for AOP
   Listening on port 8006 for SMC
   Listening on port 8007 for ISP
   Listening on port 8008 for ANS2
   Listening on port 8009 for PUP
   Detected Gibraltar B0
   Loading SOC support script
   Identified product J185fAP
    ChimpSWD-30B0D9 - CPU0:Halt CPU1:PowerOff SIO:Reset SEP:PowerOff PMP:PowerO
   ff AOP:Reset SMC:Run ISP:PowerOff ANS2:Halt PUP:Reset
   NO CPU > 
```

2. Create /tmp/efi_coredumps in the specified path to store the collected core dump files

```
   /Users/sda/tmp/efi_coredumps/
```

3. Enter efi_coredump -debug /Users/sda/tmp/efi_coredumps/iefi.core in local terminal to collect iEFI core dump

```
   NO CPU > efi_coredump -debug /Users/sda/tmp/efi_coredumps/iefi.core
```

4. Wait for the core dump collection to return to the NO CPU> flag


```
   NO CPU > efi_coredump -debug /Users/sda/tmp/efi_coredumps/iefi.core
   No cpu selected. Selecting CPU0
   Actual TCK rate now 6460000 Hz (when 8000000 Hz requested)
   Running with tckrate 6460000
   Hob address = 0x122000 0x821006000 0x820306000 0x820206000 0x820106000 0x820006000 0x810206000 0x810006000 0x808206000 0x808106000 0x808006000 0x800000000
   Using memap failed for 0x122002. Going through the CPU
   Could not find end of hob list from 0x122000 with error: AXcpu_readmem @ 0x122002 failed: ASTRIS_ERR_NOMEM
   Addr = 0x821006002 : Data = 0x0
   Addr = 0x821006000 : Data = 0x0
   hob_length 0 hob_type 0
   hob length is zero. Exiting.
   Did not find EFI_HOB_END_OF_HOB_LIST with hob starting at 0x821006000
   Addr = 0x820306002 : Data = 0xffff
   Addr = 0x820306000 : Data = 0xff1b
   hob_length 65535 hob_type 65307
   Did not find EFI_HOB_END_OF_HOB_LIST with hob starting at 0x820306000
   Addr = 0x820206002 : Data = 0x0
   Addr = 0x820206000 : Data = 0x0
   hob_length 0 hob_type 0
   hob length is zero. Exiting.
   Did not find EFI_HOB_END_OF_HOB_LIST with hob starting at 0x820206000
   Addr = 0x820106002 : Data = 0x0
   Addr = 0x820106000 : Data = 0x0
   hob_length 0 hob_type 0
   hob length is zero. Exiting.
   Did not find EFI_HOB_END_OF_HOB_LIST with hob starting at 0x820106000
   Addr = 0x820006002 : Data = 0x0
   Addr = 0x820006000 : Data = 0x0
   hob_length 0 hob_type 0
   hob length is zero. Exiting.
   Did not find EFI_HOB_END_OF_HOB_LIST with hob starting at 0x820006000
   Addr = 0x810206002 : Data = 0x0
   Addr = 0x810206000 : Data = 0x0
   hob_length 0 hob_type 0
   hob length is zero. Exiting.
   Did not find EFI_HOB_END_OF_HOB_LIST with hob starting at 0x810206000
   Addr = 0x810006002 : Data = 0x0
   Addr = 0x810006000 : Data = 0x0
   hob_length 0 hob_type 0
   hob length is zero. Exiting.
   Did not find EFI_HOB_END_OF_HOB_LIST with hob starting at 0x810006000
   Addr = 0x808206002 : Data = 0xd639
   Addr = 0x808206000 : Data = 0x7352
   hob_length 54841 hob_type 29522
   Did not find EFI_HOB_END_OF_HOB_LIST with hob starting at 0x808206000
   Addr = 0x808106002 : Data = 0xbf94
   Addr = 0x808106000 : Data = 0xc363
   hob_length 49044 hob_type 50019
   Did not find EFI_HOB_END_OF_HOB_LIST with hob starting at 0x808106000
   Addr = 0x808006002 : Data = 0x38
   Addr = 0x808006000 : Data = 0x1
   hob_length 56 hob_type 1
   Addr = 0x80800603a : Data = 0x18
   Addr = 0x808006038 : Data = 0x10
   hob_length 24 hob_type 16
   Addr = 0x808006052 : Data = 0x18
   Addr = 0x808006050 : Data = 0x5
   hob_length 24 hob_type 5
   Addr = 0x80800606a : Data = 0x30
   Addr = 0x808006068 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800609a : Data = 0x30
   Addr = 0x808006098 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x8080060ca : Data = 0x30
   Addr = 0x8080060c8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x8080060fa : Data = 0x20
   Addr = 0x8080060f8 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x80800611a : Data = 0x10
   Addr = 0x808006118 : Data = 0x6
   hob_length 16 hob_type 6
   Addr = 0x80800612a : Data = 0x30
   Addr = 0x808006128 : Data = 0x4
   hob_length 48 hob_type 4
   Addr = 0x80800615a : Data = 0x58
   Addr = 0x808006158 : Data = 0x4
   hob_length 88 hob_type 4
   Addr = 0x8080061b2 : Data = 0x58
   Addr = 0x8080061b0 : Data = 0x4
   hob_length 88 hob_type 4
   Addr = 0x80800620a : Data = 0x58
   Addr = 0x808006208 : Data = 0x4
   hob_length 88 hob_type 4
   Addr = 0x808006262 : Data = 0x58
   Addr = 0x808006260 : Data = 0x4
   hob_length 88 hob_type 4
   Addr = 0x8080062ba : Data = 0x30
   Addr = 0x8080062b8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x8080062ea : Data = 0x30
   Addr = 0x8080062e8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800631a : Data = 0x38
   Addr = 0x808006318 : Data = 0x4
   hob_length 56 hob_type 4
   Addr = 0x808006352 : Data = 0x28
   Addr = 0x808006350 : Data = 0x4
   hob_length 40 hob_type 4
   Addr = 0x80800637a : Data = 0x20
   Addr = 0x808006378 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x80800639a : Data = 0x20
   Addr = 0x808006398 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x8080063ba : Data = 0x20
   Addr = 0x8080063b8 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x8080063da : Data = 0x20
   Addr = 0x8080063d8 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x8080063fa : Data = 0x20
   Addr = 0x8080063f8 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x80800641a : Data = 0x20
   Addr = 0x808006418 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x80800643a : Data = 0x30
   Addr = 0x808006438 : Data = 0x3
   hob_length 48 hob_type 3
   Addr = 0x80800646a : Data = 0x30
   Addr = 0x808006468 : Data = 0x3
   hob_length 48 hob_type 3
   Addr = 0x80800649a : Data = 0x30
   Addr = 0x808006498 : Data = 0x3
   hob_length 48 hob_type 3
   Addr = 0x8080064ca : Data = 0x30
   Addr = 0x8080064c8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x8080064fa : Data = 0x30
   Addr = 0x8080064f8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800652a : Data = 0x30
   Addr = 0x808006528 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800655a : Data = 0x30
   Addr = 0x808006558 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800658a : Data = 0x60
   Addr = 0x808006588 : Data = 0xb
   hob_length 96 hob_type 11
   Addr = 0x8080065ea : Data = 0x40
   Addr = 0x8080065e8 : Data = 0x9
   hob_length 64 hob_type 9
   Addr = 0x80800662a : Data = 0x30
   Addr = 0x808006628 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800665a : Data = 0x18
   Addr = 0x808006658 : Data = 0xc
   hob_length 24 hob_type 12
   Addr = 0x808006672 : Data = 0x18
   Addr = 0x808006670 : Data = 0xd
   hob_length 24 hob_type 13
   Addr = 0x80800668a : Data = 0x10
   Addr = 0x808006688 : Data = 0xa
   hob_length 16 hob_type 10
   Addr = 0x80800669a : Data = 0x30
   Addr = 0x808006698 : Data = 0xe
   hob_length 48 hob_type 14
   Addr = 0x8080066ca : Data = 0x8
   Addr = 0x8080066c8 : Data = 0xffff
   hob_length 8 hob_type 65535
   Found type 0xffff 0x8080066c8
   Addr = 0x808006002 : Data = 0x38
   Addr = 0x808006000 : Data = 0x1
   hob_length 56 hob_type 1
   Found type 0x1 0x808006000
   Addr = 0x80800603a : Data = 0x18
   Addr = 0x808006038 : Data = 0x10
   hob_length 24 hob_type 16
   Addr = 0x808006052 : Data = 0x18
   Addr = 0x808006050 : Data = 0x5
   hob_length 24 hob_type 5
   Addr = 0x80800606a : Data = 0x30
   Addr = 0x808006068 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800609a : Data = 0x30
   Addr = 0x808006098 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x8080060ca : Data = 0x30
   Addr = 0x8080060c8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x8080060fa : Data = 0x20
   Addr = 0x8080060f8 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x80800611a : Data = 0x10
   Addr = 0x808006118 : Data = 0x6
   hob_length 16 hob_type 6
   Addr = 0x80800612a : Data = 0x30
   Addr = 0x808006128 : Data = 0x4
   hob_length 48 hob_type 4
   Addr = 0x80800615a : Data = 0x58
   Addr = 0x808006158 : Data = 0x4
   hob_length 88 hob_type 4
   Addr = 0x8080061b2 : Data = 0x58
   Addr = 0x8080061b0 : Data = 0x4
   hob_length 88 hob_type 4
   Addr = 0x80800620a : Data = 0x58
   Addr = 0x808006208 : Data = 0x4
   hob_length 88 hob_type 4
   Addr = 0x808006262 : Data = 0x58
   Addr = 0x808006260 : Data = 0x4
   hob_length 88 hob_type 4
   Addr = 0x8080062ba : Data = 0x30
   Addr = 0x8080062b8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x8080062ea : Data = 0x30
   Addr = 0x8080062e8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800631a : Data = 0x38
   Addr = 0x808006318 : Data = 0x4
   hob_length 56 hob_type 4
   Addr = 0x808006352 : Data = 0x28
   Addr = 0x808006350 : Data = 0x4
   hob_length 40 hob_type 4
   Addr = 0x80800637a : Data = 0x20
   Addr = 0x808006378 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x80800639a : Data = 0x20
   Addr = 0x808006398 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x8080063ba : Data = 0x20
   Addr = 0x8080063b8 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x8080063da : Data = 0x20
   Addr = 0x8080063d8 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x8080063fa : Data = 0x20
   Addr = 0x8080063f8 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x80800641a : Data = 0x20
   Addr = 0x808006418 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x80800643a : Data = 0x30
   Addr = 0x808006438 : Data = 0x3
   hob_length 48 hob_type 3
   Addr = 0x80800646a : Data = 0x30
   Addr = 0x808006468 : Data = 0x3
   hob_length 48 hob_type 3
   Addr = 0x80800649a : Data = 0x30
   Addr = 0x808006498 : Data = 0x3
   hob_length 48 hob_type 3
   Addr = 0x8080064ca : Data = 0x30
   Addr = 0x8080064c8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x8080064fa : Data = 0x30
   Addr = 0x8080064f8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800652a : Data = 0x30
   Addr = 0x808006528 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800655a : Data = 0x30
   Addr = 0x808006558 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800658a : Data = 0x60
   Addr = 0x808006588 : Data = 0xb
   hob_length 96 hob_type 11
   Addr = 0x8080065ea : Data = 0x40
   Addr = 0x8080065e8 : Data = 0x9
   hob_length 64 hob_type 9
   Addr = 0x80800662a : Data = 0x30
   Addr = 0x808006628 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800665a : Data = 0x18
   Addr = 0x808006658 : Data = 0xc
   hob_length 24 hob_type 12
   Addr = 0x808006672 : Data = 0x18
   Addr = 0x808006670 : Data = 0xd
   hob_length 24 hob_type 13
   Addr = 0x80800668a : Data = 0x10
   Addr = 0x808006688 : Data = 0xa
   hob_length 16 hob_type 10
   Addr = 0x80800669a : Data = 0x30
   Addr = 0x808006698 : Data = 0xe
   hob_length 48 hob_type 14
   Addr = 0x8080066ca : Data = 0x8
   Addr = 0x8080066c8 : Data = 0xffff
   hob_length 8 hob_type 65535
   Hob is located at 0x808006000
   Addr = 0x808006002 : Data = 0x38
   Addr = 0x808006000 : Data = 0x1
   hob_length 56 hob_type 1
   Addr = 0x80800603a : Data = 0x18
   Addr = 0x808006038 : Data = 0x10
   hob_length 24 hob_type 16
   Addr = 0x808006052 : Data = 0x18
   Addr = 0x808006050 : Data = 0x5
   hob_length 24 hob_type 5
   Addr = 0x80800606a : Data = 0x30
   Addr = 0x808006068 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800609a : Data = 0x30
   Addr = 0x808006098 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x8080060ca : Data = 0x30
   Addr = 0x8080060c8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x8080060fa : Data = 0x20
   Addr = 0x8080060f8 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x80800611a : Data = 0x10
   Addr = 0x808006118 : Data = 0x6
   hob_length 16 hob_type 6
   Addr = 0x80800612a : Data = 0x30
   Addr = 0x808006128 : Data = 0x4
   hob_length 48 hob_type 4
   Addr = 0x80800615a : Data = 0x58
   Addr = 0x808006158 : Data = 0x4
   hob_length 88 hob_type 4
   Addr = 0x8080061b2 : Data = 0x58
   Addr = 0x8080061b0 : Data = 0x4
   hob_length 88 hob_type 4
   Addr = 0x80800620a : Data = 0x58
   Addr = 0x808006208 : Data = 0x4
   hob_length 88 hob_type 4
   Addr = 0x808006262 : Data = 0x58
   Addr = 0x808006260 : Data = 0x4
   hob_length 88 hob_type 4
   Addr = 0x8080062ba : Data = 0x30
   Addr = 0x8080062b8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x8080062ea : Data = 0x30
   Addr = 0x8080062e8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800631a : Data = 0x38
   Addr = 0x808006318 : Data = 0x4
   hob_length 56 hob_type 4
   Addr = 0x808006352 : Data = 0x28
   Addr = 0x808006350 : Data = 0x4
   hob_length 40 hob_type 4
   Addr = 0x80800637a : Data = 0x20
   Addr = 0x808006378 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x80800639a : Data = 0x20
   Addr = 0x808006398 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x8080063ba : Data = 0x20
   Addr = 0x8080063b8 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x8080063da : Data = 0x20
   Addr = 0x8080063d8 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x8080063fa : Data = 0x20
   Addr = 0x8080063f8 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x80800641a : Data = 0x20
   Addr = 0x808006418 : Data = 0x4
   hob_length 32 hob_type 4
   Addr = 0x80800643a : Data = 0x30
   Addr = 0x808006438 : Data = 0x3
   hob_length 48 hob_type 3
   Addr = 0x80800646a : Data = 0x30
   Addr = 0x808006468 : Data = 0x3
   hob_length 48 hob_type 3
   Addr = 0x80800649a : Data = 0x30
   Addr = 0x808006498 : Data = 0x3
   hob_length 48 hob_type 3
   Addr = 0x8080064ca : Data = 0x30
   Addr = 0x8080064c8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x8080064fa : Data = 0x30
   Addr = 0x8080064f8 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800652a : Data = 0x30
   Addr = 0x808006528 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800655a : Data = 0x30
   Addr = 0x808006558 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800658a : Data = 0x60
   Addr = 0x808006588 : Data = 0xb
   hob_length 96 hob_type 11
   Addr = 0x8080065ea : Data = 0x40
   Addr = 0x8080065e8 : Data = 0x9
   hob_length 64 hob_type 9
   Addr = 0x80800662a : Data = 0x30
   Addr = 0x808006628 : Data = 0x2
   hob_length 48 hob_type 2
   Addr = 0x80800665a : Data = 0x18
   Addr = 0x808006658 : Data = 0xc
   hob_length 24 hob_type 12
   Addr = 0x808006672 : Data = 0x18
   Addr = 0x808006670 : Data = 0xd
   hob_length 24 hob_type 13
   Addr = 0x80800668a : Data = 0x10
   Addr = 0x808006688 : Data = 0xa
   hob_length 16 hob_type 10
   Addr = 0x80800669a : Data = 0x30
   Addr = 0x808006698 : Data = 0xe
   hob_length 48 hob_type 14
   Found type 0xe 0x808006698
   Addr = 0x8080066ca : Data = 0x8
   Addr = 0x8080066c8 : Data = 0xffff
   hob_length 8 hob_type 65535
   Found Coredump Table at 0x808006698
   Addr = 0x8080066a0 : Data = 0x83f778a18
   Addr = 0x8080066a8 : Data = 0x83f778768
   Addr = 0x8080066b0 : Data = 0x83f7789e8
   Addr = 0x8080066b8 : Data = 0x83f778750
   Addr = 0x8080066c0 : Data = 0xe
   Addr = 0x83f7789f8 : Data = 0x0
   Addr = 0x83f778760 : Data = 0x0
   gcd_memory_space_map @ 0x83f778a18
   memory_map @ 0x83f778768
     PAGE_SHIFT=14
   Generating Memory Map...
   Memory Map = 0x83f778768
   Addr = 0x83f778768 : Data = 0x83f760448
   Forward link = 0x83f760448
   map_entry is at 0x83f760440
   Addr = 0x83f760440 : Data = 0x70616d6d
   Addr = 0x83f76045c : Data = 0x7
   Addr = 0x83f760460 : Data = 0x800000000
   Addr = 0x83f760468 : Data = 0x807ffffff
   Addr = 0x83f760470 : Data = 0x0
   Addr = 0x83f760478 : Data = 0xf
   Addr = 0x83f760448 : Data = 0x83f761fc8
   map_entry is at 0x83f761fc0
   Addr = 0x83f761fc0 : Data = 0x70616d6d
   Addr = 0x83f761fdc : Data = 0x7
   Addr = 0x83f761fe0 : Data = 0x8083f8000
   Addr = 0x83f761fe8 : Data = 0x8151b7fff
   Addr = 0x83f761ff0 : Data = 0x0
   Addr = 0x83f761ff8 : Data = 0xf
   Addr = 0x83f761fc8 : Data = 0x83f760d08
   map_entry is at 0x83f760d00
   Addr = 0x83f760d00 : Data = 0x70616d6d
   Addr = 0x83f760d1c : Data = 0x4
   Addr = 0x83f760d20 : Data = 0x8151b8000
   Addr = 0x83f760d28 : Data = 0x8155bffff
   Addr = 0x83f760d30 : Data = 0x0
   Addr = 0x83f760d38 : Data = 0xf
   Addr = 0x83f760d08 : Data = 0x83f762a88
   map_entry is at 0x83f762a80
   Addr = 0x83f762a80 : Data = 0x70616d6d
   Addr = 0x83f762a9c : Data = 0xb
   Addr = 0x83f762aa0 : Data = 0x8155c0000
   Addr = 0x83f762aa8 : Data = 0x815dc3fff
   Addr = 0x83f762ab0 : Data = 0x0
   Addr = 0x83f762ab8 : Data = 0xf
   Addr = 0x83f762a88 : Data = 0x83f763908
   map_entry is at 0x83f763900
   Addr = 0x83f763900 : Data = 0x70616d6d
   Addr = 0x83f76391c : Data = 0x4
   Addr = 0x83f763920 : Data = 0x815dc4000
   Addr = 0x83f763928 : Data = 0x816fcffff
   Addr = 0x83f763930 : Data = 0x0
   Addr = 0x83f763938 : Data = 0xf
   Addr = 0x83f763908 : Data = 0x83f7629c8
   map_entry is at 0x83f7629c0
   Addr = 0x83f7629c0 : Data = 0x70616d6d
   Addr = 0x83f7629dc : Data = 0x1
   Addr = 0x83f7629e0 : Data = 0x816fd0000
   Addr = 0x83f7629e8 : Data = 0x816febfff
   Addr = 0x83f7629f0 : Data = 0x0
   Addr = 0x83f7629f8 : Data = 0xf
   Addr = 0x83f7629c8 : Data = 0x83f762fc8
   map_entry is at 0x83f762fc0
   Addr = 0x83f762fc0 : Data = 0x70616d6d
   Addr = 0x83f762fdc : Data = 0x4
   Addr = 0x83f762fe0 : Data = 0x816fec000
   Addr = 0x83f762fe8 : Data = 0x81704bfff
   Addr = 0x83f762ff0 : Data = 0x0
   Addr = 0x83f762ff8 : Data = 0xf
   Addr = 0x83f762fc8 : Data = 0x83f761a08
   map_entry is at 0x83f761a00
   Addr = 0x83f761a00 : Data = 0x70616d6d
   Addr = 0x83f761a1c : Data = 0x3
   Addr = 0x83f761a20 : Data = 0x81704c000
   Addr = 0x83f761a28 : Data = 0x817097fff
   Addr = 0x83f761a30 : Data = 0x0
   Addr = 0x83f761a38 : Data = 0xf
   Addr = 0x83f761a08 : Data = 0x83f762308
   map_entry is at 0x83f762300
   Addr = 0x83f762300 : Data = 0x70616d6d
   Addr = 0x83f76231c : Data = 0x4
   Addr = 0x83f762320 : Data = 0x817098000
   Addr = 0x83f762328 : Data = 0x8170abfff
   Addr = 0x83f762330 : Data = 0x0
   Addr = 0x83f762338 : Data = 0xf
   Addr = 0x83f762308 : Data = 0x83f760148
   map_entry is at 0x83f760140
   Addr = 0x83f760140 : Data = 0x70616d6d
   Addr = 0x83f76015c : Data = 0x3
   Addr = 0x83f760160 : Data = 0x8170ac000
   Addr = 0x83f760168 : Data = 0x8170bbfff
   Addr = 0x83f760170 : Data = 0x0
   Addr = 0x83f760178 : Data = 0xf
   Addr = 0x83f760148 : Data = 0x83f7615c8
   map_entry is at 0x83f7615c0
   Addr = 0x83f7615c0 : Data = 0x70616d6d
   Addr = 0x83f7615dc : Data = 0x4
   Addr = 0x83f7615e0 : Data = 0x8170bc000
   Addr = 0x83f7615e8 : Data = 0x8170cbfff
   Addr = 0x83f7615f0 : Data = 0x0
   Addr = 0x83f7615f8 : Data = 0xf
   Addr = 0x83f7615c8 : Data = 0x83f762348
   map_entry is at 0x83f762340
   Addr = 0x83f762340 : Data = 0x70616d6d
   Addr = 0x83f76235c : Data = 0x3
   Addr = 0x83f762360 : Data = 0x8170cc000
   Addr = 0x83f762368 : Data = 0x8170dffff
   Addr = 0x83f762370 : Data = 0x0
   Addr = 0x83f762378 : Data = 0xf
   Addr = 0x83f762348 : Data = 0x83f763f88
   map_entry is at 0x83f763f80
   Addr = 0x83f763f80 : Data = 0x70616d6d
   Addr = 0x83f763f9c : Data = 0x4
   Addr = 0x83f763fa0 : Data = 0x8170e0000
   Addr = 0x83f763fa8 : Data = 0x8170f3fff
   Addr = 0x83f763fb0 : Data = 0x0
   Addr = 0x83f763fb8 : Data = 0xf
   Addr = 0x83f763f88 : Data = 0x83f762488
   map_entry is at 0x83f762480
   Addr = 0x83f762480 : Data = 0x70616d6d
   Addr = 0x83f76249c : Data = 0x3
   Addr = 0x83f7624a0 : Data = 0x8170f4000
   Addr = 0x83f7624a8 : Data = 0x817103fff
   Addr = 0x83f7624b0 : Data = 0x0
   Addr = 0x83f7624b8 : Data = 0xf
   Addr = 0x83f762488 : Data = 0x83f760908
   map_entry is at 0x83f760900
   Addr = 0x83f760900 : Data = 0x70616d6d
   Addr = 0x83f76091c : Data = 0x1
   Addr = 0x83f760920 : Data = 0x817104000
   Addr = 0x83f760928 : Data = 0x817113fff
   Addr = 0x83f760930 : Data = 0x0
   Addr = 0x83f760938 : Data = 0xf
   Addr = 0x83f760908 : Data = 0x83f760108
   map_entry is at 0x83f760100
   Addr = 0x83f760100 : Data = 0x70616d6d
   Addr = 0x83f76011c : Data = 0x4
   Addr = 0x83f760120 : Data = 0x817114000
   Addr = 0x83f760128 : Data = 0x817133fff
   Addr = 0x83f760130 : Data = 0x0
   Addr = 0x83f760138 : Data = 0xf
   Addr = 0x83f760108 : Data = 0x83f760ac8
   map_entry is at 0x83f760ac0
   Addr = 0x83f760ac0 : Data = 0x70616d6d
   Addr = 0x83f760adc : Data = 0x3
   Addr = 0x83f760ae0 : Data = 0x817134000
   Addr = 0x83f760ae8 : Data = 0x817143fff
   Addr = 0x83f760af0 : Data = 0x0
   Addr = 0x83f760af8 : Data = 0xf
   Addr = 0x83f760ac8 : Data = 0x83f761f48
   map_entry is at 0x83f761f40
   Addr = 0x83f761f40 : Data = 0x70616d6d
   Addr = 0x83f761f5c : Data = 0x4
   Addr = 0x83f761f60 : Data = 0x817144000
   Addr = 0x83f761f68 : Data = 0x817153fff
   Addr = 0x83f761f70 : Data = 0x0
   Addr = 0x83f761f78 : Data = 0xf
   Addr = 0x83f761f48 : Data = 0x83f7630c8
   map_entry is at 0x83f7630c0
   Addr = 0x83f7630c0 : Data = 0x70616d6d
   Addr = 0x83f7630dc : Data = 0x3
   Addr = 0x83f7630e0 : Data = 0x817154000
   Addr = 0x83f7630e8 : Data = 0x817167fff
   Addr = 0x83f7630f0 : Data = 0x0
   Addr = 0x83f7630f8 : Data = 0xf
   Addr = 0x83f7630c8 : Data = 0x83f763108
   map_entry is at 0x83f763100
   Addr = 0x83f763100 : Data = 0x70616d6d
   Addr = 0x83f76311c : Data = 0x4
   Addr = 0x83f763120 : Data = 0x817168000
   Addr = 0x83f763128 : Data = 0x8171cffff
   Addr = 0x83f763130 : Data = 0x0
   Addr = 0x83f763138 : Data = 0xf
   Addr = 0x83f763108 : Data = 0x83f7633c8
   map_entry is at 0x83f7633c0
   Addr = 0x83f7633c0 : Data = 0x70616d6d
   Addr = 0x83f7633dc : Data = 0x3
   Addr = 0x83f7633e0 : Data = 0x8171d0000
   Addr = 0x83f7633e8 : Data = 0x8171f3fff
   Addr = 0x83f7633f0 : Data = 0x0
   Addr = 0x83f7633f8 : Data = 0xf
   Addr = 0x83f7633c8 : Data = 0x83f761f88
   map_entry is at 0x83f761f80
   Addr = 0x83f761f80 : Data = 0x70616d6d
   Addr = 0x83f761f9c : Data = 0x4
   Addr = 0x83f761fa0 : Data = 0x8171f4000
   Addr = 0x83f761fa8 : Data = 0x817217fff
   Addr = 0x83f761fb0 : Data = 0x0
   Addr = 0x83f761fb8 : Data = 0xf
   Addr = 0x83f761f88 : Data = 0x83f7631c8
   map_entry is at 0x83f7631c0
   Addr = 0x83f7631c0 : Data = 0x70616d6d
   Addr = 0x83f7631dc : Data = 0x3
   Addr = 0x83f7631e0 : Data = 0x817218000
   Addr = 0x83f7631e8 : Data = 0x81724bfff
   Addr = 0x83f7631f0 : Data = 0x0
   Addr = 0x83f7631f8 : Data = 0xf
   Addr = 0x83f7631c8 : Data = 0x83f762cc8
   map_entry is at 0x83f762cc0
   Addr = 0x83f762cc0 : Data = 0x70616d6d
   Addr = 0x83f762cdc : Data = 0x6
   Addr = 0x83f762ce0 : Data = 0x81724c000
   Addr = 0x83f762ce8 : Data = 0x81728bfff
   Addr = 0x83f762cf0 : Data = 0x0
   Addr = 0x83f762cf8 : Data = 0xf
   Addr = 0x83f762cc8 : Data = 0x83f762dc8
   map_entry is at 0x83f762dc0
   Addr = 0x83f762dc0 : Data = 0x70616d6d
   Addr = 0x83f762ddc : Data = 0x3
   Addr = 0x83f762de0 : Data = 0x81728c000
   Addr = 0x83f762de8 : Data = 0x8172b3fff
   Addr = 0x83f762df0 : Data = 0x0
   Addr = 0x83f762df8 : Data = 0xf
   Addr = 0x83f762dc8 : Data = 0x83f760c48
   map_entry is at 0x83f760c40
   Addr = 0x83f760c40 : Data = 0x70616d6d
   Addr = 0x83f760c5c : Data = 0x4
   Addr = 0x83f760c60 : Data = 0x8172b4000
   Addr = 0x83f760c68 : Data = 0x8172c7fff
   Addr = 0x83f760c70 : Data = 0x0
   Addr = 0x83f760c78 : Data = 0xf
   Addr = 0x83f760c48 : Data = 0x83f7625c8
   map_entry is at 0x83f7625c0
   Addr = 0x83f7625c0 : Data = 0x70616d6d
   Addr = 0x83f7625dc : Data = 0x3
   Addr = 0x83f7625e0 : Data = 0x8172c8000
   Addr = 0x83f7625e8 : Data = 0x81730ffff
   Addr = 0x83f7625f0 : Data = 0x0
   Addr = 0x83f7625f8 : Data = 0xf
   Addr = 0x83f7625c8 : Data = 0x83f763708
   map_entry is at 0x83f763700
   Addr = 0x83f763700 : Data = 0x70616d6d
   Addr = 0x83f76371c : Data = 0x4
   Addr = 0x83f763720 : Data = 0x817310000
   Addr = 0x83f763728 : Data = 0x81731bfff
   Addr = 0x83f763730 : Data = 0x0
   Addr = 0x83f763738 : Data = 0xf
   Addr = 0x83f763708 : Data = 0x83f762ec8
   map_entry is at 0x83f762ec0
   Addr = 0x83f762ec0 : Data = 0x70616d6d
   Addr = 0x83f762edc : Data = 0x6
   Addr = 0x83f762ee0 : Data = 0x81731c000
   Addr = 0x83f762ee8 : Data = 0x81731ffff
   Addr = 0x83f762ef0 : Data = 0x0
   Addr = 0x83f762ef8 : Data = 0xf
   Addr = 0x83f762ec8 : Data = 0x83f762748
   map_entry is at 0x83f762740
   Addr = 0x83f762740 : Data = 0x70616d6d
   Addr = 0x83f76275c : Data = 0x3
   Addr = 0x83f762760 : Data = 0x817320000
   Addr = 0x83f762768 : Data = 0x81733ffff
   Addr = 0x83f762770 : Data = 0x0
   Addr = 0x83f762778 : Data = 0xf
   Addr = 0x83f762748 : Data = 0x83f762f88
   map_entry is at 0x83f762f80
   Addr = 0x83f762f80 : Data = 0x70616d6d
   Addr = 0x83f762f9c : Data = 0xb
   Addr = 0x83f762fa0 : Data = 0x817340000
   Addr = 0x83f762fa8 : Data = 0x817347fff
   Addr = 0x83f762fb0 : Data = 0x0
   Addr = 0x83f762fb8 : Data = 0xf
   Addr = 0x83f762f88 : Data = 0x83f762ac8
   map_entry is at 0x83f762ac0
   Addr = 0x83f762ac0 : Data = 0x70616d6d
   Addr = 0x83f762adc : Data = 0x4
   Addr = 0x83f762ae0 : Data = 0x817348000
   Addr = 0x83f762ae8 : Data = 0x81734ffff
   Addr = 0x83f762af0 : Data = 0x0
   Addr = 0x83f762af8 : Data = 0xf
   Addr = 0x83f762ac8 : Data = 0x83f760948
   map_entry is at 0x83f760940
   Addr = 0x83f760940 : Data = 0x70616d6d
   Addr = 0x83f76095c : Data = 0xb
   Addr = 0x83f760960 : Data = 0x817350000
   Addr = 0x83f760968 : Data = 0x817397fff
   Addr = 0x83f760970 : Data = 0x0
   Addr = 0x83f760978 : Data = 0xf
   Addr = 0x83f760948 : Data = 0x83f760888
   map_entry is at 0x83f760880
   Addr = 0x83f760880 : Data = 0x70616d6d
   Addr = 0x83f76089c : Data = 0x8
   Addr = 0x83f7608a0 : Data = 0x817398000
   Addr = 0x83f7608a8 : Data = 0x83b85bfff
   Addr = 0x83f7608b0 : Data = 0x0
   Addr = 0x83f7608b8 : Data = 0xf
   Addr = 0x83f760888 : Data = 0x83f7601c8
   map_entry is at 0x83f7601c0
   Addr = 0x83f7601c0 : Data = 0x70616d6d
   Addr = 0x83f7601dc : Data = 0x3
   Addr = 0x83f7601e0 : Data = 0x83b85c000
   Addr = 0x83f7601e8 : Data = 0x83bb7ffff
   Addr = 0x83f7601f0 : Data = 0x0
   Addr = 0x83f7601f8 : Data = 0xf
   Addr = 0x83f7601c8 : Data = 0x83f762888
   map_entry is at 0x83f762880
   Addr = 0x83f762880 : Data = 0x70616d6d
   Addr = 0x83f76289c : Data = 0x4
   Addr = 0x83f7628a0 : Data = 0x83bb80000
   Addr = 0x83f7628a8 : Data = 0x83bb97fff
   Addr = 0x83f7628b0 : Data = 0x0
   Addr = 0x83f7628b8 : Data = 0xf
   Addr = 0x83f762888 : Data = 0x83f7614c8
   map_entry is at 0x83f7614c0
   Addr = 0x83f7614c0 : Data = 0x70616d6d
   Addr = 0x83f7614dc : Data = 0xb
   Addr = 0x83f7614e0 : Data = 0x83bb98000
   Addr = 0x83f7614e8 : Data = 0x83bbe7fff
   Addr = 0x83f7614f0 : Data = 0x0
   Addr = 0x83f7614f8 : Data = 0xf
   Addr = 0x83f7614c8 : Data = 0x83f760088
   map_entry is at 0x83f760080
   Addr = 0x83f760080 : Data = 0x70616d6d
   Addr = 0x83f76009c : Data = 0x3
   Addr = 0x83f7600a0 : Data = 0x83bbe8000
   Addr = 0x83f7600a8 : Data = 0x83bc8bfff
   Addr = 0x83f7600b0 : Data = 0x0
   Addr = 0x83f7600b8 : Data = 0xf
   Addr = 0x83f760088 : Data = 0x83f7611c8
   map_entry is at 0x83f7611c0
   Addr = 0x83f7611c0 : Data = 0x70616d6d
   Addr = 0x83f7611dc : Data = 0xb
   Addr = 0x83f7611e0 : Data = 0x83bc8c000
   Addr = 0x83f7611e8 : Data = 0x83bcbbfff
   Addr = 0x83f7611f0 : Data = 0x0
   Addr = 0x83f7611f8 : Data = 0xf
   Addr = 0x83f7611c8 : Data = 0x83f762d08
   map_entry is at 0x83f762d00
   Addr = 0x83f762d00 : Data = 0x70616d6d
   Addr = 0x83f762d1c : Data = 0x3
   Addr = 0x83f762d20 : Data = 0x83bcbc000
   Addr = 0x83f762d28 : Data = 0x83bccffff
   Addr = 0x83f762d30 : Data = 0x0
   Addr = 0x83f762d38 : Data = 0xf
   Addr = 0x83f762d08 : Data = 0x83f760b88
   map_entry is at 0x83f760b80
   Addr = 0x83f760b80 : Data = 0x70616d6d
   Addr = 0x83f760b9c : Data = 0xb
   Addr = 0x83f760ba0 : Data = 0x83bcd0000
   Addr = 0x83f760ba8 : Data = 0x83bcdffff
   Addr = 0x83f760bb0 : Data = 0x0
   Addr = 0x83f760bb8 : Data = 0xf
   Addr = 0x83f760b88 : Data = 0x83f760708
   map_entry is at 0x83f760700
   Addr = 0x83f760700 : Data = 0x70616d6d
   Addr = 0x83f76071c : Data = 0x4
   Addr = 0x83f760720 : Data = 0x83bce0000
   Addr = 0x83f760728 : Data = 0x83bce3fff
   Addr = 0x83f760730 : Data = 0x0
   Addr = 0x83f760738 : Data = 0xf
   Addr = 0x83f760708 : Data = 0x83f763f08
   map_entry is at 0x83f763f00
   Addr = 0x83f763f00 : Data = 0x70616d6d
   Addr = 0x83f763f1c : Data = 0x3
   Addr = 0x83f763f20 : Data = 0x83bce4000
   Addr = 0x83f763f28 : Data = 0x83bd4ffff
   Addr = 0x83f763f30 : Data = 0x0
   Addr = 0x83f763f38 : Data = 0xf
   Addr = 0x83f763f08 : Data = 0x83f762d88
   map_entry is at 0x83f762d80
   Addr = 0x83f762d80 : Data = 0x70616d6d
   Addr = 0x83f762d9c : Data = 0x4
   Addr = 0x83f762da0 : Data = 0x83bd50000
   Addr = 0x83f762da8 : Data = 0x83bd5bfff
   Addr = 0x83f762db0 : Data = 0x0
   Addr = 0x83f762db8 : Data = 0xf
   Addr = 0x83f762d88 : Data = 0x83f7639c8
   map_entry is at 0x83f7639c0
   Addr = 0x83f7639c0 : Data = 0x70616d6d
   Addr = 0x83f7639dc : Data = 0x3
   Addr = 0x83f7639e0 : Data = 0x83bd5c000
   Addr = 0x83f7639e8 : Data = 0x83be67fff
   Addr = 0x83f7639f0 : Data = 0x0
   Addr = 0x83f7639f8 : Data = 0xf
   Addr = 0x83f7639c8 : Data = 0x83f7608c8
   map_entry is at 0x83f7608c0
   Addr = 0x83f7608c0 : Data = 0x70616d6d
   Addr = 0x83f7608dc : Data = 0x4
   Addr = 0x83f7608e0 : Data = 0x83be68000
   Addr = 0x83f7608e8 : Data = 0x83be7ffff
   Addr = 0x83f7608f0 : Data = 0x0
   Addr = 0x83f7608f8 : Data = 0xf
   Addr = 0x83f7608c8 : Data = 0x83f761d48
   map_entry is at 0x83f761d40
   Addr = 0x83f761d40 : Data = 0x70616d6d
   Addr = 0x83f761d5c : Data = 0x3
   Addr = 0x83f761d60 : Data = 0x83be80000
   Addr = 0x83f761d68 : Data = 0x83bee3fff
   Addr = 0x83f761d70 : Data = 0x0
   Addr = 0x83f761d78 : Data = 0xf
   Addr = 0x83f761d48 : Data = 0x83f763548
   map_entry is at 0x83f763540
   Addr = 0x83f763540 : Data = 0x70616d6d
   Addr = 0x83f76355c : Data = 0x4
   Addr = 0x83f763560 : Data = 0x83bee4000
   Addr = 0x83f763568 : Data = 0x83bee7fff
   Addr = 0x83f763570 : Data = 0x0
   Addr = 0x83f763578 : Data = 0xf
   Addr = 0x83f763548 : Data = 0x83f761988
   map_entry is at 0x83f761980
   Addr = 0x83f761980 : Data = 0x70616d6d
   Addr = 0x83f76199c : Data = 0x3
   Addr = 0x83f7619a0 : Data = 0x83bee8000
   Addr = 0x83f7619a8 : Data = 0x83bf47fff
   Addr = 0x83f7619b0 : Data = 0x0
   Addr = 0x83f7619b8 : Data = 0xf
   Addr = 0x83f761988 : Data = 0x83f763508
   map_entry is at 0x83f763500
   Addr = 0x83f763500 : Data = 0x70616d6d
   Addr = 0x83f76351c : Data = 0x4
   Addr = 0x83f763520 : Data = 0x83bf48000
   Addr = 0x83f763528 : Data = 0x83bf4bfff
   Addr = 0x83f763530 : Data = 0x0
   Addr = 0x83f763538 : Data = 0xf
   Addr = 0x83f763508 : Data = 0x83f761588
   map_entry is at 0x83f761580
   Addr = 0x83f761580 : Data = 0x70616d6d
   Addr = 0x83f76159c : Data = 0x3
   Addr = 0x83f7615a0 : Data = 0x83bf4c000
   Addr = 0x83f7615a8 : Data = 0x83bf6bfff
   Addr = 0x83f7615b0 : Data = 0x0
   Addr = 0x83f7615b8 : Data = 0xf
   Addr = 0x83f761588 : Data = 0x83f763248
   map_entry is at 0x83f763240
   Addr = 0x83f763240 : Data = 0x70616d6d
   Addr = 0x83f76325c : Data = 0x4
   Addr = 0x83f763260 : Data = 0x83bf6c000
   Addr = 0x83f763268 : Data = 0x83bf7bfff
   Addr = 0x83f763270 : Data = 0x0
   Addr = 0x83f763278 : Data = 0xf
   Addr = 0x83f763248 : Data = 0x83f761208
   map_entry is at 0x83f761200
   Addr = 0x83f761200 : Data = 0x70616d6d
   Addr = 0x83f76121c : Data = 0x3
   Addr = 0x83f761220 : Data = 0x83bf7c000
   Addr = 0x83f761228 : Data = 0x83bfdbfff
   Addr = 0x83f761230 : Data = 0x0
   Addr = 0x83f761238 : Data = 0xf
   Addr = 0x83f761208 : Data = 0x83f7617c8
   map_entry is at 0x83f7617c0
   Addr = 0x83f7617c0 : Data = 0x70616d6d
   Addr = 0x83f7617dc : Data = 0x4
   Addr = 0x83f7617e0 : Data = 0x83bfdc000
   Addr = 0x83f7617e8 : Data = 0x83bfe3fff
   Addr = 0x83f7617f0 : Data = 0x0
   Addr = 0x83f7617f8 : Data = 0xf
   Addr = 0x83f7617c8 : Data = 0x83f760808
   map_entry is at 0x83f760800
   Addr = 0x83f760800 : Data = 0x70616d6d
   Addr = 0x83f76081c : Data = 0x3
   Addr = 0x83f760820 : Data = 0x83bfe4000
   Addr = 0x83f760828 : Data = 0x83bff7fff
   Addr = 0x83f760830 : Data = 0x0
   Addr = 0x83f760838 : Data = 0xf
   Addr = 0x83f760808 : Data = 0x83f761e88
   map_entry is at 0x83f761e80
   Addr = 0x83f761e80 : Data = 0x70616d6d
   Addr = 0x83f761e9c : Data = 0x4
   Addr = 0x83f761ea0 : Data = 0x83bff8000
   Addr = 0x83f761ea8 : Data = 0x83bffbfff
   Addr = 0x83f761eb0 : Data = 0x0
   Addr = 0x83f761eb8 : Data = 0xf
   Addr = 0x83f761e88 : Data = 0x83f760a08
   map_entry is at 0x83f760a00
   Addr = 0x83f760a00 : Data = 0x70616d6d
   Addr = 0x83f760a1c : Data = 0x3
   Addr = 0x83f760a20 : Data = 0x83bffc000
   Addr = 0x83f760a28 : Data = 0x83c02bfff
   Addr = 0x83f760a30 : Data = 0x0
   Addr = 0x83f760a38 : Data = 0xf
   Addr = 0x83f760a08 : Data = 0x83f761c88
   map_entry is at 0x83f761c80
   Addr = 0x83f761c80 : Data = 0x70616d6d
   Addr = 0x83f761c9c : Data = 0x4
   Addr = 0x83f761ca0 : Data = 0x83c02c000
   Addr = 0x83f761ca8 : Data = 0x83c03bfff
   Addr = 0x83f761cb0 : Data = 0x0
   Addr = 0x83f761cb8 : Data = 0xf
   Addr = 0x83f761c88 : Data = 0x83f760488
   map_entry is at 0x83f760480
   Addr = 0x83f760480 : Data = 0x70616d6d
   Addr = 0x83f76049c : Data = 0x3
   Addr = 0x83f7604a0 : Data = 0x83c03c000
   Addr = 0x83f7604a8 : Data = 0x83c16bfff
   Addr = 0x83f7604b0 : Data = 0x0
   Addr = 0x83f7604b8 : Data = 0xf
   Addr = 0x83f760488 : Data = 0x83f760c08
   map_entry is at 0x83f760c00
   Addr = 0x83f760c00 : Data = 0x70616d6d
   Addr = 0x83f760c1c : Data = 0x4
   Addr = 0x83f760c20 : Data = 0x83c16c000
   Addr = 0x83f760c28 : Data = 0x83c16ffff
   Addr = 0x83f760c30 : Data = 0x0
   Addr = 0x83f760c38 : Data = 0xf
   Addr = 0x83f760c08 : Data = 0x83f762e08
   map_entry is at 0x83f762e00
   Addr = 0x83f762e00 : Data = 0x70616d6d
   Addr = 0x83f762e1c : Data = 0x3
   Addr = 0x83f762e20 : Data = 0x83c170000
   Addr = 0x83f762e28 : Data = 0x83c1a7fff
   Addr = 0x83f762e30 : Data = 0x0
   Addr = 0x83f762e38 : Data = 0xf
   Addr = 0x83f762e08 : Data = 0x83f760848
   map_entry is at 0x83f760840
   Addr = 0x83f760840 : Data = 0x70616d6d
   Addr = 0x83f76085c : Data = 0x4
   Addr = 0x83f760860 : Data = 0x83c1a8000
   Addr = 0x83f760868 : Data = 0x83c1affff
   Addr = 0x83f760870 : Data = 0x0
   Addr = 0x83f760878 : Data = 0xf
   Addr = 0x83f760848 : Data = 0x83f762788
   map_entry is at 0x83f762780
   Addr = 0x83f762780 : Data = 0x70616d6d
   Addr = 0x83f76279c : Data = 0x3
   Addr = 0x83f7627a0 : Data = 0x83c1b0000
   Addr = 0x83f7627a8 : Data = 0x83c36ffff
   Addr = 0x83f7627b0 : Data = 0x0
   Addr = 0x83f7627b8 : Data = 0xf
   Addr = 0x83f762788 : Data = 0x83f763b08
   map_entry is at 0x83f763b00
   Addr = 0x83f763b00 : Data = 0x70616d6d
   Addr = 0x83f763b1c : Data = 0x4
   Addr = 0x83f763b20 : Data = 0x83c370000
   Addr = 0x83f763b28 : Data = 0x83c373fff
   Addr = 0x83f763b30 : Data = 0x0
   Addr = 0x83f763b38 : Data = 0xf
   Addr = 0x83f763b08 : Data = 0x83f762808
   map_entry is at 0x83f762800
   Addr = 0x83f762800 : Data = 0x70616d6d
   Addr = 0x83f76281c : Data = 0x3
   Addr = 0x83f762820 : Data = 0x83c374000
   Addr = 0x83f762828 : Data = 0x83c3abfff
   Addr = 0x83f762830 : Data = 0x0
   Addr = 0x83f762838 : Data = 0xf
   Addr = 0x83f762808 : Data = 0x83f763188
   map_entry is at 0x83f763180
   Addr = 0x83f763180 : Data = 0x70616d6d
   Addr = 0x83f76319c : Data = 0x4
   Addr = 0x83f7631a0 : Data = 0x83c3ac000
   Addr = 0x83f7631a8 : Data = 0x83c3b3fff
   Addr = 0x83f7631b0 : Data = 0x0
   Addr = 0x83f7631b8 : Data = 0xf
   Addr = 0x83f763188 : Data = 0x83f762f48
   map_entry is at 0x83f762f40
   Addr = 0x83f762f40 : Data = 0x70616d6d
   Addr = 0x83f762f5c : Data = 0x3
   Addr = 0x83f762f60 : Data = 0x83c3b4000
   Addr = 0x83f762f68 : Data = 0x83c45ffff
   Addr = 0x83f762f70 : Data = 0x0
   Addr = 0x83f762f78 : Data = 0xf
   Addr = 0x83f762f48 : Data = 0x83f762c88
   map_entry is at 0x83f762c80
   Addr = 0x83f762c80 : Data = 0x70616d6d
   Addr = 0x83f762c9c : Data = 0x4
   Addr = 0x83f762ca0 : Data = 0x83c460000
   Addr = 0x83f762ca8 : Data = 0x83c463fff
   Addr = 0x83f762cb0 : Data = 0x0
   Addr = 0x83f762cb8 : Data = 0xf
   Addr = 0x83f762c88 : Data = 0x83f761cc8
   map_entry is at 0x83f761cc0
   Addr = 0x83f761cc0 : Data = 0x70616d6d
   Addr = 0x83f761cdc : Data = 0x3
   Addr = 0x83f761ce0 : Data = 0x83c464000
   Addr = 0x83f761ce8 : Data = 0x83c4b3fff
   Addr = 0x83f761cf0 : Data = 0x0
   Addr = 0x83f761cf8 : Data = 0xf
   Addr = 0x83f761cc8 : Data = 0x83f762988
   map_entry is at 0x83f762980
   Addr = 0x83f762980 : Data = 0x70616d6d
   Addr = 0x83f76299c : Data = 0x4
   Addr = 0x83f7629a0 : Data = 0x83c4b4000
   Addr = 0x83f7629a8 : Data = 0x83c4cbfff
   Addr = 0x83f7629b0 : Data = 0x0
   Addr = 0x83f7629b8 : Data = 0xf
   Addr = 0x83f762988 : Data = 0x83f761088
   map_entry is at 0x83f761080
   Addr = 0x83f761080 : Data = 0x70616d6d
   Addr = 0x83f76109c : Data = 0x3
   Addr = 0x83f7610a0 : Data = 0x83c4cc000
   Addr = 0x83f7610a8 : Data = 0x83c527fff
   Addr = 0x83f7610b0 : Data = 0x0
   Addr = 0x83f7610b8 : Data = 0xf
   Addr = 0x83f761088 : Data = 0x83f760508
   map_entry is at 0x83f760500
   Addr = 0x83f760500 : Data = 0x70616d6d
   Addr = 0x83f76051c : Data = 0x4
   Addr = 0x83f760520 : Data = 0x83c528000
   Addr = 0x83f760528 : Data = 0x83c52bfff
   Addr = 0x83f760530 : Data = 0x0
   Addr = 0x83f760538 : Data = 0xf
   Addr = 0x83f760508 : Data = 0x83f760e48
   map_entry is at 0x83f760e40
   Addr = 0x83f760e40 : Data = 0x70616d6d
   Addr = 0x83f760e5c : Data = 0x3
   Addr = 0x83f760e60 : Data = 0x83c52c000
   Addr = 0x83f760e68 : Data = 0x83c563fff
   Addr = 0x83f760e70 : Data = 0x0
   Addr = 0x83f760e78 : Data = 0xf
   Addr = 0x83f760e48 : Data = 0x83f7613c8
   map_entry is at 0x83f7613c0
   Addr = 0x83f7613c0 : Data = 0x70616d6d
   Addr = 0x83f7613dc : Data = 0x4
   Addr = 0x83f7613e0 : Data = 0x83c564000
   Addr = 0x83f7613e8 : Data = 0x83c56bfff
   Addr = 0x83f7613f0 : Data = 0x0
   Addr = 0x83f7613f8 : Data = 0xf
   Addr = 0x83f7613c8 : Data = 0x83f7607c8
   map_entry is at 0x83f7607c0
   Addr = 0x83f7607c0 : Data = 0x70616d6d
   Addr = 0x83f7607dc : Data = 0x3
   Addr = 0x83f7607e0 : Data = 0x83c56c000
   Addr = 0x83f7607e8 : Data = 0x83c593fff
   Addr = 0x83f7607f0 : Data = 0x0
   Addr = 0x83f7607f8 : Data = 0xf
   Addr = 0x83f7607c8 : Data = 0x83f761248
   map_entry is at 0x83f761240
   Addr = 0x83f761240 : Data = 0x70616d6d
   Addr = 0x83f76125c : Data = 0x4
   Addr = 0x83f761260 : Data = 0x83c594000
   Addr = 0x83f761268 : Data = 0x83c59bfff
   Addr = 0x83f761270 : Data = 0x0
   Addr = 0x83f761278 : Data = 0xf
   Addr = 0x83f761248 : Data = 0x83f7606c8
   map_entry is at 0x83f7606c0
   Addr = 0x83f7606c0 : Data = 0x70616d6d
   Addr = 0x83f7606dc : Data = 0x3
   Addr = 0x83f7606e0 : Data = 0x83c59c000
   Addr = 0x83f7606e8 : Data = 0x83c61bfff
   Addr = 0x83f7606f0 : Data = 0x0
   Addr = 0x83f7606f8 : Data = 0xf
   Addr = 0x83f7606c8 : Data = 0x83f761608
   map_entry is at 0x83f761600
   Addr = 0x83f761600 : Data = 0x70616d6d
   Addr = 0x83f76161c : Data = 0x4
   Addr = 0x83f761620 : Data = 0x83c61c000
   Addr = 0x83f761628 : Data = 0x83c61ffff
   Addr = 0x83f761630 : Data = 0x0
   Addr = 0x83f761638 : Data = 0xf
   Addr = 0x83f761608 : Data = 0x83f7602c8
   map_entry is at 0x83f7602c0
   Addr = 0x83f7602c0 : Data = 0x70616d6d
   Addr = 0x83f7602dc : Data = 0x3
   Addr = 0x83f7602e0 : Data = 0x83c620000
   Addr = 0x83f7602e8 : Data = 0x83c62ffff
   Addr = 0x83f7602f0 : Data = 0x0
   Addr = 0x83f7602f8 : Data = 0xf
   Addr = 0x83f7602c8 : Data = 0x83f760f08
   map_entry is at 0x83f760f00
   Addr = 0x83f760f00 : Data = 0x70616d6d
   Addr = 0x83f760f1c : Data = 0x4
   Addr = 0x83f760f20 : Data = 0x83c630000
   Addr = 0x83f760f28 : Data = 0x83c63ffff
   Addr = 0x83f760f30 : Data = 0x0
   Addr = 0x83f760f38 : Data = 0xf
   Addr = 0x83f760f08 : Data = 0x83f763d08
   map_entry is at 0x83f763d00
   Addr = 0x83f763d00 : Data = 0x70616d6d
   Addr = 0x83f763d1c : Data = 0x3
   Addr = 0x83f763d20 : Data = 0x83c640000
   Addr = 0x83f763d28 : Data = 0x83c6a7fff
   Addr = 0x83f763d30 : Data = 0x0
   Addr = 0x83f763d38 : Data = 0xf
   Addr = 0x83f763d08 : Data = 0x83f761288
   map_entry is at 0x83f761280
   Addr = 0x83f761280 : Data = 0x70616d6d
   Addr = 0x83f76129c : Data = 0x4
   Addr = 0x83f7612a0 : Data = 0x83c6a8000
   Addr = 0x83f7612a8 : Data = 0x83c6affff
   Addr = 0x83f7612b0 : Data = 0x0
   Addr = 0x83f7612b8 : Data = 0xf
   Addr = 0x83f761288 : Data = 0x83f763cc8
   map_entry is at 0x83f763cc0
   Addr = 0x83f763cc0 : Data = 0x70616d6d
   Addr = 0x83f763cdc : Data = 0x3
   Addr = 0x83f763ce0 : Data = 0x83c6b0000
   Addr = 0x83f763ce8 : Data = 0x83c6d3fff
   Addr = 0x83f763cf0 : Data = 0x0
   Addr = 0x83f763cf8 : Data = 0xf
   Addr = 0x83f763cc8 : Data = 0x83f760ec8
   map_entry is at 0x83f760ec0
   Addr = 0x83f760ec0 : Data = 0x70616d6d
   Addr = 0x83f760edc : Data = 0x4
   Addr = 0x83f760ee0 : Data = 0x83c6d4000
   Addr = 0x83f760ee8 : Data = 0x83c6d7fff
   Addr = 0x83f760ef0 : Data = 0x0
   Addr = 0x83f760ef8 : Data = 0xf
   Addr = 0x83f760ec8 : Data = 0x83f763048
   map_entry is at 0x83f763040
   Addr = 0x83f763040 : Data = 0x70616d6d
   Addr = 0x83f76305c : Data = 0x3
   Addr = 0x83f763060 : Data = 0x83c6d8000
   Addr = 0x83f763068 : Data = 0x83c707fff
   Addr = 0x83f763070 : Data = 0x0
   Addr = 0x83f763078 : Data = 0xf
   Addr = 0x83f763048 : Data = 0x83f760c88
   map_entry is at 0x83f760c80
   Addr = 0x83f760c80 : Data = 0x70616d6d
   Addr = 0x83f760c9c : Data = 0x4
   Addr = 0x83f760ca0 : Data = 0x83c708000
   Addr = 0x83f760ca8 : Data = 0x83c717fff
   Addr = 0x83f760cb0 : Data = 0x0
   Addr = 0x83f760cb8 : Data = 0xf
   Addr = 0x83f760c88 : Data = 0x83f763348
   map_entry is at 0x83f763340
   Addr = 0x83f763340 : Data = 0x70616d6d
   Addr = 0x83f76335c : Data = 0x3
   Addr = 0x83f763360 : Data = 0x83c718000
   Addr = 0x83f763368 : Data = 0x83c737fff
   Addr = 0x83f763370 : Data = 0x0
   Addr = 0x83f763378 : Data = 0xf
   Addr = 0x83f763348 : Data = 0x83f763148
   map_entry is at 0x83f763140
   Addr = 0x83f763140 : Data = 0x70616d6d
   Addr = 0x83f76315c : Data = 0x4
   Addr = 0x83f763160 : Data = 0x83c738000
   Addr = 0x83f763168 : Data = 0x83c93bfff
   Addr = 0x83f763170 : Data = 0x0
   Addr = 0x83f763178 : Data = 0xf
   Addr = 0x83f763148 : Data = 0x83f763008
   map_entry is at 0x83f763000
   Addr = 0x83f763000 : Data = 0x70616d6d
   Addr = 0x83f76301c : Data = 0x3
   Addr = 0x83f763020 : Data = 0x83c93c000
   Addr = 0x83f763028 : Data = 0x83c9a7fff
   Addr = 0x83f763030 : Data = 0x0
   Addr = 0x83f763038 : Data = 0xf
   Addr = 0x83f763008 : Data = 0x83f763b48
   map_entry is at 0x83f763b40
   Addr = 0x83f763b40 : Data = 0x70616d6d
   Addr = 0x83f763b5c : Data = 0x4
   Addr = 0x83f763b60 : Data = 0x83c9a8000
   Addr = 0x83f763b68 : Data = 0x83c9b3fff
   Addr = 0x83f763b70 : Data = 0x0
   Addr = 0x83f763b78 : Data = 0xf
   Addr = 0x83f763b48 : Data = 0x83f762c48
   map_entry is at 0x83f762c40
   Addr = 0x83f762c40 : Data = 0x70616d6d
   Addr = 0x83f762c5c : Data = 0x3
   Addr = 0x83f762c60 : Data = 0x83c9b4000
   Addr = 0x83f762c68 : Data = 0x83ca0bfff
   Addr = 0x83f762c70 : Data = 0x0
   Addr = 0x83f762c78 : Data = 0xf
   Addr = 0x83f762c48 : Data = 0x83f763848
   map_entry is at 0x83f763840
   Addr = 0x83f763840 : Data = 0x70616d6d
   Addr = 0x83f76385c : Data = 0x4
   Addr = 0x83f763860 : Data = 0x83ca0c000
   Addr = 0x83f763868 : Data = 0x83ca0ffff
   Addr = 0x83f763870 : Data = 0x0
   Addr = 0x83f763878 : Data = 0xf
   Addr = 0x83f763848 : Data = 0x83f763488
   map_entry is at 0x83f763480
   Addr = 0x83f763480 : Data = 0x70616d6d
   Addr = 0x83f76349c : Data = 0x6
   Addr = 0x83f7634a0 : Data = 0x83ca10000
   Addr = 0x83f7634a8 : Data = 0x83ca13fff
   Addr = 0x83f7634b0 : Data = 0x0
   Addr = 0x83f7634b8 : Data = 0xf
   Addr = 0x83f763488 : Data = 0x83f7632c8
   map_entry is at 0x83f7632c0
   Addr = 0x83f7632c0 : Data = 0x70616d6d
   Addr = 0x83f7632dc : Data = 0x4
   Addr = 0x83f7632e0 : Data = 0x83ca14000
   Addr = 0x83f7632e8 : Data = 0x83ca43fff
   Addr = 0x83f7632f0 : Data = 0x0
   Addr = 0x83f7632f8 : Data = 0xf
   Addr = 0x83f7632c8 : Data = 0x83f7621c8
   map_entry is at 0x83f7621c0
   Addr = 0x83f7621c0 : Data = 0x70616d6d
   Addr = 0x83f7621dc : Data = 0x3
   Addr = 0x83f7621e0 : Data = 0x83ca44000
   Addr = 0x83f7621e8 : Data = 0x83ca5bfff
   Addr = 0x83f7621f0 : Data = 0x0
   Addr = 0x83f7621f8 : Data = 0xf
   Addr = 0x83f7621c8 : Data = 0x83f763308
   map_entry is at 0x83f763300
   Addr = 0x83f763300 : Data = 0x70616d6d
   Addr = 0x83f76331c : Data = 0x4
   Addr = 0x83f763320 : Data = 0x83ca5c000
   Addr = 0x83f763328 : Data = 0x83ca63fff
   Addr = 0x83f763330 : Data = 0x0
   Addr = 0x83f763338 : Data = 0xf
   Addr = 0x83f763308 : Data = 0x83f762388
   map_entry is at 0x83f762380
   Addr = 0x83f762380 : Data = 0x70616d6d
   Addr = 0x83f76239c : Data = 0x3
   Addr = 0x83f7623a0 : Data = 0x83ca64000
   Addr = 0x83f7623a8 : Data = 0x83ca9ffff
   Addr = 0x83f7623b0 : Data = 0x0
   Addr = 0x83f7623b8 : Data = 0xf
   Addr = 0x83f762388 : Data = 0x83f762d48
   map_entry is at 0x83f762d40
   Addr = 0x83f762d40 : Data = 0x70616d6d
   Addr = 0x83f762d5c : Data = 0x4
   Addr = 0x83f762d60 : Data = 0x83caa0000
   Addr = 0x83f762d68 : Data = 0x83caa7fff
   Addr = 0x83f762d70 : Data = 0x0
   Addr = 0x83f762d78 : Data = 0xf
   Addr = 0x83f762d48 : Data = 0x83f762208
   map_entry is at 0x83f762200
   Addr = 0x83f762200 : Data = 0x70616d6d
   Addr = 0x83f76221c : Data = 0x3
   Addr = 0x83f762220 : Data = 0x83caa8000
   Addr = 0x83f762228 : Data = 0x83cafffff
   Addr = 0x83f762230 : Data = 0x0
   Addr = 0x83f762238 : Data = 0xf
   Addr = 0x83f762208 : Data = 0x83f762b08
   map_entry is at 0x83f762b00
   Addr = 0x83f762b00 : Data = 0x70616d6d
   Addr = 0x83f762b1c : Data = 0x4
   Addr = 0x83f762b20 : Data = 0x83cb00000
   Addr = 0x83f762b28 : Data = 0x83cb07fff
   Addr = 0x83f762b30 : Data = 0x0
   Addr = 0x83f762b38 : Data = 0xf
   Addr = 0x83f762b08 : Data = 0x83f762708
   map_entry is at 0x83f762700
   Addr = 0x83f762700 : Data = 0x70616d6d
   Addr = 0x83f76271c : Data = 0x3
   Addr = 0x83f762720 : Data = 0x83cb08000
   Addr = 0x83f762728 : Data = 0x83cb77fff
   Addr = 0x83f762730 : Data = 0x0
   Addr = 0x83f762738 : Data = 0xf
   Addr = 0x83f762708 : Data = 0x83f762188
   map_entry is at 0x83f762180
   Addr = 0x83f762180 : Data = 0x70616d6d
   Addr = 0x83f76219c : Data = 0x4
   Addr = 0x83f7621a0 : Data = 0x83cb78000
   Addr = 0x83f7621a8 : Data = 0x83cbcbfff
   Addr = 0x83f7621b0 : Data = 0x0
   Addr = 0x83f7621b8 : Data = 0xf
   Addr = 0x83f762188 : Data = 0x83f761788
   map_entry is at 0x83f761780
   Addr = 0x83f761780 : Data = 0x70616d6d
   Addr = 0x83f76179c : Data = 0x3
   Addr = 0x83f7617a0 : Data = 0x83cbcc000
   Addr = 0x83f7617a8 : Data = 0x83cbdffff
   Addr = 0x83f7617b0 : Data = 0x0
   Addr = 0x83f7617b8 : Data = 0xf
   Addr = 0x83f761788 : Data = 0x83f763dc8
   map_entry is at 0x83f763dc0
   Addr = 0x83f763dc0 : Data = 0x70616d6d
   Addr = 0x83f763ddc : Data = 0x4
   Addr = 0x83f763de0 : Data = 0x83cbe0000
   Addr = 0x83f763de8 : Data = 0x83cbe7fff
   Addr = 0x83f763df0 : Data = 0x0
   Addr = 0x83f763df8 : Data = 0xf
   Addr = 0x83f763dc8 : Data = 0x83f760748
   map_entry is at 0x83f760740
   Addr = 0x83f760740 : Data = 0x70616d6d
   Addr = 0x83f76075c : Data = 0x3
   Addr = 0x83f760760 : Data = 0x83cbe8000
   Addr = 0x83f760768 : Data = 0x83cbfbfff
   Addr = 0x83f760770 : Data = 0x0
   Addr = 0x83f760778 : Data = 0xf
   Addr = 0x83f760748 : Data = 0x83f762008
   map_entry is at 0x83f762000
   Addr = 0x83f762000 : Data = 0x70616d6d
   Addr = 0x83f76201c : Data = 0x4
   Addr = 0x83f762020 : Data = 0x83cbfc000
   Addr = 0x83f762028 : Data = 0x83f74bfff
   Addr = 0x83f762030 : Data = 0x0
   Addr = 0x83f762038 : Data = 0xf
   Addr = 0x83f762008 : Data = 0x83f7604c8
   map_entry is at 0x83f7604c0
   Addr = 0x83f7604c0 : Data = 0x70616d6d
   Addr = 0x83f7604dc : Data = 0x6
   Addr = 0x83f7604e0 : Data = 0x83f74c000
   Addr = 0x83f7604e8 : Data = 0x83f74ffff
   Addr = 0x83f7604f0 : Data = 0x0
   Addr = 0x83f7604f8 : Data = 0xf
   Addr = 0x83f7604c8 : Data = 0x83f760408
   map_entry is at 0x83f760400
   Addr = 0x83f760400 : Data = 0x70616d6d
   Addr = 0x83f76041c : Data = 0x4
   Addr = 0x83f760420 : Data = 0x83f750000
   Addr = 0x83f760428 : Data = 0x83f757fff
   Addr = 0x83f760430 : Data = 0x0
   Addr = 0x83f760438 : Data = 0xf
   Addr = 0x83f760408 : Data = 0x83f7600c8
   map_entry is at 0x83f7600c0
   Addr = 0x83f7600c0 : Data = 0x70616d6d
   Addr = 0x83f7600dc : Data = 0x6
   Addr = 0x83f7600e0 : Data = 0x83f758000
   Addr = 0x83f7600e8 : Data = 0x83f75ffff
   Addr = 0x83f7600f0 : Data = 0x0
   Addr = 0x83f7600f8 : Data = 0xf
   Addr = 0x83f7600c8 : Data = 0x83f7603c8
   map_entry is at 0x83f7603c0
   Addr = 0x83f7603c0 : Data = 0x70616d6d
   Addr = 0x83f7603dc : Data = 0x4
   Addr = 0x83f7603e0 : Data = 0x83f760000
   Addr = 0x83f7603e8 : Data = 0x83f7affff
   Addr = 0x83f7603f0 : Data = 0x0
   Addr = 0x83f7603f8 : Data = 0xf
   Addr = 0x83f7603c8 : Data = 0x83f760288
   map_entry is at 0x83f760280
   Addr = 0x83f760280 : Data = 0x70616d6d
   Addr = 0x83f76029c : Data = 0x8
   Addr = 0x83f7602a0 : Data = 0x83f7b0000
   Addr = 0x83f7602a8 : Data = 0x83f7b3fff
   Addr = 0x83f7602b0 : Data = 0x0
   Addr = 0x83f7602b8 : Data = 0xf
   Addr = 0x83f760288 : Data = 0x83f760248
   map_entry is at 0x83f760240
   Addr = 0x83f760240 : Data = 0x70616d6d
   Addr = 0x83f76025c : Data = 0x4
   Addr = 0x83f760260 : Data = 0x83f7b4000
   Addr = 0x83f760268 : Data = 0x83fffffff
   Addr = 0x83f760270 : Data = 0x0
   Addr = 0x83f760278 : Data = 0xf
   Addr = 0x83f760248 : Data = 0x83f778768
   Memory Map = 0x83f778a18
   Addr = 0x83f778a18 : Data = 0x83f757c20
   Forward link = 0x83f757c20
   map_entry is at 0x83f757c18
   Addr = 0x83f757c18 : Data = 0x6d646367
   Addr = 0x83f757c50 : Data = 0x0
   Addr = 0x83f757c48 : Data = 0x0
   Addr = 0x83f757c20 : Data = 0x83f757da0
   map_entry is at 0x83f757d98
   Addr = 0x83f757d98 : Data = 0x6d646367
   Addr = 0x83f757dd0 : Data = 0x2
   Addr = 0x83f757dc8 : Data = 0x0
   Addr = 0x83f757da0 : Data = 0x83f757ca0
   map_entry is at 0x83f757c98
   Addr = 0x83f757c98 : Data = 0x6d646367
   Addr = 0x83f757cd0 : Data = 0x1
   Addr = 0x83f757cc8 : Data = 0x8000000000000000
   Addr = 0x83f757cb0 : Data = 0x808000000
   Addr = 0x83f757cb8 : Data = 0x8083f7fff
   Addr = 0x83f757cd0 : Data = 0x1
   Addr = 0x83f757cc8 : Data = 0x8000000000000000
   Addr = 0x83f757cb0 : Data = 0x808000000
   Addr = 0x83f757cb8 : Data = 0x8083f7fff
   Addr = 0x83f757ca0 : Data = 0x83f7579a0
   map_entry is at 0x83f757998
   Addr = 0x83f757998 : Data = 0x6d646367
   Addr = 0x83f7579d0 : Data = 0x2
   Addr = 0x83f7579c8 : Data = 0x0
   Addr = 0x83f7579a0 : Data = 0x83f757aa0
   map_entry is at 0x83f757a98
   Addr = 0x83f757a98 : Data = 0x6d646367
   Addr = 0x83f757ad0 : Data = 0x0
   Addr = 0x83f757ac8 : Data = 0x0
   Addr = 0x83f757aa0 : Data = 0x83f778a18
   [7 p: 0x800000000 v: 0x0 pg_ct: 8192 attrib: 0xf size: 0x8000000]
   [7 p: 0x8083f8000 v: 0x0 pg_ct: 13168 attrib: 0xf size: 0xcdc0000]
   [4 p: 0x8151b8000 v: 0x0 pg_ct: 258 attrib: 0xf size: 0x408000]
   [11 p: 0x8155c0000 v: 0x0 pg_ct: 513 attrib: 0xf size: 0x804000]
   [4 p: 0x815dc4000 v: 0x0 pg_ct: 1155 attrib: 0xf size: 0x120c000]
   [1 p: 0x816fd0000 v: 0x0 pg_ct: 7 attrib: 0xf size: 0x1c000]
   [4 p: 0x816fec000 v: 0x0 pg_ct: 24 attrib: 0xf size: 0x60000]
   [3 p: 0x81704c000 v: 0x0 pg_ct: 19 attrib: 0xf size: 0x4c000]
   [4 p: 0x817098000 v: 0x0 pg_ct: 5 attrib: 0xf size: 0x14000]
   [3 p: 0x8170ac000 v: 0x0 pg_ct: 4 attrib: 0xf size: 0x10000]
   [4 p: 0x8170bc000 v: 0x0 pg_ct: 4 attrib: 0xf size: 0x10000]
   [3 p: 0x8170cc000 v: 0x0 pg_ct: 5 attrib: 0xf size: 0x14000]
   [4 p: 0x8170e0000 v: 0x0 pg_ct: 5 attrib: 0xf size: 0x14000]
   [3 p: 0x8170f4000 v: 0x0 pg_ct: 4 attrib: 0xf size: 0x10000]
   [1 p: 0x817104000 v: 0x0 pg_ct: 4 attrib: 0xf size: 0x10000]
   [4 p: 0x817114000 v: 0x0 pg_ct: 8 attrib: 0xf size: 0x20000]
   [3 p: 0x817134000 v: 0x0 pg_ct: 4 attrib: 0xf size: 0x10000]
   [4 p: 0x817144000 v: 0x0 pg_ct: 4 attrib: 0xf size: 0x10000]
   [3 p: 0x817154000 v: 0x0 pg_ct: 5 attrib: 0xf size: 0x14000]
   [4 p: 0x817168000 v: 0x0 pg_ct: 26 attrib: 0xf size: 0x68000]
   [3 p: 0x8171d0000 v: 0x0 pg_ct: 9 attrib: 0xf size: 0x24000]
   [4 p: 0x8171f4000 v: 0x0 pg_ct: 9 attrib: 0xf size: 0x24000]
   [3 p: 0x817218000 v: 0x0 pg_ct: 13 attrib: 0xf size: 0x34000]
   [6 p: 0x81724c000 v: 0x0 pg_ct: 16 attrib: 0x800000000000000f size: 0x40000]
   [3 p: 0x81728c000 v: 0x0 pg_ct: 10 attrib: 0xf size: 0x28000]
   [4 p: 0x8172b4000 v: 0x0 pg_ct: 5 attrib: 0xf size: 0x14000]
   [3 p: 0x8172c8000 v: 0x0 pg_ct: 18 attrib: 0xf size: 0x48000]
   [4 p: 0x817310000 v: 0x0 pg_ct: 3 attrib: 0xf size: 0xc000]
   [6 p: 0x81731c000 v: 0x0 pg_ct: 1 attrib: 0x800000000000000f size: 0x4000]
   [3 p: 0x817320000 v: 0x0 pg_ct: 8 attrib: 0xf size: 0x20000]
   [11 p: 0x817340000 v: 0x0 pg_ct: 2 attrib: 0xf size: 0x8000]
   [4 p: 0x817348000 v: 0x0 pg_ct: 2 attrib: 0xf size: 0x8000]
   [11 p: 0x817350000 v: 0x0 pg_ct: 18 attrib: 0xf size: 0x48000]
   [8 p: 0x817398000 v: 0x0 pg_ct: 37169 attrib: 0xf size: 0x244c4000]
   [3 p: 0x83b85c000 v: 0x0 pg_ct: 201 attrib: 0xf size: 0x324000]
   [4 p: 0x83bb80000 v: 0x0 pg_ct: 6 attrib: 0xf size: 0x18000]
   [11 p: 0x83bb98000 v: 0x0 pg_ct: 20 attrib: 0xf size: 0x50000]
   [3 p: 0x83bbe8000 v: 0x0 pg_ct: 41 attrib: 0xf size: 0xa4000]
   [11 p: 0x83bc8c000 v: 0x0 pg_ct: 12 attrib: 0xf size: 0x30000]
   [3 p: 0x83bcbc000 v: 0x0 pg_ct: 5 attrib: 0xf size: 0x14000]
   [11 p: 0x83bcd0000 v: 0x0 pg_ct: 4 attrib: 0xf size: 0x10000]
   [4 p: 0x83bce0000 v: 0x0 pg_ct: 1 attrib: 0xf size: 0x4000]
   [3 p: 0x83bce4000 v: 0x0 pg_ct: 27 attrib: 0xf size: 0x6c000]
   [4 p: 0x83bd50000 v: 0x0 pg_ct: 3 attrib: 0xf size: 0xc000]
   [3 p: 0x83bd5c000 v: 0x0 pg_ct: 67 attrib: 0xf size: 0x10c000]
   [4 p: 0x83be68000 v: 0x0 pg_ct: 6 attrib: 0xf size: 0x18000]
   [3 p: 0x83be80000 v: 0x0 pg_ct: 25 attrib: 0xf size: 0x64000]
   [4 p: 0x83bee4000 v: 0x0 pg_ct: 1 attrib: 0xf size: 0x4000]
   [3 p: 0x83bee8000 v: 0x0 pg_ct: 24 attrib: 0xf size: 0x60000]
   [4 p: 0x83bf48000 v: 0x0 pg_ct: 1 attrib: 0xf size: 0x4000]
   [3 p: 0x83bf4c000 v: 0x0 pg_ct: 8 attrib: 0xf size: 0x20000]
   [4 p: 0x83bf6c000 v: 0x0 pg_ct: 4 attrib: 0xf size: 0x10000]
   [3 p: 0x83bf7c000 v: 0x0 pg_ct: 24 attrib: 0xf size: 0x60000]
   [4 p: 0x83bfdc000 v: 0x0 pg_ct: 2 attrib: 0xf size: 0x8000]
   [3 p: 0x83bfe4000 v: 0x0 pg_ct: 5 attrib: 0xf size: 0x14000]
   [4 p: 0x83bff8000 v: 0x0 pg_ct: 1 attrib: 0xf size: 0x4000]
   [3 p: 0x83bffc000 v: 0x0 pg_ct: 12 attrib: 0xf size: 0x30000]
   [4 p: 0x83c02c000 v: 0x0 pg_ct: 4 attrib: 0xf size: 0x10000]
   [3 p: 0x83c03c000 v: 0x0 pg_ct: 76 attrib: 0xf size: 0x130000]
   [4 p: 0x83c16c000 v: 0x0 pg_ct: 1 attrib: 0xf size: 0x4000]
   [3 p: 0x83c170000 v: 0x0 pg_ct: 14 attrib: 0xf size: 0x38000]
   [4 p: 0x83c1a8000 v: 0x0 pg_ct: 2 attrib: 0xf size: 0x8000]
   [3 p: 0x83c1b0000 v: 0x0 pg_ct: 112 attrib: 0xf size: 0x1c0000]
   [4 p: 0x83c370000 v: 0x0 pg_ct: 1 attrib: 0xf size: 0x4000]
   [3 p: 0x83c374000 v: 0x0 pg_ct: 14 attrib: 0xf size: 0x38000]
   [4 p: 0x83c3ac000 v: 0x0 pg_ct: 2 attrib: 0xf size: 0x8000]
   [3 p: 0x83c3b4000 v: 0x0 pg_ct: 43 attrib: 0xf size: 0xac000]
   [4 p: 0x83c460000 v: 0x0 pg_ct: 1 attrib: 0xf size: 0x4000]
   [3 p: 0x83c464000 v: 0x0 pg_ct: 20 attrib: 0xf size: 0x50000]
   [4 p: 0x83c4b4000 v: 0x0 pg_ct: 6 attrib: 0xf size: 0x18000]
   [3 p: 0x83c4cc000 v: 0x0 pg_ct: 23 attrib: 0xf size: 0x5c000]
   [4 p: 0x83c528000 v: 0x0 pg_ct: 1 attrib: 0xf size: 0x4000]
   [3 p: 0x83c52c000 v: 0x0 pg_ct: 14 attrib: 0xf size: 0x38000]
   [4 p: 0x83c564000 v: 0x0 pg_ct: 2 attrib: 0xf size: 0x8000]
   [3 p: 0x83c56c000 v: 0x0 pg_ct: 10 attrib: 0xf size: 0x28000]
   [4 p: 0x83c594000 v: 0x0 pg_ct: 2 attrib: 0xf size: 0x8000]
   [3 p: 0x83c59c000 v: 0x0 pg_ct: 32 attrib: 0xf size: 0x80000]
   [4 p: 0x83c61c000 v: 0x0 pg_ct: 1 attrib: 0xf size: 0x4000]
   [3 p: 0x83c620000 v: 0x0 pg_ct: 4 attrib: 0xf size: 0x10000]
   [4 p: 0x83c630000 v: 0x0 pg_ct: 4 attrib: 0xf size: 0x10000]
   [3 p: 0x83c640000 v: 0x0 pg_ct: 26 attrib: 0xf size: 0x68000]
   [4 p: 0x83c6a8000 v: 0x0 pg_ct: 2 attrib: 0xf size: 0x8000]
   [3 p: 0x83c6b0000 v: 0x0 pg_ct: 9 attrib: 0xf size: 0x24000]
   [4 p: 0x83c6d4000 v: 0x0 pg_ct: 1 attrib: 0xf size: 0x4000]
   [3 p: 0x83c6d8000 v: 0x0 pg_ct: 12 attrib: 0xf size: 0x30000]
   [4 p: 0x83c708000 v: 0x0 pg_ct: 4 attrib: 0xf size: 0x10000]
   [3 p: 0x83c718000 v: 0x0 pg_ct: 8 attrib: 0xf size: 0x20000]
   [4 p: 0x83c738000 v: 0x0 pg_ct: 129 attrib: 0xf size: 0x204000]
   [3 p: 0x83c93c000 v: 0x0 pg_ct: 27 attrib: 0xf size: 0x6c000]
   [4 p: 0x83c9a8000 v: 0x0 pg_ct: 3 attrib: 0xf size: 0xc000]
   [3 p: 0x83c9b4000 v: 0x0 pg_ct: 22 attrib: 0xf size: 0x58000]
   [4 p: 0x83ca0c000 v: 0x0 pg_ct: 1 attrib: 0xf size: 0x4000]
   [6 p: 0x83ca10000 v: 0x0 pg_ct: 1 attrib: 0x800000000000000f size: 0x4000]
   [4 p: 0x83ca14000 v: 0x0 pg_ct: 12 attrib: 0xf size: 0x30000]
   [3 p: 0x83ca44000 v: 0x0 pg_ct: 6 attrib: 0xf size: 0x18000]
   [4 p: 0x83ca5c000 v: 0x0 pg_ct: 2 attrib: 0xf size: 0x8000]
   [3 p: 0x83ca64000 v: 0x0 pg_ct: 15 attrib: 0xf size: 0x3c000]
   [4 p: 0x83caa0000 v: 0x0 pg_ct: 2 attrib: 0xf size: 0x8000]
   [3 p: 0x83caa8000 v: 0x0 pg_ct: 22 attrib: 0xf size: 0x58000]
   [4 p: 0x83cb00000 v: 0x0 pg_ct: 2 attrib: 0xf size: 0x8000]
   [3 p: 0x83cb08000 v: 0x0 pg_ct: 28 attrib: 0xf size: 0x70000]
   [4 p: 0x83cb78000 v: 0x0 pg_ct: 21 attrib: 0xf size: 0x54000]
   [3 p: 0x83cbcc000 v: 0x0 pg_ct: 5 attrib: 0xf size: 0x14000]
   [4 p: 0x83cbe0000 v: 0x0 pg_ct: 2 attrib: 0xf size: 0x8000]
   [3 p: 0x83cbe8000 v: 0x0 pg_ct: 5 attrib: 0xf size: 0x14000]
   [4 p: 0x83cbfc000 v: 0x0 pg_ct: 2772 attrib: 0xf size: 0x2b50000]
   [6 p: 0x83f74c000 v: 0x0 pg_ct: 1 attrib: 0x800000000000000f size: 0x4000]
   [4 p: 0x83f750000 v: 0x0 pg_ct: 2 attrib: 0xf size: 0x8000]
   [6 p: 0x83f758000 v: 0x0 pg_ct: 2 attrib: 0x800000000000000f size: 0x8000]
   [4 p: 0x83f760000 v: 0x0 pg_ct: 20 attrib: 0xf size: 0x50000]
   [8 p: 0x83f7b0000 v: 0x0 pg_ct: 1 attrib: 0xf size: 0x4000]
   [4 p: 0x83f7b4000 v: 0x0 pg_ct: 531 attrib: 0xf size: 0x84c000]
   [0 p: 0x808000000 v: 0x0 pg_ct: 254 attrib: 0x8000000000000000 size: 0x3f8000]
   [16:45:49] Collecting Coredumps...
   [16:45:49]  saving for va = 0x8151b8000 with size 0x408000
   ..................................................................................................................................................................................................................................................................
   4227072 bytes received in 18.546 sec, 227924 bytes per second
   [16:46:08]  saving for va = 0x8155c0000 with size 0x804000
   .................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
   8404992 bytes received in 37.345 sec, 225063 bytes per second
   [16:46:45]  saving for va = 0x815dc4000 with size 0x120c000
   ...................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
   18923520 bytes received in 84.189 sec, 224774 bytes per second
   [16:48:09]  saving for va = 0x816fd0000 with size 0x1c000
   .......
   114688 bytes received in 0.509 sec, 225320 bytes per second
   [16:48:10]  saving for va = 0x816fec000 with size 0x60000
   ........................
   393216 bytes received in 1.759 sec, 223545 bytes per second
   [16:48:12]  saving for va = 0x81704c000 with size 0x4c000
   ...................
   311296 bytes received in 1.387 sec, 224438 bytes per second
   [16:48:13]  saving for va = 0x817098000 with size 0x14000
   .....
   81920 bytes received in 0.363 sec, 225675 bytes per second
   [16:48:13]  saving for va = 0x8170ac000 with size 0x10000
   ....
   65536 bytes received in 0.293 sec, 223672 bytes per second
   [16:48:14]  saving for va = 0x8170bc000 with size 0x10000
   ....
   65536 bytes received in 0.289 sec, 226768 bytes per second
   [16:48:14]  saving for va = 0x8170cc000 with size 0x14000
   .....
   81920 bytes received in 0.360 sec, 227556 bytes per second
   [16:48:14]  saving for va = 0x8170e0000 with size 0x14000
   .....
   81920 bytes received in 0.363 sec, 225675 bytes per second
   [16:48:15]  saving for va = 0x8170f4000 with size 0x10000
   ....
   65536 bytes received in 0.291 sec, 225210 bytes per second
   [16:48:15]  saving for va = 0x817104000 with size 0x10000
   ....
   65536 bytes received in 0.289 sec, 226768 bytes per second
   [16:48:15]  saving for va = 0x817114000 with size 0x20000
   ........
   131072 bytes received in 0.579 sec, 226377 bytes per second
   [16:48:16]  saving for va = 0x817134000 with size 0x10000
   ....
   65536 bytes received in 0.294 sec, 222912 bytes per second
   [16:48:16]  saving for va = 0x817144000 with size 0x10000
   ....
   65536 bytes received in 0.299 sec, 219184 bytes per second
   [16:48:16]  saving for va = 0x817154000 with size 0x14000
   .....
   81920 bytes received in 0.364 sec, 225055 bytes per second
   [16:48:17]  saving for va = 0x817168000 with size 0x68000
   ..........................
   425984 bytes received in 1.898 sec, 224438 bytes per second
   [16:48:19]  saving for va = 0x8171d0000 with size 0x24000
   .........
   147456 bytes received in 0.652 sec, 226160 bytes per second
   [16:48:19]  saving for va = 0x8171f4000 with size 0x24000
   .........
   147456 bytes received in 0.657 sec, 224438 bytes per second
   [16:48:20]  saving for va = 0x817218000 with size 0x34000
   .............
   212992 bytes received in 0.946 sec, 225150 bytes per second
   [16:48:21]  saving for va = 0x81724c000 with size 0x40000
   ................
   262144 bytes received in 1.158 sec, 226377 bytes per second
   [16:48:22]  saving for va = 0x81728c000 with size 0x28000
   ..........
   163840 bytes received in 0.732 sec, 223825 bytes per second
   [16:48:23]  saving for va = 0x8172b4000 with size 0x14000
   .....
   81920 bytes received in 0.367 sec, 223215 bytes per second
   [16:48:23]  saving for va = 0x8172c8000 with size 0x48000
   ..................
   294912 bytes received in 1.313 sec, 224609 bytes per second
   [16:48:25]  saving for va = 0x817310000 with size 0xc000
   ...
   49152 bytes received in 0.217 sec, 226507 bytes per second
   [16:48:25]  saving for va = 0x81731c000 with size 0x4000
   .
   16384 bytes received in 0.073 sec, 224438 bytes per second
   [16:48:25]  saving for va = 0x817320000 with size 0x20000
   ........
   131072 bytes received in 0.583 sec, 224823 bytes per second
   [16:48:25]  saving for va = 0x817340000 with size 0x8000
   ..
   32768 bytes received in 0.146 sec, 224438 bytes per second
   [16:48:26]  saving for va = 0x817348000 with size 0x8000
   ..
   32768 bytes received in 0.148 sec, 221405 bytes per second
   [16:48:26]  saving for va = 0x817350000 with size 0x48000
   ..................
   294912 bytes received in 1.311 sec, 224952 bytes per second
   [16:48:27]  saving for va = 0x83b85c000 with size 0x324000
   .........................................................................................................................................................................................................
   3293184 bytes received in 14.652 sec, 224760 bytes per second
   [16:48:42]  saving for va = 0x83bb80000 with size 0x18000
   ......
   98304 bytes received in 0.438 sec, 224438 bytes per second
   [16:48:42]  saving for va = 0x83bb98000 with size 0x50000
   ....................
   327680 bytes received in 1.462 sec, 224131 bytes per second
   [16:48:44]  saving for va = 0x83bbe8000 with size 0xa4000
   .........................................
   671744 bytes received in 2.996 sec, 224214 bytes per second
   [16:48:47]  saving for va = 0x83bc8c000 with size 0x30000
   ............
   196608 bytes received in 0.880 sec, 223418 bytes per second
   [16:48:47]  saving for va = 0x83bcbc000 with size 0x14000
   .....
   81920 bytes received in 0.362 sec, 226298 bytes per second
   [16:48:48]  saving for va = 0x83bcd0000 with size 0x10000
   ....
   65536 bytes received in 0.291 sec, 225210 bytes per second
   [16:48:48]  saving for va = 0x83bce0000 with size 0x4000
   .
   16384 bytes received in 0.073 sec, 224438 bytes per second
   [16:48:48]  saving for va = 0x83bce4000 with size 0x6c000
   ...........................
   442368 bytes received in 1.974 sec, 224097 bytes per second
   [16:48:50]  saving for va = 0x83bd50000 with size 0xc000
   ...
   49152 bytes received in 0.216 sec, 227556 bytes per second
   [16:48:50]  saving for va = 0x83bd5c000 with size 0x10c000
   ...................................................................
   1097728 bytes received in 4.896 sec, 224209 bytes per second
   [16:48:55]  saving for va = 0x83be68000 with size 0x18000
   ......
   98304 bytes received in 0.435 sec, 225986 bytes per second
   [16:48:56]  saving for va = 0x83be80000 with size 0x64000
   .........................
   409600 bytes received in 1.816 sec, 225551 bytes per second
   [16:48:57]  saving for va = 0x83bee4000 with size 0x4000
   .
   16384 bytes received in 0.073 sec, 224438 bytes per second
   [16:48:58]  saving for va = 0x83bee8000 with size 0x60000
   ........................
   393216 bytes received in 1.753 sec, 224310 bytes per second
   [16:48:59]  saving for va = 0x83bf48000 with size 0x4000
   .
   16384 bytes received in 0.072 sec, 227556 bytes per second
   [16:48:59]  saving for va = 0x83bf4c000 with size 0x20000
   ........
   131072 bytes received in 0.572 sec, 229147 bytes per second
   [16:49:00]  saving for va = 0x83bf6c000 with size 0x10000
   ....
   65536 bytes received in 0.287 sec, 228348 bytes per second
   [16:49:00]  saving for va = 0x83bf7c000 with size 0x60000
   ........................
   393216 bytes received in 1.753 sec, 224310 bytes per second
   [16:49:02]  saving for va = 0x83bfdc000 with size 0x8000
   ..
   32768 bytes received in 0.147 sec, 222912 bytes per second
   [16:49:02]  saving for va = 0x83bfe4000 with size 0x14000
   .....
   81920 bytes received in 0.365 sec, 224438 bytes per second
   [16:49:03]  saving for va = 0x83bff8000 with size 0x4000
   .
   16384 bytes received in 0.073 sec, 224438 bytes per second
   [16:49:03]  saving for va = 0x83bffc000 with size 0x30000
   ............
   196608 bytes received in 0.869 sec, 226246 bytes per second
   [16:49:03]  saving for va = 0x83c02c000 with size 0x10000
   ....
   65536 bytes received in 0.293 sec, 223672 bytes per second
   [16:49:04]  saving for va = 0x83c03c000 with size 0x130000
   ............................................................................
   1245184 bytes received in 5.545 sec, 224560 bytes per second
   [16:49:09]  saving for va = 0x83c16c000 with size 0x4000
   .
   16384 bytes received in 0.072 sec, 227556 bytes per second
   [16:49:09]  saving for va = 0x83c170000 with size 0x38000
   ..............
   229376 bytes received in 1.022 sec, 224438 bytes per second
   [16:49:10]  saving for va = 0x83c1a8000 with size 0x8000
   ..
   32768 bytes received in 0.146 sec, 224438 bytes per second
   [16:49:11]  saving for va = 0x83c1b0000 with size 0x1c0000
   ................................................................................................................
   1835008 bytes received in 8.165 sec, 224741 bytes per second
   [16:49:19]  saving for va = 0x83c370000 with size 0x4000
   .
   16384 bytes received in 0.073 sec, 224438 bytes per second
   [16:49:19]  saving for va = 0x83c374000 with size 0x38000
   ..............
   229376 bytes received in 1.025 sec, 223781 bytes per second
   [16:49:20]  saving for va = 0x83c3ac000 with size 0x8000
   ..
   32768 bytes received in 0.146 sec, 224438 bytes per second
   [16:49:20]  saving for va = 0x83c3b4000 with size 0xac000
   ...........................................
   704512 bytes received in 3.126 sec, 225372 bytes per second
   [16:49:23]  saving for va = 0x83c460000 with size 0x4000
   .
   16384 bytes received in 0.072 sec, 227556 bytes per second
   [16:49:23]  saving for va = 0x83c464000 with size 0x50000
   ....................
   327680 bytes received in 1.458 sec, 224746 bytes per second
   [16:49:25]  saving for va = 0x83c4b4000 with size 0x18000
   ......
   98304 bytes received in 0.439 sec, 223927 bytes per second
   [16:49:25]  saving for va = 0x83c4cc000 with size 0x5c000
   .......................
   376832 bytes received in 1.676 sec, 224840 bytes per second
   [16:49:27]  saving for va = 0x83c528000 with size 0x4000
   .
   16384 bytes received in 0.072 sec, 227556 bytes per second
   [16:49:27]  saving for va = 0x83c52c000 with size 0x38000
   ..............
   229376 bytes received in 1.021 sec, 224658 bytes per second
   [16:49:28]  saving for va = 0x83c564000 with size 0x8000
   ..
   32768 bytes received in 0.145 sec, 225986 bytes per second
   [16:49:28]  saving for va = 0x83c56c000 with size 0x28000
   ..........
   163840 bytes received in 0.726 sec, 225675 bytes per second
   [16:49:29]  saving for va = 0x83c594000 with size 0x8000
   ..
   32768 bytes received in 0.144 sec, 227556 bytes per second
   [16:49:29]  saving for va = 0x83c59c000 with size 0x80000
   ................................
   524288 bytes received in 2.333 sec, 224727 bytes per second
   [16:49:31]  saving for va = 0x83c61c000 with size 0x4000
   .
   16384 bytes received in 0.073 sec, 224438 bytes per second
   [16:49:31]  saving for va = 0x83c620000 with size 0x10000
   ....
   65536 bytes received in 0.291 sec, 225210 bytes per second
   [16:49:32]  saving for va = 0x83c630000 with size 0x10000
   ....
   65536 bytes received in 0.292 sec, 224438 bytes per second
   [16:49:32]  saving for va = 0x83c640000 with size 0x68000
   ..........................
   425984 bytes received in 1.901 sec, 224084 bytes per second
   [16:49:34]  saving for va = 0x83c6a8000 with size 0x8000
   ..
   32768 bytes received in 0.146 sec, 224438 bytes per second
   [16:49:34]  saving for va = 0x83c6b0000 with size 0x24000
   .........
   147456 bytes received in 0.651 sec, 226507 bytes per second
   [16:49:35]  saving for va = 0x83c6d4000 with size 0x4000
   .
   16384 bytes received in 0.072 sec, 227556 bytes per second
   [16:49:35]  saving for va = 0x83c6d8000 with size 0x30000
   ............
   196608 bytes received in 0.876 sec, 224438 bytes per second
   [16:49:35]  saving for va = 0x83c708000 with size 0x10000
   ....
   65536 bytes received in 0.288 sec, 227556 bytes per second
   [16:49:36]  saving for va = 0x83c718000 with size 0x20000
   ........
   131072 bytes received in 0.580 sec, 225986 bytes per second
   [16:49:36]  saving for va = 0x83c738000 with size 0x204000
   .................................................................................................................................
   2113536 bytes received in 9.405 sec, 224725 bytes per second
   [16:49:46]  saving for va = 0x83c93c000 with size 0x6c000
   ...........................
   442368 bytes received in 1.964 sec, 225238 bytes per second
   [16:49:48]  saving for va = 0x83c9a8000 with size 0xc000
   ...
   49152 bytes received in 0.218 sec, 225468 bytes per second
   [16:49:48]  saving for va = 0x83c9b4000 with size 0x58000
   ......................
   360448 bytes received in 1.596 sec, 225845 bytes per second
   [16:49:50]  saving for va = 0x83ca0c000 with size 0x4000
   .
   16384 bytes received in 0.071 sec, 230761 bytes per second
   [16:49:50]  saving for va = 0x83ca10000 with size 0x4000
   .
   16384 bytes received in 0.072 sec, 227556 bytes per second
   [16:49:50]  saving for va = 0x83ca14000 with size 0x30000
   ............
   196608 bytes received in 0.871 sec, 225727 bytes per second
   [16:49:51]  saving for va = 0x83ca44000 with size 0x18000
   ......
   98304 bytes received in 0.439 sec, 223927 bytes per second
   [16:49:51]  saving for va = 0x83ca5c000 with size 0x8000
   ..
   32768 bytes received in 0.143 sec, 229147 bytes per second
   [16:49:51]  saving for va = 0x83ca64000 with size 0x3c000
   ...............
   245760 bytes received in 1.090 sec, 225468 bytes per second
   [16:49:52]  saving for va = 0x83caa0000 with size 0x8000
   ..
   32768 bytes received in 0.144 sec, 227556 bytes per second
   [16:49:52]  saving for va = 0x83caa8000 with size 0x58000
   ......................
   360448 bytes received in 1.606 sec, 224438 bytes per second
   [16:49:54]  saving for va = 0x83cb00000 with size 0x8000
   ..
   32768 bytes received in 0.143 sec, 229147 bytes per second
   [16:49:54]  saving for va = 0x83cb08000 with size 0x70000
   ............................
   458752 bytes received in 2.038 sec, 225099 bytes per second
   [16:49:56]  saving for va = 0x83cb78000 with size 0x54000
   .....................
   344064 bytes received in 1.523 sec, 225912 bytes per second
   [16:49:58]  saving for va = 0x83cbcc000 with size 0x14000
   .....
   81920 bytes received in 0.362 sec, 226298 bytes per second
   [16:49:58]  saving for va = 0x83cbe0000 with size 0x8000
   ..
   32768 bytes received in 0.147 sec, 222912 bytes per second
   [16:49:58]  saving for va = 0x83cbe8000 with size 0x14000
   .....
   81920 bytes received in 0.360 sec, 227556 bytes per second
   [16:49:59]  saving for va = 0x83cbfc000 with size 0x2b50000
   ....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
   45416448 bytes received in 201.604 sec, 225276 bytes per second
   [16:53:20]  saving for va = 0x83f74c000 with size 0x4000
   .
   16384 bytes received in 0.072 sec, 227556 bytes per second
   [16:53:20]  saving for va = 0x83f750000 with size 0x8000
   ..
   32768 bytes received in 0.145 sec, 225986 bytes per second
   [16:53:20]  saving for va = 0x83f758000 with size 0x8000
   ..
   32768 bytes received in 0.144 sec, 227556 bytes per second
   [16:53:21]  saving for va = 0x83f760000 with size 0x50000
   ....................
   327680 bytes received in 1.458 sec, 224746 bytes per second
   [16:53:22]  saving for va = 0x83f7b4000 with size 0x84c000
   ...................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
   8699904 bytes received in 38.747 sec, 224531 bytes per second
   [16:54:01]  saving for va = 0x808000000 with size 0x3f8000
   ..............................................................................................................................................................................................................................................................
   4161536 bytes received in 18.524 sec, 224656 bytes per second
   Compressing /Users/sda/tmp/efi_coredumps/iefi.core
   [16:54:22] Saved coredump to  /Users/sda/tmp/efi_coredumps/iefi.core.gz
    ChimpSWD-30B0D9 - CPU0:Halt CPU1:PowerOff SIO:Reset SEP:PowerOff PMP:PowerO
   ff AOP:Reset SMC:Run ISP:PowerOff ANS2:Halt PUP:Reset
   CPU0 >
```

# END

