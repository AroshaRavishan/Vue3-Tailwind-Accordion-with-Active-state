# Vue Accordion Component

This component creates an accordion that allows users to toggle the visibility of exam details. It uses Vue's Composition API for managing state and handling the toggle functionality.

## Features

- Collapsible sections for displaying exam details
- Dynamic toggling of active section
- Smooth rotation of icons to indicate expanded/collapsed state

# Looped Accordion Component

This Vue.js component implements an accordion-style list for displaying exams and their details. Each exam can be expanded to show its items and their respective durations.

## Script Setup

### Imports and References

- **Imports**: The `ref` function is imported from Vue to create reactive references.
- **References**:
  - `activeExamIndex`: A reactive reference to store the index of the currently active (expanded) exam. Initialized to `null`.
  - `exams`: A reactive reference containing an array of exam objects. Each exam object has a `title` and an array of `items`. Each item has a `title` and a `duration`.

### Function: `toggleExams(index)`

- **Purpose**: This function toggles the visibility of the items within an exam.
- **Parameters**: It takes a single parameter `index`, which represents the index of the clicked exam.
- **Behavior**:
  - If the `index` matches the `activeExamIndex`, it means the clicked exam is already active. The function sets `activeExamIndex` to `null` to collapse the exam.
  - If the `index` does not match the `activeExamIndex`, the function sets `activeExamIndex` to the `index` of the clicked exam, thereby expanding it and collapsing any previously active exam.

## Template Structure

- **Accordion Container**: A `div` with a class of `accordion` to wrap the entire list of exams.
- **Exam List**: Iterates over the `exams` array using `v-for` and renders each exam as an individual accordion item.
  - **Exam Header**:
    - Contains the exam title and an SVG icon.
    - Clicking the header triggers the `toggleExams(index)` function.
    - The SVG icon rotates 180 degrees if the exam is active (expanded).
  - **Exam Content**:
    - Conditionally rendered using `v-if` to display the exam items only when the `activeExamIndex` matches the exam's index.
    - Lists each item with its title and duration.

## Styling

- **Accordion Item**: Styles for the border and margin of each accordion item.
- **Accordion Header**: Styles for the padding, background color, and cursor of the header. Also styles for flexbox alignment.
- **Accordion Content**: Styles for the padding and background color of the content.
- **Accordion Icon**: Transitions the SVG icon rotation.
