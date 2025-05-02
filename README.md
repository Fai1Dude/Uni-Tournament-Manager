# Uni-Tournament-Manager
### (the main goal was the Figma Design to show key concepts of design and understanding of it)
University tournament manager app developed using Java and Java FX as frontend  
A **Java-based back-end** plus an extensive **Figma-designed front-end** for managing university-level sports tournaments.  
The goal is to let organizers create events, register teams/players, auto-generate match tables, and publish live results through a slick JavaFX GUI.

> **Status:** back-end core models & JSON login demo are functional, but the GUI and DB layers are still work-in-progress.  
> A full, multi-screen interface was prototyped in Figma (see `SWEFRONTENDPRJ206.fig`) and is ready to be converted to FXML.

---

## ✨ Current back-end highlights

| Module | What it does | File(s) |
|--------|--------------|---------|
| **Auth demo** | Simple REST call → parses JSON into a `User` object via Jackson | `AuthenticateUser.java` :contentReference[oaicite:0]{index=0}:contentReference[oaicite:1]{index=1} |
| **Domain model** | `Student`, `Team`, `Match`, `Tournament` with elimination / round-robin generators | `Student.java`, `Team.java`, `Match.java`, `Tournament.java` :contentReference[oaicite:2]{index=2} |
| **CLI demo** | Creates a sample tournament, randomizes scores, authenticates a demo user | `Main.java` :contentReference[oaicite:3]{index=3}:contentReference[oaicite:4]{index=4} |
| **JSON mapping** | Uses `jackson-databind-2.13.0.jar` (bundled) |

Planned database calls (`archive()`, etc.) are stubbed for now. All entities are plain POJOs → ideal for later JPA / JDBC integration.

---

## 🎨 Front-end concept (Figma)

Although not yet coded, the **front-end work represents ~70 hours of design**:

| Screen | Purpose | Design notes |
|--------|---------|--------------|
| **Landing / Sign-In** | Student/Staff login, SSO-ready | KFUPM green gradient, large mascot illustration |
| **Dashboard** | “My Tournaments”, quick actions | Card grid, dynamic progress bars |
| **Bracket view** | Tree layout for elimination rounds | Zoomable, drag-scroll, team logos |
| **Score entry** | Staff-only modal to update scores | Number spinners, validation badges |
| **Settings** | Dark/light theme, notifications | Uses the *Figmotion* animation plugin |

Color palette & typography follow **Material 3** guidelines; components were designed with the **Figma Auto-Layout** and **Variants** features so they translate cleanly to **JavaFX + FXML**.

> *The Figma file is included in the repo (`SWEFRONTENDPRJ206.fig`).  
> Use the **“Figma → FXML Exporter”** plugin to generate starter `.fxml` files once the plugin bug is resolved.*

---

## 🚀 Running the demo

```bash
# compile everything (requires Java 17+)
javac -cp jackson-databind-2.13.0.jar *.java

# run CLI showcase
java  -cp .:jackson-databind-2.13.0.jar Main

# 🛣️ Roadmap
Fix Figma-to-FXML exporter and scaffold JavaFX controllers.

Implement SQLite / MySQL persistence (JPA or plain JDBC).

Replace demo HTTP auth with real campus SSO / JWT.

Add unit tests (JUnit 5) for match generators.

Package with Maven (shade Jackson) and create a one-click installer.

# 🙏 Acknowledgements
Solo work by Faisal Alhamdi.
