# AI-Powered River Feature Inventory Agent — Drone-Based Hydromorphological Mapping (YOLO + ByteTrack)

## Short overview

An agentic AI system that turns drone imagery and video of river corridors into a deduplicated, geo-referenced inventory of instream wood. Built with YOLO object detection and ByteTrack multi-object tracking inside an agentic IDE workflow, it outputs Excel- and GIS-ready records with WGS84 coordinates for every detected feature — counts, not scores.

## Full overview

Traditional river habitat surveys rely on manual walkover mapping — slow, subjective, and difficult to repeat consistently across long reaches. I am developing an AI agent that converts drone imagery and video of river corridors into a precise, quantitative inventory of channel features.

The agent uses a YOLO detection backbone paired with ByteTrack multi-object tracking, so every feature is assigned a persistent track ID across frames. This eliminates the double-counting problem that makes frame-by-frame detection unusable for inventory work: a single log jam appearing in 200 frames is counted once, not 200 times.

Each detection is then geo-referenced. Using UAV telemetry (GNSS position, altitude above ground, gimbal orientation) and camera intrinsics, pixel coordinates are converted to real-world WGS84 latitude/longitude, giving every logged feature a mappable location rather than just a bounding box.

## Feature classes detected

- Fallen trees / instream wood (already in or across the channel)
- Leaning trees (early-warning indicator for future recruitment)
- Large woody debris and log jams
- Wood stumps

## Outputs

- Structured JSON for direct GIS and database import
- An Excel-ready inventory table with absolute counts, confidence values and bank-side position
- A per-object register with track ID, pixel bounding box, and WGS84 coordinates
- Annotated frames for visual QA and verification

## Design principle

The system is deliberately scoped as a census tool, not an assessment tool. It produces counts, positions and coordinates — not habitat scores or ecological grades. Interpretation stays with the hydromorphologist; the agent removes the manual counting burden and delivers auditable, repeatable, spatially explicit data.

## Applications

River restoration monitoring · large-wood recruitment studies · flood-risk and blockage screening · baseline surveys for WFD-aligned reporting · repeat-survey change detection

## How it was built

The system is built as an agent-in-the-loop pipeline rather than a standalone script, so detection, tracking and reporting all run behind a single controlled instruction set.

- **Environment**: Developed in Google Antigravity, an agentic IDE, with the project folder explicitly scoped to the agent for bounded, reproducible file access.
- **Reasoning layer**: Claude Code is integrated as an editor extension, orchestrating the analysis and enforcing the counts-only, no-redundancy constraints.
- **Detection layer**: A YOLO MCP Server exposes object detection as a callable tool, keeping the vision model swappable without rewriting agent logic.
- **Instruction layer**: A persistent instructions file defines the class taxonomy, ByteTrack deduplication protocol, pixel-to-WGS84 geo-location method and output schemas — making every run structurally deterministic.
- **Workflow**: Survey media is referenced from the scoped folder; the agent detects, tracks, resolves unique objects, projects centroids to geographic coordinates, and exports the inventory for Excel and GIS.

## Skills

**Core technical**
- Computer Vision
- Object Detection (YOLOv8 / YOLOv11)
- Multi-Object Tracking (ByteTrack)
- Python
- OpenCV
- Machine Learning Pipelines

**Geospatial**
- GIS / Geospatial Analysis
- Photogrammetry
- UAV / Drone Data Processing
- Coordinate Reference Systems (WGS84, UTM)
- Remote Sensing

**AI systems engineering**
- Agentic AI Development
- Model Context Protocol (MCP)
- Prompt Engineering
- Claude Code
- Workflow Automation
- Git / Version Control

**Domain**
- Hydromorphology
- Fluvial Geomorphology
- River Habitat Survey
- River Restoration Monitoring
- Environmental Data Analysis
