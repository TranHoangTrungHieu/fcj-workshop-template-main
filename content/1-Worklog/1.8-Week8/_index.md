---
title: "Week 8 Worklog"
weight: 8
chapter: false
pre: "<b>1.8.</b>"
---

## 🎯 Week 8 Objectives
- Learn DynamoDB design (PK/SK model).
- Implement CRUD Lambda functions for events.
- Build API Gateway → Lambda → DynamoDB pipeline.
- Learn EventBridge scheduling for calendar events.

---

## 📅 Tasks Completed

| Day | Task Description | Reference |
|-----|------------------|-----------|
| Monday | DynamoDB basics & table design decisions | https://youtu.be/y99YGaQjgxQ |
| Tuesday | Create DynamoDB table for events (PK: userId, SK: eventId) | — |
| Wednesday | Write Lambda functions for Create/Read/Update/Delete events | https://youtu.be/JIbIYZIeLqU |
| Thursday | EventBridge scheduler research (Cron, rules, targets) | https://youtu.be/eI3W6CXYhYw |
| Friday | Implement scheduled triggers for reminders | — |

---

## 🧠 Knowledge Gained
- NoSQL modeling vs SQL.
- Designing scalable partition keys.
- Lambda execution model & cold starts.
- EventBridge scheduled events.

---

## 🛠 Practical Skills
- Define DynamoDB table schema.
- Build serverless CRUD API.
- Build scheduled reminder triggers.
- Log events with CloudWatch Logs.

---

## ✔️ Week 8 Summary
Aurora Calendar backend was implemented: events API, scheduling logic, and DynamoDB integration.
