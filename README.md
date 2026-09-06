# Face Gender Categorization Under Emotional Expression

<details>
<summary>🇹🇷 Türkçe özet için tıklayın</summary>

Team Axion tarafından yürütülen bir davranışsal deney: yüz uyaranlarında ifade edilen duygunun (mutlu/kızgın/nötr), cinsiyet kategorileştirme görevindeki tepki süresi ve doğruluğu nasıl etkilediğini inceliyor.

**Deney tasarımı:** KDEF veri setinden, saç/kulak ipuçları kaldırılmış, iç yüz hatlarına odaklanan yüz fotoğrafları. Katılımcı, ifade edilen duyguyu görmezden gelip yüzün cinsiyetini mümkün olduğunca hızlı ve doğru belirtiyor. 2 (yüz cinsiyeti) × 3 (duygu) tasarım, katılımcı başına 120 deneme, sabit tohumla aynı pseudo-rastgele sıra. PsychoPy ile yazıldı. 20 katılımcıdan 2'si dışlanıp N=18'e (10 kadın, 8 erkek) inildi.

**Analiz:** veri hazırlama/ön işleme, Repeated Measures ANOVA (2×3, Greenhouse-Geisser düzeltmeli), post-hoc karşılaştırmalar, G*Power ile örneklem/etki büyüklüğü hesaplamaları.

**Bulgu:** duygu ifadesinin doğruluk üzerinde anlamlı bir ana etkisi ve yüz cinsiyetiyle anlamlı bir etkileşimi var (p < 0.0001); tepki süresinde yüz cinsiyeti etkisi sınırda anlamlı (p ≈ 0.05).

**Gizlilik notu:** bu depo, orijinal ham veri setinin anonimleştirilmiş bir kopyasıdır. Katılımcı isimleri katılımcı kodlarıyla (P01-P20) değiştirildi, ekip üyelerinin yazarlık bilgisi (bu kişisel veri değil, akademik atıf) olduğu gibi korundu. KDEF uyaran görselleri kendi lisans koşulları nedeniyle depoya dahil edilmedi.

</details>

---

A behavioral experiment run by Team Axion, looking at how the emotion expressed on a face (happy, angry, neutral) affects reaction time and accuracy in a gender categorization task.

## Experiment design

- **Stimuli:** faces from the KDEF (Karolinska Directed Emotional Faces) dataset, cropped to an oval or rectangle to isolate the inner facial features and remove hair and ear cues.
- **Task:** the participant ignores the expressed emotion and reports the face's gender as fast and accurately as possible (F for female, M for male).
- **Design:** 2 (face gender: female/male) x 3 (emotion: happy/angry/neutral), 120 trials per participant, the same pseudo-random order for every participant via a fixed seed.
- **Tool:** PsychoPy (`experiment/gender_task.psyexp`).
- **Sample:** 20 files collected, 2 excluded (one pilot recording, one participant below the age criterion), leaving N=18 (10 female, 8 male participants).

## Analysis

- Data preparation and preprocessing: outlier removal, accuracy and reaction time calculation.
- A repeated measures ANOVA (the 2x3 design) for both accuracy and reaction time, with the Greenhouse-Geisser correction.
- Post-hoc comparisons, plus sample size and effect size calculations with G*Power.

**Summary of findings:** emotion had a significant main effect on accuracy, and a significant interaction with face gender (p < 0.0001). The effect of face gender on reaction time was borderline significant (p roughly 0.05). Full statistical output is under `codes/results/main_analysis/` and in `reports/`.

## Folder structure

```
gender_emotion_experiment/
├── experiment/               PsychoPy experiment definition (gender_task.psyexp, conditions.xlsx)
├── codes/
│   ├── data_preparation.ipynb
│   ├── data_preproccessing.ipynb
│   ├── RM_anova.ipynb
│   ├── extra_analysis.ipynb
│   ├── raw_data/              Anonymized participant data (P01-P20)
│   ├── processed_data/        Merged and cleaned data, plus plots
│   └── results/main_analysis/  ANOVA tables, post-hoc tests, summary statistics
└── reports/                   The project's four written reports
```

## A note on data privacy

This repository is an anonymized copy of the original raw dataset. Participant names, both in file names and inside the CSVs, were replaced with participant codes (P01-P20). Team members' authorship information (on the reports' signature pages) was left untouched, since that's academic attribution rather than personal data. The KDEF stimulus images themselves aren't included here, because of their own license terms.

## Tools

PsychoPy for the experiment, Python with Pandas and Pingouin/statsmodels for the RM-ANOVA, Matplotlib and Seaborn for the plots.
