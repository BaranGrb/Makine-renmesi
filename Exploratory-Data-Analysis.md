# Titanic Veri Seti Keşifsel Veri Analizi (EDA)

```python
"""
TITANIC VERİ SETİ KEŞİFSEL VERİ ANALİZİ (EDA)
Bu kod, Titanic veri seti üzerinde temel EDA işlemlerini gerçekleştirir.
Her adımda açıklama satırları bulunmaktadır.
"""

# 1. VERİ YÜKLEME: CSV dosyasını pandas DataFrame'e yükle
import pandas as pd
df = pd.read_csv("train.csv")
```

## 📊 1. İlk 5 Satır - Veri Setinin Başlangıcı
**Açıklama:** Veri setinin yapısını görmek için ilk 5 kaydı gösterir, sütun isimlerini ve veri türlerini anlamaya yardımcı olur.
```python
print("=== 1. İLK 5 SATIR ===")
print(df.head())
```
**Çıktı:**
| PassengerId | Survived | Pclass | Name                                                | Sex    | Age  | SibSp | Parch | Ticket      | Fare    | Cabin | Embarked |
|-------------|----------|--------|-----------------------------------------------------|--------|------|-------|-------|-------------|---------|-------|----------|
| 1           | 0        | 3      | Braund, Mr. Owen Harris                             | male   | 22.0 | 1     | 0     | A/5 21171   | 7.2500  | NaN   | S        |
| 2           | 1        | 1      | Cumings, Mrs. John Bradley (Florence Briggs Th...) | female | 38.0 | 1     | 0     | PC 17599    | 71.2833 | C85   | C        |
| 3           | 1        | 3      | Heikkinen, Miss. Laina                              | female | 26.0 | 0     | 0     | STON/O2. 3101282 | 7.9250 | NaN   | S        |
| 4           | 1        | 1      | Futrelle, Mrs. Jacques Heath (Lily May Peel)        | female | 35.0 | 1     | 0     | 113803      | 53.1000 | C123  | S        |
| 5           | 0        | 3      | Allen, Mr. William Henry                            | male   | 35.0 | 0     | 0     | 373450      | 8.0500  | NaN   | S        |

## 📊 2. Son 5 Satır - Veri Setinin Sonu
**Açıklama:** Veri setinin son kısmını gösterir, verilerin tutarlılığını kontrol etmek için kullanışlıdır.
```python
print("\n=== 2. SON 5 SATIR ===")
print(df.tail())
```
**Çıktı:**
| PassengerId | Survived | Pclass | Name                                                | Sex    | Age  | SibSp | Parch | Ticket      | Fare    | Cabin | Embarked |
|-------------|----------|--------|-----------------------------------------------------|--------|------|-------|-------|-------------|---------|-------|----------|
| 886         | 0        | 2      | Montvila, Rev. Juozas                               | male   | 27.0 | 0     | 0     | 211536      | 13.00   | NaN   | S        |
| 887         | 1        | 1      | Graham, Miss. Margaret Edith                        | female | 19.0 | 0     | 0     | 112053      | 30.00   | B42   | S        |
| 888         | 0        | 3      | Johnston, Miss. Catherine Helen "Carrie"            | female | NaN  | 1     | 2     | W./C. 6607  | 23.45   | NaN   | S        |
| 889         | 1        | 1      | Behr, Mr. Karl Howell                               | male   | 26.0 | 0     | 0     | 111369      | 30.00   | C148  | C        |
| 890         | 0        | 3      | Dooley, Mr. Patrick                                 | male   | 32.0 | 0     | 0     | 370376      | 7.75    | NaN   | Q        |

## 📊 3. Rastgele 1 Satır - Veri Örneği
**Açıklama:** Veri setinden rastgele bir örnek seçer, verilerin dağılımını anlamak için kullanılır.
```python
print("\n=== 3. RASTGELE 1 SATIR ===")
print(df.sample())
```
**Örnek Çıktı:**
| PassengerId | Survived | Pclass | Name                          | Sex    | Age  | SibSp | Parch | Ticket  | Fare | Cabin | Embarked |
|-------------|----------|--------|-------------------------------|--------|------|-------|-------|---------|------|-------|----------|
| 345         | 1        | 2      | Brown, Miss. Amelia "Mildred" | female | 24.0 | 0     | 0     | 248733  | 13.0 | F33   | S        |

## 📐 4. Veri Boyutları
**Açıklama:** (satır_sayısı, sütun_sayısı) formatında veri setinin boyutunu gösterir.
```python
print("\n=== 4. VERİ BOYUTLARI ===")
print(df.shape)
```
**Çıktı:** `(891, 12)` - 891 satır, 12 sütun

