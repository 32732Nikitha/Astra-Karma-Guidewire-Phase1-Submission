# Astra-Karma-Guidewire-Phase1-Submission
**BHIMA ASTRA**

**AI-Powered Parametric Insurance for Gig Delivery Workers**

Guidewire DEVTrails 2026 \| Phase 1 Submission

**Table of Contents**

  -----------------------------------------------------------------------
  **\#**    **Section Title**
  --------- -------------------------------------------------------------
  **1**     [Introduction and Problem Understanding](#sec1)

  **2**     [Our Solution Overview](#sec2)

  **3**     [Why This Model: Design Decisions](#sec3)

  **4**     [End to End System Flow](#sec4)

  **5**     [Parametric Trigger System](#sec5)

  **6**     [AI and Machine Learning Architecture](#sec6)

  **7**     [Adversarial Defense and Anti-Spoofing Strategy](#sec7)

  **8**     [Multi-Agent System Design](#sec8)

  **9**     [Financial Model](#sec9)

  **10**    [Stakeholder Benefits](#sec10)

  **11**    [Advantages of Our Model](#sec11)

  **12**    [Limitations and Future Improvements](#sec12)

  **13**    [Technology Stack](#sec13)

  **14**    [Final Conclusion](#sec14)
  -----------------------------------------------------------------------

[]{#sec1 .anchor}**1. Introduction and Problem Understanding**

Gig delivery workers earn on a per-order basis, making their income
highly volatile and directly dependent on external conditions such as
weather, pollution, and platform availability. Despite this
vulnerability, they lack access to structured income protection, as
traditional insurance models are incompatible with their daily earning
cycles.

BHIMA ASTRA introduces an AI-driven parametric insurance model that uses
real-time environmental and operational data to detect disruption events
and automatically trigger predefined payouts. Instead of claim-based
assessment, the system relies on objective thresholds such as rainfall
intensity, temperature, and air quality levels.

By combining predictive risk modeling with automated payout execution,
the solution delivers immediate financial support during income
disruptions. Designed with weekly premiums and fixed payout structures,
it ensures affordability, transparency, and operational scalability for
gig workers.

**The Problem at Scale**

  -------------------------------------------------------------------------
  **Metric**                **Figure**          **Significance**
  ------------------------- ------------------- ---------------------------
  Gig workers in India by   23.5 Million        Rapidly growing unprotected
  2030                                          workforce \[1\]\[2\]

  Q-commerce India market   Rs. 64,000 Crore    Platform economy scale
  size (2025-26)                                \[3\]\[4\]

  Gig workers with zero     90%                 Extreme financial
  savings today                                 vulnerability \[5\]

  Monthly income lost       20-30%              Directly insurable risk
  during disruptions                            \[6\]\[7\]

  Delivery partners on      3 Million+          Target addressable market
  Blinkit/Zepto/Instamart                       \[8\]

  Structured income         None                The gap BHIMA ASTRA fills
  protection available                          
  -------------------------------------------------------------------------

These six data points define the gap this system fills: millions of
workers, zero protection, and a measurable and insurable risk.
\[1\]-\[8\]

[]{#sec2 .anchor}**2. Our Solution Overview**

**What the System Does**

BHIMA ASTRA is an AI-driven parametric income protection platform
designed exclusively for gig delivery workers operating across
Q-commerce platforms in India, including Swiggy Instamart, BigBasket
Now, Flipkart Minutes, Amazon Now, FreshToHome Express, Zepto, and
Blinkit \[1\]-\[7\]. It addresses one precisely defined problem: when
external disruptions such as extreme rainfall, heatwaves, severe air
pollution, floods, platform outages, or social disruptions such as
curfews and strikes prevent a worker from completing deliveries, the
worker loses income with no safety net.

The system detects those disruptions in real time, evaluates them
against predefined thresholds, and automatically transfers a fixed
payout to the worker with no claim submission, no adjuster, and no
delay.

The policy is structured on a weekly cycle, matching the income rhythm
of gig workers. Workers select from three plan tiers: Basic (Rs.
49/week), Standard (Rs. 79/week), or Premium (Rs. 119/week), each with
predefined payout levels and a maximum of two covered events per week.
Premiums are not uniform: the AI layer personalises each worker\'s
premium within their chosen plan based on their delivery zone, seasonal
disruption risk, historical event frequency, and delivery volume. The
worker owns their individual policy independently of which platform they
work on.

**Key Components**

  ------------------------------------------------------------------------
  **Component**          **Role in System**          **Section Reference**
  ---------------------- --------------------------- ---------------------
  Worker Registration    Captures platform, city,    Section 4 Step 1
  and Profile            zone, vehicle type, shift   
                         hours, experience           

  AI Risk Engine         Random Forest (income       Section 6
                         prediction) + XGBoost       
                         (disruption probability)    

  Weekly Premium         Converts expected loss into Section 6.3
  Generator              personalised weekly premium 
                         per plan tier               

  Real-Time Monitoring   Continuously ingests        Section 4 Step 5
  Layer                  weather, AQI, traffic, and  
                         platform status APIs        

  Parametric Trigger     Evaluates multi-level       Section 4 Step 7
  Engine                 thresholds (IMD/CPCB) and   
                         composite disruption score  

  Manager Intelligence   Human-verified detection of Section 8 D3
  Layer                  curfews, protests, and zone 
                         shutdowns                   

  Payout Execution       Automatically transfers     Section 4 Step 8
  Engine                 predefined payout when      
                         trigger fires               

  Fraud Detection Layer  GPS validation, anomaly     Section 9
                         detection, peer comparison, 
                         duplicate prevention        

  Analytics Dashboard    Worker earnings view plus   Section 10
                         insurer loss ratio and      
                         predictive analytics        
  ------------------------------------------------------------------------

**Platform and Coverage Scope**

The system covers income loss arising from five categories of external
disruption, each with predefined parametric thresholds:

  ------------------------------------------------------------------------
  **Disruption           **Trigger Standard**        **Payout Levels**
  Category**                                         
  ---------------------- --------------------------- ---------------------
  Heavy Rainfall         IMD: \>= 64.5 mm (L1), \>=  Rs. 300 / Rs. 600 /
                         115.6 mm (L2), \>= 204.5 mm Rs. 1,200
                         (L3)                        

  Extreme Heat /         IMD: \>= 40 deg C (L1), \>= Rs. 300 / Rs. 600
  Heatwave               45 deg C (L2)               

  Severe Air Pollution   CPCB AQI: \>= 300 (L1), \>= Rs. 300 / Rs. 500
                         400 (L2)                    

  Flood / Zone Shutdown  Flood alert flag or zone    Plan-level payout
                         shutdown flag = 1           

  Platform Outage /      Platform API outage flag or Plan-level payout
  Curfew                 manager-verified social     
                         disruption                  
  ------------------------------------------------------------------------

Coverage is strictly limited to income loss only. Health, life,
accident, and vehicle repair claims are explicitly excluded in all plan
tiers.

**Deployment Model**

The system operates as a standalone insurance platform. Delivery
platforms (Blinkit, Zepto, Swiggy Instamart, and others) act as
distribution partners, promoting the product within their worker-facing
apps and earning a 5-10% commission per active policy. This is a
bancassurance-style model that requires no insurance liability from the
platform. The worker owns their policy independently, meaning coverage
persists even if the worker switches platforms. The insurer manages the
risk pool, pricing engine, and payout execution directly.

[]{#sec3 .anchor}**3. Why This Model: Design Decisions**

The problem statement explicitly requires AI risk assessment, dynamic
weekly premiums, parametric triggers for weather and pollution, fraud
detection, and instant payouts. These are not differentiators. Every
competing team must deliver them. The five points below are design and
research decisions that go beyond what is required. These
differentiators are designed to improve real-world deployability, reduce
basis risk, and ensure scalability across heterogeneous gig ecosystems.

**Required vs. Differentiated Features**

  -----------------------------------------------------------------------
  **Required of ALL Teams**           **What We Do BEYOND Requirements**
  ----------------------------------- -----------------------------------
  AI-powered dynamic premium          D1: 7-platform cross-dataset AI
  calculation                         training \[1\]-\[7\]

  Parametric trigger automation       D2: Multi-level graduated severity
                                      bands \[8\]\[9\]

  Fraud detection mechanisms          D3: Manager-as-intelligence for
                                      social disruptions \[10\]

  Weather, AQI, and curfew triggers   D4: Policy portability across all
                                      platforms \[11\]

  Real-time monitoring and instant    D5: Composite disruption score
  payout                              (multi-signal fusion) \[12\]

  Weekly pricing model                

  Income loss coverage only           
  -----------------------------------------------------------------------

**D1: 7-Platform Cross-Dataset AI Trained Across the Full Q-Commerce
Spectrum \[1\]-\[7\]**

  -----------------------------------------------------------------------
  **What It Is**                      **Why No Other Team Will Have
                                      This**
  ----------------------------------- -----------------------------------
  The AI models are trained on data   Most teams will build their risk
  derived from primary research       model from one platform or from
  across all seven Q-commerce         synthetic assumptions. A model
  platforms active in India: Swiggy   trained on one platform misprices
  Instamart, BigBasket Now, Flipkart  risk for all others. Zepto workers
  Minutes, Amazon Now, FreshToHome    earn Rs. 50-55 per order on dense
  Express, Zepto, and Blinkit         short routes; Blinkit workers earn
  \[1\]-\[7\]. Each platform has a    Rs. 70 on pre-booked 5 km slots;
  distinct earnings structure, shift  Amazon Now workers earn Rs. 25-35
  model, store type, and income       on longer routes \[5\]\[6\]\[7\].
  volatility profile, all documented  Training across all seven produces
  in seven dedicated ecosystem        a model accurate for the entire
  studies.                            Q-commerce workforce. The dataset
                                      breadth is itself a research moat
                                      that cannot be replicated quickly.

  -----------------------------------------------------------------------

**All 7 Platforms in the Training Dataset**

  ---------------------------------------------------------------------------------------------
  **Platform**    **Store Model**  **Earn/Order**   **Monthly     **Volatility     **Shift
                                                    Income**      Profile**        Type**
  --------------- ---------------- ---------------- ------------- ---------------- ------------
  Swiggy          Dark stores      Rs. 50-75        Rs. 15K-19K   High volatility  Flexible
  Instamart \[1\]                                                                  login

  BigBasket Now   Warehouse/dark   Rs. 35           Rs. \~20K     Stable           \~13 hr
  \[2\]           store                                                            shifts

  Flipkart        Micro-fulfil.    Rs. 47           Rs. 14K-20K   Moderate         Flexible
  Minutes \[3\]   hubs                                                             

  Amazon Now      Fulfillment      Rs. 25-35        Rs. 17K-22K   Low-moderate     Flexible gig
  \[4\]           centers                                                          

  FreshToHome     Food fulfil.     N/A              Rs.           Limited data     N/A
  Express \[5\]   centers                           17.5K-25.8K                    

  Zepto \[6\]     Dark stores      Rs. 50-55        Rs. 20K-21K   High density     Long cont.
                                                                                   shifts

  Blinkit \[7\]   Dark stores      Rs. \~70         Rs. 23K-29K   Slot-dependent   Pre-booked
                                                                                   slots
  ---------------------------------------------------------------------------------------------

**D2: Multi-Level Graduated Severity Bands Payout Scaled to Actual
Disruption Intensity \[8\]\[9\]**

  -----------------------------------------------------------------------
  **What It Is**                      **Why No Other Team Will Have
                                      This**
  ----------------------------------- -----------------------------------
  The problem statement requires      Single-threshold parametric systems
  triggers but does not specify how   create basis risk, which is the
  triggers should fire. This system   core trust failure documented by
  uses three severity levels per      PwC and the World Bank in
  trigger, anchored to national       parametric insurance adoption
  standards. Rainfall (IMD): \>= 64.5 research \[9\]. A worker in 65 mm
  mm -\> Rs. 300, \>= 115.6 mm -\>    rain and one in 200 mm rain both
  Rs. 600, \>= 204.5 mm -\> Rs.       receive the same amount under a
  1,200. Temperature (IMD): \>= 40    flat trigger, which feels arbitrary
  deg C -\> Rs. 300, \>= 45 deg C -\> and reduces willingness to renew.
  Rs. 600. AQI (CPCB): \>= 300 -\>    Graduated bands directly address
  Rs. 300, \>= 400 -\> Rs. 500 \[8\]. this: the payout is proportionate
  The payout a worker receives scales and explainable, which is critical
  with the disruption they actually   for adoption among low-income
  experienced.                        workers who are already skeptical
                                      of insurance products.

  -----------------------------------------------------------------------

**D3: Manager-as-Local-Intelligence Layer Human-Verified Detection for
Social Disruptions \[10\]**

  -----------------------------------------------------------------------
  **What It Is**                      **Why No Other Team Will Have
                                      This**
  ----------------------------------- -----------------------------------
  For curfews, protests, and zone     The problem statement requires
  shutdowns, the system proposes a    curfew and strike detection but
  manager-driven detection layer.     does not specify how. API-only
  Dark store managers flag            detection is noisy and delayed:
  disruptions via a dashboard,        news feeds report events after they
  drawing on rider feedback, local    have escalated, not as riders are
  awareness, and system signals (news being blocked. IMF research on
  APIs, government alerts). The       social unrest forecasting confirms
  system then checks route            that ground-level human signals are
  feasibility algorithmically: if no  faster and more locally accurate
  viable route exists to the delivery than any automated feed \[10\].
  zone, payout triggers. If a route   Route feasibility as the final
  exists, no payout fires regardless  arbiter also prevents both false
  of the flag. All manager inputs are positives and fraud.
  logged and auditable, ensuring      
  traceability and preventing misuse  
  \[10\].                             

  -----------------------------------------------------------------------

**D4: Policy Portability Across All 7 Platforms The Worker Owns Their
Coverage \[11\]**

  -----------------------------------------------------------------------
  **What It Is**                      **Why No Other Team Will Have
                                      This**
  ----------------------------------- -----------------------------------
  The worker owns their individual    Existing gig worker insurance
  policy independently of which       (e.g., Zepto\'s GPA group policy)
  platform they work on. Coverage     is platform-owned. If a worker
  remains active whether a worker is  switches platforms or goes
  delivering for Zepto one week and   inactive, coverage disappears
  Blinkit the next. The platform acts instantly \[11\]. Given that 33% of
  only as a distribution partner: it  gig workers who quit a platform
  never owns, pays for, or controls   eventually return, often using it
  the policy. Premium is deducted     as emergency income, many workers
  from weekly earnings via the active rotate across platforms regularly.
  platform but the policy belongs to  Policy portability is the only
  the worker \[11\].                  design that provides continuous
                                      protection for a workforce that is
                                      structurally multi-platform. No
                                      current product offers this.

  -----------------------------------------------------------------------

**D5: Composite Disruption Score Multi-Signal Fusion Beyond Single-API
Triggers \[12\]**

  -----------------------------------------------------------------------
  **What It Is**                      **Why No Other Team Will Have
                                      This**
  ----------------------------------- -----------------------------------
  Rather than firing payouts on a     The problem statement says to use
  single API signal, the system uses  weather APIs and traffic data, but
  a weighted Composite Disruption     using them as independent, parallel
  Score combining rainfall, AQI,      triggers means a heavy-rain day
  traffic congestion index, and zone  with moderate AQI and high
  flood alert: Composite Score = w1 x congestion may not cross any single
  R_norm + w2 x AQI_norm + w3 x       threshold, even though the combined
  Traffic_norm + w4 x Flood_flag. All effect has halted deliveries. A
  inputs are normalized to a common   composite score captures the
  scale to ensure comparability       real-world truth: disruptions are
  across signals. Trigger bands are   multi-dimensional. This design also
  evaluated against this composite,   makes the system more robust
  not against any one variable in     against API failures: if one data
  isolation. Weights are tuned per    source is unavailable, the score
  city based on historical disruption degrades gracefully rather than
  patterns \[12\].                    failing to trigger at all \[12\].

  -----------------------------------------------------------------------

**Differentiator Summary**

  ------------------------------------------------------------------------------
  **\#**   **Differentiator**        **What It Replaces**   **Evidence Source**
  -------- ------------------------- ---------------------- --------------------
  D1       7-platform cross-dataset  Single-platform or     Ecosystem Studies
                                     synthetic data         \[1\]-\[7\]

  D2       Multi-level graduated     Single threshold: flat IMD / CPCB standards
           severity bands            or no payout           \[8\]\[9\]

  D3       Manager-as-intelligence   API-only detection of  Curfews and Protests
           layer                     social disruptions     doc \[10\]

  D4       Policy portability across Platform-owned GPA     PARAMETERS.docx
           platforms                 group policy           \[11\]
                                     (non-portable)         

  D5       Composite disruption      Single-signal triggers GPS and Data Flow
           score                     (weather OR AQI OR     doc \[12\]
                                     traffic)               
  ------------------------------------------------------------------------------

[]{#sec4 .anchor}**4. End to End System Flow**

The system is structured as a six-stage pipeline. Each stage has clearly
defined inputs, a processing function, outputs, and data sources. Stages
1 to 4 operate at policy inception (weekly), while Stages 5 and 6
operate continuously throughout the policy period.

Each step is represented as a self-contained visual block showing what
happens, why it exists, and the design justification behind it.

  -----------------------------------------------------------------------
  **Step 1 --- Worker Registration**

  **What Happens:** The worker registers by providing profile and
  operational data, including platform, city, vehicle type, shift hours,
  experience level, and delivery zone.

  **Why It Exists:** The system requires worker-specific data to
  determine exposure to environmental and operational risks. Without this
  information, risk classification and eligibility for payouts cannot be
  established.

  **Design Justification:** Gig worker income varies significantly based
  on location and working patterns. Associating each worker with a
  geo-zone enables region-specific risk modeling, ensuring that pricing
  and trigger evaluation reflect actual conditions.
  -----------------------------------------------------------------------

**▼**

  -----------------------------------------------------------------------
  **Step 2 --- Risk Calculation**

  **What Happens:** The system computes risk_score, claim_probability,
  and expected_loss using environmental exposure, disruption
  probabilities, and income patterns. Expected income is derived from
  delivery volume and earnings per order.

  **Why It Exists:** Insurance pricing must be based on expected future
  loss. Without quantifying risk, premiums would not reflect actual
  exposure, leading to financial imbalance.

  **Design Justification:** Disruption probabilities and average loss
  values are used to estimate expected weekly loss. This converts raw
  worker data into a measurable financial risk, forming the foundation
  for actuarial pricing.
  -----------------------------------------------------------------------

**▼**

  -----------------------------------------------------------------------
  **Step 3 --- Weekly Premium Generation**

  **What Happens:** The system converts expected loss into a weekly
  premium by adding expense loading and a risk margin. A tiered pricing
  model is offered with corresponding payout levels.

  **Why It Exists:** Premium generation translates calculated risk into a
  usable financial product. It ensures that expected payouts, operational
  costs, and uncertainty are accounted for.

  **Design Justification:** A weekly model aligns with gig workers\'
  income cycles. Tiered pricing balances affordability and coverage,
  while partial payouts reduce moral hazard and maintain sustainability.
  -----------------------------------------------------------------------

**▼**

  -----------------------------------------------------------------------
  **Step 4 --- Policy Subscription**

  **What Happens:** The worker selects a plan and activates a 7-day
  policy with predefined rules, including payout limits and maximum
  events per week.

  **Why It Exists:** A policy establishes contractual boundaries under
  which monitoring and payouts operate. Without defined terms, trigger
  events cannot be evaluated consistently.

  **Design Justification:** Event caps and payout limits control insurer
  exposure. Fixed rules ensure predictability, which is essential for
  parametric insurance systems.
  -----------------------------------------------------------------------

**▼**

  -----------------------------------------------------------------------
  **Step 5 --- Real-Time Monitoring**

  **What Happens:** The system continuously collects real-time data such
  as rainfall, temperature, AQI, flood alerts, and platform status
  through external APIs.

  **Why It Exists:** Parametric insurance depends on objective and
  continuously updated data. Monitoring enables immediate detection of
  disruptions without relying on user input.

  **Design Justification:** Independent data sources ensure transparency
  and prevent manipulation. Continuous monitoring guarantees that events
  are captured regardless of when they occur.
  -----------------------------------------------------------------------

**▼**

  -----------------------------------------------------------------------
  **Step 6 --- Event Occurrence**

  **What Happens:** A disruption event occurs within the worker\'s zone,
  affecting delivery activity and reducing income. The system records the
  event and associated parameters.

  **Why It Exists:** The insurance model is triggered by disruptions that
  directly impact income. Identifying these events establishes the basis
  for payout eligibility.

  **Design Justification:** Separating event detection from payout logic
  ensures objectivity. Income loss is a consequence of disruption, but
  the system focuses on measurable triggers rather than subjective
  reporting.
  -----------------------------------------------------------------------

**▼**

  -----------------------------------------------------------------------
  **Step 7 --- Trigger Activation**

  **What Happens:** The system evaluates whether predefined thresholds
  are crossed. If conditions are satisfied and the worker is active, the
  trigger is activated.

  **Why It Exists:** Trigger-based activation replaces traditional claim
  assessment, enabling automated and deterministic decision-making.

  **Design Justification:** Thresholds are based on standardized
  classifications such as rainfall levels and AQI categories. Multi-level
  trigger bands align payout with event severity, reducing mismatch
  between disruption intensity and compensation.
  -----------------------------------------------------------------------

**▼**

  -----------------------------------------------------------------------
  **Step 8 --- Payout Execution**

  **What Happens:** Once triggered, the system automatically transfers a
  predefined payout to the worker. No claim submission or verification is
  required.

  **Why It Exists:** Gig workers require immediate financial support.
  Delayed claim processing would reduce the effectiveness of income
  protection.

  **Design Justification:** Fixed payouts eliminate administrative
  overhead and enable rapid disbursement. The system provides partial
  income replacement, ensuring liquidity while maintaining financial
  sustainability.
  -----------------------------------------------------------------------

**Example Scenario: Swiggy Instamart Delivery Partner Mumbai Monsoon
Rainfall Event \[1\]\[8\]**

  -------------------------- --------------------------------------------
  **Worker**                 Swiggy Instamart Partner: Mumbai (High
                             Rainfall Zone) \[1\]

  **Plan Subscribed**        Standard Plan: Rs. 79/week, Rs. 400
                             payout/event

  **Policy Status**          Active: Day 3 of 7 \| Events Used: 0 of 2

  **Normal Daily Income**    35 orders x Rs. 43/order = Rs. 1,500

  **Disruption Event**       Monsoon rainfall: 128 mm recorded by Weather
                             API

  **IMD Classification       Very Heavy Rain: Level 2 threshold (\>=
  \[8\]**                    115.6 mm)

  **Disrupted Daily Income** 15 orders x Rs. 40/order = Rs. 600

  **Income Loss**            Rs. 1,500 - Rs. 600 = Rs. 900 (60%
                             reduction)
  -------------------------- --------------------------------------------

Trigger Evaluation: Observed rainfall of 128 mm is evaluated against
IMD-aligned thresholds. Level 1 (\>= 64.5 mm): exceeded. Level 2 (\>=
115.6 mm): exceeded. Level 3 (\>= 204.5 mm): not met. Highest activated
level: Level 2. Worker active in registered disruption zone: confirmed.
Trigger Event = TRUE. Standard Plan Level 2 payout of Rs. 600 is
automatically issued. \[8\]

**Payout Outcome**

  -----------------------------------------------------------------------
  **Metric**                          **Value**
  ----------------------------------- -----------------------------------
  Delivery Earnings (Disruption Day)  Rs. 600

  Insurance Payout (Level 2 Trigger)  \+ Rs. 600

  Total Income on Disruption Day      Rs. 1,200

  Expected Income (Normal Day)        Rs. 1,500

  Residual Basis Risk                 Rs. 300 (by design: partial
                                      coverage, not full indemnity)

  Income Recovery Rate                67% of loss recovered

  Events Remaining This Week          1 of 2
  -----------------------------------------------------------------------

The Rs. 600 payout reflects Level 2 severity, not Level 1, because 128
mm exceeds the Very Heavy Rain threshold of 115.6 mm \[8\]. A
single-threshold system would have paid only Rs. 300, illustrating
precisely why tiered bands are essential. The residual basis risk of Rs.
300 is intentional: the system provides liquidity support, not full
indemnification. The 2-event weekly cap and Rs. 79 premium together
maintain actuarial sustainability.

[]{#sec5 .anchor}**5. Parametric Trigger System**

The parametric trigger system forms the core decision engine of BHIMA
ASTRA. Rather than relying on subjective loss assessment, it uses
objective, pre-defined thresholds sourced from India Meteorological
Department (IMD) and Central Pollution Control Board (CPCB) national
standards \[8\]. When real-time data crosses a threshold and the worker
is confirmed active in the affected zone, the payout fires
automatically.

**Trigger Thresholds and Payout Levels \[8\]\[9\]**

  --------------------------------------------------------------------------------------------------
  **Trigger       **Level**   **Threshold**      **Standard**     **Basic   **Standard   **Premium
  Type**                                                          Plan**    Plan**       Plan**
  --------------- ----------- ------------------ ---------------- --------- ------------ -----------
  Heavy Rainfall  L1          \>= 64.5 mm/day    IMD Heavy Rain   Rs. 300   Rs. 400      Rs. 600
  \[8\]                                                                                  

  Heavy Rainfall  L2          \>= 115.6 mm/day   IMD Very Heavy   Rs. 300   Rs. 600      Rs. 900
  \[8\]                                          Rain                                    

  Heavy Rainfall  L3          \>= 204.5 mm/day   IMD Extremely    Rs. 600   Rs. 800      Rs. 1,200
  \[8\]                                          Heavy Rain                              

  Extreme Heat    L1          \>= 40 deg C       IMD Heatwave     Rs. 300   Rs. 300      Rs. 300
  \[8\]                                                                                  

  Extreme Heat    L2          \>= 45 deg C       IMD Severe       Rs. 300   Rs. 600      Rs. 600
  \[8\]                                          Heatwave                                

  Air Pollution   L1          AQI \>= 300        CPCB Very Poor   Rs. 300   Rs. 300      Rs. 300
  \[9\]                                                                                  

  Air Pollution   L2          AQI \>= 400        CPCB Severe      Rs. 300   Rs. 500      Rs. 500
  \[9\]                                                                                  

  Flood / Zone    \--         Flood alert = 1    State / IMD      Plan      Plan payout  Plan payout
  Shutdown \[8\]                                 alert            payout                 

  Platform Outage \--         Outage flag or     System/Manager   Plan      Plan payout  Plan payout
  / Curfew                    manager-verified                    payout                 
  --------------------------------------------------------------------------------------------------

**Composite Disruption Score \[12\]**

Rather than evaluating triggers independently, the system computes a
weighted Composite Disruption Score that fuses multiple environmental
signals. This ensures that combined adverse conditions, even when no
single variable crosses its threshold, are properly captured and
evaluated \[12\].

  -----------------------------------------------------------------------

  **Composite Score = w₁·R_norm + w₂·AQI_norm + w₃·Traffic_norm +
  w₄·Flood_flag**

  where w1 \... w4 are weights tuned per city based on historical
  disruption patterns \[12\]

  All inputs normalised to a common scale (0 to 1) to ensure
  comparability across signals.

  -----------------------------------------------------------------------

This design makes the system more robust against API failures. If one
data source is unavailable, the composite score degrades gracefully
rather than failing to trigger at all \[12\].

[]{#sec6 .anchor}**6. AI and Machine Learning Architecture**

The AI layer is designed to enable data-driven, actuarially consistent,
and personalised insurance pricing for gig delivery workers operating
under uncertain environmental conditions. The system integrates three
interconnected models: an Income Prediction Model, a Disruption Risk
Prediction Model, and a Premium Adjustment Model.

These models operate as a closed actuarial decision loop, where each
stage directly feeds into the next:

  -----------------------------------------------------------------------

  **E\[L\_(weekly)\] = P\_(disruption) × ( Ŷ\_(income) × S\_(event) )**

  Ŷ\_(income) = predicted weekly income of the worker

  P\_(disruption) = probability of a disruption event in the worker\'s
  zone

  S\_(event) = severity factor from parametric trigger thresholds
  \[Section 5\]

  -----------------------------------------------------------------------

**6.1 Income Prediction Model**

**Purpose**

The Income Prediction Model estimates the expected daily and weekly
earnings of a gig delivery worker under normal, undisrupted operating
conditions. This predicted income serves as the baseline for all
downstream insurance computations, including income loss estimation,
coverage determination, and premium pricing.

Unlike salaried employment, gig worker income is inherently stochastic
and depends on multiple interacting factors such as order volume,
working hours, surge demand, incentives, and geographic demand
variability \[2\]\[3\]\[4\]. Empirical analysis across multiple
quick-commerce platforms shows that daily earnings range from Rs. 560 to
Rs. 3,000, with an average of approximately Rs. 1,350, while weekly
earnings vary between Rs. 4,000 and Rs. 21,000 depending on worker
activity and zone characteristics \[1\]\[5\].

**Algorithm: Random Forest Regressor \[13\]**

The income prediction task is formulated as a supervised regression
problem and implemented using a Random Forest Regressor. This model is
selected due to its strong performance on structured, high-dimensional
datasets and its ability to capture complex, non-linear relationships
between multiple input variables \[13\]\[14\].

Random Forest operates by aggregating predictions from multiple decision
trees trained on different subsets of the data, resulting in reduced
variance and improved generalisation, robustness to noise and outliers
(e.g., surge spikes), and the ability to model interaction effects
without explicit feature engineering. Studies in income and salary
prediction consistently demonstrate that ensemble tree-based models
outperform linear regression in multi-factor scenarios involving
behavioural and contextual features \[14\]\[15\].

**Model Inputs**

  --------------------------------------------------------------------------
  **Variable**          **Description**        **Type**    **Source**
  --------------------- ---------------------- ----------- -----------------
  Orders per Day        Number of deliveries   Observed    \[2\]\[3\]\[4\]
                        completed                          

  Earnings per Order    Pay per delivery       Observed    \[2\]\[3\]\[4\]

  Shift Hours           Active working hours   Observed    \[2\]
                        per day                            

  Surge Multiplier      Demand-based pricing   Observed    \[2\]\[3\]
                        multiplier                         

  Geo-Zone ID           Worker\'s delivery     Observed    \[5\]
                        zone                               

  Zone Demand Level     Low / Medium / High    Derived     \[5\]
                        demand                             

  Day of Week           Demand variation       Derived     \[5\]
                        pattern                            

  Experience Level      Worker tenure (years)  Observed    \[5\]
  --------------------------------------------------------------------------

**Model Outputs**

  ------------------------------------------------------------------------------
  **Output Variable**      **Description**     **Range**      **Role in System**
  ------------------------ ------------------- -------------- ------------------
  expected_income          Predicted daily     Rs. 560 to Rs. Baseline income
                           earnings            3,000          estimation

  income_baseline_weekly   Predicted weekly    Rs. 4,000 to   Coverage and
                           earnings            Rs. 21,000     pricing anchor
  ------------------------------------------------------------------------------

**Income Loss Estimation**

  -----------------------------------------------------------------------

  **Loss = Ŷ\_(income) × S\_(event)**

  S\_(event) = severity of disruption derived from parametric triggers
  (e.g., rainfall thresholds, AQI levels)

  Empirical evidence shows disruption events reduce earnings by 30-60%
  \[2\]\[3\]\[4\]

  Example: Baseline income = Rs. 1,500 / day

  After heavy rainfall = Rs. 600 (income drops approx. 60%)

  Loss = Rs. 900

  -----------------------------------------------------------------------

**6.2 Disruption Risk Prediction Model**

**Purpose**

The Disruption Risk Prediction Model estimates the probability that one
or more parametric trigger events will occur in a worker\'s delivery
zone during the upcoming 7-day policy period. Unlike traditional
insurance models that rely on static, city-level averages, this model
generates zone-specific, time-sensitive probability estimates, allowing
the system to dynamically adjust risk based on real environmental and
operational conditions \[16\]\[17\].

**Algorithm: XGBoost Classifier \[16\]**

The disruption prediction problem is formulated as a supervised
classification task and implemented using XGBoost (Extreme Gradient
Boosting). XGBoost is selected due to its strong performance on
structured datasets, particularly in scenarios involving environmental
variables and risk prediction \[16\]\[17\].

**Model Inputs**

  ------------------------------------------------------------------------------
  **Variable**        **Description**    **Range**   **Type**   **Source**
  ------------------- ------------------ ----------- ---------- ----------------
  Rainfall (mm/day)   Daily              0-300 mm    Observed   \[8\]
                      precipitation                             
                      level                                     

  Temperature (deg C) Ambient outdoor    20-48 deg C Observed   \[8\]
                      temperature                               

  AQI                 Air Quality Index  0-500       Observed   \[9\]

  Flood Alert Flag    Flood occurrence   0 / 1       Observed   \[8\]
                      indicator                                 

  Platform Outage     App/service        0 / 1       Observed   \[1\]
  Flag                disruption                                

  Zone Shutdown Flag  Restricted access  0 / 1       Observed   \[1\]
                      indicator                                 

  Traffic Index       Road congestion    0-100       Observed   \[18\]
                      level                                     

  Historical          Past event rate in Derived     Derived    \[5\]
  Disruption          zone                                      
  Frequency                                                     
  ------------------------------------------------------------------------------

**Model Outputs**

  -------------------------------------------------------------------------------------
  **Output Variable**               **Description**     **Range**   **Role in System**
  --------------------------------- ------------------- ----------- -------------------
  P(Rain Event)                     Probability of      0.15-0.25   Risk estimation
                                    rainfall trigger                

  P(Heat Event)                     Probability of      0.10-0.20   Risk estimation
                                    heatwave trigger                

  P(AQI Event)                      Probability of      0.05-0.15   Risk estimation
                                    pollution trigger               

  combined_disruption_probability   Overall weekly      0.30-0.40   Core premium driver
                                    disruption                      
                                    probability                     

  zone_risk_score                   Normalised risk     0.0-1.0     Pricing adjustment
                                    score for zone                  
  -------------------------------------------------------------------------------------

  -----------------------------------------------------------------------

  **E\[L\_(weekly)\] = P\_(disruption) × ( Ŷ\_(income) × S\_(event) )**

  Representative values:

  P\_(disruption) = 0.35

  Expected loss / event = Rs. 600

  E\[L\_(weekly)\] = 0.35 x Rs. 600 = Rs. 210 (pure actuarial premium)
  \[16\]\[17\]

  -----------------------------------------------------------------------

**6.3 Premium Adjustment Model (Dynamic Pricing) \[19\]\[20\]**

**Purpose**

The Premium Adjustment Model converts the expected loss derived from
Models 6.1 and 6.2 into a final, personalised weekly premium for each
worker. This model ensures that pricing is not fixed or uniform but
dynamically reflects the worker\'s income level, geographic exposure,
and environmental risk conditions. Unlike traditional insurance systems
where all users in a category pay the same premium, this system
introduces intra-plan personalisation, improving actuarial fairness and
reducing adverse selection \[19\]\[20\].

  -----------------------------------------------------------------------

  **Weekly Premium = E\[L\] + Expense Loading + Risk Margin**

  Expense Loading = 10% to 15% of E\[L\]

  Risk Margin = 20% to 30% of E\[L\]

  Representative values: E\[L\] = Rs. 210 Expense = Rs. 21 Margin = Rs.
  52

  Weekly Premium = Rs. 283 (full-risk premium) \[16\]\[19\]

  -----------------------------------------------------------------------

**Tiered Plan Structure**

  --------------------------------------------------------------------------------
  **Plan**    **Weekly     **Payout per **Max           **Max        **Target
              Premium**    Event**      Events/Week**   Payout**     Segment**
  ----------- ------------ ------------ --------------- ------------ -------------
  Basic       Rs. 49       Rs. 300      2               Rs. 600      Low-income /
                                                                     part-time

  Standard    Rs. 79       Rs. 400      2               Rs. 800      Regular
                                                                     workers

  Premium     Rs. 119      Rs. 600      2               Rs. 1,200    High-income /
                                                                     full-time
  --------------------------------------------------------------------------------

**Dynamic Adjustment Factors**

  ------------------------------------------------------------------------
  **Factor**               **Effect on Premium**             **Source**
  ------------------------ --------------------------------- -------------
  Geographic Zone Risk     High-risk zones increase premium  \[5\]\[16\]
                           within plan band                  

  Seasonal Risk            Monsoon / extreme weather periods \[8\]
                           increase premium                  

  Historical Disruption    Frequent past events increase     \[5\]
  Freq.                    premium                           

  Worker Income Exposure   Higher earnings implies higher    \[5\]
                           insurable loss implies higher     
                           premium                           

  Tenure and Consistency   Stable workers receive discount   \[1\]\[19\]
                           within plan band                  
  ------------------------------------------------------------------------

Dynamic pricing in insurance has been shown to improve risk alignment
and reduce adverse selection by ensuring that lower-risk users are not
overcharged while higher-risk users are priced appropriately
\[19\]\[20\]\[21\].

**Integration with Parametric System**

Once the premium is finalised and the worker subscribes, the system
monitors environmental triggers in real time (Section 5). When a
predefined threshold is crossed, payout is executed automatically. No
claim submission or verification is required. The AI layer therefore
determines how much to charge while the parametric system determines
when to pay. This separation ensures that the system remains fully
parametric, automated, and scalable, while still leveraging AI for
accurate risk-based pricing.

**References for Section 6**

\[1\] Swiggy Instamart Delivery Partner Ecosystem (Internal Research
Document)

\[2\] Swiggy Instamart Delivery Partner Ecosystem (Internal Research
Document)

\[3\] BigBasket Now Delivery Partner Ecosystem (Internal Research
Document)

\[4\] Zepto / Blinkit / Flipkart Minutes / Amazon Now Delivery Partner
Ecosystem Documents

\[5\] A. Dataset and Variables Design (Section A, Internal Document)

\[8\] India Meteorological Department (IMD) Rainfall Classification.
https://mausam.imd.gov.in/

\[9\] Central Pollution Control Board (CPCB) National AQI Classification
Standard. https://cpcb.nic.in/

\[13\] Breiman, L. (2001). Random Forests. Machine Learning, 45, 5-32.

\[14\] Eichinger, F., and Mayer, R. (2022). Predicting Salaries with
Random-Forest Regression. Springer.

\[15\] Galar, C., et al. (2022). Supervised Machine Learning Predictive
Analytics for Alumni Income. Journal of Big Data, 9(1).

\[16\] Chen, T., and Guestrin, C. (2016). XGBoost: A Scalable Tree
Boosting System. Proc. 22nd ACM SIGKDD, 785-794.

\[17\] Fauzan, M. A., and Murfi, H. (2018). The Accuracy of XGBoost for
Insurance Claim Prediction. IJASCA, 10(2).

\[18\] Google Maps Platform Routes and Traffic API.
https://developers.google.com/maps/documentation/routes

\[19\] AccelTree (2025). AI-Driven Dynamic Premium Pricing in Insurance.
https://acceltree.com/

\[20\] Insurance Thought Leadership (2024). Dynamic Pricing Gives
Insurers a Competitive Edge.

\[21\] SimpleSolve (2025). Dynamic Pricing in Insurance Using AI and
Predictive Analytics.

[]{#sec7 .anchor}**7. Adversarial Defense and Anti-Spoofing Strategy**

Parametric insurance fires automatic payouts on objectively measured
events like rainfall, AQI, heatwave, and flood alert, thus removing all
administrative friction. This same design, however, changes the fraud
surface entirely: because payouts trigger on environmental data rather
than individual declarations, the attack vector shifts from falsifying
loss documentation to falsifying presence in the disrupted zone at the
moment of the trigger.

In Q-commerce gig insurance this takes two principal forms: (1)
Individual GPS spoofing, where a worker overrides the phone\'s GPS
output using a freely available Android app to report disruption-zone
coordinates while remaining at home. (2) Coordinated ring fraud, where a
Telegram-organised syndicate of workers simultaneously spoof their
location, flooding the claims pipeline in a narrow window and draining
the liquidity pool before any rule-based check responds.

The DEVTrails 2026 threat report confirmed this precisely: 500 workers
exploited a beta platform through coordinated GPS spoofing, triggering
mass false payouts in under fifteen minutes. Preventing this attack
class is the primary design objective of the fraud detection system.

  -----------------------------------------------------------------------
  **Core Design Principle**

  BHIMA ASTRA treats fraud detection as a signal separation problem:

  distinguishing real-world disruption behavior from simulated presence
  under adversarial conditions.
  -----------------------------------------------------------------------

**7.1 Limitations of Existing Approaches**

Rule-based systems are the most widely deployed fraud control in
insurance \[22\], but they have no temporal memory and evaluate each
claim at a single instant, unable to distinguish a genuine worker who
lost GPS lock in a storm from one spoofing coordinates at home.
Isolation Forest detects statistical outliers \[23\] but scores every
claimant in isolation: a ring of 200 workers filing simultaneously
appears as 200 individually marginal anomalies, because the algorithm
cannot represent the connections between them \[24\]. XGBoost excels on
tabular claim data \[16\]\[25\] but processes each record as an
independent row and cannot learn that a worker stationary for 40 minutes
before a trigger, who files within 60 seconds of its timestamp, presents
a fundamentally different behavioral profile from an active worker.

  -----------------------------------------------------------------------
  **The Key Distinction**

  Traditional models ask: \"Is this unusual?\"

  BHIMA ASTRA asks: \"Is this physically plausible and socially
  independent?\"

  The distinction is the entire design.
  -----------------------------------------------------------------------

**7.2 Original Contributions**

  --------------------------------------------------------------------------
  **Contribution**      **Description**
  --------------------- ----------------------------------------------------
  C1: Cost-cascade      \~80% of claims resolved at the rule layer with zero
  architecture          ML overhead; expensive models invoked only at the
                        4-20% margin.

  C2: Temporal and      LSTM behavioral sequence model (time axis) combined
  relational hybrid     with graph community detection (relational axis). No
                        prior parametric insurance fraud system combines
                        both.

  C3: Agent-based       Adaptive cluster-context escalation, stateful
  orchestration         48-hour hold/release lifecycle, and weekly online
                        learning from confirmed fraud outcomes.

  C4:                   Covers all five Q-commerce disruption triggers:
  Parametric-specific   rainfall, AQI, heatwave, flood alert, and platform
  design                outage. Designed for gig workers, not generic
                        insurance claimants.
  --------------------------------------------------------------------------

**7.3 Core Detection Architecture**

**Stage 1: Deterministic Filtering Layer (\~80% of claims)**

Resolves approximately 80% of claims with zero ML overhead through
contract rules and four anti-spoofing checks:

-   GPS and cell tower delta: Spoofing apps alter GPS output but cannot
    change tower registration. Delta \> 500 m flags the claim \[23\].

-   Accelerometer and motion mismatch: A flat accelerometer reading for
    \> 10 min during a trigger window is a static-presence signal.

-   Timing implausibility: A claim filed within 60 seconds of a trigger
    timestamp is physically implausible for a genuine
    notification-read-interact workflow.

-   Device fingerprinting: A previously flagged device ID triggers an
    immediate audit hold. Clean claims score 0.0 and are paid within 5
    minutes.

**Stage 2: Behavioral Intelligence Layer (\~15% of claims)**

A lightweight LSTM network evaluates the 10-minute behavioral time
series around the trigger event \[26\]. The fraud signal lies in the
sequence and rhythm of features, not any single snapshot. A genuine
rider shows GPS jitter correlated with motion spikes, app interactions,
and tower transitions; a spoofer at home shows a flat accelerometer,
zero app events, and a single static tower. No non-sequential model
captures this distinction \[26\]\[22\].

Architecture: 2 LSTM layers, 32 hidden units, 10 time steps x 5
features, \~25,000 parameters, less than 5 ms CPU inference
\[26\]\[27\].

  -----------------------------------------------------------------------
  **Score Range**                     **Action**
  ----------------------------------- -----------------------------------
  Score \< 0.3                        Full payout released instantly

  Score 0.3-0.7                       50% released immediately, 50% held
                                      48 h (auto-released if no
                                      escalation)

  Score \> 0.7                        Full hold, placed in audit queue
  -----------------------------------------------------------------------

  ------------------------------------------------------------------------
  **Feature**           **Description**        **Range**   **Type**
  --------------------- ---------------------- ----------- ---------------
  GPS and cell tower    GPS vs. triangulated   0-10,000 m  Continuous
  delta                 cell tower position                

  Accelerometer         Movement intensity     0.0-50.0    Continuous
  variance              across x/y/z axes                  

  App interaction count User-initiated events  0-60        Integer
                        per minute                         

  Cell tower transition New tower connection   0 / 1       Binary
                        within minute                      

  Order status event    Delivery status change 0 / 1       Binary
                        within minute                      
  ------------------------------------------------------------------------

**Stage 3: Relational Intelligence Layer (\~4% of claims)**

Individual LSTM scores for ring members typically sit at 0.25-0.30, each
plausible alone. Yet the ring leaves an unmistakable relational
signature: same filing window, GPS clustered within an impossible
radius, identical device model and OS, same IP subnet
\[28\]\[29\]\[24\]. For each trigger event, a claim graph is constructed
where nodes represent workers and edges connect those sharing multiple
signals such as time window, location proximity, device similarity, or
IP subnet. Louvain community detection \[29\] identifies dense clusters
of coordinated workers; groups above threshold size are flagged as
potential fraud rings and the entire cohort is held. Phase 3 upgrades to
a GCN (PyTorch Geometric) with learned edge weights \[30\]\[31\].

**Stage 4: Decision Intelligence Layer (\~1% of claims)**

The Fraud Agent acts as the system\'s decision layer, combining signals
across stages and enabling context-aware escalation that no standalone
model can achieve. A worker scoring 0.28, individually below threshold,
who belongs to a cluster of 14 workers all scoring 0.22 to 0.30 is
routed to Stage 3, because the agent holds the joint cluster
distribution in context. It manages the full claim lifecycle:
escalation, 48-hour hold decisions, and automated release, ensuring
consistent and stateful execution. Confirmed outcomes feed the Insight
Agent\'s weekly retraining cycle, continuously improving LSTM and GNN
accuracy from real operational data, a feedback loop absent from every
static fraud pipeline.

**7.4 Cost Cascade and System Advantages**

  ----------------------------------------------------------------------------------
  **Stage**   **Model**   **Claims   **Cost**   **Fraud Signal Detected**
                          %**                   
  ----------- ----------- ---------- ---------- ------------------------------------
  Stage 1     Rule engine \~80%      \~0 ms     Contract breach, GPS-tower delta,
                                                timing, device

  Stage 2     Tiny LSTM   \~15%      \~5 ms CPU Individual behavioral sequence
                                                anomalies

  Stage 3     Louvain /   \~4%       \~50 ms    Coordinated ring / syndicate fraud
              GCN                    CPU        

  Stage 4     LLM Agent   \~1%       \~500 ms   Edge cases and full audit
              (RAG)                  API        documentation
  ----------------------------------------------------------------------------------

**7.5 Fraud Resilience Scenarios**

  ---------------------------------------------------------------------------
  **Scenario**   **Situation**       **System Response** **Result**
  -------------- ------------------- ------------------- --------------------
  Mass GPS       500 workers         Stage 3 constructs  Entire ring blocked
  Spoofing       simultaneously      a claim graph;      before payout. Fraud
  Attack         activate GPS        Louvain detects a   contained within 90
                 spoofing apps and   \>8-node community  seconds.
                 file claims during  with high           
                 a Tier 2 rainfall   shared-attribute    
                 trigger in Mumbai.  edge weights.       

  Genuine        Worker in a         Score 0.41: 50%     Remaining 50%
  Worker:        flood-affected zone payout released     released within 4
  Network        loses mobile        immediately. Stage  hours. Worker
  Failure During connectivity for 18 4 LLM agent         receives full
  Disruption     minutes, producing  cross-references    payout. No manual
                 erratic GPS         the Monitor         intervention
                 patterns that       Agent\'s network    required.
                 resemble spoofing.  outage log. Outage  
                                     confirmed.          

  Coordinated    18 workers each     Fraud Agent         Entire cohort held.
  Low-Score Ring score 0.24-0.29 on  observes the        Cluster-context
                 the LSTM,           cluster joint       escalation exposes
                 individually below  distribution and    coordinated fraud
                 the 0.30 escalation routes the full     that
                 threshold.          cohort to Stage 3.  individual-level
                                     Louvain confirms a  models would
                                     dense community.    completely miss.
  ---------------------------------------------------------------------------

[]{#sec8 .anchor}**8. Multi-Agent System Design**

The system employs a multi-agent architecture that coordinates real-time
monitoring, fraud detection, claims processing, and decision escalation
across specialized agent roles. Each agent is purpose-built for a
specific function within the insurance pipeline, enabling parallel
processing, stateful lifecycle management, and continuous improvement
through online learning.

  ------------------------------------------------------------------------
  **Agent**        **Role**                    **Key Capability**
  ---------------- --------------------------- ---------------------------
  Monitor Agent    Continuously ingests        Triggers composite
                   real-time API feeds         disruption score evaluation
                   (weather, AQI, traffic,     per zone
                   platform status)            

  Trigger Agent    Evaluates IMD/CPCB          Fires trigger events and
                   thresholds and composite    determines severity level
                   score against active        (L1/L2/L3)
                   policies                    

  Fraud Agent      Orchestrates the 4-stage    Stateful 48-hour
                   fraud detection cascade     hold/release lifecycle;
                                               cluster-context escalation

  Payout Agent     Executes approved payouts   Ensures immediate transfer
                   via UPI/Razorpay sandbox    for clean claims; updates
                                               event counter

  Manager          Processes dark store        Route feasibility check as
  Intelligence     manager flags for social    final arbiter for social
  Agent            disruptions (curfews,       trigger payouts \[10\]
                   protests)                   

  Insight Agent    Runs weekly retraining      Online learning from
                   cycle on confirmed fraud    operational data;
                   outcomes                    continuously improves LSTM
                                               and GNN accuracy
  ------------------------------------------------------------------------

The D3 differentiator, the Manager-as-Local-Intelligence Layer, is
embedded within the Manager Intelligence Agent \[10\]. Dark store
managers flag disruptions via a dashboard, drawing on rider feedback,
local awareness, and system signals. The system checks route feasibility
algorithmically: if no viable route exists to the delivery zone, payout
triggers. All manager inputs are logged and auditable, ensuring
traceability and preventing misuse.

[]{#sec9 .anchor}**9. Financial Model**

**9.1 Delivery Partners (The Worker)**

**Their Reality Today**

  -----------------------------------------------------------------------
  **Metric**                          **Value**
  ----------------------------------- -----------------------------------
  Net monthly income (full-time)      \~Rs. 18,763 after fuel and
                                      maintenance costs \[32\]

  Operating expenses                  \~32% of gross earnings consumed
                                      \[32\]

  Workers struggling to cover basics  35% cannot cover food and rent
                                      regularly \[32\]

  Income drop on a disrupted day      Rs. 560-900 lost per event day
                                      \[7\]\[10\]

  Existing income protection          None (structured) \[6\]
  -----------------------------------------------------------------------

**What BHIMA ASTRA Delivers for Workers**

  -----------------------------------------------------------------------
  **Benefit**                         **Detail**
  ----------------------------------- -----------------------------------
  Automatic payout on disruption: no  Rs. 300-1,200 transferred
  claim filing                        automatically with minimal delay
                                      after trigger validation.
                                      \[10\]\[11\]

  Affordable: just 1.0%-2.5% of       Rs. 49-119/week premium on a \~Rs.
  weekly income                       4,690/week income. Less than Rs.
                                      17/day at max. \[32\]\[10\]

  Platform-enabled enrolment with     No separate app or form. Worker is
  opt-out                             protected from day one. Proven in
                                      Uber and fintech insurance. \[33\]

  Standard plan Rs. 800 payout: 17%   On a disrupted week where income
  income replacement                  falls to Rs. 600, Rs. 800 is
                                      meaningful liquidity. \[32\]\[10\]

  Evidence from real-world pilot      Jan Sahas parametric pilot (India):
  implementations                     informal workers received Rs. 1,000
                                      payouts during heatwaves. Same
                                      trigger model. \[34\]
  -----------------------------------------------------------------------

**9.2 Delivery Platforms**

**Why Platforms Will Participate**

  -----------------------------------------------------------------------
  **Value Proposition**    **Detail**
  ------------------------ ----------------------------------------------
  Worker retention: the #1 33% of gig workers who quit eventually return.
  platform pain point      Constant re-onboarding is expensive. Welfare
                           benefits are the top retention driver.
                           \[32\]\[35\]

  Regulatory compliance at Rajasthan Gig Workers Act 2023 and Karnataka
  zero premium cost        Bill 2024 mandate worker welfare
                           contributions. Platform distributes but never
                           underwrites. \[36\]\[37\]

  Distribution commission: 10,000 policies x Rs. 75 avg x 7.5% = Rs.
  5-10% per policy         56,250/week earned by platform. No insurance
                           liability at all. \[33\]

  Public reputation: a     Swiggy introduced accident cover due to media
  verifiable welfare story and protest pressure. \[38\] Our model gives
                           platforms the same story at zero premium cost.

  No financial liability   Platform is distributor only. It never
                           underwrites risk, never pays claims, and never
                           owns any policy.
  -----------------------------------------------------------------------

**Platform Commission: Structured Illustration**

  -----------------------------------------------------------------------
  **Platform Commission Illustration**

  Scenario: 1 platform x 1 major city (e.g. Blinkit, Mumbai)

  Active delivery fleet = 50,000 workers

  Adoption rate (conservative 20%)= 10,000 policies

  Average weekly premium = Rs. 75

  Platform commission rate = 7.5%

  Weekly commission income = Rs. 56,250

  Annual commission income = Rs. 29.2 Lakh (single city, 1 platform)

  Note: Commission earned purely from distribution. No capital at risk.
  No insurance liability.
  -----------------------------------------------------------------------

**9.3 Insurance Provider (The Insurer)**

  -----------------------------------------------------------------------
  **Structural Advantage** **Detail**
  ------------------------ ----------------------------------------------
  Near-zero customer       Platform brings pre-qualified policyholders
  acquisition cost         directly. No agent network, no ads, no
                           per-customer marketing spend. \[33\]

  52 premium payments per  Weekly model = 52 revenue events/year vs. 1
  year per worker          for annual insurance. Stable, predictable,
                           high-frequency premium inflow. \[10\]

  Zero claim investigation Parametric model: trigger fires implies payout
  cost                     transfers automatically. No adjuster, no loss
                           assessment, no dispute. \[11\]

  AI risk pricing reduces  XGBoost zone_risk_score prices each worker by
  adverse selection        actual zone and season. High-risk zones priced
                           higher. \[10\]

  Risk pool cross-subsidy  Premium plan (Rs. 119) cross-subsidises Basic
                           plan (Rs. 49). Larger pool = more stable loss
                           ratio over time. \[10\]
  -----------------------------------------------------------------------

**9.4 Revenue Model: Phased Rollout**

**Phase 1: Pilot Deployment (1 platform x 1 city)**

  -----------------------------------------------------------------------
  **Parameter**                       **Value**
  ----------------------------------- -----------------------------------
  Active delivery workforce           30,000 workers

  Adoption rate (conservative)        10%

  Policyholders                       3,000 workers

  Average weekly premium              Rs. 70

  Annual premium inflow               3,000 x Rs. 70 x 52 = approx. Rs.
                                      1.09 Crore

  Annual claims estimate              3,000 x 0.55 x 9 x Rs. 400 =
                                      approx. Rs. 59.4 Lakh

  Loss ratio                          \~54% (within target actuarial
                                      range of 50-65%)

  Surplus                             Rs. 1.09 Cr - Rs. 0.70 Cr = Rs.
                                      0.39 Crore

  Break-even threshold                \~2,000-2,500 policyholders
  -----------------------------------------------------------------------

**Phase 2: Controlled Expansion (2-3 cities x 2 platforms)**

  -----------------------------------------------------------------------
  **Parameter**                       **Value**
  ----------------------------------- -----------------------------------
  Worker pool                         \~150,000

  Adoption rate                       15%

  Policyholders                       \~22,500

  Average weekly premium              Rs. 75

  Annual premium                      approx. Rs. 8.8 Crore

  Annual claims                       22,500 x 0.55 x 9 x Rs. 400 =
                                      approx. Rs. 4.45 Crore

  Loss ratio                          \~50-55%
  -----------------------------------------------------------------------

**Phase 3: Mature Scale (3 platforms x major metro clusters)**

  -----------------------------------------------------------------------
  **Parameter**                       **Value**
  ----------------------------------- -----------------------------------
  Worker pool                         \~500,000

  Adoption rate                       20%

  Policyholders                       100,000

  Average weekly premium              Rs. 75

  Annual premium                      approx. Rs. 39 Crore

  Annual claims                       100,000 x 0.55 x 9 x Rs. 400 =
                                      approx. Rs. 19.8 Crore

  Loss ratio                          \~50-60%
  -----------------------------------------------------------------------

**9.5 Sensitivity Analysis**

  -------------------------------------------------------------------------
  **Scenario**   **Parameter Change**  **Impact**    **Result**
  -------------- --------------------- ------------- ----------------------
  High           Disruption weeks: 9   Claims up 33% Claims approx. Rs. 26
  Disruption     to 12                               Cr (Phase 3); Loss
  Year                                               ratio approx. 65-68%;
                                                     still within
                                                     acceptable actuarial
                                                     range

  Low Adoption   Adoption: 20% to 10%; Premium and   Loss ratio remains
                 Policyholders: 100K   claims both   stable; model scalable
                 to 50K                halve         but slower to
                                                     profitability

  Severe Event   Payout/event: Rs. 400 Claims        Loss ratio may reach
  Spike          to Rs. 600            increase      \~70%; mitigated
                                       \~50%         through payout caps,
                                                     tiered coverage,
                                                     risk-based pricing
  -------------------------------------------------------------------------

  -----------------------------------------------------------------------
  **Key Insight**

  The model is robust under variability, with loss ratios remaining
  within acceptable bounds across multiple stress conditions.
  -----------------------------------------------------------------------

[]{#sec10 .anchor}**10. Stakeholder Benefits**

  ------------------------------------------------------------------------
  **Stakeholder**       **Primary Value**            **Key Number**
  --------------------- ---------------------------- ---------------------
  Delivery Partner      Automatic income payout on   Rs. 300-1,200 payout;
  (Worker)              disruption day with no claim 1.0-2.5% of weekly
                        needed                       income \[10\]\[11\]

  Delivery Platform     Worker retention, regulatory 5-10% commission;
                        compliance, and commission   zero premium
                        income                       liability
                                                     \[33\]\[36\]\[37\]

  Insurance Provider    High-frequency weekly        Rs. 39 Cr/yr revenue;
                        revenue; low-cost parametric loss ratio improves
                        operations                   with scale \[10\]
  ------------------------------------------------------------------------

This combination of scale, data availability, and measurable disruption
risk makes gig worker income protection uniquely suitable for parametric
insurance design.

[]{#sec11 .anchor}**11. Advantages of Our Model**

  -----------------------------------------------------------------------
  **Advantage**            **Description**
  ------------------------ ----------------------------------------------
  Fully Automated Payouts  No claim filing, no adjuster, no delay.
                           Payouts execute automatically within minutes
                           of a confirmed trigger.

  AI-Personalised Pricing  Premiums reflect each worker\'s actual risk
                           profile, not a flat rate. This improves
                           fairness and reduces adverse selection.

  Multi-Level Trigger      Payouts scale with disruption severity,
  Bands                    reducing basis risk and increasing worker
                           trust in the product.

  Platform Distribution    Zero customer acquisition cost for the
  Model                    insurer. Platforms distribute the product and
                           earn commission without taking on insurance
                           liability.

  Policy Portability       Workers retain coverage regardless of which
                           platform they work on: the only design that
                           matches the multi-platform reality of gig
                           work.

  Composite Disruption     Captures combined adverse conditions that no
  Score                    single-signal trigger would detect, improving
                           trigger accuracy and reducing false negatives.

  Fraud-Resilient          4-stage cost-cascade system resolves \~80% of
  Architecture             claims instantly, while protecting the
                           liquidity pool from coordinated ring attacks.

  Actuarially Sustainable  Loss ratios projected at 50-65% across all
                           phases, with break-even achieved at
                           \~2,000-2,500 policyholders in pilot
                           deployment.

  Weekly Renewal Cycle     Aligns with gig workers\' income rhythm,
                           enabling dynamic weekly repricing and 52
                           premium revenue events per year.

  Regulatory Alignment     Designed to help platforms meet obligations
                           under the Rajasthan Gig Workers Act (2023) and
                           Karnataka Gig Workers Bill (2024)
                           \[36\]\[37\].
  -----------------------------------------------------------------------

[]{#sec12 .anchor}**12. Limitations and Future Improvements**

**Known Limitations**

  -------------------------------------------------------------------------
  **Limitation**   **Description**             **Mitigation in Current
                                               Design**
  ---------------- --------------------------- ----------------------------
  Basis Risk       Mismatch between actual     Mitigated by multi-level
                   income loss and fixed       severity bands (D2), but not
                   parametric payout. A        fully eliminated. By design:
                   worker\'s actual loss may   full indemnification is not
                   differ from the predefined  the model\'s goal.
                   payout.                     

  Data Dependency  Model accuracy depends on   System designed to function
                   platform data availability. with self-reported data as
                   In early deployment,        fallback. 7-platform
                   historical training data    cross-dataset reduces
                   may be limited or           single-source dependence.
                   inconsistent across         
                   platforms.                  

  GPS Spoofing     Adversarial actors may      Stage 2 LSTM and Stage 3
  Evolution        develop more sophisticated  graph-based detection
                   spoofing methods that       provide adaptive layers;
                   challenge the deterministic weekly online retraining
                   fraud layer.                allows the system to evolve
                                               with attacker strategies.

  Coverage         Health, life, accident, and Scope kept narrow to ensure
  Exclusions       vehicle repair claims are   actuarial sustainability.
                   explicitly out of scope.    Expansion considered for
                   Workers face additional     Phase 3 and beyond.
                   vulnerabilities beyond      
                   income disruption.          

  Urban            Initial deployment targets  Phased rollout design
  Concentration    Tier-1 cities where API     accounts for this; Tier-2
                   data coverage is reliable.  expansion planned in Phase
                   Tier-2 and rural coverage   2.
                   may be limited.             
  -------------------------------------------------------------------------

**Future Improvements (Planned for Phase 2 and Beyond)**

-   Seasonal model recalibration: Automated re-training of AI models at
    the onset of monsoon, summer, and winter seasons to maintain
    prediction accuracy.

-   Expanded platform coverage: Onboarding of additional Q-commerce and
    hyperlocal delivery platforms beyond the current seven.

-   Real-time claim audit trail: Immutable, time-stamped audit logs
    accessible to both insurer and worker for full transparency.

-   Tier-2 city expansion: API infrastructure and manager intelligence
    layer adaptation for smaller urban centres.

-   Health and accident micro-coverage: Exploratory integration of basic
    accident cover as an add-on to the income protection plan.

-   GCN upgrade (Phase 3): Transition from Louvain community detection
    to PyTorch Geometric GCN for more sophisticated ring fraud detection
    with learned edge weights.

-   Worker dashboard: A mobile-native earnings and coverage view,
    enabling workers to track policy status, trigger events, and payout
    history in real time.

[]{#sec13 .anchor}**13. Technology Stack**

The technology stack is designed for real-time data ingestion,
low-latency inference, and scalable payout execution. Full stack details
will be provided in Phase 2 submission.

  -----------------------------------------------------------------------
  **Layer**        **Technology / Framework**   **Purpose**
  ---------------- ---------------------------- -------------------------
  Machine Learning Python, scikit-learn (Random Income prediction and
                   Forest), XGBoost             disruption risk
                                                classification
                                                \[13\]\[16\]

  Fraud Detection: Python, TensorFlow / PyTorch Behavioral sequence
  Behavioral       (LSTM)                       analysis for individual
                                                spoofing detection \[26\]

  Fraud Detection: Python, NetworkX (Louvain);  Community detection for
  Graph            Phase 3: PyTorch Geometric   coordinated ring fraud
                                                \[29\]\[30\]

  Fraud Decision   LLM Agent with RAG (Phase    Edge case resolution and
  Layer            2+)                          audit documentation

  Data Ingestion   OpenWeatherMap API, AQICN    Real-time environmental
                   API, Google Maps Traffic     and operational data
                   API, IMD/CPCB feeds          \[8\]\[9\]\[18\]

  Payment          Razorpay / UPI (sandbox for  Automated payout transfer
  Execution        Phase 1)                     

  Backend / API    Python (FastAPI / Django)    Policy management,
  Layer                                         trigger evaluation, fraud
                                                orchestration

  Database         PostgreSQL / MongoDB (TBD    Worker profiles, policy
                   Phase 2)                     records, audit logs

  Explainability   SHAP (SHapley Additive       Audit-ready feature
                   exPlanations)                attribution for fraud
                                                decisions \[31\]
  -----------------------------------------------------------------------

[]{#sec14 .anchor}**14. Final Conclusion**

India\'s gig delivery workforce is one of the fastest-growing labour
segments in the world, yet it operates without any structured income
protection. When rainfall floods a city, temperatures spike during a
heatwave, or air quality reaches hazardous levels, millions of workers
simply lose income with no recourse, no savings, and no safety net.

BHIMA ASTRA changes that. By combining AI-driven risk pricing with fully
automated parametric payouts, it delivers income protection that is
immediate, affordable, and scalable: matching the income rhythm of
weekly gig work rather than the annual cycles of traditional insurance.

The model succeeds across all three stakeholder dimensions
simultaneously. Workers receive automatic payouts without filing a
claim. Platforms gain a welfare benefit that aids retention and
regulatory compliance at zero premium cost. Insurers gain a
high-frequency, low-overhead revenue stream with actuarially sustainable
loss ratios.

Five design differentiators, including cross-platform AI training,
multi-level severity bands, manager-as-intelligence for social
disruptions, policy portability, and composite disruption scoring,
directly address the core failure modes of parametric insurance: basis
risk, single-signal brittleness, and platform dependency \[1\]-\[12\].

The fraud architecture ensures that the automated payout model is not
exploitable at scale. By resolving approximately 80% of claims instantly
at the rule layer while deploying adaptive behavioral and graph-based
detection for the remainder, the system protects the liquidity pool
without penalising genuine workers \[22\]-\[31\].

Phase 1 pilot projections demonstrate financial viability from as few as
2,000-2,500 policyholders, with loss ratios converging to the 50-65%
actuarial target as the risk pool scales. The path from pilot to Rs. 39
Crore in annual premiums across three platforms and 100,000 workers is a
realistic, evidence-based roadmap.

  -----------------------------------------------------------------------
  **Closing Statement**

  This is not a proof of concept. It is a deployable, actuarially
  grounded, and research-backed

  parametric income protection system.

  Built for the 23.5 million gig workers who will be delivering for
  India\'s Q-commerce economy by 2030,

  and who currently have nothing.
  -----------------------------------------------------------------------

**References**

All references below are Q-commerce and directly related research used
in this document.

  -----------------------------------------------------------------------------------------------
  **Index**   **Paper Name**            **Reference Details**
  ----------- ------------------------- ---------------------------------------------------------
  \[1\]       \[Swiggy Instamart        Swiggy Instamart Delivery Partner Ecosystem (Internal
              Delivery Partner          Research Document)
              Ecosystem\]               

  \[2\]       \[BigBasket Now Delivery  BigBasket Now Delivery Partner Ecosystem (Internal
              Partner Ecosystem\]       Research Document)

  \[3\]       \[Flipkart Minutes        Flipkart Minutes Delivery Partner Ecosystem (Internal
              Delivery Partner          Research Document)
              Ecosystem\]               

  \[4\]       \[Amazon Now Delivery     Amazon Now Delivery Partner Ecosystem (Internal Research
              Partner Ecosystem\]       Document)

  \[5\]       \[FreshToHome Express     FreshToHome Express Delivery Partner Ecosystem (Internal
              Delivery Partner          Research Document)
              Ecosystem\]               

  \[6\]       \[Zepto Delivery Partner  Zepto Delivery Partner Ecosystem (Internal Research
              Ecosystem\]               Document)

  \[7\]       \[Blinkit Delivery        Blinkit Delivery Partner Ecosystem (Internal Research
              Partner Ecosystem\]       Document)

  \[8\]       \[IMD Rainfall            India Meteorological Department (IMD). Rainfall
              Classification and        Classification and Heatwave Criteria.
              Heatwave Criteria\]       https://mausam.imd.gov.in/

  \[9\]       \[CPCB National AQI       Central Pollution Control Board (CPCB). National AQI
              Classification Standard\] Classification Standard. https://cpcb.nic.in/

  \[10\]      \[Curfews Protests and    Redl, C., and Hlatshwayo, S. (2021). Forecasting Social
              Social Unrest             Unrest: A Machine Learning Approach. IMF Working Papers,
              Forecasting\]             2021/263.

  \[11\]      \[Zepto GPA Group         PARAMETERS.docx: Zepto GPA Group Insurance Model
              Insurance and Platform    (Internal); CompareC over. https://comparecover.in/
              Insurance\]               

  \[12\]      \[GPS and Composite       GPS and Data Flow Design Document: Composite Disruption
              Disruption Score Design\] Score (Internal Research Document)

  \[13\]      \[Random Forests\]        Breiman, L. (2001). Random Forests. Machine Learning, 45,
                                        5-32. https://doi.org/10.1023/A:1010933404324

  \[14\]      \[Predicting Salaries     Eichinger, F., and Mayer, R. (2022). Predicting Salaries
              with Random-Forest        with Random-Forest Regression. In Data Science Analytics
              Regression\]              and Applications. Springer.

  \[15\]      \[Supervised Machine      Galar, C., et al. (2022). Supervised Machine Learning
              Learning for Alumni       Predictive Analytics for Alumni Income. Journal of Big
              Income\]                  Data, 9(1).

  \[16\]      \[XGBoost: A Scalable     Chen, T., and Guestrin, C. (2016). XGBoost: A Scalable
              Tree Boosting System\]    Tree Boosting System. Proc. 22nd ACM SIGKDD, 785-794.
                                        https://doi.org/10.1145/2939672.2939785

  \[17\]      \[XGBoost for Insurance   Fauzan, M. A., and Murfi, H. (2018). The Accuracy of
              Claim Prediction\]        XGBoost for Insurance Claim Prediction. IJASCA, 10(2).

  \[18\]      \[Google Maps Platform    Google Maps Platform. Routes and Traffic API
              Routes and Traffic API\]  Documentation.
                                        https://developers.google.com/maps/documentation/routes

  \[19\]      \[AI-Driven Dynamic       AccelTree (2025). AI-Driven Dynamic Premium Pricing in
              Premium Pricing in        Insurance. https://acceltree.com/white-papers/
              Insurance\]               

  \[20\]      \[Dynamic Pricing Gives   Insurance Thought Leadership (2024). Dynamic Pricing
              Insurers a Competitive    Gives Insurers a Competitive Edge.
              Edge\]                    https://www.insurancethoughtleadership.com/

  \[21\]      \[Dynamic Pricing in      SimpleSolve (2025). Dynamic Pricing in Insurance Using AI
              Insurance Using AI\]      and Predictive Analytics.
                                        https://www.simplesolve.com/blog/

  \[22\]      \[Intelligent Financial   West, J., and Bhattacharya, M. (2016). Intelligent
              Fraud Detection\]         Financial Fraud Detection: A Comprehensive Review.
                                        Computers and Security, 57, 47-66.

  \[23\]      \[Isolation Forest\]      Liu, F. T., Ting, K. M., and Zhou, Z. H. (2008).
                                        Isolation Forest. IEEE ICDM, 413-422.
                                        https://doi.org/10.1109/ICDM.2008.17

  \[24\]      \[Graph-Based Anomaly     Pourhabibi, T., et al. (2020). Fraud Detection: A
              Detection for Fraud\]     Systematic Literature Review of Graph-Based Anomaly
                                        Detection. Decision Support Systems, 133, 113303.

  \[25\]      \[XGBoost for Insurance   Fauzan, M. A., and Murfi, H. (2018). The Accuracy of
              Claim Prediction          XGBoost for Insurance Claim Prediction. IJASCA, 10(2).
              (Fauzan)\]                

  \[26\]      \[Long Short-Term         Hochreiter, S., and Schmidhuber, J. (1997). Long
              Memory\]                  Short-Term Memory. Neural Computation, 9(8), 1735-1780.
                                        https://doi.org/10.1162/neco.1997.9.8.1735

  \[27\]      \[AI-Driven Dynamic       AccelTree (2025). AI-Driven Dynamic Premium Pricing in
              Premium Pricing           Insurance (White Paper).
              (AccelTree)\]             

  \[28\]      \[Semi-Supervised Graph   Wang, D., et al. (2019). A Semi-Supervised Graph
              Attentive Network for     Attentive Network for Financial Fraud Detection. IEEE
              Fraud\]                   ICDM, 598-607.

  \[29\]      \[Fast Unfolding of       Blondel, V. D., et al. (2008). Fast Unfolding of
              Communities in Large      Communities in Large Networks. J. Stat. Mech., P10008.
              Networks\]                

  \[30\]      \[Semi-Supervised         Kipf, T. N., and Welling, M. (2017). Semi-Supervised
              Classification with       Classification with Graph Convolutional Networks. ICLR.
              GCNs\]                    https://arxiv.org/abs/1609.02907

  \[31\]      \[SHAP: A Unified         Lundberg, S. M., and Lee, S. I. (2017). A Unified
              Approach to Interpreting  Approach to Interpreting Model Predictions. NeurIPS, 30.
              Model Predictions\]       https://arxiv.org/abs/1705.07874

  \[32\]      \[Economic Lives of       Brailovskaya, V., et al. (2023). Economic Lives of
              Digital Platform Gig      Digital Platform Gig Workers: India. IDinsight.
              Workers India\]           https://www.idinsight.org/

  \[33\]      \[CGAP on Embedded        CGAP. Embedded Insurance Adoption and Bancassurance
              Insurance Adoption\]      Models. (Internal Reference)

  \[34\]      \[World Bank Stories of   World Bank (2021). Stories of Climate Resilience: Jan
              Climate Resilience Jan    Sahas parametric pilot, India.
              Sahas\]                   

  \[35\]      \[Future of India\'s Gig  Drishti IAS (2024). Future of India\'s Gig Work.
              Work\]                    https://www.drishtiias.com/

  \[36\]      \[Rajasthan               Rajasthan Platform-Based Gig Workers Act, 2023.
              Platform-Based Gig        https://prsindia.org/
              Workers Act 2023\]        

  \[37\]      \[Karnataka Gig Workers   Karnataka Gig Workers Bill, 2024; Union Budget 2025.
              Bill 2024\]               

  \[38\]      \[Swiggy Accident Cover   Rathi, A., et al. Understanding Food Delivery Platform:
              and Welfare Programs\]    Delivery Persons\' Perspective. TISS Hyderabad. (Internal
                                        Research)
  -----------------------------------------------------------------------------------------------
