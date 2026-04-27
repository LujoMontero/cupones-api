<div align="center">

# 🧾 Cupones API

### Pruebas de Regresión Automatizadas · Flask · Pytest · GitHub Actions

![Python](https://img.shields.io/badge/Python_3.10-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![Pytest](https://img.shields.io/badge/Pytest-0A9EDC?style=for-the-badge&logo=pytest&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)

[![Tests](https://github.com/LujoMontero/cupones-api/actions/workflows/test-regresion.yml/badge.svg)](https://github.com/LujoMontero/cupones-api/actions)

</div>

---

## 📌 ¿Qué hace este proyecto?

API REST que aplica cupones de descuento y calcula precios finales con impuestos. El enfoque del proyecto es demostrar **pruebas de regresión**: cómo detectar automáticamente cuando un cambio rompe funcionalidades existentes, usando un pipeline CI/CD con GitHub Actions.

---

## 🏗️ Estructura del proyecto

```
cupones-api/
├── app/
│   ├── __init__.py
│   ├── cupones.py     # Lógica de negocio: descuentos e impuestos
│   └── api.py         # Endpoints Flask
├── tests/
│   ├── test_cupones.py  # Pruebas unitarias de la lógica
│   └── test_api.py      # Pruebas de integración HTTP
├── .github/workflows/
│   └── test-regresion.yml
└── requirements.txt
```

---

## 🚀 Instalación

```bash
# 1. Clonar el repositorio
git clone https://github.com/LujoMontero/cupones-api.git
cd cupones-api

# 2. Crear entorno virtual
python -m venv venv
source venv/bin/activate    # Linux/Mac
venv\Scripts\activate       # Windows

# 3. Instalar dependencias
pip install -r requirements.txt

# 4. Levantar la API
python app/api.py
```

---

## 🎟️ Cupones disponibles

| Cupón | Descuento |
|---|---|
| `BIENVENIDA` | 10% |
| `VERANO` | 20% |
| `VIP` | 30% |

**Cálculo aplicado:**

```
Precio final = (Precio base × (1 - descuento)) × (1 + IVA)
```

---

## ✅ Ejecutar pruebas

```bash
pytest
```

---

## 🧪 Pruebas de regresión

El proyecto simula el ciclo real de detección y corrección de regresiones:

**Paso 1 — Pruebas en verde ✅**
```bash
pytest  # Todos los tests pasan
```

**Paso 2 — Simular regresión 🔴**
```python
# En app/cupones.py, eliminar el cupón "BIENVENIDA"
CUPONES = {"VERANO": 0.20, "VIP": 0.30}  # BIENVENIDA eliminado
```

**Paso 3 — Detectar fallo automático 🚨**
```bash
pytest  # test_descuento_bienvenida FALLA → regresión detectada
```

**Paso 4 — Corregir y volver a verde ✅**
```python
CUPONES = {"BIENVENIDA": 0.10, "VERANO": 0.20, "VIP": 0.30}
```

---

## 🔁 Pipeline CI/CD

Se ejecuta automáticamente en cada `push` o `pull_request` a `main`:

```yaml
on: [push, pull_request]
jobs:
  regresion:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: pip install -r requirements.txt
      - run: pytest
```

👉 [Ver resultados en Actions](https://github.com/LujoMontero/cupones-api/actions)

---

## 💡 Conceptos aplicados

- **Pruebas de regresión**: Verificar que cambios nuevos no rompan funcionalidades existentes
- **Integración continua**: Ejecución automática de pruebas en cada commit
- **Flask Test Client**: Pruebas de integración sin necesidad de levantar servidor real
- **Pytest**: Suite de testing moderna con fixtures y reportes claros

---

## 👨‍💻 Autor

**Luis Montero** · [GitHub](https://github.com/LujoMontero) · [LinkedIn](https://www.linkedin.com/in/luis-montero-if/)
