# Agentic-AI
Agentic AI course by Andrew Ng

AGENTIC AI COURSE NOTES by Chetna Agarwal
DeepLearning.AI

### MODULE 1: INTRODUCTION TO AGENTIC WORKFLOWS


1. WELCOME (2 mins)

Key Topics:
- Agentic AI term coined by Andrew Ng as important trend in AI applications
- Despite marketing hype, truly valuable agentic applications growing rapidly
- Best practices for building Agentic AI applications

Applications Covered:
- Customer support agents
- Deep research and insightful reports
- Processing legal documents
- Medical diagnosis suggestions

Critical Success Factor:
- Disciplined development process focused on evals (evaluations) and error analysis
- This differentiates effective builders from less effective ones
- Most important skill in AI today

Key Takeaway: Agentic workflows enable applications that would be impossible otherwise; knowing how to build them opens significant job and software development opportunities.

---

2. WHAT IS AGENTIC AI? (5 mins)

Key Concepts:

Non-Agentic Workflow (Zero-Shot):
- Like asking someone to write an essay from start to finish in one go without backspace
- Single prompt → single output
- LLMs do surprisingly well despite constraints

Agentic Workflow:
- Iterative multi-step process
- Write outline → do web research → write first draft → review/revise → iterate
- Takes longer but delivers much better results

Definition: Agentic AI workflow is a process where an LLM-based app executes multiple steps to complete a task

Workflow Example (Essay Writing):
1. Generate essay outline
2. Determine web research needs
3. Download relevant web pages
4. Write first draft
5. Reflect on what needs revision
6. Optional: Human-in-the-loop review
7. Revise draft
8. Iterate until complete

Course Example - Research Agent:
- Topic: "How do I build a new rocket company to compete with SpaceX"
- Steps: Planning → web search → download pages → synthesize findings → draft outline → editor review → generate comprehensive markdown report
- Produces more thoughtful reports than single-prompt approaches

Applications:
- Legal document compliance
- Healthcare sector research
- Business product research

Key Skill: Breaking down complex tasks into smaller steps for agentic workflows to execute sequentially

Key Takeaway: Agentic workflows vary in autonomy levels - from simple to highly autonomous systems, all incredibly valuable.

---

3. DEGREES OF AUTONOMY (5 mins)

Key Context:
- Debate in AI community about "what is an agent?" was unnecessary
- Andrew Ng introduced term "agentic" as adjective instead of binary classification
- Systems can be agentic to different degrees

Spectrum of Autonomy:

Less Autonomous Agents:
- Fully deterministic sequence of steps
- Predefined workflow by programmer
- Functions/tools hard-coded by engineer
- Example: Essay about black holes → predetermined web search → fetch pages → write essay
- Linear execution path

Notation Convention:
- Red = User input/query
- Gray boxes = LLM calls
- Green boxes = Other software/actions (web search API, code execution)

More Autonomous Agents:
- LLM decides sequence of steps
- LLM chooses which tools to use (web search vs. recent news vs. research papers)
- LLM decides how many resources to fetch
- Can reflect, iterate, fetch more data autonomously
- Non-linear, adaptive execution path

Three Levels:

1. Less Autonomous:
   - All steps predetermined
   - Tool use hard-coded
   - Autonomy mainly in text generation

2. Semi-Autonomous:
   - Makes some decisions
   - Chooses from predefined tools
   - Moderate decision-making capability

3. Highly Autonomous:
   - Decides sequence of steps
   - Can write new functions/create new tools
   - Makes many decisions autonomously
   - Less controllable, more unpredictable
   - Active area of research

Key Insight: Valuable applications exist across entire spectrum - many highly valuable less autonomous agents being built today, while highly autonomous agents remain area of active research.

Key Takeaway: "Agentic" as adjective helps focus on building systems rather than debating definitions; practical value exists at all autonomy levels.

---

4. BENEFITS OF AGENTIC AI (4 mins)

Three Main Benefits:

