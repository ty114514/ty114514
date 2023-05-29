# WIP

## 全 CPU 架构补全计划:
+ 路由器 AC2100 mipsle
+ 树莓派 3B arm64
+ wsl
+ IBM LinuxOne 

|Arch|Name|Detials|
|---|---|---|
|AMD64|红米 Pro14 2022 WSL|AMD Ryzen 6800H 16G+512G|
||
|ARMv8|树莓派 3B|BCM2837B0(a53\*4) 1G+64G|
||红米 Note12Turbo Termux|SnapDragon 7+ Gen2 16G+1024G|
|s390x|IBM LinuxOne|Unknown s390x CPU(1Core\*2Slot z/VM) 4G+50G|
|riscv64|VisionFive 2|JH7110(U74\*4) 4G+64G|

### 各个平台对 CPU 架构的命名:
|Target|AMD64|ARMv8|ARMv7|
|---|---|---|---|
|Linux|amd64 x86_64|aarch64||
|Windows|x64|
|C|
|Go|
|Rust|
|Zig|
|Docker|linux/amd64|linux/arm64/v8|linux/arm/v7|

### 编译自查:
Linux:
|-|AMD64 glibc|AMD64 musl|ARMv8 glibc|
|---|---|---|---|
|C (Ubuntu)|
|Go|GOARCH=amd64|GOARCH=amd64|GOARCH=arm64|
|Rust|||aarch64-unknown-linux-gnu|
|Zig||
### arm64: 
```bash
Linux ubuntu 5.4.0-1073-raspi #84-Ubuntu SMP PREEMPT Sat Oct 15 11:13:36 UTC 2022 aarch64 aarch64 aarch64 GNU/Linux
```

<details> 
    <summary>lscpu</summary>
    <pre><code>
Architecture:                    aarch64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
CPU(s):                          4
On-line CPU(s) list:             0-3
Thread(s) per core:              1
Core(s) per socket:              4
Socket(s):                       1
Vendor ID:                       ARM
Model:                           4
Model name:                      Cortex-A53
Stepping:                        r0p4
CPU max MHz:                     1200.0000
CPU min MHz:                     600.0000
BogoMIPS:                        38.40
L1d cache:                       128 KiB
L1i cache:                       128 KiB
L2 cache:                        512 KiB
Vulnerability Itlb multihit:     Not affected
Vulnerability L1tf:              Not affected
Vulnerability Mds:               Not affected
Vulnerability Meltdown:          Not affected
Vulnerability Mmio stale data:   Not affected
Vulnerability Spec store bypass: Not affected
Vulnerability Spectre v1:        Mitigation; __user pointer sanitization
Vulnerability Spectre v2:        Not affected
Vulnerability Srbds:             Not affected
Vulnerability Tsx async abort:   Not affected
Flags:                           fp asimd evtstrm crc32 cpuid</code></pre> 
</details>

### mipsle:
```bash
Linux ImmortalWrt 5.10.109 #0 SMP Thu Apr 13 06:21:20 2023 mips GNU/Linux
```

<details> 
    <summary>cat /proc/cpuinfo</summary>
    <pre><code>
system type             : MediaTek MT7621 ver:1 eco:3
machine                 : Xiaomi Redmi Router AC2100
processor               : 0
cpu model               : MIPS 1004Kc V2.15
BogoMIPS                : 586.13
wait instruction        : yes
microsecond timers      : yes
tlb_entries             : 32
extra interrupt vector  : yes
hardware watchpoint     : yes, count: 4, address/irw mask: [0x0ffc, 0x0ffc, 0x0ffb, 0x0ffb]
isa                     : mips1 mips2 mips32r1 mips32r2
ASEs implemented        : mips16 dsp mt
Options implemented     : tlb 4kex 4k_cache prefetch mcheck ejtag llsc pindexed_dcache userlocal vint perf_cntr_intr_bit cdmm nan_legacy nan_2008 perf
shadow register sets    : 1
kscratch registers      : 0
package                 : 0
core                    : 0
VPE                     : 0
VCED exceptions         : not available
VCEI exceptions         : not available

