1) Descripción
Prueba funcional automatizada E2E del flujo de compra en https://www.saucedemo.com/:

Login con standard_user / secret_sauce

Agregar 2 productos al carrito

Ver carrito

Completar formulario de compra

Finalizar hasta ver “THANK YOU FOR YOUR ORDER”

2) Tecnologías
Opción A (principal): Cypress.io (TypeScript/JavaScript)

Opción B (alternativa): Serenity BDD (Java + JUnit/Cucumber)

El repositorio incluye ambas opciones para facilidad de revisión. Puedes ejecutar solo la que prefieras.

3) Requisitos previos
Node.js 18+ y npm (para Cypress)

Java 11 o 17 y Maven 3.8+ (para Serenity)

Sistema operativo: Windows/macOS/Linux

Navegadores: Chrome/Chromium

4) Estructura del proyecto (Cypress)
bash
Copiar
/cypress
  /e2e
    purchase.e2e.cy.ts
  /fixtures
    user.json
  /pages
    LoginPage.ts
    InventoryPage.ts
    CartPage.ts
    CheckoutPage.ts
    CheckoutOverviewPage.ts
    CheckoutCompletePage.ts
  /support
    commands.ts
cypress.config.ts
package.json
README.txt
conclusiones.txt
5) Datos de prueba
Usuario: standard_user

Password: secret_sauce

URL base: https://www.saucedemo.com/

Checkout ejemplo:

First Name: QA

Last Name: Automation

Zip: 170505

6) Instalación (Cypress)
bash
Copiar
# 1) Instalar dependencias
npm ci

# 2) Ejecutar en modo UI (opcional)
npx cypress open

# 3) Ejecutar en headless y generar reportes (recomendado para entrega)
npm run test:headless
Scripts útiles (Cypress)
En package.json:

json
Copiar
{
  "scripts": {
    "test": "cypress run",
    "test:headless": "cypress run --browser chrome --headless",
    "report:mochawesome": "npx mochawesome-merge cypress/reports/*.json | npx marge --reportDir cypress/reports/html"
  }
}
Los reportes HTML quedarán en cypress/reports/html (si usas mochawesome).
Screenshots/videos (si hay fallos) en cypress/screenshots y cypress/videos.

7) Ejecución del caso E2E (Cypress)
El caso principal está en cypress/e2e/purchase.e2e.cy.ts.

Flujo automatizado:

Navega a la URL base.

Login (standard_user / secret_sauce).

Agrega dos productos (por ejemplo “Sauce Labs Backpack” y “Sauce Labs Bike Light”).

Abre el carrito y valida que existan 2 ítems.

Checkout → completa el formulario (First/Last/Zip).

Finaliza compra.

Valida el mensaje “THANK YOU FOR YOUR ORDER”.

Ejecuta:

bash
Copiar
npm run test:headless
# opcional para un html consolidado si usas mochawesome
npm run report:mochawesome
8) Evidencias de ejecución
Logs: consola del runner

Screenshots/Videos: auto-generados por Cypress en fallos (headless)

Reportes HTML: cypress/reports/html/index.html (si se configuró mochawesome)

9) Empaquetado para envío
Incluye en el .zip:

Código fuente completo (incluyendo package.json, cypress.config.ts)

Carpeta de reportes (cypress/reports/html)

Carpeta de evidencias si aplica (cypress/screenshots, cypress/videos)

Este README.txt

conclusiones.txt

Ejemplo:

lua
Copiar
saucedemo-e2e/
  cypress/
  cypress.config.ts
  package.json
  README.txt
  conclusiones.txt
Comprimir la carpeta saucedemo-e2e en saucedemo-e2e.zip.

10) Alternativa: Serenity BDD (opcional)
Estructura (Serenity + JUnit/Cucumber)
bash
Copiar
src
 └─ test
    ├─ java
    │   ├─ runners/PurchaseRunner.java
    │   ├─ steps/PurchaseSteps.java
    │   └─ ui/ (PageObjects)
    └─ resources
        └─ features/purchase/purchase.feature
pom.xml
