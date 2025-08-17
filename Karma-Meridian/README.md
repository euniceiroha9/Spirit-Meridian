# Soul Lifecycle Management Smart Contract

## Overview

The Soul Lifecycle Management Smart Contract is an advanced blockchain system built for the Stacks network that enables users to create, manage, and evolve digital soul entities through various incarnation cycles. The contract provides a comprehensive framework for tracking karmic progression, interdimensional transitions, and spiritual relationships across multiple realms.

## Core Features

### Soul Entity Management
- **Entity Creation**: Generate unique digital soul entities with customizable metadata
- **Evolution System**: Transform souls through different incarnation forms with karma requirements
- **State Management**: Track entities through active, dormant, transitioning, and contract-bound states
- **Ownership Transfer**: Secure transfer of soul entities between users

### Karma System
- **Karma Accumulation**: Track positive and negative karma points for each entity
- **Transaction Ledger**: Comprehensive logging of all karma changes with reasons and validators
- **Evolution Requirements**: Different incarnation forms require varying karma thresholds
- **Administrative Controls**: Admin functions for karma adjustments when necessary

### Incarnation Forms
The system supports five distinct incarnation types:
1. **Humanoid** (Form 1) - Basic incarnation form, starting point for new entities
2. **Creature** (Form 2) - Animal-like manifestations
3. **Botanical** (Form 3) - Plant-based life forms
4. **Ethereal** (Form 4) - Spiritual manifestations (highest karma requirement)
5. **Synthetic** (Form 5) - Artificial life forms (moderate karma requirement)

### Dimensional Realms
Souls can exist and transition between four dimensional planes:
1. **Material Realm** - Physical world manifestation
2. **Virtual Realm** - Digital existence plane
3. **Astral Plane** - Spiritual dimension
4. **Void Space** - Empty dimensional space

## Contract Architecture

### Data Structures

#### Soul Entity Registry
Primary storage for soul entity information including:
- Owner address and creation timestamp
- Current incarnation form and lifetime count
- Accumulated karma balance and entity state
- Active dimensional realm and spiritual essence power
- Contract binding status and descriptive metadata

#### Incarnation History
Tracks the complete lifecycle of each incarnation:
- Form type and timestamp records
- Karma accumulated during each incarnation
- Dimensional realm location
- Milestone achievements and experiences

#### Karma Transaction Ledger
Complete audit trail of karma changes:
- Amount changed and reason description
- Block height and validator information
- Sequential transaction tracking per entity

#### Relationship Mapping
Inter-soul relationship tracking:
- Primary and secondary entity connections
- Relationship classification and bond strength
- Establishment timestamps

## Public Functions

### Core Operations

#### `create-soul-entity`
```clarity
(create-soul-entity (metadata (string-ascii 256)))
```
Creates a new soul entity with the specified metadata. Returns the unique entity identifier.

#### `evolve-soul-entity`
```clarity
(evolve-soul-entity (entity-id uint) (target-incarnation-form uint) (destination-realm uint))
```
Evolves a soul entity to a new incarnation form and dimensional realm. Requires sufficient karma and respects cooldown periods.

#### `enhance-entity-karma`
```clarity
(enhance-entity-karma (entity-id uint) (karma-amount int) (enhancement-reason (string-ascii 128)))
```
Adds karma to a soul entity with a descriptive reason for the enhancement.

#### `transfer-entity-ownership`
```clarity
(transfer-entity-ownership (entity-id uint) (new-owner-address principal))
```
Transfers ownership of a soul entity to a new address. Entity must not be contract-bound.

### Contract Binding Functions

#### `bind-entity-to-contract`
```clarity
(bind-entity-to-contract (entity-id uint) (target-contract-address principal))
```
Binds a soul entity to an external contract, changing its state to contract-bound.

#### `release-entity-from-contract`
```clarity
(release-entity-from-contract (entity-id uint))
```
Releases a soul entity from contract binding, returning it to active state.

