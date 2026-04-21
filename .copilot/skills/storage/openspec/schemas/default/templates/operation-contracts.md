# Operation Contracts - UC{{#}} {{use-case.name}}

- [Back to Use Case](../use-cases/UC{{#}}%20{{use-case.name}}.md)
- [back to SSD](../SSDs/SSD%20UC{{#}}%20{{use-case.name}}.md)

## Scenario

- Use case: `UC{{#}} {{use-case.name}}`
- Scenario: `<Main Success Scenario | Extension X>`

{for operation in system-operations}
## Operation Contract: {{operation.name}}

### Operation

- `{{operation.signature}}`

### Cross References

- Use case step(s): `{{operation.use-case-steps}}`
- SSD message(s): `{{operation.ssd-messages}}`

### Preconditions (optional)

- {{operation.precondition-1}}

### Postconditions

- {{operation.postcondition-1}}
- {{operation.postcondition-2}}
- {{operation.postcondition-3}}

{end operation}

## Validation Checklist

- [ ] Operations come from SSD system events
- [ ] Single scenario scope
- [ ] Postconditions use Domain Model terms
- [ ] State changes are explicit (create/delete/link/update)
- [ ] Traceability to Use Case and SSD is explicit
