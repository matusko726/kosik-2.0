# sklad
sklad = {
    "ovocie": {
        "jablko": {"cena": 0.80, "mnozstvo": 3},
        "banan": {"cena": 1.50, "mnozstvo": 2},
        "hruska": {"cena": 1.20, "mnozstvo": 5},
        "marhula": {"cena": 2.00, "mnozstvo": 4},
        "slivka": {"cena": 1.80, "mnozstvo": 6}
    },
    "zelenina": {
        "mrkva": {"cena": 0.60, "mnozstvo": 10},
        "petrzlen": {"cena": 0.90, "mnozstvo": 8},
        "celer": {"cena": 1.10, "mnozstvo": 3},
        "zemiak": {"cena": 0.70, "mnozstvo": 15}
    },
    "sladkosti": {
        "cokolada": {"cena": 1.50, "mnozstvo": 5},
        "cukor": {"cena": 1.20, "mnozstvo": 10}
    },
    "mliecne": {
        "mlieko": {"cena": 1.00, "mnozstvo": 4},
        "jogurt": {"cena": 0.60, "mnozstvo": 6},
        "maslo": {"cena": 2.50, "mnozstvo": 2},
        "syr": {"cena": 2.00, "mnozstvo": 3}
    },
    "pecivo": {
        "chlieb": {"cena": 1.80, "mnozstvo": 3},
        "rohlik": {"cena": 0.15, "mnozstvo": 20},
        "bageta": {"cena": 0.90, "mnozstvo": 5}
    }
}

nakupny_kosik = []

# Nakupovací cyklus
while True:
    print("Čo chcete pridať do košíka? ")
    vstup = input("Zadajte položku: ").strip().lower()
    
    if vstup == "uz nic" or vstup == "koniec":
        break
    
    # polozka
    najdena = False
    for kategoria, produkty in sklad.items():
        if vstup in produkty:
            najdena = True
            # skal
            if produkty[vstup]["mnozstvo"] > 0:
                nakupny_kosik.append(vstup)
                # Znížime množstvo v sklade o 1
                produkty[vstup]["mnozstvo"] -= 1
                print(f"-> Mas pridanu Zostava ich uz len: {produkty[vstup]['mnozstvo']} ks")
            else:
                print(f"-> Ľutujeme, položku '{vstup}' uz vykupili dôchodci ")
            break
            
    if not najdena:
        print(f"->  '{vstup}' nieje spawnuta na sklade")

        print("\n----------------------------------------")
print("Vsetky tvoje veci:")

celkova_suma = 0

# polozky
for polozka in nakupny_kosik:
    # cena
    for kategoria, produkty in sklad.items():
        if polozka in produkty:
            cena = produkty[polozka]["cena"]
            celkova_suma += cena
            print(f"- {polozka} ({kategoria}): {cena:.2f} €")

print("----------------------------------------")
print(f"Zaplat inak mas po chlebe: {celkova_suma:.2f} €")
