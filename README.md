# BMÜ329 Veri Tabanı Sistemleri Dersi Dönem Projesi
### Gereksinimleri ve E-R Diyagramı Formatı

**Proje Başlığı:** Takipçi Davranış Analizi ve Otomasyon Sistemi

---

## Grup Üyeleri

| Numarası    | Ad                                  | Soyadı     |
|-------------|-------------------------------------|------------|
| 220260138   | [Ömer Faruk](https://github.com/OmerFaruk-Celik/Takipci_Davranis_Analiz_Ve_Otomasyon_Sistemi.git)   | Çelik      |
| 210260304   | [Resul](https://github.com/Resulkacary/Takipci_Davranis_Analiz_Ve_Otomasyon_Sistemi.git)           | Kaçar      |
| 220260124   | [Muhammed Raşid](https://github.com/mryln) | Yılan     |

---

### Proje Gereksinimleri ve Varlıkların Detayları

Bu proje, kullanıcıların sosyal medya üzerindeki davranışlarını analiz ederek, kişisel ilgi alanlarına göre özel içerik ve reklam önerileri sunmayı hedefler. Kullanıcı ve takipçi ilişkileri, gönderiler, popüler içerikler, reklamlar ve sosyal medya gibi birçok varlık arasındaki ilişkiler analiz edilmiştir.

#### Veritabanı Temsili (Varlık-İlişki SQL Notasyonu)

    Kullanıcı
    (Kullanıcı ID (PK), İsim)

    Takipçi
    (Kullanıcı Adı (PK), Takip Edilen, Takip Tarihi)

    Gönderi
    (Gönderi ID (PK), Gönderi Metni, Beğeni Sayısı, Yorum Sayısı, Görünürlük, Gönderi Tarihi, Tür)

    Gruplar
    (Grup ID (PK), Üye Sayısı, Rol)

    Popüler İçerikler
    (İçerik ID (PK), Tür, Görünürlük, Yayınlanma Tarihi)

    Reklam
    (Reklam ID (PK), Tür, Reklam Kategorisi, Tıklanma Sayısı)

    Sosyal Medya
    (Kullanıcı Adı (PK) ,İsim ,E-posta, Şifre)

Bu notasyonda, Primary Key (PK) olan sütunları belirttik.

### Varlıklar ve Özellikleri

1. **Kullanıcı**
   - Kullanıcı ID
   - İsim

2. **Takipçi**
   - Kullanıcı Adı (Username)
   - Takip Edilen
   - Takip Tarihi

3. **Gönderi**
   - Gönderi ID
   - Gönderi Metni
   - Beğeni Sayısı
   - Yorum Sayısı
   - Görünürlük
   - Gönderi Tarihi
   - Tür

4. **Gruplar**
   - Grup ID
   - Üye Sayısı
   - Rol

5. **Popüler İçerikler**
   - İçerik ID
   - Tür
   - Görünürlük
   - Yayınlanma Tarihi

6. **Reklam**
   - Reklam ID
   - Tür
   - Reklam Kategorisi
   - Tıklanma Sayısı

7. **Sosyal Medya**
   - İsim
   - Kullanıcı Adı
   - E-posta
   - Şifre

### İlişki Türlerinin Açıklamaları

- **Birden Çoğa (1:N)**: Bir varlık diğer varlıktan birden fazla örneğe sahip olabilir. Örneğin, "Kullanıcı" birden fazla "Takipçiye" sahip olabilir.
- **Çoktan Çoğa (N:M)**: İki varlık birbiriyle çoklu ilişkiye sahip olabilir. Örneğin, "Takipçi" birden fazla "Gönderiyi" beğenebilir ve bir "Gönderi" birden fazla "Takipçi" tarafından beğenilebilir.
- **Birden Bire (1:1)**: Bir varlık diğer varlığa yalnızca bir kez bağlanabilir. Örneğin, bir "Gönderi" yalnızca bir "Popüler İçerik" olarak işaretlenebilir.
- **Çoktan Bire (N:1)**: Birden fazla varlık yalnızca bir varlığa bağlanabilir. Örneğin, birden fazla "Reklam," tek bir "Popüler İçeriğin" yanında gösterilebilir.

### İlişkiler ve Türleri

Aşağıdaki tablo, projedeki varlıklar arasındaki ilişkileri ve bu ilişkilerin türlerini özetlemektedir.

| **İlişki**       | **Varlık 1**       | **Varlık 2**           | **İlişki Türü**       |
|------------------|--------------------|------------------------|-----------------------|
| **Sahiptir**     | Kullanıcı          | Takipçi                | Birden Çoğa           |
| **Beğeni**       | Takipçi            | Gönderi                | Çoktan Çoğa           |
| **Yorum**        | Takipçi            | Gönderi                | Çoktan Çoğa           |
| **Yayımlar**     | Kullanıcı          | Gönderi                | Birden Çoğa           |
| **Katılma**      | Takipçi            | Gruplar                | Çoktan Çoğa           |
| **Olma**         | Gönderi            | Popüler İçerikler      | Birden Bire           |
| **Görüntüleme**  | Takipçi            | Popüler İçerikler      | Çoktan Çoğa           |
| **Gösterilme**   | Reklam             | Popüler İçerikler      | Çoktan Bire           |
| **Etkileşim**    | Reklam             | Gruplar                | Çoktan Çoğa           |
| **Yayınlar**     | Reklam             | Sosyal Medya           | Birden Çoğa           |
| **Tıklanma**     | Takipçi            | Reklam                 | Çoktan Çoğa           |

### ER Diyagramı

Projedeki varlıklar arasındaki ilişkileri gösteren basit ER diyagramı aşağıda sunulmuştur.

<p align="center">
  <img src="pictures/VTYS_GRUP16(4).png" alt="ER Diyagramı" width="1200"/>
</p>

### Proje Amacı

Bu proje, sosyal medya platformları üzerinde kullanıcıların etkileşimlerini analiz ederek, onlara özel içerik ve reklam önerileri sunmayı ve kullanıcının kitleye özgü ürünler oluşturmasını hedefler.

---

## Kurulum ve Kullanım

1. Projeyi klonlayın:
   ```bash
   git clone https://github.com/OmerFaruk-Celik/Takipci_Davranis_Analiz_Ve_Otomasyon_Sistemi.git

    Gerekli bağımlılıkları yükleyin:

    bash

# Gerekli komutlar buraya eklenecektir
