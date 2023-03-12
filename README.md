# pizzaordersystem
pizza order system #python 

import csv
import datetime


print("\n===============================================")
print("                 PIZZA DÜKKANI  ")
print("===============================================")
print("                 HOŞ GELDİNİZ !!!          ")
print("===============================================")

class Pizza:
    def __init__(self, description, cost):
        self.description = description
        self.cost = cost
        
    def get_description(self):
        return self.description
    
    def get_cost(self):
        return self.cost


class Sos:
    def __init__(self, description, cost):
        self.description = description
        self.cost = cost
        
    def get_description(self):
        return self.description
    
    def get_cost(self):
        return self.cost


# İki farklı pizza nesnesi oluşturuyoruz
pizza1 = Pizza("Küçük Margarita", 20.0)
pizza2 = Pizza("Küçük Pepperoni", 25.0)
pizza3 = Pizza("Büyük Margarita", 30.0)
pizza4 = Pizza("Büyük Pepperoni", 35.0)

# İki farklı sos nesnesi oluşturuyoruz
sos1 = Sos("Domates Sosu", 5.0)
sos2 = Sos("Barbekü Sosu", 7.0)

# Kullanıcıdan hangi pizzayı almak istediğini ve boyutunu sorduk
while True:
    try:
        pizza_choice = input("Hangi boyutta pizza almak istersiniz? (1) Küçük, (2) Büyük: ")
        if pizza_choice == "1":
            pizza_size = "Küçük"
            pizza_choice = input("Hangi pizzayı almak istersiniz? (1) Margarita, (2) Pepperoni: ")
            if pizza_choice == "1":
                pizza = pizza1
                pizza_description = pizza1.get_description()
                pizza_cost = pizza1.get_cost()
                break
            elif pizza_choice == "2":
                pizza = pizza2
                pizza_description = pizza2.get_description()
                pizza_cost = pizza2.get_cost()
                break
            else:
                print("Geçersiz pizza seçimi! Tekrar Deneyin")
                
        elif pizza_choice == "2":
            pizza_size = "Büyük"
            pizza_choice = input("Hangi pizzayı almak istersiniz? (1) Margarita, (2) Pepperoni: ")
            if pizza_choice == "1":
                pizza = pizza3
                pizza_description = pizza3.get_description()
                pizza_cost = pizza3.get_cost()
                break
            elif pizza_choice == "2":
                pizza = pizza4
                pizza_description = pizza4.get_description()
                pizza_cost = pizza4.get_cost()
                break
            else:
                print("Geçersiz pizza seçimi! Tekrar Deneyin")
                
        else:
            print("Geçersiz boyut seçimi! Tekrar Deneyin")
    except:    
        print("Geçersiz Tuşlama Tekrar dener misin :d ")

# Kullanıcıya sos seçip seçmek istemediğini soruyoruz
sos_choice = input("Sos ister misiniz? (E)vet/(H)ayır: ")

# Kullanıcının seçimine göre sos açıklamasını ve fiyatını ekliyoruz veya eklemeden devam ediyoruz
if sos_choice.lower() == "e" or sos_choice.lower() == "evet":
    sos_choice = input("Hangi sosu almak istersiniz? (1) Domates Sosu, (2) Barbekü Sosu: ")
    if sos_choice == "1":
        sos = sos1
        sos_description = sos1.get_description()
        sos_cost = sos1.get_cost()
    elif sos_choice == "2":
        sos = sos2
        sos_description = sos2.get_description()
        sos_cost = sos2.get_cost()
    else:
        print("Geçersiz sos seçimi!")
        exit()
else:
    sos_description = "Sos yok"
    sos_cost = 0.0

total_cost = pizza_cost + sos_cost

print("Seçilen pizza:", pizza_description)
print("Pizza fiyatı:", pizza_cost)
print("Seçilen sos:", sos_description)
print("Sos fiyatı:", sos_cost)
print("Toplam fiyat:", total_cost)

print("-------------------------------------------------------------------")
print("Hesap ödemesi")
  
name = input("İsim: ")
id_number = input("TC Kimlik Numarası: ")
cc_number = input("Kredi Kartı Numarası: ")
cc_cvv = input("Kredi Kartı CVV: ")

# Sipariş zamanını kaydediyoruz
order_time = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")

# Sipariş bilgilerini CSV dosyasına kaydediyoruz
with open("Orders_Database.csv", "a", newline="") as file:
    writer = csv.writer(file)
    writer.writerow([name, id_number, cc_number, cc_cvv, pizza_description, sos_description, total_cost, order_time])


          
    print(pizza_description," Siparişiniz alınmıştır. İyi günler!")
    # Sipariş bilgilerini fiş şeklinde yazdırma
print("\n===============================================")
print("                 PIZZA DÜKKANI ")
print("===============================================")
print("                 SİPARİŞ BİLGİLERİ              ")
print("===============================================")
print(f"Tarih/Saat: {order_time}")
print(f"Müşteri Adı: {name}")
print(f"TC Kimlik Numarası: {id_number}")
print(f"Kredi Kartı Numarası: {cc_number}")
print("===============================================")
print("                 SİPARİŞ İÇERİĞİ                ")
print("===============================================")
print(f"{pizza_size} {pizza_description}: {pizza_cost} TL")
if sos_description != "Sos yok":
    print(f"{sos_description}: {sos_cost} TL")
print("===============================================")
print(f"Toplam Fiyat: {total_cost} TL")
print("===============================================")

    
print("Sipariş zamanı:", order_time)
