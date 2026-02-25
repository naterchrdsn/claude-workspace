# RPI Feature Template

Copy this template to start a new feature using the RPI workflow.

## Usage

```bash
# Create new feature folder
cp -r examples/rpi-template rpi/my-feature-name

# Edit the request
# Then run research phase
/rpi:research rpi/my-feature-name/REQUEST.md

# If GO, run plan phase
/rpi:plan my-feature-name

# Then implement
/rpi:implement my-feature-name
```

## Structure

```
rpi-template/
├── REQUEST.md          # Fill this out first
├── research/           # Created by /rpi:research
│   └── .gitkeep
├── plan/               # Created by /rpi:plan
│   └── .gitkeep
└── implement/          # Created by /rpi:implement
    └── .gitkeep
```

## Tips

1. **Be specific in REQUEST.md** - Vague requests lead to vague research
2. **Include constraints** - Technical, timeline, budget constraints help research
3. **List open questions** - Better to surface unknowns early
4. **Link related work** - Context helps agents make better recommendations
