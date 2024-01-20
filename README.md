dtbo compile

cpp -nostdinc -I /usr/src/linux-headers-$(uname -r)/include -undef -x assembler-with-cpp  tc358743.dts > tc358743.dts.preprocessed

dtc -@ -i /usr/src/linux-headers-$(uname -r)/include -H epapr -I dts -O dtb -o tc358743.dtbo -Wno-unit_address_vs_reg tc358743.dts.preprocessed
