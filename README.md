# Kyle Spivey

Forward-deployed systems builder and founder of JobSpark Systems.

I build software around how an operation actually works. My background is in maritime operations, moving logistics, and business ownership. I built JobSpark after seeing scheduling, crew coordination, paperwork, and missed handoffs break down inside a live service business.

[Run the JobSpark demo](https://jobsparksystems.app)

[Read the architecture and engineering proof](https://github.com/SKYBEAMS/SKYBEAMS/blob/main/ENGINEERING_PROOF.md)

[Visit JobSpark Systems](https://jobsparksystems.com)

## What I Built

I built JobSpark to coordinate intake, scheduling, truck and crew assignments, dispatch, communications, field execution, closeout, history, and payroll around one accepted job record.

I focused on what happens when reality changes. A customer asking for a different time cannot silently rewrite a locked dispatch plan. Missing contract information pauses completion. Retrying a completed payroll step cannot count the same work twice.

Two workflows show the architecture best:

- Customer confirmation with owner-reviewed changes, including changes after dispatch locks
- Validated closeout with checkpoints that resume interrupted work without duplicating payroll

I mapped both workflows in the [engineering overview](https://github.com/SKYBEAMS/SKYBEAMS/blob/main/ENGINEERING_PROOF.md).

## Evidence Behind the Demo

I use focused tests against the Firestore emulator to prove the difficult parts of the lifecycle. They cover interrupted closeout, duplicate requests, competing crew assignments, approved changes rebuilding dependent communications, communication recovery, and truck unlock/relock cycles.

[See the tested behavior and its limits](https://github.com/SKYBEAMS/SKYBEAMS/blob/main/ENGINEERING_PROOF.md#tested-behavior).

## Current Boundary

I deployed the application and separated the public demo into a synthetic workspace. The demo does not use customer records or send live messages.

For V1, I keep Make as the automatic intake path. Autonomous mode controls automatic communications. Native SignalWire call-to-job intake remains staged.

Before onboarding the first customer, I still need to verify the live messaging configuration, production workers, and external contract reader. The demo proves the product flow and interface; my private repository contains the implementation and lifecycle tests.

## Stack

I built JobSpark with React, TypeScript, Vite, Tailwind CSS, Node.js, Express, Firestore, Firebase Authentication, and Firebase Storage. I use Make for the current intake handoff, SignalWire at the communications boundary, GitHub Actions for verification, Vercel for the frontend, and Render for the API.

## What I Do

I map an operation, define its records and decision rules, and carry that model through implementation. I focus on the shared state behind multiple workflows: who can change it, what should happen next, and what requires a person's judgment.

I am looking for engineering and implementation work where operating experience and systems building belong in the same role.
