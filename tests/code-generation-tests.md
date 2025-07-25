# LLM-Optimized Documentation Code Generation Tests

## code_gen_001: Numeric String Sorting

**Category:** Code Generation  
**Prompt:** Write a complete C# method that sorts an array of file names with numbers using the new numeric ordering feature in .NET 10. Include error handling and demonstrate both case-sensitive and case-insensitive variants.  
**Description:** Test zero-shot code generation for CompareOptions.NumericOrdering with comprehensive usage patterns

**Expected Results:**
- **Keywords:** `CompareOptions.NumericOrdering`, `StringComparer.Create`, `Array.Sort`, `CultureInfo`, `using System.Globalization`, `try-catch`, `IgnoreCase`
- **URLs:** `libraries/index.json`, `libraries/numeric-ordering.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## code_gen_002: File-Based App with Dependencies

**Category:** Code Generation  
**Prompt:** Create a complete file-based C# application that references an external project and publishes to a native executable. Show both the source code and the command to publish it.  
**Description:** Test zero-shot code generation for file-based apps with project references and publishing

**Expected Results:**
- **Keywords:** `#:project`, `dotnet publish`, `native executable`, `#:property PublishAot`, `using`, `System.AppContext.GetData`
- **URLs:** `cli/index.json`, `cli/file-based-apps.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## code_gen_003: Error Handling Patterns

**Category:** Code Generation  
**Prompt:** Generate code that demonstrates proper error handling for both the numeric ordering feature and file-based app publishing, including specific exception types and recovery strategies.  
**Description:** Test understanding of error scenarios and diagnostic guidance from token-dense documentation

**Expected Results:**
- **Keywords:** `ArgumentException`, `CompileException`, `try-catch`, `error handling`, `exception types`, `recovery`
- **URLs:** `libraries/numeric-ordering.md`, `cli/file-based-apps.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## code_gen_004: Performance-Optimized Usage

**Category:** Code Generation  
**Prompt:** Write C# code that uses CompareOptions.NumericOrdering in a performance-critical scenario, incorporating the performance guidance from the documentation to minimize allocations and optimize for repeated comparisons.  
**Description:** Test integration of performance characteristics and optimization patterns from token-dense documentation

**Expected Results:**
- **Keywords:** `StringComparer.Create`, `reuse`, `performance`, `allocations`, `benchmarks`, `CultureInfo.InvariantCulture`
- **URLs:** `libraries/numeric-ordering.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## code_gen_005: Cross-Feature Integration

**Category:** Code Generation  
**Prompt:** Create a file-based application that uses numeric ordering to sort configuration files, demonstrating integration between CLI and library features with proper error handling and logging.  
**Description:** Test ability to combine multiple features from different areas using cross-references in documentation

**Expected Results:**
- **Keywords:** `file-based`, `numeric ordering`, `configuration`, `integration`, `error handling`, `logging`
- **URLs:** `index.json`, `cli/file-based-apps.md`, `libraries/numeric-ordering.md`
- **HAL Navigation:** Required
- **Source Citation:** Required