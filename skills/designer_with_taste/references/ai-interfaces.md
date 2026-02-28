# AI/ML Interface Design

Principles drawn from Google PAIR (People + AI Research), Google AI Principles, Google 
Conversation Principles, Microsoft Responsible AI, IBM Design with Watson, Yves Béhar (10 
Principles for Design in the Age of AI), Tom Castle (5 Rules for AI Tech in Design), Josh Clark 
(Design in the Era of the Algorithm), Calm Technology (Amber Case), and principles of bot 
design (Intercom).

---

## Core AI Interface Philosophy

AI is not magic — it is a tool with capabilities, limitations, and failure modes. The designer's 
job is to make AI useful, trustworthy, and controllable. Every AI interface should answer: 
**what does this AI do, how confident is it, and what happens when it's wrong?**

---

## The Seven Laws of AI Interface Design

### 1. Make the AI's Capabilities Visible
Users cannot form correct mental models of AI if they don't understand what it can and cannot do.

```
Do:    Show examples of what the AI handles well
Do:    Set expectations ("I can help with X, Y, Z")
Do:    Communicate scope limits naturally ("I'm not sure about that")
Don't: Imply general intelligence or omniscience
Don't: Hide the fact that AI is involved
Don't: Let marketing language set unrealistic expectations
```

### 2. Show Confidence, Not Certainty
AI outputs exist on a confidence spectrum. The interface should reflect this.

```
High confidence (>90%):   Present as a statement with option to edit
                          "Your flight is at 3:15 PM from Gate B12"
                          
Medium confidence (60-90%): Present as a suggestion with alternatives
                          "It looks like you might mean [Option A] or [Option B]"
                          
Low confidence (<60%):    Ask for clarification or show multiple options
                          "I found several possibilities — which did you mean?"
                          
Uncertainty:              Say so directly
                          "I don't have enough information to answer that"
```

### 3. Keep Humans in Control
AI should amplify human capability, not replace human judgment. The person using the AI must 
always be the final decision-maker.

```
Patterns for human control:
- Suggest, don't auto-act: "Would you like me to [action]?"
- Easy override: every AI decision should be editable/reversible
- Opt-in escalation: start with low-stakes automation, earn trust
- Bulk actions need confirmation: "Apply to all 47 items?"
- Critical decisions always require explicit human approval
- "Don't do this again" option for recurring suggestions
```

### 4. Design for Failure Gracefully
AI will be wrong. The interface must handle this without breaking trust.

```
Error handling hierarchy for AI:
1. Prevent: constrain inputs to reduce bad outputs
2. Detect: show when AI confidence is low
3. Recover: make it trivial to correct mistakes
4. Learn: use corrections to improve ("Thanks, I'll remember that")
5. Escalate: offer human alternative when AI can't help

Error UX patterns:
- "Not what you expected? [Edit] [Try again] [Get human help]"
- Inline editing of AI output (don't require starting over)
- Feedback mechanism: thumbs up/down, report issue
- Graceful degradation: if AI fails, fall back to manual workflow
```

### 5. Explain Without Overwhelming
Transparency about AI reasoning builds trust, but most users don't want a research paper.

```
Progressive explanation:
Level 0: Result only (default for most users)
         "Price: $45/night"

Level 1: Brief rationale (on request or hover)
         "Price based on similar listings in your area this season"

Level 2: Detailed factors (for power users, via expand/link)
         "Factors: location (±$8), season (+$12), amenities (+$5), 
          demand (+$10). Based on 342 comparable listings."

Level 3: Full audit trail (for compliance, debugging)
         Model version, input features, confidence score, training data
```

### 6. Match AI Speed to User Expectations
AI responses have variable latency. The interface must manage perceived speed.

```
Instant (<500ms):    Show result directly, no loading state needed
Fast (500ms-2s):     Subtle loading indicator (typing dots, shimmer)
Medium (2s-10s):     Progress indicator + "thinking about X..."
Slow (10s-60s):      Step-by-step progress + estimated time remaining
Very slow (>60s):    Background processing + notification when ready

Streaming responses (LLM chat):
- Show text as it generates (token by token or chunk by chunk)
- Indicate when response is still generating vs. complete
- Allow user to stop generation mid-stream
- Don't auto-scroll if user has scrolled up to read earlier content
```

### 7. Respect Social Norms
AI should behave in ways that feel socially appropriate (Amber Case). Don't be creepy, 
don't be presumptuous, don't pretend to be human when the user hasn't consented to that fiction.

```
Do:    Identify as AI when directly asked
Do:    Respect privacy — don't surface info users didn't share
Do:    Match formality to context (business vs. casual)
Don't: Fake emotions or claim to "feel" things
Don't: Use dark patterns powered by AI (manipulative personalization)
Don't: Personalize in ways that feel surveilled
```

---

## Chat Interface Design

The most common AI interface pattern. Design it well.

### Message Layout
```
AI messages:  Left-aligned, with AI avatar/icon
User messages: Right-aligned, with user avatar (optional)
System messages: Center-aligned, muted, smaller text

Message structure:
┌──────────────────────────────────┐
│ 🤖 AI Avatar                     │
│                                   │
│ Message content with proper       │
│ paragraph spacing, formatted      │
│ text, and inline code.           │
│                                   │
│ - Lists render cleanly            │
│ - Code blocks are syntax-colored  │
│                                   │
│         12:34 PM  ✓ Read          │
└──────────────────────────────────┘
```

