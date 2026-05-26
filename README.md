# 📱 Mi Cartera Móvil (Aplicación Web Progresiva)

Esta es la interfaz móvil e interactiva para el control de fondos de inversión. Funciona como una **PWA (Progressive Web App)**, lo que permite instalarla en dispositivos Android o iOS como una aplicación nativa, abriéndose a pantalla completa y con un rendimiento optimizado para smartphones.

---

## 🔒 Arquitectura de Seguridad (Zero-Token)

Para proteger la privacidad y la seguridad de las credenciales, el sistema aplica un principio de **separación de entornos**:

1. **Búnker Privado (`control-cartera`):** Un repositorio privado donde reside el script de Python, la lista de activos (`posiciones.json`) y el histórico de transacciones. Un robot de **GitHub Actions** descarga los precios cada 2 horas de Yahoo Finance.
2. **Pasarela de Datos Segura:** Al finalizar, el robot privado realiza un filtrado de datos y "empuja" una copia limpia del CSV de precios a este repositorio público utilizando variables de entorno cifradas (`secrets`).
3. **Cliente Ligero (Este Repositorio):** Esta aplicación no contiene **ningún token ni contraseña de GitHub**. Es un entorno estático y seguro que cualquier usuario puede inspeccionar sin poner en riesgo el ecosistema privado.

---

## ⚡ Características Principales

* **Cálculo en Tiempo Real:** Permite introducir las participaciones de cada fondo mediante el teclado numérico del móvil y recalcula el valor de la posición y el total global al instante.
* **Persistencia Local (`localStorage`):** No utiliza cookies complejas ni bases de datos externas. Las participaciones introducidas se guardan de forma cifrada en la memoria local del navegador del smartphone. Aunque la app se cierre o el móvil se apague, los datos permanecen guardados.
* **Actualización en la Nube:** Los precios se refrescan automáticamente cada 2 horas gracias al backend automatizado en GitHub Actions.
* **Formato Localizado:** Adaptado al sistema decimal y de moneda de España (`es-ES`), sorteando los conflictos de formato anglosajón de Yahoo Finance.

---

## 🛠️ Tecnologías Utilizadas

* **Frontend:** HTML5, CSS3 (Diseño responsivo móvil *Mobile-First* con elementos flotantes fijos).
* **Lógica:** Vanilla JavaScript (ES6+) empleando la API asíncrona `fetch` con políticas de exclusión de caché (`no-store`) y desestructuración de cadenas de texto.
* **Persistencia:** Web Storage API (`localStorage`).
* **Despliegue:** GitHub Pages (Alojamiento estático gratuito y seguro con cifrado SSL).

---

## 📲 Cómo instalarla en tu Smartphone (Android / Chrome)

1. Accede a la URL de GitHub Pages generada por este repositorio desde el navegador **Google Chrome** de tu móvil.
2. Despliega el menú de opciones de Chrome (los tres puntos verticales arriba a la derecha).
3. Selecciona la opción **"Añadir a la pantalla de inicio"** o **"Instalar aplicación"**.
4. Aparecerá un acceso directo en el escritorio de tu teléfono. Al pulsar sobre él, la aplicación se iniciará de forma independiente a pantalla completa como una app nativa del sistema.
