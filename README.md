# Kyle Spivey

Forward-deployed systems builder and founder of JobSpark Systems.

I build software around how an operation actually works. My background is in maritime operations, moving logistics, and business ownership. JobSpark grew out of the scheduling, crew coordination, paperwork, and missed handoffs I saw firsthand.

[Try the JobSpark demo](https://jobsparksystems.app)

[Architecture and engineering details](https://github.com/SKYBEAMS/SKYBEAMS/blob/main/ENGINEERING_PROOF.md)

[Website and contact](https://jobsparksystems.com/#contact)

## JobSpark

JobSpark connects intake, scheduling, truck and crew assignments, dispatch, customer communications, field execution, closeout, history, and payroll around a shared job record.

The important part is what happens when something changes. A customer asking for a different time does not silently change the dispatch plan. Missing closeout information pauses completion. Retrying a completed payroll step should not count the same work twice.

Two workflows explain the design best:

- Customer confirmation and owner-reviewed changes, including changes after dispatch is locked.
- Validated closeout with checkpoints that let interrupted processing resume.

Both are covered in the [engineering overview](https://github.com/SKYBEAMS/SKYBEAMS/blob/main/ENGINEERING_PROOF.md).

## Current status

The application is deployed. The public demo uses synthetic data in an isolated workspace and does not send live customer messages.

Make remains the automatic intake path for V1. Autonomous mode controls automatic communications, not intake. Native SignalWire call-to-job intake remains staged.

Live messaging configuration and production worker checks are still part of first-customer activation. The demo is a walkthrough of the product, not proof that those live services have been verified.

Application code and customer configuration are private. This public repository contains the architecture overview.

## Stack

React, TypeScript, Vite, Tailwind CSS, Node.js, Express, Firestore, Firebase Authentication and Storage. Make handles the current intake handoff. SignalWire is the communications provider integration. Delivery uses GitHub Actions, Vercel, and Render.

## What I bring

I can map an operation, define its records and decision rules, and carry that model through implementation. My focus is the shared state behind multiple workflows: who can change it, what should happen next, and what needs a person's judgment.

I'm looking for engineering and implementation work where that combination of operating experience and systems building is useful.
