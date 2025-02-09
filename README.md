![Image](https://github.com/user-attachments/assets/2ae3b9e8-6d7b-4006-8192-74b80147c73d)

# **🏊 The Art & Science of Medley Relay Optimization 🏆**

## **The Challenge: Selecting the Best Relay Lineup 🏅**
At first, picking a relay lineup seemed straightforward—just put the fastest swimmer in each stroke. When I first looked at the problem, I thought it would be easy. But while the concept is simple, finding the optimal lineup quickly proved to be far more challenging than expected. The best lineup maximizes time savings, and an optimized relay can make or break a championship race.

One of the biggest challenges is that **your fastest swimmer in one stroke is often also the fastest in another.** While this might sound like a good problem to have, it creates tough decisions—choosing where they provide the **biggest time advantage** while ensuring the other strokes don’t suffer.

## **🏊‍♂️ The Example: Understanding Trade-Offs in Relay Assignments**
The following is **real data** from an actual relay lineup, with names changed and times slightly modified. This example highlights how certain swimmers excel in multiple strokes, requiring careful decision-making.

### **🔢 Try It Yourself: Optimize the Relay Before Reading On**
Below, swimmers' times are listed **by stroke** rather than by swimmer. Try selecting the best lineup while ensuring each swimmer only competes in one event. 

#### **Backstroke Times: ⏱️**
- **Kyle**: 22.43
- **Chad**: 24.77
- **Jake**: 25.86
- **Steve**: 27.05
- **Ryan**: 32.13

#### **Breaststroke Times: ⏱️**
- **Jake**: 26.80
- **Ryan**: 29.04
- **Chad**: 32.46
- **Kyle**: 33.21
- **Steve**: 37.05

#### **Butterfly Times: ⏱️**
- **Jake**: 23.66
- **Kyle**: 24.57
- **Steve**: 27.40
- **Ryan**: 28.79
- **Chad**: 29.69

#### **Freestyle Times: ⏱️**
- **Kyle**: 20.93
- **Chad**: 21.60
- **Jake**: 21.92
- **Ryan**: 24.91

Take a moment to pick the best lineup before reading on. 

### **The Initial Problem: Dual Strengths in Multiple Strokes**
At the start, we identify that two swimmers, Kyle and Jake, stand out as the fastest in multiple strokes:

- **Kyle** is the fastest in both **Backstroke** and **Freestyle**.
- **Jake** is the fastest in both **Breaststroke** and **Butterfly**.

Since each swimmer can only race one leg of the relay, we must determine how to assign them in a way that maximizes the team’s total speed. Simply placing each swimmer in their strongest stroke does not always yield the best outcome—we also need to consider their relative advantage over the next fastest swimmer in each stroke.

### **Step 1: Choosing Kyle’s Stroke**
Since Kyle is the fastest in both Backstroke and Freestyle, we compare his time advantage in each:

- In **Backstroke**, Kyle is **2.34 seconds faster** than the next fastest swimmer, Chad.
- In **Freestyle**, Kyle is only **0.67 seconds faster** than Chad.

Clearly, Kyle’s advantage in Backstroke is much greater, making it the smarter choice for him. This also settles Chad in Freestyle, as he is the next-best option.

### **Step 2: Choosing Jake’s Stroke**
Jake is the fastest in both Breaststroke and Butterfly, so we compare his advantage in each:

- In **Breaststroke**, Jake is **2.24 seconds faster** than Kevin.
- In **Butterfly**, Jake is **0.91 seconds faster** than Kyle.

At first, placing Jake in Breaststroke seems like the right decision. However, since we already assigned Kyle to Backstroke, we must find the next best option for Butterfly—which would be Steve.

This presents a problem:

- Jake is **3.74 seconds faster** than Steve in Butterfly, which is a massive gap compared to his **2.24-second advantage** in Breaststroke over Kevin.

### **Step 3: Making the Final Assignments**
Since replacing Jake in Butterfly would create a major weakness, the best solution is:

### **🏊‍♂️ Final Relay Lineup:**
✅ **Backstroke:** Kyle (biggest advantage over next fastest)  
✅ **Breaststroke:** Kevin (second-best option, allowing Jake to stay in Fly)  
✅ **Butterfly:** Jake (massive time gap over any other option)  
✅ **Freestyle:** Chad (next best after Kyle)  

## **📊 Using Data to Optimize Your Relay Selection**
### **🏆 The SwimSwam Medley Relay Calculator**
The **[SwimSwam Medley Relay Calculator](https://swimswam.com/medley-relay-calculator/)** automates relay optimization. It evaluates all **possible permutations**, ensuring the best lineup with no guesswork. 

### **⚠️ The Drawback: Manual Data Entry**
The downside? **Manually inputting times is time-consuming** and **prone to human error**. A small typo could cost seconds and ruin a well-planned relay.

## **📊 Building an Optimized Medley Relay in Excel**
Instead of manually entering data, **Excel Solver** allows for a seamless, automated relay selection based on meet data. Since coaches usually receive times in **CSV or Excel format**, this method enables **copy-pasting directly**, eliminating errors.

### **📂 I Did Most of the Work—Just Add Times and Fix Solver!**
In the files above, I attached the relay data in **CSV and Excel format**, so you don’t have to build anything from scratch. Just add your swimmers' times, fix Solver settings, and you're good to go! If you don't see a Solver button in your Excel menu, scroll down for the fix.

### **📑 Step 1: Organizing Swimmer Data in Excel**
Update the table already built in the file where:

✅ **Rows represent swimmers**  
✅ **Columns represent stroke times**  
✅ **Binary selection columns (0 or 1) indicate which stroke they are assigned**  

| Swimmer  | 50 Y Back | 50 Y Breast | 50 Y Fly | 50 Y Free | Back (0/1) | Breast (0/1) | Fly (0/1) | Free (0/1) |
|----------|----------|------------|----------|----------|------------|------------|--------|--------|
| Kyle | **22.43** | 33.21 | 24.57 | 20.93 | **1** | 0 | 0 | 0 |
| Chad | 24.77 | 32.46 | 29.69 | **21.60** | 0 | 0 | 0 | **1** |
| Jake | 25.86 | **26.80** | **23.66** | 21.92 | 0 | 0 | **1** | 0 |
| Steve | 27.05 | 37.05 | 27.40 | - | 0 | 0 | 0 | 0 |
| Ryan | **31.85** | **29.04** | **28.51** | **24.63** | 0 | **1** | 0 | 0 |

### **⚙️ Step 2: Running Solver**
- Open **Excel Solver** (Data → Solver).  
- Set the **objective cell** to minimize **total relay time**.  
- Add constraints:  
  ✅ Each swimmer’s stroke selection must sum to **1**.  
  ✅ Each stroke must have **exactly one** selected swimmer.  
  ✅ Binary constraints (only 0s and 1s in selection columns).  
- Click **Solve**, and Excel will provide the optimal lineup.  

## **🚀 Setting Up Excel Solver**
Before using Solver, it needs to be enabled:

✅ Open Excel and go to **File → Options → Add-ins**.  
✅ In the **Manage** box, select **Excel Add-ins** and click **Go**.  
✅ Check **Solver Add-in** and click **OK**.  
✅ Solver will now appear under **Data → Solver**.  

### **🏆 Conclusion: Why This Approach Works**
By implementing this system in Excel, coaches can:  
✔ **Automate relay selection** without manual input.  
✔ **Reduce human error**, ensuring the best lineup.  
✔ **Quickly adjust for meet conditions**, making real-time decisions easy.  