1. Performance Improvement:
Human Eval Coding Benchmark Results:
- GPT-3.5 non-agentic: 48% accuracy
- GPT-4 non-agentic: 67% accuracy  
- GPT-3.5 + agentic workflow: 95%+ accuracy
- GPT-4 + agentic workflow: Even higher

Key Finding: Agentic workflow improvement > generational model improvement
- Wrapping older model in agentic workflow outperforms newer model without workflow
- Techniques: reflection, iteration, code improvement

2. Parallelization:
- Can execute multiple tasks simultaneously
- Example: Essay on black holes
  * 3 LLMs generate web search terms in parallel
  * Download 9 web pages simultaneously (vs. human sequential reading)
  * Aggregate all findings for final essay
- Faster than sequential human process despite multi-step workflow

3. Modularity:
- Swap components easily:
  * Different web search engines (Google, Bing, DuckDuckGo, Tavily, u.com)
  * Add news search engines for recent breakthroughs
  * Try different LLM providers for different steps
- Optimize each component independently
- Mix best-of-breed tools

Key Takeaway: Agentic workflows enable previously impossible tasks, parallelize human-sequential work, and allow modular optimization.

---

5. AGENTIC AI APPLICATIONS (7 mins)

Application Examples by Difficulty:

EASIER APPLICATIONS (Clear Step-by-Step Process):

1. Invoice Processing:
   Workflow: PDF → text conversion API → LLM identifies document type → extract required fields (biller, biller address, amount due, due date) → update database
   Why easier: Clear process, text-only, known steps

2. Customer Order Inquiry Agent:
   Workflow: Extract key info from email → look up customer records → draft response → human review → send
   Steps: Email → LLM extracts order details → query orders database → LLM drafts response → request human review tool
   Currently: Being deployed in many businesses

MODERATE DIFFICULTY:

3. General Customer Service Agent:
   Challenge: Must handle varied queries (inventory checks, returns, policy questions)
   Example queries:
   - "Do you have black/blue jeans?" → multiple API calls to inventory database
   - "Return beach towel" → verify purchase → check return policy (30 days, unused) → issue return packing slip → update database
   Difficulty: LLM must plan sequence of steps; steps not known ahead of time

HARDEST APPLICATIONS:

4. Computer Use Agents:
   Example: Check seat availability on United Airlines flights SFO to DC
   Capabilities:
   - Navigate web browsers autonomously
   - Read web pages
   - Click elements
   - Fill text fields
   - Reason over page content
   - Adapt to issues (switched to Google Flights when United site had trouble)
   Current State: Exciting cutting-edge research; not yet reliable for mission-critical applications
   Challenges: Slow-loading pages, complex page parsing, reliability issues

Difficulty Spectrum:

Easier → Harder:
- Clear SOP (Standard Operating Procedure) available
- Text-only assets (LLMs excel at text)
- Known steps ahead of time
  
  →
  
- Steps must be planned/solved as you go
- Multi-modal inputs (sound, vision, audio)
- No predefined procedure

Key Skill: Task decomposition - breaking complex workflows into discrete executable steps

Key Takeaway: Start with clear-process, text-based applications; gradually build toward more autonomous, multi-modal, planning-required tasks.

---

6. TASK DECOMPOSITION: IDENTIFYING STEPS IN A WORKFLOW (8 mins)

Core Concept: Break complex tasks into discrete steps executable by LLMs or tools

Key Question: Can each step be done by:
- An LLM?
- Short piece of code?
- Function call?
- A tool?

If NO: "How would I as a human do this step?" → Decompose further

Example 1: Research Agent (Essay Writing)

Iteration 1 (Direct Generation):
- Single step: Write essay
- Problem: Surface-level, obvious facts only

Iteration 2 (3 Steps):
1. Write essay outline (LLM capable)
2. Search web (LLM generates search terms)
3. Write essay based on results (LLM capable)
- Problem: Disjointed, inconsistent across sections

Iteration 3 (5 Steps - Final):
1. Write essay outline
2. Search web
3. Write FIRST DRAFT
4. Consider what needs revision (LLM critique)
5. Revise draft
- Mirrors human writing process