## ℹ️ 5. Veri Bilgisi
**Açıklama:** Her sütunun veri tipi, boş olmayan değer sayısı ve bellek kullanımı hakkında detaylı bilgi verir.
```python
print("\n=== 5. VERİ BİLGİSİ ===")
df.info()
```
**Çıktı:**
```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 891 entries, 0 to 890
Data columns (total 12 columns):
 #   Column       Non-Null Count  Dtype  
---  ------       --------------  -----  
 0   PassengerId  891 non-null    int64  
 1   Survived     891 non-null    int64  
 2   Pclass       891 non-null    int64  
 3   Name         891 non-null    object 
 4   Sex          891 non-null    object 
 5   Age          714 non-null    float64
 6   SibSp        891 non-null    int64  
 7   Parch        891 non-null    int64  
 8   Ticket       891 non-null    object 
 9   Fare         891 non-null    float64
 10  Cabin        204 non-null    object 
 11  Embarked     889 non-null    object 
dtypes: float64(2), int64(5), object(5)
memory usage: 83.7+ KB
```

## 📈 6. İstatistiksel Özet
**Açıklama:** Sayısal sütunlar için count, mean, std, min, 25%, 50%, 75%, max değerlerini gösterir.
```python
print("\n=== 6. İSTATİSTİKSEL ÖZET ===")
print(df.describe())
```
**Çıktı:**
|         | PassengerId | Survived | Pclass   | Age       | SibSp     | Parch     | Fare      |
|---------|-------------|----------|----------|-----------|-----------|-----------|-----------|
| count   | 891.000000  | 891.000000 | 891.000000 | 714.000000 | 891.000000 | 891.000000 | 891.000000 |
| mean    | 446.000000  | 0.383838  | 2.308642  | 29.699118  | 0.523008  | 0.381594  | 32.204208  |
| std     | 257.353842  | 0.486592  | 0.836071  | 14.526497  | 1.102743  | 0.806057  | 49.693429  |
| min     | 1.000000    | 0.000000  | 1.000000  | 0.420000   | 0.000000  | 0.000000  | 0.000000   |
| 25%     | 223.500000  | 0.000000  | 2.000000  | 20.125000  | 0.000000  | 0.000000  | 7.910400   |
| 50%     | 446.000000  | 0.000000  | 3.000000  | 28.000000  | 0.000000  | 0.000000  | 14.454200  |
| 75%     | 668.500000  | 1.000000  | 3.000000  | 38.000000  | 1.000000  | 0.000000  | 31.000000  |
| max     | 891.000000  | 1.000000  | 3.000000  | 80.000000  | 8.000000  | 6.000000  | 512.329200 |

## 🚫 7. Eksik Veri Sayıları
**Açıklama:** Her sütunda kaç tane eksik veri (NaN) olduğunu gösterir.
```python
print("\n=== 7. EKSİK VERİ SAYILARI ===")
print(df.isnull().sum())
```
**Çıktı:**
```
PassengerId      0
Survived         0
Pclass           0
Name             0
Sex              0
Age            177
SibSp            0
Parch            0
Ticket           0
Fare             0
Cabin          687
Embarked         2
dtype: int64
```

## 🚫 8. Sadece Boş Alanlar
**Açıklama:** Sadece eksik veri içeren sütunları ve eksik veri sayılarını gösterir.
```python
print("\n=== 8. SADECE BOŞ ALANLAR ===")
miss = df.isnull().sum()
print(miss[miss > 0])
```
**Çıktı:**
```
Age         177
Cabin       687
Embarked      2
dtype: int64
```

## 🚫 9. Age Boş Kayıt Sayısı
**Açıklama:** Yaş sütununda kaç tane eksik veri olduğunu gösterir.
```python
print("\n=== 9. AGE BOŞ KAYIT SAYISI ===")
print(df["Age"].isnull().sum())
```
**Çıktı:** `177`

## 🔍 10. Embarked Benzersiz Değerler
**Açıklama:** Embarked (biniş limanı) sütunundaki tüm farklı değerleri listeler.
```python
print("\n=== 10. EMBARKED BENZERSİZ DEĞERLER ===")
print(df["Embarked"].unique())
```
**Çıktı:** `array(['S', 'C', 'Q', nan], dtype=object)`

## 🔍 11. Embarked Değer Sayıları
**Açıklama:** Her biniş limanı değerinden kaç tane olduğunu gösterir (frekans dağılımı).
```python
print("\n=== 11. EMBARKED DEĞER SAYILARI ===")
print(df["Embarked"].value_counts())
```
**Çıktı:**
```
S    644
C    168
Q     77
Name: Embarked, dtype: int64
```

## 🔍 12. Embarked Değer Oranları
**Açıklama:** Her biniş limanı değerinin toplam içindeki oranını yüzde olarak gösterir.
```python
print("\n=== 12. EMBARKED DEĞER ORANLARI ===")
print(df["Embarked"].value_counts(normalize=True))
```
**Çıktı:**
```
S    0.724719
C    0.188976
Q    0.086305
Name: Embarked, dtype: float64
```

