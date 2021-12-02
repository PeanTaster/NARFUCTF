# ReveseOrReverse

## Описание: 
Видно не стоило переворачивать ноут с HDD вверх дном. Там явно что-то накрылось...

## Решение
Если заметить, то можно увидеть, что файл отражен (Байты задом наперед). Для решения требуется отразить байты. Гуглим как это сделать.

Сделать это можно такой командой: perl -0777pe '$_=reverse $_'  [input_file]

Другие примеры: 

dd if=/dev/urandom of=/tmp/a bs=1M count=1
dd if=/dev/urandom of=/tmp/a bs=1M count=1
LC_ALL=C tac -rs $'.\\|\n' /tmp/a > /tmp/r

time perl -0777pe '$_=reverse $_' /tmp/a         | diff -q - /tmp/r
time xxd -p -c1 /tmp/a | tac | xxd -p -r         | diff -q - /tmp/r
time perl -0777 -F -ape '$_=reverse@F' /tmp/a    | diff -q - /tmp/r
time LC_ALL=C tac -rs $'.\\|\n' /tmp/a           | diff -q - /tmp/r

CTF{tryhard_ben_10_reverse}