processor               : 1
cpu model               : MIPS 1004Kc V2.15
BogoMIPS                : 586.13
wait instruction        : yes
microsecond timers      : yes
tlb_entries             : 32
extra interrupt vector  : yes
hardware watchpoint     : yes, count: 4, address/irw mask: [0x0ffc, 0x0ffc, 0x0ffb, 0x0ffb]
isa                     : mips1 mips2 mips32r1 mips32r2
ASEs implemented        : mips16 dsp mt
Options implemented     : tlb 4kex 4k_cache prefetch mcheck ejtag llsc pindexed_dcache userlocal vint perf_cntr_intr_bit cdmm nan_legacy nan_2008 perf
shadow register sets    : 1
kscratch registers      : 0
package                 : 0
core                    : 0
VPE                     : 1
VCED exceptions         : not available
VCEI exceptions         : not available

processor               : 2
cpu model               : MIPS 1004Kc V2.15
BogoMIPS                : 586.13
wait instruction        : yes
microsecond timers      : yes
tlb_entries             : 32
extra interrupt vector  : yes
hardware watchpoint     : yes, count: 4, address/irw mask: [0x0ffc, 0x0ffc, 0x0ffb, 0x0ffb]
isa                     : mips1 mips2 mips32r1 mips32r2
ASEs implemented        : mips16 dsp mt
Options implemented     : tlb 4kex 4k_cache prefetch mcheck ejtag llsc pindexed_dcache userlocal vint perf_cntr_intr_bit cdmm nan_legacy nan_2008 perf
shadow register sets    : 1
kscratch registers      : 0
package                 : 0
core                    : 1
VPE                     : 0
VCED exceptions         : not available
VCEI exceptions         : not available

processor               : 3
cpu model               : MIPS 1004Kc V2.15
BogoMIPS                : 586.13
wait instruction        : yes
microsecond timers      : yes
tlb_entries             : 32
extra interrupt vector  : yes
hardware watchpoint     : yes, count: 4, address/irw mask: [0x0ffc, 0x0ffc, 0x0ffb, 0x0ffb]
isa                     : mips1 mips2 mips32r1 mips32r2
ASEs implemented        : mips16 dsp mt
Options implemented     : tlb 4kex 4k_cache prefetch mcheck ejtag llsc pindexed_dcache userlocal vint perf_cntr_intr_bit cdmm nan_legacy nan_2008 perf
shadow register sets    : 1
kscratch registers      : 0
package                 : 0
core                    : 1
VPE                     : 1
VCED exceptions         : not available
VCEI exceptions         : not available</code></pre> 
</details>

<details> 
    <summary>lscpu</summary>
    <pre><code>
Architecture:          mips
  Byte Order:          Little Endian
CPU(s):                4
  On-line CPU(s) list: 0-3
Model name:            -
  Model:               MIPS 1004Kc V2.15
  Thread(s) per core:  2
  Core(s) per socket:  2
  Socket(s):           1
  BogoMIPS:            586.13
  Flags:               mips16 dsp mt
Caches (sum of all):
  L1d:                 64 KiB (2 instances)
  L1i:                 64 KiB (2 instances)
  L2:                  256 KiB (1 instance)</code></pre> 
</details>

### amd64:
WIP

### riscv64:
WIP

### s390x:
```bash
Linux main 5.15.0-58-generic #64-Ubuntu SMP Thu Jan 5 12:29:14 UTC 2023 s390x s390x s390x GNU/Linux
```

<details> 
    <summary>lscpu</summary>
    <pre><code>
Architecture:            s390x
  CPU op-mode(s):        32-bit, 64-bit
  Byte Order:            Big Endian
CPU(s):                  2
  On-line CPU(s) list:   0,1
