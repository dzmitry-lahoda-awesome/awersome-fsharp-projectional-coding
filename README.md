# Projectional coding

Code all external calls, contracts, integrations interactively in original language of system.
Then do proper F# generations and usage.

- like language projection generators (generators which generate representation of windows COM api to feel it as native as possible) https://docs.microsoft.com/en-us/uwp/winrt-cref/winmd-files , but for broader set of problems

- is absolute opposite of embbeded DLS https://martinfowler.com/bliki/InternalDslStyle.html

- you do not create custom languages and parsers, like in https://en.wikipedia.org/wiki/Language_workbench, but use only existing standards; if there is not standard - just do raw F# coding

- you still consider programs to be texts, not binary ASTs as in https://en.wikipedia.org/wiki/Intentional_programming

## List of related concepts

- https://en.wikipedia.org/wiki/Grammar-oriented_programming
- https://en.wikipedia.org/wiki/Language-oriented_programming
- https://en.wikipedia.org/wiki/Domain-specific_language
- https://en.wikipedia.org/wiki/Data-driven_programming
- https://en.wikipedia.org/wiki/Extensible_programming
- https://arxiv.org/pdf/1904.11254.pdf 

# Example

## Problem 1

You are tasked to create microservice wich aggregates data from SQL native and JSON native databases. And provide web api.

### Possible steps

- Create and push SQL scripts into repo you created in database client
- Create JSON scripts you used to run agains JSON database
- Write definion of OpenAPI
- Validate queries and data they return with with parties (Data Engineers for queries and frontend developers for API)
- Template original queries (any custom templating will work fine)
- Generate F# stubs-types-entries
- Code wiring logic
- Write tests in Gherking language (provide these to Tester to testers)

### Analysis

- We use as much of discovery phase artifacts as possibe
- We communicate as effectively as possible (we will have iterate this manu times as system evolves)
- We get F# codes generators from which we can start domain modelling (if we need to)
- We write as few mappers as possible (hence can be concurrent on market with TypeScript considering speed of development)

## Problem 2

You have to read configurations in our microservices in hosted environment. 

### Steps
- Generate configuration from known files (as these will be provided) in JSON
- Generate configuration from environment variables (provide all these as part of local build-run scripts)
- Wire custom hierarchy of choices
- Change wiring and configuration if host changes

### Analysys

We could delegate merging work to `Microsoft.Extensions.Configuration`, but ... (I have several pros and cons for these, need to recall, but propsed solution with compile time configuration still makes sense - software is much harded to break because of miss configuration)

## Projects

- https://github.com/Szer/GiraffeGenerator - API
- https://github.com/panesofglass/FSharp.Data.JsonSchema - API

- https://github.com/Zaid-Ajaj/Npgsql.FSharp.Analyzer - SQL
- https://github.com/rspeele/rezoom.sql - SQL

- https://github.com/fsharp/FSharp.Data - CSV, JSON, XML (these still lack generation of lenses for immutable and mutable variants)

- https://github.com/fsprojects/FSharp.Interop.Dynamic - to work with JSON as properties instead of hash maps

- https://github.com/fsprojects/FSharp.Text.RegexProvider 

- https://github.com/fsprojects/TickSpec - tests
- https://github.com/SpecFlowOSS/SpecFlow-Examples/tree/master/BowlingKata/BowlingKata-Fsharp - tests
 
 - https://github.com/Fable-Fauna/Fable.Flora - styling user interfaces
 - https://github.com/fable-compiler/ts2fable - web native APIs
 
 - https://github.com/fsprojects/FsXaml - windows user interfaces
 
 - https://github.com/fsprojects/FSharp.Configuration - YAML, INI, AppSettings, ResX
 
 - https://github.com/fsprojects/SQLProvider - DDL applied to database -> schema
 
 - https://github.com/Tarmil/FSharp.Data.LiteralProviders - environment variables
 
### Possible
 
 - generator for ElasticSearch queries
 - F# native GRPC generator
 - GraphQL
 - GC free untyped C bindings with calli
 - Some modelling laguages
 - git configuration
