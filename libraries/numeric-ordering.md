# Feature: CompareOptions.NumericOrdering

## Metadata
- **Type**: Framework API
- **Category**: Globalization/String Comparison
- **Introduced**: .NET 10
- **Status**: Stable
- **Assembly**: System.Runtime.dll
- **Namespace**: System.Globalization
- **Package**: Built-in (.NET 10+)

## API Surface
**Primary Types**: CompareOptions enum
**Entry Points**: CompareOptions.NumericOrdering flag
**Configuration**: Used with StringComparison, CultureInfo.CompareInfo methods
**Performance**: Parsing overhead during comparison, optimized for repeated comparisons

## Capability Matrix
**Numeric Comparison**: String representations of numbers compared by numeric value
**Lexicographic Fallback**: Non-numeric portions compared lexicographically
**Leading Zeros**: "2" and "02" treated as numerically equal
**Mixed Content**: Combines numeric and text comparison in single string

## Type System Integration
**Supported Types**: string, ReadOnlySpan<char>, Span<char>
**Culture Sensitivity**: Respects current culture's number formatting
**Nullable Reference Types**: Standard string nullability rules apply
**Generic Constraints**: Works with IComparable<string> patterns

## Configuration Vectors
**Comparison Methods**: String.Compare, CultureInfo.CompareInfo.Compare, Array.Sort
**Combination Flags**: Can combine with IgnoreCase, IgnoreSymbols, etc.
**Culture Context**: Uses current culture's numeric parsing rules
**Case Sensitivity**: Separate from numeric ordering, controlled by IgnoreCase

## Performance Characteristics
**Throughput**: ~20-30% slower than lexicographic comparison for pure numeric strings
**Memory**: No additional allocations during comparison
**Parsing Overhead**: Number detection and parsing per comparison operation
**Benchmarks**: "10" vs "2" comparison ~150ns vs ~50ns lexicographic

## Extension Points
**Custom Comparers**: IComparer<string> implementations using CompareOptions
**LINQ Integration**: OrderBy, ThenBy with StringComparer.Create
**Collection Sorting**: Array.Sort, List<T>.Sort with custom comparers
**Search Operations**: Array.BinarySearch, SortedList with numeric ordering

## Error Handling
**ArgumentException**: Invalid CompareOptions combination
**CultureNotFoundException**: Invalid culture for comparison context
**Overflow**: Very large numbers may fall back to lexicographic comparison
**Null Handling**: Standard null-first ordering in comparisons

## Interop Boundaries
**Legacy Sorting**: Migration from custom numeric string comparers
**Database Integration**: Matches SQL Server ISNUMERIC-based ordering
**File System**: Natural sorting for file names with numbers
**Version Comparisons**: Semantic versioning component comparison

## AOT Compatibility
**Source Generators**: No special requirements
**Reflection**: No reflection usage in implementation
**Trimming**: Included in core string comparison functionality
**Warnings**: No AOT-specific warnings

## Constraint Matrix
- **Cannot**: Use with IndexOf, LastIndexOf, StartsWith, EndsWith operations
- **Must**: Be used only with comparison operations (Compare, Equals with comparison)
- **Should**: Combine with other CompareOptions flags for complete comparison logic
- **Exception**: Throws ArgumentException for invalid flag combinations

## Integration Points
**StringComparer**: StringComparer.Create(CultureInfo, CompareOptions.NumericOrdering)
**Array.Sort**: Custom IComparer<string> with numeric ordering
**LINQ Ordering**: OrderBy with StringComparer implementing numeric comparison
**CultureInfo.CompareInfo**: CompareInfo.Compare with NumericOrdering flag

## Common Patterns
**File Name Sorting**: 
```csharp
var comparer = StringComparer.Create(CultureInfo.CurrentCulture, CompareOptions.NumericOrdering);
files.OrderBy(f => f.Name, comparer);
```

**Version-like Comparison**:
```csharp
string[] versions = {"1.10", "1.2", "1.20"};
Array.Sort(versions, StringComparer.Create(CultureInfo.InvariantCulture, 
    CompareOptions.NumericOrdering | CompareOptions.IgnoreCase));
```

**Natural Sorting**:
```csharp
var options = CompareOptions.NumericOrdering | CompareOptions.IgnoreCase;
var result = string.Compare("Item2", "Item10", CultureInfo.CurrentCulture, options);
// result < 0 (Item2 comes before Item10)
```

**Mixed Content**:
```csharp
string[] items = {"abc2def", "abc10def", "abc1def"};
var comparer = StringComparer.Create(CultureInfo.CurrentCulture, CompareOptions.NumericOrdering);
Array.Sort(items, comparer);
// Result: ["abc1def", "abc2def", "abc10def"]
```

## Version Evolution
**.NET 10**: Initial implementation with core comparison operations
**Future**: Potential extension to search operations (IndexOf, etc.)

## Diagnostic Markers
**Performance**: Use StringComparer.Create once, reuse for multiple comparisons
**Culture**: Specify explicit culture for consistent cross-platform behavior
**Validation**: Test with edge cases like leading zeros, very large numbers
**Combination**: Verify flag combinations don't throw ArgumentException