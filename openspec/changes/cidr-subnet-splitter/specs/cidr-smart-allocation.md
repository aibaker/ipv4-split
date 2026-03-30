## ADDED Requirements

### Requirement: Smart CIDR allocation
The system SHALL allow users to specify subnet requirements and automatically calculate the optimal split.

#### Scenario: Allocate by count and prefix
- **WHEN** user enters allocation requirements (e.g., "4×/25, 8×/26") and clicks "Allocate"
- **THEN** system validates requirements can fit within available space and performs splits automatically

#### Scenario: Over-allocation rejected
- **WHEN** user requests more IP space than available in the CIDR
- **THEN** system displays error showing required vs available IPs

#### Scenario: Manual mode fallback
- **WHEN** smart allocation cannot satisfy requirements (e.g., conflicting sizes)
- **THEN** system offers to perform partial allocation and leaves remainder for manual splitting

#### Scenario: Smart allocation uses existing splits
- **WHEN** user runs smart allocation on partially-split CIDR
- **THEN** system reuses existing child subnets where possible rather than resetting

#### Scenario: Preset AWS 3-tier template
- **WHEN** user selects "AWS 3-tier" preset for a /22
- **THEN** system allocates: 4 AZs × (/25 pod + /26 node + /26 service) = 12 subnets
