RedBarrio 🏘️
RedBarrio es una aplicación móvil híbrida diseñada para la gestión integral de comunidades y juntas de vecinos. Facilita la comunicación, la organización de eventos, la gestión de espacios comunes y la participación ciudadana a través de una plataforma centralizada.

Este proyecto está construido con Ionic (Angular) para el frontend, Capacitor para la compilación nativa, y utiliza Supabase como backend (Base de Datos, Autenticación y Edge Functions).

✨ Características Principales
La aplicación redbarrio incluye las siguientes funcionalidades clave:

Autenticación de Usuarios: Sistema completo de registro, inicio de sesión y recuperación de contraseña.

Gestión de Perfil: Los usuarios pueden ver y actualizar su información personal.

Muro de Noticias: Un espacio para que la administración publique anuncios y noticias relevantes para la comunidad.

Sistema de Votaciones: Permite crear votaciones sobre temas de interés y que los vecinos participen de forma digital.

Reserva de Espacios Comunes: Un módulo para ver la disponibilidad y solicitar la reserva de espacios (como salones de eventos, quinchos, etc.).

Solicitud de Certificados: Formulario para solicitar certificados (ej. de residencia) a la administración.

Inscripción a Proyectos: Los vecinos pueden inscribirse en diferentes proyectos o iniciativas de la comunidad.

Integración de Pagos (Transbank): Pasarela de pago integrada para gestionar cobros (como gastos comunes o reservas) utilizando Supabase Edge Functions para la comunicación con Transbank.

🛠️ Stack Tecnológico
Frontend: Ionic 7+ con Angular 16+

Backend (BaaS): Supabase

Base de Datos: PostgreSQL

Autenticación: Supabase Auth

Serverless: Supabase Edge Functions (Deno)

Plataforma Móvil: Capacitor (para builds nativos en Android e iOS)

Pasarela de Pagos: Transbank (integrado vía Edge Functions)

🚀 Puesta en Marcha (Frontend)
Para ejecutar el proyecto en un entorno de desarrollo, sigue estos pasos:

Clonar el repositorio (si aún no lo has hecho):

Bash

git clone https://github.com/tu-usuario/capstone-rn-jf-sd-parte2.git
Navegar a la carpeta del proyecto:

Bash

cd capstone-rn-jf-sd-parte2/redbarrio
Instalar dependencias de Node.js:

Bash

npm install
Configurar variables de entorno: Copia tus claves de API de Supabase (URL y anon_key) en el archivo src/environments/environment.ts. Las encontrarás en la configuración de tu proyecto Supabase.

TypeScript

// src/environments/environment.ts
export const environment = {
  production: false,
  supabaseUrl: 'TU_SUPABASE_URL',
  supabaseKey: 'TU_SUPABASE_ANON_KEY'
};
Nota: Haz lo mismo para src/environments/environment.prod.ts con las claves de producción si es necesario.

Ejecutar el servidor de desarrollo:

Bash

ionic serve
Esto abrirá la aplicación en tu navegador en http://localhost:8100.

🔧 Configuración del Backend (Supabase)
El backend, incluyendo las funciones de pago, se gestiona con la Supabase CLI.

Iniciar sesión en la CLI de Supabase (si es la primera vez):

Bash

supabase login
Vincular tu proyecto Supabase: Navega a la carpeta supabase y vincula tu proyecto remoto (obten el [PROJECT_ID] desde la URL de tu dashboard de Supabase).

Bash

cd ../supabase
supabase link --project-ref [PROJECT_ID]
Desplegar las Edge Functions: Este proyecto usa Edge Functions para simular y confirmar pagos con Transbank. Para desplegarlas:

Bash

supabase functions deploy transbank-simular
supabase functions deploy transbank-confirm
Asegúrate de configurar las variables de entorno necesarias (como las API keys de Transbank) en el dashboard de tu proyecto Supabase.

📜 Scripts Útiles (Frontend)
Desde la carpeta redbarrio/:

ionic serve: Inicia el servidor de desarrollo web.

npm run build: Compila la aplicación web para producción. El resultado se guarda en la carpeta www/.

ionic cap sync: Sincroniza los cambios del build web (www/) con los proyectos nativos (Android/iOS).

ionic cap run android: Ejecuta la aplicación en un dispositivo o emulador Android (requiere Android Studio).

ionic cap run ios: Ejecuta la aplicación en un dispositivo o emulador iOS (requiere Xcode y un Mac).