### Relationship Management

#### `establish-entity-relationship`
```clarity
(establish-entity-relationship (primary-entity-id uint) (secondary-entity-id uint) (relationship-type uint))
```
Creates a relationship between two soul entities with specified classification.

## Read-Only Functions

### Query Functions

#### `get-soul-entity-details`
Returns complete information about a specific soul entity.

#### `get-incarnation-history-details`
Retrieves detailed history for a specific incarnation cycle.

#### `get-karma-transaction-details`
Returns information about a specific karma transaction.

#### `check-evolution-eligibility`
Checks if an entity is eligible for evolution to a target form, including karma requirements and cooldown status.

#### `get-system-statistics`
Returns overall system statistics including total entities created and current configuration.

## Evolution Requirements

### Karma Thresholds
- **Standard Forms** (Humanoid, Creature, Botanical): 100 karma points
- **Synthetic Form**: 200 karma points (2x multiplier)
- **Ethereal Form**: 300 karma points (3x multiplier)

### Cooldown Period
- **Evolution Cooldown**: 144 blocks (approximately 24 hours)
- Prevents rapid successive evolutions

### Prerequisites
- Sufficient karma balance for target incarnation
- Cooldown period completion
- Entity must not be contract-bound
- Valid incarnation form and dimensional realm

## Administrative Features

### System Maintenance
- Toggle maintenance mode to pause contract operations
- Update evolution processing fees
- Administrative karma adjustments with audit trail

### Event Logging
Comprehensive event tracking system that logs:
- Entity creation and evolution events
- Karma enhancements and adjustments
- Ownership transfers and contract bindings
- Relationship establishments

## Error Handling

The contract implements comprehensive error handling with specific error codes:

- `ERR-UNAUTHORIZED-ACCESS` (100): Permission denied
- `ERR-SOUL-ENTITY-NOT-FOUND` (101): Entity doesn't exist
- `ERR-ENTITY-ALREADY-ACTIVE` (102): Entity state conflict
- `ERR-INSUFFICIENT-KARMA-BALANCE` (103): Not enough karma
- `ERR-INVALID-INCARNATION-TYPE` (104): Invalid form specified
- `ERR-EVOLUTION-COOLDOWN-ACTIVE` (105): Evolution on cooldown
- `ERR-INVALID-AMOUNT-PROVIDED` (106): Invalid numeric value
- `ERR-SOUL-ENTITY-IS-BOUND` (107): Entity is contract-bound
- `ERR-INVALID-REALM-SPECIFIED` (108): Invalid dimensional realm
- `ERR-INVALID-INPUT-PARAMETERS` (109): General input validation error

## Security Features

### Access Control
- Owner-only operations for entity management
- Administrator-only functions for system configuration
- Contract binding prevents unauthorized transfers

### Validation
- Comprehensive input validation on all parameters
- Entity existence checks before operations
- State verification for valid transitions

### Audit Trail
- Complete transaction history for all karma changes
- Event logging for all major operations
- Immutable record of entity lifecycle

## Usage Examples

### Creating a Soul Entity
```clarity
(contract-call? .soul-lifecycle create-soul-entity "My first soul entity")
```

### Evolving to Ethereal Form
```clarity
;; Requires 300 karma and completed cooldown
(contract-call? .soul-lifecycle evolve-soul-entity u1 u4 u3)
```

### Adding Karma
```clarity
(contract-call? .soul-lifecycle enhance-entity-karma u1 50 "Completed spiritual quest")
```

### Checking Evolution Eligibility
```clarity
(contract-call? .soul-lifecycle check-evolution-eligibility u1 u4)
```

## Integration Guidelines

### External Contract Integration
- Use binding functions to integrate soul entities with other contracts
- Implement proper release mechanisms in external contracts
- Respect entity states and karma requirements

### Event Monitoring
- Monitor system events for entity lifecycle changes
- Track karma transactions for analytics
- Use relationship data for social features