Example 2: Customer Order Inquiry Agent

Steps:
1. Extract key information (who, what order, order number) - LLM
2. Query orders database - LLM + database function call
3. Draft and send response - LLM + email API

Example 3: Invoice Processing

Steps:
1. Extract required fields (biller, address, due date, amount) - LLM
2. Update database - LLM + database update function

Building Blocks Available:

1. AI Models:
   - Large Language Models (text generation, extraction, decision-making)
   - Multimodal models (images, audio)
   - Specialized models (PDF-to-text, text-to-speech, image analysis)

2. Software Tools:
   - APIs (web search, weather, email, calendar)
   - Information retrieval (RAG, database queries)
   - Code execution

3. Functions:
   - Database operations
   - File operations
   - External service integrations

Iterative Improvement Process:
1. Build initial task decomposition
2. Implement and test
3. Evaluate results
4. Identify issues
5. Further decompose problematic steps
6. Repeat until performance satisfactory

Key Takeaway: Effective agentic workflow design requires iterative task decomposition, matching steps to available building blocks (LLMs, tools, APIs), and continuous refinement based on evaluation.

---

7. EVALUATION AGENTIC AI (EVALS) (5 mins)

Core Insight: Ability to drive disciplined evaluation process = biggest predictor of success in building agentic workflows