## 🔗 13. Korelasyon Matrisi
**Açıklama:** Sayısal sütunlar arasındaki korelasyon katsayılarını gösterir (-1 ile 1 arasında).  
**Not:** 1: Tam pozitif korelasyon, -1: Tam negatif korelasyon, 0: İlişki yok
```python
print("\n=== 13. KORELASYON MATRİSİ ===")
print(df.corr(numeric_only=True))
```
**Çıktı:**
|             | PassengerId | Survived | Pclass   | Age       | SibSp     | Parch     | Fare      |
|-------------|-------------|----------|----------|-----------|-----------|-----------|-----------|
| PassengerId | 1.000000    | -0.005007 | -0.035144 | 0.036847  | -0.057527 | -0.001652 | 0.012658  |
| Survived    | -0.005007   | 1.000000  | -0.338481 | -0.077221 | -0.035322 | 0.081629  | 0.257307  |
| Pclass      | -0.035144   | -0.338481 | 1.000000  | -0.369226 | 0.083081  | 0.018443  | -0.549500 |
| Age         | 0.036847    | -0.077221 | -0.369226 | 1.000000  | -0.308247 | -0.189119 | 0.096067  |
| SibSp       | -0.057527   | -0.035322 | 0.083081  | -0.308247 | 1.000000  | 0.414838  | 0.159651  |
| Parch       | -0.001652   | 0.081629  | 0.018443  | -0.189119 | 0.414838  | 1.000000  | 0.216225  |
| Fare        | 0.012658    | 0.257307  | -0.549500 | 0.096067  | 0.159651  | 0.216225  | 1.000000  |

## 🔗 14. Survived Korelasyonları (Sıralı)
**Açıklama:** Hayatta kalma durumu ile diğer değişkenler arasındaki ilişkiyi büyükten küçüğe sıralar. Mutlak değer alındığı için hem pozitif hem negatif ilişkileri büyüklüklerine göre sıralar.
```python
print("\n=== 14. SURVIVED KORELASYONLARI (SIRALI) ===")
print(abs(df.corr(numeric_only=True)['Survived']).sort_values(ascending=False))
```
**Çıktı:**
```
Survived       1.000000
Pclass         0.338481
Fare           0.257307
Parch          0.081629
Age            0.077221
SibSp          0.035322
PassengerId    0.005007
Name: Survived, dtype: float64
```

## 📊 15. Age Maksimum Değer
**Açıklama:** Veri setindeki en yüksek yaş değerini gösterir.
```python
print("\n=== 15. AGE MAKSİMUM DEĞER ===")
print(df["Age"].max())
```
**Çıktı:** `80.0`

## 📊 16. Age Minimum Değer
**Açıklama:** Veri setindeki en düşük yaş değerini gösterir.
```python
print("\n=== 16. AGE MİNİMUM DEĞER ===")
print(df["Age"].min())
```
**Çıktı:** `0.42`

## 📊 17. Age Ortalama
**Açıklama:** Tüm yolcuların yaşlarının aritmetik ortalamasını gösterir.
```python
print("\n=== 17. AGE ORTALAMA ===")
print(df["Age"].mean())
```
**Çıktı:** `29.69911764705882`

## 📊 18. Age Medyan
**Açıklama:** Yaş değerlerini küçükten büyüğe sıraladığımızda ortadaki değeri gösterir. Aykırı değerlerden aritmetik ortalamaya göre daha az etkilenir.
```python
print("\n=== 18. AGE MEDYAN ===")
print(df["Age"].median())
```
**Çıktı:** `28.0`

## 📊 19. Age Standart Sapma
**Açıklama:** Yaş değerlerinin ortalamadan ne kadar saçıldığını gösterir. Büyük standart sapma = daha fazla çeşitlilik, küçük standart sapma = daha homojen dağılım.
```python
print("\n=== 19. AGE STANDART SAPMA ===")
print(df["Age"].std())
```
**Çıktı:** `14.526497332334044`

## 📊 20. Age Varyans
**Açıklama:** Yaş değerlerinin ortalamadan farklarının karelerinin ortalamasıdır. Standart sapmanın karesine eşittir, dağılımın yayılımını ölçer.
```python
print("\n=== 20. AGE VARYANS ===")
print(df["Age"].var())
```
**Çıktı:** `211.01912474630812`

## 🔄 21. Tekrarlı Veri Kontrolü
**Açıklama:** Tüm sütunları aynı olan tamamen tekrar eden satırları kontrol eder. Eğer boş DataFrame dönerse, tümüyle aynı olan tekrar eden satır yok demektir.
```python
print("\n=== 21. TEKRARLI VERİ KONTROLÜ ===")
print(df[df.duplicated() == True])
```
