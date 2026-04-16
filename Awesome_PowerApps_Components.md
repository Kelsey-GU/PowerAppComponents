# Awesome Power Apps Components

A curated list of awesome Power Apps Component Framework (PCF) controls, libraries, open-source repositories, and resources. 

---

## Contents
- [Official Microsoft Resources](#official-microsoft-resources)
- [Community Galleries](#community-galleries)
- [Notable GitHub Repositories](#notable-github-repositories)
- [Design & UI Toolkits](#design--ui-toolkits)
- [Security & Evaluation Checklist](#security--evaluation-checklist)

---

## Official Microsoft Resources
The best starting points for enterprise-grade, supported implementations.

* **[Creator Kit (Power CAT)](https://github.com/microsoft/powercat-code-components)** - A comprehensive library of Fluent UI-based controls, templates, and utilities. **Highly Recommended** for modern app design.
* **[Power Apps Samples](https://github.com/microsoft/PowerApps-Samples)** - The official Microsoft repository for sample code, including numerous raw PCF component examples useful for learning.
* **[AppSource](https://appsource.microsoft.com/)** - Microsoft's official marketplace where you can find certified third-party/ISV PCF components.

## Community Galleries
Hubs where developers share their custom PCF creations.

* **[PCF Gallery](https://pcf.gallery/)** - The definitive community-driven database for discovering custom Power Apps controls. Features hundreds of components with direct links to the creators' GitHub repos.

## Notable GitHub Repositories
Highly valued open-source component collections maintained by independent developers and community groups.

* **[MscrmTools / PCF-Controls](https://github.com/MscrmTools/PCF-Controls)** - Extensive collection of widely used controls including specialized inputs, lookups, and visual switches.
* **[rwilson504 / PCFControls](https://github.com/rwilson504/PCFControls)** - Features specialized canvas and PCF controls such as file uploaders, drag-and-drop utilities, and grid replacements utilizing Fluent UI.
* **[365lyf / PCFControls](https://github.com/365lyf/PCFControls)** - A catalogue of unique controls including swipe detection layers, countdown timers, and specialized progress bars.

## Design & UI Toolkits
Resources aimed at styling and structuring app development.

* **[PnP Power Apps Design Toolkit](https://github.com/pnp/powerapps-designtoolkit)** - Maintained by the M365 Patterns & Practices (PnP) team, providing reusable thematic components and strict UI guidance.

## Security & Evaluation Checklist
> [!WARNING]
> Community components execute within your app's security context. Always test thoroughly in a sandbox first.

When pulling from repositories on this list—especially community ones—evaluate the following:
* **Maintenance:** Ensure the repository has been updated recently (last 6-12 months) and issues are actively monitored.
* **Licensing:** Verify the repository uses an acceptable license (e.g., MIT, Apache 2.0) for your organization's use case.
* **External APIs (CSP):** Check the source code for outbound API calls. If they exist, you must allowlist those domains in your Power Platform admin center via Content Security Policy.
* **Deployment:** Always deploy an unmanaged/managed solution containing new controls to a **Development/Sandbox environment** before moving it to Production.
