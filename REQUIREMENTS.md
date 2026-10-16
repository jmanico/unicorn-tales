# Requirements

## Required Requirement Inputs

- Project purpose: Provide a story platform for children under a shared family account. Use stories and related challenges to help children learn and grow. Let parents guide lessons according to their values, within quality and safety limits. Let children choose the course of a story. Let parents use the platform to tell stories themselves. Support learning from homework and school subjects through educational stories.
- Primary users / actors: Two or more parents and multiple children under the same family account. Parents act as administrators and can tell stories to their children.
- Core workflows: Understand children, their preferences, and their wishes. Generate stories dynamically and let children make story choices. Let parents in a family account guide lessons through their values and lesson selections. Provide stories for parents to tell to their children. Let parents enter homework and school subjects for educational stories. Let children respond to educational challenges related to stories.
- Business objects / data entities: Family accounts, children, parents, preferences, wishes, stories, lessons, story choices, parent values, parent lesson selections, homework, school subjects, and educational challenges.
- External integrations: UNKNOWN
- Authentication / roles: Parents are administrators within their shared family account and control lessons for its children. Children take part in stories. Authentication: UNKNOWN.
- Regulatory or privacy constraints: UNKNOWN

## Functional Requirements

### Story Generation

- **FR-1.1** The system MUST generate stories during use.

### Story Choices

- **FR-2.1** The system MUST present story choices to the child.
- **FR-2.2** The system MUST let the child select a story choice.
- **FR-2.3** The system MUST continue the story according to the child's selected choice.

### Parent Administration

- **FR-3.1** The system MUST provide an administrator role for parents within their family account.
- **FR-3.2** The system MUST let each parent select lessons for each child in their family account.
- **FR-3.3** The system MUST limit lessons in a child's stories to the parents' lesson selections for that child.
- **FR-3.4** The system MUST NOT let children change the lesson selections made by parents.
- **FR-3.5** The system MUST limit lessons in a child's challenges to the parents' lesson selections for that child.
- **FR-3.6** The system MUST let parents provide values to guide lessons for their children.
- **FR-3.7** The system MUST use parent values to guide lessons in stories and challenges.

### Parent Storytelling

- **FR-4.1** The system MUST present story content to parents for them to tell the story to their children.

### Educational Stories

- **FR-5.1** The system MUST let parents enter homework for their children.
- **FR-5.2** The system MUST let parents enter the subjects their children study at school.
- **FR-5.3** The system MUST generate educational stories based on homework that a parent enters.
- **FR-5.4** The system MUST generate educational stories based on school subjects that a parent enters.

### Educational Challenges

- **FR-6.1** The system MUST present educational challenges related to the child's story.
- **FR-6.2** The system MUST let children respond to educational challenges.

### Family Accounts

- **FR-7.1** The system MUST group parents and children under the same family account.
- **FR-7.2** The system MUST support two or more parents in a family account.
- **FR-7.3** The system MUST support multiple children in a family account.

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
- **OQ-8** How must the system verify a parent's role and family membership? What privacy rules apply to child information?
- **OQ-9** What must happen before parents select lessons for a child, or if they select no lessons?
- **OQ-10** How must changes to lesson selections affect existing stories and stories in progress?
- **OQ-11** Which controls must parents have in addition to lesson selection, including controls for challenges?
- **OQ-12** What controls must parents have when they tell stories themselves? How must story choices work in this workflow?
- **OQ-13** How must the system resolve different values or lesson selections from parents in the same family account?
- **OQ-14** What information and input formats must parents use for homework and school subjects?
- **OQ-15** How must parents choose which homework or school subjects an educational story uses?
- **OQ-16** How must homework and school subjects interact with the parents' values and lesson selections?
- **OQ-17** What criteria must show that educational stories and challenges teach the intended material correctly?
- **OQ-18** Which challenge types and other educational activities must the system support?
- **OQ-19** When must challenges appear, and how must they affect story progress?
- **OQ-20** What responses must children be able to give to challenges? What feedback must the system provide?
- **OQ-21** How must parents and children be added to or removed from a family account?
- **OQ-22** What limits, if any, must apply to the number of parents and children in a family account?
- **OQ-23** Which quality and safety criteria must identify parent guidance or lessons that are unsuitable or dangerous?
- **OQ-24** How must the system respond when parent guidance or lesson selections fail those criteria?
- **OQ-25** How must parents express their values, and what criteria must show that lessons reflect those values?
