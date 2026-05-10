# Exchange 05 — Skills vs commands conceptual question

- **Timestamp:** 2026-05-09
- **Context:** With the agents reorganization done, I had asked whether to scaffold `.claude/commands/` next. The user paused for a conceptual sanity-check first.

## User Input

```
does skills make commands obsolete?
```

## Tool Calls

None — purely conceptual response.

## My Visible Response (verbatim)

> No — they're complementary, not redundant. The distinction is **who pulls the trigger**:
>
> | | **Skills** | **Slash commands** |
> |---|---|---|
> | Invoked by | Claude (heuristic, based on `description` matching the user's message) | The user (typing `/name`) |
> | Predictability | May not fire when you want it, may fire when you don't | Exact, deterministic |
> | Discoverability | Shows up in the Skills system list | Tab-completes when you type `/` |
> | Arguments | Whatever Claude infers from context | Explicit, parsed positional/flag args |
> | Best for | "I want this capability available; let the model decide when" | "I want a typeable shortcut I can rely on" |
>
> The `deep-bible-study-devotional` skill already fires on natural language ("give me a study on John 3"). That's great for conversational use. But you'd still want commands for things like:
>
> - `/study Genesis 6` — explicit "do the full study now, don't chat first"
> - `/teacher perry-stone Isaiah 53` — pin a specific teacher voice for a chapter
> - `/word hesed` — quick word study (invokes the linguist agent)
> - `/personal-note Genesis 1` — scaffold a `.personal/Genesis/Genesis-01/notes.md` from a template
>
> These all benefit from being typeable, deterministic, and arg-bearing. A skill *could* do them, but you'd be constantly nudging it ("yes, actually do the study, don't ask me clarifying questions first") instead of pressing a button.
>
> Quick rule of thumb: **if you already know exactly what you want, command. If you want Claude to figure out the right time to apply something, skill.** Plenty of teams have both.
>
> Want me to scaffold `.claude/commands/` with a starter set tailored to this repo? I'd propose something like the four above plus a `/chapter` for filling in stub READMEs. Or just create the empty folder + a README explaining the convention and let you populate it organically.

## Files Read / Modified

None.

## Outcome

The user didn't answer this directly — instead they immediately moved into the skills battery request (Exchange 06). The `.claude/commands/` scaffolding is still pending as of session end.
