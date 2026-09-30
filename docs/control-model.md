# Control Model

## Objective

The architecture is designed to balance two competing failure modes:

- **too little autonomy**, where humans become unnecessary bottlenecks; and
- **too much autonomy**, where agents infer authority from capability.

The control model treats authority as explicit configuration.

## Decision Test

Before an agent takes an action, the system should be able to answer:

1. Is this action inside the role's assigned responsibility?
2. Is the required information available and sufficiently current?
3. Is the action reversible or routine?
4. Does it create an external commitment?
5. Does policy require human approval?
6. Will the result produce an observable completion signal?

If responsibility or authority is missing, the correct behavior is routing or escalation—not improvising permission.

## Example Authority Matrix

| Action | Operations | Coordinator | Specialist | Research | Human |
| --- | --- | --- | --- | --- | --- |
| Classify incoming work | Execute | Observe | Observe | Observe | Override |
| Reprioritize within policy | Recommend | Execute | Recommend | Recommend | Override |
| Perform routine domain task | Route | Coordinate | Execute | N/A | Override |
| Research alternatives | Request | Request | Request | Execute | Request |
| Change standing authority | No | No | No | No | Execute |
| Make material external commitment | No | No | Approval-gated | No | Execute |

This is illustrative rather than a production permission table.

## Control Invariant

**No component can grant itself additional authority.**

Authority changes are explicit governance events. Learning, better reasoning, repeated success, or prior approval can improve execution quality but do not change permission boundaries.
