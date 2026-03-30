## ADDED Requirements

### Requirement: Subnet merging
The system SHALL allow users to merge adjacent available subnets back into their parent CIDR block.

#### Scenario: Merge two sibling subnets
- **WHEN** user selects two sibling subnets (same parent, both available) and clicks "Merge"
- **THEN** system combines them into their parent CIDR block

#### Scenario: Merge fails if any subnet is blocked
- **WHEN** user attempts to merge sibling subnets where at least one is blocked
- **THEN** system displays error "Cannot merge: one or more subnets are blocked"

#### Scenario: Merge fails if any subnet is split
- **WHEN** user attempts to merge sibling subnets where at least one has children
- **THEN** system displays error "Cannot merge: one or more subnets have children"

#### Scenario: Recursive merge to root
- **WHEN** user clicks "Merge All" on a parent with available children
- **THEN** system recursively merges all possible sibling pairs up to the root
