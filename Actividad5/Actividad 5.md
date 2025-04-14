# Informe: Explorando diferentes formas de fusionar en Git

## Objetivo de aprendizaje

Explorar el proceso de fusionar ramas en Git mediante tres estrategias: **fast-forward**, **no-fast-forward** y **squash**.

---

## 1. Fusión Fast-forward (`git merge --ff`)

### Comandos ejecutados:

```bash
mkdir prueba-fast-forward-merge
cd prueba-fast-forward-merge
git init
echo "# Mi Proyecto" > README.md
git add README.md
git commit -m "Commit inicial en main"
git checkout -b add-description
echo "Este proyecto es un ejemplo de cómo usar Git." >> README.md
git add README.md
git commit -m "Agregar descripción al README.md"
git checkout main
git merge add-description
git log --graph --oneline
```

### Imagen de resultado:

> <img src="imgs/Screenshot 2025-04-14 003727.png"width="600">

## 2. Fusión No-fast-forward (`git merge --no-ff`)

### Comandos ejecutados:

```bash
mkdir prueba-no-fast-forward-merge
cd prueba-no-fast-forward-merge
git init
echo "# Mi Proyecto" > README.md
git add README.md
git commit -m "Commit inicial en main"
git checkout -b add-feature
echo "Implementando una nueva característica..." >> README.md
git add README.md
git commit -m "Implementar nueva característica"
git checkout main
git merge --no-ff add-feature
git log --graph --oneline
```

### Imagen de resultado:

![[Screenshot 2025-04-14 011537.png]]

---

## 3. Fusión Squash (`git merge --squash`)

### Comandos ejecutados:

```bash
mkdir prueba-squash-merge
cd prueba-squash-merge
git init
echo "# Mi Proyecto" > README.md
git add README.md
git commit -m "Commit inicial en main"
git checkout -b add-basic-files
echo "# CÓMO CONTRIBUIR" >> CONTRIBUTING.md
git add CONTRIBUTING.md
git commit -m "Agregar CONTRIBUTING.md"
echo "# LICENCIA" >> LICENSE.txt
git add LICENSE.txt
git commit -m "Agregar LICENSE.txt"
git checkout main
git merge --squash add-basic-files
git add .
git commit -m "Agregar documentación estándar del repositorio"
git log --graph --oneline
```

### Imagen de resultado:

![[Pasted image 20250414013241.png]]

---

## 4. Resolver conflictos en una fusión no-fast-forward

### Comandos ejecutados:

```bash
mkdir prueba-merge-conflict
cd prueba-merge-conflict
git init
echo "<html><body><h1>Proyecto inicial CC3S2</h1></body></html>" > index.html
git add index.html
git commit -m "commit inicial del index.html en main"
git checkout -b feature-update
echo "<p>.....</p>" >> index.html
git add index.html
git commit -m "Actualiza ..."
git checkout main
echo "<footer>Contacta aquí example@example.com</footer>" >> index.html
git add index.html
git commit -m "....index.html"
git merge --no-ff feature-update
```
Se puede ver como al realizar el merge la terminal nos muestra el conflicto que hay
![[Screenshot 2025-04-14 020623.png]]
### Resolución manual:

Abrimos `index.html`  con un editor de texto, editamos y eliminamos los marcadores de conflicto y se deja la versión combinada.

### Finalización:

```bash
git add index.html
git commit
git log --graph --oneline
```

### Imagen de resultado:

![[Pasted image 20250414021635.png]]

---

## 5. Comparación de historiales tras diferentes fusiones

### Comandos ejecutados:

```bash
mkdir prueba-compare-merge
cd prueba-compare-merge
git init
echo "Version 1.0" > version.txt
git add version.txt
git commit -m "...."
git checkout -b feature-1
echo "Caracteristica 1 agregada" >> version.txt
git add version.txt
git commit -m "Agregar caracteristica 1"
git checkout main
git checkout -b feature-2
echo "Caracteristica 2 agregada" >> version.txt
git add version.txt
git commit -m "Se agrega caracteristica 2"
git checkout main
git merge feature-1 --ff
git merge feature-2 --no-ff
git checkout -b feature-3
echo "Caracteristica 3 paso 1" >> version.txt
git add version.txt
git commit -m "Caracteristica 3 paso 1"
echo "Caracteristica 3 paso 2" >> version.txt
git add version.txt
git commit -m "Caracteristica 3 paso 2"
git checkout main
git merge --squash feature-3
git commit -m "Agregar caracteristica 3 en un commit"
```

### Imagen de resultado:
`Merge ff`
![[Screenshot 2025-04-14 023910.png]]
Intento de `Merge no ff`, se puede ver el conflicto de querer realizar este comando
![[Screenshot 2025-04-14 024449.png]]
Se procede a solucionarlo de forma manual
![[Screenshot 2025-04-14 024532.png]]
`Merge squash` para la rama `feature-3`
![[Screenshot 2025-04-14 025307.png]]
Se puede ver como toda la rama `feature-3` se comprimió a un solo `commit`
![[Screenshot 2025-04-14 030018.png]]
## 6. Fusiones automáticas y revertir fusiones

### Comandos ejecutados:

```bash
mkdir prueba-auto-merge
cd prueba-auto-merge
git init
echo "Linea 1" > file.txt
git add file.txt
git commit -m "Agrega linea 1"
echo "Linea 2" >> file.txt
git add file.txt
git commit -m "...linea 2"
git checkout -b auto-merge
echo "Linea 3" >> file.txt
git add file.txt
git commit -m "..."
```


### Imagen de resultado:

![[Screenshot 2025-04-14 004702.png]]

---
## 7. Fusión remota en un repositorio colaborativo

### Comandos ejecutados:
1. Clona un repositorio remoto desde GitHub o crea uno nuevo:
   ```bash
   git clone https://github.com/tu-usuario/nombre-del-repositorio.git
   cd nombre-del-repositorio
   ```

2. Crea una nueva rama colaboracion y haz algunos cambios:
   ```bash
   git checkout -b colaboracion
   echo "Colaboración remota" > colaboracion.txt
   git add colaboracion.txt
   git commit -m "...."
   ```

3. Empuja los cambios a la rama remota:
   ```bash
   git push origin colaboracion
   ```

### Imagen de resultado:
![[Screenshot 2025-04-14 003827.png]]
**Preguntas:**
- ¿Cómo cambia la estrategia de fusión cuando colaboras con otras personas en un repositorio remoto?
-Se trabaja con PRs, y los merges se hacen con políticas definidas como no-ff, squash, etc.
- ¿Qué problemas comunes pueden surgir al integrar ramas remotas?
-Conflictos de fusión si ambos tocan las mismas líneas. Push rechazado si el remoto está más avanzado. Hacer `rebase` en ramas públicas puede sobrescribir trabajo ajeno.
