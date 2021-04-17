# MCP39F511A-SMBUS-Battery-Monitor

This is a smart battery monitor based on Microchip 24-Bit Single Phase AC/DC Power Monitoring IC-**MCP39F511A**.



## MCP39F511A Features


The MCP39F511A device is a highly-integrated, complete single-phase power-monitoring IC designed for real-time measurement of input power for AC and DC power supplies, making it suitable for a wide range of consumer and industrial applications. It is capable of detecting the input voltage types in order to select DC or AC mode automatically. It includes dual-channel Delta-Sigma ADCs, a 16-bit calculation engine, EEPROM and a flexible 2-wire interface. Separate AC and DC calibration registers are provided, to ensure high-accuracy measurements in both modes. An integrated low-drift voltage reference with 7 ppm/°C in addition to 94.5 dB of SINAD performance on each measurement channel allows for better than 0.1% accurate designs across a 4000:1 dynamic range.

Additional Features

-   Real-Time Measurement of Input Power for AC or DC Supplies
-   Power Monitoring Accuracy capable of 0.1% error across 4000:1 dynamic range
-   Automatic Sensing and Switching Between AC and DC Modes
-   Built-In Calculations:

-   Active, Reactive, Apparent Power
-   Active and Reactive Energy Accumulation
-   True RMS Current, RMS Voltage
-   Line Frequency, Power Factor

-   Dedicated Zero Crossing Detection (ZCD) Pin
-   Dedicated PWM Output Pin
-   Automatic Event Pin Control through Fast Voltage Surge Detection
-   Fast Calibration Routines
-   2-wire UART: Baud Rate up to 115.2kbps
-   512 bytes User-accessible EEPROM through page read/write commands
-   Low-Drift Internal Voltage Reference: 10 ppm/°C typical
-   28-lead 5x5 QFN package
-   Extended Temperature Range -40°C to +125°C
-   AEC-Q100 qualified

Device web page https://www.microchip.com/wwwproducts/en/MCP39F521

## Applications

   It is intended to be used in systems with **SMBUS** communication like **DJI** smart batteries, **Ardupilot** flight controller systems and any other system that need a smart battery.
   
SMBUS specification http://smbus.org/specs/

A practical example it's given with ardupilot flight controller https://ardupilot.org/copter/docs/common-smart-battery-landingpage.html

