# Copilot for Security - Self-Reflective Benchmarking Manual Testing Guide

## Overview

This guide provides step-by-step instructions for manually evaluating Microsoft Copilot for Security using the self-reflective benchmarking methodology. No programming knowledge is required - just access to Copilot for Security and a spreadsheet application.

**Author**: Abdalla Elzedy (aee189@g.harvard.edu)  
**Required Access**: Microsoft Copilot for Security with appropriate permissions

## Prerequisites

1. **Access Requirements**:
   - Active Copilot for Security license
   - Permissions to query your organization's security data
   - Access to Microsoft Excel or Google Sheets
   - A text editor for preparing long prompts

2. **Preparation**:
   - Download the prompt file [`copilot-manual-prompts.txt`](https://github.com/AbdallaElzedy/Copilot-for-Security/blob/main/copilot-manual-prompts.txt)
   - Create a fresh spreadsheet for tracking results
   - Have a timer/stopwatch ready
   - Prepare a large text file (100K+ characters) for token testing



## Setting Up Your Tracking Spreadsheet

Create a spreadsheet with the following columns:

### Main Tracking Sheet
| Column | Description | Example |
|--------|-------------|---------|
| A: Prompt ID | Identifier from prompt file | DISCOVERY-001 |
| B: Date/Time | When executed | 2024-03-15 10:30 AM |
| C: Response Time | Seconds to complete | 3.5 |
| D: Summary | Brief response summary | Found 128K token limit |
| E: Key Findings | Bullet points of discoveries | • Input limit: 128K tokens |
| F: Limitations Found | Specific constraints | Rate limit: 20 req/min |
| G: Optimizations | Performance tips discovered | Batch queries reduce SCU 40% |
| H: Errors | Any errors encountered | None |
| I: Follow-up Needed | Additional testing required | Test exact boundary |
| J: Confidence | High/Medium/Low | High |
| K: Full Response | Complete response text | [Full text] |

### Summary Sheets to Create

1. **Limitations Summary**
   - Limitation Type
   - Specific Value/Constraint  
   - Validation Status
   - Workaround Available

2. **Optimization Strategies**
   - Strategy Name
   - Expected Improvement
   - Tested (Yes/No)
   - Actual Improvement

3. **Data Sources**
   - Source Name
   - Retention Period
   - Access Method
   - Limitations

## Step-by-Step Execution Instructions

### Phase 1: Discovery (Days 1-2)

#### Day 1 Morning Session (1.5 hours)
1. Open Copilot for Security in your browser
2. Open your tracking spreadsheet
3. Copy prompt `[DISCOVERY-001]` from the prompt file
4. Paste into Copilot for Security
5. Start your timer
6. Submit the prompt
7. When response completes:
   - Stop timer and record time
   - Read response carefully
   - Extract key findings
   - Record in spreadsheet
8. Wait 30 seconds (to avoid rate limits)
9. Repeat for prompts 002-003

#### Day 1 Afternoon Session (1.5 hours)
1. Continue with prompts `[DISCOVERY-004]` and `[DISCOVERY-005]`
2. Review all responses
3. Create initial limitations list
4. Identify areas needing deeper investigation

### Phase 2: Boundary Testing (Days 3-5)

#### Day 3: Token Limit Testing
1. Prepare test documents:
   - 50K character document
   - 100K character document  
   - 150K character document
2. Execute `[BOUNDARY-001]` with normal text
3. Execute `[BOUNDARY-002]` with your large documents
4. Record exact limits discovered

#### Day 4: Rate and Complexity Testing
1. Execute `[BOUNDARY-003]` rapidly (have all 10 queries ready to paste quickly)
2. For `[BOUNDARY-004]`, prepare both simple and complex KQL queries
3. Document any timeouts or errors

#### Day 5: Advanced Boundaries
1. Complete remaining boundary tests
2. Pay special attention to SCU consumption (`[BOUNDARY-007]`)
3. Create boundary summary table

### Phase 3: Optimization Discovery (Days 6-7)

1. Focus on finding performance improvements
2. Test each optimization suggestion
3. Measure actual improvements
4. Document successful strategies

### Phase 4: Validation (Days 8-9)

1. Revisit each discovered limitation
2. Test edge cases
3. Confirm all findings
4. Update confidence levels

### Phase 5: Advanced Discovery (Day 10)

1. Look for undocumented features
2. Try creative approaches
3. Document any surprises

## What to Look For in Responses

### High-Value Discoveries
- ✅ Specific numbers (e.g., "128K tokens", "20 requests/minute")
- ✅ Undocumented features or capabilities
- ✅ Performance optimization techniques
- ✅ Workarounds for limitations
- ✅ Hidden API endpoints or parameters

### Red Flags
- ⚠️ Vague responses without specifics
- ⚠️ Contradictory information between responses
- ⚠️ Claimed capabilities that fail when tested
- ⚠️ Significant performance degradation
- ⚠️ Unexplained errors or timeouts

## How to Document Findings

### For Each Discovery
1. **Record the raw response** - Copy full text to preserve evidence
2. **Extract key facts** - Pull out specific numbers and constraints
3. **Note confidence level** - Based on specificity and consistency
4. **Plan validation** - How will you confirm this finding?
5. **Document workarounds** - Any suggested alternatives

### Daily Summary
At the end of each day:
1. Review all findings
2. Update summary sheets
3. Identify patterns
4. Plan next day's focus areas
5. Export spreadsheet backup

## Testing Best Practices

### Timing Considerations
- **Best testing times**: Early morning or late evening (lower system load)
- **Avoid**: Monday mornings, Friday afternoons (high load)
- **Wait between prompts**: 30 seconds minimum
- **Heavy tests**: Space out by 5 minutes

### Prompt Execution Tips
1. **Copy exactly** - Don't modify prompts initially
2. **One at a time** - Don't batch unless testing batching
3. **Clear context** - Start new sessions for different phases
4. **Document everything** - Even unexpected behaviors

### Error Handling
If you encounter errors:
1. Screenshot the error
2. Wait 5 minutes before retrying
3. Try a simpler version of the prompt
4. Document in the Errors column
5. Move to next prompt if persistent

## Creating Your Final Report

### Report Sections
1. **Executive Summary**
   - Total prompts executed
   - Key limitations discovered
   - Major optimization opportunities
   - Critical recommendations

2. **Detailed Findings**
   - Limitations table with specifics
   - Optimization strategies ranked by impact
   - Data source capabilities matrix
   - Error patterns and mitigations

3. **Validation Results**
   - Confirmed vs unconfirmed findings
   - Discrepancies between claimed and actual
   - Confidence levels for each discovery

4. **Recommendations**
   - Implementation priorities
   - Workaround strategies
   - Optimization quick wins
   - Future testing areas

### Key Metrics to Calculate
- **Discovery Efficiency**: Findings per prompt
- **Validation Rate**: Confirmed/Total discoveries  
- **Optimization Impact**: Average improvement percentage
- **System Reliability**: Success/Total prompts

## Troubleshooting Guide

### Common Issues and Solutions

| Issue | Likely Cause | Solution |
|-------|--------------|----------|
| No response | Rate limited | Wait 5-10 minutes |
| Partial response | Output limit hit | Ask for continuation |
| Vague answers | Prompt too broad | Use more specific version |
| Errors on valid queries | Permission issues | Check access rights |
| Inconsistent results | System updates | Note timestamp, retest |

### When to Escalate
Contact support if:
- Consistent errors on valid queries
- Unable to access claimed data sources
- System completely unresponsive
- Security concerns arise

## Testing Checklist

### Daily Checklist
- [ ] Spreadsheet backup created
- [ ] All responses documented
- [ ] Errors investigated
- [ ] Findings summarized
- [ ] Next day planned

### Phase Completion Checklist
- [ ] All prompts executed
- [ ] Key findings extracted
- [ ] Summary sheet updated
- [ ] Validation items identified
- [ ] Phase report drafted

### Final Checklist
- [ ] All phases completed
- [ ] Findings validated
- [ ] Report generated
- [ ] Data archived
- [ ] Results shared with team

## Expected Outcomes

By completing this evaluation, you should have:

1. **Comprehensive Constraint Map**
   - All system limits documented
   - Validation status for each
   - Workarounds identified

2. **Optimization Playbook**
   - Tested performance improvements
   - SCU consumption patterns
   - Query optimization techniques

3. **Operational Guidelines**
   - Best practices for your organization
   - Do's and don'ts based on findings
   - Training materials for team

4. **Future Roadmap**
   - Additional testing needs
   - Monitoring recommendations
   - Update detection strategy

## Tips for Success

1. **Be Patient** - Some responses take time
2. **Be Thorough** - Don't skip validation
3. **Be Curious** - Try variations if something seems interesting
4. **Be Organized** - Good documentation is crucial
5. **Be Collaborative** - Share findings with your team

## Support and Resources

- **Prompt File**: Use `copilot-manual-prompts.txt` for all prompts
- **Spreadsheet Template**: Create from the structure above
- **Questions**: Document unclear items for vendor follow-up
- **Community**: Share findings with security community (sanitized)

---

Remember: This evaluation will help your organization use Copilot for Security more effectively. Take your time, be thorough, and document everything. Good luck!

