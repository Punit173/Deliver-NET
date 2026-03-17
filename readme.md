# <span style="color: #1E88E5;">DeliverNET</span>
### <span style="color: #42A5F5;">Network for Earnings Trust</span>

**DeliverNET** is an AI-powered parametric insurance platform that protects India's gig delivery workers (e.g., Swiggy, Zomato) from income loss. 

**The Problem:** Delivery partners often lose **20–30% of their weekly earnings** to uncontrollable external disruptions (extreme weather, strikes, road blockages) and currently absorb the entire financial loss themselves. 

**The Solution:** Operating on a **weekly premium model** aligned with their earning cycle, DeliverNET focuses exclusively on **income protection**. It continuously monitors environmental and social signals to automatically **detect disruptions and trigger instant payouts** for affected workers.

---

# <span style="color: #1E88E5;">Delivery Persona</span>

## <span style="color: #2196F3;">Persona: Food Delivery Partner (Swiggy / Zomato)</span>

Profile of a typical worker:

- Works 4–10 hours per day
- Earnings depend on completed deliveries
- Weekly earnings fluctuate depending on demand
- Operates within a fixed delivery zone

Types of delivery workers:

| Worker Type | Description |
|--------------|-------------|
| Full-time Hustler | Works 8–10 hours daily |
| Part-time Rider | Works 4–6 hours daily |
| Casual Rider | Works occasionally during peak hours |

### <span style="color: #64B5F6;">Persona Scenarios</span>

- **Rahul (Full-time Hustler):** Relies on deliveries to support his family. A 2-day localized flood can wipe out 30% of his weekly income, severely impacting his ability to meet basic expenses.
- **Sunita (Part-time Rider):** Balances deliveries with college classes. When unexpected political strikes barricade roads during her peak evening hours, she loses her crucial supplemental income.
- **Anil (Casual Rider):** Logs in primarily on weekends for extra cash. A sudden internet shutdown in his zone completely derails his already limited window of earning opportunity.

Income loss occurs when unpredictably these disruptions prevent them from working.

---

# <span style="color: #1E88E5;">Application Workflow</span>

```text
+-----------------------+
| 1. Worker Onboarding  |
| - App Installation    |
| - Aadhaar Verification|
| - Create ID Token     |
+-----------------------+
            |
            v
+-----------------------+
|  2. Risk Profiling    |
| - Activity Patterns   |
| - Zone Disruption Risk|
| - Compute Risk Score  |
+-----------------------+
            |
            v
+-----------------------+
| 3. Weekly Policy      |
| - Dynamic Premium     |
| - Issue Weekly Cover  |
+-----------------------+
            |
            v
+-----------------------+
| 4. Real-Time Monitor  |
| - Weather/Traffic APIs|
| - Platform Status     |
| - Worker Mobility     |
+-----------------------+
            |
            v
+-----------------------+
| 5. Disruption Detect  |
| - Dual-Gate Validation|
| - Auto Claim Initiate |
+-----------------------+
            |
            v
+-----------------------+
|  6. Instant Payout    |
| - Benefit Calculated  |
| - Direct Compensation |
| - Mobile Notification |
+-----------------------+
```

---

# <span style="color: #1E88E5;">Disruption Types</span>

| Disruption Type | Example Scenario | Impact |
|-----------------|------------------|--------|
| Environmental | Severe rainfall causing waterlogging in delivery zones | Deliveries halted |
| Environmental | Heatwave with temperature exceeding safe outdoor limits | Reduced working hours |
| Environmental | Hazardous AQI levels due to pollution | Outdoor work unsafe |
| Social | Local protest blocks restaurant access roads | Pickup locations inaccessible |
| Social | City curfew or police barricades | Delivery zones restricted |
| Infrastructure | Internet shutdown in region | Platform connectivity lost |
| Infrastructure | Major road closure due to construction or accident | Delivery routes blocked |

---

# <span style="color: #1E88E5;">Weekly Premium Model</span>

