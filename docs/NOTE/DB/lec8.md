# Storage and File Structure

主要面临的问题有

- **Data Storage(数据存储)** ：如何高效地存储和管理数据。
- **API 应用程序接口 (SQL)** ：提供标准化的接口，支持查询、插入、删除和更新操作。
- **High Performance(高性能)** ：通过索引、缓冲管理、查询处理和优化来提升数据库性能。
- **Concurrent Control(并发控制)** ：确保多个用户同时访问数据库时的一致性和正确性。
- **Reliability(可靠性)** ：在系统故障时，保证数据的完整性和可恢复性。
- **Security(安全性)** ：通过授权和加密机制保护数据免受未授权访问。

## Overview of Physical Storage Media

### Physical Level of Databases

- **Files and Storage** : 数据库在物理层面上存储为文件，例如 `.mdf`, `.ldf`, `.ora`, `.dbf` 等。

- **Storage Media Classification** :
    - **Speed**: 数据访问速度。
    - **Cost**: 每单位数据的存储成本。
    - **Reliability**:数据在断电或系统崩溃时可能丢失。存储设备的物理故障（如 RAID 提供的容错机制）。

Storages classified by reliability:

- Volatile storage: loses contents when power is switched off, e.g., DDR2, SDR. 
- Non-volatile storage(非易失性存储器): contents persist even when power is switched off. Includes secondary and tertiary storage, as well as batter-backed up main-memory. 

Storages classified by speed: 
- Cache 
- Main-memory 
- Flash memory
- Magnetic-disk 
- Optical storage 
- Tape storage


### Hierarchy

<figure markdown="span">
![](./img/lec8-1.png){ width="400" }
<figcaption>Storage Hierarchy</figcaption>
</figure>

- Primary storage: Fastest media but volatile (cache, main memory). 

- Secondary storage (辅助存储器，联机存储器): next level in hierarchy, non-volatile, moderately fast access time ;Also called on-line storage E.g., flash memory, magnetic disks 

- Tertiary storage (三级存储器，脱机存储器): lowest level in hierarchy, non-volatile, slow access time ;also called off-line storage,E.g., magnetic tape, optical storage

### Physical Storage Media (Cont.)

#### Cache
- **Fastest and most costly form of storage**, volatile, and managed by the computer system hardware.
- **Speed**: ≤ 0.5 nanoseconds (ns, 1 ns = 10⁻⁹ seconds).
- **Size**: ~ KB to ~ MB.

#### Main Memory
- **Fast access** : 10 to 100 ns.
- **Capacity** : Generally too small (or too expensive) to store the entire database.
    - Widely used capacities: up to a few Gigabytes (1 GB = $10^9$ B).
    - Capacities have increased, and per-byte costs have decreased steadily (roughly a factor of 2 every 2–3 years).
- **Volatile** : Contents are lost during power failure or system crash.

#### Flash Memory (快闪存储器)

- Also known as **EEPROM** (Electrically Erasable Programmable Read-Only Memory, 电可擦可编程只读存储器).
- **Non-volatile** : Data survives power failures.
- **Write/Erase Limitations** :
    - Data can be written at a location only once, but the location can be erased and rewritten.
    - Supports a limited number of write/erase cycles (10K–1M).
    - Erasing must be done to an entire bank of memory.
- **Performance** :
    - Reads: Roughly as fast as main memory (< 100 ns).
    - Writes: Slower (~10 μs), and erases are even slower.
- **Cost** : Similar to main memory.
- **Usage** : Widely used in embedded devices such as digital cameras, phones, and USB keys.

#### Magnetic Disk
- **Storage** : Data is stored on spinning disks and read/written magnetically.
- **Primary medium** : Used for long-term storage, typically storing the entire database.
- **Access** :
    - Data must be moved to main memory for access and written back for storage.
    - Much slower access than main memory.
    - Direct-access: Data can be read in any order (unlike magnetic tape).
- **Capacity** :
    - Ranges up to ~1.5 TB (as of 2009).
    - Larger capacity and lower cost/byte than main memory or flash memory.
    - Growing rapidly with technology improvements (factor of 2–3 every 2 years).
- **Reliability** :
    - Survives power failures and system crashes.
    - Disk failure is rare but can destroy data.

#### Optical Storage
- **Non-volatile** : Data is read optically from a spinning disk using a laser.
- **Popular Forms** :
    - CD-ROM (640 MB).
    - DVD (4.7–17 GB).
- **Write Types** :
    - Write-once, read-many (WORM) disks (e.g., CD-R, DVD-R) for archival storage.
    - Multiple-write versions available (e.g., CD-RW, DVD-RW, DVD-RAM).
