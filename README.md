# 🌊 AI-Powered River Feature Inventory Agent

### Drone-Based Hydromorphological Mapping · YOLO + ByteTrack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![YOLO](https://img.shields.io/badge/YOLO-v8%20%7C%20v11-00FFFF?style=flat)
![ByteTrack](https://img.shields.io/badge/Tracking-ByteTrack-orange?style=flat)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat&logo=opencv&logoColor=white)
![MCP](https://img.shields.io/badge/Model%20Context%20Protocol-MCP-black?style=flat)
![WGS84](https://img.shields.io/badge/CRS-WGS84%20%7C%20UTM-green?style=flat)

[![Watch the video](https://img.youtube.com/vi/C0hAM_ieXMw/maxresdefault.jpg)](https://youtu.be/C0hAM_ieXMw)

> An agentic AI system that turns drone imagery and video of river corridors into a **deduplicated, geo-referenced inventory of instream wood**. Built with YOLO object detection and ByteTrack multi-object tracking inside an agentic IDE workflow, it outputs Excel- and GIS-ready records with WGS84 coordinates for every detected feature — **counts, not scores**.

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Feature Classes Detected](#-feature-classes-detected)
- [Outputs](#-outputs)
- [Design Principle](#-design-principle)
- [Applications](#-applications)
- [How It Was Built](#%EF%B8%8F-how-it-was-built)
- [Skills](#-skills)

---

## 🔎 Overview

Traditional river habitat surveys rely on manual walkover mapping — slow, subjective, and difficult to repeat consistently across long reaches. This project is an AI agent that converts drone imagery and video of river corridors into a precise, quantitative inventory of channel features.

The agent uses a **YOLO detection backbone** paired with **ByteTrack multi-object tracking**, so every feature is assigned a persistent track ID across frames. This eliminates the double-counting problem that makes frame-by-frame detection unusable for inventory work:

> A single log jam appearing in 200 frames is counted **once**, not 200 times.

Each detection is then geo-referenced. Using UAV telemetry (GNSS position, altitude above ground, gimbal orientation) and camera intrinsics, pixel coordinates are converted to real-world **WGS84 latitude/longitude**, giving every logged feature a mappable location rather than just a bounding box.

---

## 🌲 Feature Classes Detected

| Class | Description |
| :--- | :--- |
| 🪵 **Fallen trees / instream wood** | Already in or across the channel |
| 🌳 **Leaning trees** | Early-warning indicator for future recruitment |
| 🪵 **Large woody debris & log jams** | Accumulated wood structures |
| 🌱 **Wood stumps** | Remaining rooted stumps |

---

## 📤 Outputs

| Output | Purpose |
| :--- | :--- |
| **Structured JSON** | Direct GIS and database import |
| **Excel-ready inventory table** | Absolute counts, confidence values and bank-side position |
| **Per-object register** | Track ID, pixel bounding box, and WGS84 coordinates |
| **Annotated frames** | Visual QA and verification |

---

## 🎯 Design Principle

The system is deliberately scoped as a **census tool, not an assessment tool**. It produces counts, positions and coordinates — not habitat scores or ecological grades.

> Interpretation stays with the hydromorphologist; the agent removes the manual counting burden and delivers auditable, repeatable, spatially explicit data.

---

## 🚀 Applications

- River restoration monitoring
- Large-wood recruitment studies
- Flood-risk and blockage screening
- Baseline surveys for WFD-aligned reporting
- Repeat-survey change detection

---

## 🏗️ How It Was Built

The system is built as an **agent-in-the-loop pipeline** rather than a standalone script, so detection, tracking and reporting all run behind a single controlled instruction set.

| Layer | Details |
| :--- | :--- |
| **🧩 Environment** | Developed in Google Antigravity, an agentic IDE, with the project folder explicitly scoped to the agent for bounded, reproducible file access. |
| **🧠 Reasoning layer** | Claude Code is integrated as an editor extension, orchestrating the analysis and enforcing the counts-only, no-redundancy constraints. |
| **👁️ Detection layer** | A YOLO MCP Server exposes object detection as a callable tool, keeping the vision model swappable without rewriting agent logic. |
| **📜 Instruction layer** | A persistent instructions file defines the class taxonomy, ByteTrack deduplication protocol, pixel-to-WGS84 geo-location method and output schemas — making every run structurally deterministic. |
| **⚙️ Workflow** | Survey media is referenced from the scoped folder; the agent detects, tracks, resolves unique objects, projects centroids to geographic coordinates, and exports the inventory for Excel and GIS. |

---

## 🛠️ Skills

**Core technical**

`Computer Vision` · `Object Detection (YOLOv8 / YOLOv11)` · `Multi-Object Tracking (ByteTrack)` · `Python` · `OpenCV` · `Machine Learning Pipelines`

**Geospatial**

`GIS / Geospatial Analysis` · `Photogrammetry` · `UAV / Drone Data Processing` · `Coordinate Reference Systems (WGS84, UTM)` · `Remote Sensing`

**AI systems engineering**

`Agentic AI Development` · `Model Context Protocol (MCP)` · `Prompt Engineering` · `Claude Code` · `Workflow Automation` · `Git / Version Control`

**Domain**

`Hydromorphology` · `Fluvial Geomorphology` · `River Habitat Survey` · `River Restoration Monitoring` · `Environmental Data Analysis`
