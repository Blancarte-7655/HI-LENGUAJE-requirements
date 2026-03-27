# Dependencias e instalacion en entorno virtual

Este documento resume todas las dependencias del proyecto y como instalarlas dentro de un entorno virtual.

## 1) Dependencias del proyecto

Las dependencias se toman de `requirements.txt`:

- opencv-python>=4.9.0
- mediapipe>=0.10.9
- torch>=2.2.0
- torchvision>=0.17.0
- scikit-learn>=1.4.0
- numpy>=1.26.0
- matplotlib>=3.8.0
- seaborn>=0.13.0
- Pillow>=10.2.0

## 2) Crear y activar el entorno virtual

### macOS / Linux

```bash
cd /ruta/al/proyecto
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install --upgrade pip
python3 -m pip install -r requirements.txt
```

### Ubuntu (maquina virtual)

Si estas dentro de una VM con Ubuntu, primero instala dependencias del sistema:

```bash
sudo apt update
sudo apt install -y python3 python3-venv python3-pip build-essential
```

Luego crea y activa el entorno virtual en la carpeta del proyecto:

```bash
cd /ruta/al/proyecto
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install --upgrade pip
python3 -m pip install -r requirements.txt
```

Si prefieres instalar libreria por libreria con sus versiones minimas, usa:

```bash
python3 -m pip install \
	opencv-python>=4.9.0 \
	mediapipe>=0.10.9 \
	torch>=2.2.0 \
	torchvision>=0.17.0 \
	scikit-learn>=1.4.0 \
	numpy>=1.26.0 \
	matplotlib>=3.8.0 \
	seaborn>=0.13.0 \
	Pillow>=10.2.0
```

Para validar las versiones instaladas:

```bash
python3 -m pip show opencv-python mediapipe torch torchvision scikit-learn numpy matplotlib seaborn Pillow
```

Opcional (si usas interfaz grafica o quieres evitar errores de OpenCV en algunos entornos):

```bash
sudo apt install -y libgl1 libglib2.0-0
```

### Windows (PowerShell)

```powershell
cd C:\ruta\al\proyecto
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

### Windows (CMD)

```bat
cd C:\ruta\al\proyecto
py -m venv .venv
.\.venv\Scripts\activate.bat
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## 3) Verificar que quedo bien instalado

Con el entorno activo:

```bash
python -m pip list
python -c "import cv2, mediapipe, torch, sklearn, numpy, matplotlib, seaborn, PIL; print('OK')"
```

## 4) Ejecutar el proyecto

Con el entorno activo:

```bash
python main.py
```

## 5) Recomendaciones

- Siempre instala con `python -m pip` para asegurar que pip use el interprete del entorno activo.
- Si estas en macOS y `python` no existe, usa `python3` en todos los comandos.
- Si cambian dependencias, actualiza `requirements.txt` y vuelve a instalar con:

```bash
python -m pip install -r requirements.txt
```

## 6) Nota sobre PyTorch y GPU

Este proyecto declara `torch` y `torchvision` en `requirements.txt`.
Si necesitas una variante especifica de CUDA, instala PyTorch segun la guia oficial de tu hardware/driver y despues vuelve a instalar el resto de paquetes.
