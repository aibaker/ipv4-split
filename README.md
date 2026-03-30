
This is a greenfield single-page application for CIDR subnet management. No existing system to integrate with. Target users are network engineers, DevOps engineers, and cloud architects who need to plan VPC subnet allocations.

## Goals / Non-Goals

**Goals:**
- Build an interactive SPA that visualizes CIDR blocks as a tree
- Allow recursive splitting of any CIDR block into equal smaller subnets (manual mode)
- Support smart allocation: auto-split based on requirements (e.g., "4×/25, 8×/26")
- Include AWS 3-tier preset for common VPC patterns
- Support blocking and unblocking subnets
- Support merging available subnets back to parent
- Support hierarchical labeling: main group (category) + subgroup (value)
  - Example: "AZ/AZ1", "Target/pod", "Custom/database"
  - Multiple hierarchical labels per subnet supported
- Support multiple view modes: tree, flat list, grouped by main group, nested (main group → subgroup)
- Export allocations in JSON, CSV, and Terraform HCL formats

**Non-Goals:**
- IPv6 support (v4 only for initial release)
- Backend persistence (state is ephemeral in browser)
- User authentication
- Collaborative features

## Decisions

1. **Framework: Vanilla JS with Vue.js 3 (CDN)**
   - Chosen over React: Smaller bundle, simpler setup without build tools
   - Vue 3 Composition API provides clean state management
   - Single HTML file deployment possible

2. **State Management: Vue reactive system**
   - Single source of truth for CIDR tree
   - Undo/redo capability via history stack

3. **CIDR Calculation: ipaddr.js library**
   - Reliable IPv4 CIDR manipulation
   - Handles edge cases (overlapping ranges, invalid inputs)

4. **UI: Tree visualization with collapsible nodes**
   - Clear hierarchy showing parent-child relationships
   - Visual distinction between available and blocked subnets

5. **Export Formats:**
   - JSON: Machine-readable for integration
   - CSV: Spreadsheet-friendly
   - Terraform HCL: Infrastructure-as-code ready

6. **Smart Allocation Algorithm:**
   - Parse requirement string (e.g., "4×/25, 8×/26") into structured request
   - Calculate total IPs required vs available
   - Use greedy approach: allocate largest subnets first
   - Offer partial allocation if exact fit impossible
   - Reuse existing child subnets when possible rather than reset

## Risks / Trade-offs

- **Risk**: Large CIDR blocks (e.g., /8) could create performance issues with thousands of nodes
  - **Mitigation**: Lazy rendering - only expand nodes when clicked
- **Risk**: Browser storage limits for large allocations
  - **Mitigation**: Offer export/import JSON for persistence
- **Trade-off**: No backend means no collaboration, but simplifies deployment
