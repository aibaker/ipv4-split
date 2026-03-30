## Why

Network engineers and DevOps teams frequently need to divide large CIDR blocks into smaller subnets for cloud infrastructure (AWS VPCs, Azure VNETs, Kubernetes clusters). Doing this manually is error-prone and time-consuming. A visual, interactive tool would eliminate calculation errors and speed up network planning.

## What Changes

- New single-page web application for CIDR subnet splitting
- Interactive CIDR visualization tree
- Recursive subnet division (split any subnet into smaller blocks)
- Subnet blocking (mark subnets as reserved/unavailable)
- Subnet merging (combine adjacent free subnets back into larger blocks)
- Export capability for subnet allocations

## Capabilities

### New Capabilities
- **cidr-visualization**: Interactive tree view showing CIDR hierarchy with expandable/collapsible nodes
- **cidr-splitting**: Split any CIDR block into equal smaller subnets (e.g., /22 → 4x /24)
- **cidr-blocking**: Mark subnets as blocked/reserved so they're excluded from allocation
- **cidr-merging**: Combine adjacent available subnets back into their parent CIDR
- **cidr-export**: Export subnet allocations in practical formats (JSON, CSV, Terraform HCL)
- **cidr-smart-allocation**: Auto-split CIDR based on user requirements (e.g., "4×/25, 8×/26") with AWS 3-tier preset
- **cidr-labeling**: Hierarchical labels (main group → subgroup, e.g., AZ/AZ1, Target/pod) with view modes (tree/flat/grouped/nested)

## Impact

- New frontend-only SPA (no backend required)
- Pure client-side CIDR calculations using JavaScript
- Can be deployed as static files to any web server or CDN
