# LLM-Optimized Documentation Format Validation Tests

## format_001: Metadata Completeness

**Category:** Format Validation  
**Prompt:** Analyze the metadata structure for the CompareOptions.NumericOrdering feature. What information is provided and how does it support code generation?  
**Description:** Test recognition and utilization of rich metadata in token-dense format

**Expected Results:**
- **Keywords:** `metadata`, `Framework API`, `System.Globalization`, `.NET 10`, `Stable`, `Assembly`, `Namespace`
- **URLs:** `libraries/numeric-ordering.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## format_002: Performance Characteristics Usage

**Category:** Format Validation  
**Prompt:** What performance implications should I consider when using CompareOptions.NumericOrdering, and how do I optimize for my use case?  
**Description:** Test extraction and application of performance guidance from documentation

**Expected Results:**
- **Keywords:** `performance`, `20-30% slower`, `benchmarks`, `150ns`, `allocations`, `StringComparer.Create`, `reuse`
- **URLs:** `libraries/numeric-ordering.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## format_003: Constraint Matrix Understanding

**Category:** Format Validation  
**Prompt:** What are the limitations and restrictions when using CompareOptions.NumericOrdering? What operations are not supported?  
**Description:** Test extraction of constraint information and limitation awareness

**Expected Results:**
- **Keywords:** `Cannot`, `IndexOf`, `LastIndexOf`, `StartsWith`, `EndsWith`, `Must`, `comparison operations`
- **URLs:** `libraries/numeric-ordering.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## format_004: Integration Points Discovery

**Category:** Format Validation  
**Prompt:** How does CompareOptions.NumericOrdering integrate with other .NET components like LINQ, collections, and sorting operations?  
**Description:** Test discovery of integration patterns and system interactions

**Expected Results:**
- **Keywords:** `StringComparer`, `Array.Sort`, `LINQ`, `OrderBy`, `CultureInfo.CompareInfo`, `integration points`
- **URLs:** `libraries/numeric-ordering.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## format_005: Diagnostic Markers Application

**Category:** Format Validation  
**Prompt:** What warnings, errors, or diagnostic information should I watch for when implementing CompareOptions.NumericOrdering in my application?  
**Description:** Test extraction of diagnostic guidance and troubleshooting information

**Expected Results:**
- **Keywords:** `ArgumentException`, `diagnostic markers`, `performance`, `culture`, `validation`, `flag combinations`
- **URLs:** `libraries/numeric-ordering.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## format_006: CLI Command Surface Analysis

**Category:** Format Validation  
**Prompt:** Analyze the command surface documentation for file-based apps. What verbs, options, and execution patterns are supported?  
**Description:** Test extraction of comprehensive CLI command information

**Expected Results:**
- **Keywords:** `Primary Verbs`, `publish`, `run`, `build`, `Syntax Pattern`, `Global Options`, `dotnet publish`
- **URLs:** `cli/file-based-apps.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## format_007: State Management Understanding

**Category:** Format Validation  
**Prompt:** How does the file-based apps feature manage build state and artifacts? What cleanup and persistence behavior should I expect?  
**Description:** Test understanding of operational behavior from CLI documentation

**Expected Results:**
- **Keywords:** `State Management`, `Build Artifacts`, `temporary build directory`, `automatic cleanup`, `Output Files`
- **URLs:** `cli/file-based-apps.md`
- **HAL Navigation:** Required
- **Source Citation:** Required