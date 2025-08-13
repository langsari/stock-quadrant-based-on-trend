# stock-quadrant-based-on-trend
Identify market leaders and laggards with a model that classifies a stock's trend into distinct phases (e.g., Superuptrend, Sideway, Crash Trend) based on momentum and key moving averages.

# 📈 Stock Quadrant Divining Based on Trend

ระบบวิเคราะห์และจำแนกสภาพตลาดหุ้นออกเป็น 5 สถานะ:
- **Super Bullish**
- **Uptrend**
- **Sideway**
- **Downtrend**
- **Crash**

พร้อมแนะนำการกระทำ (Buy / Hold / Sell / Avoid) และคำนวณ **EMA** ที่เหมาะสมกับหุ้นรายตัว
เพื่อช่วยในการตัดสินใจลงทุนอย่างมีระบบ

---

## 🔍 Features
- จำแนก Trend Regime แบบเรียลไทม์จากข้อมูลราคาหุ้น
- ระบุ Action แนะนำ (Buy / Hold / Sell / Avoid)
- คำนวณ **EMA ที่เหมาะสม** กับแต่ละหุ้นโดยใช้ ATR% และการ Optimize
- รองรับทั้ง **Rule-based** และ **Machine Learning Model**
- ระบบ Backtest พร้อมการวัดผล Sharpe, Sortino, Max Drawdown, Hit Ratio
- Visualization กราฟราคาพร้อมจุดเข้า/ออกและสีพื้นหลังตาม Regime

---

## 📊 Trend Regime Definitions
ใช้การคำนวณ **Slope** (โมเมนตัม) และ **Volatility** (ความผันผวน) บนหน้าต่าง 20 และ 60 วัน  
ผสมกับค่า **EMA**, **ADX**, **ATR**, **Bollinger Band Width**, และ **Max Drawdown**

| Regime         | Condition                                                                 |
|----------------|---------------------------------------------------------------------------|
| Crash          | S ≤ p10 & V ≥ p70 & DD ≥ 20%                                               |
| Downtrend      | S ≤ p30 & Close < EMA_long & ADX ≥ 20                                      |
| Sideway        | \|S\| ≤ p40 & ADX < 20 & BandWidth ≤ p40                                   |
| Uptrend        | S ≥ p60 & Close > EMA_long & ADX ≥ 20                                      |
| Super Bullish  | S ≥ p80 & EMA50 > EMA200 & ADX ≥ 25                                        |

> **S** = 0.6·Slope(20) + 0.4·Slope(60)  
> **V** = Volatility 20 วัน หรือ ATR%  
> **DD** = Max Drawdown 60–120 วัน

---

## 📦 Installation

```bash
git clone https://github.com/yourusername/stock-quadrant-divining.git
cd stock-quadrant-divining
pip install -r requirements.txt
