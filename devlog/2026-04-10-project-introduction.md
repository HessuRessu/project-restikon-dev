# Restikon Reborn 


## Project Introduction

Restikon Reborn is a large-scale village builder / colony simulation project, which focuses on individual villagers rather than abstract systems. Development happens in spare time, using Unity for the runtime and Blender for most of the art and animation work.

At its core, the project explores a simple idea: a settlement exists because its people act. **Villagers** gather resources, carry them through the world, store them, and use them to build and survive. If those chains break - if food is not delivered, if firewood is not hauled, if storage fills up - then the settlement collapses. Nothing is implied; systems only work when agents make them work and the player is responsible for keeping the system together.

![Agent behaviour](../media/gui/2026-04-10-GUI-1.png)

![Spring harvesting closeup](../media/closeup/2026-04-10-Spring-Closeup-2.png)

**The simulation** is intentionally systemic. Resources are not just numbers but things that must be moved, fabricated, refined, traded and consumed. Needs such as hunger and warmth are not background stats but pressures that shape behavior. Logistics, storage, and environment define what is possible at any given moment, and expansion emerges from those constraints rather than from scripted progression.

![Fall closeup](../media/closeup/2026-04-10-Fall-Closeup-1.png)

**Expansion** is crucial, territories (or biomes) are different. For example, while one territory is fertile and ideal for producing food, other offers valuable minerals yet lacks any chance of producing food. This presents a challenge and a possibility - logistics and storage must be orchestrated to support settlement expansion. The settlement is not just a single village but a network of territorial hubs connected via logistics and need-based resource exchange.

![Builder menu](../media/gui/2026-04-10-GUI-2.png)

**Seasons** play a central role in the game. They are not just visual changes, but shifts in how the village operates. Availability of resources, movement patterns, and survival pressure evolve over time, forcing the settlement to adapt or fail.

![Seasons](../media/seasons/2026-04-10-Seasons-1.png)

![Winter closeup](../media/closeup/2026-04-10-Winter-Closeup-1.png)

This repository serves as a record of that process: progress, experiments, and the occasional problem worth documenting. The project itself is still in an early stage and not publicly available. For now, this is a place to capture how the simulation takes shape over time.

The broader direction is still forming. The setting leans toward grounded, somewhat imperial realism with light steampunk influences, but the focus remains firmly on systems first. Visual polish and presentation will come later—once the simulation itself is worth showing.

## Tech Stack

The project is built on Unity, but most core systems are custom-built to support large-scale simulation.

- **GPU Instancing & Rendering Pipeline**  
  Custom asset-centric rendering pipeline with compute shader driven frustum culling, Hi-Z occlusion culling, GPU-based LOD selection, and support for large numbers of dynamic instances.

- **Vertex Animation Textures (VAT)**  
  GPU-driven animation system allowing thousands of animated agents without CPU overhead.

- **Burst-Based Simulation Pipeline**  
  Job-based simulation using Unity Burst and NativeCollections, designed to scale to large agent counts with minimal CPU cost.

- **Hierarchical Pathfinding (HPA\*)**  
  Multi-level navigation system optimized for large worlds, supporting agent-based traversal with different movement constraints. With runtime modification support.

- **Agent-Centric Task System**  
  Custom task pipeline where agents operate through dynamic task assignment (gathering, hauling, building), rather than scripted behavior.

- **Logistics & Storage System**  
  Resource flow is fully simulated: items must be physically transported, stored, and retrieved, forming real supply chains.

- **World & Biome System**  
  Environment-driven constraints (resource distribution, terrain) affecting expansion and survival.

- **Control texture based terrain shading**  
  Custom terrain mesh shading with compute shader based support to modify terrain visuals efficiently runtime.

- **Delta / Fixed frame phasing**
  To enable smooth simulation and separation of rendering, the project uses custom Delta / Fixed frame phasing with extendable behaviour model.

- **Networking (In Progress)**  
  Early multiplayer support with synchronized simulation state and bandwidth-optimized updates.