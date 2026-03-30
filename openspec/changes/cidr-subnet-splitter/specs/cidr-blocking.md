## ADDED Requirements

### Requirement: Subnet blocking
The system SHALL allow users to mark subnets as blocked/reserved to exclude them from allocation.

#### Scenario: Block a subnet
- **WHEN** user selects a subnet and clicks "Block"
- **THEN** system marks the subnet as blocked with visual indicator (red)

#### Scenario: Block subnet with children
- **WHEN** user blocks a subnet that has child subnets
- **THEN** system blocks all descendant subnets recursively

#### Scenario: Unblock a subnet
- **WHEN** user selects a blocked subnet and clicks "Unblock"
- **THEN** system removes the blocked status

#### Scenario: Prevent splitting blocked subnet
- **WHEN** user attempts to split a blocked subnet
- **THEN** system displays error "Cannot split blocked subnet"
