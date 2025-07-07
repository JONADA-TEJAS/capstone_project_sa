# capstone_project_sa
#  Dynamic Pricing for Urban Parking Lots

This project presents an intelligent pricing system for urban parking lots using dynamic, demand-based, and competitive strategies. The goal is to **maximize revenue** while ensuring efficient parking distribution across the city.

---

##  Problem Statement

Urban parking is limited and often under-optimized. A static pricing system cannot account for:

- Real-time occupancy
- Local traffic conditions
- Special events
- Nearby lot competition

Our goal: **Design dynamic pricing models that adapt in real-time** to these factors, maximizing revenue and balancing lot usage.

---

##  Dataset

- Source: Provided `.csv` file with ~58,000 parking entries.
- Features:
  - `SystemCodeNumber` (parking lot ID)
  - `Latitude`, `Longitude`
  - `Capacity`, `Occupancy`, `QueueLength`
  - `VehicleType`, `TrafficConditionNearby`, `IsSpecialDay`
  - Timestamps (`LastUpdatedDate`, `LastUpdatedTime`)

We processed and merged these fields into a clean real-time-ready dataset (`clean_dataset_final.csv`).

---

##  Pricing Models Implemented

###  Model 1: Linear Occupancy-Based Pricing
- Formula: `Price = Base + α × (Occupancy / Capacity)`
- Simple, responsive to real-time usage

###  Model 2: Demand-Based Pricing
- Factors:
  - Occupancy rate
  - Queue length
  - Traffic level
  - Vehicle type (Car, Bike, Truck)
  - Special day
- Formula: 

###  Model 3: Competitive Pricing
- Enhances Model 2 by checking nearby lots (within 2 km)
- If:
- Lot is full and neighbors are cheaper → decrease price (encourage rerouting)
- Neighbors are more expensive → increase price
- Goal: simulate supply-demand competition across city

---

##  Real-Time Streaming with Pathway

We used the **Pathway library** to simulate real-time streaming and compute prices live.

- Parsed each row as a real-time event
- Applied all 3 models on the fly
- Output written to `/content/output.csv` for downstream evaluation

---

##  Revenue Evaluation

We calculated revenue per lot and average revenue per model:

| Pricing Model | Average Revenue |
|---------------|-----------------|
| **Model 1**   | ₹8141.92         |
| **Model 2**   | ₹7555.18         |
| **Model 3**   | ₹7737.10         |

 Model 1 gave the highest average revenue, but **Model 3 is more fair and adaptable**, especially in real-world competitive settings.

---

##  Visualizations

###  Revenue Comparison

Bar chart showing average revenue per model:

![image](https://github.com/user-attachments/assets/cbcfc35a-b885-40ad-9fb9-cf579170c07b)


###  Bokeh Plot (Interactive)

Dynamic price trends over time for a selected lot:

![image](https://github.com/user-attachments/assets/86bd50cc-881a-40a2-9edc-a4839884aefc)


---

##  Project Structure

---

##  Key Takeaways

- Dynamic pricing boosts responsiveness and fairness
- Model 2 reacts well to demand features
- Model 3 introduces competition-aware pricing
- Pathway enables scalable real-time execution

---

##  Tools & Tech

-  Python, Pandas, NumPy
-  Pathway (real-time streaming)
-  Matplotlib, Bokeh (visualizations)

---

##  Future Improvements

- Incorporate weather and event APIs
- Implement reinforcement learning (RL-based dynamic pricing)
- Build a live Streamlit dashboard for monitoring

---

##  Author

** Jonada Tejas **  
Data Science & ML Enthusiast  
 [teju6342@gmail.com]

---

>  “Smart parking isn't just about finding a spot — it's about **dynamic, data-driven efficiency**.”

