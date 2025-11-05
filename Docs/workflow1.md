# 🧩 SupplyPlan — Inventory & Reorder Optimization Micro-SaaS

## 🗓️ Phase 1: MVP (8 Weeks)

### Week 1: Setup
- [ ] Create repo + environment (FastAPI + PostgreSQL)
- [ ] Generate or collect dummy data (CSV)
- [ ] Build schema: SKU, demand, lead_time, cost

### Week 2–3: Core Optimization
- [ ] Implement EOQ formula
- [ ] Implement Reorder Point formula
- [ ] Run Monte Carlo simulation for service levels
- [ ] Return JSON results per SKU

### Week 4: LLM Explanation Layer
- [ ] Connect OpenAI API
- [ ] Prompt engineering for inventory summary
- [ ] Add endpoint `/explain` that returns human-readable report

### Week 5–6: Frontend Dashboard
- [ ] Build simple Streamlit dashboard:
  - File upload (CSV)
  - Table of SKUs with EOQ, ROP, Service Level
  - Visualization: Service Level vs Safety Stock
- [ ] Add “Generate Report” button → calls `/explain`

### Week 7: Deployment
- [ ] Containerize with Docker
- [ ] Deploy to Render or Railway
- [ ] Add sample login + demo data

### Week 8: Polish
- [ ] Add PDF export + alerts
- [ ] Collect feedback
- [ ] Prep for Stripe integration

---

## ⚙️ Technical Architecture

**Backend:** FastAPI (Python)  
**Optimization:** NumPy, Pandas, SciPy  
**Simulation:** Monte Carlo engine  
**AI Layer:** OpenAI GPT model  
**Frontend:** Streamlit (MVP) → React (v2)  
**Database:** PostgreSQL (Supabase optional)  
**Hosting:** Render/Railway  
**Payments:** Stripe

---

## 🔁 Example API Flow

1. `POST /upload` → upload CSV → store in DB  
2. `POST /optimize` → compute EOQ, ROP, service level  
3. `POST /explain` → send results to LLM → return human text  
4. `GET /dashboard` → retrieve computed results  
5. `POST /alert` → send email/WhatsApp if reorder threshold breached

---

## 🧠 Data Fields

| Field | Type | Description |
|--------|------|-------------|
| sku | string | Item ID |
| avg_demand | float | Average daily demand |
| demand_std | float | Demand variability |
| lead_time | float | Average supplier lead time (days) |
| holding_cost | float | Cost per unit per year |
| ordering_cost | float | Cost per order |
| eoq | float | Computed optimal order quantity |
| reorder_point | float | Point at which to reorder |
| service_level | float | Simulated probability of no stockout |
| explanation | text | LLM-generated summary |

---

## 🚀 Future Upgrades
- [ ] Add time series forecasting (Prophet, ARIMA)
- [ ] Add supplier reliability metrics
- [ ] Add WhatsApp / Slack notification bot
- [ ] Multi-warehouse management
- [ ] Auto-order integration via API
