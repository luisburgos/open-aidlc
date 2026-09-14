# Items

## ADDED Requirements

### Requirement: An item carries a done state

Every item is either done or not done. An item is not done when it is written.

#### Scenario: A new item starts not done

- **WHEN** an item is written
- **THEN** the item is not done

#### Scenario: Marking an item done

- **WHEN** a person marks a not-done item as done
- **THEN** the item is done

#### Scenario: Unmarking an item

- **WHEN** a person marks a done item as not done
- **THEN** the item is not done

#### Scenario: Marking an item that is already done

- **WHEN** a person marks a done item as done
- **THEN** the item is done
- **AND** nothing else about the item changes
