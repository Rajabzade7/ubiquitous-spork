import serial // Serial is not included with Python. It is a package that you'll need to install separately. 
import time // модуль time, который используется для решения задач, связанных со временем. 
import serial.tools.list_ports // чтобы получить список доступных последовательных портов.

speeds = ['1200','2400', '4800', '9600', '19200', '38400', '57600', '115200'] // необходимо хранить список доступных скоростей
ports = [p.device for p in serial.tools.list_ports.comports()] // возвращает список доступных COM-портов
port_name = ports[0] // имя первого порта будет = 0 элементу
port_speed = int(speeds[-1]) // скорость будет выбрана первая с конца, сделовательно - 115200
port_timeout = 10 //  timeout порта = 10
ard = serial.Serial(port_name, port_speed, timeout = port_timeout) // создаем объект `Serial`, указывая имя порта и скорость передачи данных
time.sleep(1) // необходимо для стабильной работы
ard.flushInput() // чтобы очистить входной буфер

// раздел последовательного чтения 
try:
    msg_bin = ard.read(ard.inWaiting()) // в переменной msg_bin происходит чтение ard и возвращается количество байт в буфере приема.
    msg_bin += ard.read(ard.inWaiting()) // прибаление по одному
    msg_bin += ard.read(ard.inWaiting())
    msg_bin += ard.read(ard.inWaiting())
    msg_str_ = msg_bin.decode() //екодировка, т.е. преобразование в представительный вид 
    print(len(msg_bin)) / выводится длина, до которой дошли 
    
except Exception as e:    
    print('Error!') // выводится ошибка
    ard.close() // объект закрывается
    time.sleep(1) // он в одну секунду
    print(msg_str_) // выводится строковый вид msg_bin
