# Steps to zephyr repo
mkdir stm32_h755_zephyr
python -m venv .venv
pip install west
west init stm32_h755_zephyr
cd stm32_h755_zephyr
west update
pip install -r zephyr\scripts\requirements.txt

# Build and Flash
west build -b nucleo_h755zi_q/stm32h755xx/m7 zephyr/samples/basic/button --pristine
west flash

Note: Below steps are additional and were followed by me to create this project/board specific tracking.

# Add .gitignore in top level to ignore stm32_h755_zephyr folders
"Ignore build, modules, zephyr, bootloader, tools folders"

# Move samples into board specific folder to track changes
# that I want to make wrt my board STM32H755ZI-Q
cd stm32_h755_zephyr
cp -r zephyr/samples/ stm32_h755_samples/
west build -b nucleo_h755zi_q/stm32h755xx/m7 stm32_h755_samples/basic/blinky --pristine
west flash

# References
https://docs.zephyrproject.org/latest/develop/getting_started/index.html