DeliverNET's dynamic weekly premium and disruption payouts are determined by parameters like **worker type (Hustler: 1.5x, Part-time: 1.0x, Casual: 0.7x), delivery zone risk, seasonal risks, and historical earnings.**

### <span style="color: #2196F3;">Calculations at a Glance</span>

> **Weekly Premium:**  
> `~1% of Average Weekly Earnings`  
> _(e.g., Full-time earning ₹5000/week pays ₹50 premium)_
>
> **Disruption Payout:**  
> `Proportional to Daily Earnings (Weekly / 7) × Severity`  
> _(e.g., [₹5000 / 7] × 0.8 severe disruption ≈ ₹570 payout)_

*(Note: Payouts automatically scale within the defined worker type tier.)*

### <span style="color: #2196F3;">Coverage Tiers Example</span>

| Worker Type | Earnings Range | Weekly Premium | Coverage per Event |
| ----------- | -------------- | -------------- | ------------------ |
| Casual      | ₹1500–2500     | ₹15 – ₹25      | ₹100 – ₹200        |
| Part-time   | ₹2500–4000     | ₹25 – ₹40      | ₹200 – ₹350        |
| Full-time   | ₹4000–7000     | ₹40 – ₹70      | ₹350 – ₹600        |


---

# <span style="color: #1E88E5;">Parametric Trigger System</span>

DeliverNET uses **multi-gate parametric validation**.

---

## <span style="color: #2196F3;">Gate 1: External Trigger Detection</span>

| Trigger | Threshold | Data Source |
|--------|-----------|-------------|
| Heavy Rain | > 50mm/hour | Weather API |
| Heatwave | > 45°C | Weather API |
| Air Pollution | AQI > 400 | AQI API |
| Traffic Block | Severe congestion / road closure | Traffic API |
| Social Disturbance| Sudden drop in deliveries | Platform activity data |

---

## <span style="color: #2196F3;">Gate 2: Activity and Location Validation</span>

System verifies:

- worker location
- delivery activity
- online status
- movement patterns

---

## <span style="color: #2196F3;">Gate 3: Authority Geofencing</span>

DeliverNET provides a portal for local authorities (e.g., police, municipal corporations) to draw **virtual geofences** around heavily disrupted or restricted areas (e.g., riot zones, sudden road collapses, major VIP events). 

When an authority geofence is activated:
- Riders pinging from within the boundary are automatically classified under a valid disruption.
- Acts as a high-priority override, instantly verifying the disruption without needing secondary external API confirmation.

Only if **these gates confirm disruption**, payouts are triggered.

---

# <span style="color: #1E88E5;">Platform Data Example</span>

Platform activity signals are simulated using APIs.

Example event streams:

```json
// Swiggy sends:
{"worker_hash": "D9F3X7...", "platform": "swiggy", "status": "offline", "zone": "andheri_east_3"}

// Zomato sends:
{"worker_hash": "D9F3X7...", "platform": "zomato", "status": "offline", "zone": "andheri_east_3"}
```

These signals help detect **mass activity drops in specific zones**.

---

# <span style="color: #1E88E5;">Mobile Platform Justification</span>

DeliverNET is designed as a **mobile-first platform**.

Reasons:

- Delivery workers primarily operate using smartphones
- Enables real-time notifications
- Allows continuous activity tracking
- Simplifies permission management (location, movement, network)
- Enables instant payout alerts
- Allows background disruption monitoring

Mobile integration ensures **minimal friction for workers**.

---

# <span style="color: #1E88E5;">AI / ML Integration</span>

AI powers several core components of DeliverNET to ensure accurate validations, discover unmapped disruptions, and prevent fraud.

## <span style="color: #2196F3;">1. AI-Powered Risk Assessment</span>
Machine learning models predict disruption risk based on **weather history, zone-level disruption patterns, traffic congestion, seasonal trends, and worker behavior**, outputting a `Zone Risk Score (0-1)` that dynamically influences premium pricing.

---

