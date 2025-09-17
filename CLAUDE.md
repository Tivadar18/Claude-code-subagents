# Claude Code Subagents Laboratory

## Project Overview
This laboratory serves as a systematic testing ground for building specialized Claude Code subagents. The primary goal is creating production-ready AI assistants that excel at specific domains and can be orchestrated for complex workflows.

## Claude Code Subagents Best Practices

### Core Principles
1. **Single Responsibility**: Each subagent excels at one specific domain
2. **Context Isolation**: Separate context windows prevent conversation pollution
3. **Tool Restriction**: Limit access to only necessary tools for security and focus
4. **Detailed Prompts**: More guidance = better performance (opposite of main Claude)
5. **Proactive Invocation**: Use "PROACTIVELY" in descriptions for auto-delegation

### Metaprompt Structure
```yaml
---
name: agent-name              # Unique identifier (lowercase-with-hyphens)
description: When to invoke   # Critical for auto-delegation decisions
tools: Tool1, Tool2          # Optional - inherits all if omitted
model: sonnet                # Optional - sonnet/opus/haiku
---
```

### System Prompt Architecture
1. **Role Definition**: Establish expertise level and domain authority
2. **Invocation Protocol**: Clear step-by-step workflow when called
3. **Quality Standards**: Checklists and validation criteria
4. **Domain Knowledge**: Comprehensive coverage of expertise areas
5. **Methodologies**: Professional approaches and best practices
6. **Integration Points**: How to work with other agents

### File Structure
- Store in `.claude/agents/` directory
- Use `.md` files with YAML frontmatter
- Version control for team collaboration
- Use `/agents` command for interactive management

## Development Workflow
1. **Design Phase**: Define single responsibility and use cases
2. **Prompt Engineering**: Create detailed system prompt with examples
3. **Tool Selection**: Limit to necessary tools for focused performance
4. **Testing**: Validate with real-world scenarios and edge cases
5. **Documentation**: Record performance metrics and learnings
6. **Iteration**: Refine based on usage patterns and feedback

## Current Subagents

### Production Ready
1. **market-researcher** - Expert market analysis, consumer insights, competitive intelligence
2. **gtm-strategist** - Comprehensive Go-To-Market strategy design and execution

### Planned Development
- **sales-enablement** - Sales collateral, training, and performance optimization
- **customer-success** - Onboarding automation, health scoring, churn prevention
- **competitive-analyst** - Deep competitive intelligence and positioning
- **content-strategist** - Multi-channel content planning and optimization

## Subagent Organization

### Core GTM Functions
- **Strategic Planning**: market-researcher, gtm-strategist, competitive-analyst
- **Sales Operations**: sales-enablement, lead-qualifier, demo-optimizer
- **Customer Lifecycle**: customer-success, onboarding-specialist, renewal-predictor
- **Content & Messaging**: content-strategist, copywriter, brand-voice-keeper

### Orchestration Patterns
- **Sequential**: market-researcher → gtm-strategist → sales-enablement
- **Parallel**: competitive-analyst + market-researcher → strategy synthesis
- **Conditional**: lead-qualifier → (hot: sales-enablement | warm: nurture-specialist)

### Integration Points
```
Market Research → GTM Strategy → Sales Enablement → Customer Success
     ↓              ↓              ↓                    ↓
Competitive    →   Messaging   →   Content        →   Expansion
Analysis           Strategy        Creation            Strategy
```

## Subagent Quality Standards

### Prompt Quality Checklist
- [ ] Single, clear responsibility defined
- [ ] Step-by-step invocation protocol
- [ ] Domain expertise comprehensively covered
- [ ] Quality standards and validation criteria
- [ ] Integration points with other agents specified
- [ ] Professional methodologies included
- [ ] Success metrics and deliverables defined

### Testing Framework
- **Unit Tests**: Single-task performance validation
- **Integration Tests**: Multi-agent workflow testing
- **Edge Cases**: Handling of incomplete or ambiguous inputs
- **Performance**: Response time and quality metrics
- **Consistency**: Repeated execution reliability

## Usage Patterns

### Triggering Subagents

**Auto-Delegation** (Recommended):
```
"I need market research for the B2B productivity tools space"
# Claude automatically invokes market-researcher subagent
```

**Explicit Invocation**:
```
"Use the gtm-strategist subagent to create a launch plan for our new feature"
# Forces specific subagent usage
```

### Input Templates
Each subagent requires specific context. Always provide:
- Business objectives and constraints
- Target market or audience definition
- Success criteria and timeline
- Available resources and limitations
- Specific deliverables expected

## Advanced Orchestration

### Multi-Agent Workflows
```
# Sequential GTM Planning
1. Use market-researcher to analyze competitive landscape
2. Use gtm-strategist to design go-to-market approach
3. Use sales-enablement to create implementation materials
```

### Parallel Processing
```
# Comprehensive Analysis
Run market-researcher and competitive-analyst subagents in parallel to gather comprehensive market intelligence for our product launch strategy.
```

### Context Handoffs
Subagents can reference previous outputs:
```
"Based on the market research findings above, use gtm-strategist to create our launch strategy"
```

## Development Status
- **Phase 1**: Core Subagents (IN PROGRESS)
  - ✅ market-researcher (Production)
  - ✅ gtm-strategist (Production)
  - 🔄 sales-enablement (Development)
  - 📋 customer-success (Planned)
- **Phase 2**: Workflow Orchestration (ACTIVE)
- **Phase 3**: Performance Optimization (PLANNED)

## Key Learnings

### What Works Well
- **Detailed system prompts** with step-by-step workflows
- **Domain-specific expertise** with comprehensive knowledge coverage
- **Clear tool restrictions** for focused performance
- **Proactive invocation** using "PROACTIVELY" in descriptions
- **Integration protocols** for multi-agent workflows

### Common Pitfalls
- Vague or generic descriptions lead to poor auto-delegation
- Tool overload reduces focus and increases confusion
- Missing quality standards result in inconsistent outputs
- Lack of integration points makes orchestration difficult

### Performance Optimization
- Start with Claude-generated agents, then customize
- Test with real-world scenarios, not just perfect inputs
- Version control prompts for team collaboration
- Monitor usage patterns and refine accordingly

Remember: Specialized beats generalized. Focus beats flexibility.

## Example Meta Prompts

### Market Research Trigger
```
Use the market-researcher subagent to analyze the [MARKET/INDUSTRY] space.

Inputs needed:
• Business Context: [Decision context]
• Target Market: [Geographic/demographic scope]
• Research Questions: [3-5 specific questions]
• Competitive Landscape: [Key players]
• Strategic Goals: [Market entry/expansion/positioning]
• Timeline: [Delivery expectations]
• Constraints: [Budget/resource limitations]
```

### GTM Strategy Trigger
```
Use the gtm-strategist subagent to design a comprehensive go-to-market strategy.

Inputs needed:
• Product/Service: [What you're launching]
• Target Segments: [ICP and buyer personas]
• Business Model: [Revenue and pricing approach]
• Market Position: [Competitive differentiation]
• Resources: [Budget, team, timeline]
• Success Metrics: [KPIs and goals]
• Constraints: [Limitations and requirements]
```