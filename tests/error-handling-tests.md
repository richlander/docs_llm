# LLM-Optimized Documentation Error Handling Tests

## error_001: Non-Existent Feature Request

**Category:** Error Handling  
**Prompt:** I need documentation for OrderedDictionary enhancements in .NET 10. Can you help me find it?  
**Description:** Test handling of requests for features not yet documented in the system

**Expected Results:**
- **Keywords:** `not found`, `available features`, `CompareOptions.NumericOrdering`, `file-based apps`, `documentation areas`
- **URLs:** `index.json`, `libraries/index.json`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## error_002: Ambiguous Feature Query

**Category:** Error Handling  
**Prompt:** How do I use the new comparison features in .NET 10?  
**Description:** Test handling of vague queries and guidance toward specific features

**Expected Results:**
- **Keywords:** `comparison`, `CompareOptions.NumericOrdering`, `string comparison`, `specific feature`, `clarification`
- **URLs:** `libraries/index.json`, `libraries/numeric-ordering.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## error_003: Wrong Area Navigation

**Category:** Error Handling  
**Prompt:** I'm looking for C# language features in .NET 10. What's available?  
**Description:** Test handling of requests for areas not yet populated with content

**Expected Results:**
- **Keywords:** `C# features`, `not yet documented`, `available areas`, `CLI`, `libraries`, `coming soon`
- **URLs:** `index.json`, `csharp/index.json`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## error_004: Invalid Usage Pattern Request

**Category:** Error Handling  
**Prompt:** Show me how to use CompareOptions.NumericOrdering with IndexOf for substring searching.  
**Description:** Test identification of invalid usage patterns from constraint documentation

**Expected Results:**
- **Keywords:** `Cannot`, `IndexOf`, `not supported`, `comparison operations only`, `constraints`, `limitations`
- **URLs:** `libraries/numeric-ordering.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## error_005: Missing Prerequisite Information

**Category:** Error Handling  
**Prompt:** How do I use file-based apps without having .NET installed?  
**Description:** Test identification of missing prerequisites and dependency guidance

**Expected Results:**
- **Keywords:** `Dependencies`, `.NET SDK 10+`, `required`, `prerequisites`, `installation`
- **URLs:** `cli/file-based-apps.md`
- **HAL Navigation:** Required
- **Source Citation:** Required

---

## error_006: Version Mismatch Query

**Category:** Error Handling  
**Prompt:** Can I use CompareOptions.NumericOrdering in .NET 8?  
**Description:** Test handling of version compatibility questions

**Expected Results:**
- **Keywords:** `Introduced`, `.NET 10`, `not available`, `version requirement`, `compatibility`
- **URLs:** `libraries/numeric-ordering.md`
- **HAL Navigation:** Required
- **Source Citation:** Required