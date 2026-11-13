# interactor-curve-guest

Curve playback between sends: a viewer draws each remote part on a cubic curve through judged control points, behind the present.

## What is here

- `curve.sgd`: control points of position, velocity and tick for each part, and the Hermite segment at a view time. When points run out a part coasts and then stands; a late point bends the path and never moves the part.
- `tests/curve_gate.gd`: the error against the `T^4 / 384` bound at 6, 8 and 16 ticks, and the largest move in a tick after one, two and three lost sends.
- `docs/curve.md`: the calls, the bound, what was measured and the controls.

    godot --headless --path . -s tests/curve_gate.gd [-- --control=snap|novel]

## The other parts

Each part of the presence slice is a repository of its own in `V-Sekai-fire`, and they are checked
out side by side.

| Repository | What it holds |
| --- | --- |
| `interactor-packets-guest` | the Packet codec and the order of a body's 21 parts |
| `interactor-zone-router-guest` | the model of a zone that only routes, and the trace a relay replays |
| `interactor-observer-guest` | one client's check of what the zone relays: hashes, tags and verdicts |
| `interactor-curve-guest` | curve playback between sends |
| `interactor-replica-guest` | a shared object as four replicas |
| `interactor-anny-follow-guest` | the avatar posed from the muscle skeleton |
| `transport-zone-relay` | the relay in C, on sockets, with its load generator |
| `interactor-presence-gates` | the gates that join the parts on a real body, the videos and the ledger |

## Rules of the source

Guests are SafeGDScript and gates are GDScript run on a double-precision editor with the sandbox
built in. A gate prints a `RESULT:` line and has controls that must fail. Comments are at most 3%
of a file's lines, which `tools/comment_density.exs` of `interactor-presence-gates` checks, and
the explanation is in the documentation.

## Licence

MIT; see `LICENSE`.
