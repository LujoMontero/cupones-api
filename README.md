# 🧾 Cupones API – Pruebas de Regresión Automatizadas

Autor: **Luis Montero**  
Repositorio: [github.com/LujoMontero/cupones-api](https://github.com/LujoMontero/cupones-api)

Este proyecto es una API construida con **Python + Flask** que permite aplicar cupones de descuento y calcular precios finales con impuestos. Fue desarrollado como parte de un **ejercicio guiado de automatización de pruebas**, aplicando pruebas de regresión e integración continua (CI) con **GitHub Actions**.

---

## 🚀 Objetivos del proyecto

- Construir una API REST básica.
- Aplicar cupones de descuento a precios base.
- Implementar pruebas unitarias y de regresión.
- Simular y detectar errores de regresión.
- Automatizar pruebas con GitHub Actions.

---

## 📁 Estructura del proyecto

```
cupones-api/
├── app/
│   ├── __init__.py
│   ├── cupones.py         # Lógica de negocio
│   └── api.py             # API Flask
├── tests/
│   ├── test_cupones.py    # Pruebas unitarias
│   └── test_api.py        # (Opcional) Pruebas HTTP
├── requirements.txt
├── .github/
│   └── workflows/
│       └── test-regresion.yml
```

---

## ⚙ Instalación

1. Clona este repositorio:

```bash
git clone https://github.com/LujoMontero/cupones-api.git
cd cupones-api
```

2. Crea y activa un entorno virtual:

```bash
python -m venv venv
venv\Scripts\activate     # Windows
# source venv/bin/activate  # Linux/Mac
```

3. Instala dependencias:

```bash
pip install -r requirements.txt
```

4. Ejecuta el servidor:

```bash
python app/api.py
```

---

## 🧪 Ejecutar pruebas

Para correr las pruebas unitarias y de regresión:

```bash
pytest
```

---

## 💥 Simular una regresión

1. En `app/cupones.py`, elimina accidentalmente un cupón (por ejemplo `"BIENVENIDA"`).
2. Ejecuta `pytest` y notarás que falla `test_descuento_bienvenida`.
3. Corrige el error restaurando el cupón y vuelve a ejecutar `pytest`.

---

## 🤖 Automatización con GitHub Actions

El archivo `.github/workflows/test-regresion.yml` contiene un workflow que:

- Se ejecuta con cada `push` o `pull request` a `main`.
- Instala dependencias.
- Corre las pruebas con `pytest`.

Puedes ver los resultados en la pestaña [Actions](https://github.com/LujoMontero/cupones-api/actions).

---

## 📸 Evidencias requeridas
Falla en consola

![Captura de pantalla 2025-06-17 220406](https://github.com/user-attachments/assets/ef43e8d0-b030-46a3-8a47-00b98535835a)

Falla en Git Action

![Captura de pantalla 2025-06-17 220617](https://github.com/user-attachments/assets/8e43f45e-6ca7-49d9-8bda-642289c36bca)

Test aprobados
![Captura de pantalla 2025-06-17 220725](https://github.com/user-attachments/assets/eaefe86e-02bf-4e8f-893d-2252a022405f)

![Captura de pantalla 2025-06-17 221219](https://github.com/user-attachments/assets/a86219ce-f1b7-4acb-8cd7-3d928af05853)

---

## 🧠 Lecciones aprendidas

- Las pruebas de regresión permiten detectar fallos que afectan funcionalidades previas.
- Automatizar las pruebas garantiza calidad continua en un entorno ágil.
- Integrar pruebas en CI/CD mejora la confianza del equipo y acelera la entrega.

---

## 🛠 Tecnologías utilizadas

- Python 3.10
- Flask
- Pytest
- GitHub Actions

---

## 📄 Licencia

MIT License © 2025 Luis Montero
