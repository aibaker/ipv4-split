## ADDED Requirements

### Requirement: Export subnet allocations
The system SHALL allow users to export subnet allocations in multiple formats.

#### Scenario: Export as JSON
- **WHEN** user clicks "Export" and selects JSON format
- **THEN** system downloads a JSON file with all subnet details (CIDR, status, label)

#### Scenario: Export as CSV
- **WHEN** user clicks "Export" and selects CSV format
- **THEN** system downloads a CSV file with columns: CIDR, Start IP, End IP, Status, Label

#### Scenario: Export as Terraform HCL
- **WHEN** user clicks "Export" and selects Terraform HCL format
- **THEN** system downloads an HCL file with aws_vpc_subnet resource blocks

#### Scenario: Export only unblocked subnets
- **WHEN** user enables "Export available only" option
- **THEN** exported data excludes blocked subnets

#### Scenario: Export includes labels
- **WHEN** user exports subnets with labels assigned
- **THEN** exported data includes all labels (AZ, target, custom)
