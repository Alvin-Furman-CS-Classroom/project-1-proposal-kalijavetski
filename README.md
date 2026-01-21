# [ChoreogrAIphy]

## System Overview

ChoreogrAIphy addresses a common challenge in dance: transforming an abstract theme or concept into concrete performance elements. Choreographers, especially those new to the field, often struggle to begin the creative process or find themselves repeating familiar patterns. ChoreogrAIphy provides AI-powered inspiration by generating coordinated song suggestions, costume specifications, and starting choreography from a single thematic input.
The system takes a user-provided theme (e.g., "ocean," "rebellion") along with choreography preferences (movement types, difficulty level, spatial constraints). It then produces three coordinated outputs: curated song recommendations that match the theme's mood and energy, costume design specifications derived through logical reasoning about the theme and intended movement, and optimized 30-second choreography sequences that serve as creative starting points.
ChoreogrAIphy integrates five AI modules working in concert. Costume reasoning uses propositional logic to generate appropriate costume specs based on theme and movement preferences. Song search employs informed search algorithms to find optimal musical matches from a pre-analyzed database. Choreography planning uses optimization techniques to generate movement sequences that balance aesthetic goals with physical constraints. An NLP-based feature extraction module analyzes new songs when needed, while a supervised learning classifier validates that generated choreography matches the intended style.
By synthesizing these AI techniques, ChoreogrAIphy helps choreographers overcome creative blocks, discover unexpected combinations, and launch new works with confidence. The system doesn't replace artistic vision—it amplifies it, providing an intelligent foundation upon which choreographers build unique performances.

## Modules

### Module 1: [Costume Design Reasoning]

**Topics:** Propositional Logic (Knowledge Bases, Inference Methods), Basic Search

**Input:** 
- Theme keywords (list of strings like "christmas, scary, heartbreak")
- Choreography preferences (text description of what movements the piece will include, energy level, any special requirements)
  
**Output:** 
- Text description of recommended costume (includes colors, style, fabric, length, what to avoid)
- 3-5 images from image search that match the costume description

**Integration:** This is the first module that is completed. It only needs the theme and preferences from the user - nothing from other modules. The costume ideas help set the visual direction before picking songs or creating actual choreography.

**Prerequisites:** Propositional Logic (Knowledge Bases, Inference Methods, Chaining) which are covered before Checkpoint 1.

---

### Module 2: [Song Search and Recommendation]

**Topics:** Informed Search (Beam Search, Heuristics)

**Input:** 
- Theme keywords (same list from user input, e.g., "ocean, waves, calm")

**Output:** 
- Top 3 song recommendations (each includes song title, artist name, and brief explanation of why it matches)

**Integration:** This module will run after the costume is given. It uses the same theme keywords the user provided initially. The selected song then becomes input for the choreography planning module.

**Prerequisites:** Informed Search (Heuristics, Beam Search) which is covered by Checkpoint 2.

---

### Module 3: [Choreography Sequence Planning]

**Topics:** Advanced Search (Optimization, Simulated Annealing)

**Input:** 
- Song mood and tempo (extracted from the selected song in Module 2)
- Choreography preferences (from user's initial input describing movement types and constraints)
- Optional: Starting pose (if user wants to specify where the sequence begins)

**Output:** 
- Ordered sequence of dance moves (list format, approximately 30 seconds of choreography)
- Example output: "standing pose → pirouette → arabesque → leap → turn sequence → floor slide → recovery"

**Integration:** This module needs the song selection from Module 2 (specifically mood and tempo) and the choreography preferences from the original user input. The generated sequence represents the creative core of the system's output.

**Prerequisites:** Advanced Search (Optimization, Simulated Annealing) which has been covered by Checkpoint 3.

---

### Module 4: [Alternative Song Analysis and Comparison]

**Topics:** NLP (Text Analysis, Sentiment Analysis)

**Input:** 
- User's alternative song choice (song title and artist name)
- System's recommended song from Module 2 (already has analyzed features)

**Output:** 
- Comparison report showing differences in mood, tempo, energy, and lyrical themes
- Example: "Your song is 20 BPM faster, more upbeat mood, similar themes of freedom but more hopeful tone"

**Integration:** This module is optional and only runs if the user wants to explore alternative songs. It takes the recommended song from Module 2 as a baseline and compares user suggestions against it

**Prerequisites:** NLP (n-grams, Word Embeddings, text analysis techniques) has been covered by Checkpoint 4.

---

### Module 5: [Choreography Style Validation]

**Topics:** Supervised Learning (Classification)

**Input:** 
- Generated choreography sequence (from Module 3)
- User's intended dance style (e.g., jazz, contemporary, hip-hop, ballet)

**Output:** 
- Style match validation (confirms whether generated choreography matches intended style)
- Confidence score (percentage indicating how well the sequence fits the style)

**Integration:** This module runs after choreography planning to validate that the generated sequence actually matches the style the user wanted. It acts as a quality check on Module 3's output.

**Prerequisites:** Supervised Learning (Classification techniques) which should hopefully be covered by Checkpoint 5.

---

## Feasibility Study

_A timeline showing that each module's prerequisites align with the course schedule. Verify that you are not planning to implement content before it is taught._

| Module | Required Topic(s) | Topic Covered By | Checkpoint Due |
| ------ | ----------------- | ---------------- | -------------- |
| 1      |Propositional Logic| Finished on 1/20                 | February 11               |
| 2      |Informed search (specifically beam search) |  Finished by end of January                | February 26               |
| 3      | Advanced Search (Simulated Annealing)   |  Middle/End of February                | March 19               |
| 4      | NLP (Text Analysis, Sentiment Analysis) |  Middle/End of March                | April 2                |
| 5      | Supervised Learning (Classification) | Middle of April                 | April 16               |

## Coverage Rationale

I chose these five AI topics because each one handles a different part of creating a dance performance. Propositional logic works for costumes because costume rules are clear - if there are jumps, don't use long skirts. These kinds of if-then rules are exactly what propositional logic is for. Beam search is good for finding songs because I need to balance multiple factors like mood, tempo, and energy. It lets me search efficiently through lots of songs while keeping the best options. Simulated annealing fits choreography generation because sometimes you need to accept an awkward move to get to a better sequence overall. This technique lets the system explore more creative options instead of getting stuck.
NLP handles song lyrics analysis so users can compare songs based on what they're actually about, not just how they sound. Supervised learning validates the choreography style by learning patterns from examples. It checks that the generated sequence actually matches jazz or contemporary or whatever style was requested. Together, these techniques cover the whole workflow from initial concept to finished, validated choreography.