## <span style="color: #2196F3;">2. Behavioral Graph Analysis (Alternative Discovery)</span>
DeliverNET implements network-level behavior pattern analysis instead of relying purely on fixed anomaly thresholds.

*Example:*
```text
Delivery network graph suddenly fragments.

Clusters of riders disconnect from restaurant hubs.

Graph connectivity drops below threshold.

System flags "Operational Network Collapse".

Admin validates cause:
Localized internet outage affecting delivery apps.

AI stores network signature.

Future occurrences auto-trigger disruption classification.
```
---

## <span style="color: #2196F3;">3. Problem Listener Agent (Fallback NLP)</span>
Not all real-world disruptions are captured by automated sensors. The **Problem Listener** is a trained AI conversational agent that acts as a fallback claim channel. 

1. **Worker Reports Issue:** The worker opens the app and describes the disruption in natural language.
2. **AI Analyzes:** The agent uses NLP to parse the context, cross-checks the GPS trail and activity logs, correlates data with other riders in the micro-zone, and re-queries external APIs.
3. **Claim Decision:** If validated as genuine, the NLP agent automatically calculates and triggers the payout. Inconclusive claims are escalated to admins.

**Sample Chat Flow:**
```text
Worker:  "I couldn't deliver for 3 hours today. There was a gas leak near MG Road..."
Agent:   Analyzing... Location confirmed. Activity dropped to 0. 6 other riders in zone offline. News API confirms gas leak.
         Claim Status: APPROVED. Estimated Loss: ₹380 credited.
```

---

## <span style="color: #2196F3;">4. Intelligent Fraud Detection</span>

- **Duplicate Claim Prevention:** To prevent multi-platform double claiming (e.g., Swiggy & Zomato), a **Canonical Identity Token** is generated securely on a blockchain layer. All platform claims link to a single identity.
- **Location and Activity Validation:** Worker activity is constantly monitored through GPS, average orders, and active time. If a worker is inactive during the disruption window, their automated payout may be flagged and denied.

---

# <span style="color: #1E88E5;">Edge Case Handling</span>

### <span style="color: #42A5F5;">Scenario</span>

If a rider’s weekly earnings are **insufficient to cover the premium deduction**.

Example:

```text
Weekly earnings: ₹120
Premium due: ₹29
```

### <span style="color: #42A5F5;">Solution</span>

DeliverNET introduces **Premium Grace Buffer**.

Rules:

- Premium deduction delayed for one week
- Worker continues to receive disruption protection
- Premium recovered from next active week

If inactivity continues for multiple weeks:

```text
Policy automatically moves to "Dormant Mode"
Coverage paused until next earning cycle.
```

---

# <span style="color: #1E88E5;">Tech Stack</span>

| Component | Technologies & Tools |
|-----------|----------------------|
| **Mobile App** | Flutter |
| **Backend** | Node.js, FastAPI |
| **AI / ML** | Python, Scikit-learn, Pandas, NumPy |
| **Database** | PostgreSQL, Redis (for real-time events) |
| **Blockchain** | Identity hash storage, Canonical identity tokens |
| **External APIs** | OpenWeather API, Google Maps Traffic, Swiggy/Zomato (Simulated) |
| **Payments** | Razorpay Sandbox, UPI Simulation |

---

# <span style="color: #1E88E5;">Development Plan</span>

### <span style="color: #42A5F5;">Phase 1 – Ideation</span>

- Define persona
- Design risk model
- Create disruption detection logic
- Document architecture

---

### <span style="color: #42A5F5;">Phase 2 – Automation</span>

- Worker onboarding system
- Policy creation
- Premium calculation engine
- Parametric trigger monitoring

---

### <span style="color: #42A5F5;">Phase 3 – Scale & Optimisation</span>

- AI anomaly detection
- Fraud detection system
- Instant payout simulation
- Analytics dashboards

---

# <span style="color: #1E88E5;">Project Name</span>

**DeliverNET**: Network for Earnings Trust