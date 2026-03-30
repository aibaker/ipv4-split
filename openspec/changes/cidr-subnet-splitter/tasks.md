## 1. Project Setup

- [ ] 1.1 Create index.html with Vue.js 3 CDN import
- [ ] 1.2 Add ipaddr.js library for CIDR calculations
- [ ] 1.3 Set up basic HTML structure and CSS styling
- [ ] 1.4 Add CIDR input validation (accept /20 to /32, reject larger)

## 2. Core Data Model

- [ ] 2.1 Implement CIDRNode class with ip, prefix, children, blocked properties
- [ ] 2.2 Create root state management with Vue reactive system
- [ ] 2.3 Add undo/redo history stack

## 3. CIDR Tree Visualization

- [ ] 3.1 Implement recursive tree rendering component
- [ ] 3.2 Add expand/collapse functionality
- [ ] 3.3 Style nodes based on status (available/blocked/partial)

## 4. CIDR Splitting

- [ ] 4.1 Implement split function (divide CIDR into 2 subnets)
- [ ] 4.2 Add recursive split validation (/30 limit)
- [ ] 4.3 Add blocked subnet validation
- [ ] 4.4 Wire up split button UI

## 5. CIDR Blocking

- [ ] 5.1 Implement block/unblock toggle function
- [ ] 5.2 Add recursive blocking for child nodes
- [ ] 5.3 Wire up block button UI

## 6. CIDR Merging

- [ ] 6.1 Implement merge function for sibling subnets
- [ ] 6.2 Add validation (check if siblings are available and have no children)
- [ ] 6.3 Implement "Merge All" recursive function
- [ ] 6.4 Wire up merge button UI

## 7. Smart Allocation

- [ ] 7.1 Implement requirement parser (e.g., "4×/25, 8×/26")
- [ ] 7.2 Add validation: check if requirements fit in available space
- [ ] 7.3 Implement auto-split algorithm to satisfy requirements
- [ ] 7.4 Add partial allocation fallback when full fit impossible
- [ ] 7.5 Implement AWS 3-tier preset (/22 → 12 subnets)
- [ ] 7.6 Wire up smart allocation UI panel
- [ ] 7.7 Smart allocation reuses existing splits where possible

## 8. Subnet Labeling

- [ ] 8.1 Extend CIDRNode data model to include labels array
- [ ] 8.2 Add predefined labels: AZ1-AZ4, pod, node, service
- [ ] 8.3 Add custom label creation and storage
- [ ] 8.4 Add/remove label UI on subnet selection
- [ ] 8.5 Support multiple labels per subnet

## 9. View Modes

- [ ] 9.1 Implement flat list view (all subnets sorted by IP)
- [ ] 9.2 Implement tree view (existing, rename to distinguish)
- [ ] 9.3 Implement group by AZ view
- [ ] 9.4 Implement group by target view
- [ ] 9.5 Implement group by custom label view
- [ ] 9.6 Implement nested grouping view (main group → subgroup hierarchy with two dropdowns)
- [ ] 9.7 Add nested grouping main/sub group dropdowns (exclude main from sub options)
- [ ] 9.8 Handle unlabeled subnets in grouped views
- [ ] 9.9 Add view mode switcher UI (tabs or dropdown)

## 10. Export Functionality

- [ ] 10.1 Implement JSON export
- [ ] 10.2 Implement CSV export
- [ ] 10.3 Implement Terraform HCL export
- [ ] 10.4 Add "available only" filter option
- [ ] 10.5 Include labels in export output
- [ ] 10.6 Wire up export dropdown UI

## 11. Polish & Testing

- [ ] 11.1 Add input validation for CIDR format
- [ ] 11.2 Test with example: /22 split into 4 AZs with 3 subnets each
- [ ] 11.3 Add keyboard shortcuts
- [ ] 11.4 Responsive design for mobile
