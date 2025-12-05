#  Sistema Escolar WebApp - Frontend

Una aplicación web moderna y completa para la gestión integral de instituciones educativas.  Desarrollada con **Angular** y diseñada para facilitar la administración de estudiantes, profesores, materias, eventos académicos y visualización de datos.

---

##  Características Principales

-  **Registro de Usuarios**: Registro seguro de Administradores, Profesores y Estudiantes
-  **Sistema de Login**: Autenticación con JWT tokens
-  **Panel Personalizado por Rol**: Dashboards específicos para Administradores, Profesores y Estudiantes
-  **Gestión de Eventos Académicos**: 
  - Crear nuevos eventos académicos
  - Editar eventos existentes
  - Eliminar eventos
-  **Visualización de Eventos**: 
  - Vista general de todos los eventos académicos
  - Filtros por tipo, fecha y estado
-  **Gráficas y Reportes**: 
  - Dashboards con visualización de datos
  - Gráficas estadísticas de estudiantes
  - Reportes de desempeño académico
-  **Interfaz Responsiva**: Diseño adaptable para todos los dispositivos
-  **Validaciones en Tiempo Real**: Formularios con validación completa

---

##  Vistas por Rol de Usuario

### ** Administrador**
- Dashboard con estadísticas generales
- Gestión completa de eventos académicos
- Visualización de gráficas de desempeño
- Vista de todos los usuarios del sistema

### ** Profesor**
- Dashboard personalizado con información relevante
- Ver eventos académicos asignados

### ** Estudiante**
- Dashboard con información académica personal
- Consultar eventos académicos disponibles


---

##  Tecnologías Utilizadas

- **Angular 18+** - Framework frontend
- **TypeScript** - Lenguaje de programación
- **Bootstrap 5** - Framework CSS
- **Angular Material** - Componentes UI
- **Chart.js / ng2-charts** - Librerías de gráficas
- **SCSS** - Preprocesador CSS
- **Vercel** - Plataforma de deployment

---

##  Requisitos Previos

- **Node.js** 18+ instalado
- **npm** o **yarn** como gestor de paquetes
- **Angular CLI** instalado globalmente:
  ```bash
  npm install -g @angular/cli
  ```

---

##  Instalación y Ejecución

### **1. Clonar el repositorio**
```bash
git clone https://github.com/abibad/sistema_escolar_webapp.git
cd sistema_escolar_webapp
```

### **2. Instalar dependencias**
```bash
npm install
```

### **3. Configurar ambiente**

Edita el archivo `src/environments/environment.ts` para desarrollo:
```typescript
export const environment = {
  production: false,
  url_api: "http://127.0.0.1:8000"
};
```

Y `src/environments/environment.prod.ts` para producción:
```typescript
export const environment = {
  production: true,
  url_api: "https://abibad.pythonanywhere.com"
};
```

### **4.  Ejecutar en desarrollo**
```bash
ng serve
```

Accede a la aplicación en `http://localhost:4200`

### **5. Construir para producción**
```bash
ng build --configuration production
```

---

##  Flujo de Autenticación

1. **Registro**: El usuario se registra en la aplicación seleccionando su rol
2. **Login**: Ingresa con email y contraseña
3. **Token JWT**: El servidor retorna un token que se almacena en `localStorage`
4. **Protección de Rutas**: Guards verifican el token y rol del usuario
5. **Dashboard Personalizado**: Se muestra la vista correspondiente al rol

---

##  Flujo Principal de la Aplicación

```
Login/Registro
     ↓
Autenticación (JWT)
     ↓
Dashboard Personalizado
     ├── Admin → Gestión Completa
     ├── Profesor →  Eventos y Gráficas
     └── Estudiante → Consulta de Información y gráficas 
     ↓
Gestión de Eventos Académicos
     ├── Crear Evento
     ├── Ver Eventos
     ├── Editar Evento
     └── Eliminar Evento
     ↓
Visualización de Gráficas 
```

---

##  Secciones Principales

### **1.  Autenticación**
- Registro de nuevos usuarios
- Login seguro con validaciones
- Manejo de sesiones

### **2. Eventos Académicos**
- **Crear**: Formulario para registrar nuevos eventos
- **Listar**: Vista de todos los eventos con filtros
- **Editar**: Modificar datos de eventos existentes
- **Eliminar**: Eliminar eventos del sistema

### **3. Gráficas y Reportes**
- Estadísticas de estudiantes por nivel
- Gráficas de desempeño académico
- Reportes por período académico
- Análisis de eventos registrados

---

##  URLs de la Aplicación

| Entorno | URL |
|---------|-----|
| Desarrollo Local | http://localhost:4200 |
| Producción | https://sistema-escolar-webapp.vercel.app |

---

##  Rutas Principales

```
/                    → Página de inicio / Redirect a login
/registro            → Formulario de registro
/login               → Página de login
/admin-view    → Dashboard administrador
/maestro-view  → Dashboard profesor
/alumno-view  → Dashboard estudiante
/eventos-academicos  → Gestión de eventos (crear/editar)
/eventos-view        → Visualización de eventos
/graficas            → Gráficas y reportes
```

---

##  Consumo de API

Los servicios en `src/app/services/` se encargan de comunicarse con el backend:

```typescript
// Ejemplo: EventosService
export class EventosService {
  private apiUrl = environment.url_api;

  crear(evento: any) {
    return this.http. post(`${this.apiUrl}/eventos/`, evento);
  }

  obtener() {
    return this.http. get(`${this.apiUrl}/eventos/`);
  }

  actualizar(id: number, evento: any) {
    return this.http.put(`${this.apiUrl}/eventos/${id}/`, evento);
  }

  eliminar(id: number) {
    return this.http.delete(`${this.apiUrl}/eventos/${id}/`);
  }
}
```

---

##  Troubleshooting

### **Error: "Cannot find module"**
```bash
rm -rf node_modules package-lock.json
npm install
```

### **Error CORS**
Asegúrate de que el backend está configurado con CORS habilitado y que tienes la URL correcta en `environment.ts`

### **Puerto 4200 en uso**
```bash
ng serve --port 4201
```

### **Gráficas no aparecen**
Verifica que la librería de gráficas está instalada:
```bash
npm install chart.js ng2-charts
```

---

##  Deployment en Vercel

1.  Conecta tu repositorio GitHub a Vercel
2. En la configuración de build:
   - **Build Command**: `npm run build`
   - **Output Directory**: `dist/dev-sistema-escolar-webapp`
3. Agrega variables de entorno si es necesario
4. Haz deploy automático con cada push a `main`

---

##  Autor

**Abibad** - Desarrollo Full Stack

---

##  Licencia

Este proyecto está bajo la licencia MIT.

---

##  Soporte

Para reportar errores o sugerencias, abre un issue en el repositorio de GitHub. 
