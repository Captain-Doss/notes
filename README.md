# notes
work book (Day 5) 
the lower value - alway win
the high value - alway lose
cisco - 2 sec hello

unicast = sM Dm = one to one
multicast = dest :00-1-5e-xxx 
broadcast = send to many
root -bridge priority : 24k= protected,32=not protected, 28,

how becomes RootPort = kanangKamay
Cost >> Priority >> Number, lowest cost WINS!
10G cost - 1
1gig cost = 4
faE cost = 19
======================================================================
Qpid: 802.1Q:trunking = "make switch love each other!"LQ
Darna: 802.1d: STP = "slowly protect switches" , wait 30 seconds
WonderWoman: 802.1w: rapidSTP = "quickly,Brutally protect switches"
SuperMan: 802.1s: MiSTP = "Protect Many Switches at the same time!"


corebaba = back to being normal (no config)
-conf  t
-default interface range fa0/10-12

-conf t 
config t
NO spanning-tree vlan 1-999
end

config t
 spanning-tree vlan 1-999
end


293-320
TAAS/BABA: *********************(cupid config)*
config t
Int Range fa0/10-12
 shutdown
 switchport trunk Encap Dot1Q
 switchport mode trunk
 switchport trunk allowed vlan 1-100
 switchport trunk native vlan 99
 no shut


346 -365
*************************(wonderwoman config)*
config t
spanning-tree Mode Rapid-pvst
do sh spanning-tree vlan 1
configure 802.1w/RapidSTP:

TAAS/d1: RootBridge: laspagin si Wonderwoman
config t
spanning-tree Mode Rapid-pvst
spanning-tree BackBoneFast
spanning-tree portfast bpduguard default
Int Range fa0/1-8
   spanning-tree Portfast
@BABA/d2/a1/a2:
config t
spanning-tree Mode Rapid-pvst
spanning-tree UplinkFast
spanning-tree portfast bpduguard default
Int Range fa0/1-8
  spanning-tree Portfast
end

************how to check(wonderwoman)
802.1WDoes NOT forgive Mistakes/KIll it.
**#sh int status err-disabled **
TAAS: bounce/UP/down, bring BACK TO LIFE.
config t
int fa 0/3
 shut
 no shut
int fa 0/7
 shut
 no shut
end

383 - 424
*****************************(Superman config)*
config t
vtp domain ccna
vtp password pass
vtp mode server
vtp version 2
exit

a1/a2: access SW
config t
vtp domain ccna
vtp password pass
vtp mode client
vtp version 1
exit

TAAS:/D1
config t
vlan 11-19
exit
vlan 21-29
exit
vlan 31-39
exit
BABA: sh vlan brief:

CONFIG T
spanning-tree mode Mst
spanning-tree mst configuration
 name supermanstp
 revision 1
   Instance 1 vlan 11-19
   Instance 2 vlan 21-29
   Instance 3 vlan 31-39
exit
do sh spanning-tree mst configuration 


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

TASK14: MAKE YOUR OWN SUPERMAN BOSSING:


@Taas: Make Taas RootBridge again:/d1
config t
spanning-tree mst 0 root primary
spanning-tree mst 1 root secondary
spanning-tree mst 2 root primary
spanning-tree mst 3 root secondary
@baba/d2
config t
spanning-tree mst 0 root Secondary
spanning-tree mst 1 root primary
spanning-tree mst 2 root Secondary
spanning-tree mst 3 root primary


************(PANO PROTECTAHAN ANG MGA PORT )
@BABA
config t
Int fa0/6
switchport mode access
switchport port-security
switchport port-security mac-address Sticky
switchport port-security maximum 1
switchport port-security violation shutdown
Int fa0/8
switchport mode access
switchport port-security
switchport port-security mac-address Sticky
switchport port-security maximum 1
switchport port-security violation shutdown
do sh port-security address
   1    ccd8.c1fb.1045    SecureSticky                  Fa0/6        -
   1    ccd8.c1fb.2325    SecureSticky                  Fa0/8
do sh int status err-disable

476-484
******HOW TO DISABLE IT******
config t
Int fa0/6
NO switchport port-security
shut
no shut
Int fa0/8
NO switchport port-security
shut
no shut


=====================
config t
hostname PLDT-ITO
Track 1 Int gi 0/1 line-protocol
Int vlan 1
standby 1 ip 10.22.1.6
standby 1 preempt
standby 1 Priority 150
standby 1 Track 1 decrement 60

@D1 para realworld:
config t
Track 1 Int e1/0 line-protocol
Int vlan 10
standby 10 ip 10.22.1.3
standby 10 preempt
standby 10 Priority 150
standby 10 Track 1 decrement 60

config t
hostname GLOBE-ITO
Int vlan 1
standby 1 ip 10.22.1.6
standby 1 preempt
standby 1 Priority 100
end

config t
Track 1 Int e1/0 line-protocol
Int vlan 10
standby 10 ip 10.22.1.3
standby 10 preempt
standby 10 Priority 150
standby 10 Track 1 decrement 60
