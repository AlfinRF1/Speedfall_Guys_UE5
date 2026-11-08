# 🏆 SPEEDFALL GUYS

![Unreal Engine 5](https://img.shields.io/badge/Unreal%20Engine-5.3%2B-blue?style=for-the-badge&logo=unrealengine)
![Genre](https://img.shields.io/badge/Genre-3D%20Arcade%20Platformer-ff69b4?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-In%20Development-green?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

> **"Berlari, meluncur, terhempas, dan capai mahkota kemenangan!"**  
> *SPEEDFALL GUYS* adalah game *3D obstacle course platformer* bertempo cepat berbasis fisika **Unreal Engine 5** yang terinspirasi dari game arcade populer seperti *Fall Guys* dan *Stumble Guys*.

---

## 🌟 High Concept & Key Features

Pemain bersaing menavigasi arena halang rintang berstruktur heksagonal. Tantangan utama berasal dari kombinasi medan licin tanpa gesekan dan jebakan mekanis yang bergerak dinamis.

### 🧪 1. Friction-Free Slime Mechanics (`BP_SlimeZone`)
* **Ground Friction 0.0:** Menghilangkan gaya gesek pengereman karakter saat menyentuh slime.
* **Launch Momentum:** Menghempaskan karakter secara instan menggunakan vector lari pemain ($V_{\text{launch}} = \mathbf{v}_{\text{forward}} \cdot 800$).
* **Reduced Steering Control:** Menurunkan `Max Acceleration` menjadi $300.0$ untuk mensimulasikan sensasi terpeleset dan kontrol meluncur yang menantang.

### 🧱 2. Staggered Side Pushers (`BP_SidePusher`)
* **Timeline & Lerp Vector:** Dinding pendorong magenta yang menjulur secara halus menggunakan interpolasi linier.
* **Instance Editable Delay:** Pengaturan variabel `DelayAwal` langsung dari Viewport untuk membuat pola pendorong selang-seling (alternating pattern) antar balok.

### 🌀 3. Sweeper & Pendulum Hazards (`BP_4BladeSpinner` & `BP_SwingingBall`)
* **4-Blade Spinner:** Balok penyapu 4 arah menggunakan komponen `RotatingMovement` dengan kecepatan $90^\circ/\text{s}$ Yaw.
* **Sine Wave Pendulum:** Bola ayun raksasa yang bergerak menggunakan fungsi matematika sinusoidal:
  $$\theta(t) = \theta_{\text{max}} \cdot \sin(\omega \cdot t)$$
  menghasilkan gerakan pendulum alami (cepat di titik tengah, melambat di titik puncak).

---

## 🎮 Game Design Document (GDD) Summary

### 01. Identitas Dokumen
| Atribut | Detail |
| :--- | :--- |
| **Judul Game** | **SPEEDFALL GUYS** |
| **Engine** | Unreal Engine 5 |
| **Pengembang** | Alfin Rahmad Fauzi — Politeknik Negeri Jember (PSDKU Nganjuk) |
| **Platform Utama** | PC (Windows — Steam/Epic Games Store) |
| **Target Audience** | 10–25 Tahun (PEGI 7 / IGRS 7+) |

### 02. Design Pillars
1. **Slime Physics & Momentum:** Tantangan navigasi akibat hilangnya pengereman dan dorongan kecepatan meluncur.
2. **Staggered Dynamic Hazards:** Jebakan interaktif dengan *timing* jeda selang-seling yang tak bisa ditebak.
3. **Vibrant Arcade Aesthetics:** Kontras warna mencolok (*Cyan*, *Magenta*, *Yellow*, *Blue*) ala acara permainan fisik retro/modern.

### 03. Core Gameplay Loop
```text
  [ START RUN ]
       │
       ▼
 [ Read Hazard Pattern ] ──► [ Slide on Slime / Jump ]
       │                                 │
       │                                 ▼
       │                    [ Avoid Pusher & Spinner ]
       │                                 │
       └─────────────────────────────────┴──► [ Checkpoint / Finish Arch ]
                                                      │
                                                      ▼
                                            [ Record Time & Reward ]
```

---

## 🛠️ Tech Stack & Blueprint Architecture

```text
Content/
 ├── _MyGame/
 │    ├── Blueprints/
 │    │    ├── BP_SlimeZone.uasset        # Trigger volume & slip physics
 │    │    ├── BP_SidePusher.uasset       # Horizontal Timeline pusher
 │    │    ├── BP_4BladeSpinner.uasset    # Rotating obstacle
 │    │    └── BP_SwingingBall.uasset     # Sine-wave Driven Pendulum
 │    ├── Materials/
 │    │    ├── M_Slime_Floor.uasset       # Slime shader
 │    │    └── PM_Slime.uasset            # Physical Material (Friction 0.0)
 │    └── Maps/
 │         └── LV_Level01.umap            # Main Hexagonal Arena Stage
```

---

## 🚀 Cara Menjalankan Proyek

### Prasyarat:
* **Unreal Engine 5.3** atau versi yang lebih baru.
* **Git LFS** (Large File Storage) terpasang di sistem.

### Langkah Instalasi:

1. **Clone Repositori ini:**
   ```bash
   git clone https://github.com/alfinrahmadfauzi/Speedfall-Guys-UE5.git
   cd Speedfall-Guys-UE5
   ```

2. **Pull Large Files:**
   ```bash
   git lfs pull
   ```

3. **Buka Proyek:**
   * Double-click pada file `SPEEDFALL_GUYS.uproject`.
   * Tunggu Unreal Engine melakukan *compilation shaders* pertama kali.

4. **Play Map:**
   * Buka folder `Content/_MyGame/Maps/`.
   * Buka `LV_Level01`.
   * Klik tombol **Play (`Alt + P`)** di editor toolbar.

---

## 📄 Lisensi

Hak cipta dilindungi undang-undang. Proyek ini dikembangkan untuk keperluan akademik dan portofolio pengembangan game (*Game Development*).

---
*Dikembangkan oleh AlFIN2GD menggunakan Unreal Engine 5.*
