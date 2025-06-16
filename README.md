from openpyxl import Workbook

# Kullanıcıdan sayfa isimlerini al (virgül ile ayırarak)
sayfa_isimleri = input("Sayfa isimlerini girin (virgül ile ayırın): ")
sheet_names = [name.strip() for name in sayfa_isimleri.split(",")]

# Yeni bir çalışma kitabı oluştur
wb = Workbook()

# Varsayılan gelen ilk sayfayı sil
default_sheet = wb.active
wb.remove(default_sheet)

# Sayfaları oluştur
for name in sheet_names:
    wb.create_sheet(title=name)

# Kullanıcıdan dosya yolu al
file_path = input("Excel dosyasının kaydedileceği tam yolu girin (örn: C:\\Users\\...\\dosya.xlsx): ")

# Kaydet
wb.save(file_path)
print(f'✅ Excel dosyası "{file_path}" başarıyla oluşturuldu.')
