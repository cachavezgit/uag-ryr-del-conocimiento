# Razonamiento y Representación del Conocimiento — UAG

Repositorio de ejercicios del curso **Razonamiento y Representación del Conocimiento**, Maestría en Inteligencia Artificial, Universidad Autónoma de Guadalajara.

---

## U4A2-ontologias

Actividad 2 de la Unidad 4: Ontologías y Web Semántica. Contiene dos ontologías OWL desarrolladas con vocabulario RDF/RDFS/OWL y serializadas en formato Turtle (`.ttl`) y RDF/XML (`.owl`).

### ejercicio1-geografia

Ontología que modela la estructura geográfica de México.

**Namespace:** `http://www.uag.mx/ontologias/geografia_mexico#`

**Clases principales:**

| Clase | Descripción |
|-------|-------------|
| `EntidadGeografica` | Clase abstracta raíz para entidades con ubicación geográfica |
| `Pais` | Territorio soberano con fronteras definidas |
| `Estado` | Entidad federativa perteneciente a un país |
| `Ciudad` | Asentamiento urbano |
| `CapitalEstatal` | Ciudad sede del gobierno de un estado |
| `CapitalNacional` | Ciudad sede del gobierno federal |
| `Frontera` | Límite geográfico entre territorios |
| `FronteraInternacional` | Límite entre países (conecta exactamente 2 países) |
| `FronteraEstatal` | Límite entre entidades federativas |
| `RegionGeografica` | Agrupación de estados con características comunes |
| `Municipio` | División administrativa dentro de un estado |
| `CuerpoDeAgua` | Océano, mar, golfo o lago |

**Propiedades de objeto notables:** `perteneceA` / `contiene` (inversas), `esCapitalDe` / `tieneCapital` (funcionales inversas), `limitaCon` / `tieneFronteraCon` (simétricas), `perteneceARegion`, `tieneAccesoAMar`, `conecta`.

**Instancias incluidas:**
- Países: México, Estados Unidos, Guatemala, Belice
- Regiones: Noroeste, Noreste, Occidente, Centro, Sureste
- Cuerpos de agua: Océano Pacífico, Golfo de México, Mar Caribe, Golfo de California
- Estados (con capitales): Sonora, Chihuahua, Nuevo León, Jalisco, Ciudad de México, Quintana Roo, y 14 estados adicionales referenciados
- Fronteras internacionales: México–EUA (3 145 km), México–Guatemala (958 km), México–Belice (276 km)
- Ciudades adicionales: Ciudad Juárez, Cancún, Tijuana

**Archivos:**

| Archivo | Descripción |
|---------|-------------|
| [geografia_mexico.ttl](U4A2-ontologias/ejercicio1-geografia/geografia_mexico.ttl) | Ontología en formato Turtle |
| [geografia_mexico.owl](U4A2-ontologias/ejercicio1-geografia/geografia_mexico.owl) | Ontología en formato RDF/XML |
| [organigrama_clases.png](U4A2-ontologias/ejercicio1-geografia/organigrama_clases.png) | Diagrama de jerarquía de clases (PNG) |
| [organigrama_clases.svg](U4A2-ontologias/ejercicio1-geografia/organigrama_clases.svg) | Diagrama de jerarquía de clases (SVG) |

---

### ejercicio2-biblioteca

Ontología que modela el sistema de gestión de una biblioteca universitaria.

**Namespace:** `http://www.uag.mx/ontologias/biblioteca#`

**Clases principales:**

| Clase | Descripción |
|-------|-------------|
| `RecursoBibliografico` | Clase abstracta raíz para todo material de la biblioteca |
| `Libro` | Obra identificada por ISBN (requiere ≥1 autor y exactamente 1 editorial) |
| `Revista` | Publicación periódica identificada por ISSN |
| `Tesis` | Trabajo de grado universitario |
| `Persona` | Clase abstracta para personas relacionadas con la biblioteca |
| `Autor` | Persona que escribe o contribuye a un recurso |
| `Editor` | Persona responsable de la edición |
| `Usuario` | Persona registrada que puede realizar préstamos |
| `Estudiante` | Usuario con matrícula (máx. 3 préstamos simultáneos) |
| `Profesor` | Usuario docente (máx. 5 préstamos simultáneos) |
| `Editorial` | Organización publicadora |
| `CopiaFisica` | Ejemplar concreto con código de barras y ubicación en estantería |
| `Prestamo` | Evento de préstamo de una copia a un usuario |
| `Categoria` | Clasificación temática (soporta subcategorías transitivas) |
| `Biblioteca` | Sede que alberga la colección |

**Restricciones de cardinalidad destacadas:** un `Libro` debe tener exactamente 1 ISBN y 1 editorial; un `Prestamo` involucra exactamente 1 copia y 1 usuario; cada `CopiaFisica` pertenece a exactamente 1 recurso y 1 biblioteca.

**Instancias incluidas:**
- Categorías: Ciencia, Computación, Inteligencia Artificial (subcategoría de Computación), Literatura, Historia, Matemáticas
- Editoriales: Pearson, Springer, O'Reilly, Fondo de Cultura Económica
- Autores: Stuart Russell, Peter Norvig, Thomas Cormen, Gabriel García Márquez, Octavio Paz
- Libros: *Artificial Intelligence: A Modern Approach*, *Introduction to Algorithms*, *Cien años de soledad*, *El laberinto de la soledad*
- Biblioteca: Biblioteca Central UAG (Zapopan, Jalisco)
- Copias físicas: 5 ejemplares con estados disponible/prestado
- Usuarios: 2 estudiantes, 1 profesora
- Préstamos activos: 2 (con fechas de préstamo y límite)

**Archivos:**

| Archivo | Descripción |
|---------|-------------|
| [biblioteca.ttl](U4A2-ontologias/ejercicio2-biblioteca/biblioteca.ttl) | Ontología en formato Turtle |
| [biblioteca.owl](U4A2-ontologias/ejercicio2-biblioteca/biblioteca.owl) | Ontología en formato RDF/XML |
| [ontologia_biblioteca.png](U4A2-ontologias/ejercicio2-biblioteca/ontologia_biblioteca.png) | Diagrama de la ontología (PNG) |
| [ontologia_biblioteca.svg](U4A2-ontologias/ejercicio2-biblioteca/ontologia_biblioteca.svg) | Diagrama de la ontología (SVG) |