### Input Area
```
┌──────────────────────────────────────────┐
│  [📎] Type a message...          [Send ➤] │
│                                           │
│  [Suggested: "Tell me more"] ["Example"]  │
└──────────────────────────────────────────┘

Features:
- Auto-resize textarea (grows with content, max ~6 lines)
- Send on Enter (Shift+Enter for new line)
- File/image attachment support if relevant
- Suggestion chips for common follow-ups
- Character/token count if there's a limit
- Disable send button when input is empty
```

### Conversation Flow Patterns
```
Onboarding:
  Start with a greeting + 2-3 suggested actions
  "Hi! I can help you with [A], [B], or [C]. What would you like?"

Clarification:
  When ambiguous, ask ONE clear question with options
  "Did you mean [Option A] or [Option B]?"

Multi-turn context:
  Show the AI remembers context (reference prior messages)
  But allow topic changes gracefully

Long responses:
  Chunk into paragraphs with clear structure
  Use headers, lists, code blocks for scannability
  Collapsible sections for lengthy detail

Dead ends:
  Always provide a way forward
  "I can't help with that, but you could [alternative] or [escalate]"
```

### Typing / Thinking Indicators
```css
/* Animated typing indicator */
.typing-indicator span {
  display: inline-block;
  width: 8px; height: 8px;
  border-radius: 50%;
  background: var(--text-3);
  animation: typing 1.4s infinite;
}
.typing-indicator span:nth-child(2) { animation-delay: 0.2s; }
.typing-indicator span:nth-child(3) { animation-delay: 0.4s; }

@keyframes typing {
  0%, 60%, 100% { opacity: 0.3; transform: translateY(0); }
  30% { opacity: 1; transform: translateY(-4px); }
}
```

---

## Generative AI Output Patterns

### Text Generation
```
- Stream the response (shows progress, feels faster)
- Render markdown formatting as it arrives
- Provide copy button for the full response
- Allow inline editing of generated text
- "Regenerate" button for alternative responses
- Tone/length controls before or after generation
```

### Image Generation
```
- Show generation progress (steps, percentage)
- Generate 2-4 variations, let user choose
- Provide iteration controls: "more like this", "change X"
- Show the prompt used (transparency)
- Watermark or label as AI-generated
- Download in multiple resolutions
```

### Code Generation
```
- Syntax highlighting appropriate to language
- Copy button (one-click)
- "Apply to file" / "Insert at cursor" actions
- Diff view showing what changes from current code
- Run/test button if sandbox is available
- Explain button for understanding generated code
```

### Structured Data Generation (forms, tables, configs)
```
- Show generated data in its final format (preview)
- Editable inline before accepting
- Validate against schema/constraints
- Highlight AI-filled vs. user-filled fields differently
- "Accept all" + individual field acceptance
```

---

## AI Feature Patterns

### Smart Suggestions
```
Position:   Inline (ghost text) or dropdown below input
Trigger:    After typing pause (300-500ms), not every keystroke
Accept:     Tab key or click to accept
Dismiss:    Keep typing to ignore, Escape to dismiss
Styling:    Lower opacity than user text (ghost text: 40-50% opacity)
Frequency:  Don't show on every input — only when confident
```

### AI-Powered Search
```
- Show AI interpretation of query: "Showing results for [interpreted query]"
- Mix AI answers with traditional results (clearly differentiated)
- Allow refinement: "Did you mean..." or faceted filters
- Show sources / evidence for AI answers
- Fall back gracefully to keyword search if AI has low confidence
```

### Automated Classification / Tagging
```
- Show AI-applied tags with visual distinction (dashed border, "AI" label)
- Easy to remove: X button on each tag
- Easy to add manually alongside AI suggestions
- Confidence threshold: only show high-confidence tags by default
- Learning feedback: user corrections improve future suggestions
```

---

## Responsible AI Design

From Google AI Principles, Microsoft Responsible AI, and IBM Design with Watson:

```
Fairness:     Test for bias across demographics. Show when AI may be biased.
Transparency: Users know they're interacting with AI. Decisions are explainable.
Privacy:      Minimize data collection. Be explicit about what data AI uses.
Safety:       Constrain AI actions to prevent harm. Human oversight for critical decisions.
Accountability: Clear ownership. Audit trails. Feedback mechanisms.
```

### Bias Disclosure Pattern
```
When AI output may be biased or limited:
"Note: This recommendation is based on [data source]. It may not fully 
represent [underrepresented group/context]. [Learn more]"

When AI lacks data:
"I have limited information about [topic]. This suggestion may be less 
accurate than usual."
```

---

## AI Interface Design Checklist

```
□ AI capabilities are clearly communicated (what it does and doesn't do)
□ Confidence levels are visible (suggestions vs. certain answers)
□ Human override: every AI action is editable/reversible
□ Failure states: graceful degradation when AI is wrong
□ Explanation available: at least one level of "why" on demand
□ Loading states: appropriate for response latency
□ Streaming: for LLM responses, show text as it generates
□ Feedback mechanism: users can rate/correct AI output
□ Privacy: users understand what data AI uses
□ No deceptive patterns: AI doesn't pretend to be human
□ Accessibility: AI features work with screen readers/keyboard
□ Empty state: clear guidance when no AI output yet
□ Chat input: auto-resize, Enter to send, suggestion chips
□ Regenerate: option to get alternative AI responses
□ Escalation: clear path from AI to human help
```
