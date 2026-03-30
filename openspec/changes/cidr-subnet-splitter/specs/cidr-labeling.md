## ADDED Requirements

### Requirement: Hierarchical subnet labeling
The system SHALL support hierarchical labels with main group (category) and subgroup (value).

#### Scenario: Assign main group and subgroup
- **WHEN** user selects a subnet and assigns "AZ" group with "AZ1" subgroup
- **THEN** system stores the hierarchical label for that subnet

#### Scenario: Predefined main groups
- **WHEN** user needs to label a subnet
- **THEN** system provides predefined main groups: "AZ", "Target", "Custom"

#### Scenario: Predefined subgroups
- **WHEN** user selects "AZ" main group
- **THEN** system shows subgroups: AZ1, AZ2, AZ3, AZ4
- **WHEN** user selects "Target" main group
- **THEN** system shows subgroups: pod, node, service

#### Scenario: Create custom subgroup
- **WHEN** user creates a new subgroup under any main group (e.g., "database" under "Custom")
- **THEN** system saves it for reuse across subnets

#### Scenario: Multiple hierarchical labels per subnet
- **WHEN** user assigns both "AZ/AZ1" and "Target/pod" to a subnet
- **THEN** system displays both hierarchical labels for that subnet

#### Scenario: Remove hierarchical label
- **WHEN** user removes a label from a subnet
- **THEN** system removes both the main group and subgroup association

### Requirement: View modes with hierarchical labels
The system SHALL allow users to switch between different visualization modes including hierarchical grouping.

#### Scenario: Tree view
- **WHEN** user selects tree view
- **THEN** system displays CIDR hierarchy with parent-child relationships

#### Scenario: Flat list view
- **WHEN** user selects flat list view
- **THEN** system displays all subnets in a single-level list sorted by IP range

#### Scenario: Group by main group
- **WHEN** user selects "Group by AZ" or "Group by Target" or "Group by Custom"
- **THEN** system displays subnets organized under their subgroup values
- **Example** for Group by AZ:
  - AZ1
    - 10.0.0.0/24
  - AZ2
    - 10.0.1.0/24
  - AZ3
    - 10.0.2.0/24
  - AZ4
    - 10.0.3.0/24

#### Scenario: Nested grouping view with main and sub group selectors
- **WHEN** user selects nested grouping view
- **THEN** system presents two dropdowns: "Main Group" and "Sub Group"
- **AND** both dropdowns contain: AZ, Target, and all Custom labels
- **AND** the Sub Group dropdown excludes whatever is selected in Main Group

#### Scenario: Nested grouping displays 2-level hierarchy
- **WHEN** user selects Main Group=AZ and Sub Group=Target
- **THEN** system displays hierarchy:
  - AZ
    - AZ1
      - pod
        - 10.0.0.0/25
      - node
        - 10.0.0.128/26
      - service
        - 10.0.0.192/26
    - AZ2
      - pod
        - 10.0.1.0/25
      ...

- **WHEN** user selects Main Group=Target and Sub Group=AZ
- **THEN** system displays hierarchy:
  - Target
    - pod
      - AZ1: 10.0.0.0/25
      - AZ2: 10.0.1.0/25
      - AZ3: 10.0.2.0/25
      - AZ4: 10.0.3.0/25
    - node
      - ...

#### Scenario: Unlabeled subnets in grouped views
- **WHEN** user views grouped by a label but some subnets have no label for that group
- **THEN** system displays those subnets under "Unlabeled" section
