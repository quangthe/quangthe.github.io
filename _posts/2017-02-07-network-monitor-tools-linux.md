---
layout: post
title: Command line tools to monitor network on Linux
---

I have a Raspberry Pi (Rasp Pi) running MiniDLNA to serve music streaming at home. The Rasp Pi is mounted on wall and has no monitor attached to it. To check whether Rasp Pi can serve all its clients smoothly, we need to install some command line tools on Rasp Pi and run it via ssh terminal. 

Here are some my favorite tools

## iftop
Iftop measures the data flowing through individual socket connections. 

Pros:

- Reports the bandwidth used by individual connections

Cons: 

- Cannot report the process name/id involved in the particular socket connection

```bash
$ sudo iftop -n

              12.5Kb         25.0Kb        37.5Kb         50.0Kb   62.5Kb
└─────────────┴──────────────┴─────────────┴──────────────┴──────────────
192.168.1.16           => 192.168.1.12            1.97Kb  9.57Kb  7.82Kb
                       <=                          208b   1.55Kb  1.28Kb
239.255.255.250        => 192.168.1.19               0b      0b      0b
                       <=                            0b   4.61Kb  3.29Kb
255.255.255.255        => 192.168.1.19               0b      0b      0b
                       <=                         4.11Kb  3.29Kb  3.52Kb
239.255.255.250        => 192.168.1.4                0b      0b      0b
                       <=                         1.93Kb  2.72Kb  1.94Kb
224.0.0.251            => 192.168.1.6                0b      0b      0b
                       <=                          488b    518b   1.28Kb
255.255.255.255        => 192.168.1.12               0b      0b      0b
                       <=                            0b    156b    111b
192.168.1.255          => 192.168.1.12               0b      0b      0b
                       <=                            0b    156b    111b




─────────────────────────────────────────────────────────────────────────
TX:             cum:   13.7KB   peak:   3rates:   1.97Kb  9.57Kb  7.82Kb
RX:                    20.2KB           28.7Kb    6.72Kb  13.0Kb  11.5Kb
TOTAL:                 33.9KB           60.3Kb    8.69Kb  22.5Kb  19.4Kb

```


## vnstat
Runs a background service/daemon and keeps recording the size of data transfer all the time.

Check service status
```bash
$ service status vnstat
```

```
$ vnstat 
Database updated: Tue Feb  7 14:36:43 2017

   eth0 since 02/06/17

          rx:  438.29 MiB      tx:  2.96 GiB      total:  3.38 GiB

   monthly
                     rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
       Feb '17    438.29 MiB |    2.96 GiB |    3.38 GiB |   49.71 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated      1.81 GiB |   12.52 GiB |   14.33 GiB |

   daily
                     rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
     yesterday    353.46 MiB |  873.41 MiB |    1.20 GiB |  116.33 kbit/s
         today     84.83 MiB |    2.10 GiB |    2.19 GiB |  348.50 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated       138 MiB |    3.45 GiB |    3.59 GiB |
```

To monitor the bandwidth usage in realtime, use the '-l' option (live mode)

```
$ vnstat -l -i eth0
Monitoring eth0...    (press CTRL-C to stop)

   rx:        3 kbit/s     1 p/s          tx:        2 kbit/s     0 p/s
```

## speedometer
Visualize incomming and outgoing traffic on given interface 

```bash
$ speedometer -r eth0 -t eth0
```

![alt text](https://github.com/quangthe/quangthe.github.io/blob/master/images/speedometer.png?raw=true "Speedometer")
