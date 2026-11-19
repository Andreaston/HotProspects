#  HotProspects

App de iOS hecha con **SwiftUI** y **SwiftData** para llevar el control de las personas que conoces en eventos. Cada persona se añade escaneando su código QR, y después puedes marcarla como contactada, eliminarla o programar un recordatorio para contactarla.

## Qué hace

- **Tres listas con pestañas**
  - **Everyone (Todos):** todas las personas guardadas.
  - **Contacted (Agenda):** las que ya has contactado.
  - **Uncontacted (Desconocidos):** las que aún no has contactado.
- **Escaneo de códigos QR** para añadir personas nuevas. El QR contiene el nombre y el email separados por un salto de línea.
- **Tu propio código QR** (pestaña **Me**): escribes tu nombre y tu email y la app genera un QR que otros pueden escanear. Con una pulsación larga sobre el QR puedes compartirlo.
- **Acciones de deslizamiento** sobre cada persona:
  - Eliminar.
  - Marcar como contactada / no contactada.
  - Recordatorio (solo para personas contactadas), mediante una notificación local a las 9:00.
- **Selección múltiple** con el botón *Edit* y borrado de varias personas a la vez con *Delete Selected*.

## Tecnologías

- SwiftUI (`TabView`, `NavigationStack`, `List`, `swipeActions`, `toolbar`, `contextMenu`, `ShareLink`)
- SwiftData (`@Model`, `@Query`, `#Predicate`, `modelContext`)
- `@AppStorage` para guardar tu nombre y email
- Core Image (`CIFilter.qrCodeGenerator`) para generar el QR
- `UserNotifications` para los recordatorios
- [CodeScanner](https://github.com/twostraws/CodeScanner) para escanear códigos QR

## Estructura del proyecto

| Archivo | Descripción |
| --- | --- |
| `HotProspectsApp.swift` | Punto de entrada; configura `.modelContainer(for: Prospect.self)` |
| `ContentView.swift` | `TabView` con las tres listas y la pestaña **Me** |
| `ProspectView.swift` | Lista filtrable de personas, escaneo, acciones y notificaciones |
| `MeView.swift` | Formulario con tus datos y generación del código QR |
| `Prospect.swift` | Modelo de SwiftData: `name`, `emailAddress`, `isContacted` |

## Requisitos

- Xcode con soporte para SwiftData (iOS 17 o superior).
- Paquete **CodeScanner** añadido al proyecto y enlazado al target de la app.
- Un iPhone físico para probar el escáner: el simulador no tiene cámara (en

