# DDOS-Playbook-Response

## Scenario
An external attacker launches a distributed denial-of-service (DDoS) attack targeting public-facing infrastructure such as websites, APIs, DNS servers or network gateways. The objective is to disrupt service availability, degrade performance or cause reputational and financial damage.

## Incident Classification
| Category            | Details   |
|---------------------|--------------|
| Incident Type       | Network/Application Layer Availability Attack |
| Severity            | High (especially for customer-facing or critical systems) |
| Priority            | Critical if sustained outage or service degradation occurs |
| Detection Sources   | NOC alerts, SIEM, firewall logs, application monitoring tools, CDN/WAF, ISP notifications |

## Phases and Actions
### 1. Preparation (Pre-Incident Setup)
| Task                | Tool/Action |
|---------------------|--------------|
| Implement DDoS Protection | Use cloud-based mitigation services (e.g., Cloudflare, AWS Shield, Akamai) |
| Deploy WAF and rate limiting | Protect applications and APIs |
| Ensure scalable infrastructure | Use autoscaling groups or CDN caching to absorb surges |
| Establish communication with ISP | Predefine escalation process and mitigation support |
| Conduct DDoS drills | Simulate DDoS scenarios and validate response procedures |

### 2. Detection & Analysis
| Step                 | Action    |
|----------------------|---------------|
| Identify traffic surge | Monitor bandwidth, request rates or connection counts exceeding normal thresholds |
| Determine attack vector | Is it volumetric (UDP flood), protocol (SYN flood) or application-layer (HTTP GET flood)? |
| Correlate with logs | Identify source IPs, user agents, referrers, payloads |
| Confirm Impact | Assess performance degradation, service outages or collateral damage |
| MITRE ATT&CK mapping | T1498 (Network Denial of Service), T1499 (Endpoint Denial of Service), T1498.001 (Direct Network Flood) |

### 3. Containment
| Step                  | Action           |
|-----------------------|-------------------------|
| Engage cloud DDos mitigation service | Route traffic through mitigation provider (e.g., Cloudflare Magic Transit) | 
| Block malicious IPs | Using firewall, WAF or geo-blocking rules |
| Implement rate limiting and filters | Drop traffic by rate thresholds or specific patterns |
| Redirect or reroute traffic | Temporarily divert traffic to alternate IP or load balancer |

### 4. Eradication
| Step                   | Action           |
|------------------------|------------------------|
| Drop traffic from confirmed malicious sources | Based on IP reputation or behavioural patterns |
| Adjust filtering rules | Fine-tune ACLs, WAF policies, IDS/IPS signatures |
| Remove temporary rules post-attack | Once attack subsides, restore normal access patterns |
| Investigate for blended threats | Confirm no malware or lateral movement occurred during the disruption |

### 5. Recovery
| Step                    | Action           |
|-------------------------|--------------------------|
| Monitor for residual traffic | Use NOC dashboards and SIEM to track post-attack anomalies |
| Confirm service restoration | Perform user acceptance testing or API health checks |
| Notify affected customers or partners | If SLAs or public services were impacted |
| Resume normal routing | If temporary redirection or black-holing was used during attack |

### 6. Lessons Learned & Reporting
| Step                     | Action              |
|--------------------------|----------------------------|
| Conduct incident review | Document timeline, impact, attacker strategy and response actions |
| Access mitigation effectiveness | Determine what worked and what needs to be improved |
| Update response playbook | Refine thresholds, alerting rules and communication steps |
| Improve vendor coordination | Review performance of ISP and mitigation patterns |
| Report as required | To regulators, leadership or clients if impact was severe or prolonged |

## Tools Typical Involved
- SIEM (e.g., Splunk, Sentinel)
- Network traffic analysis tools (e.g., NetFlow, Zabbix, Ixia)
- DDoS protection services (e.g., Cloudflare, AWS Shield, Akamai Kona)
- Firewall/WAF (e.g., Fortinet, Palo Alto, ModSecurity)
- CDN and DNS services (e.g., CloudFlare, Fastly, Akamai)
- ISP support and coordination channels

## Success Metrics
| Metric            | Target       |
|-------------------|------------------|
| Time to Detect DDoS | <5 minutes from onset |
| Mitigation Engagement Time | <15 minutes from confirmation |
| Service Downtime | Zero or <30minutes |
| Customer Notification Time | Within 1 hour if SLA is affected |
| Post_Mortem Completion | Within 48 hours |

