# Fixes & To-Do List for Currency Converter SOAP Service

This README documents issues and missing components in the SOAP-based Currency Converter Spring Boot project.

---

## Issues & Fixes Needed

### 1. Missing or Incorrect XML Binding
- JAXB classes for request/response (`ConvertCurrencyRequest`, `ConvertCurrencyResponse`) are either not generated or manually incomplete.
- Fix: Generate JAXB classes from the `.xsd` file using the Maven plugin or `xjc` tool.

---

### 2. Endpoint Logic is Hardcoded
- Conversion rate is hardcoded (`Double conversionRate = 3.2;`).
- Fix: Make it dynamic or configurable through application properties or an external API.

---

### 3. WSDL Not Auto-Generated
- WSDL endpoint (`/ws/currencies.wsdl`) is referenced but may not be generating correctly.
- Fix: Ensure `WebServiceConfig` has the correct bean setup and `@EnableWs` is used.

---

### 4. `application.properties` is Missing
- No configuration for endpoint base path, logging, or server port.
- Fix: Add basic setup like:
  ```properties
  server.port=8080
  logging.level.org.springframework.ws=TRACE
5. No Test Cases
Missing unit or integration tests for the endpoint.

Fix: Add tests using MockWebServiceClient.

6. No Error Handling
No validation or exception handling for missing or invalid input.

Fix: Add try/catch or use Spring exception resolvers.
