# LLM-Optimized Documentation Navigation Tests

## nav_001: Information Graph Discovery

**Category:** Navigation  
**Prompt:** I want to learn about new .NET 10 features for AI development. What areas should I explore and how do I navigate the documentation?  
**Description:** Test entry point discovery and information graph navigation from llms.txt

**Expected Results:**
- **Keywords:** `llms.txt`, `HAL+JSON`, `information graph`, `CLI`, `libraries`, `C#`, `areas`
- **URLs:** `index.json`, `cli/index.json`, `libraries/index.json`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## nav_002: Feature Discovery by Area

**Category:** Navigation  
**Prompt:** What CLI features are documented in this system? List them with brief descriptions.  
**Description:** Test area-based navigation and feature enumeration

**Expected Results:**
- **Keywords:** `CLI features`, `dotnet tool exec`, `file-based apps`, `command aliases`, `shell completion`
- **URLs:** `cli/index.json`, `cli/file-based-apps.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## nav_003: Cross-Reference Following

**Category:** Navigation  
**Prompt:** Find me documentation about string comparison improvements that might be useful for file processing applications.  
**Description:** Test cross-feature discovery and relationship navigation

**Expected Results:**
- **Keywords:** `CompareOptions.NumericOrdering`, `string comparison`, `numeric ordering`, `file processing`
- **URLs:** `libraries/index.json`, `libraries/numeric-ordering.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## nav_004: Token-Dense Format Understanding

**Category:** Navigation  
**Prompt:** Explain the structure and purpose of the token-dense documentation format used in this system.  
**Description:** Test understanding of the documentation methodology and format design

**Expected Results:**
- **Keywords:** `token-dense`, `metadata`, `semantic profile`, `constraint matrix`, `integration points`, `zero-shot`
- **URLs:** `llms.txt`, `index.json`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## nav_005: Testing Methodology Discovery

**Category:** Navigation  
**Prompt:** How should I test whether this documentation system is effective for AI code generation?  
**Description:** Test discovery of testing approach and validation methodology

**Expected Results:**
- **Keywords:** `zero-shot code generation`, `testing methodology`, `compilation success`, `runtime correctness`, `validation`
- **URLs:** `llms.txt`, `testing.md`
- **HAL Navigation:** Required
- **Source Citation:** Required