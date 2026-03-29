<h1 align="center"> Pulse Meter - FPGA Basys 3</h1>
<p align="center">
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/Hardware-Basys_3_FPGA-orange?style=for-the-badge" alt="Hardware">
  <img src="https://img.shields.io/badge/Language-VHDL-blue?style=for-the-badge" alt="Language">
</p>

---

<h2>Descriere Proiect</h2>
<p>
Acest proiect implementează un dispozitiv de măsurare a pulsului (BPM) utilizând o placă de dezvoltare **Basys 3**. Sistemul calculează frecvența impulsurilor primite prin intermediul unui buton și afișează rezultatul în timp real pe un display cu 7 segmente.
</p>
<ul>
  <li><b>Arhitectură:</b> FSM (Finite State Machine) cu 7 stări.</li>
  <li><b>Precizie:</b> Divizor de ceas de 1kHz pentru măsurarea duratei în ms.</li>
  <li><b>Conversie:</b> Modul dedicat Bin-to-BCD pentru afișaj.</li>
</ul>

---

<h2>Limbaj si unelte folosite:</h2>
<ul>
  <li>
    <a href="https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/archive.html">
      Xilinix Vivado
  </li>
  <li>
    <a href="https://nandland.com/introduction-to-vhdl-for-beginners-with-code-examples/">
      VHDL
  </li>
</ul>

---

<h2>Funcționare (Diagrama de Stări)</h2>
<p>
Logica sistemului este guvernată de un automat de stări finit (FSM). Mai jos este prezentată diagrama de tranziții originală care a stat la baza implementării VHDL:
</p>
<p align="center">
  <img src="Diagrama de tranzitii_pulse_meter.jpg" alt="Diagrama de tranzitii" width="600"/>
</p>
<p>
Descrierea Stărilor:
</p>
<ol>
    <li><b>Start:</b> Starea inițială, așteaptă activarea sistemului.</li>
    <li><b>SwOn:</b> Înregistrează primul impuls (dezactivarea switch-ului).</li>
    <li><b>Inceput:</b> Pregătește contorul pentru măsurarea duratei.</li>
    <li><b>Count:</b> Starea activă de numărare, măsoară timpul dintre impulsuri.</li>
    <li><b>Final:</b> Înregistrează al doilea impuls și oprește măsurarea.</li>
    <li><b>Pulse:</b> Calculează valoarea pulsului (BPM) pe baza timpului măsurat.</li>
    <li><b>Afisaj:</b> Trimite valoarea calculată către modulele de conversie și afișare.</li>
</ol>

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
