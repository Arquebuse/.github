# Arquebuse project

Arquebuse is an open-source notification system tailored specifically for enterprise environments, providing secure and efficient delivery of targeted notifications to Windows desktop users.

Designed with simplicity at its core, Arquebuse integrates seamlessly with existing infrastructure, allowing administrators to easily select recipients, send critical application outage alerts, and request user acknowledgments directly via the native Windows notification center. 

It respects users' "Do Not Disturb" settings, ensuring alerts are delivered respectfully without disruption. Arquebuse simplifies enterprise communication, empowering organizations to effectively manage notifications at scale.

## Modules

- [**Desktop‑App**](https://github.com/Arquebuse/desktop-app): Windows service that registers with WNS, receives and displays notifications.
- [**Controller‑Core**](https://github.com/Arquebuse/controller-core): .NET 8 Minimal API managing client registrations, AD queries, and sending WNS notifications (uses SQLite).
- [**Controller‑CLI**](https://github.com/Arquebuse/controller-cli): PowerShell Core module to manage subscriptions and send notifications via Controller‑Core.

## Goals

- Deliver targeted Windows notifications at scale.
- Integrate with Active Directory for precise targeting.
- Maintain simplicity, security, and enterprise readiness.

## Architecture Overview

Arquebuse is composed of three loosely coupled modules:

1. [**Desktop‑App**](https://github.com/Arquebuse/desktop-app) (client) connects to WNS and displays toasts.
2. [**Controller‑Core**](https://github.com/Arquebuse/controller-core) (server) exposes REST endpoints, queries LDAP, persists subscriptions, and invokes WNS.
3. [**Controller‑CLI**](https://github.com/Arquebuse/controller-cli) (admin) is a PowerShell module consuming the REST API to manage and send alerts.

## Technologies

- [**Desktop‑App**](https://github.com/Arquebuse/desktop-app): .NET 8 Windows Service, WNS integration, JSON logging
- [**Controller‑Core**](https://github.com/Arquebuse/controller-core): .NET 8 Minimal API, Kestrel (HTTPS), System.DirectoryServices (LDAP), SQLite
- [**Controller‑CLI**](https://github.com/Arquebuse/controller-cli): PowerShell 7+ module, REST API over HTTPS
