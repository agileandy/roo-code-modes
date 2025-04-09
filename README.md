# Agentic Swarm Prompts for TDD Software Development


**A collection of specialized system prompts designed to orchestrate a swarm of AI coding agents for robust, test-driven software development.**

Primarily designed and tested with the [RooCode](https://docs.roocode.com) agentic coding tool, the principles and structure can be adapted for other multi-agent AI development environments.

## Overview

Coordinating multiple AI agents to build software effectively requires clear roles, defined responsibilities, and a structured workflow. This project provides a set of fine-tuned system prompts for distinct agent roles, enabling them to collaborate efficiently on software projects.

The core focus is on **Test-Driven Development (TDD)**, ensuring quality from the outset. It also emphasizes security, performance, user experience, rapid feedback via MVPs, and creating code optimized for future AI interaction (Agentic Coding).

## Core Philosophy & Principles

These prompts are built upon the following development principles:

1.  **Test-Driven Development (TDD):** The "Red -> Green -> Refactor" cycle is central. Tests define requirements and are written first.
2.  **Security by Design:** Security considerations are integrated from the architecture phase onwards.
3.  **Performance Awareness:** Efficiency is considered during design and implementation.
4.  **User Experience (UX) Focus:** The end-user's needs guide requirements and validation.
5.  **MVP & Pareto (80/20):** Prioritize the core 20% of features delivering 80% of the value for rapid feedback and iteration.
6.  **Agentic Coding:** Code should be modular, clear, well-documented (docstrings, *why* comments), and token-efficient for maintainability by both humans and AI agents.
7.  **Concise Dev Log:** Maintain essential context (`activeDevelopment.md`) for seamless handoffs and session resumption.
8.  **Trunk-Based Development:** Utilize short-lived feature branches merging frequently into the main trunk.
9.  **Minimal & Efficient Artifacts:** Maintain a defined set of project documents, avoiding redundancy and optimizing for clarity and token efficiency.

## The Agent Roles

The swarm consists of the following specialized agents:

*   **👑 Team Lead (Orchestrator):** Manages the overall workflow, delegates tasks, monitors progress, and ensures adherence to principles. Initiates foundational setup (like Git repo) early.
*   **🏗️ Software Architect:** Designs the system architecture, defines the technical plan, and collaborates with UX/Security. Creates `systemDesign.md`.
*   **🎨 UX Designer:** Champions the user experience, defines user flows, and validates implementation against UX goals. Contributes primarily to `projectOverview.md`.
*   **🛡️ Security Consultant:** Integrates security practices into the design, defines security requirements, and reviews implementation for vulnerabilities. Contributes to `systemDesign.md`.
*   **🧪 Software Engineer in Test (SET):** Writes failing tests first (Red phase) based on requirements, defining "done". Maintains the test suite (part of Source Code).
*   **💻 Software Engineer:** Writes the minimum code to pass tests (Green phase), then refactors code and tests for quality and maintainability. Updates `activeDevelopment.md` and `.aiderrules`.
*   **🚀 DevOps Engineer:** Manages the codebase (Git), CI/CD pipelines, environments, deployments, and generates user-facing `CHANGELOG.md` release notes. Sets up the repository early and maintains `techEnvironment.md`.
*   **✍️ Technical Writer:** Ensures all documentation artifacts are clear, concise, up-to-date, and non-redundant. Guards the integrity of the project's recorded memory across all `.md` files.

## The Workflow

The intended workflow emphasizes TDD and early setup:

```
mermaid
graph TD
    A[Start Project] --> B{Design & Plan};
    B --> C[Architect Defines Plan];
    %% DevOps setup starts early/in parallel %%
    A --> D(DevOps Sets Up Repo & CI Stub);
    C --> E[Tech Writer Documents Design in systemDesign.md];
    D --> F[Repo Ready];
    E --> G{Write Tests (SET) -> Commit to Repo};
    F --> G;
    G --> H{Write Code (Engineer) -> Commit to Repo};
    H --> I[Update Docs (Writer/Eng) -> Commit to Repo];
    I --> J{Build & Deploy (DevOps)};
    J --> K[Release Notes (DevOps) -> Update CHANGELOG.md];
    K --> L[Cycle Complete/Next Feature];