Choosing the smart battery type in Mission Planner 
![enter image description here](https://lh3.googleusercontent.com/Nz-Pm1pWJTOUIaxA-z57OdngeumQ3byctwtXQpXhdJjJvFH2G75ZisiXTt_YqtdU_KT-H7r8BxtbJXsmjkfiC7dk_nBpC6IXZzAnMZEXXUMdKEmUa3rm-YRL7fMDNnnFpL4B_h-DdeFJD3oupeDf4Xo9g6Dn9DS2gAJ0pONZQpTh-VDq5p-k_-YIqCLixPxyzsFc_1xiJCDfkdUAY84rwKvuFDElOazsuFaVKV0OYDmp81ejp-FZe_ThhOaoDbhUK3veCs--ZQ04HXqB6wcP_gjUEn03-y1hBO-J8jzdc3NW5SWLbFloRVrCuE_Z4dpi4lbXtnajVtCz--DkNRfJn35n_iG8OE6iFba7EjcfYEl6NRTXY2O11-NxNzWuyFSxKlbdTLcmpHaBDyAThOB1OaTAIUaLeAW-yXNobNUMilDSiB7Rc8qEFtWbEncP-JZ5lQuWVdd9xRi5KGi0K-ZaL8leC5z2iDeEBrMUa4RmStFe_cKMEo2vfOeeFzlenm7YsotuGxmqYq859y3Np_nV0buwtyf7UizVAZ8er6XtD1JjNKFOalG4K1F4rl6ZHhaMYLripbNF4uViVaMyafElcr7H9fH7AwB1MeJp1bWUgWmZWsb3DcUdldw8J3FPW6YNFXn1ap8luLlEaPn9geQMB6E0DqHzDcmETp9U2jmAye3svp2CE77IcOm-HygEWqvwdtamlR5GBlN8k-47oyUWkofI=w1836-h530-no?authuser=0)
Battery data reporting in Mission Planner

![enter image description here](https://lh3.googleusercontent.com/hcL6z32l4YAc2mXp1lRe-uz-v7Su1y8u6KC85UWVEVa2h-mTP8tP8_Yr1OnQzo8a2IyKg1VMdzUMCdkijQlNhCU0yPWmhL33xeFpH7a7uBdMMz_tRICi-dvyxnP0DDylh35PQnCFl60mTG2XjByv4Qli2t6q900__D6xdWrOWyZQZdKO7zM_tFJhuQe06LKGHuJatR3tXRFOFjUtTWwS1DIstCho5Xoz_FHmOcj1dVUWz1azOfiUONmOsL_i_5rTZ7WTMRXeH9sP3GqeXYw1sPjtdb9DBtcg-om1B6oxMkscEvvuzQSTrLD-NZQRyu-2-7NognPl_X5dV5sD_S0Jai_J_aSO8NOHEJVnFFphHFaoQKyY15fqkSwAvkb8-c8YipZhLy75yid7pzNplYG0E-p7USjREm0Al7NKdbD5wIMpE1cv0AgFisqb7SkHwfYYluO2STIA-kzLQgiWZRKRG38QT0zo8B5esi76KOeh-uHfz7SQ7MU0d5Ln2dgTNY0b-8BjsTX0TIBBSyPbv4L0qBYSE3ME6PcoJj6SK71nKDl83wb6lgiEU1xNynSRFNRW7vpk_mDQLEjSemAyzN6C3FQizCwogOTMK9zaPpyH_K0KxfNqvc5UT8P0spnnQJPfTamQe6bQoc1ysl-6Wmv5NA-OSXF4PPYKZTu6CdivQMBtUmi3RDi1pf2AEfixdiAprrH7trKxJpnbQ4srLOLTSRKQ=w1834-h1268-no?authuser=0)
The system can provide the standard smart battery commands:

    const unsigned int Temperature            = 0;                            // cmd 08   r     - °C
          unsigned int Voltage                = 0;                            // cmd 09   r     - mV
            signed int Current                = 0;                            // cmd 0A   r     - mA
            signed int AverageCurrent         = 0;                            // cmd 0B   r     - average current for 60 sec
          unsigned int RelativeStateOfCharge  = 0;                            // cmd 0D   r     - %
          unsigned int AbsoluteStateOfCharge  = 0;                            // cmd 0E   r     - %
          unsigned int RemainingCapacity      = 0;                            // cmd 0F   r     - mAh
          unsigned int FullChargeCapacity     = 0;                            // cmd 10   r     - mAh
          unsigned int RunTimeToEmpty         = 0;                            // cmd 11   r     - min
          unsigned int AverageTimeToEmpty     = 0;                            // cmd 12   r     - min
          unsigned int AverageTimeToFull      = 0;                            // cmd 13   r     - min
    const unsigned int ChargingCurrent        = 4000;                         // cmd 14   r     - mA
    const unsigned int ChargingVoltage        = 4200;                        // cmd 15   r     - nCell * 4200mV
          unsigned int BatteryStatus          = 0;                            // cmd 16   r     - status
          unsigned int CycleCount             = 10;                           // cmd 17   r     - #
    const unsigned int DesignCapacity         = 9000;                         // cmd 18   r     - mAh
    const unsigned int DesignVoltage          = 11100;                        // cmd 19   r     - nCell * 3700mV
    const unsigned int SpecificationInfo      = 0x0021;                       // cmd 1A   r     - user
    const unsigned int SerialNumber           = 12345;                        // cmd 1C   r     - #

## System Block Diagram 
![enter image description here](https://lh3.googleusercontent.com/nfrRgmDpWArEZyKCqp56XCvQEb8YLTjk311lAF-9KTVOoLHCybbQCt4Gp0QiAcUMQO0m9Y9CEkIWEDdodZbueM5s8twYw3EhHnEBz-cypKiFNXePmYkJRBnyDVswa_BuvIPQL80JcJxGzYxEFiw6Pn0vBqQOgOznodHR9tf3NdyQh5yWdnjKgCETpPf-ctZdyVy7ImQgH4NyK7Jt69VEJ9luRyIH2Qoq0eo6IrZcFbj3fqAhQCt4UN2x6pTz7BEZ7KgKfrW_vacdC8l-r5AkF_2ivZwJXE7i0ARP2ga5neRCIa2m1I07tp6uyfrv7z9X0wdQDZM7CJM70GdfZl6WFoFxzvCSf_SCvJahmNEUlSQoO6n22N0XUNu4vmhxn-30Dr00B_xZ0gqaAwcFRs2rczKQbU15Z3tDJKognfqB1A9r-wMcASAMEbRgdg3rNH1FMsZl2HDjMhtaW4W-IJd5-Obj3osu6AcYGn68IH3UyQYj3-24yCvnnAA07AHNfiMxxelSVnPaw-AzV2jzvkqdmtLrpSpmwddrMVBxRcrY2FA3zZBi8LdEhlRhW5o_JE4_L6Y_XjObBQv2D70YOpnCLrbp7rvi5vDD1jXDJksEqsMuZtHWvimPGflz341RZ2a5Q1n3xbqI87AmG2Lsxtv-7pDxe2fKZk7m0JzykRWY_JDa0Fw9or5dWU1lTQEyOyHnEAat772VmuGpi53au52L_RsM=w1055-h808-no?authuser=0)

## Application Block Diagram 

![enter image description here](https://lh3.googleusercontent.com/DRrNh55AveYvC-94fU-31DCoUqkRBPB8UTMdCdU7ND902tVJEhDFkg43Dc6Bc1atgFdoPf5TVL1H_UeL5eVNndZsQXybrotDiFZ8bH8874Lh9UvqZgNAY723LVcLeZqs4t8z3GmMDSTV3qTFXqYnJB7F2xriXrzmw-EHvE8fCHHicjIhoM2yC64nnVO_yJ1KoxgYxK-RZLn5eTp1hANRHa1rPthQHEoM5xwlJ6lWbmczDNknfky2wl4o6tAlUhyUECrrZQJDYMZkjGLF9PCyQd7VVUIq94aQ2VljQ8d65HTChVENfD-XHHWvk9i4viuUDNxH40ZIsCBYgdE2Sh8uMJuKohaWXsnseKRklLprJdB4gdlr8t3D_WOzMpkZVv6Yd2ZjC_L1ZlJqSAq6fLjPUQaTuAh7LZCGzeZKulj3PucyChBGsq_76ntG2GIjk6uTX9QfDfn998xeNLod0HHS6lUHeKncppxoXoAa93nLtFQpl_E_njTRceHfqY4G5QieuBK9cBXg67qW7lnW3SBcIEudWxqm3CptJsSXz-Jaom53rnqeMpNTHrmgPF1u31HCn2UUwucga6jqSNYs4G895lEsY7ClQZhmlpbVRyzlokqENlMLG-BG6u2xF79fBgVJIiJK3LlmrxiwCq22MzxGAMHFEPLwELIcDV8-lGDhM6G1G7vEdhgLtT1xeH9WqpY_rKqeMvsf0t8KaLdJY7QB74HL=w1918-h887-no?authuser=0)

## PCB

The PCB design its done in Altium designer.

![enter image description here](https://lh3.googleusercontent.com/Inny6Rmvvf0m7qI5NzU4f-6bc4WiuC_tW0TJT-wi3_VeKG1nn7TIgDNy4kCZNQuXjgsIBpZeTB_FxmBoI4RloEczqI8ZF5iHU1IWLeGLQN7i9x_bajdC9R54vAHWiUMYzg8N9qbkvoBzFDQcEqKUZttaTfVJN2GFjP1ZiV5KQ7LautGzyS0qeRmKqKJtJkxkT5-gsmcvmUxoEw0tm6syPitnR0MN0PGUP9r01ozemO-JS6V6NV_FJS0d-4Kz3zjmrA6jkpK5ReXr_uGfcAGlGXRt02loo2mbVI_ZL4kHQwP3eAOnxz6EOzmyDwtW6bjm6NvaRXlJ3rKsoIOJhGolH0s4-Z-uZc89oMOy0ck9Oz4TPrPP_MiNWRMcF16M-2ZuLLysi8o4kbqnHw40vNUrgjQHTQTQ_da0aB5saOhglsN-ifu0dg5DnDTJ6dvyasGPixPBfU0bLjVa61xWQhEhq2Fblyqid-zV5QNJ60OX27c6_8idUUEDptB7be9dfE62gTG0GF8BapZfAtnQBvwR9lGLIXwRi9pvq4yVGH21567V4AE5vw07MAIErqIsrVUcWSUDtueVocSwyizqIX5hYU2luGurq2PiK7ayoGM5L-IKYEmEu0vQBjFs7kELH6Rml59u3bKCyTOD9WKHzUJ4dlIfc0j48A6MQ0Iw3NENY5PAz7mirUMMpPSLrKI5LZB6qpvQXv-0Q6Syn04t4otKG7Z7=w1176-h850-no?authuser=0)

## TOP

![enter image description here](https://lh3.googleusercontent.com/0sR9tUNKSVFZ6ngiYEknXE-KwPa7t5PO1uAQQ_g4ya1COkfoZOUy0oj9Js52t1xWhz2JlhvSx76p3RtglKbGnLkOzIt9pv1MPGV5Sxdj8ryAw51JZnaTyrq91bXKyyIfq2Vq7k-_8rFRcX5o0eIySgb4kRB_VlrbDvTnj-8xJ5zTTyW8rrqgl9GSxv1urxdUn-I_fg64qsgv1Sfoakg4y-vUiON9J4Gc8i1RsK75fjf_lc8nJtbX_lxdqmw2s2HDFys-jbpBDwfSzt3Z6XyVjGvqqiSYgrNp9Pt4FYDQDMLRxmLuCcQi7piRM-tGrdP2lefcoJxhz1gbRHrxdan3rSVsXHlCxucOXOLNjBoY9zJRqgWjYWKRm0gVOu4Tc3VgzCe99qazKBEsE0MHOvvQvP7oYFsplXRfRddjTs0aNSwyK9Lgl-W60Xeey_xyr5JUM6A7QJc5QbhUCxaDCPgB9_Ertab9Cb_sGdz1uXuKHu1L4wNiFVXbqhgbUvmlw5LsnTnLnT7vytRMTtdHi6aEkxmndAlLbTQ9H0cNnrnbpBNgTXz8Or9psKIR4NS1KITmzkdPrevvzd4RhDdAe7073JrpFBXhIbN1CyZ7O95SMAapovqWK0KeSTW4G_I1wW1bmSzPG_bIP2SE10cQsAgCM4BiVJYsTgiDm7wfHF0GOCfiDjttPuf9CsdA2fxgVI1oc1zswRgp59O-00uM6rDWpwVS=w1918-h937-no?authuser=0)
BOTTOM
![enter image description here](https://lh3.googleusercontent.com/rPR1jMwrJ2FJ34PbIamnCQ8-TPfeDdgksoXUgEFM9N8Z4wVGwKos3V2guCtpA-zUaferPNvGgB86Hb7ek1Z0SlTtT05s_ZU7YeKQvc_JTx-5m26-6OzR4qa0dT-AjNoxIqeIUtzb-AaNCtleHNBelAL5BRQ6UEw5eMZDgkz3He_v-_PBoI_h6sKH4izuwBofXf69GKJzJzbUBwjKVEuZfrHIk_ZVW0S9TtgYAitPvASqvV4MqvVqKw7pTYErn4JEfpdK7ykFOWSgUcLWRRoDKDtKFwoAQjHxntq_P6783kVtnDwRAiT93_qt91tH7AyhaaK-38fOPRLQUJVnrUqkipA9xwIHdyCWz7Rt6e5YknqrWHCuiXsYi3f_AHSDx8wd86lKlHUTTEKjYW6KfO7yG5RCnFaCLioicc4J1AsBQ0juU58NbK36MBBQ9KG41-2WRk1PLKxU60ct7Iwe-s1KFMT3Ngzak5NtZQ31FriVmfsf52eoBBRGu7we4xRk3QrTyHFt13FySNwyCRAPXgpSUfZtm450nAbYbq_8sOQ_ccbKzFwzgJuKQqXhel4UCpRDEQlht7-Blf93ex0187YSKkbOAJ5kAp0kbFOeYn9ITF1kcpZL9H6YmtXSr4rR_VcT3zI5oGp4ag0itBFo6-Vl1kX_znmLpBHDXUOlcnY6Ymv4Xlth9WUJUXwaPU6o3muWVlhkwsSkzLH7p-ROczdZqT4S=w1918-h934-no?authuser=0)

## Schematics
Microcontroller

![enter image description here](https://lh3.googleusercontent.com/mSzP7UsCJ-I1wtHEh31xxDW4gVl6GFHgebOBKciEZVFpPPXRAUbkpExHZWhTk8EMTdNuoJgXLgYo6xoNQa0jmwH8--gCtyMGX1775qpx-YiO80Rn3pq7rpd_Ckj_UxwUKTF-6f2mpWWj86FpqvNTYPcsQeqf7HOXHYqJ6jPhNUhK5_n0lqXcrEL82m1dIYZ3g5nmws4L2BrYNKWv5veKXrUbyfuvi8cFwaaFVTtWIjIbYvMqveechPfYSm7bxTQljnWBcOfhsUhQckiqrI4nzsyLbzXMmKL_G7vGiIhNlCeZ5SNlEE3SQXjweIunII8sl9ORiMssU9KEW7p_qqqQ5Ap-8xpteJxnnA_gTb8Tm7z36rreaXDSbKTRDatWzDGvvDgZ0ixW3rBv889DtG2e-qq8ydhrsf9QSUcvVN9Q9gUtmRky2MhTq-Nsr0i5hs_Yk-KB17zMpO8xDb2WTGK3cj-oFsc4tgJ8scdM8g1QGGGM9p-UUdbet_nvV5skuFMTF4US3bM6--IkLced9AozEVEbt1bDB_7kWYXwSwlM9HmU2cbbElPsIJKNOfZIIUw3jJnJBN6XGrWKxR4qKbnGUM4LYg4l7H-_96HjXq2KPoc1cF8mTKakyijfJ8nsMnl0rMCR8fT6lBwB1I6EQOemr3ryUqRmf4QeZAlUWiR0Dv5A4024yEGmfg8FLKwekpzM6cp5EnETyo0YdRn7gbTxj2y-=w1918-h1373-no?authuser=0)

MCP39F511A

![enter image description here](https://lh3.googleusercontent.com/71c8oBwLsAw3XT1_llCBbGCrN1vHdI6WyFuoPbn-n6hjH4qT6ILGn9BV-Au-fF9diRwI35YrsSBMYYvXuIxJgCC8dq43H4qciqMhepObRPCbxDSPZNHNLKcdOsivBCWZ0nG9gf40MIak2imfClUkM-1lAOGv8q2kXlkWNcYT_9cK0_JBJezKHLTUZyWRXvWmj_GTYzRdhcB-7upScwjt-Cgn2_lq-30iSD-xc46xCy00rQa3NFlVAeiphWEmKYKFq_3n-J61pa7MVzj3k8YzO6PjLSBoVjQ9ITV6VsQNxZsNsCtMvnliIOlXgcZwrRxlWmCr7GJOpSWHdtXbt1DwoTEmSN07sRXPHRipHww3QuwUI2OVgqg48d1AR1XkS9K1QRGg_n89-5XNI71qq2tyObMF3vlkMjVZt4IJzF_NuIC7agfyMP3VLMQvl6t0hu7pivF0fTANVHaYl34Acv1pf2P46zFLfE6erxrGnU7KG8AMShHlOwfxwMEvuxMBNqr9GUptMglyUfso5aW2tKJTxKbCnWglpo5hWDPfntF-XsjKTm-uvZtKE3X368FnIy-BBqodXNUO82dy5mtRKHHZeX0nlatHaKzOQRUM53l-jezDoN1JD7vCpEtO39NSbXP2y5H3IvFKXBQkiQXDRz-nvqQ-G6-py0AQPdNsMaxTf2tt_n16cSutcxG8LF806FfZQ2WWerKyLc2Qv5gx9u1LsFcV=w1918-h1375-no?authuser=0)

Buck Regulator

![enter image description here](https://lh3.googleusercontent.com/3hX1JJJAWlHgz38uZvJ5Z_MsRw8_mWo0P34lmFC91bp2TH8DcgoOfaAnUo8M9oZivhTsR7epX7uRan9CzmzavXLvqW2MIJqbOC5OgTRkZitb4S7KijOGK8MGmobo7R-SQCUuBXHAHgWpKFXdyiLURvV5ozS9iYuUwVU9DcG1IIKGAe6JK3C_3pwoTZqG6YIP1HtLqDA1LiZFebY3lRxuRbmfOveRzLbbwlPDoZ0xZNlN-hBbp-gNxj9XdTQY76bIAakv6r6n0HzmZSgjvB2mb_2KPlmBVNxtLrW-TqiiHiCWxUf5ojCHOJeUHCLRVxlhskrePAg9ikouW9eMPJhHGeQRZxx4pYWEf6M0nAgm5EmWYQfHy-LPpB4PL9lpnx7XLBnnmH6i8BeY7xrULijf0EwvY7Daw9vaXAyBebrbHWAAoZhhoDbocHHxFKiJlIJURQIZ9f5Bswlx1iDy27pZbDrgyG4p2EhNj1VDjKuYWrSa5ZD57djgrcQYP-Q_EzSIHM68lhZFAZyyv3_mYYXah1lnthwqYoSod9SDqi9BXVG0P6o0oGknBrLBJK2GVADc4ZIx9qSIWjnMZMV0MsraQjH1EPt3RxrI-1CDvs9OIF04ArMSQY-Ro6qdfAmsOgk_gZu3eHLdlpHZlJMZRFf6aGfykWN8iz7d8axungwygGjQVERNUeomdhppiwSitCu4cdda6skUhpkVPSvxlK8uVtDO=w2432-h1740-no?authuser=0)

USB

![enter image description here](https://lh3.googleusercontent.com/EyopO2MBJqn86X5iwVRczDiwxQ_dlM-pvUYlvo_hllaSmSesBSFkcyJUeM-JFxQIsymLDzD51IoTAnCTUEGUCeY5mHrJrSmkJKAXetQZMpycmrOCMRjDTtCohmoVKAhlk2B9lT_pwq5EZDTEfzaQn33C-mtTcQYOvAIPMBvoFkIXDtYRMZrN-F7SgPnlkMOW4oTta7E3s5CXOaU12qGl0XGXdff-rzOjFwpuL7X5UR1Joy008vd349rsd1XBiVQ2l4dpzuxgnOw_mSZzMlNy9epNs5oHKkh-xash22p4TuPwiRo5QduUHSX6dX99Qn0d1my3T2zNyut0M4iJlnIIFvUXDPpNN9lqnggnswdYkR1D49O5fEqUeEixVZGKAVr2ZwvYO9dOG8PF9bZeqOWYmI87-CeL9YVnCs7_NLCNtpZWpUtVWPESqz1U1jFL9bNT_ICjke_mIjPsqk1r_HAKkDD--ROKQLTSn8PAwGHjKaFEN7tlJRPSgOan0BbrQjJ-3xtZ77Pce1J1ikEsopTAVWXYGlCLtA5MiVVHaoHV0B4ng1xEYtC_Fo-HUVTZsoxFlCqdfQCgb-Y2lr5mYgocO1mQxl28s9zORJFYd7RCdfgLCpA-monuS3Z1TAHVRwzM4l6XvjD8xTHzcdi4-Tji474VwojrCQComzbHAhdyBIX_1s9vbzrl-gDI2toxTqMT6zSVPua5jw7MQ4zDLdKhJr8a=w2116-h1511-no?authuser=0)
