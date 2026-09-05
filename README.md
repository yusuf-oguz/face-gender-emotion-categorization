# Face Gender Categorization Under Emotional Expression

İTÜ YZV447E (Cognitive Neuroscience) dönem projesi — Team Axion. Yüz uyaranlarında ifade edilen duygunun (mutlu/kızgın/nötr), cinsiyet kategorileştirme görevindeki tepki süresi ve doğruluğu nasıl etkilediğini inceleyen bir davranışsal deney.

## Deney Tasarımı

- **Uyaranlar:** KDEF (Karolinska Directed Emotional Faces) veri setinden, iç yüz hatlarına odaklanmak için oval/dikdörtgen kırpılmış yüz fotoğrafları (saç/kulak ipuçları kaldırıldı).
- **Görev:** Katılımcı, ifade edilen duyguyu görmezden gelip yüzün cinsiyetini mümkün olduğunca hızlı ve doğru belirtiyor (F = Kadın, M = Erkek).
- **Tasarım:** 2 (Yüz Cinsiyeti: Kadın/Erkek) × 3 (Duygu: Mutlu/Kızgın/Nötr), katılımcı başına 120 deneme, tüm katılımcılarda aynı (sabit tohum ile) pseudo-rastgele sıra.
- **Araç:** PsychoPy (`experiment/gender_task.psyexp`).
- **Örneklem:** 20 dosya toplandı, 2'si analiz dışı bırakıldı (bir pilot/deneme kaydı, bir katılımcı yaş kriteri altında) → N=18 (10 kadın, 8 erkek katılımcı).

## Analiz

- Veri hazırlama ve ön işleme (aykırı değer temizliği, doğruluk/tepki süresi hesaplama).
- **Repeated Measures ANOVA** (2×3 tasarım) — hem doğruluk hem tepki süresi için, Greenhouse-Geisser düzeltmesiyle.
- Post-hoc karşılaştırmalar, G*Power ile örneklem büyüklüğü/etki büyüklüğü hesaplamaları.

**Bulgu özeti:** Duygu ifadesinin doğruluk üzerinde anlamlı bir ana etkisi ve yüz cinsiyeti ile anlamlı bir etkileşimi bulundu (p < 0.0001); tepki süresinde yüz cinsiyeti etkisi sınırda anlamlı (p ≈ 0.05). Tam istatistiksel sonuçlar için `codes/results/main_analysis/` ve `reports/`.

## Klasör Yapısı

```
gender_emotion_experiment/
├── experiment/              # PsychoPy deney tanımı (gender_task.psyexp, conditions.xlsx)
├── codes/
│   ├── data_preparation.ipynb
│   ├── data_preproccessing.ipynb
│   ├── RM_anova.ipynb
│   ├── extra_analysis.ipynb
│   ├── raw_data/             # Anonimleştirilmiş katılımcı verisi (P01-P20)
│   ├── processed_data/        # Birleştirilmiş/temizlenmiş veri + grafikler
│   └── results/main_analysis/  # ANOVA tabloları, post-hoc testler, özet istatistikler
└── reports/                  # Dönem projesi raporları (1-4)
```

## ⚠️ Veri Gizliliği Notu

Bu depo, orijinal ham veri setinin **anonimleştirilmiş bir kopyasıdır.** Katılımcı isimleri (dosya adlarında ve CSV içeriklerinde) katılımcı kodlarıyla (P01-P20) değiştirilmiştir; ekip üyelerinin yazarlık/katkı bilgileri (rapor imza sayfaları) olduğu gibi korunmuştur — bu kişisel veri değil, akademik atıf bilgisidir. KDEF uyaran görselleri, kendi lisans koşulları nedeniyle bu depoya dahil edilmemiştir.

## Kullanılan Araçlar

PsychoPy (deney), Python — Pandas, Pingouin/statsmodels (RM-ANOVA), Matplotlib/Seaborn (görselleştirme).
