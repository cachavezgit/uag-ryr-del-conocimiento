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

---

### ejercicio3-diagramas

Ejercicio de resolución de ontologías a partir de diagramas TBox/ABox dados. Se desarrollaron tres ontologías independientes.

#### diagrama1 — Ontología de Personas

Ontología basada en un diagrama de clases con jerarquía de mamíferos y personas, con individuos Mary y John.

**Namespace:** `http://www.uag.mx/ontologias/personas#`

**Clases:**

| Clase | Descripción |
|-------|-------------|
| `Mamiferos` | Clase raíz de la jerarquía |
| `Personas` | Subclase de Mamíferos; restricción: `TienePiernas = 2` |
| `PersonasFemeninas` | Subclase de Personas |
| `PersonasMasculinas` | Subclase de Personas |

**Propiedades:**

| Propiedad | Tipo | Descripción |
|-----------|------|-------------|
| `TieneMadre` | ObjectProperty (funcional) | Dominio: Personas → rango: PersonasFemeninas |
| `HermanaDe` | ObjectProperty | Dominio: PersonasFemeninas → rango: Personas |
| `TieneHermana` | ObjectProperty | Inversa de `HermanaDe` |
| `TienePiernas` | DatatypeProperty (xsd:integer) | Número de piernas de una persona |

**Instancias:** Mary (PersonasFemeninas, `HermanaDe` John), John (PersonasMasculinas, `TieneHermana` Mary). Ambos con `TienePiernas = 2`.

**Archivos:**

| Archivo | Descripción |
|---------|-------------|
| [ontologia_personas.owl](U4A2-ontologias/ejercicio3-diagramas/diagrama1/ontologia_personas.owl) | Ontología en formato RDF/XML |
| [ontologia_personas.ttl](U4A2-ontologias/ejercicio3-diagramas/diagrama1/ontologia_personas.ttl) | Ontología en formato Turtle |
| [ontologia1.png](U4A2-ontologias/ejercicio3-diagramas/diagrama1/ontologia1.png) | Diagrama de la ontología (PNG) |
| [ontologia1.svg](U4A2-ontologias/ejercicio3-diagramas/diagrama1/ontologia1.svg) | Diagrama de la ontología (SVG) |

#### diagrama2 — Ontología de Fred

Ontología basada en una red semántica con jerarquía de animales, relaciones de alimentación y mascota, con individuos Fred, Tibbs y cat_liker.

**Namespace:** `http://www.uag.mx/ontologias/fred#`

**Clases:**

| Clase | Descripción |
|-------|-------------|
| `animal` | Clase raíz de la jerarquía |
| `cat` | Subclase de animal |
| `person` | Subclase de animal |
| `vegetarian` | Subclase de animal; restricción: `eats` solo valores que no sean `animal` (`allValuesFrom complementOf animal`) |
| `cow` | Subclase de vegetarian |
| `sheep` | Subclase de animal; restricción: `eats` solo `grass` (`allValuesFrom {grass}`) |
| `man` | Subclase de person, adult y male |
| `adult` | Clase auxiliar |
| `male` | Clase auxiliar |

**Propiedades:**

| Propiedad | Tipo | Descripción |
|-----------|------|-------------|
| `has_pet` | ObjectProperty | Dominio: person → rango: animal |
| `likes` | ObjectProperty | Relación de agrado entre individuos o clases |
| `eats` | ObjectProperty | Dominio: animal; lo que un animal come |

**Instancias:** grass (individuo genérico), Tibbs (cat), cat_liker (person y vegetarian, `likes` cat), Fred (man y cow, `has_pet` Tibbs).

**Archivos:**

| Archivo | Descripción |
|---------|-------------|
| [ontologia_fred.owl](U4A2-ontologias/ejercicio3-diagramas/diagrama2/ontologia_fred.owl) | Ontología en formato RDF/XML |
| [ontologia_fred.ttl](U4A2-ontologias/ejercicio3-diagramas/diagrama2/ontologia_fred.ttl) | Ontología en formato Turtle |
| [ontologia2.png](U4A2-ontologias/ejercicio3-diagramas/diagrama2/ontologia2.png) | Diagrama de la ontología (PNG) |
| [ontologia2.svg](U4A2-ontologias/ejercicio3-diagramas/diagrama2/ontologia2.svg) | Diagrama de la ontología (SVG) |

#### diagrama3 — Ontología de Animales y Mascotas

Ontología con jerarquía Animal–Mammal–Dog y relaciones de propiedad entre humanos y mascotas, con individuos Robbie, Zeus y MrBurns.

**Namespace:** `http://www.uag.mx/ontologias/animals#`

**Clases (TBox):**

| Clase | Descripción |
|-------|-------------|
| `Animal` | Clase raíz; restricción: `eyes = 2` |
| `Mammal` | Subclase de Animal; restricción: `legs = 4` |
| `Dog` | Subclase de Mammal |
| `Human` | Clase independiente para humanos |

**Propiedades (TBox):**

| Propiedad | Tipo | Descripción |
|-----------|------|-------------|
| `owns` | ObjectProperty | Dominio: Human |
| `hasPet` | ObjectProperty | Subpropiedad de `owns`; rango: Mammal |
| `petOf` | ObjectProperty | Inversa de `hasPet` |
| `eyes` | DatatypeProperty (xsd:integer) | Número de ojos de un animal |
| `legs` | DatatypeProperty (xsd:integer) | Número de patas de un animal |

**Instancias (ABox):** Robbie (Dog, `petOf` Zeus), Zeus (Human, `owns` Robbie, `sameAs` MrBurns), MrBurns (Human, `sameAs` Zeus).

**Archivos:**

| Archivo | Descripción |
|---------|-------------|
| [ontologia_animals.owl](U4A2-ontologias/ejercicio3-diagramas/diagrama3/ontologia_animals.owl) | Ontología en formato RDF/XML |
| [ontologia_animals.ttl](U4A2-ontologias/ejercicio3-diagramas/diagrama3/ontologia_animals.ttl) | Ontología en formato Turtle |
| [ontologia3.png](U4A2-ontologias/ejercicio3-diagramas/diagrama3/ontologia3.png) | Diagrama de la ontología (PNG) |
| [ontologia3.svg](U4A2-ontologias/ejercicio3-diagramas/diagrama3/ontologia3.svg) | Diagrama de la ontología (SVG) |
