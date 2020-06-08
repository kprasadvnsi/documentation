# View and control CPU frequency

Rockchip RK3399 is a 6-core ARM® 64-bit processor with a main frequency of up to
2.0GHz. It is based on a big.LITTLE core architecture: dual-core cortex-a72 +
quad-core cortex-a53

## 1. CPU command


### 1. Check the frequency that CPU0~3 support

```bash
root@OrangePi:~# cat
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
408000 600000 816000 1008000 1200000 1416000
```

### 2. Check the frequency that cpu4~5 support

```bash
root@OrangePi:~# cat
/sys/devices/system/cpu/cpu4/cpufreq/scaling_available_frequencies
408000 600000 816000 1008000 1200000 1416000 1608000 1800000
```

### 3. Set the maximum frequency of CPU0~5

```bash
echo 816000 > /sys/devices/system/cpu/cpu0(0~5)
/cpufreq/scaling_max_freq
```

### 4. Check the current frequency of CPU0 ~ 5

```bash
root@OrangePi:~# cat
/sys/devices/system/cpu/cpu[012345]/cpufreq/cpuinfo_cur_freq
408000
408000
408000
408000
408000
408000
```

### 5. Check the current temperature of CPU

```bash
root@OrangePi:~# cat /sys/class/thermal/thermal_zone[01]/temp
48750
48750
```

### 6. CPU ID

```bash
root@OrangePi:~# hexdump /sys/bus/nvmem/devices/rockchip-efuse0/nvmem
0000000 4b52 9933 fe91 5421 4356 3432 2e38 3030
0000010 0000 0000 060b 230c 1e18 1915 0008 0000
0000020 0000 0010 0000 0000 0000 0000 0000 0000
0000030 0000 0000 0000 0000 0000 0000 0000 0000
*
0000080
```

### 7. You're looking at CPU statistics

```bash
root@OrangePi:~# lscpu
Architecture: aarch64
Byte Order: Little Endian
CPU(s): 6
On-line CPU(s) list: 0-5
Thread(s) per core: 1
Core(s) per socket: 3
Socket(s): 2
Vendor ID: ARM
Model: 4
Model name: Cortex-A53
Stepping: r0p4
CPU max MHz: 1800.0000
CPU min MHz: 408.000
BogoMIPS: 48.00
```