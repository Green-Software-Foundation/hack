---
name: IF Team Ideas
about: This describes a possible project for hackathon participants
title: "[Idea] ...."
labels: if-team-idea
assignees: ''

---

Please use this template to suggest an idea that people can try to implement as part of Carbon Hack 24. **Provide as much detail as possible**. If someone else submitted an idea but you feel you can do a better job of explaining, please go ahead and submit again.

## Prize category
_Help the participant understand which of the prize categories this idea would best fit_

- [ ] Best Model
- [ ] Best Content
- [ ] Beyond Carbon
- [ ] Best contribution to the framework

## User Story
_Describe the benefits of this change, ideally in the following format:_

- As a **< type of user >**, I want **< some goal >** so that **< some reason >**

## Rationale
Provide the relevant background information to understand why this is a useful thing to work on

*This is where you can provide more details that help the reader understand why you want to make this change*

## Impact
Finish this scentance: "If this idea is successful implemented the ....."

## Implementation guidelines
- If there are specific implementation details that are REQUIRED or PREFERRED please describe them here
*e.g. this model MUST conform to the `ModelPlugin` interface*
*e.g. this feature MUST be part of the supercomputer module*
*e.g. this feature SHOULD be be a model plugin*

## Difficulty
_Provide an assessment of the expected difficulty **from 1-5** to help hackers find tasks at their preferred skill level_

## Scope Of Work
_List some of the tasks that will be required to implement this idea_

- [ ] A new model plugin
- [ ] A new feature in an existing model plugin
- [ ] A manifest file will have to be written
- [ ] Implement test cases
- [ ] A new feature to the framework itself (the cli tool)
- [ ] It will require changes to the documentation


## Examples and resources
_Provide any links to prior discussions, similar code, examples, pseudocode, diagrams or anything else than can help the hacker understand the task_

## Manifest File
Provide a dummy Mmnifest file to help the implementer understand how this functionality will be executed, provide them with the necessary data, observations and structure so they can move fast with development.

```yaml
name: nesting-demo
description:
tags:
  kind: web
  complexity: moderate
  category: on-premise
initialize:
  models:
    - name: teads-curve
      model: TeadsCurveModel
      path: "@grnsft/if-unofficial-models"
    - name: sci-e
      model: SciEModel
      path: "@grnsft/if-models"
    - name: sci-m
      path: "@grnsft/if-models"
      model: SciMModel
    - name: sci-o
      model: SciOModel
      path: "@grnsft/if-models"
    - name: sci
      model: SciModel
      path: "@grnsft/if-models"
graph:
  children:
    child: # an advanced grouping node
      pipeline:
        - teads-curve
        - sci-e
        - sci-m
        - sci-o
        - sci
      config:
        teads-curve:
          thermal-design-power: 65
        sci-m:
          total-embodied-emissions: 251000 # gCO2eq
          time-reserved: 3600 # 1 hour in s
          expected-lifespan: 126144000 # 4 years in seconds    
          resources-reserved: 1 
          total-resources: 1 
        sci-o:
          grid-carbon-intensity: 457 # gCO2/kwh
        sci:
          functional-unit-duration: 1 
          functional-duration-time: ''
          functional-unit: requests # factor to convert per time to per f.unit
      children:
        child-1:
          inputs:
            - timestamp: 2023-07-06T00:00
              duration: 10
              cpu-util: 50
              e-net: 0.000811 #kwh     
              requests: 380
        child-2:
          inputs: 
            - timestamp: 2023-07-06T00:00
              duration: 10
              cpu-util: 33
              e-net: 0.000811 #kwh     
              requests: 380

```
