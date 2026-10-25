$$$ Study workflow $$$

Capture traffic on the monitored endpoint’s virtual interface in Wireshark.
Generate a short, authorized test connection from the endpoint to a listener in the lab. Record the source/destination addresses, port, start time, duration, and byte counts.
Compare it with normal traffic in the same capture. Look for an endpoint initiating an unexpected outbound session, unusual destination ports, repeated connection attempts, long-lived low-volume sessions, or interactive-looking bursts of data.
Check the process and destination on the endpoint, then correlate the connection’s timestamp with the capture. A port number alone is not proof of malicious activity.

$$$ Useful Wireshark filters $$$

1. tcp.flags.syn == 1 && tcp.flags.ack == 0 — initial TCP connection attempts
2. tcp — all TCP traffic
3. tcp.stream eq N — inspect one selected TCP conversation (replace N with its stream number)
4. ip.dst == X.X.X.X — traffic to a specific destination
Use Statistics → Conversations to find unusual peers and ports, then Follow → TCP Stream to inspect a selected conversation. Treat stream contents as potentially sensitive.

Deliverable: A short report listing the observed connection tuple (source/destination IP and port), timing, duration, traffic pattern, why it merits review, and what endpoint evidence would confirm or rule out a reverse shell. Include the capture and note that unusual ports or outbound connections are indicators for investigation—not conclusive evidence.
