# Setting up your project to use our rules

Copy the [EditorConfig rules](csharp.editorconfig) from line 3 to the last line, and paste under the `[*.{cs}]` of your EditorConfig.

Create a folder called `analysis` and put the `csharp.ruleset` and `banned_symbols.txt` file in there.

In the folder where your project's solution file resides, create or modify if the `Directory.Build.props` file already exists and add these following properties into the `Project` member.

```xml
<ItemGroup Label="Code Analysis">
    <PackageReference Include="Microsoft.CodeAnalysis.BannedApiAnalyzers" Version="3.3.2" PrivateAssets="All" />
    <AdditionalFiles Include="$(MSBuildThisFileDirectory)analysis\banned_symbols.txt" />
    <PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="5.0.3" PrivateAssets="All" />
</ItemGroup>
<PropertyGroup Label="Code Analysis">
    <CodeAnalysisRuleSet>$(MSBuildThisFileDirectory)analysis\csharp.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

It should look like this:

```xml
<Project>
    ...
    <ItemGroup Label="Code Analysis">
        <PackageReference Include="Microsoft.CodeAnalysis.BannedApiAnalyzers" Version="3.3.2" PrivateAssets="All" />
        <AdditionalFiles Include="$(MSBuildThisFileDirectory)analysis\banned_symbols.txt" />
        <PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="5.0.3" PrivateAssets="All" />
    </ItemGroup>
    <PropertyGroup Label="Code Analysis">
        <CodeAnalysisRuleSet>$(MSBuildThisFileDirectory)analysis\csharp.ruleset</CodeAnalysisRuleSet>
    </PropertyGroup>
    ...
</Project>
```

Now move the `solution-name.sln.DotSettings` to the folder where the project solution file is located and rename the part of the `solution-name` to the name of your solution.

Your project is now set up and you can use our code rules.
