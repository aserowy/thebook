# How to write concepts

## Motivation

Concepts are an important step in distributing work flows in our LOB and in simplifying documentation of cross-cutting concerns.

This concept describes how concepts should be structured in order to homogenise the work with them and to meet the expectations of the readers. This increases the degree of reusability and allows you to use concepts from this repository in your project as guidance and documentation. Furthermore, concepts from projects can be distributed in this repository.

## Context

For the structural design of concepts, we use the [four quadrant model][1]. As the name suggests, the model divides content into four questions to be answered:

- Why?
- What?
- How to?
- What else?

The following table shows possible topics or possibilities to answer the questions. It is important that the order of the questions should not be changed in your writing.

| Quadrant  | Topics\possibilities |
| ---       | --- |
| Why       | purposes, motivate, raise awareness |
| What      | explaining terms, creating a background, go into detail |
| How to    | examples, give concrete instructions, tutorials |
| What else | alternative solutions, looking ahead, related topics |

To meet expectations, first-level headings should be similar in all concepts. Of course, deeper level headings should have a technical reference. The following are possible headings for the individual quadrants.

| Quadrant  | Headings |
| ---       | --- |
| Why       | motivation, task |
| What      | context, influencing factors, alternatives, solution, background |
| How to    | example, application, step by step |
| What else | next steps, extensions, feedback, outlook |

At the end of the document, a section for meta-information is defined, in which the version and the author are specified.

```markdown
## Meta

| Meta    |     |
| ---     | --- |
| editor  | Alexander Serowy |
| version | 0.1 |
```

[1]: <https://www.amazon.de/-/en/Uwe-Vigenschow/dp/3864906970> "Soft Skills für Softwareentwickler"

## Step by step

In our example we write a concept to document microservices. In the first step we write the motivation why the concept was created in the first place.

> Documentation is often an uninvited guest to developers. In order to increase the acceptance of up-to-date documentation, we provide a slightly weighty way to capture these systems...".

After the motivation, we present in our concept how exactly the documentation is structured and which content elements we should describe. In addition, background and terminology are described and specified here as well.

Next comes the "How to". In this section we will then build up a documentation about an exemplary micro service. We describe how the microservice that is to be described looks like and then go step by step through the individual structures that were defined and explained in the previous step.

In the last step, we then write about related topics and alternative solutions, such as how decisions can be written and filed differently like ADR (Architecture Decision Record).

## Next steps

Using this template we can achieve a high degree of reusability for concepts. If you use concepts as documentation in projects, you are welcome to make them available to everyone in this repository!

## Meta

| Meta    |     |
| ---     | --- |
| editor  | Alexander Serowy |
| version | 0.1 |
