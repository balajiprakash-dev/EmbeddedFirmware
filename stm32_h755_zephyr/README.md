## Steps to setup Zephyr

```sh
mkdir stm32_h755_zephyr
cd stm32_h755_zephyr

python -m venv .venv
.venv\Scripts\activate

pip install west
west init
west update
pip install -r zephyr\scripts\requirements.txt
````

---

## Steps to build and flash

```sh
west build -b nucleo_h755zi_q/stm32h755xx/m7 zephyr/samples/basic/button --pristine

west flash
```

---

## Steps to create stm32 board specific project tracking

* Below steps are additional and were followed by me to create this project/board specific tracking.

* Added `.gitignore` at the top level to avoid tracking generated folders like `build/`, `modules/`, `zephyr/`, `bootloader/`, `tools/`.

---

```sh
cd stm32_h755_zephyr

cp -r zephyr/samples stm32_h755_samples

west build -b nucleo_h755zi_q/stm32h755xx/m7 stm32_h755_samples/basic/blinky --pristine

west flash
```

---

## Reference

[Zephyr Getting Started Guide](https://docs.zephyrproject.org/latest/develop/getting_started/index.html)

[Nucleo H755ZI-Q Overview](https://docs.zephyrproject.org/latest/boards/st/nucleo_h755zi_q/doc/index.html)

---