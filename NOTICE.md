---
tema: Atribuciones globales del repositorio
verificado_fecha: 2026-11-10
tags: [meta, license, attribution, general]
---

# Atribuciones y fuentes

Este repositorio (`swe-certifications`) contiene apuntes de estudio para múltiples certificaciones de ingeniería de software, derivados de fuentes oficiales de cada plataforma. Cada certificación tiene su propia carpeta. En los tracks de formato vault (Azure), cada archivo cita sus URLs en el frontmatter (`fuentes:`). En los tracks de Anthropic, cada nota indica al principio su origen (curso oficial o nota reconstruida y las páginas consultadas).

## Plataformas cubiertas (actuales y futuras)

### Anthropic / Claude

- **Anthropic Academy:** https://academy.claude.com — cursos oficiales (Claude 101, Building with the Claude API, Claude Code in Action, Introduction to Model Context Protocol, etc.). Contenido propiedad de Anthropic.
- **Anthropic Partner Academy (Skilljar):** https://anthropic-partners.skilljar.com — rutas de preparación de las certificaciones *Claude Certified Associate* y *Claude Certified Architect*. Contenido propiedad de Anthropic.
- **AI Fluency: Framework & Foundations:** Copyright 2025 Rick Dakan, Joseph Feller y Anthropic, publicado bajo **CC BY-NC-SA 4.0** (https://creativecommons.org/licenses/by-nc-sa/4.0/). Los PDF de este curso incluidos en `anthropic/*/APUNTES-CURSOS/` y las notas de AI Fluency mantienen esa licencia: atribución, **sin uso comercial** y compartir igual.
- **Documentación técnica:** https://platform.claude.com/docs (Claude API) y https://code.claude.com/docs (Claude Code y Claude Agent SDK). Contenido propiedad de Anthropic.
- **Artículos de ingeniería:** https://www.anthropic.com/engineering y https://claude.com/resources.
- **Model Context Protocol:** https://modelcontextprotocol.io

> [!warning] Material de terceros en los tracks de Anthropic
> Las notas que reproducían el texto de las lecciones oficiales y la guía oficial del examen **no se publican** en este repositorio. Lo publicado son resúmenes y notas reconstruidas con citas breves y su fuente, simulacros propios y los materiales de *AI Fluency* bajo su licencia CC BY-NC-SA 4.0. Si eres titular de algún material incluido y quieres que se retire, abre un issue.

### Microsoft / Azure

- **Documentación:** https://learn.microsoft.com — licencia Creative Commons Attribution 4.0 (CC BY 4.0).
- **Repositorios GitHub:** https://github.com/MicrosoftDocs (CC BY 4.0).
- **Azure SDKs:** https://github.com/Azure (MIT).
- **Microsoft Agent Framework:** https://github.com/microsoft/agent-framework (MIT).
- **Prompty:** https://github.com/microsoft/prompty (MIT).
- **Prompt Flow:** https://github.com/microsoft/promptflow (MIT).
- **Certificaciones:** https://learn.microsoft.com/credentials/certifications

### Amazon Web Services (AWS)

- **Documentación:** https://docs.aws.amazon.com — licencia propietaria, uso permitido para fines educativos con atribución.
- **Guías de certificación:** https://aws.amazon.com/certification
- **AWS SDKs:** https://github.com/aws (Apache 2.0 mayormente).

### Google Cloud Platform (GCP)

- **Documentación:** https://cloud.google.com/docs — licencia Creative Commons Attribution 4.0 (CC BY 4.0) en la mayoría de páginas.
- **Repositorios GitHub:** https://github.com/GoogleCloudPlatform
- **Certificaciones:** https://cloud.google.com/certification

### Kubernetes / CNCF

- **Documentación:** https://kubernetes.io — Creative Commons Attribution 4.0 (CC BY 4.0).
- **Repositorios:** https://github.com/kubernetes (Apache 2.0).
- **CNCF certifications:** https://www.cncf.io/training/certification (CKA, CKAD, CKS, KCNA, KCSA).

### HashiCorp

- **Documentación:** https://developer.hashicorp.com — licencia MPL 2.0 / propietaria.
- **Repositorios:** https://github.com/hashicorp (MPL 2.0 / BSL).

### Linux Foundation

- **Documentación:** https://training.linuxfoundation.org
- **Certificaciones:** LFCS, LFCE, KCNA, etc.

### Otros recursos open source

- **OpenAI Python SDK:** https://github.com/openai/openai-python (Apache 2.0).
- **PyPI:** https://pypi.org (información pública de paquetes).
- **Python:** https://docs.python.org (PSF License).

## Marcas registradas

Las siguientes marcas son propiedad de sus respectivos titulares y se mencionan únicamente con fines descriptivos y educativos:

- Microsoft, Azure, Azure AI Foundry, GitHub, Visual Studio Code — Microsoft Corporation.
- AWS, Amazon Web Services y servicios asociados — Amazon.com, Inc.
- Google Cloud, GCP y servicios asociados — Google LLC.
- Kubernetes — The Linux Foundation.
- Docker — Docker, Inc.
- Terraform, Vault, Consul, Nomad — HashiCorp.
- OpenAI, GPT — OpenAI.
- Anthropic, Claude — Anthropic PBC.

Este repositorio **no está afiliado, patrocinado ni avalado** por ninguna de las entidades mencionadas.

## Cumplimiento de atribución (CC BY 4.0)

Conforme a CC BY 4.0, este repositorio:

1. Indica la fuente original de cada hecho técnico (URLs en el frontmatter de cada archivo, o el bloque de origen al principio de cada nota en los tracks de Anthropic).
2. Enlaza a las licencias originales de las fuentes.
3. Indica que el contenido ha sido transformado, sintetizado y reorganizado, no copiado literalmente (salvo citas breves con su fuente y los materiales de *AI Fluency*, que se redistribuyen bajo su propia licencia CC BY-NC-SA 4.0).
4. No sugiere endoso por parte de las entidades originales.
5. Mantiene avisos de copyright y atribución.

## Reportar atribuciones faltantes

Si detectas una atribución faltante, incorrecta o un posible problema de licencia en cualquier archivo del repositorio, por favor abre un issue en GitHub describiendo:

- Archivo afectado.
- Fuente original que falta atribuir.
- Licencia original de esa fuente.

Las correcciones de atribución se procesan con prioridad.