Vendor ID:               IBM/S390
  Machine type:          8561
  Thread(s) per core:    1
  Core(s) per socket:    1
  Socket(s) per book:    1
  Book(s) per drawer:    1
  Drawer(s):             2
  CPU dynamic MHz:       5200
  CPU static MHz:        5200
  BogoMIPS:              3241.00
  Dispatching mode:      horizontal
  Flags:                 esan3 zarch stfle msa ldisp eimm dfp edat etf3eh highgprs te vx vxd vxe gs vxe2 vxp sort dflt s
                         ie
Virtualization features:
  Hypervisor:            z/VM 7.2.0
  Hypervisor vendor:     IBM
  Virtualization type:   full
Caches (sum of all):
  L1d:                   256 KiB (2 instances)
  L1i:                   256 KiB (2 instances)
  L2d:                   8 MiB (2 instances)
  L2i:                   8 MiB (2 instances)
  L3:                    256 MiB
  L4:                    960 MiB
NUMA:
  NUMA node(s):          1
  NUMA node0 CPU(s):     0,1
Vulnerabilities:
  Itlb multihit:         Not affected
  L1tf:                  Not affected
  Mds:                   Not affected
  Meltdown:              Not affected
  Mmio stale data:       Not affected
  Retbleed:              Not affected
  Spec store bypass:     Not affected
  Spectre v1:            Mitigation; __user pointer sanitization
  Spectre v2:            Mitigation; etokens
  Srbds:                 Not affected
  Tsx async abort:       Not affected
</code></pre> 
</details>

<details> 
    <summary>cat /proc/cpuinfo</summary>
    <pre><code>
vendor_id       : IBM/S390
# processors    : 2
bogomips per cpu: 3241.00
max thread id   : 0
features        : esan3 zarch stfle msa ldisp eimm dfp edat etf3eh highgprs te vx vxd vxe gs vxe2 vxp sort dflt sie
facilities      : 0 1 2 3 4 6 7 8 9 10 12 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 30 31 32 33 34 35 36 37 38 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 57 58 59 60 61 73 74 75 76 77 80 81 82 128 129 130 131 133 134 135 146 147 148 150 151 152 155 156 168
cache0          : level=1 type=Data scope=Private size=128K line_size=256 associativity=8
cache1          : level=1 type=Instruction scope=Private size=128K line_size=256 associativity=8
cache2          : level=2 type=Data scope=Private size=4096K line_size=256 associativity=8
cache3          : level=2 type=Instruction scope=Private size=4096K line_size=256 associativity=8
cache4          : level=3 type=Unified scope=Shared size=262144K line_size=256 associativity=32
cache5          : level=4 type=Unified scope=Shared size=983040K line_size=256 associativity=60
processor 0: version = FF,  identification = 0A18E8,  machine = 8561
processor 1: version = FF,  identification = 0A18E8,  machine = 8561

cpu number      : 0
physical id     : 0
core id         : 0
book id         : 0
drawer id       : 0
dedicated       : 0
address         : 0
siblings        : 1
cpu cores       : 1
version         : FF
identification  : 0A18E8
machine         : 8561
cpu MHz dynamic : 5200
cpu MHz static  : 5200

cpu number      : 1
physical id     : 1
core id         : 1
book id         : 1
drawer id       : 1
dedicated       : 0
address         : 1
siblings        : 1
cpu cores       : 1
version         : FF
identification  : 0A18E8
machine         : 8561
cpu MHz dynamic : 5200
cpu MHz static  : 5200
    </code></pre> 
</details>

### ppc64:
WIP

<details> 
    <summary>lscpu</summary>
    <pre><code>
    </code></pre> 
</details>


<details> 
    <summary>lscpu</summary>
    <pre><code>
    </code></pre> 
</details>

<details> 
    <summary>lscpu</summary>
    <pre><code>
    </code></pre> 
</details>

