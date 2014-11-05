Server:

ib0       Link encap:InfiniBand  HWaddr A0:00:02:20:FE:80:00:00:00:00:00:00:00:00:00:00:00:00:00:00
          inet addr:10.10.0.34  Bcast:10.10.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:65520  Metric:1
          RX packets:3162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1024
          RX bytes:1008686 (985.0 KiB)  TX bytes:344910 (336.8 KiB)

Infiniband device 'mlx4_0' port 1 status:
        default gid:     fe80:0000:0000:0000:0002:c903:00ee:ae01
        base lid:        0x7
        sm lid:          0x2
        state:           4: ACTIVE
        phys state:      5: LinkUp
        rate:            56 Gb/sec (4X FDR)
        link_layer:      InfiniBand

Infiniband device 'mlx4_0' port 2 status:
        default gid:     fe80:0000:0000:0000:0002:c903:00ee:ae02
        base lid:        0x6
        sm lid:          0x2
        state:           4: ACTIVE
        phys state:      5: LinkUp
        rate:            56 Gb/sec (4X FDR)
        link_layer:      InfiniBand

# ib_read_lat -d mlx4_0 -i 1
************************************
* Waiting for client to connect... *
************************************

Client:

# ib_read_lat -d mlx4_0 -i 1 -a 10.10.0.34
---------------------------------------------------------------------------------------
                    RDMA_Read Latency Test
 Dual-port       : OFF          Device         : mlx4_0
 Number of qps   : 1            Transport type : IB
 Connection type : RC           Using SRQ      : OFF
 TX depth        : 1
 Mtu             : 2048[B]
 Link type       : IB
 Outstand reads  : 16
 rdma_cm QPs     : OFF
 Data ex. method : Ethernet
---------------------------------------------------------------------------------------
 local address: LID 0x01 QPN 0x0264 PSN 0xb41e9e OUT 0x10 RKey 0x98011302 VAddr 0x007faf47400000
 remote address: LID 0x07 QPN 0x0262 PSN 0xcf7035 OUT 0x10 RKey 0xd8011314 VAddr 0x007fb500ad3000
---------------------------------------------------------------------------------------
 #bytes #iterations    t_min[usec]    t_max[usec]  t_typical[usec]
 2       1000          2.29           15.78        2.34
 4       1000          2.28           7.58         2.34
 8       1000          2.25           4.61         2.31
 16      1000          2.25           5.56         2.31
 32      1000          2.27           5.85         2.32
 64      1000          2.28           5.03         2.35
 128     1000          2.32           4.52         2.38
 256     1000          2.44           5.58         2.49
 512     1000          2.60           5.97         2.65
 1024    1000          2.89           4.39         2.95
 2048    1000          3.48           7.56         3.55
 4096    1000          4.07           8.42         4.13
 Completion with error at client
 Failed status 10: wr_id 0 syndrom 0x88
scnt=1, ccnt=1

Server:

TEST BW
Server:

# ib_read_bw -d mlx4_0 -i 1

************************************
* Waiting for client to connect... *
************************************

Client:
#watch -n 1 perfquery -l 7 1
Every 1.0s: perfquery -l 7 1                                                                                                                    Wed Nov  5 11:32:44 2014

# Port counters: Lid 7 port 1 (CapMask: 0x1400)
PortSelect:......................1
CounterSelect:...................0x0000
SymbolErrorCounter:..............0
LinkErrorRecoveryCounter:........0
LinkDownedCounter:...............0
PortRcvErrors:...................0
PortRcvRemotePhysicalErrors:.....0
PortRcvSwitchRelayErrors:........0
PortXmitDiscards:................0
PortXmitConstraintErrors:........0
PortRcvConstraintErrors:.........0
CounterSelect2:..................0x00
LocalLinkIntegrityErrors:........0
ExcessiveBufferOverrunErrors:....0
VL15Dropped:.....................0
PortXmitData:....................6465317
PortRcvData:.....................427938
PortXmitPkts:....................41531
PortRcvPkts:.....................130792613
PortXmitWait:....................2

