# Development Standards

## Code Quality Requirements

### Type Hints & Documentation
- Use comprehensive type hints (generics, unions, protocols)
- Docstrings explain "why" more than "what", include usage examples for public APIs
- Follow semantic naming from coding_style.md (include units, be specific)

### Error Handling
- Provide actionable error messages: what failed, why, how to fix
- Fail fast and report problems clearly
- Use appropriate exception types

### Logging & Observability  
- Import from `centralized_logging` module
- Use structured logging with structlog
- Log at appropriate levels for debugging
- Properly instrument code to assist debugging and monitoring with Sentry
- Include metrics and tracing alongside logging for system visibility

### Testing Standards
- Small, targeted test cases
- Creative test data but semantic variable names
- Separate unit tests (`tests/unit/`) from integration tests (`tests/integration/`)
- No complex logic in tests

## Quality Gates
Before creating PR, ensure:
- [ ] All TODO comments follow format from coding_style.md
- [ ] No FIXME comments remain
- [ ] `uv run mypy .` passes
- [ ] `uv run ruff check .` passes  
- [ ] `uv run pytest tests/` passes
- [ ] Pre-commit hooks pass
- [ ] Documentation updated for public interface changes

## Branch & Commit Standards
- Branch naming: `feature/YYYY-MM-DD-brief-description` or `fix/YYYY-MM-DD-brief-description`
- Conventional commits format
- Atomic commits (single logical change)

## Security
  - Sanitize all inputs
  - Never hardcode secrets or credentials
  - Use environment variables for configuration

## Resource Management
- **Memory Usage**: Be mindful of memory allocation patterns in data processing
- **I/O Operations**: Use async patterns where appropriate for I/O-bound operations
- **Database Queries**: Optimize database interactions and avoid N+1 query problems
- **External APIs**: Implement proper retry logic and rate limiting for external service calls