- **Performance** :
    - Reads and writes are slower than magnetic disks.
- **Juke-box Systems(自动光盘机)** :
    - Large numbers of removable disks with a few drives.
    - Mechanism for automatic loading/unloading of disks for storing large volumes of data.

#### Tape Storage

- **非易失性** ：主要用于备份（从磁盘故障中恢复）和归档数据。
- **顺序访问** ：访问速度远慢于磁盘。
- **容量** ：容量非常高（40 到 300 GB 的磁带可用）。
- **可移除** ：磁带可以从驱动器中移除，因此存储成本远低于磁盘，但驱动器价格昂贵。
- **磁带自动机 (Tape Jukebox)** ：
    - 可用于存储海量数据。
    - 容量范围从数百 TB（1 TB = $10^{12}$ 字节）到甚至 PB（1 PB = $10^{15}$ 字节）。


## Magnetic Disks

<figure markdown="span">
![](./img/lec8-2.png){ width="400" }
<figcaption>
Structure
</figcaption>
</figure>

### Disk Structure 

磁头 (Read-Write Head)

- **位置**：磁头非常接近盘片表面（几乎接触）。
- **功能**：用于读取或写入磁性编码的信息。

盘片表面 (Surface of Platter)

- **圆形磁道 (Tracks)**：
    - 盘片表面被划分为多个圆形磁道。
    - 典型硬盘每个盘片上有超过 50K–100K 条磁道。

- **扇区 (Sectors)**：
    - 每个磁道被划分为多个扇区。
    - 扇区是可以读取或写入的最小数据单位。

- **扇区大小**：通常为 512 字节。

- **每磁道的扇区数**：
    - 内圈磁道：500 到 1000 个扇区。
    - 外圈磁道：1000 到 2000 个扇区。

读/写扇区 (To Read/Write a Sector)

- **磁臂 (Disk Arm)**：
   - 磁臂移动以将磁头定位到正确的磁道上。
- **盘片旋转 (Platter Spins)**：
   - 盘片持续旋转，当扇区经过磁头下方时，数据被读取或写入。

磁头-磁盘组件 (Head-Disk Assemblies)

- **多盘片 (Multiple Disk Platters)**：
   - 单个主轴上通常有 4 到 16 个盘片。
- **磁头 (Heads)**：
   - 每个盘片对应一个磁头，所有磁头安装在一个公共磁臂上。
- **柱面 (Cylinder)**：
   - 第 i 个柱面由所有盘片的第 i 个磁道组成。

磁盘控制器 (Disk Controller)

- **功能**：
    - 作为计算机系统与磁盘驱动硬件之间的接口。
    - 接收高层次的读/写扇区命令。
    - 执行动作，例如移动磁臂到正确的磁道并实际读取或写入数据。
- **校验和 (Checksum)**：
    - 计算并附加校验和到每个扇区，以验证数据是否正确读取。
    - 如果数据损坏，存储的校验和与重新计算的校验和很可能不匹配。
- **写入验证 (Write Verification)**：
    - 写入后通过读取扇区来确保写入成功。
- **坏扇区重映射 (Bad Sector Remapping)**：
    - 将坏扇区从逻辑地址映射到预留的物理扇区。
    - 重映射信息记录在磁盘或其他非易失性存储器中。

磁盘的性能主要由以下几个方面决定：

- 转速（RPM）：盘片的旋转速度，转速越高，数据访问速度越快。
- 磁头寻道时间（Seek Time）：磁头移动到目标轨道所需的时间，寻道时间越短，数据访问速度越快。
- 数据传输率（Data Transfer Rate）：硬盘与计算机之间的数据传输速度，传输率越高，数据访问速度越快。
- 缓存（Cache）：硬盘内部的高速缓存，用于临时存储数据，提高数据传输效率。

!!!quote
    [计组关于磁盘性能的描述](../CO/wk6.md)


### Optimization of Disk-Block Access

#### Block

- **定义**：来自单个磁道的连续扇区序列。
- **数据传输**：数据在磁盘和主存之间以块为单位传输。
- **块大小**：
    - 范围从 512 字节到几千字节。
    - **小块**：需要更多的磁盘传输。
    - **大块**：可能浪费更多空间（由于部分填充的块）。
    - **典型块大小**：目前范围为 4 到 16 KB。

#### Disk-Arm-Scheduling Algorithms

<figure markdown="span">
![](./img/lec8-3.png){ width="400" }
</figure>