Best Practice Approach:
1. Build first, examine later (don't anticipate problems in advance)
2. Manually examine outputs
3. Identify issues
4. Create evals to track specific problems
5. Iterate to improve

Example Problem: Competitor Mentions

Unexpected behavior:
- "I'm glad you shopped with us. We're much better than our competitor, ComproCo."
- "Unlike RivalCo, we make returns easy."

Solution:
- Hard to anticipate in advance
- Discovered through manual output examination
- Created eval: Search for competitor names (ComproCo, RivalCo, TheOtherCo)
- Track frequency as fraction of overall responses

Objective vs. Subjective Metrics:

Objective (Code-Based):
- Competitor mentions (yes/no)
- Clear binary criteria
- Write code to check

Subjective (LLM-as-Judge):
- Essay quality (1-5 scale)
- Harder to code
- Use LLM to evaluate
- Example: "Assign following essay quality score between 1-5"
- Caveat: LLMs not great at 1-5 scale ratings (better techniques taught later)

Two Major Eval Types (Detailed in Module 4):

1. End-to-End Evals:
   - Measure entire agent output quality

2. Component-Level Evals:
   - Measure single step output quality
   - Useful for debugging specific parts

Error Analysis:
- Examine intermediate outputs ("traces")
- Read through every step
- Spot improvement opportunities
- Key skill for effective development

Key Takeaway: Disciplined eval process differentiates effective builders; build first, evaluate systematically, iterate based on data.

---

8. AGENTIC DESIGN PATTERNS (7 mins)

Four Key Design Patterns:

1. REFLECTION
Concept: LLM examines and critiques its own outputs, iterates to improve

Process:
- Generate initial output (e.g., code)
- Prompt: "Check this code for correctness, style, efficiency; give constructive criticism"
- LLM critiques own work
- Revise based on critique
- Can add external feedback (run code, see errors)
- Iterate to v2, v3, etc.

Variation - Multi-Agent Reflection:
- Separate "Critique Agent" (LLM prompted with critique role)
- Two agents go back and forth
- Each has specific persona

Result: Performance bump (not 100% reliable but often helpful)

2. TOOL USE
Concept: LLMs call functions to accomplish tasks

Examples:
- Web search: "What's the best coffee maker according to reviewers?" → search internet
- Code execution: Math calculations with compound interest
- Data analysis
- Database queries
- Productivity apps (email, calendar)
- Image processing
- And much more

Key: LLM decides WHICH tools to use (which functions to call)

3. PLANNING
Concept: LLM decides sequence of actions (not hard-coded by developer)

Example (HuggingGPT paper):
Task: "Generate image of girl reading book in same pose as boy in image; describe in your voice"

LLM plans:
1. Use pose determination model (find boy's pose)
2. Pose-to-image generation (generate girl)
3. Image-to-text
4. Text-to-speech

Characteristics:
- LLM determines sequence of API calls
- Harder to control
- More experimental
- Can give delightful results

4. MULTI-AGENT COLLABORATION
Concept: Multiple specialized agents work together (like human teams)

Example 1 - ChatDev (Chen Qian et al.):
Roles: CEO, Programmer, Tester, Designer, etc.
Collaborate as virtual software company

Example 2 - Marketing Brochure:
Agents:
- Researcher (online research)
- Marketer (write text)
- Editor (polish text)
Work together on task

Characteristics:
- More difficult to control
- Unpredictable agent behavior
- Research shows better outcomes for complex tasks
- Applications: Biographies, chess moves, complex decisions

Key Takeaway: Four patterns (Reflection, Tool Use, Planning, Multi-Agent) are fundamental building blocks; combine them to create powerful agentic workflows.

---

MODULE 1 COMPLETE

===========================================

MODULE 2: REFLECTION DESIGN PATTERN
===========================================

1. REFLECTION TO IMPROVE OUTPUTS OF A TASK (3 mins)

Core Concept: LLM examines and improves its own outputs through self-critique

Basic Workflow:
- Write code for task X → LLM generates code V1
- Pass code back to LLM with critique prompt
- LLM checks for bugs, writes improved V2

Key Insight: Same process applies to other output types (not just code)
- Essays, reports, structured data, emails, etc.

Reflection Pattern Value:
- Iterative improvement through self-review
- Can incorporate external feedback (code execution results, data validation)
- Similar to human revision process

Key Takeaway: Reflection pattern enables LLMs to iteratively improve outputs across diverse tasks beyond coding.

---

2. WHY NOT JUST DIRECT GENERATION? (5 mins)

Direct Generation (Zero-Shot Prompting):
- Single prompt → single output
- No examples provided
- Example: "Write essay about black holes" → generate text
- Example: "Write Python function for compound interest" → generate code

Terminology:
- Zero-shot: 0 examples in prompt
- One-shot: 1 example input-output pair
- Few-shot: Multiple examples
- Two-shot: 2 examples

Research Evidence (Madaan et al. paper):
- Multiple studies show reflection improves performance
- Tested across various tasks and models (GPT-3.5, GPT-4)
- Chart shows: Dark bars (with reflection) consistently higher than light bars (zero-shot)
- Performance varies by application

Use Cases Where Reflection Helps:

1. Structured Data:
   - HTML tables (incorrect formatting)
   - Complex JSON (nested structures with bugs)
   - Reflection validates structure

2. Sequential Instructions:
   - Example: "How to brew perfect cup of tea"
   - LLM may miss steps
   - Reflection checks coherence and completeness

3. Domain Names (Real project at AI Fund):
   - Check: Easy to pronounce?
   - Check: Unintended negative meanings in any language?
   - Check: Problematic connotations?
   - Used for startup naming

Reflection Prompt Examples:

Example 1 - Domain Names:
"Review domain names suggested. Check if each name is:
- Easy to pronounce
- Might mean something negative in English or other languages
Output short list of only names satisfying these criteria."

Example 2 - Email Improvement:
"Review email first draft:
- Check tone
- Verify all facts/dates/promises are accurate (based on context provided)
- Write next draft based on problems found"

Tips for Writing Reflection Prompts:
1. Clearly indicate: "review" or "reflect" on first draft
2. Specify clear criteria (tone, facts, pronunciation, meanings)
3. Guide LLM on what matters most

Learning Best Practice:
- Read prompts written by others
- Download open-source software
- Find and study well-crafted prompts
- Learn from effective implementations

Key Takeaway: Reflection consistently outperforms direct generation across tasks; effective reflection prompts specify clear review criteria.

---



Video 3: Chart Generation Workflow (3 mins)

Multimodal Reflection:
- Uses multimodal LLM (vision capability) to evaluate chart quality
- LLM reviews generated chart image and provides feedback
- Reflection process improves chart aesthetics, readability, clarity
- Agent can iterate on chart based on visual feedback

Implementation:
- Generate initial chart from data
- Multimodal LLM critiques chart appearance
- Refine chart based on feedback
- Can use different models for generation vs reflection (e.g., Claude for chart generation, GPT-4 Vision for reflection)

Key Takeaway: Multimodal LLMs enable reflection on visual outputs like charts; using different models for generation and reflection can improve results.

---

Video 4: Ungraded Lab - Chart Generation (15 mins)

Practical Implementation:
- Hands-on lab demonstrating chart generation with reflection
- Uses Python libraries to create visualizations
- Implements reflection loop for chart improvement
- Shows iterative refinement process

Process:
- Define data requirements and chart type
- Generate initial chart
- Apply multimodal reflection
- Iterate based on feedback
- Produce final polished chart

Key Takeaway: Lab provides practical experience with implementing reflection pattern for chart generation tasks.

---

Video 5: Evaluating the Impact of Reflection (8 mins)

SQL Generation Example:
- Task: Generate SQL queries from natural language
- Without reflection: 87% accuracy
- With reflection: 95% accuracy
- Demonstrates measurable improvement from reflection pattern

Evaluation Methods:
- LLM-as-judge: Use LLM to evaluate output quality
- Rubric-based scoring: Define clear criteria for assessment
- Automated testing: Check correctness against expected results
- Human evaluation: Expert review for subjective quality

Reflection Benefits:
- Catches errors before final output
- Improves accuracy significantly
- Reduces need for human review
- Cost-effective despite extra LLM calls

Key Takeaway: Reflection pattern shows measurable performance gains (87% → 95%); proper evaluation methods are essential to quantify improvement.

---

Video 6: Using External Feedback (4 mins)

Performance Plateau:
- Pure LLM reflection eventually hits ceiling
- External feedback breaks through performance plateau
- Combines LLM reasoning with external verification

External Feedback Sources:
- Pattern matching: Regex validation, format checking
- Fact-checking: Database lookups, API calls, web search
- Word counting: Exact length requirements
- Code execution: Running tests, checking syntax
- External validators: Specialized tools for domain-specific checks

Combining Approaches:
- LLM reflection for reasoning and improvement
- External tools for objective verification
- Hybrid approach more reliable than either alone
- External feedback provides ground truth

Key Takeaway: Reflection with external feedback is more powerful than reflection alone; external tools provide objective verification that LLMs cannot match.

---


=== MODULE 3: TOOL USE ===

Video 1: What are Tools? (6 mins)

Tool Use Basics:
- Tools are functions that LLMs can request to be called
- LLMs don't call tools directly - they request tool execution
- Enables LLMs to do much more than just generate text
- Example: getCurrentTime() function

How Tool Use Works:
1. User provides input prompt
2. LLM examines available tools
3. LLM decides whether to call a tool
4. If yes, tool executes and returns value
5. Value fed back to LLM
6. LLM generates final output

LLM Autonomy:
- LLM decides when to use tools (not hard-coded)
- Can skip tool use if not needed for query
- Dashed box notation indicates tool availability

Common Tool Use Cases:
- Web search for restaurant recommendations
- Database queries for retail/customer data
- Interest calculations and math operations
- Code execution for complex calculations

Multiple Tools:
- LLMs can access multiple tools simultaneously
- Example: Calendar assistant with checkCalendar, makeAppointment, deleteAppointment
- LLM chains tool calls to complete complex tasks
- Sequential tool execution based on previous results

Key Takeaway: Tool use dramatically expands LLM capabilities by giving them ability to take actions, gather information, and interact with external systems.

---

Video 2: Creating a Tool (5 mins)

Historical Approach (pre-trained tool use):
- Tell LLM to output "FUNCTION: functionName" when it wants tool called
- Developer writes code to detect this pattern
- Extract function name and arguments
- Execute function manually
- Return result to LLM
- LLM generates final response

Function with Arguments:
- getCurrentTime(timezone) example
- LLM outputs: "FUNCTION: getCurrentTime Pacific/Auckland"
- Developer parses function name and arguments
- Executes function with LLM-provided arguments
- Returns result to LLM

Tool Use Process Summary:
1. Provide tool to LLM (implement function + tell LLM it's available)
2. LLM generates specific output indicating tool call request
3. Developer calls function and gets output
4. Output fed back to LLM
5. LLM decides next action (could call another tool)

Key Takeaway: Modern LLMs are trained natively to use tools with better syntax than old "FUNCTION:" approach; understanding the process helps with debugging.

---

Video 3: Tool Syntax (5 mins)

Modern Tool Implementation:
- Use AISuite open-source library (or similar)
- Similar to OpenAI syntax
- Supports multiple LLM providers

Code Structure:
- response = client.chat.completions.create()
- model="openai:gpt-4o"
- messages=[messages]
- tools=[get_current_time]
- max_turns=5

Max Turns Parameter:
- Ceiling on sequential tool calls
- Prevents infinite loops
- Usually set to 5
- Rarely hit in practice

JSON Schema Generation:
- AISuite automatically creates JSON schema for tools
- Pulls function name
- Extracts description from docstring
- Identifies parameters and types
- LLM uses schema to decide when/how to call tool

Complex Functions:
- getCurrentTime(timezone) example
- Schema includes parameter descriptions
- LLM knows valid arguments (e.g., "America/New_York")
- Single function call handles tool execution and response

Key Takeaway: Modern syntax with libraries like AISuite automates tool description and execution; docstrings are crucial for LLM understanding.

---

Video 4: Code Execution (5 mins)

Code as Universal Tool:
- Instead of creating separate tools for every operation
- Let LLM write and execute code
- More flexible than individual functions
- Example: Don't need separate square root, exponentiation tools

Implementation:
- Prompt: "Write code to solve user's query. Return as Python code delimited with <execute_python> tags"
- LLM generates code
- Use regex to extract code from tags
- Execute code using Python's exec() or sandbox
- Return output to LLM
- LLM formats final answer

Reflection for Code:
- If code execution fails, pass error to LLM
- LLM can reflect and revise code
- Try 1-2 more times for accuracy
- Significantly improves success rate

Security Concerns:
- Arbitrary code execution has risks
- Real example: Agentic coder deleted *.py files
- Risk is relatively low per line of code
- Many developers execute without extensive checking

Best Practice - Sandboxing:
- Run code in isolated environment
- Docker containers
- E2B lightweight sandbox
- Reduces risk of data loss/leakage
- Prevents system damage

Importance:
- Many LLM trainers optimize specifically for code execution
- Extremely powerful tool for LLM applications
- Enables complex calculations and operations

Key Takeaway: Code execution is a "meta-tool" that gives LLMs extreme flexibility; use sandboxing for safety in production.

---

Video 5: MCP - Model Context Protocol (5 mins)

Problem MCP Solves:
- Developers were building custom wrappers for each tool
- M applications × N tools = M×N total work
- Duplicated effort across teams
- Example: Every app reimplementing Slack, GitHub, Google Drive integrations

MCP Solution:
- Standard protocol for LLM-tool integration
- Total work reduced to M + N
- Proposed by Anthropic, adopted widely
- Growing ecosystem of clients and servers

MCP Components:
- Clients: Applications that want access to tools/data
- Servers: Software wrappers providing tools/resources
- Resources: Data sources (Slack, GitHub, Google Drive, Postgres)
- Tools: Functions that take actions

MCP Example:
- Cloud desktop app as MCP client
- GitHub MCP server provides tools
- Query: "Summarize readme.md from GitHub repo"
- MCP server fetches file
- LLM generates summary
- Query: "Latest pull requests"
- MCP server lists PRs
- LLM summarizes results

Growing Ecosystem:
- Rapidly expanding list of MCP clients
- Many MCP servers available
- Build your own MCP client or server
- DeepLearning.AI has dedicated MCP course

Key Takeaway: MCP standardizes tool integration, reducing duplicated effort; enables access to growing ecosystem of tools and data sources.

---


=== MODULE 4: PRACTICAL TIPS FOR BUILDING AGENTIC AI ===

Video 1: Evaluations (Evals) (15 mins)

Build-Test-Improve Cycle:
- Build quick prototype first, then evaluate
- Avoid over-theorizing - build and test quickly
- Look at outputs to discover errors
- Put evals in place to track progress

Invoice Processing Example:
- Task: Extract 4 fields (biller, address, amount, due date)
- Manual review of 10-20 invoices
- Found: Dates frequently mixed up
- Solution: Create eval to measure date extraction accuracy
- Use standard format (YYYY-MM-DD) for comparison
- Regex pattern matching to test correctness

Marketing Copy Example:
- Task: Write Instagram captions ≤10 words
- Found: Length guideline violated
- Eval: Measure word count programmatically
- No per-example ground truth (same 10-word limit for all)

Research Agent Example:
- Found: Missing important discussion points
- Create gold standard talking points per topic
- Use LLM-as-judge to count points mentioned
- Return JSON with score and explanation

Two Axes of Evaluation:
1. How to evaluate: Code (objective) vs LLM-as-judge (subjective)
2. Ground truth: Per-example vs universal target

Four Eval Quadrants:
- Code + per-example: Invoice date extraction
- Code + no per-example: Marketing copy length
- LLM-as-judge + per-example: Research talking points
- LLM-as-judge + no per-example: Chart rubric grading

Best Practices:
- Start with 10-20 examples (quick and dirty is fine)
- Iterate on evals over time
- Blend metrics with human review
- Add examples when eval doesn't match judgment
- Focus on areas worse than expert human performance

Key Takeaway: End-to-end evals track overall system performance; build quick evals early and improve them iteratively.

---

Video 2: Error Analysis and Prioritizing Next Steps (9 mins)

Why Error Analysis Matters:
- Agentic workflows have many components
- Any component could cause problems
- Going by gut often wastes time
- Systematic analysis reveals highest-impact fixes

Trace Analysis:
- Trace: Complete set of intermediate outputs
- Span: Output of single step
- Examine each step's output quality
- Compare to what human expert would produce

Research Agent Example:
- Problem: Missing key points in essays
- Potential causes:
  * Poor search terms
  * Bad web search engine
  * Wrong articles selected
  * LLM ignoring fetched content

Systematic Approach:
1. Focus on unsatisfactory examples only
2. Build spreadsheet to track errors
3. Examine each component's output
4. Count error frequency per component
5. Prioritize components with most errors + clear improvement path

Spreadsheet Method:
- Columns: Each workflow step
- Rows: Test queries
- Mark errors where output << expert quality
- Don't blame component if inputs were already bad
- Calculate error percentages

Example Results:
- Search terms errors: 5%
- Search results errors: 45%
- Action: Focus on improving web search engine

Key Takeaway: Error analysis prevents wasted effort; examine traces systematically and use data to prioritize component improvements.

---

Video 3: Component-Level Evaluations (3 mins)

Why Component Evals:
- End-to-end evals are expensive to run
- Noise from other components obscures improvements
- Faster iteration on single component
- Clearer signal for specific errors

Web Search Example:
- Create gold standard web resources per query
- Measure overlap with search results
- Use F1 score or similar metrics
- Quickly test different:
  * Search engines (Google, Bing, DuckDuckGo)
  * Number of results
  * Date ranges

Benefits:
- Avoid full workflow reruns
- Faster hyperparameter tuning
- Team can optimize independently
- Still run end-to-end eval before finishing

Key Takeaway: Component-level evals enable faster iteration on individual components before validating with end-to-end evals.

---

Video 4-8: Additional Module 4 Topics (Summarized)

How to Address Problems:
- Improve prompts with better instructions
- Add examples (few-shot learning)
- Change system design/workflow
- Switch models or providers
- Add reflection loops
- Incorporate external feedback

Latency & Cost Optimization:
- Use faster/cheaper models where possible
- Parallel execution of independent steps
- Cache frequent queries
- Reduce token usage in prompts
- Stream responses for better UX

Development Process Summary:
1. Build quick prototype
2. Run end-to-end evals
3. Do error analysis
4. Build component evals
5. Iterate improvements
6. Validate with end-to-end evals
7. Repeat cycle

---

=== MODULE 5: PATTERNS FOR HIGHLY AUTONOMOUS AGENTS ===

Video 1: Planning Workflows (7 mins)

Planning Pattern:
- LLM generates multi-step plan
- LLM executes each step sequentially
- Don't hard-code workflow sequence
- Agent decides steps dynamically

Customer Service Example:
- Query: "Round sunglasses under $100?"
- Tools: getItemDescription, checkInventory, getItemPrice, processReturn, etc.
- Prompt: "Return step-by-step plan"
- Plan generated:
  1. Get item descriptions (find round ones)
  2. Check inventory (in stock?)
  3. Get item price (under $100?)

Execution Process:
- Step 1 text → LLM → calls getItemDescription
- Step 1 output + Step 2 text → LLM → calls checkInventory
- Step 2 output + Step 3 text → LLM → calls getItemPrice
- Final output → Generate user response

Email Assistant Example:
- Query: "Reply to Bob's NYC dinner invite, confirm attendance, archive"
- Plan:
  1. Search email from Bob mentioning dinner/NYC
  2. Send confirmation email
  3. Move to archive

Use Cases:
- Agentic coding systems (works very well)
- Customer service automation
- Email management
- Complex multi-tool workflows

Challenges:
- Hard to control runtime behavior
- Unpredictable plans
- Still experimental outside coding

Key Takeaway: Planning pattern enables flexible, dynamic workflows; LLM decides sequence based on task requirements.

---

Video 2: Creating and Executing LLM Plans (2 mins)

Plan Structure:
- Detailed step-by-step instructions
- Not just one-line descriptions
- Includes context and parameters
- JSON or structured format

Execution Details:
- Each step fed to LLM with:
  * User query
  * Available tools
  * Previous step outputs
  * Current step instructions
- LLM selects appropriate tool
- Tool executes and returns result
- Result passed to next step

Key Takeaway: Plans are detailed instructions executed sequentially with full context at each step.

---

Video 3: Planning with Code Execution (7 mins)

Code as Planning Tool:
- LLM writes code to implement plan
- Code execution provides flexibility
- Can handle complex logic and loops
- More powerful than simple tool calls

Customer Service with Code:
- Write Python code to query database
- Execute code to get results
- Use results to generate response
- Code can handle complex conditionals

Advantages:
- Express complex logic clearly
- Reusable functions
- Better error handling
- More predictable behavior

Key Takeaway: Combining planning with code execution creates highly flexible agents.

---

Video 4: Multi-Agent Workflows (9 mins)

Multi-Agent Pattern:
- Multiple specialized agents
- Each agent has specific role
- Agents collaborate to complete task
- Coordination via manager or protocol

Market Research Team Example:
- Researcher agent: Finds information
- Analyst agent: Processes data
- Writer agent: Creates report
- Manager agent: Coordinates workflow

Benefits:
- Specialization improves quality
- Parallel execution possible
- Easier to debug individual agents
- More maintainable

Coordination Approaches:
- Centralized (manager delegates)
- Decentralized (agents communicate)
- Sequential (pipeline)
- Parallel (concurrent execution)

Key Takeaway: Multi-agent systems enable specialization and better organization of complex workflows.

---

Video 5: Communication Patterns (4 mins)

Common Patterns:

1. Sequential:
- Agent A → Agent B → Agent C
- Linear handoff
- Simple coordination

2. Hub-and-Spoke:
- Manager agent coordinates
- Delegates to specialist agents
- Collects and synthesizes results

3. Fully Connected:
- Agents communicate directly
- More flexible
- Complex coordination

4. Hierarchical:
- Multiple manager layers
- Scales to large systems

Message Passing:
- Shared context/memory
- Explicit message queue
- Tool calls between agents

Key Takeaway: Choose communication pattern based on task complexity and coordination needs.

---

