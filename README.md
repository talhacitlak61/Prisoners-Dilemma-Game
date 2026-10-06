🎮 Mahkumun İkilemi (Prisoner's Dilemma) - Oyun Tasarımı ve Geliştirme Ortamı

Bu depo, Algoritmik Oyun Kuramı dersi kapsamında geliştirilen Mahkumun İkilemi oyununun web tabanlı simülasyonu için hazırlanmış geliştirme ortamını ve sistem mimarisini içermektedir.

🛠️️ Geliştirme Ortamı ve Kullanılacak Teknolojiler

Proje, hem oyun kuramı analizlerini matematiksel olarak yapabilmek hem de son kullanıcıya interaktif bir deneyim sunabilmek amacıyla aşağıdaki teknolojilerle geliştirilecektir:

Programlama Dili: Python 3.9+

Web Çerçevesi (UI): Streamlit (Hızlı ve interaktif arayüz tasarımı için)

Veri Yapıları ve Matematiksel Analiz: NumPy (Ödeme matrislerinin tutulması ve Nash dengesi hesaplamaları için)

Versiyon Kontrol ve Barındırma: GitHub & Streamlit Community Cloud (Canlıya alma)

🏗️ Sistem Mimarisi ve UML Sınıf Diyagramı

Oyun, Nesne Yönelimli Programlama (OOP) prensiplerine uygun olarak tasarlanmıştır. Sistem temel olarak Oyuncu (İnsan/Yapay Zeka), Oyun Motoru (Kurallar ve Matris) ve Strateji modüllerinden oluşmaktadır.

classDiagram
    class GameEngine {
        +matrix: dict
        +player1: Player
        +player2: Player
        +play_round(choice1, choice2)
        +calculate_nash_equilibrium()
        +get_results()
    }
    
    class Player {
        +name: string
        +score: int
        +history: list
        +make_choice()
    }
    
    class HumanPlayer {
        +make_choice(ui_input)
    }
    
    class AIPlayer {
        +strategy: string
        +make_choice(opponent_history)
    }

    Player <|-- HumanPlayer
    Player <|-- AIPlayer
    GameEngine "1" *-- "2" Player : manages


🧠 Oyun Mantığı ve Sözde Kod (Pseudocode)

Oyunun arka planında çalışacak temel karar ve hesaplama mekanizmasının sözde kodu aşağıda verilmiştir:

BAŞLA Oyun_Döngüsü

    Oluştur Player1 (İnsan)
    Oluştur Player2 (Yapay Zeka - Seçilen Strateji: Tit-for-Tat veya Rastgele)
    
    TANIMLA Odeme_Matrisi:
        İşbirliği-İşbirliği = (-1, -1)
        İhanet-İşbirliği = (0, -3)
        İşbirliği-İhanet = (-3, 0)
        İhanet-İhanet = (-2, -2)

    Player1 seçimini UI (Arayüz) üzerinden al (Sessiz / İhanet)
    Player2 (AI) stratejisine göre seçimini hesapla
    
    EĞER Player1 == "Sessiz" VE Player2 == "Sessiz" İSE:
        Player1_Skor += -1
        Player2_Skor += -1
    VE EĞER Player1 == "İhanet" VE Player2 == "Sessiz" İSE:
        Player1_Skor += 0
        Player2_Skor += -3
    ... (Diğer matris durumları kontrol edilir)
    
    Sonuçları ve güncel skor tablosunu ekrana yazdır.
    Oyun geçmişini kaydet.

BİTİR Oyun_Döngüsü


🚀 Kurulum ve Çalıştırma (Taslak)

Bu bölüm uygulamanın kodlanması tamamlandığında aktif edilecektir.
Uygulamayı lokal ortamda çalıştırmak için:

git clone [repo_linki]

pip install streamlit numpy

streamlit run main.py
