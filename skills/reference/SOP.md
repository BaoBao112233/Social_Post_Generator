# SOP: Generate Image Prompts for Marketing Posts

## Purpose
Convert a user-provided marketing post draft plus uploaded product images into high-quality image generation prompts that align with the brand context, visual guidelines, and available image references.

## Inputs
The workflow requires the following inputs:
1. Post content pasted by the user
2. One or more uploaded product images
3. Brand context file: `@file:brand_context.md`
4. Visual guideline file: `@file:visual_guideline.md`
5. Product information file: `@file:product_catalog.md`
6. Image references folder: `@file:image_reference`

## Output
The final output should include:
1. A short analysis of the post content
2. Key visual direction derived from the brand context and visual guidelines
3. Recommended creative angles for the image
4. 3-5 polished image prompts suitable for image generation
5. 1 negative prompt block
6. A short rationale explaining why the prompts fit the post and brand

## Core Rules
- Always use the uploaded product image(s) as the primary visual anchor.
- Always read and apply guidance from `@file:brand_context.md`.
- Always read and apply guidance from `@file:visual_guideline.md`.
- Always read and apply guidance from `@file:product_catelog.md`.
- Always review relevant references from `@file:image_reference` before writing prompts.
- Do not invent brand attributes that are not supported by the provided files.
- Do not hardcode brand-specific assumptions into the workflow itself; derive them from the provided files at runtime.
- Preserve product accuracy. Do not change the product’s core shape, color, materials, or defining features unless explicitly requested.
- Prompts must be usable for image generation and should be visually specific, clear, and production-ready.

## Workflow

### Step 1: Intake the assets
When the user provides content and product images:
- Read the pasted content carefully
- Inspect all uploaded product images
- Load `@file:brand_context.md`
- Load `@file:visual_guideline.md`
- Load `@file:product_catalog.md`
- Review relevant examples from `@file:image_reference`

### Step 2: Analyze the post content
Extract the following:
- Main topic of the post
- Core message
- Target audience, if stated or implied
- Desired emotional tone
- Key product selling points
- Any campaign angle, seasonal angle, or offer mentioned
- Any visual cues explicitly mentioned in the content

### Step 3: Derive the visual strategy
Based on the content and the reference files, determine:
- Visual mood
- Composition style
- Environment or setting
- Lighting direction
- Color treatment
- Styling level (clean studio, lifestyle, premium editorial, travel-inspired, etc.)
- Whether the image should focus on product-only, product-in-use, or product-in-context storytelling

### Step 4: Ground the output in brand context
From `@file:brand_context.md`, identify:
- Brand personality
- Tone and emotional positioning
- Audience expectations
- Any brand do/don’t rules relevant to visuals

From `@file:visual_guideline.md`, identify:
- Preferred composition
- Framing
- Background style
- Color palette direction
- Lighting preferences
- Texture/material cues
- Visual motifs to include or avoid

From `@file:image_reference`, identify:
- Repeating visual patterns
- Composition approaches that match the current post
- Reference styles most relevant to the requested image direction

### Step 5: Choose the image direction
Propose 2-3 possible directions internally, then select the best one based on:
- Fit with the content
- Fit with the brand
- Fit with the product image
- Feasibility for image generation
- Clarity for a marketing post visual

Examples of direction types:
- Hero product shot
- Lifestyle scene
- Editorial campaign visual
- Travel-inspired aspirational shot
- Clean conversion-focused product visual

### Step 6: Write the prompts
Create 3-5 final prompts.

Each prompt should:
- Clearly describe the product as seen in the uploaded image
- Reflect the intended campaign/message of the post
- Follow the brand and visual guideline files
- Specify scene, composition, lighting, mood, and styling
- Be concrete enough for image generation
- Avoid generic language like “make it nice” or “beautiful ad image”

Each prompt should ideally contain:
- Subject
- Scene/environment
- Composition/framing
- Lighting
- Mood
- Brand-fit styling cues
- Quality/detail cues
- Any necessary constraints to preserve product fidelity

### Step 7: Write the negative prompt
Provide one reusable negative prompt block that prevents:
- Off-brand styling
- Wrong product proportions
- Distorted product details
- Cluttered composition
- Cheap-looking ad aesthetics
- Inconsistent lighting
- Irrelevant props or background elements

### Step 8: Return the result in the required format
Use the output format below.

## Required Output Format

### 1. Content Analysis
- Main message:
- Audience:
- Tone:
- Product role in the post:
- Recommended visual objective:

### 2. Visual Direction Summary
- Brand-aligned mood:
- Recommended setting:
- Composition style:
- Lighting style:
- Color direction:
- Reference pattern observed:

### 3. Prompt Options

#### Prompt 1
[final image prompt]

#### Prompt 2
[final image prompt]

#### Prompt 3
[final image prompt]

#### Prompt 4
[optional]

#### Prompt 5
[optional]

### 4. Negative Prompt
[negative prompt block]

### 5. Rationale
Explain briefly why these prompts fit the content, product, and brand guidelines.

## Prompt Writing Standards
- Be specific, not vague
- Prioritize visual clarity
- Keep the product as the hero unless the post clearly requires a lifestyle-first approach
- Reflect the emotional and commercial goal of the post
- Use language suitable for image generation
- Maintain consistency with the uploaded product image
- Avoid adding unsupported claims, features, or visual elements

## Decision Heuristics
Use these rules when deciding the image style:
- If the post is conversion-focused, prioritize clean product-first compositions
- If the post is storytelling-focused, prioritize lifestyle or contextual scenes
- If the post emphasizes aspiration or brand emotion, prioritize cinematic/editorial composition
- If the product image is highly detailed, preserve fidelity and avoid over-stylization
- If brand or visual guideline files conflict with the post tone, prioritize brand consistency while keeping the core message intact

## Failure Handling
If inputs are incomplete:
- If no product image is uploaded, ask for the product image before generating prompts
- If the content is too short or vague, generate prompts using the clearest available angle and state assumptions
- If the brand or visual guidance files are missing, warn that the prompts will be less accurate
- If image references are unavailable, proceed using brand context and visual guideline only

## Example Instruction for Claude
When executing this SOP:
1. Read the pasted post content
2. Inspect the uploaded product image(s)
3. Load `@file:brand_context.md`
4. Load `@file:visual_guideline.md`
4. Load `@file:product_catalog.md`
5. Review relevant assets in `@file:image_reference`
6. Analyze the content and determine the best visual direction
7. Generate 3-5 brand-aligned image prompts
8. Return them in the required output format above