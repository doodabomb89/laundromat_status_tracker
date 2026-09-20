# Laundromat Status SG

A real time washing machine and dryer availability checker for laundromats, letting customers check whether a machine is free before visiting. Built under my startup VeenaTech.

## The Problem

Anyone who has gone to a laundromat knows the frustration of showing up with a bag of laundry only to find every washer and dryer already in use. There is currently no way for a customer to check machine availability remotely, so people either wait around, come back later and hope for the best, or waste a trip entirely. Laundromat Status SG solves this by giving customers live, accurate machine availability from their phone, with zero manual input required from the shop owner.

## Overview

The system detects whether a washing machine or dryer is currently running by monitoring its power draw, then surfaces live availability on a simple web dashboard. I have reached out to several laundromats directly to validate the idea and bring the product to real locations.

## My Role

Sole builder. Designed the hardware detection approach, built the backend and database, and built the frontend dashboard for displaying live machine status.

## Current Status

The core detection logic and database are built and working. A Supabase database is set up to store laundromat, machine, and live status data, and an HTML interface for displaying washer and dryer availability is ready. I have contacted several laundromats to validate demand and begin onboarding real locations.

## Hardware Approach

The first version of the hardware used a current sensor connected to an ESP32 microcontroller, wired directly to a washing machine's power line to detect when it was drawing current and therefore running. This worked in principle but proved difficult to build reliably, since it required custom circuit wiring and careful calibration for each machine.

I then switched to using smart plugs instead, which turned out to be a far more efficient approach. A smart plug sits between the machine and the wall socket, reports live power draw over its own local API, and requires no custom wiring or circuit debugging at all. This made the hardware side dramatically simpler to install and far more reliable to run unattended in a real laundromat.

## Tech Stack

- Hardware: Smart plug monitoring live power draw to detect machine activity
- Backend and database: Supabase
- Frontend: HTML interface displaying live washer and dryer status

## How It Works

Each washing machine or dryer is connected through a smart plug. The plug reports live power draw, which is used to determine whether the machine is currently running or idle. This status is written to a Supabase database, which the frontend dashboard reads from to show customers, in real time, which machines are free.

## Screenshots / Demo

Add photos of the physical smart plug setup and a screenshot of the dashboard here.

## What I Learned

Starting with a custom current sensor and ESP32 setup taught me a lot about circuit design, but it also taught me when to cut a technically interesting approach in favor of something simpler and more reliable. Switching to smart plugs meant giving up some of the custom control of the original design, but it made the hardware dramatically easier to deploy and maintain across multiple laundromat locations, which matters far more for a real product than a cleverer circuit.
