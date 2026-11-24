# SGLang development

- The goal is to become a regular upstream SGLang contributor, starting with KV-cache management and correctness, especially prefix reuse, slot ownership, and eviction. Start with small features, bug fixes with regression tests, targeted tests, or measurable performance improvements. Use Tiny SGLang as preparation and verify behavior in upstream SGLang.
- This checkout is the personal SGLang fork. Base upstream contribution branches on the official repository. Keep the SGLang environment separate from the llm_roadmap root uv project.

## Coding standards

- Treat every change as production code for upstream review. Follow SGLang's contribution guide, style, and tooling. Match the conventions of the code you are editing and preserve the contracts that existing callers rely on.
- Write the simplest complete implementation. Use precise names, direct control flow, and cohesive functions. Reuse existing code where it fits. Add abstractions only when a concrete requirement or real duplication justifies them. Keep the diff focused on the requested behavior.
- Verify assumptions against the implementation and its tests. Remove boilerplate, redundant comments, speculative fallback paths, and unused scaffolding. Keep comments that explain an invariant or a design decision the code alone cannot convey.
- Preserve existing docstrings when editing, moving, or refactoring code. If a docstring no longer matches the behavior, update it rather than removing it.
- For KV-cache changes, trace slot ownership and lifetime through allocation, sharing, release, and eviction. Make the relevant invariants clear in the code and verify that the change preserves them.
- Review the diff line by line. For every added or changed line, be able to explain why it belongs in the change and why its form fits the surrounding code. Simplify or remove lines without a clear purpose. Run the applicable upstream format, lint, and focused behavior checks. Cover real regressions with a targeted test where needed, and report any checks you could not run.

## Finding contribution opportunities

- Find SGLang contribution opportunities independently by tracing code and tests, probing invariants, or running small experiments. Do not use the open issue backlog to find work. Prioritize KV-cache correctness, then look for focused features, test gaps, and measurable performance fixes.
- Verify the finding against current upstream code with the smallest useful reproduction or benchmark. Check related pull requests by code path and behavior before implementing a fix.
- Report the expected and observed behavior, the revision and verification method, the likely scope, and any overlapping work.

## GPU development

- Run SGLang GPU tests, reproductions, and benchmarks over SSH in `/home/repos/sglang` on DevEnv using your SSH alias. Use the checkout's own `.venv`, separate from `llm_roadmap`.
- Check GPU availability with `nvidia-smi` before starting a run. Verify the checkout revision and record the model, runtime, and launch settings with the results. For performance work, record the workload and baseline, change one variable at a time, and check correctness before comparing timings.
