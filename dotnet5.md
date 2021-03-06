# Support for .NET 5.0
Microsoft will release new previews of .NET 5.0 regularly until the final version in November 2020. I plan to keep this page updated with any necessary changes to support the code examples in the fourth edition of my book.

- [Download .NET 5.0 SDK](https://dotnet.microsoft.com/download/dotnet-core/5.0)
- 16 March 2020: [Announcing .NET 5 Preview 1](https://devblogs.microsoft.com/dotnet/announcing-net-5-0-preview-1/)
- 2 April 2020: [Announcing .NET 5 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-5-0-preview-2/)

Previews 1 and 2 use the C# 8.0 compiler so there aren't any new language features. Previews 1 and 2 also do not include any new features for the base class libraries or app models like ASP.NET Core. They mostly include a few bug fixes and performance improvements. Of course, those are important improvements but from the perspective of the code in my book, they don't require changes beyond the project file updates shown on this page.

## Chapters 1 to 19
After installing the .NET 5.0 SDK, following the step-by-step instructions in the book should work as expected since the project file will automatically reference .NET 5.0 as the target framework. 

To upgrade a project in the GitHub repository from .NET Core 3.1 to .NET 5.0 just requires a version number change in your project file.

Change this:
```
<TargetFramework>netcoreapp3.1</TargetFramework>
```
To this:
```
<TargetFramework>netcoreapp5.0</TargetFramework>
```
Previews 1 and 2 use `netcoreapp5.0` as the target framework name. This will change to `net5.0` in a future preview, as described in detail at the following link: https://github.com/dotnet/designs/blob/master/accepted/2020/net5/net5.md

For projects that reference additional NuGet packages, use the latest NuGet package version (including preview versions), as shown in the rest of this page, instead of the version given in the book. 

If I am slow updating this page then you can search for them yourself at the following link: https://www.nuget.org

## Chapter 4 - Writing, Debugging, and Testing Functions
For the `Instrumenting` project, the additional referenced NuGet packages should use the latest preview versions, as shown in the following markup: 
```
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.Extensions.Configuration" Version="5.0.0-preview.2.20160.3" />
    <PackageReference Include="Microsoft.Extensions.Configuration.Binder" Version="5.0.0-preview.2.20160.3" />
    <PackageReference Include="Microsoft.Extensions.Configuration.FileExtensions" Version="5.0.0-preview.2.20160.3" />
    <PackageReference Include="Microsoft.Extensions.Configuration.Json" Version="5.0.0-preview.2.20160.3" />
  </ItemGroup>

</Project>
```
For the `CalculatorLibUnitTests` project, the additional referenced NuGet packages for unit testing can use the latest versions including preview versions, as shown in the following markup:
```
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp5.0</TargetFramework>
    <IsPackable>false</IsPackable>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.6.0-preview-20200318-01" />
    <PackageReference Include="xunit" Version="2.4.1" />
    <PackageReference Include="xunit.runner.visualstudio" Version="2.4.1" />
    <PackageReference Include="coverlet.collector" Version="1.2.0" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference 
      Include="..\CalculatorLib\CalculatorLib.csproj" />
  </ItemGroup>

</Project>
```
## Chapter 11 - Working with Databases Using Entity Framework Core
For the `WorkingWithEFCore` project, the additional referenced NuGet packages should use the preview versions, as shown in the following markup:
```
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference 
      Include="Microsoft.EntityFrameworkCore.Sqlite" 
      Version="5.0.0-preview.2.20159.4" />
    <PackageReference
      Include="Microsoft.EntityFrameworkCore.Proxies"
      Version="5.0.0-preview.2.20159.4" />
  </ItemGroup>

</Project>
```
## Chapter 12 - Querying and Manipulating Data Using LINQ
For the `LinqWithEFCore` and `Exercise02` projects, the additional referenced NuGet packages should use the preview versions, as shown in the following markup:
```
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference 
      Include="Microsoft.EntityFrameworkCore.Sqlite" 
      Version="5.0.0-preview.2.20159.4" />
  </ItemGroup>

</Project>
```
## Chapter 14 - Practical Applications of C# and .NET
For the `NorthwindContextLib` project, the referenced NuGet package for SQLite should use the preview version, as shown in the following markup:
```
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <ProjectReference Include=
      "..\NorthwindEntitiesLib\NorthwindEntitiesLib.csproj" />
    <PackageReference
      Include="Microsoft.EntityFrameworkCore.SQLite" 
      Version="5.0.0-preview.2.20159.4" />
  </ItemGroup>

</Project>
```
## Chapter 16 - Building Websites Using the Model-View-Controller Pattern
For the `NorthwindMvc` project, the referenced NuGet packages should use the preview versions, as shown in the following markup:
```
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp5.0</TargetFramework>
    <UserSecretsId>aspnet-NorthwindMvc-72F8E5E5-AF15-4520-91A9-EF8090AF2961</UserSecretsId>
  </PropertyGroup>

  <ItemGroup>
    <None Update="app.db" CopyToOutputDirectory="PreserveNewest" />
  </ItemGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore" Version="5.0.0-preview.2.20167.3" />
    <PackageReference Include="Microsoft.AspNetCore.Identity.EntityFrameworkCore" Version="5.0.0-preview.2.20167.3" />
    <PackageReference Include="Microsoft.AspNetCore.Identity.UI" Version="5.0.0-preview.2.20167.3" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Sqlite" Version="5.0.0-preview.2.20159.4" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Tools" Version="5.0.0-preview.2.20159.4" />
    
    <!-- added in Chapter 18 to call a web service -->
    <PackageReference Include="Newtonsoft.Json" Version="12.0.3" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include=
      "..\NorthwindContextLib\NorthwindContextLib.csproj" />
  </ItemGroup>

</Project>
```
## Chapter 17 - Building Websites Using a Content Management System
Also read [Upgrading to Piranha CMS 8.1](piranha-cms.md)

For the `NorthwindCms` project, the referenced NuGet packages should use the latest or preview versions, as shown in the following markup:
```
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>
    <TargetFramework>netcoreapp5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <Folder Include="wwwroot\" />
  </ItemGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore.Sqlite" Version="5.0.0-preview.2.20159.4" />
    <PackageReference Include="Piranha" Version="8.1.0" />
    <PackageReference Include="Piranha.AspNetCore" Version="8.1.0" />
    <PackageReference Include="Piranha.AspNetCore.Identity.SQLite" Version="8.1.0" />
    <PackageReference Include="Piranha.AttributeBuilder" Version="8.1.0" />
    <PackageReference Include="Piranha.Data.EF.SQLite" Version="8.1.2" />
    <PackageReference Include="Piranha.ImageSharp" Version="8.1.0-rc1" />
    <PackageReference Include="Piranha.Local.FileStorage" Version="8.1.0" />
    <PackageReference Include="Piranha.Manager" Version="8.1.0" />
    <PackageReference Include="Piranha.Manager.TinyMCE" Version="8.1.0" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include=
      "..\NorthwindEntitiesLib\NorthwindEntitiesLib.csproj" />
    <ProjectReference Include=
      "..\NorthwindContextLib\NorthwindContextLib.csproj" />
  </ItemGroup>

</Project>
```
## Chapter 18 - Building and Consuming Web Services
For the `NorthwindService` project, the referenced NuGet packages should use the latest or preview versions, as shown in the following markup:
```
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <ProjectReference Include=
      "..\NorthwindContextLib\NorthwindContextLib.csproj" />

    <PackageReference Include="Swashbuckle.AspNetCore" Version="5.3.1" />
    
    <PackageReference Include=
      "Microsoft.Extensions.Diagnostics.HealthChecks.EntityFrameworkCore" 
      Version="5.0.0-preview.2.20167.3" />
  </ItemGroup>

</Project>
```
## Chapter 19 - Building Intelligent Apps Using Machine Learning
For the `NorthwindML` project, the referenced NuGet packages should use the latest or preview versions, as shown in the following markup:
```
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference 
      Include="Microsoft.AspNetCore.Mvc.NewtonsoftJson" 
      Version="5.0.0-preview.2.20167.3" />
    <PackageReference 
      Include="Microsoft.EntityFrameworkCore.Sqlite" 
      Version="5.0.0-preview.2.20159.4" />
    <PackageReference 
      Include="Microsoft.ML" 
      Version="1.5.0-preview2" />
    <PackageReference 
      Include="Microsoft.ML.Recommender" 
      Version="0.17.0-preview2" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include=
      "..\NorthwindContextLib\NorthwindContextLib.csproj" />
    <ProjectReference Include=
      "..\NorthwindEmployees\NorthwindEmployees.csproj" />
  </ItemGroup>

</Project>
```
