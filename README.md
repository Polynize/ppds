# Poly Performance Data Schema (v1.0)

⚠ This data standard is under development. Please do not use the information below without emailing contact@polynize.io

## Purpose
The Poly Performance Data Schema is a universal standard designed to capture, structure, and evaluate human performance across a variety of real-world contexts. It supports structured analysis of text, voice, and video-based responses and allows organizations, platforms, and researchers to measure skill-based performance in a transparent, modular, and extensible format.

This schema is one of the foundational components of the [Poly Performance Network](https://polynize.io/ppn) — a global initiative bringing together leaders across business, education, gaming, sports, and innovation to build a shared language and infrastructure for human capability. It is designed to be used in:
- Workforce and skills development
- Real-time coaching and learning systems
- Hiring and certification workflows
- AI-human collaboration interfaces

## Overview
The schema enables a consistent structure for modeling real-world scenarios, evaluating responses, and benchmarking individual or group performance. It is designed to:
- Provide a standard method for capturing and analyzing skill performance across domains
- Support integration with AI models, coaching engines, and data visualization tools
- Enable cross-domain benchmarking of performance using scenario-driven assessments
- Allow organizations to define their own analysis frameworks while maintaining interoperability

It is modular, extensible, and intended to evolve with contributions from the wider community.

## Schema Description

The schema is composed of several interrelated entities that represent the structure of a performance activity, including its components, skillsets, benchmarks, and results.

### Entity Relationship Overview
```
Activity
  ├── AnalysisDefinition
  │     └── MetricDefinition(s)
  └── Scenario(s)
        └── Challenge(s)
              └── Response(s)
                  └── Analysis
                        └── Metric(s)
Skillset(s)
  └── Skill(s)
Scenario
  └── Benchmark (per Scenario)
PlayerPerformanceReport
  └── Analysis Summary
```

### Full Activity Example
```json
{
  "activityId": "7a1fa358-6f80-41f0-8bde-0e1d2f3cc192",
  "title": "Customer Escalation Management",
  "description": "This simulation evaluates how a candidate handles client complaints and difficult escalations.",
  "frameworkTag": "MEDDIC",
  "languageCode": "en-US",
  "analysisDefinition": {
    "analysisDefinitionId": "1b2d07ae-0b95-4b9b-88de-b2bc0a47d8a4",
    "description": "Score empathy and problem-solving in high-stress interactions.",
    "metricDefinitions": [
      {
        "metricDefinitionId": "5c18496c-4fd1-4f64-a037-96e74945d6dc",
        "skillId": "6c67093c-c5c5-48ec-b105-fcf823ed2f60",
        "evaluationCriteria": "Recognize and reflect emotional state",
        "weight": 0.6
      },
      {
        "metricDefinitionId": "66d2f888-9b6d-42ed-9e31-b70b9277c5a0",
        "skillId": "2f5f4607-5a47-4d84-929b-85e3b5cb1fd8",
        "evaluationCriteria": "Offer actionable, client-centered solutions",
        "weight": 0.4
      }
    ]
  },
  "scenarios": [
    {
      "scenarioId": "a19d41f7-3473-4e3a-9c3e-dcb24b2d1f42",
      "title": "Delayed Shipment Escalation",
      "scenarioText": "A customer calls in to complain about a shipment delay on a high-value order.",
      "benchmark": {
        "benchmarkId": "bf64cce1-7f1b-4d10-8e88-9c50fc85f765",
        "benchmarkResponse": "Thank you for bringing this to our attention. I understand this delay is frustrating...",
        "benchmarkScore": 85.0
      },
      "challenges": [
        {
          "challengeId": "2e94ae36-6d32-453b-9307-7e733790260a",
          "prompt": "Respond to the customer's frustration about the delay.",
          "inputType": "text",
          "response": {
            "responseId": "82bdecd7-68c1-4f92-a991-6dbbc3fe3444",
            "responseText": "I completely understand your frustration and I want to assure you...",
            "responseAudioUrl": null,
            "responseVideoUrl": null,
            "languageCode": "en-US",
            "timestamp": "2025-06-18T01:00:00Z"
          },
          "analysis": {
            "analysisId": "e1a04a8e-0fc7-4d67-b1aa-25f98e82e88f",
            "scenarioId": "a19d41f7-3473-4e3a-9c3e-dcb24b2d1f42",
            "responseId": "82bdecd7-68c1-4f92-a991-6dbbc3fe3444",
            "skillsetId": "baf25bb4-d73a-4eb6-bfa7-f4c7e9c95b44",
            "benchmarkId": "bf64cce1-7f1b-4d10-8e88-9c50fc85f765",
            "analysisComments": "Strong display of empathy and structured problem-solving.",
            "metrics": [
              {
                "metricId": "83d258f0-7e6d-4060-b678-f96e7ddab316",
                "skillId": "6c67093c-c5c5-48ec-b105-fcf823ed2f60",
                "score": 92,
                "piq": 108.2,
                "passed": true
              },
              {
                "metricId": "3c6e6118-c7ef-4d86-b4cd-f14ff34eb528",
                "skillId": "2f5f4607-5a47-4d84-929b-85e3b5cb1fd8",
                "score": 89,
                "piq": 104.7,
                "passed": true
              }
            ]
          }
        }
      ]
    }
  ],
  "skillsets": [
    {
      "skillsetId": "baf25bb4-d73a-4eb6-bfa7-f4c7e9c95b44",
      "name": "Client Conflict Management",
      "description": "Ability to resolve client escalations with empathy and logic.",
      "skills": [
        {
          "skillId": "6c67093c-c5c5-48ec-b105-fcf823ed2f60",
          "name": "Empathy",
          "description": "Understanding others’ emotions.",
          "intelligenceTag": "emotional"
        },
        {
          "skillId": "2f5f4607-5a47-4d84-929b-85e3b5cb1fd8",
          "name": "Problem Solving",
          "description": "Identify and resolve issues efficiently.",
          "intelligenceTag": "strategic"
        }
      ]
    }
  ]
}
```

## Extensibility
- `customDimensions`: Partner-specific metrics or behaviors
- `coachRecommendations`: AI + human hybrid insights
- `frameworkTags`: Attach known evaluation models (e.g. STAR, OKRs)
- `contextualSignals`: Incorporate time pressure, stakeholder tension, etc.

## Licensing and Usage
This schema is open and extensible under Creative Commons Attribution-ShareAlike (CC BY-SA). Organizations may adopt and extend it provided attribution is maintained.

Let us know how you’re using the Poly Performance Data Schema. To contribute improvements or propose extensions, please submit a pull request to our GitHub repository.
