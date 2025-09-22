# 🏥 Automated Medical Report Summarizer & Explainer  
Fine-tuning **LLaMA 3 (8B)** with **PEFT + QLoRA** to generate structured **SOAP medical summaries** from patient–clinician dialogues.  

---

## 📌 Project Overview  
This project develops an **AI-powered system** that converts lengthy medical dialogues into concise, structured **SOAP (Subjective, Objective, Assessment, Plan) reports**. The model was fine-tuned on the **OMI Health medical dialogue dataset** and optimized using **LoRA/QLoRA** techniques to handle large-scale training efficiently.  

The pipeline also integrates evaluation metrics (**ROUGE** and **BERTScore**) to measure summarization quality and provides a foundation for building patient-friendly medical report explainers.  


---

## 🛠️ Pipeline Overview  

Below is a visual representation of how the **Automated Medical Report Summarizer & Explainer** pipeline works:

![Pipeline Overview](![WhatsApp Image 2025-09-22 at 19 02 18_c7b41fe7](https://github.com/user-attachments/assets/68670023-b5f5-42d9-a7b3-c9e15f3baf1a)
)  
*Figure: From raw doctor–patient dialogues → Generated SOAP notes → Simplified patient-friendly summaries.*

**Pipeline Steps:**  
1. **Input Dialogue** – Raw doctor–patient conversation.  
2. **Preprocessing** – Clean text, standardize speaker tags (`[Doctor]`, `[Patient]`), tokenize.  
3. **Model Inference** – Fine-tuned **LLaMA 3 (8B)** generates structured SOAP notes.  
4. **Postprocessing / Explanation** – Summarize and simplify SOAP notes into patient-friendly summaries.  
5. **Evaluation** – Compare generated SOAP notes to references using **ROUGE** and **BERTScore**.  



---

## 🚀 Features  
- Fine-tuned **Meta-LLaMA 3 8B** model for dialogue-to-SOAP summarization  
- **LoRA & QLoRA** for parameter-efficient training  
- Data preprocessing with text cleaning + role tagging (`[Doctor]`, `[Patient]`)  
- Support for **Hugging Face datasets & transformers**  
- Evaluation using **ROUGE** and **BERTScore**  
- Modular notebook for **training, inference, and evaluation**  

---

## 📂 Dataset  
- **Source**: [OMI Health – Medical Dialogue to SOAP Summary](https://huggingface.co/datasets/omi-health/medical-dialogue-to-soap-summary)  
- **Size**: ~10k dialogues with corresponding SOAP summaries  
- **Structure**:  
  - `dialogue`: raw doctor–patient conversation  
  - `soap`: corresponding structured SOAP note  

---

## 🧠 Model Architecture  
- **Base Model**: Meta-LLaMA 3 (8B)  
- **Fine-tuning**:  
  - **LoRA/QLoRA** for efficient adaptation  
  - **PEFT** integration for low-resource environments  
- **Evaluation Metrics**: ROUGE, BERTScore  

---

## ⚙️ Installation  

```bash
# Clone the repository
git clone https://github.com/your-username/medical-report-summarizer.git
cd medical-report-summarizer
```

## 📊 Results  

### 📈 Evaluation Metrics  
- **Average ROUGE-1 F1**: 0.4703  
- **Average ROUGE-2 F1**: 0.1897  
- **Average ROUGE-L F1**: 0.3008  
- **Average BERTScore F1**: 0.6934  

### 📝 Qualitative Example  
**Input Dialogue (Simplified)**:
Doctor: Hello, can you please tell me about your past medical history?
Patient: Hi, I don't have any past medical history.
Doctor: Okay. What brings you in today?
Patient: I've been experiencing painless blurry vision in my right eye for a week now. I've also had intermittent fevers, headache, body aches, and a nonpruritic maculopapular rash on my lower legs for the past 6 months.
Doctor: Thank you for sharing that. Have you had any other symptoms such as neck stiffness, nausea, vomiting, Raynaud's phenomenon, oral ulcerations, chest pain, shortness of breath, abdominal pain, or photosensitivity?
Patient: No, only an isolated episode of left knee swelling and testicular swelling in the past.
Doctor: Do you work with any toxic substances or have any habits like smoking, drinking, or illicit drug use?
Patient: No, I work as a flooring installer and I don't have any toxic habits.
Doctor: Alright. We checked your vital signs and they were normal. During the physical exam, we found bilateral papilledema and optic nerve erythema in your right eye, which was greater than in your left eye. You also have a right inferior nasal quadrant visual field defect and a right afferent pupillary defect. Your muscle strength and reflexes were normal, and your sensation to light touch, pinprick, vibration, and proprioception was intact. We also noticed the maculopapular rash on your bilateral lower extremities.
Patient: Oh, I see.
Doctor: Your admitting labs showed some abnormal results. You have microcytic anemia with a hemoglobin of 11.6 gm/dL, hematocrit of 35.3%, and mean corpuscular volume of 76.9 fL. You also have hyponatremia with a sodium level of 133 mmol/L. Your erythrocyte sedimentation rate (ESR) is elevated at 33 mm/hr, and your C-reactive protein (CRP) is also elevated at 13.3 mg/L. Your urinalysis did not show any protein or blood.
Patient: Okay. What does that mean?
Doctor: These results could indicate an underlying inflammatory or infectious process. We also performed a lumbar puncture, which showed clear and colorless fluid, 2 red blood cells per microliter, and 56 white blood cells per microliter.
Patient: So, what's the next step?
Doctor: We need to investigate further to determine the cause of your symptoms. We'll run additional tests and consult with a specialist to get a clearer understanding of your condition. In the meantime, we'll monitor your symptoms and provide supportive care. We'll keep you informed about any new findings and discuss the best course of treatment.
Patient: Alright, thank you, Doctor.

**Generated SOAP Note**:  

- **Subjective**: Painless blurry vision in the right eye for one week, intermittent fever, headache, body aches, maculopapular rash on lower limbs for six months. No neck stiffness, nausea, vomiting, Raynaud's phenomenon, oral ulcers, chest pain, dyspnea, abdominal pain, or photosensitivity.  

- **Objective**: Vital signs normal. Bilateral papilledema, optic nerve erythema (right > left), right inferior nasal quadrant visual field defect, right afferent pupillary defect. Muscle tone and reflexes normal; sensation intact. Labs: microcytic anemia (Hb 11.6 g/dL, Hct 35.3%, MCV 76.9 fL), hyponatremia (Na 133 mmol/L), ESR 33 mm/hr, CRP 13.3 mg/L. Lumbar puncture: clear fluid, 2 RBC/μL, 56 WBC/μL.  

- **Assessment**: Differential includes autoimmune disorders, vasculitis, infection, malignancy, and neurologic eye conditions.  

- **Plan**: Further labs (CBC, CMP, rheumatologic serologies, urinalysis, CSF analysis), imaging, and specialist consultations (ophthalmology, rheumatology) recommended. Close monitoring of symptoms and supportive care.  

**Simplified/Explained Summary**:  
The patient reports painless blurry vision in the right eye for one week, along with intermittent fever, headaches, body aches, and a non-pruritic maculopapular rash on both lower limbs present for six months. There is no associated neck stiffness, nausea, vomiting, Raynaud’s phenomenon, oral ulcers, chest pain, dyspnea, abdominal pain, or photosensitivity. Further tests and specialist consultations are planned to determine the underlying cause.


---

## 🛠️ Tech Stack  
- **Python**  
- **PyTorch**  
- **Hugging Face Transformers**  
- **PEFT + QLoRA**  
- **Datasets, Accelerate**  
- **ROUGE & BERTScore**  
