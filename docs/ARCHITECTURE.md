# Architecture

The framework follows a modular plugin architecture for WordPress:

- Domain modules: inbox, lead lifecycle, tasking, quotes, and in-person order flows.
- Integration modules: telephony adapters and outbound notification channels.
- Analytics layer: normalized metrics pipeline feeding executive dashboards.
- Audit layer: ownership transitions, activity logs, and operational traceability.

Design priorities:
- Provider-agnostic integration contracts.
- Extensible entities and workflow states.
- Separation of domain logic, transport adapters, and presentation components.
