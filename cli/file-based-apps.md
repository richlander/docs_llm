# Feature: File-based apps with publish support

## Metadata
- **Type**: CLI Command
- **Category**: Build/Publishing
- **Introduced**: .NET 10
- **Status**: Stable
- **Scope**: SDK component, per-project feature
- **Elevation**: No special permissions required
- **Dependencies**: .NET SDK 10+, C# compiler

## Command Surface
**Primary Verbs**: publish, run, build
**Syntax Pattern**: `dotnet publish <file.cs>` | `dotnet run <file.cs>` | `dotnet build <file.cs>`
**Global Options**: --configuration, --runtime, --self-contained, --output
**Configuration**: Via #:property directives, command-line arguments, environment variables

## Execution Context
**Working Directory**: File location determines project context
**User Profile**: No special profile dependencies
**System Directory**: Uses installed SDK toolchain
**Isolation**: Each .cs file treated as independent project

## Publishing Resolution
**Target Discovery**: Infers executable target from file extension and content
**Version Selection**: Uses SDK version from global.json or latest installed
**Dependency Graph**: Resolves references via #:project directives
**Conflict Resolution**: Command-line arguments override directive settings

## Core Mechanics
**Compilation**: Single-file compilation with implicit Program class
**Project References**: #:project directive for external project dependencies
**Native AOT**: Enabled by default, controlled via #:property PublishAot
**Runtime Path Access**: System.AppContext.GetData for file/directory paths

## State Management
**Build Artifacts**: Temporary build directory, cleaned automatically
**Output Files**: Native executable in specified output location
**Source Tracking**: No persistent state between executions
**Cleanup**: Automatic cleanup of intermediate build files

## Performance Profile
**Compilation Time**: 2-10 seconds for simple apps, depends on dependencies
**Disk Usage**: Temporary build artifacts ~50-100MB, final executable ~10-50MB
**Network**: Package restore for referenced projects
**Parallelization**: Builds referenced projects concurrently

## Integration Points
**MSBuild**: Generates temporary project file with appropriate settings
**Project System**: #:project references resolved through MSBuild
**IDE**: Limited IntelliSense support, full IDE features require .csproj
**CI/CD**: Direct integration with build pipelines, no project file needed

## Error Scenarios
**Compilation Errors**: Standard C# compiler errors with file context
**Missing References**: Clear error messages for unresolved #:project references
**Publishing Failures**: Native AOT compatibility issues reported with guidance
**Runtime Errors**: Standard .NET runtime exception handling

## Security Model
**File Access**: Standard file system permissions for input file
**Code Execution**: Compiled code runs with user permissions
**Package Trust**: NuGet package signature validation for dependencies
**Sandboxing**: No additional sandboxing beyond standard .NET execution

## Diagnostic Capabilities
**Verbose Logging**: --verbosity diagnostic for compilation and publishing steps
**Build Output**: Temporary project file location and MSBuild output
**Performance**: --timed flag for build performance analysis
**Runtime Diagnostics**: System.AppContext.GetData for runtime path information

## Directive System
**#:property**: Control MSBuild properties (PublishAot, RuntimeIdentifier, etc.)
**#:project**: Reference external projects for compilation
**Shebang**: #!/usr/bin/env dotnet for direct shell execution
**Comments**: Standard C# comments, directives must be at file start

## Runtime Features
**Path Access**: 
- System.AppContext.GetData("FILE_PATH") returns source file path
- System.AppContext.GetData("DIRECTORY_PATH") returns source directory

**Shebang Support**:
```csharp
#!/usr/bin/env dotnet
Console.WriteLine("Hello from file-based app!");
```

**Project References**:
```csharp
#:project ../MyLibrary/MyLibrary.csproj
using MyLibrary;
var service = new MyService();
```

**AOT Control**:
```csharp
#:property PublishAot=false
// Disables native AOT compilation
```

## Publishing Examples
**Basic Publish**:
```bash
dotnet publish hello.cs
# Creates native executable hello.exe (Windows) or hello (Unix)
```

**Cross-platform Publish**:
```bash
dotnet publish hello.cs -r linux-x64 --self-contained
# Creates Linux x64 native executable
```

**Configured Output**:
```bash
dotnet publish hello.cs -o ./bin/Release
# Publishes to specific output directory
```

## Common Patterns
**Simple Script**:
```csharp
Console.WriteLine($"Running from: {System.AppContext.GetData("DIRECTORY_PATH")}");
```

**With Dependencies**:
```csharp
#:project ../Common/Common.csproj
#:property RuntimeIdentifier=win-x64

using Common.Utilities;
Helper.DoWork();
```

**Shell Executable**:
```csharp
#!/usr/bin/env dotnet
#:property PublishAot=true

if (args.Length == 0)
{
    Console.WriteLine("Usage: script.cs <name>");
    return 1;
}
Console.WriteLine($"Hello, {args[0]}!");
return 0;
```

## Version Evolution
**.NET 10**: Initial implementation with publish support and native AOT default
**Future**: Enhanced IDE integration, additional directive types

## Diagnostic Markers
**CS0006**: Assembly reference errors for missing #:project references
**SYSLIB**: Native AOT compatibility warnings when PublishAot=true
**MSB**: MSBuild errors from temporary project generation
**Performance**: Use --timed to identify slow compilation steps