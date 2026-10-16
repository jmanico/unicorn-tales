# Requirements

## Required Requirement Inputs

- Project purpose: Provide a story platform for children. Use lessons in stories to help children grow. Let parents control the lessons. Let children choose the course of a story. Let parents use the platform to tell stories themselves.
- Primary users / actors: Children and parents. Parents act as administrators and can tell stories to their children.
- Core workflows: Understand children, their preferences, and their wishes; generate stories dynamically; let parents select lessons; teach those lessons through stories; let children make story choices; provide stories for parents to tell to their children.
- Business objects / data entities: Children, parents, preferences, wishes, stories, lessons, story choices, and parent lesson selections.
- External integrations: UNKNOWN
- Authentication / roles: Parents are administrators who control lessons. Children take part in stories. Authentication: UNKNOWN.
- Regulatory or privacy constraints: UNKNOWN

## Functional Requirements

### Story Generation

- **FR-1.1** The system MUST generate stories during use.

### Story Choices

- **FR-2.1** The system MUST present story choices to the child.
- **FR-2.2** The system MUST let the child select a story choice.
- **FR-2.3** The system MUST continue the story according to the child's selected choice.

### Parent Administration

- **FR-3.1** The system MUST provide an administrator role for parents.
- **FR-3.2** The system MUST let parents select the lessons taught in stories for their children.
- **FR-3.3** The system MUST limit lessons in a child's stories to the lessons selected by the child's parent.
- **FR-3.4** The system MUST NOT let children change the lesson selections made by parents.

### Parent Storytelling

- **FR-4.1** The system MUST present story content to parents for them to tell the story to their children.

## Non-Functional Requirements

None stated

## Open Questions

- **OQ-1** Which age groups must the system support?
- **OQ-2** What information must the system obtain about each child, including preferences and wishes? How must the system obtain this information?
- **OQ-3** How must information about a child affect system behavior?
- **OQ-4** What action must start story generation? Must the system generate a complete story or generate parts as the child makes choices?
- **OQ-5** Which lessons can parents select? What criteria define a good lesson that helps a child grow?
- **OQ-6** When must the system present story choices? What rules must connect each choice to the next part of the story?
- **OQ-7** What response must the system give if story generation fails?
- **OQ-8** How must the system verify that a parent can administer a child's lesson selections? What privacy rules apply to child information?
- **OQ-9** What must happen before a parent selects lessons, or if the parent selects no lessons?
- **OQ-10** How must changes to lesson selections affect existing stories and stories in progress?
- **OQ-11** Which controls must parents have in addition to lesson selection?
- **OQ-12** What controls must parents have when they tell stories themselves? How must story choices work in this workflow?
- **OQ-13** Can more than one parent administer the same child? If so, how must the system resolve different lesson selections?
