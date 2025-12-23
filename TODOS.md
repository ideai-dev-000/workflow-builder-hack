# TODOs

## Session Management Improvements

### High Priority

- [ ] **Centralized Session State Management**
  - Create a single source of truth for "is session ready?" state
  - All components should check this before making API calls
  - Prevent race conditions from multiple components checking session independently

- [ ] **Session Ready Flag**
  - Track when session is actually usable (not just loading)
  - Components wait for session to be ready before making API calls
  - Add retry logic if session creation fails

- [ ] **Graceful Degradation for Auth Errors**
  - Handle "not logged in" as a normal state, not an error
  - Distinguish between "not logged in" (expected) vs "error" (unexpected)
  - Don't throw errors for expected auth states

- [ ] **Fix Anonymous Session Creation**
  - Ensure anonymous sessions are fully established before use
  - Add proper waiting/retry mechanism
  - Handle failures gracefully with fallback

### Medium Priority

- [ ] **Client/Server Session Sync**
  - Fix timing issues between client-side session checks and server-side cookie validation
  - Ensure hydration doesn't cause session mismatches
  - Better coordination between `NEXT_PUBLIC_APP_MODE` and `APP_MODE`

- [ ] **API Call Coordination**
  - Components should wait for session to be ready before API calls
  - Add session-ready check to all API call sites
  - Prevent API calls on mount before session is established

- [ ] **Cookie Timing Issues**
  - Fix Better Auth cookie timing with Next.js SSR/hydration
  - Ensure cookies are set immediately after sign-in
  - Handle cookie propagation delays

### Low Priority

- [ ] **Session State Debugging**
  - Add better logging for session state transitions
  - Track session creation/ready states for debugging
  - Monitor session-related errors

- [ ] **Session Retry Logic**
  - If session creation fails, retry with exponential backoff
  - Show user-friendly messages if session can't be created
  - Fallback to manual sign-in if anonymous session fails

## Mode System Enhancements

- [ ] **Complete Architecture Mode**
  - Implement all 10 architecture diagram shapes
  - Add custom node components for each shape
  - Create architecture-specific code generation

- [ ] **Mode-Specific Code Generation**
  - Different code generation for workflow vs architecture mode
  - Architecture mode: Generate Mermaid/PlantUML/SVG diagrams
  - Workflow mode: Keep current TypeScript generation

## General Improvements

- [ ] **Error Handling Standardization**
  - Consistent error handling across all API calls
  - Silent handling of expected errors (like auth)
  - User-friendly error messages for unexpected errors

- [ ] **Testing**
  - Add tests for session management
  - Test mode switching
  - Test error handling scenarios

