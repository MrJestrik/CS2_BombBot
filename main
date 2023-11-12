import pymem, pymem.process, time

plantedC4 = 25234632
m_nBombSite = 0xE84
m_bBeingDefused = 0xEBC
m_bBombDefused = 0xED4


def main():
    print("BombBot started.")
    pm = pymem.Pymem("cs2.exe")
    client = pymem.process.module_from_name(pm.process_handle, "client.dll").lpBaseOfDll

    while True:

        cplantedc4 = pm.read_ulonglong(client + plantedC4)
        cplantedc4 = pm.read_ulonglong(cplantedc4)
        planted = pm.read_bool(client + plantedC4 - 0x8)
        if planted:
            site = pm.read_int(cplantedc4 + m_nBombSite)
            beingdefused = pm.read_bool(cplantedc4 + m_bBeingDefused)
            defused = pm.read_bool(cplantedc4 + m_bBombDefused)
            # cplantedc4 = pm.read_ulonglong(client + plantedC4)
            if site > 0:
                site = "B"
            else:
                site = "A"
            if not defused:
                print(f"Bomb planted on: {site}\nDefusing: {beingdefused}")
            else:
                print("Bomb Defused!")
        else:
            print("Bomb not planted!")

        time.sleep(1)
