https://github.com/user-attachments/assets/2b770bef-8d42-43bd-9e2c-188191848529

https://github.com/user-attachments/assets/b8cdd3ae-bdc7-461e-847f-8634f9b3e742

# 🩺 Clinical Screening Triage & Epidemiological Insights Hub

An enterprise-grade, interactive medical data analytics application built in **Power BI Desktop**. This project bypasses generic business reporting models to engineer a **Clinical Decision Support System (CDSS)** using real-world public health data. It automatically parses hematological biomarkers into diagnostic profiles based on global healthcare rules.

---

## 🚀 Live Visual Architecture Preview
*A look at the production-grade dashboard canvas layouts engineered during this implementation:*

### 🖥️ Page 1: Clinical Screening Hub
* **Core Function:** Live operational board for practitioners to instantly evaluate patient anomalies, locate risk clusters, and view an urgent patient registry.
* **UX/UI Model:** Features a clean, custom-built 3D Glassmorphic / Neumorphic dashboard card configuration designed to reduce clinical fatigue in high-stress hospital environments.

### 📊 Page 2: Epidemiological Trends & Demographic Diagnostics
* **Core Function:** Population health analytics tracking how active blood profiles, internal cell dimensions, and mean immune metrics distribution behave across pediatric, adult, and geriatric cohorts.

---

## 🧬 Medical Analytics Logic & Feature Engineering (DAX)

Instead of using basic visualizations, this project uses specialized diagnostic logic gates built with **Data Analysis Expressions (DAX)** to replicate real-world physician triage decisions.

### 1️⃣ Advanced Anemia Type Classifier (Calculated Column)
This custom script maps international diagnostic baselines established by the **World Health Organization (WHO)** and the **National Institutes of Health (NIH)**. It tracks intersecting metrics across `Gender`, `Hemoglobin`, and `MCV` (Mean Corpuscular Volume) to classify complex anemias:

```dax
Anemia_Type_Classifier = 
VAR IsAnemic = 
    IF(
        (blood_count_dataset[Gender] = "Female" && blood_count_dataset[Hemoglobin] < 12.0) || 
        (blood_count_dataset[Gender] = "Male" && blood_count_dataset[Hemoglobin] < 13.5), 
        1, 
        0
    )
RETURN
IF(
    IsAnemic = 1,
    IF(
        blood_count_dataset[MCV] < 80, 
        "Iron Deficiency Anemia (Microcytic)", 
        "Chronic Disease Anemia (Normocytic)"
    ),
    "Healthy / Normal Blood Profile"
)
```

### 2️⃣ Pathological Infection Screening Rule (Calculated Column)
Flags acute inflammatory or physiological immune alerts inside the registry by cross-verifying absolute white blood cell values against international standard units:

```dax
Infection_Profile = 
IF(
    blood_count_dataset[White_Blood_Cells] > 11000, 
    "Active Infection / High Risk", 
    "Normal / Immune Stable"
)
```

---

## 🛠️ Data Engineering & ETL Pipeline (Power Query)
Before building any visual models on the canvas, the raw source dataset was optimized for high query performance and reporting scale:
* **Unique Index Generation:** Formatted an explicit serialization rule (`From 1`) to assign a structured `Patient_ID` across thousands of records, allowing individual data points to scatter freely.
* **Data Typology Standardization:** Mapped baseline text attributes into solid integer keys and forced all raw counts (`WBC`, `Platelets`) to strictly compile into decimal numbers.
* **Numeric Normalization:** Found extreme scientific anomalies (like machine artifacts showing `5.39761E-79` in the Basophil parameters) and applied a fixed rounding matrix to reduce them to clear `0` baselines.

---

## 🎨 Professional Enterprise UI/UX Specifications
The entire interface overrides Power BI's default design styles by injecting a comprehensive **JSON UI Schema Blueprint**:
* **Rounded Contours:** Smoothly curves sharp borders (`"radius": 12`) to blend visual panels together seamlessly.
* **3D Depth Projection:** Utilizes custom outer drop-shadow presets (`blur: 15, distance: 6`) against a cool corporate gray backdrop (`#F0F4F8`) to simulate a floating glass effect.
* **Corporate Text Classing:** Formats text headers globally into Deep Trust Navy (`#1A365D`) and switches tabular charts into high-end executive grids with solid column accent borders.

---

## 📂 Repository Pipeline & Setup Instruction
1. Clone this repository locally.
2. Load the optimized raw clinical data sheet `.csv` inside Power BI Desktop.
3. Import the `3D_Corporate_Medical_Master.json` canvas design profile layout sheet to apply themes.
4. Execute the calculation expressions above to initialize the screening metrics.

---

*Footnote Disclaimer: This project is built for informational and educational portfolio demonstration purposes only. All underlying patient records are open-source, fully anonymized public records. It is not intended for active real-world clinical diagnosis or personalized medical advice.*
