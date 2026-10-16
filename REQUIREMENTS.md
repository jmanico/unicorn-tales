# Requirements

## Required Requirement Inputs

- Project purpose: Provide a story platform for children. Use lessons in stories to help children grow. Let children choose the course of a story.
- Primary users / actors: Children.
- Core workflows: Understand children, their preferences, and their wishes; generate stories dynamically; teach lessons through stories; let children make story choices.
- Business objects / data entities: Children, preferences, wishes, stories, lessons, and story choices.
- External integrations: UNKNOWN
- Authentication / roles: UNKNOWN
- Regulatory or privacy constraints: UNKNOWN

## Functional Requirements

### Story Generation

- **FR-1.1** The system MUST generate stories during use.

### Story Choices

- **FR-2.1** The system MUST present story choices to the child.
- **FR-2.2** The system MUST let the child select a story choice.
- **FR-2.3** The system MUST continue the story according to the child's selected choice.

## Non-Functional Requirements

None stated

## Open Questions

- **OQ-1** Which age groups must the system support?
- **OQ-2** What information must the system obtain about each child, including preferences and wishes? How must the system obtain this information?
- **OQ-3** How must information about a child affect system behavior?
- **OQ-4** What action must start story generation? Must the system generate a complete story or generate parts as the child makes choices?
- **OQ-5** Which lessons must the stories teach? What criteria define a good lesson that helps a child grow?
- **OQ-6** When must the system present story choices? What rules must connect each choice to the next part of the story?
- **OQ-7** What response must the system give if story generation fails?
- **OQ-8** What access and privacy rules must apply to children and their information?
