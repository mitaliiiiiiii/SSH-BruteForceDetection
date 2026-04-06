# SSH-BruteForceDetection
#20
........................................................................................................................................

SSH Brute Force Detection using journalctl & systemctl

Overview

This project demonstrates how to detect and analyze SSH authentication attempts using Linux system logs. By leveraging "systemctl" and "journalctl", we simulate login attempts and identify patterns such as failed logins and successful access.

---

Objective

- Monitor SSH service activity
- Detect failed login attempts (brute-force pattern)
- Identify successful logins
- Analyze logs based on time and frequency

---

Tools Used

- journalctl (log analysis)
- systemctl (service management)
- grep (filtering logs)
- awk (data extraction)
- sort, uniq (counting occurrences)

---

Steps Performed

1. Start SSH Service

sudo systemctl start ssh

2. Simulate Login Attempts

- Multiple failed login attempts using wrong password
- One successful login

---

3. Analyze SSH Logs

journalctl -u ssh

---

4. Detect Failed Login Attempts

journalctl -u ssh | grep -i "failed"

---

5. Detect Successful Logins

journalctl -u ssh | grep -i "accepted"

---

6. Count Failed Attempts

journalctl -u ssh | grep -i "failed" | wc -l

---

7. Identify Source IP

journalctl -u ssh | grep -i "failed" | awk '{print $(NF-3)}'

---

8. Count Attempts per IP

journalctl -u ssh | grep -i "failed" | awk '{print $(NF-3)}' | sort | uniq -c

---

9. Time-Based Analysis

journalctl -u ssh --since "10 minutes ago"

---

Key Findings

- Multiple failed login attempts were detected
- Source IP identified as local system (::1 / 127.0.0.1)
- Successful login observed after failed attempts
- Demonstrates basic brute-force pattern behavior

---

Key Learnings

- Understood systemd-based logging using journalctl
- Learned how to monitor and analyze SSH authentication logs
- Practiced detecting brute-force patterns
- Improved log filtering and analysis skills

---

Conclusion

This exercise demonstrates a basic approach to detecting brute-force login attempts using Linux system logs. It highlights the importance of monitoring authentication logs for security analysis
