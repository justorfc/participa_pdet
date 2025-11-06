# Configuración de Protección de Rama (Branch Protection)

Este documento describe cómo configurar la protección de la rama `main` en GitHub.

## ¿Por qué proteger la rama main?

Proteger la rama `main` ayuda a:
- Prevenir cambios accidentales o no revisados
- Asegurar que todo el código pase por revisión (code review)
- Garantizar que las pruebas automatizadas se ejecuten antes de fusionar
- Mantener un historial limpio y estable del código

## Configuración Recomendada en GitHub

Para configurar la protección de la rama `main`, sigue estos pasos:

### 1. Acceder a la Configuración del Repositorio

1. Ve a tu repositorio en GitHub: https://github.com/justorfc/participa_pdet
2. Haz clic en **Settings** (Configuración)
3. En el menú lateral, haz clic en **Branches** (Ramas)
4. En la sección "Branch protection rules", haz clic en **Add rule** (Agregar regla)

### 2. Configurar la Regla de Protección

Configura los siguientes ajustes para la rama `main`:

#### Nombre de la rama
- **Branch name pattern**: `main`

#### Configuración recomendada:

✅ **Require a pull request before merging**
- Require approvals: 1
- Dismiss stale pull request approvals when new commits are pushed
- Require review from Code Owners (basado en el archivo CODEOWNERS)

✅ **Require status checks to pass before merging**
- Require branches to be up to date before merging
- Status checks to require:
  - `test (3.9)` - Pruebas con Python 3.9
  - `test (3.10)` - Pruebas con Python 3.10
  - `test (3.11)` - Pruebas con Python 3.11

✅ **Require conversation resolution before merging**
- Asegura que todos los comentarios de revisión se resuelvan

✅ **Require linear history** (opcional)
- Previene merge commits, requiere rebase o squash

✅ **Do not allow bypassing the above settings**
- Incluye a los administradores (opcional, pero recomendado para proyectos importantes)

❌ **Allow force pushes** - Debe estar deshabilitado
❌ **Allow deletions** - Debe estar deshabilitado

### 3. Guardar la Configuración

Haz clic en **Create** o **Save changes** para aplicar la regla.

## Archivos de Soporte Incluidos

Este repositorio incluye los siguientes archivos para soportar la protección de rama:

### `.github/CODEOWNERS`
Define quién debe revisar cambios en diferentes partes del código.

### `.github/workflows/ci.yml`
Workflow de GitHub Actions que ejecuta:
- Instalación de dependencias
- Linting básico con flake8
- Verificación de importación del módulo principal
- Validación de estructura de directorios

## Flujo de Trabajo con Rama Protegida

1. **Crear una rama nueva** para tu trabajo:
   ```bash
   git checkout -b feature/nueva-funcionalidad
   ```

2. **Hacer cambios y commits** en tu rama:
   ```bash
   git add .
   git commit -m "Descripción del cambio"
   ```

3. **Subir tu rama** al repositorio:
   ```bash
   git push origin feature/nueva-funcionalidad
   ```

4. **Crear un Pull Request** en GitHub:
   - Ve a tu repositorio en GitHub
   - Haz clic en "Compare & pull request"
   - Describe tus cambios
   - Asigna revisores si es necesario

5. **Esperar la revisión y las pruebas**:
   - Los checks de CI deben pasar (verde ✓)
   - Un revisor debe aprobar los cambios
   - Resolver cualquier comentario de revisión

6. **Fusionar el Pull Request**:
   - Una vez aprobado y con checks pasando, haz clic en "Merge pull request"

## Comandos Git Útiles

```bash
# Ver el estado actual
git status

# Ver ramas locales y remotas
git branch -a

# Actualizar tu rama con los últimos cambios de main
git checkout main
git pull origin main
git checkout tu-rama
git rebase main

# O usando merge
git checkout tu-rama
git merge main
```

## Preguntas Frecuentes

### ¿Puedo hacer commits directamente a main?
No, con la protección activada, todos los cambios deben pasar por un Pull Request.

### ¿Qué pasa si falla un check de CI?
No podrás fusionar el PR hasta que todos los checks pasen. Revisa los logs del workflow para ver qué falló.

### ¿Puedo hacer cambios urgentes sin revisión?
Los administradores pueden tener permisos para hacer bypass, pero no es recomendado excepto en emergencias.

### ¿Cómo agrego más revisores?
Modifica el archivo `.github/CODEOWNERS` para agregar más usuarios o equipos como propietarios del código.

## Recursos Adicionales

- [Documentación oficial de GitHub sobre Branch Protection](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)
- [Guía de CODEOWNERS](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
