<h1 align="center">💓 Pulse Meter - FPGA Basys 3</h1>
<h3 align="center">Proiect Sisteme cu Circuite Integrate Digitale - Vivado</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Status-Project_Completed-brightgreen?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/Hardware-Basys_3_FPGA-orange?style=for-the-badge" alt="Hardware">
  <img src="https://img.shields.io/badge/Language-VHDL-blue?style=for-the-badge" alt="Language">
</p>

---

### 📝 Descriere Proiect
Acest proiect implementează un dispozitiv de măsurare a pulsului (BPM) utilizând o placă de dezvoltare **Basys 3**. Sistemul calculează frecvența impulsurilor primite prin intermediul unui buton și afișează rezultatul în timp real pe un display cu 7 segmente.

- ⚙️ **Arhitectură:** FSM (Finite State Machine) cu 7 stări.
- ⏱️ **Precizie:** Divizor de ceas de $1kHz$ pentru măsurarea duratei în $ms$.
- 🔢 **Conversie:** Modul dedicat Bin-to-BCD pentru afișaj.

---

### 📂 Structură Repository
Proiectul este organizat pentru a asigura o integrare ușoară în Vivado:

- 📁 **`src/`**
  - `top_level.vhd` - Instanțierea tuturor componentelor.
  - `pulse_meter_fsm.vhd` - Logica de control a stărilor.
  - `bpm_calculator.vhd` - Calculul matematic al pulsului.
- 📁 **`constraints/`**
  - `Basys3.xdc` - Configurarea pinilor pentru ceas, butoane și display.
- 📁 **`docs/`**
  - `Diagrama de tranzitii.jpg` - Schița originală a automatului de stări.

---

### 🛠️ Languages and Tools:
<p align="left">
  <img src="https://img.shields.io/badge/Xilinx_Vivado-FF0000?style=for-the-badge&logo=xilinx&logoColor=white" alt="Vivado" />
  <img src="https://img.shields.io/badge/VHDL-5C2D91?style=for-the-badge" alt="VHDL" />
</p>

---

### 📟 Funcționare (Diagrama de Stări)

Logica sistemului este guvernată de un automat de stări finit (FSM). Mai jos este prezentată diagrama de tranziții originală care a stat la baza implementării VHDL:

<p align="center">
  <img src="Diagrama de tranzitii_pulse_meter.jpg" alt="Diagrama de tranzitii" width="600"/>
</p>

#### Descrierea Stărilor:
1.  **`Start`**: Starea inițială, așteaptă activarea sistemului.
2.  **`SwOn`**: Înregistrează primul impuls (dezactivarea switch-ului).
3.  **`Inceput`**: Pregătește contorul pentru măsurarea duratei.
4.  **`Count`**: Starea activă de numărare, măsoară timpul dintre impulsuri.
5.  **`Final`**: Înregistrează al doilea impuls și oprește măsurarea.
6.  **`Pulse`**: Calculează valoarea pulsului (BPM) pe baza timpului măsurat.
7.  **`Afisaj`**: Trimite valoarea calculată către modulele de conversie și afișare.

---

### 📌 Mapare Pini (Basys 3)
| Semnal | Pin | Descriere |
| :--- | :--- | :--- |
| `clk` | W5 | Ceas principal (100MHz) |
| `rst` | U18 | Reset (Buton Central) |
| `btnL` | W19 | Intrare Puls (Buton Stâng) |
| `seg[0-6]` | W7-U7 | Segmente Display 7-Seg |
| `an[0-3]` | U2-W4 | Anozi Display 7-Seg |

---
<p align="center">
  <i>Realizat de Mădărășan Ioan-Alexandru</i>
</p>
