<!-- HEADER WAVE -->
<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=0,2,2,5,30&height=180&section=header&text=StrikeShield&fontSize=48&fontColor=00FF41&fontAlignY=40&desc=Red%20Team%20vs%20Blue%20Team%20%7C%20Solo%20Attack%20%26%20Defense%20Lab&descSize=17&descAlignY=62&descColor=ffffff&animation=twinkling"/>

<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=18&pause=1200&color=00FF41&center=true&vCenter=true&width=520&height=45&lines=3+Live+VMs+%7C+1+Solo+Operator;19%2C369+Requests+Generated+%26+Blocked;Attacker+%2B+Defender+%3A%3A+Same+Person;Nmap+%7C+Dirb+%7C+Curl+%7C+UFW+%7C+Apache" alt="typing"/>

<br/><br/>

<img src="https://img.shields.io/badge/Status-Complete-00FF41?style=for-the-badge&labelColor=0d1117"/>
<img src="https://img.shields.io/badge/Type-Red%20Team%20%2F%20Blue%20Team-red?style=for-the-badge&labelColor=0d1117"/>
<img src="https://img.shields.io/badge/Requests%20Logged-19%2C369-0066FF?style=for-the-badge&labelColor=0d1117"/>

</div>

---

## `$ ./overview`

```json
{
  "project"     : "StrikeShield",
  "type"        : "Red Team vs Blue Team simulation",
  "environment" : "3 live virtual machines",
  "operator"    : "Solo — played both attacker and defender",
  "requests"    : "19,369 real HTTP requests generated and analyzed",
  "goal"        : "Simulate a realistic attack chain, then detect, log, and block it"
}
```

StrikeShield is a self-contained offense/defense lab built across three live VMs. I attacked my own infrastructure with real reconnaissance and enumeration tools, then switched hats to detect and block that same traffic using firewall rules and log analysis — no scripts faking the traffic, no simulated logs. Every request in the dataset actually hit the target.

---

## 🖥️ Lab Architecture

```
 ┌─────────────────┐        ┌─────────────────┐        ┌─────────────────┐
 │   ATTACKER VM    │        │    TARGET VM     │        │   DEFENDER VM    │
 │  Kali Linux       │──────▶│  Apache + Web App │◀──────│  UFW + Log Watch │
 │  Nmap / Dirb /    │        │  (intentionally   │        │  iptables rules  │
 │  Curl             │        │   exposed)        │        │  Log analysis    │
 └─────────────────┘        └─────────────────┘        └─────────────────┘
        │                                                        ▲
        └────────────────────  19,369 requests  ─────────────────┘
```

---

## ⚔️ Red Team Phase

<div align="center">

| Stage | Tool | Purpose |
|:---:|:---:|:---|
| 🔍 Recon | **Nmap** | Port scanning, service/version fingerprinting |
| 📂 Enumeration | **Dirb** | Directory & file brute-forcing against the web app |
| 🌐 Exploitation attempts | **Curl** | Manual request crafting, header manipulation, endpoint probing |

</div>

**What was tested:** open ports, exposed services, hidden/unlinked directories, misconfigured endpoints, and repeated brute-force patterns against the target's web surface.

---

## 🛡️ Blue Team Phase

<div align="center">

| Stage | Tool | Purpose |
|:---:|:---:|:---|
| 🚧 Blocking | **UFW** | Firewall rules to rate-limit and block malicious source IPs |
| 📊 Detection | **Apache log analysis** | Parsed access/error logs to identify scan patterns, brute-force signatures, and anomalous request rates |
| 🔁 Response loop | Manual | Rules updated iteratively as new attack patterns were observed |

</div>

**What was detected:** Nmap scan signatures, Dirb's sequential directory brute-force pattern, and abnormal request-rate spikes consistent with automated enumeration — all traced back to source IP and blocked at the firewall.

---

## 📈 Results

```
 Total requests generated  : 19,369
 Requests blocked          : [add your final blocked count here]
 Detection method          : Apache log pattern analysis
 Mitigation method         : UFW rule-based IP blocking
 Time to detect (avg)      : [add your measured detection time here]
```

> Fill in the two bracketed values with your actual lab numbers if you tracked them — real metrics here are what make this stand out in an interview.

---

## 🧠 Key Takeaways

- Recon and enumeration tools leave distinct, detectable signatures in web server logs
- Firewall rules alone aren't enough — pairing UFW blocking with active log monitoring closed the gap between "attack happened" and "attack detected"
- Running both sides solo forced a genuinely adversarial mindset on both ends, rather than defending against a known/scripted attack

---

## 🛠️ Built With

<div align="center">

<img src="https://skillicons.dev/icons?i=linux,bash,apache&theme=dark&perline=5"/>

</div>

---

<div align="center">

### 🤝 Part of my broader security portfolio

<a href="https://github.com/SaiDinesh200214"><img src="https://img.shields.io/badge/GitHub-Profile-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
<a href="https://saidinesh-portfolioweb.netlify.app/"><img src="https://img.shields.io/badge/Portfolio-Visit-00FF41?style=for-the-badge&labelColor=0d1117"/></a>

</div>

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=0,2,2,5,30&height=120&section=footer&text=TARGET%20SECURED%20%E2%9C%85&fontSize=26&fontColor=00FF41&fontAlignY=55&animation=twinkling"/>