- **目标**：对磁盘访问请求进行排序，以最小化磁盘臂的移动。
- **电梯算法 (Elevator Algorithm)**：
    - 磁盘臂向一个方向移动（从外圈到内圈或反之），处理该方向上的下一个请求。
    - 当该方向没有更多请求时，反转方向并重复。

#### File Organization

- **优化块访问时间**：通过组织块的位置，使其与数据访问方式相对应。
    - 例如，将相关信息存储在同一个柱面或附近的柱面上。
- **文件碎片化**：
    - 随着文件中数据的插入或删除，文件可能会变得碎片化。
    - 如果磁盘上的空闲块分散，新创建的文件可能会被分散存储。
    - 对碎片化文件的顺序访问会导致磁盘臂移动增加。
- **碎片整理工具**：
    - 一些系统提供碎片整理工具以加速文件访问。
    - 但在运行这些工具时，系统通常无法使用。

#### 非易失性写缓冲区 (Nonvolatile Write Buffers)

- **作用**：通过将块立即写入非易失性 RAM 缓冲区来加速磁盘写入。

- **非易失性 RAM**：
    - 由电池供电的 RAM 或闪存组成。
    - 即使断电，数据仍然安全，并将在电力恢复后写入磁盘。
- **控制器行为**：
    - 当磁盘没有其他请求或请求等待了一段时间时，控制器将数据写入磁盘。
    - 数据库操作可以在数据写入磁盘之前继续运行。
    - 写入可以重新排序以最小化磁盘臂移动。

#### 日志磁盘 (Log Disk)
- **定义**：专门用于写入块更新日志的磁盘。
- **特点**：
    - 写入日志磁盘非常快，因为不需要寻道。
    - 不需要特殊硬件（如非易失性 RAM）。
- **文件系统行为**：
    - 日志文件系统以安全顺序将数据写入非易失性 RAM 或日志磁盘。
    - 如果没有日志记录，重新排序写入可能会导致文件系统数据损坏。

## RAID

> Redundant Array of Inexpensive Disks
> RAID 最初是作为一种成本较低的替代方案，用于替代大型昂贵的磁盘。  
> RAID 中的 "I" 最初代表 "inexpensive"（廉价）。  
> 如今，RAID 被视为 "independent"（独立的）。

!!!info 
    Disk organization techniques that manage a large numbers of disks, providing a view of a single disk of 
    
    •High capacity and high speed  by using multiple disks in parallel, and 
    
    •High reliability by storing data redundantly, so that data can be recovered even if  a disk fails 

**The chance that some disk out of a set of N disks will fail is much higher than the chance that a specific single disk will fail**

!!!eg
    a system with 100 disks, each with MTTF of 100,000 hours (approx.  11 years), will have a system MTTF of 1000 hours (approx. 41 days) 
    
    Techniques for using redundancy to avoid data loss are critical with large numbers of disks 

### Reliability improvement

- **冗余原理** ：存储额外的信息，用于在磁盘故障时重建丢失的数据

- **镜像(Mirroring)技术** ：
    - 每个磁盘都有一个完整的副本
    - 一个逻辑磁盘实际由两个物理磁盘组成
    - 每次写操作都在两个磁盘上执行
    - 读操作可以从任一磁盘进行
  
- **故障恢复** ：
    - 单个磁盘故障时，数据仍可从镜像磁盘获取
    - 只有当磁盘及其镜像磁盘在系统修复前都发生故障时才会丢失数据
    - 这种双重故障的概率非常小
    - 需注意依赖性故障模式(如火灾、建筑物倒塌或电涌)

- **平均数据丢失时间** ：
    - 取决于平均故障时间(MTTF)和平均修复时间
    - 示例：
    - MTTF = 100,000小时
    - 平均修复时间 = 10小时
    - 镜像磁盘对的平均数据丢失时间 = 500 $\times$ $10^6$小时(约57,000年)
    - (计算公式：$100000^2$/(2 $\times$ 10))

### Performance improvement

- **并行化的主要目标** ：
  1. 负载均衡：通过处理多个小访问提高吞吐量
  2. 并行化大型访问以减少响应时间

- **数据条带化(Striping)技术** ：

1 **比特级条带化** ：

- 将每个字节的位分散到多个磁盘
- 示例：在8个磁盘阵列中，每个字节的第i位写入第i个磁盘
- 可实现8倍于单磁盘的数据读取速率
- 缺点：寻道/访问时间比单磁盘更差
- 现在较少使用
 
2 **块级条带化** ：

- 在n个磁盘中，文件的第i个块存储在第((i mod n) + 1)个磁盘上
- 不同块的请求可以在不同磁盘上并行运行
- 长序列块的请求可以并行使用所有磁盘

