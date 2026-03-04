# Search Pattern Examples

## Example 1: Finding Logic (Conceptual)

**Question:** "Where is the logic that changes a booking to confirmed status?"

```
# Step 1: Semantic search (both codebases, parallel)
claude-context: "confirm booking status change transition confirmed"
  → path: /path/to/common-api
  → path: /path/to/common-booking

# Step 2: Extract identifiers from results
Found: BookingState.SUCCESS, updateBookingState, confirmed_by, forceConfirmBooking

# Step 3: Grep for exact tracking
Grep: "BookingState.SUCCESS" → all files setting success state
Grep: "confirmed_by" → all confirmation pathways
Grep: "forceConfirmBooking" → auto-confirmation logic

# Step 4: Read key files for full understanding
```

## Example 2: Before Code Modification

**Task:** "Add a new state PENDING_PAYMENT to BookingState"

```
# Step 1: Find enum definition
claude-context: "BookingState enum definition state types"
Grep: "BookingState" (files_with_matches) → list all files

# Step 2: Analyze impact
Grep: "BookingState\." (content mode) → every state reference
Grep: "state === " or "\.state ==" → string-based comparisons
Grep: "switch.*state" or "case.*state" → switch statements

# Step 3: Check patterns
claude-context: "how are new booking states handled, state transition validation"

# Step 4: Make changes in all identified locations

# Step 5: Verify
Grep: "PENDING_PAYMENT" → confirm it appears in all needed places
Grep: "BookingState" → count matches, compare with step 2
```

## Example 3: Cross-Codebase Investigation

**Question:** "What is the flow for passing bookings from the API server to the booking server?"

```
# Step 1: Search both codebases in parallel
claude-context (api): "booking queue send message SQS"
claude-context (booking): "booking queue receive process SQS"

# Step 2: Track queue names
Grep (api): "QUEUE_NAME" → find queue identifiers
Grep (booking): same queue names → find consumers

# Step 3: Trace serialization
Grep (api): "BookingQueueSerializer" → what data is sent
Grep (booking): "SqsMessageHandler" → what data is received
```

## Example 4: Grep-First Search

**Task:** "Find all call sites of the confirmBooking function"

```
# Step 1: Grep for exact name
Grep: "confirmBooking" (files_with_matches) → all files
Grep: "confirmBooking" (content, context=3) → usage context

# Step 2: Semantic search for indirect references
claude-context: "booking confirmation flow, confirm booking process"
→ may reveal indirect callers, queue-based invocations, etc.
```
