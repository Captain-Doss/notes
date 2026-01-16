# notes
work book (Day 5) 
the lower value - alway win
the high value - alway lose
cisco - 2 sec hello

unicast = sM Dm = one to one
multicast = dest :00-1-5e-xxx 
broadcast = send to many
root -bridge priority : 24k= protected,32=not protected, 28,

======================================================================
Qpid: 802.1Q:trunking = "make switch love each other!"LQ
Darna: 802.1d: STP = "slowly protect switches" , wait 30 seconds
WonderWoman: 802.1w: rapidSTP = "quickly,Brutally protect switches"
SuperMan: 802.1s: MiSTP = "Protect Many Switches at the same time!"



-conf  t
-default interface range fa0/10-12

-conf t 
config t
NO spanning-tree vlan 1-999
end

config t
 spanning-tree vlan 1-999
end

TAAS/BABA: cupid config
config t
Int Range fa0/10-12
 shutdown
 switchport trunk Encap Dot1Q
 switchport mode trunk
 switchport trunk allowed vlan 1-100
 switchport trunk native vlan 99
 no shut

TAAS/BABA: d1/d2: superman config
config t
vtp domain ccna
vtp password pass
vtp mode server
vtp version 2
exit


Config t  = config para maging -24k            
spanning-tree mode pvst
spanning-tree vlan 1-100 root Secondary
do sh spanning-tree vlan 1
