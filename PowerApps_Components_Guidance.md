# Power Apps Components Guidance: Finding High-Quality Resources

When building Power Apps, leveraging pre-built components can significantly accelerate development, improve consistency, and elevate the user experience. This guide will help you navigate the best official Microsoft resources and the most reputable open-source community repositories to find the best components for your needs.

---

## 1. Official Microsoft Resources

For enterprise applications where stability, security, and long-term support are paramount, always start by checking Microsoft's official resources.

### Creator Kit (by Microsoft Power CAT)
The **Creator Kit** is the gold standard for production-ready Power Apps components. Developed by the Power Customer Advisory Team (Power CAT), it provides a set of reusable components based on the Fluent UI framework. 
* **Best for:** Ensuring your apps have a consistent, modern, and native Microsoft look and feel. It includes advanced controls like details lists, command bars, and dialogs.
* **Source:** [Microsoft/powercat-code-components on GitHub](https://github.com/microsoft/powercat-code-components) or [AppSource](https://appsource.microsoft.com/en-gb/product/dynamics-365/microsoftpowercatarch.creatorkit1)
* **Quality Level:** 🟢 **High** (Official, Enterprise-grade, Supported by community/CAT)

### Power Apps Samples
Microsoft maintains an official repository containing various sample codes for Power Apps, including examples specifically for the Power Apps Component Framework (PCF).
* **Best for:** Developers looking to learn how to build their own custom PCF controls by examining official code samples and best practices.
* **Source:** [Microsoft/PowerApps-Samples on GitHub](https://github.com/microsoft/PowerApps-Samples)
* **Quality Level:** 🟢 **High** (Official codebase examples)

---

## 2. Community Galleries and Community Open Source

When official components do not meet your specific requirements (e.g., you need a specialized Gantt chart, interactive map, or unique UI toggle), the community has a vast ecosystem of open-source components.

### PCF Gallery
The **PCF Gallery** is the definitive, community-maintained collection of code components for Power Apps. It is the primary hub for discovering custom controls.
* **Best for:** Browsing a massive database of UI enhancements, custom data visualizers, and utility controls created by developers worldwide. Entries usually link directly to the creator's GitHub repo for the source code.
* **Source:** [pcf.gallery](https://pcf.gallery/)
* **Quality Level:** 🟡 **Variable** (Community-maintained; quality depends on the individual author)

### Top Community GitHub Repositories
Several trusted independent developers and organizations maintain high-quality open-source components on GitHub:
* **[MscrmTools / PCF-Controls](https://github.com/MscrmTools/PCF-Controls):** Contains various widely used PCF controls ranging from custom switches to advanced lookup alternatives.
* **[PnP Power Apps Design Toolkit](https://github.com/pnp/powerapps-designtoolkit):** Maintained by the Microsoft 365 Patterns and Practices (PnP) team, focusing on UI guidance and reusable components.
* **[rwilson504 / PCFControls](https://github.com/rwilson504/PCFControls):** A great collection of canvas and PCF controls, including file uploaders/downloaders and grid replacements utilizing Fluent UI.

---

## 3. How to Evaluate and Choose a Component

Before importing any third-party or community-created component into your production environment, use this checklist to ensure it is safe and suitable:

> [!CAUTION]
> Code components have access to data and can execute within the security context of your app. Always review and validate third-party code before deploying it to production.

1. **Check the Origin and Maintenance:**
   * Is it officially from Microsoft, or from a community member?
   * When was the GitHub repository last updated? (Look for projects updated within the last 6-12 months).
   * Are there many unresolved issues in the "Issues" tab, or is the developer responsive?
2. **Review the Licensing:**
   * Verify the open-source license (e.g., MIT, Apache 2.0). Ensure the license allows for commercial or internal organizational use.
3. **Audit the Code (Security):**
   * Review the source code specifically for external API calls. If the component interacts with external services, you will need to allowlist those sources in your Power Platform admin center due to Content Security Policy (CSP) rules.
4. **Test in a Sandbox First:**
   * **Never** install an unverified managed solution directly into your production environment. Always import and test it in a developer or sandbox environment to ensure it performs as expected without breaking existing functionality.

## Summary Recommendation
Always try to solve your UI/UX needs using the out-of-the-box controls or the **Microsoft Creator Kit** first. If a specific functionality is missing, search the **PCF Gallery** for a highly-rated, recently updated community component, and thoroughly vet the GitHub source before implementation.
