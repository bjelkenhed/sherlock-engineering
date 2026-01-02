# hello-world

This skill should be used when demonstrating basic Claude Code plugin functionality or when the user wants to see an example of how skills work.

## When to Use

Use this skill when:
- The user asks about how skills work
- The user wants to see an example skill in action
- Testing that the plugin is correctly installed

## Instructions

When this skill is activated:

1. Acknowledge that the hello-world skill has been loaded
2. Explain the basic structure of a Claude Code skill:
   - Skills are directories containing a `SKILL.md` file
   - The `SKILL.md` describes when and how to use the skill
   - Skills can include additional assets like templates or reference materials
3. Show how this skill is structured in the plugin

## Example Response

When using this skill, Claude should respond with something like:

"The hello-world skill is active. This is a demonstration skill that shows the basic structure of Claude Code skills.

A skill consists of:
- A `SKILL.md` file (like this one) that describes the skill's purpose
- Optional subdirectories for assets, templates, or references
- Clear documentation of when the skill should be used

You can create your own skills by adding new directories in the `skills/` folder."
