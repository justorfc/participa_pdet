# Instrucciones de Configuración - Protección de Rama Main

Este documento proporciona un resumen rápido de los archivos creados y los pasos necesarios para activar completamente la protección de la rama `main`.

## ✅ Archivos Creados

Los siguientes archivos han sido agregados al repositorio para soportar la protección de rama:

### 1. `.github/CODEOWNERS`
**Propósito**: Define quién debe revisar cambios en diferentes partes del código.
- Requiere aprobación de @justorfc para todos los cambios
- Aplica especialmente a código de la app, documentación y archivos de configuración

### 2. `.github/workflows/ci.yml`
**Propósito**: Workflow de CI (Integración Continua) que se ejecuta automáticamente.
- Se ejecuta en push a `main` y en pull requests
- Prueba con Python 3.9, 3.10 y 3.11
- Verifica:
  - Instalación de dependencias
  - Linting con flake8
  - Importación del módulo principal
  - Estructura de directorios

### 3. `.github/BRANCH_PROTECTION.md`
**Propósito**: Documentación completa sobre cómo configurar la protección.
- Instrucciones paso a paso para GitHub UI
- Configuración recomendada detallada
- Flujo de trabajo con ramas protegidas
- Preguntas frecuentes

### 4. `.github/pull_request_template.md`
**Propósito**: Plantilla para nuevos pull requests.
- Guía a los contribuyentes sobre qué información incluir
- Checklist de revisión antes de enviar
- Mejora la calidad y consistencia de los PRs

### 5. `README.md` (actualizado)
**Propósito**: Añade información sobre contribución y protección de rama.
- Sección nueva: "Contribución y Protección de Rama"
- Flujo de trabajo básico con git
- Referencia a documentación detallada

## 🚀 Pasos para Activar la Protección (REQUERIDO)

Los archivos creados **no activan automáticamente** la protección de rama. El administrador del repositorio debe configurarla en GitHub:

### Opción 1: Configuración Manual en GitHub UI

1. Ve a: https://github.com/justorfc/participa_pdet/settings/branches
2. Haz clic en "Add rule" (Agregar regla)
3. En "Branch name pattern", escribe: `main`
4. Selecciona las siguientes opciones:

   ✅ **Require a pull request before merging**
   - ✅ Require approvals: 1
   - ✅ Dismiss stale pull request approvals when new commits are pushed
   - ✅ Require review from Code Owners

   ✅ **Require status checks to pass before merging**
   - ✅ Require branches to be up to date before merging
   - Selecciona: `test (3.9)`, `test (3.10)`, `test (3.11)`
     (estos aparecerán después del primer run del workflow)

   ✅ **Require conversation resolution before merging**

   ✅ **Do not allow bypassing the above settings**
   - ✅ Include administrators (recomendado para máxima seguridad)

   ❌ **Allow force pushes** - Deshabilitado
   ❌ **Allow deletions** - Deshabilitado

5. Haz clic en "Create" o "Save changes"

### Opción 2: Configuración con GitHub CLI

Si tienes `gh` CLI instalado y configurado:

```bash
# Requiere permisos de administrador
gh api repos/justorfc/participa_pdet/branches/main/protection \
  --method PUT \
  --field required_status_checks='{"strict":true,"contexts":["test (3.9)","test (3.10)","test (3.11)"]}' \
  --field enforce_admins=true \
  --field required_pull_request_reviews='{"dismiss_stale_reviews":true,"require_code_owner_reviews":true,"required_approving_review_count":1}' \
  --field restrictions=null
```

## 🧪 Verificar la Configuración

Después de configurar la protección:

1. **Verificar workflow CI**:
   - Ve a: https://github.com/justorfc/participa_pdet/actions
   - Deberías ver el workflow "CI" ejecutándose

2. **Probar protección**:
   - Intenta hacer push directo a `main` (debería fallar)
   - Crea un PR desde otra rama (debería requerir revisión y checks)

3. **Verificar reglas**:
   - Ve a: https://github.com/justorfc/participa_pdet/settings/branches
   - Deberías ver la regla para `main` activa

## 📋 Flujo de Trabajo Post-Configuración

Una vez activada la protección, el flujo de trabajo será:

1. **Desarrollador crea rama**:
   ```bash
   git checkout -b feature/mi-cambio
   ```

2. **Desarrollador hace cambios**:
   ```bash
   git add .
   git commit -m "Descripción del cambio"
   git push origin feature/mi-cambio
   ```

3. **Desarrollador crea Pull Request** en GitHub

4. **Sistema ejecuta checks automáticos**:
   - CI workflow se ejecuta
   - Todos los tests deben pasar (verde ✓)

5. **Revisor aprueba el PR**:
   - Revisa el código
   - Aprueba o solicita cambios
   - Todos los comentarios deben resolverse

6. **Merge al main**:
   - Solo posible si:
     - ✓ Checks de CI pasan
     - ✓ Revisión aprobada
     - ✓ Conversaciones resueltas
     - ✓ Rama actualizada con main

## ⚠️ Limitaciones Actuales

1. **Los checks de CI aparecerán después del primer run**: Después de mergear este PR, el workflow CI se ejecutará por primera vez. Después de eso, podrás seleccionarlo como required check.

2. **Configuración manual requerida**: La protección de rama no se puede activar completamente solo con archivos en el repositorio - requiere configuración en GitHub.

3. **Permisos de administrador**: Solo los administradores del repositorio pueden configurar branch protection rules.

## 📚 Recursos y Documentación

- **Documentación detallada**: `.github/BRANCH_PROTECTION.md`
- **Workflow CI**: `.github/workflows/ci.yml`
- **Code Owners**: `.github/CODEOWNERS`
- **Template PR**: `.github/pull_request_template.md`

## ✉️ Contacto

Para preguntas o problemas con la configuración:
- Abre un issue en el repositorio
- Consulta la documentación oficial de GitHub
- Revisa los logs del workflow si falla CI

## 🎉 ¡Listo!

Una vez completados estos pasos, tu rama `main` estará protegida y todos los cambios requerirán:
- Pull Request
- Revisión de código
- Checks de CI exitosos
- Resolución de comentarios

Esto mejora significativamente la calidad del código y reduce errores accidentales.
