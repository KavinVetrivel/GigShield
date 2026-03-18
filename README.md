# GigShield — AI-Powered Parametric Income Insurance for India's Gig Economy

> **Guidewire DEVTrails 2026** | University Hackathon Submission
> **Persona:** Food Delivery Partners — Zomato & Swiggy riders
> **Coverage:** Income loss only · Weekly pricing model · Zero-touch claims

---

## Table of Contents

1. [Problem Statement & Why It Matters](#1-problem-statement--why-it-matters)
2. [Why the Current System Fails](#2-why-the-current-system-fails)
3. [Our Solution — GigShield](#3-our-solution--gigshield)
4. [Persona & User Scenarios](#4-persona--user-scenarios)
5. [Innovation Differentiators](#5-innovation-differentiators)
6. [Weekly Premium Model](#6-weekly-premium-model)
7. [Parametric Triggers](#7-parametric-triggers)
8. [System Architecture](#8-system-architecture)
9. [AI/ML Integration](#9-aiml-integration)
10. [Fraud Detection Engine](#10-fraud-detection-engine)
11. [Zero-Touch Claims & Payout Flow](#11-zero-touch-claims--payout-flow)
12. [Tech Stack](#12-tech-stack)
13. [Platform Choice — Web PWA](#13-platform-choice--web-pwa)
14. [Data Models](#14-data-models)
15. [API Design](#15-api-design)
16. [Development Roadmap (6 Weeks)](#16-development-roadmap-6-weeks)
17. [Business Viability](#17-business-viability)
18. [Team](#18-team)

---

## 1. Problem Statement & Why It Matters

India has **12+ million platform-based delivery partners** working for Zomato, Swiggy, Zepto, Amazon, and Dunzo. They are the last-mile backbone of the country's digital economy, yet they operate with zero financial protection against the disruptions that make their work impossible.

When a monsoon floods Velachery, a curfew shuts down Koramangala, or a severe AQI alert grounds riders in Delhi — these workers lose 100% of that day's income with no recourse. Research shows external disruptions cost gig workers **20–30% of monthly earnings** on average, with no existing insurance product covering this gap.

### The Core Gap

```
What exists today:          What gig workers actually need:
─────────────────────       ────────────────────────────────
Annual/monthly premiums  →  Weekly premiums (matches pay cycle)
Static risk forms        →  Real-time, hyper-local risk data
Manual 15–45 day claims  →  Automatic sub-90-second payouts
Salaried worker focus    →  Informal/gig worker eligible
Health/accident cover    →  Income protection during disruptions
```

---

## 2. Why the Current System Fails

### Three Disconnected Silos

```
┌─────────────────────┐     ┌─────────────────────┐     ┌─────────────────────┐
│   GIG PLATFORM      │     │  FORMAL INSURANCE   │     │   THE WORKER        │
│  (Zomato/Swiggy)    │     │  (IRDAI products)   │     │  (Self-managed)     │
├─────────────────────┤     ├─────────────────────┤     ├─────────────────────┤
│ Per-order payments  │     │ Annual/monthly only  │     │ Informal savings    │
│ Weekly settlement   │ ✗── │ Static risk forms    │ ──✗ │ Chit funds          │
│ Has earnings data   │     │ 15–45 day claims     │     │ Moneylenders        │
│ No disruption cover │     │ Excludes gig workers │     │ Absorbs full loss   │
└─────────────────────┘     └─────────────────────┘     └─────────────────────┘
          │                           │                           │
          └───────────────────────────┴───────────────────────────┘
                     No communication during a disruption event
```

**During a heavy rain event:**
- Platform: order volume drops, no action for workers
- Insurer: unaware the disruption even occurred
- Worker: loses ₹400–900, borrows from moneylender at 2–5%/month

### Risk Factor Blindspot

| Traditional Insurer Tracks | What Actually Drives Gig Risk |
|---------------------------|-------------------------------|
| City-average rainfall (annual) | Pincode waterlog history (12-week rolling) |
| State flood claim rate (2–3 yr old) | Live IMD rain forecast for active hours |
| Broad occupation category | Platform order density in delivery radius |
| Self-declared income (unverified) | Actual platform earnings (verified via API) |
| Binary claim history (yes/no) | Frequency, zone, and event-type pattern |

---

## 3. Our Solution — GigShield

**GigShield** is an AI-enabled parametric income insurance platform built exclusively for food delivery partners. It combines real-time environmental data, verified platform earnings, and machine learning to offer **automated weekly coverage** with **zero-touch payouts** — directly to the worker's UPI handle within 90 seconds of a verified disruption.

### What Makes It Parametric

Traditional insurance asks: *"Did you suffer a loss? Prove it."*
Parametric insurance asks: *"Did a pre-agreed external event occur? We already know — here's your money."*

GigShield monitors 5 external data signals continuously. When a signal crosses a verified threshold **and** the worker has an active policy **and** the fraud check passes — the payout is processed automatically. No form. No surveyor. No waiting.

---

## 4. Persona & User Scenarios

### Chosen Persona: Food Delivery Partner (Zomato/Swiggy), Chennai

**Profile:**
- Works 8–10 hours/day, 6 days/week
- Average earnings: ₹800–1,200/day (₹5,600–8,400/week)
- Operates primarily on a two-wheeler (bike/scooter)
- Payment: weekly settlement from platform to UPI
- Financial safety net: near zero — most rely on daily earnings for that day's needs

### Scenario 1 — Heavy Monsoon Rain (Trigger: T1)

> Rajan, a Swiggy partner in Velachery, wakes up to 58mm of rain forecast. By 11am his zone goes silent — no orders, flooded roads, dangerous conditions. Under the old system: he loses ₹700 and borrows from his cousin. Under GigShield: the weather trigger fires at 11:20am, fraud guard confirms his GPS is in the zone, and ₹350 lands in his UPI account by 11:22am. He knows exactly what his week's safety net looks like.

### Scenario 2 — Sudden Curfew/Section 144 (Trigger: T4)

> Priya, a Zomato partner in T. Nagar, is mid-shift when local authorities issue movement restrictions due to a political event. Her platform app goes dark for 4 hours. GigShield's news NLP pipeline detects the gazette notification within 12 minutes, cross-references her active zone, confirms her platform inactivity, and processes ₹450 to her account — before she even realises what triggered it.

### Scenario 3 — Severe AQI Alert (Trigger: T3)

> During Diwali week, AQI in Chennai crosses 420 (Severe) for 7 continuous hours. Health advisories recommend no outdoor activity. Karthik, who works 7am–5pm, cannot safely operate. GigShield detects the AQI threshold breach, verifies it persists beyond the 6-hour minimum, and pays out ₹300. The premium he paid that week was ₹52 — a 5.8x return on a genuine disruption.

### Scenario 4 — Platform App Outage (Trigger: T5 — Our Unique Differentiator)

> Swiggy's order routing system experiences an API failure between 6pm–9pm (peak dinner hours). Order acceptance rates drop 74% across South Chennai. This is not weather. This is not a curfew. No existing insurance product covers this. GigShield's platform health monitor detects the anomaly, confirms the zone-wide depression (not individual rider behaviour), and processes ₹250 to every active policyholder in the affected zone.

---

## 5. Innovation Differentiators

GigShield is built to stand apart from other teams working on the same problem statement. Here are our specific innovations:

### 5.1 Platform Outage as an Insurable Event

No other parametric insurance product in India or globally covers app-side platform failures as an income trigger. We monitor order acceptance rates across zones using a statistical anomaly detection model. A zone-wide drop of >70% for >2 hours — when weather and social triggers are absent — is classified as a platform disruption event and triggers a payout. This is an entirely new category of parametric insurance.

### 5.2 The Zone-Learning Feedback Loop

Every week, our risk model re-trains on the prior 12 weeks of zone × event × claim data. Zones that historically see disruptions but workers never claim (because they found workarounds, or the threshold was slightly off) get recalibrated. Zones with unexpectedly high claim rates are flagged for threshold review. The model gets smarter every week — not just about weather, but about how weather affects *this pincode's delivery workers specifically*.

### 5.3 GigScore — The Worker's Resilience Score

Inspired by credit scores but built for the gig economy, GigScore (0–100) measures a worker's disruption resilience and responsible policy usage. Factors:
- Weeks continuously covered (continuity bonus)
- Claim-to-disruption ratio (are you claiming only when genuinely disrupted?)
- Zone risk level vs. premium paid
- Platform activity consistency

A high GigScore earns premium discounts (up to 30%), early access to new trigger types, and fast-track payouts. This reduces churn, incentivises responsible usage, and creates a loyalty loop that no traditional insurer offers gig workers.

### 5.4 Hyper-Local Pincode Risk Scoring vs. City-Level

Traditional insurers use city-level aggregates. We score at the pincode cluster level (5-6 pincodes per cluster based on geographic and delivery-zone similarity). Velachery (flood-prone, low-lying) and Adyar (partially coastal) carry different risk scores than Perungudi (elevated, well-drained). Workers in safer zones pay less — accurately. This is underwriting precision no existing product offers for this segment.

### 5.5 Dual Dashboard — Worker View + Insurer View

Most hackathon solutions build only the worker interface. GigShield includes a full insurer/admin analytics dashboard showing:
- Live loss ratios by zone and trigger type
- Next-week predicted disruption probability (ML forecast)
- Fraud alert queue with anomaly scores
- Premium adequacy analysis (are we pricing zones correctly?)

This makes GigShield immediately pitch-able to actual insurers as a B2B2C platform — not just a consumer app.

---

## 6. Weekly Premium Model

### Why Weekly

Gig workers operate week-to-week. Their income lands weekly. Their expenses are weekly. An annual or even monthly premium requires upfront cash they often don't have. By aligning the premium debit to the weekly settlement, coverage becomes frictionless — the ₹49–65 deduction happens automatically from the Zomato/Swiggy payout, never from the worker's pocket.

### Premium Formula

```
Weekly Premium = Base Rate × Zone Risk Factor × Seasonal Multiplier × GigScore Discount

Where:
  Base Rate          = ₹49 (covers up to ₹1,500 income protection per week)
  Zone Risk Factor   = 0.80 – 1.40  (pincode cluster flood/disruption history)
  Seasonal Multiplier= 1.00 – 1.30  (monsoon Jun–Sep gets 1.20–1.30x)
  GigScore Discount  = 0.70 – 1.00  (high GigScore = up to 30% off)
```

### Premium Range Examples

| Pincode | Zone Type | Season | GigScore | Weekly Premium |
|---------|-----------|--------|----------|----------------|
| Velachery (600042) | High flood risk | Monsoon | 60 (avg) | ₹71 |
| Perungudi (600096) | Low flood risk | Monsoon | 60 (avg) | ₹52 |
| T. Nagar (600017) | Medium curfew risk | Dry | 85 (high) | ₹39 |
| Anna Nagar (600040) | Low risk | Dry | 72 (avg) | ₹41 |

### Coverage Tiers

| Tier | Weekly Premium | Max Weekly Payout | Target Worker |
|------|---------------|-------------------|---------------|
| Basic | ₹29 | ₹700 | Part-time, <5 hrs/day |
| Standard | ₹49 | ₹1,500 | Full-time, 8 hrs/day |
| Premium | ₹79 | ₹2,500 | High-earner, 10+ hrs/day |

Workers select their tier based on their typical weekly earnings. The platform API verifies that the chosen tier is consistent with their actual 4-week average earnings.

### Premium Deduction Flow

```
Sunday 11:59pm — Platform calculates weekly earnings
Monday 12:00am — GigShield API receives earnings webhook
Monday 12:01am — AI recalculates premium for coming week
Monday 12:02am — Premium deducted from settlement before payout
Monday 12:03am — New weekly policy activated
Monday 12:04am — Worker notified via app + SMS
```

---

## 7. Parametric Triggers

GigShield monitors 5 independent data signals. Any single trigger, if threshold is met and fraud check passes, initiates an automatic payout.

### Trigger Definitions

```
┌────┬──────────────────┬────────────────────────────────────────┬──────────────────────┬──────────────┐
│ ID │ Trigger Name     │ Threshold Condition                    │ Data Source          │ Max Payout   │
├────┼──────────────────┼────────────────────────────────────────┼──────────────────────┼──────────────┤
│ T1 │ Heavy Rain       │ Rainfall > 35mm/hr for ≥ 2 continuous  │ OpenWeatherMap API   │ ₹350 / day   │
│    │                  │ hours in worker's active zone          │ + IMD radar (mock)   │              │
├────┼──────────────────┼────────────────────────────────────────┼──────────────────────┼──────────────┤
│ T2 │ Urban Flood      │ Flood Level 2+ NDMA alert for worker's │ NDMA Flood Alert API │ ₹500 / day   │
│    │                  │ pincode cluster for ≥ 4 hours          │ (mock/scraper)       │              │
├────┼──────────────────┼────────────────────────────────────────┼──────────────────────┼──────────────┤
│ T3 │ Severe AQI       │ AQI > 400 (Severe category) sustained  │ CPCB AQI Live Feed   │ ₹300 / day   │
│    │                  │ for ≥ 6 hours in city boundary         │ (official API)       │              │
├────┼──────────────────┼────────────────────────────────────────┼──────────────────────┼──────────────┤
│ T4 │ Curfew / Section │ Delivery restriction order confirmed   │ Govt gazette API +   │ ₹450 / day   │
│    │ 144 / Strike     │ in worker's zone for ≥ 3 hours         │ News NLP pipeline    │              │
├────┼──────────────────┼────────────────────────────────────────┼──────────────────────┼──────────────┤
│ T5 │ Platform Outage  │ Zone-wide order acceptance rate drops  │ Platform webhook +   │ ₹250 / day   │
│    │ (UNIQUE)         │ > 70% vs. same-hour 4-week avg for     │ Isolation Forest     │              │
│    │                  │ ≥ 2 hours (weather-absent condition)   │ anomaly model        │              │
└────┴──────────────────┴────────────────────────────────────────┴──────────────────────┴──────────────┘
```

### Payout Calculation

```
Daily Payout = min(Trigger Max Payout, Worker's Avg Hourly Earnings × Hours Disrupted)

Avg Hourly Earnings = Worker's 4-week rolling avg weekly income ÷ avg active hours/week

Example:
  Worker earns ₹6,000/week over 50 active hours → ₹120/hour
  T1 (Rain) disrupts 3 hours → 3 × ₹120 = ₹360 → capped at T1 max = ₹350
```

Multiple triggers can fire in a single day. They do not stack beyond the worker's actual average daily earnings, preventing over-insurance.

---

## 8. System Architecture

### High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        EXTERNAL DATA LAYER                               │
│  OpenWeatherMap  │  NDMA Flood API  │  CPCB AQI  │  Platform Webhooks  │
│  IMD Radar Mock  │  Govt Gazette    │  News NLP  │  Traffic Mock API   │
└──────────┬───────────────┬──────────────────┬───────────────┬──────────┘
           │               │                  │               │
           ▼               ▼                  ▼               ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                      AI ENGINE (Python / FastAPI)                        │
│                                                                          │
│  ┌─────────────────┐  ┌──────────────────┐  ┌────────────────────────┐ │
│  │ Risk Scoring    │  │ Disruption       │  │ Fraud Guard            │ │
│  │ Model           │  │ Detector         │  │                        │ │
│  │                 │  │                  │  │ Isolation Forest       │ │
│  │ GBT Regressor   │  │ 5 trigger        │  │ GPS cross-check        │ │
│  │ Zone × weather  │  │ monitors         │  │ Duplicate detection    │ │
│  │ × history       │  │ Real-time eval   │  │ Anomaly scoring        │ │
│  └────────┬────────┘  └────────┬─────────┘  └───────────┬────────────┘ │
│           │                    │                         │              │
│           └────────────────────┼─────────────────────────┘              │
│                                ▼                                         │
│                    ┌───────────────────────┐                            │
│                    │  Payout Orchestrator  │                            │
│                    │  Zero-touch · UPI     │                            │
│                    │  Razorpay sandbox     │                            │
│                    └───────────────────────┘                            │
└─────────────────────────────┬───────────────────────────────────────────┘
                              │
                ┌─────────────┴─────────────┐
                ▼                           ▼
┌───────────────────────┐     ┌──────────────────────────┐
│   Worker PWA          │     │   Admin Dashboard         │
│   (React, mobile)     │     │   (React, insurer view)  │
│                       │     │                           │
│  Onboard · Policy     │     │  Loss ratios · Forecasts  │
│  Claim status · Alerts│     │  Fraud queue · Analytics  │
└───────────────────────┘     └──────────────────────────┘
                │                           │
                └─────────────┬─────────────┘
                              ▼
             ┌────────────────────────────┐
             │  FastAPI Backend           │
             │  Python 3.12 · REST +      │
             │  WebSocket                 │
             └──────────┬─────────────────┘
                        │
           ┌────────────┼────────────┐
           ▼            ▼            ▼
     ┌──────────┐ ┌──────────┐ ┌──────────┐
     │PostgreSQL│ │  Redis   │ │ Celery   │
     │Policies  │ │Event cache│ │Async tasks│
     │Claims    │ │Rate limit │ │Trigger   │
     │Workers   │ │Sessions  │ │monitoring│
     └──────────┘ └──────────┘ └──────────┘
```

### Component Responsibilities

| Component | Role | Technology |
|-----------|------|------------|
| Trigger Monitor | Polls/receives external APIs every 5 min, evaluates thresholds | Celery Beat + Python |
| Risk Engine | Weekly premium calculation via ML model | scikit-learn GBT |
| Fraud Guard | Anomaly scoring on every auto-triggered claim | Isolation Forest |
| Payout Orchestrator | Manages claim → approval → payment pipeline | FastAPI + Razorpay |
| Worker App | Onboarding, policy view, claim status, GigScore | React PWA |
| Admin Dashboard | Insurer analytics, loss ratios, fraud alerts | React + Chart.js |
| Backend API | REST endpoints + WebSocket for real-time alerts | FastAPI (Python) |
| Database | Persistent storage for all entities | PostgreSQL 16 |
| Cache / Queue | Event queue, session cache, rate limiting | Redis 7 |
| Task Queue | Async jobs: trigger eval, payouts, notifications | Celery 5 |

---

## 9. AI/ML Integration

### 9.1 Weekly Premium Risk Model

**Algorithm:** Gradient Boosted Regressor (scikit-learn `GradientBoostingRegressor`)

**Training Data (synthetic + historical proxy for demo):**
- 12 weeks of historical weather data per pincode cluster (Chennai zones)
- Historical disruption frequency by zone and month
- Simulated claim rates by trigger type and zone

**Input Features:**

```python
features = {
    # Worker-level
    'weeks_on_platform': int,           # Platform tenure
    'avg_weekly_active_hours': float,   # Rolling 4-week average
    'zone_pincode_cluster': int,        # Encoded cluster ID
    'coverage_tier': int,               # 1=Basic, 2=Standard, 3=Premium
    'gigascore': float,                 # 0–100
    'claim_count_12w': int,             # Claims in last 12 weeks
    'claim_to_disruption_ratio': float, # Personal fraud signal

    # Zone-level (refreshed weekly)
    'zone_flood_risk_score': float,     # 0–1, from historical data
    'zone_avg_disruption_days_12w': float,
    'zone_order_density_index': float,  # How busy this zone is

    # Temporal
    'is_monsoon_season': bool,          # Jun–Sep
    'month_of_year': int,               # Seasonality
    'week_forecast_rain_mm': float,     # Next 7-day forecast
    'week_forecast_aqi_avg': float,
}
```

**Output:** `predicted_weekly_premium` (₹, float)

**Retraining Schedule:** Every Sunday at 11pm, before Monday morning policy renewals.

**Model Accuracy Target:** MAE < ₹8 on premium prediction (cross-validated on held-out zones).

### 9.2 Disruption Trigger Monitor

```python
# Pseudocode for the Celery Beat trigger evaluation task
@celery.task
def evaluate_triggers():
    active_workers = Worker.get_active_policyholders()
    
    for worker in active_workers:
        zone = worker.zone_cluster
        
        # T1: Heavy Rain
        rain_data = weather_api.get_hourly(zone.lat, zone.lon)
        if rain_data.mm_per_hr > 35 and rain_data.consecutive_hours >= 2:
            trigger_claim(worker, trigger='T1', hours=rain_data.consecutive_hours)
        
        # T2: Flood Alert
        flood_alert = ndma_api.get_alert(zone.pincode_cluster)
        if flood_alert.level >= 2 and flood_alert.duration_hrs >= 4:
            trigger_claim(worker, trigger='T2', hours=flood_alert.duration_hrs)
        
        # T3: AQI
        aqi = cpcb_api.get_aqi(zone.city)
        if aqi.value > 400 and aqi.sustained_hours >= 6:
            trigger_claim(worker, trigger='T3', hours=aqi.sustained_hours)
        
        # T4: Curfew / Social
        social = social_monitor.check(zone)
        if social.restriction_active and social.confirmed_hours >= 3:
            trigger_claim(worker, trigger='T4', hours=social.confirmed_hours)
        
        # T5: Platform Outage (unique)
        platform_health = platform_api.get_zone_health(zone)
        if platform_health.order_acceptance_drop_pct > 70 and \
           platform_health.duration_hrs >= 2 and \
           not weather_api.is_weather_event_active(zone):  # exclude T1/T2 overlap
            trigger_claim(worker, trigger='T5', hours=platform_health.duration_hrs)
```

### 9.3 News NLP Pipeline (Curfew Trigger)

For the T4 trigger, GigShield uses a spaCy NLP pipeline to classify government notifications and news alerts:

```
Raw text (gazette / news headline)
         │
         ▼
spaCy NER → Extract: Location, Event Type, Duration
         │
         ▼
Classifier → Categories: [CURFEW, STRIKE, BANDH, SECTION_144, PROTEST_CLOSURE, IRRELEVANT]
         │
         ▼
Location matcher → Does extracted location overlap with any active worker zone?
         │
         ▼
Confidence threshold (> 0.85) → Trigger T4 evaluation
```

Training data: 2,000 manually labelled Indian govt notifications and news headlines (Tamil Nadu + national events).

---

## 10. Fraud Detection Engine

Fraud in parametric insurance takes specific forms for gig workers. GigShield's Fraud Guard addresses each:

### 10.1 Fraud Attack Vectors & Countermeasures

| Attack Type | How It Works | GigShield Counter |
|------------|--------------|-------------------|
| GPS Spoofing | Worker fakes location to appear in disrupted zone | Cross-check GPS with last 6 platform delivery locations; flag >2km discrepancy |
| Policy Front-Running | Worker buys policy after hearing about incoming storm | 6-hour lockout between policy activation and first eligible claim |
| Claim Duplication | Same event filed multiple times or across multiple accounts | Event ID deduplication; device fingerprint + Aadhaar hash matching |
| Coordinated Fraud | Group of workers in same zone files simultaneously without platform inactivity evidence | Zone-level claim rate vs. platform activity correlation check |
| Manufactured Outage | Worker goes offline voluntarily, claims platform outage | T5 requires zone-wide signal, not individual inactivity |
| Threshold Gaming | Worker moves to high-risk zone temporarily | Zone assignment uses 4-week historical GPS centroid, not real-time location |

### 10.2 Isolation Forest Implementation

```python
from sklearn.ensemble import IsolationForest
import numpy as np

class FraudGuard:
    def __init__(self):
        self.model = IsolationForest(
            contamination=0.05,   # expect 5% anomalous claims
            n_estimators=200,
            random_state=42
        )
    
    def score_claim(self, claim) -> dict:
        features = np.array([[
            claim.gps_distance_from_zone_centroid_km,
            claim.hours_since_policy_activation,
            claim.worker_claim_frequency_12w,
            claim.zone_claim_rate_vs_baseline,
            claim.platform_activity_drop_pct,
            claim.time_since_last_delivery_hrs,
            claim.device_seen_before_bool,
            claim.trigger_matches_zone_history_bool,
        ]])
        
        score = self.model.decision_function(features)[0]
        # Score: positive = normal, negative = anomalous
        # Normalise to 0–1 where 1 = fully legitimate
        normalised = (score + 0.5) / 1.0
        
        if normalised >= 0.75:
            return {'decision': 'AUTO_APPROVE', 'score': normalised}
        elif normalised >= 0.50:
            return {'decision': 'SOFT_REVIEW', 'score': normalised}
        else:
            return {'decision': 'BLOCK_FLAG', 'score': normalised}
```

### 10.3 Fraud Scoring Thresholds

```
Score 0.75 – 1.00  →  AUTO APPROVE  →  Payout processed immediately
Score 0.50 – 0.74  →  SOFT REVIEW   →  Queued for admin review (24h window)
Score 0.00 – 0.49  →  BLOCK + FLAG  →  Payment blocked, anomaly logged
```

---

## 11. Zero-Touch Claims & Payout Flow

### End-to-End Flow

```
[DISRUPTION EVENT DETECTED]
           │
           ▼ (< 5 min)
[Trigger threshold verified by AI engine]
           │
           ▼ (< 10 sec)
[Worker active policy confirmed]
  - Policy active this week?
  - 6-hour lockout from activation passed?
  - Worker in affected zone?
           │
           ▼ (< 15 sec)
[Fraud Guard score computed]
  - GPS cross-check
  - Duplicate event ID check
  - Isolation Forest score
           │
      ┌────┴────┐
      │         │
   ≥ 0.75    < 0.50
      │         │
      ▼         ▼
[AUTO        [BLOCK +
 APPROVE]     FLAG]
      │
      ▼ (< 30 sec)
[Payout calculation]
  min(trigger_max, hours_lost × avg_hourly_rate)
      │
      ▼ (< 60 sec)
[Razorpay API / UPI transfer initiated]
      │
      ▼ (< 90 sec total)
[Worker notified: SMS + FCM push]
  "₹350 credited to your UPI. Claim #GS-2026-0441"
      │
      ▼
[Event logged to PostgreSQL]
[Admin dashboard updated in real-time via WebSocket]
```

### Payout Channels

| Channel | Use Case | Settlement Time |
|---------|----------|----------------|
| UPI (primary) | All workers with registered UPI handle | < 30 seconds |
| IMPS | Fallback for non-UPI workers | < 2 minutes |
| Razorpay Wallet | For workers without bank linked | Instant |

---

## 12. Tech Stack

### Backend

| Layer | Technology | Reason |
|-------|------------|--------|
| Language | Python 3.12 | AI/ML ecosystem, team expertise |
| Web Framework | FastAPI | Async support, auto OpenAPI docs, high performance |
| Task Queue | Celery 5 + Redis | Async trigger monitoring, scheduled weekly jobs |
| ORM | SQLAlchemy 2.0 | Type-safe models, async query support |
| Database | PostgreSQL 16 | ACID compliance, JSON support for event payloads |
| Cache / Broker | Redis 7 | Celery broker, session cache, rate limiting |
| Validation | Pydantic v2 | FastAPI-native, strict data validation |
| Auth | JWT + OAuth2 | Stateless auth, platform OAuth integration |

### AI / ML

| Component | Technology | Reason |
|-----------|------------|--------|
| Premium Model | scikit-learn GBT | Interpretable, fast inference, weekly retraining |
| Fraud Detection | scikit-learn Isolation Forest | Unsupervised, handles concept drift, no labelled fraud data needed at start |
| News NLP (T4) | spaCy 3 + custom NER | Lightweight, deployable on-device, good Hindi/Tamil support |
| Data Processing | pandas + NumPy | Standard pipeline for feature engineering |
| Model Persistence | joblib | Lightweight model serialisation for FastAPI loading |
| Experiment Tracking | MLflow (local) | Track retraining runs, compare model versions |

### Frontend

| Layer | Technology | Reason |
|-------|------------|--------|
| Framework | React 18 + TypeScript | Component reuse across worker and admin apps |
| PWA | Vite + Workbox | Offline support, installable without app store |
| State Management | Zustand | Lightweight, no boilerplate |
| Charts (Admin) | Chart.js + react-chartjs-2 | Loss ratio charts, disruption forecasts |
| UI Components | Tailwind CSS + shadcn/ui | Fast, accessible, mobile-first |
| Real-time | WebSocket (native) | Live admin dashboard updates |
| Maps | Leaflet.js | Zone visualisation, no paid API needed |
| Notifications | Firebase Cloud Messaging | Push notifications to worker PWA |

### Infrastructure & DevOps

| Component | Technology | Reason |
|-----------|------------|--------|
| Containerisation | Docker + Docker Compose | Single-command local setup |
| Deployment | Railway / Render (free tier) | Hackathon-friendly, supports PostgreSQL + Redis |
| Reverse Proxy | Nginx | Static files + API proxy |
| Environment | python-dotenv | Config management |
| Testing | pytest + httpx | FastAPI async test client |
| API Docs | Swagger UI (auto via FastAPI) | Built-in, zero config |

### External APIs

| API | Purpose | Access |
|-----|---------|--------|
| OpenWeatherMap | Rain/weather data (T1) | Free tier (1000 calls/day) |
| CPCB AQI API | Air quality data (T3) | Public / mock |
| NDMA Flood Alerts | Flood level alerts (T2) | Mock + scraper |
| NewsAPI / Inshorts | Curfew/social events (T4) | Free tier + NLP |
| Razorpay | Payment sandbox (payouts) | Test mode (no real money) |
| Firebase | Push notifications | Free tier (Spark plan) |

### Repository Structure

```
gigshield/
├── backend/
│   ├── app/
│   │   ├── main.py              # FastAPI app entry point
│   │   ├── api/
│   │   │   ├── workers.py       # Worker registration, profile
│   │   │   ├── policies.py      # Policy creation, renewal
│   │   │   ├── claims.py        # Claim management
│   │   │   ├── payouts.py       # Payout processing
│   │   │   └── admin.py         # Admin dashboard endpoints
│   │   ├── models/
│   │   │   ├── worker.py        # SQLAlchemy Worker model
│   │   │   ├── policy.py        # Policy, WeeklyPolicy models
│   │   │   ├── claim.py         # Claim, Event models
│   │   │   └── zone.py          # ZoneCluster, RiskScore models
│   │   ├── services/
│   │   │   ├── risk_engine.py   # Premium calculation service
│   │   │   ├── fraud_guard.py   # Isolation Forest service
│   │   │   ├── trigger_monitor.py # Parametric trigger evaluation
│   │   │   ├── payout_service.py  # Razorpay integration
│   │   │   └── nlp_pipeline.py  # spaCy curfew detection
│   │   ├── ml/
│   │   │   ├── premium_model.py # GBT model training + inference
│   │   │   ├── fraud_model.py   # Isolation Forest training
│   │   │   ├── train.py         # Weekly retraining script
│   │   │   └── models/          # Saved .joblib model files
│   │   └── tasks/
│   │       ├── celery_app.py    # Celery configuration
│   │       ├── trigger_tasks.py # Scheduled trigger monitoring
│   │       └── retrain_tasks.py # Weekly model retraining
│   ├── tests/
│   ├── Dockerfile
│   └── requirements.txt
├── frontend/
│   ├── worker-app/              # Worker PWA (React)
│   └── admin-dashboard/         # Insurer dashboard (React)
├── docker-compose.yml
├── nginx.conf
└── README.md
```

---

## 13. Platform Choice — Web PWA

We chose a **Progressive Web App (PWA)** over a native mobile app for the following reasons:

1. **No App Store barrier:** Food delivery workers are already managing Zomato/Swiggy apps. Adding another native app to install creates friction. A PWA is accessible via a link, installable from the browser, and works offline.

2. **Device range:** Delivery workers use low-to-mid range Android phones (₹6,000–₹15,000 range). A lightweight PWA performs better than a React Native app on constrained hardware.

3. **Single codebase:** One React codebase serves both the worker-facing PWA and the admin/insurer dashboard.

4. **SMS fallback:** For workers without smartphones or in low-connectivity zones, all critical notifications (claim triggered, payout sent) are duplicated via SMS using Twilio/MSG91.

---

## 14. Data Models

### Core Entities

```python
# Worker
class Worker(Base):
    id: UUID
    phone: str                    # Primary identifier (UPI linked)
    name: str
    aadhaar_hash: str             # Hashed for fraud dedup, not stored raw
    platform: Enum['zomato', 'swiggy', 'zepto']
    zone_cluster_id: int          # FK to ZoneCluster
    upi_handle: str
    gigascore: float              # 0–100
    created_at: datetime
    is_active: bool

# Weekly Policy
class WeeklyPolicy(Base):
    id: UUID
    worker_id: UUID               # FK to Worker
    week_start: date              # Monday
    week_end: date                # Sunday
    coverage_tier: Enum[1, 2, 3]
    premium_charged: Decimal      # Actual ₹ deducted
    max_payout: Decimal           # Tier-based ceiling
    is_active: bool
    activated_at: datetime

# Claim / Payout
class Claim(Base):
    id: UUID
    policy_id: UUID               # FK to WeeklyPolicy
    worker_id: UUID
    trigger_type: Enum['T1','T2','T3','T4','T5']
    event_id: str                 # External event fingerprint (dedup key)
    hours_disrupted: float
    calculated_payout: Decimal
    fraud_score: float
    fraud_decision: Enum['AUTO_APPROVE','SOFT_REVIEW','BLOCK_FLAG']
    payout_status: Enum['pending','processing','paid','blocked']
    razorpay_transfer_id: str
    created_at: datetime
    paid_at: datetime

# Zone Cluster
class ZoneCluster(Base):
    id: int
    name: str                     # e.g., "South Chennai - Velachery"
    pincodes: List[str]           # JSON array of pincodes
    flood_risk_score: float       # 0–1, updated weekly
    disruption_freq_12w: float    # Avg disruption days per week
    lat_centroid: float
    lon_centroid: float
```

---

## 15. API Design

### Key Endpoints

```
Worker & Onboarding
  POST   /api/v1/workers/register        Register new worker
  POST   /api/v1/workers/verify-platform  Verify Zomato/Swiggy account
  GET    /api/v1/workers/{id}/profile     Get worker profile + GigScore
  GET    /api/v1/workers/{id}/earnings    Get rolling earnings from platform

Policy Management
  POST   /api/v1/policies/quote           Get weekly premium quote
  POST   /api/v1/policies/activate        Activate weekly policy
  GET    /api/v1/policies/{id}            Get policy details
  GET    /api/v1/policies/active          Get worker's current active policy

Claims
  GET    /api/v1/claims/{worker_id}       Get all claims for worker
  GET    /api/v1/claims/{id}/status       Real-time claim status
  POST   /api/v1/claims/manual            Manual claim (edge cases only)

Triggers (internal / webhooks)
  POST   /api/v1/triggers/weather-event   Weather API webhook receiver
  POST   /api/v1/triggers/platform-health Platform health signal
  GET    /api/v1/triggers/active          Currently active triggers by zone

Admin
  GET    /api/v1/admin/dashboard          Loss ratios, payout totals
  GET    /api/v1/admin/fraud-queue        Claims in SOFT_REVIEW
  GET    /api/v1/admin/zone-risk          Risk scores by zone
  GET    /api/v1/admin/forecast           Next-week disruption prediction
  POST   /api/v1/admin/simulate-trigger   Simulate a disruption (demo mode)

WebSocket
  WS     /ws/admin/live                   Real-time event stream for admin
  WS     /ws/worker/{id}/alerts           Real-time payout alerts for worker
```

---

## 16. Development Roadmap (6 Weeks)

### Phase 1: Ideation & Foundation (Weeks 1–2) — Due March 20

**Goal:** Core architecture, onboarding flow, and basic API skeleton.

- [ ] Repository setup with Docker Compose (FastAPI + PostgreSQL + Redis)
- [ ] Worker registration and platform OAuth mock
- [ ] Zone cluster data for Chennai (12 clusters, seeded)
- [ ] Basic premium calculator (rule-based, before ML model)
- [ ] Figma wireframes for worker PWA onboarding
- [ ] README (this document) published to GitHub
- [ ] 2-minute video: strategy walkthrough + Figma prototype demo

**Deliverables:** GitHub repo with README.md + 2-min video

---

### Phase 2: Automation & Protection (Weeks 3–4) — Due April 4

**Goal:** Working parametric engine, ML premium model, full claims flow.

- [ ] ML premium model trained on synthetic Chennai data (scikit-learn GBT)
- [ ] Celery Beat trigger monitor (all 5 triggers, API + mock sources)
- [ ] Fraud Guard Isolation Forest (v1, basic feature set)
- [ ] Full claims API: creation → fraud check → payout decision
- [ ] Razorpay sandbox integration for payout simulation
- [ ] Worker PWA: onboarding, policy view, claim status screens
- [ ] Admin dashboard: basic loss ratio chart, live event log
- [ ] 2-minute demo video: live trigger → auto-claim → payout

**Key Tips Applied:**
- 3 live triggers (T1 weather, T3 AQI, T5 platform outage) with real API calls
- ML premium adjusted by zone + season from day 1
- Zero-touch UX: worker never touches a claim form

---

### Phase 3: Scale & Optimise (Weeks 5–6) — Due April 17

**Goal:** Advanced fraud, dual dashboards, final demo package.

- [ ] Isolation Forest v2 with GPS spoofing and coordinated fraud detection
- [ ] GigScore algorithm implemented and visible in worker app
- [ ] Zone-learning feedback loop (weekly model retraining pipeline)
- [ ] spaCy NLP pipeline for T4 curfew detection
- [ ] Worker dashboard: earnings protected widget, weekly coverage timeline
- [ ] Admin dashboard: predictive disruption forecast, fraud alert queue, zone risk heatmap
- [ ] End-to-end demo simulation: trigger fake rainstorm → auto claim → UPI payout
- [ ] 5-minute demo video (screen recording of full platform)
- [ ] Final pitch deck (PDF): persona, AI architecture, business model

---

## 17. Business Viability

### Unit Economics (Standard Tier, Chennai)

```
Premium revenue per worker per week:   ₹49 – ₹71 (avg ₹55)
Expected claim payout per worker/week: ₹18 – ₹35 (avg ₹25)
  (Based on ~0.8 disruption days/worker/week avg in Chennai)

Gross margin per worker per week:      ₹55 – ₹25 = ₹30
Less: API costs + compute per worker:  ~₹2
Less: Payment processing (Razorpay):   ~₹1.5
Net contribution per worker per week:  ~₹26.50

At 10,000 active workers:
  Weekly revenue:     ₹5,50,000
  Weekly payouts:     ₹2,50,000
  Weekly net:         ₹2,65,000 (~₹1.3Cr/year)
```

### Distribution Model

GigShield operates as a **B2B2C platform**. The insurer (e.g., Bajaj Allianz, New India Assurance, or a digital-first player like Digit) provides the regulatory wrapper (IRDAI licence). GigShield provides the technology layer: risk scoring, trigger monitoring, fraud detection, and payout processing. Revenue is split via a technology service fee.

Alternatively, GigShield can integrate directly with Zomato/Swiggy as a platform benefit — workers opt-in at registration, and the premium is deducted automatically from their weekly settlement. This eliminates distribution cost entirely.

### Regulatory Compliance

All insurance products are structured as **index-based parametric coverage** under IRDAI's Sandbox regulations (IRDAI Regulatory Sandbox 2019), which permit innovative product testing without full regulatory approval. The 6-week hackathon demo operates under this sandbox intent. The product explicitly excludes health, life, accident, and vehicle repair coverage — remaining squarely within the parametric income protection category.

---

## 18. Team

| Name | Role |
|------|------|
| [Member 1] | Backend Engineer — FastAPI, AI/ML |
| [Member 2] | Frontend Engineer — React PWA |
| [Member 3] | Data / ML Engineer — Risk models |
| [Member 4] | Product / UX — Figma, user research |

**Repository:** https://github.com/[team]/gigshield
**Demo Video (Phase 1):** [Link to be added]

---

*GigShield — Protect the people who deliver India's digital economy.*