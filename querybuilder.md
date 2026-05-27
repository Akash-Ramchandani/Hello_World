# QueryBuilder Wiring Executor (CONCERN=QUERYBUILDER_WIRING)

## Trigger (MUST be evidence-based)
Apply ONLY when Whole-File Concern/Evidence Table shows Dominant Symbols contain:
- QueryBuilder, Query, SearchResult, Hit

## Hard Constraints
- Modify ONLY tests under `core/src/test/java`
- MUST NOT modify production code
- No inference; use only code-visible evidence and existing assertions

## Actions (MUST)
1) Collapse deep chains:
   - Replace repeated QueryBuilder→Query→SearchResult→Hit mocking chains with a minimal reusable stub helper if assertions prove identical behavior.
2) Make “Hit” data explicit:
   - Prefer small deterministic collections for hits (size 0/1/2) rather than many mocked Hit objects, only if tests assert on count/paths.
3) Parameterize identical shapes:
   - If multiple tests vary only by (limit/offset/query string), convert to @ParameterizedTest when assertions are identical.

## Prohibitions
- Do NOT create new query semantics or inferred “business rules”
- Do NOT broaden fixtures or add AEM context just to satisfy QueryBuilder types

## Output
- List impacted tests (exact names)
- Show old vs new mocking surface area (identifiers only)
- Applied/Blocked per step with evidence pointers
