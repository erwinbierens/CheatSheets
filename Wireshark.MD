Wireshark Cheatsheet
--------------------------------

Wireshark is a network packet analyzer. A network packet analyzer will try to capture network packets and tries to display that packet data as detailed as possible.
You could think of a network packet analyzer as a measuring device used to examine what’s going on inside a network cable, just like a voltmeter is used by an electrician to examine what’s going on inside an electric cable (but at a higher level, of course).
In the past, such tools were either very expensive, proprietary, or both. However, with the advent of Wireshark, all that has changed.
Wireshark is perhaps one of the best open source packet analyzers available today.

[+] RTP + No QoS
Searching for RTP Packets within a specified range that DO NOT have the DSCP field set to “46” or IP PREC 5.

(udp.port >=16384 and udp.port <= 32767) and not(ip.dsfield.dscp==46 or ip.tos.precedence==5)

[+] RTP other than G.711 or G.729 
Searches for RTP types other than G.711 or G.729. Why would I need this? 
If you are using Cisco NBAR to match packets in a class-map the “audio” and “video” keywords only match specific traffic. 
You can define payload types to match as well. For instance, DTMF is usually payload type 101, T.38 is another dynamic payload type.

not (rtp.p_type==0 or rtp.p_type==18)

[+] Not Source port UDP/TCP port 5060
Searches for SIP Packets that are not sourced from UDP port 5060 or TCP port 5060.

not (udp.srcport==5060 or tcp.srcport==5060) and sip

[+] Not Destination port UDP/TCP 5060  
Searches for SIP packets that are not destined for UDP port 5060 or TCP port 5060.

not (udp.dstport==5060 or tcp.dstport==5060) and sip

[+] Searches for a specific MPLS label that is not tagged with EXP 5.

mpls.label==123123 and not mpls.exp==5