### RAID levels

<figure markdown="span">
![](./img/lec8-4.png){ width="400" }
<figcaption>
RAID 0 and RAID 1
</figcaption>
</figure>

#### RAID Level 0

- **块级条带化** ：不具备冗余性。
- **应用场景** ：用于高性能应用，数据丢失不关键。
- **工作原理** ：使用块级条带化，将数据分散到多个磁盘上。没有冗余，因此数据丢失风险较高。
- **优点** ：提供高数据传输速率，适用于对性能要求高但数据安全性要求不高的应用。

#### RAID Level 1

- **镜像磁盘与块级条带化** ：提供最佳性能。
- **应用场景** ：常用于数据库系统中的日志文件存储。
- **工作原理** ：使用镜像技术，每个磁盘都有一个完整的副本。所有写操作都在两个磁盘上执行，读操作可以从任一磁盘进行。
- **优点** ：提供高数据安全性和读取性能，适用于需要高可靠性的数据存储。

#### RAID Level 2

<figure markdown="span">
![](./img/lec8-5.png){ width="400" }
<figcaption>
RAID 2
</figcaption>
</figure>

- **Memory-Style Error-Correcting-Codes (ECC)与比特级条带化** 。

- **工作原理** ：使用内存风格的错误校正码(ECC)和比特级条带化。数据被分成位并分布在多个磁盘上，ECC用于错误检测和校正。
- **优点** ：提供错误校正能力，但实现复杂且成本较高。

#### RAID Level 3

<figure markdown="span">
![](./img/lec8-6.png){ width="400" }
<figcaption>
RAID 3
</figcaption>
</figure>

- **比特交错奇偶校验** ：
    - 单个奇偶位足以进行错误校正。
    - 写入数据时，需计算并写入相应的奇偶位。
    - 数据恢复通过计算其他磁盘（包括奇偶位磁盘）的位的异或。
    - 数据传输速度快于单个磁盘，但每个I/O需要所有磁盘参与。
- **工作原理** ：使用比特交错奇偶校验。一个奇偶位磁盘用于错误校正。写入数据时，需计算并写入相应的奇偶位。
- **优点** ：提供快速的数据传输速率，适用于需要高吞吐量的应用。

#### RAID Level 4

<figure markdown="span">
![](./img/lec8-7.png){ width="400" }
<figcaption>
RAID 4
</figcaption>
</figure>

- **块交错奇偶校验** ：
    - 使用块级条带化，并在单独的磁盘上保存奇偶校验块。
    - 写入数据块时，需计算并写入相应的奇偶校验块。
    - 数据恢复通过计算其他磁盘（包括奇偶校验块）的块的异或。
- **工作原理**：使用块交错奇偶校验。数据块和奇偶校验块分布在不同的磁盘上。
- **优点**：提供数据冗余和错误校正能力，但奇偶校验磁盘可能成为瓶颈。

#### RAID Level 5

<figure markdown="span">
![](./img/lec8-8.png){ width="400" }
<figcaption>
RAID 5
</figcaption>
</figure>

- **块交错分布式奇偶校验** ：

    - 数据和奇偶校验分布在所有N+1个磁盘上。
    - 提供比RAID 4更高的I/O速率。
    - 避免了奇偶校验磁盘的瓶颈。

- **工作原理** ：使用块交错分布式奇偶校验。数据和奇偶校验分布在所有磁盘上，避免了单一奇偶校验磁盘的瓶颈。
- **优点** ：提供高I/O速率和数据冗余，适用于大多数应用。

#### RAID Level 6

<figure markdown="span">
![](./img/lec8-9.png){ width="400" }
<figcaption>
RAID 6
</figcaption>
</figure>

- **P+Q冗余方案**：
  - 类似于RAID 5，但存储额外的冗余信息以防止多重磁盘故障。
  - 提供比RAID 5更好的可靠性，但成本更高。
- **工作原理**：使用P+Q冗余方案，类似于RAID 5，但增加了额外的冗余信息以防止多重磁盘故障。
- **优点**：提供更高的可靠性，适用于需要极高数据安全性的应用。

