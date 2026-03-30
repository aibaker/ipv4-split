## ADDED Requirements

### Requirement: Recursive CIDR splitting
The system SHALL allow users to split any CIDR block into equal smaller subnets by increasing the prefix length by 1.

#### Scenario: Split a CIDR block
- **WHEN** user selects a CIDR block and clicks "Split"
- **THEN** system divides the block into 2 equal subnets (prefix length increases by 1)

#### Scenario: Recursive splitting
- **WHEN** user splits an already-split subnet again
- **THEN** system creates 2 children, each half the size of the parent

#### Scenario: Prevent over-splitting
- **WHEN** user attempts to split a /30 or smaller CIDR
- **THEN** system displays error "Cannot split beyond /31"

#### Scenario: Split blocked subnet
- **WHEN** user attempts to split a blocked subnet
- **THEN** system displays error "Cannot split blocked subnet"
