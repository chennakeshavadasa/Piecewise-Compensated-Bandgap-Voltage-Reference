# Piecewise Compensated High-PSRR-Bandgap-Voltage-Reference

- Piecewise Compensated High PSRR Bandgap Voltage Reference using GPDK90. 

## Specification
(V<sub>DDA</sub> = 2.5V, T<sub>J</sub> = 27°C, C<sub>L</sub> = 5pF unless otherwise specified below)

| Parameter                              | Symbol      | Condition                          | Min  | Typ  | Max  | Units |
|----------------------------------------|-------------|------------------------------------|------|------|------|-------|
| Bias Current for Bandgap               | IDDA        | VDDA=2.5, TJ=27°C                 |      | 10   |      | µA    |
| Output Voltage Process Dependence      | VREF(P)     | Over Strong-Weak Corners          | 0.645 | 0.650| 0.655| V     |
| Output Voltage Temperature Dependence  | VREF(T)     | Over -50°C ≤ T ≤ 150°C            | 0.645| 0.650| 0.655| V     |
| Output Voltage VDDA Dependence         | VREF(VDDA)  | 1 ≤ VDDA ≤ 2.5                    | 0.645| 0.650| 0.655|  V     |
| VREF dependence on VDDA                | PSRR        | vref/vdda at 1kHz                 |      | -60  |      | dB    |
| Phase Margin                           | PM          | PM of combined ±feedback loops    |      |  50  |      | Deg   |
<!--| VREF from Start Up Test Bench          | VREF(SU)    | \|1.35 - VREF(SU)\| at 100µs      |      |      | 10   | mV    | --> 

## Circuit
<p align="center">
  <img src="https://github.com/user-attachments/assets/a5326e8c-8563-4fb8-977d-4a9b34e025ba" alt="X">
</p>

## Piecewise Compensated Second Order Curvature corrected BGR
- **Second Order Curvature Corrected Bandgap Reference Schematic**
<p align="center">
  <img src="https://github.com/user-attachments/assets/ff6e6bf6-733e-461a-ac23-5595cf6b1d97" alt="Centered Image">
</p>

- **Second Order Curvature Corrected Reference Voltage wrt to Temperature**<br>
     - I have added an extra exponential current to Iref to cancel higher order terms in Iref (Especially ones from Vbe).<br>
     - This has been realized by pushing Iref current to a resistor and this is sensed by a mosfet in subthreshold region and this exponential current is pushed to Iref to cancel higher order terms in Iref.<br>
     - As you can see this Bandgap Reference has a very small Temperature coefficient across temperature making it very accurate<br>
     - **Temperature Coefficient = 5ppm/°C**<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/1b80d940-3ce1-41d8-8bd0-170feee953a5" alt="Centered Image">
</p>

- **Second Order Curvature Corrected Reference Voltage across Different Process Corners (FF,FS,TT,SF,SS)**
<p align="center">
  <img src="https://github.com/user-attachments/assets/e93fa2a8-b90c-47e0-9e59-2e60372731ca" alt="Centered Image">
</p>

- **Higher Order Compensation Current**
<p align="center">
  <img src="https://github.com/user-attachments/assets/9a502581-43e5-4b58-9e3c-86a54abb65f4" alt="Centered Image">
</p>

- **Second Order Curvature Corrected Reference Voltage wrt Supply Voltage sweep**
<p align="center">
  <img src="https://github.com/user-attachments/assets/1bbd5559-3357-4e8e-a73f-d4fa7126d1e9" alt="Centered Image">
</p>

- **PSRR of the Piecewise Compensated Bandgap Voltage Reference**
<p align="center">
  <img src="https://github.com/user-attachments/assets/46b0ac8a-9b5a-4d13-9531-29da682a4cbd" alt="Centered Image">
</p>

- **Stability of the Combined Feedback Loop**
<p align="center">
  <img src="https://github.com/user-attachments/assets/4f264ae7-e5e1-42eb-9fbf-592d42d3a127" alt="Centered Image">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/29adc811-3d15-49cc-b1e5-eca5379057ce" alt="Centered Image">
</p>

## First Order Bandgap Reference Schematic
<p align="center">
  <img src="https://github.com/user-attachments/assets/ab9723e8-e332-417d-8fc6-dd6d3e69cd26" alt="Centered Image">
</p>

- **First Order Bandgap Reference Voltage wrt to Temperature**
<p align="center">
  <img src="https://github.com/user-attachments/assets/98212ab5-0599-4d20-b7f7-460fb5422447" alt="Centered Image">
</p>

   - **First Order Bandgap Reference Voltage across Different Process Corners (FF, FS, TT, SF, SS)** <br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/bcf74cd5-2143-4e4a-ba26-32b5da708089" alt="Centered Image">
</p>

- **First Order Bandgap Reference Rate of Voltage Change wrt Temperature**<br>
    - **Temperature Coefficient = 4ppm/°C**
<p align="center">
  <img src="https://github.com/user-attachments/assets/38e08011-efec-408b-baf4-801ff1f0977f" alt="Centered Image">
</p>

## OTA
<p align="center">
  <img src="https://github.com/user-attachments/assets/9e0f1edc-f944-4a49-8ca6-bda8e6b66f73" alt="Centered Image">
</p>


- GBW: 4.885MHz (NN/TT)
- Phase Margin: 76.2° (NN/TT)

<p align="center">
  <img src="https://github.com/user-attachments/assets/c9df5386-ac4e-46e2-85b2-80d700506657" alt="Centered Image">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/2ba33913-77e3-4222-8c89-c8ca63ee6d26" alt="Centered Image">
</p>


## Reference
**[1]**. A high PSRR bandgap voltage reference with piecewise compensation Longcheng Que, Daogang Min, Linhai Wei, Yun Zhou, Jian Lv <br>
**[2]**. A 1-V 3.1-ppm/°C 0.8-ju.W Bandgap Reference with Piecewise Exponential Curvature Compensation Hongrui Luo, Quan Sun, Ruizhi Zhang, Hong Zhang <br>
**[3]**. A Curvature Compensation Technique for Low-Voltage Bandgap Reference Jie Shen, Houpeng Chen, Shenglan Ni and Zhitang Song <br>
**[4]**. Design of a High Precision Band-gap Reference with Piecewise-Linear Compensation Lei Quan, Yongsheng Yin , Xinbo Yang, Honghui Deng <br>
