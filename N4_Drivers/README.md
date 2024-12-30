|               |                                 |                                        |
| ------------- | ------------------------------- | -------------------------------------- |
| **Modul 165** | **NoSQL-Datenbanken einsetzen** | ![IPSO Logo](./x_gitres/ipso_logo.png) |

- [1. Neo4j .NET Driver](#1-neo4j-net-driver)
  - [1.1. Installation](#11-installation)
  - [1.2. Code-Beispiel](#12-code-beispiel)
  - [1.3. Einsatzmöglichkeiten](#13-einsatzmöglichkeiten)
- [2. Aufgaben](#2-aufgaben)
  - [2.1. Using Neo4j from .NET](#21-using-neo4j-from-net)

---

</br>

# 1. Neo4j .NET Driver

Der [Neo4j .NET Driver](https://neo4j.com/docs/getting-started/languages-guides/neo4j-dotnet/) ist eine offizielle .NET-Bibliothek für die Interaktion mit Neo4j-Datenbanken. Er ermöglicht Entwicklern, Cypher-Abfragen direkt aus C#- oder anderen .NET-Sprachen auszuführen. Der Treiber unterstützt asynchrone und synchrone Kommunikation mit der Datenbank und nutzt das Bolt-Protokoll für schnelle und sichere Verbindungen

## 1.1. Installation

Installiere den Neo4j .NET Driver via NuGet:
`dotnet add package Neo4j.Driver`

## 1.2. Code-Beispiel

```c#
using Neo4j.Driver;

var uri = "bolt://localhost:7687";
var user = "neo4j";
var password = "password";

using var driver = GraphDatabase.Driver(uri, AuthTokens.Basic(user, password));
using var session = driver.AsyncSession();

var query = "MATCH (p:Person {name: $name}) RETURN p";
var parameters = new { name = "Alice" };

var result = await session.RunAsync(query, parameters);

await foreach (var record in result)
{
    var person = record["p"].As<INode>();
    Console.WriteLine($"Found person: {person["name"]}");
}
```

## 1.3. Einsatzmöglichkeiten

- Integration von Neo4j in .NET-Anwendungen wie Web-APIs, Microservices oder Desktop-Apps.
- Datenanalysen, Empfehlungsalgorithmen und Graph-basierte Abfragen.

Der Neo4j .NET Driver ist eine leistungsstarke Möglichkeit, die Flexibilität von Neo4j mit der Leistung von .NET zu kombinieren.

</br>

# 2. Aufgaben

## 2.1. Using Neo4j from .NET

| **Vorgabe**             | **Beschreibung**                                                                           |
| ----------------------- | ------------------------------------------------------------------------------------------ |
| **Lernziele**           | Können einen Datenbanktreiber installieren                                                 |
|                         | Können CRUD Operationen in der gewählten Programmiersprache ausführen                      |
| **Sozialform**          | Einzelarbeit                                                                               |
| **Auftrag**             | siehe unten                                                                                |
| **Hilfsmittel**         | [Neo4j .NET Driver](https://neo4j.com/docs/getting-started/languages-guides/neo4j-dotnet/) |
| **Erwartete Resultate** |                                                                                            |
| **Zeitbedarf**          | 90 min                                                                                     |
| **Lösungselmente**      | Lauffähige C# Anwendung                                                                    |

Lerne wie Datenbankbefehle (CRUD) in Deiner bevorzugten Sprache mit dem zugehörigen Neo4j-Treiber ausführt werden können.

**Aufgabe 1 - Neo4j .Net Driver:**

Rufe den Link zur offiziellen Neo4j Treiber auf und lese, wie der .NET Treiber in einem .NET-Projekt installiert und konfiguriert werden kann.
Erstelle ein neues Konsolen-Projekt, füge diesem die Klasse HelloWorldExample hinzu und versuche einen Greeting Node einzufügen.

- [getting-started](https://neo4j.com/docs/getting-started/languages-guides/neo4j-dotnet/)
- [dotnet-manual](https://neo4j.com/docs/dotnet-manual/current/get-started/)

**Aufgabe 2 - Example Project:**

Lade von GitHub das offizielles Beispielprojekt [movies-dotnetcore-bolt](https://github.com/neo4j-examples/movies-dotnetcore-bolt) herunter. Analysiere den Programmcode und prüfen, ob dieser fehlerfrei ausgeführt werden kann.
