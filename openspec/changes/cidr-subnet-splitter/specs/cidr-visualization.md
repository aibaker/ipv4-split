## ADDED Requirements

### Requirement: CIDR tree visualization
The system SHALL display CIDR blocks in an interactive tree structure showing parent-child hierarchy with expandable/collapsible nodes.

#### Scenario: Initial CIDR display
- **WHEN** user enters a valid CIDR block (e.g., "10.0.0.0/22")
- **THEN** system displays the CIDR as the root node with its IP range and prefix length

#### Scenario: Reject CIDR larger than /20
- **WHEN** user enters a CIDR with prefix /19 or larger (e.g., "10.0.0.0/16")
- **THEN** system displays error "Maximum CIDR is /20"

#### Scenario: Expand node to see children
- **WHEN** user clicks the expand icon on a CIDR node
- **THEN** system reveals child subnet nodes (if any exist)

#### Scenario: Collapse node to hide children
- **WHEN** user clicks the collapse icon on a CIDR node
- **THEN** system hides all descendant nodes

#### Scenario: Visual distinction by status
- **WHEN** a subnet is displayed
- **THEN** system shows visual indicator distinguishing available (green), blocked (red), and partially allocated (yellow) subnets