!!!info "Choosing RAID Levels"
    选择RAID级别的因素

    - **成本** ：考虑经济成本。
    - **性能** ：每秒I/O操作次数和正常操作期间的带宽。
    - **故障期间的性能** ：在磁盘故障期间的性能表现。
    - **故障磁盘重建期间的性能** ：包括重建故障磁盘所需的时间。

    RAID级别的使用建议

    - **RAID 0** ：仅在数据安全性不重要时使用，例如数据可以从其他来源快速恢复。
    - **RAID 1和5** ：主要竞争者。
    - **RAID 1** ：提供更好的写入性能，适用于高更新率环境，如日志磁盘。
    - **RAID 5** ：适用于低更新率和大数据量的应用。

    不常用的RAID级别

    - **RAID 2和4** ：不再使用，因为被RAID 3和5取代。
    - **RAID 3** ：由于比特级条带化需要单块读取所有磁盘，浪费磁盘臂移动，已不再使用。
    - **RAID 6** ：由于RAID 1和5提供了足够的安全性，RAID 6使用较少。

    其他注意事项

    - **RAID 1** ：尽管存储成本较高，但随着磁盘容量的快速增长，成本影响减小。
    - **RAID 5** ：需要至少2次块读取和2次块写入来写入单个块，而RAID 1只需2次块写入。

### Hardware

#### 软件RAID

- **定义** ：完全通过软件实现的RAID，不需要特殊的硬件支持。

#### 硬件RAID

- **定义** ：使用特殊硬件实现的RAID。
- **特点** ：

- 使用非易失性RAM记录正在执行的写操作。
- 注意：写入期间的电源故障可能导致磁盘损坏。
- 例如，在写入一个块后但在镜像系统中写入第二个块之前发生故障。
- 这种损坏的数据必须在恢复电源时检测到。
- 从损坏中恢复类似于从故障磁盘中恢复。
- NV-RAM有助于有效检测潜在的损坏块。
- 否则，必须读取磁盘的所有块并与镜像/奇偶校验块进行比较。

### RAID 问题

#### 潜在故障
>Latent failure

- **定义** ：先前成功写入的数据被损坏。
- **影响** ：即使只有一个磁盘故障，也可能导致数据丢失。

#### 数据清理
>Data scrubbing

- **定义** ：持续扫描潜在故障，并从副本/奇偶校验中恢复。

#### 热插拔
>Hot swap

- **定义** ：在系统运行时更换磁盘，无需断电。
- **支持** ：由某些硬件RAID系统支持。
- **优点** ：减少恢复时间，大大提高可用性。

#### 备用磁盘
>Spare disk

- **定义** ：许多系统维护备用磁盘，在线保持，并在检测到故障时立即用作故障磁盘的替代品。
- **优点** ：大大减少恢复时间。

#### 硬件RAID系统的可靠性
>Reliability of hardware RAID systems

- **特点** ：确保单点故障不会停止系统功能。
- **方法** ：
    - 使用带电池备份的冗余电源。
    - 使用多个控制器和多重互连以防止控制器/互连故障。

!!!info "Optical Disk"
    - 只读光盘 (CD-ROM，Compact Disc Read Only Memory)
        - 特点：
            - 可移动光盘，每张容量640 MB。
            - 寻道时间约为100毫秒（光学读头较重且较慢）。
            - 较高的延迟（3000 RPM）和较低的数据传输速率（3-6 MB/s），相比磁盘。
    - 数字视频光盘 (DVD，Digital Versatile Disc)
        - DVD-5：容量4.7 GB，DVD-9：容量8.5 GB。
        - DVD-10和DVD-18：双面格式，容量分别为9.4 GB和17 GB。
        - 蓝光DVD：27 GB（双面光盘为54 GB）。
        - 寻道时间较慢，原因与CD-ROM相同。
        - 一次写入版本 (CD-R和DVD-R)
            - 特点：
                - 数据只能写入一次，不能擦除。
                - 高容量和长寿命；用于档案存储。
        - 多次写入版本（CD-RW、DVD-RW、DVD+RW和DVD-RAM）也可用。

!!!info "Magnetic Tape"
    - **大容量和高传输速率**：
    
    - DAT（数字音频磁带）格式容量为几GB，DLT（数字线性磁带）格式容量为10-40 GB，Ultrium格式容量超过100 GB，Ampex格式容量为330 GB。
    - 传输速率从几MB/s到几十MB/s。

    - **磁带便宜，但驱动器成本很高**。

    - **访问时间非常慢**，与磁盘和光盘相比：
    
    - 仅限于顺序访问。
    - 一些格式（如Accelis）提供更快的寻道（几十秒），但容量较低。

    - **主要用于备份**，存储不常用的信息，以及作为离线介质在系统之间传输信息。

    - **磁带自动机用于超大容量存储**：
    
    - 多个PB（\(10^{15}\)字节）。


## Tertiary Storage 

## Storage Access

## File Organization

## Organization of Records in Files

## Data-Dictionary Storage

## Storage Structures for Object-Oriented Databases

