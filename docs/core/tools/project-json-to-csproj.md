---
title: project.json 與 csproj 比較 - .NET Core
description: 查看 project.json 與 csproj 項目的對應。
author: natemcmaster
ms.author: mairaw
ms.date: 03/13/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: c5753d73f062aa107d7afbec6146ea3452901fb1
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a>project.json 與 csproj 屬性的對應

作者：[Nate McMaster](https://github.com/natemcmaster)

在 .NET Core 工具開發期間，有項重要的設計變更導致不再支援 *project.json* 檔案，相反地，.NET Core 專案會改為使用 MSBuild/csproj 格式。

本文說明如何以 MSBuild/csproj 格式表示 *project.json* 中的設定，讓您了解如何使用此新的格式，並了解將專案升級至最新版的工具時，移轉工具所做的變更。 
 
## <a name="the-csproj-format"></a>csproj 格式

新格式 \*.csproj 是以 XML 為基礎的格式。 下列範例顯示使用 `Microsoft.NET.Sdk` 之 .NET Core 專案的根節點。 若是 Web 專案，所使用的 SDK 會是 `Microsoft.NET.Sdk.Web`。

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a>常見的最上層屬性

### <a name="name"></a>name
```json
{
  "name": "MyProjectName"
}
```

不再受支援。 在 csproj 中，這是由目錄名稱所定義的專案檔名所決定。 例如，`MyProjectName.csproj`。

根據預設，專案檔名也會指定 `<AssemblyName>` 和 `<PackageId>` 屬性的值。 

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

如果 `buildOptions\outputName` 屬性定義於 project.json，則 `<AssemblyName>` 會有與 `<PackageId>` 不同的值。 如需詳細資訊，請參閱[其他常見的建置選項](#other-common-build-options)。

### <a name="version"></a>版本

```json
{
  "version": "1.0.0-alpha-*"
}
```
使用 `VersionPrefix` 和 `VersionSuffix` 屬性：

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

您也可以使用 `Version` 屬性，但此屬性可能會在封裝期間覆寫版本設定：

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a>其他常見的根層級選項

```json
{
  "authors": [ "Anne", "Bob" ],
  "company": "Contoso",
  "language": "en-US",
  "title": "My library",
  "description": "This is my library.\r\nAnd it's really great!",
  "copyright": "Nugetizer 3000",
  "userSecretsId": "xyz123"
}
```

```xml
<PropertyGroup>
  <Authors>Anne;Bob</Authors>
  <Company>Contoso</Company>
  <NeutralLanguage>en-US</NeutralLanguage>
  <AssemblyTitle>My library</AssemblyTitle>
  <Description>This is my library.
And it's really great!</Description>
  <Copyright>Nugetizer 3000</Copyright>
  <UserSecretsId>xyz123</UserSecretsId>
</PropertyGroup>
```

## <a name="frameworks"></a>frameworks

### <a name="one-target-framework"></a>一個目標架構
```json
{
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp1.0</TargetFramework>
</PropertyGroup>
```

### <a name="multiple-target-frameworks"></a>多個目標架構

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

使用 `TargetFrameworks` 屬性，定義您的目標架構清單。 使用分號來分隔多個架構值。 

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a>相依性

> [!IMPORTANT]
> 如果相依性是**專案**而不是套件，則格式會不同。 如需詳細資訊，請參閱[相依性類型](#dependency-type)一節。

### <a name="netstandardlibrary-metapackage"></a>NETStandard.Library 中繼套件

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  }
}
```

```xml
<PropertyGroup>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

### <a name="microsoftnetcoreapp-metapackage"></a>Microsoft.NETCore.App 中繼套件

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.0"
  }
}
```

```xml
<PropertyGroup>
  <RuntimeFrameworkVersion>1.0.3</RuntimeFrameworkVersion>
</PropertyGroup>
```

請注意，移轉專案中的 `<RuntimeFrameworkVersion>` 值取決於您已安裝的 SDK 版本。

### <a name="top-level-dependencies"></a>最上層相依性
```json
{
  "dependencies": {
    "Microsoft.AspNetCore": "1.1.0"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore" Version="1.1.0" />
</ItemGroup>
```

### <a name="per-framework-dependencies"></a>每個架構相依性
```json
{
  "framework": {
    "net451": {
      "dependencies": {
        "System.Collections.Immutable": "1.3.1"
      }
    },
    "netstandard1.5": {
      "dependencies": {
        "Newtonsoft.Json": "9.0.1"
      }
    }
  }
}
```

```xml
<ItemGroup Condition="'$(TargetFramework)'=='net451'">
  <PackageReference Include="System.Collections.Immutable" Version="1.3.1" />
</ItemGroup>

<ItemGroup Condition="'$(TargetFramework)'=='netstandard1.5'">
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
</ItemGroup>
```

### <a name="imports"></a>匯入

```json
{
  "dependencies": {
    "YamlDotNet": "4.0.1-pre309"
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dnxcore50",
        "dotnet"
      ]
    }
  }
}
```

```xml
<PropertyGroup>
  <PackageTargetFallback>dnxcore50;dotnet</PackageTargetFallback>
</PropertyGroup>
<ItemGroup>
  <PackageReference Include="YamlDotNet" Version="4.0.1-pre309" />
</ItemGroup>
```

### <a name="dependency-type"></a>相依性類型

#### <a name="type-project"></a>類型︰專案
```json
{
  "dependencies": {
    "MyOtherProject": "1.0.0-*",
    "AnotherProject": {
      "type": "project"
    }
  }
}
```

```xml
<ItemGroup>
  <ProjectReference Include="..\MyOtherProject\MyOtherProject.csproj" />
  <ProjectReference Include="..\AnotherProject\AnotherProject.csproj" />
</ItemGroup>
```

> [!NOTE]
> 這會破壞 `dotnet pack --version-suffix $suffix` 判斷專案參考之相依性版本的方式。


#### <a name="type-build"></a>類型︰組建
```json
{
  "dependencies": {
    "Microsoft.EntityFrameworkCore.Design": {
      "version": "1.1.0",
      "type": "build"
    }
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="1.1.0" PrivateAssets="All" />
</ItemGroup>
```

#### <a name="type-platform"></a>類型：平台
```json
{
  "dependencies": {
    "Microsoft.NETCore.App": {
      "version": "1.1.0",
      "type": "platform"
    }
  }
}
```

csproj 中沒有對應項。 

## <a name="runtimes"></a>runtimes
```json
{
  "runtimes": {
    "win7-x64": {},
    "osx.10.11-x64": {},
    "ubuntu.16.04-x64": {}
  }
}
```

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win7-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="standalone-apps-self-contained-deployment"></a>獨立應用程式 (獨立性部署)
在 project.json 中，定義 `runtimes` 區段表示應用程式在建置和發行期間是獨立的。
在 MSBuild 中，所有專案在建置期間都是「可攜式」，但可發行為獨立專案。

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

如需詳細資訊，請參閱[獨立性部署 (SCD)](../deploying/index.md#self-contained-deployments-scd)。

## <a name="tools"></a>tools
```json
{
  "tools": {
    "Microsoft.EntityFrameworkCore.Tools.DotNet": "1.0.0-*"
  }
}
```

```xml
<ItemGroup>
  <DotNetCliToolReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.0" />
</ItemGroup>
```

> [!NOTE]
> 在 csproj 中不支援對工具進行 `imports`。 需要 imports 的工具將無法搭配新的 `Microsoft.NET.Sdk` 使用。

## <a name="buildoptions"></a>buildOptions

另請參閱[檔案](#files)。

### <a name="emitentrypoint"></a>emitEntryPoint

```json
{
  "buildOptions": {
    "emitEntryPoint": true
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

如果 `emitEntryPoint` 為 `false`，則 `OutputType` 的值會轉換成預設值 `Library`：

```json
{
  "buildOptions": {
    "emitEntryPoint": false
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Library</OutputType>
  <!-- or, omit altogether. It defaults to 'Library' -->
</PropertyGroup>
```

### <a name="keyfile"></a>keyFile

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

`keyFile` 項目在 MSBuild 中已擴充成三個屬性：

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a>其他常見的建置選項

```json
{
  "buildOptions": {
    "warningsAsErrors": true,
    "nowarn": ["CS0168", "CS0219"],
    "xmlDoc": true,
    "preserveCompilationContext": true,
    "outputName": "Different.AssemblyName",
    "debugType": "portable",
    "allowUnsafe": true,
    "define": ["TEST", "OTHERCONDITION"]
  }
}
```

```xml
<PropertyGroup>
  <TreatWarningsAsErrors>true</TreatWarningsAsErrors>
  <NoWarn>$(NoWarn);CS0168;CS0219</NoWarn>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
  <PreserveCompilationContext>true</PreserveCompilationContext>
  <AssemblyName>Different.AssemblyName</AssemblyName>
  <DebugType>portable</DebugType>
  <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  <DefineConstants>$(DefineConstants);TEST;OTHERCONDITION</DefineConstants>
</PropertyGroup>
```

## <a name="packoptions"></a>packOptions

另請參閱[檔案](#files)。

### <a name="common-pack-options"></a>常見的封裝選項

```json
{
  "packOptions": {    
    "summary": "numl is a machine learning library intended to ease the use of using standard modeling techniques for both prediction and clustering.",
    "tags": ["machine learning", "framework"],
    "releaseNotes": "Version 0.9.12-beta",
    "iconUrl": "http://numl.net/images/ico.png",
    "projectUrl": "http://numl.net",
    "licenseUrl": "https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md",
    "requireLicenseAcceptance": false,
    "repository": {
      "type": "git",
      "url": "https://raw.githubusercontent.com/sethjuarez/numl"
    },
    "owners": ["Seth Juarez"]
  }
}
```

```xml
<PropertyGroup>
  <!-- summary is not migrated from project.json, but you can use the <Description> property for that if needed. -->
  <PackageTags>machine learning;framework</PackageTags>
  <PackageReleaseNotes>Version 0.9.12-beta</PackageReleaseNotes>
  <PackageIconUrl>http://numl.net/images/ico.png</PackageIconUrl>
  <PackageProjectUrl>http://numl.net</PackageProjectUrl>
  <PackageLicenseUrl>https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md</PackageLicenseUrl>
  <PackageRequireLicenseAcceptance>false</PackageRequireLicenseAcceptance>
  <RepositoryType>git</RepositoryType>
  <RepositoryUrl>https://raw.githubusercontent.com/sethjuarez/numl</RepositoryUrl>
  <!-- owners is not supported in MSBuild -->
</PropertyGroup>
```

MSBuild 中的 `owners` 項目沒有對應項。 對於 `summary`，您可以使用 MSBuild `<Description>` 屬性，即使 `summary` 的值不會自動移轉至該屬性亦然，因為該屬性會對應至 [`description`](#-other-common-root-level-options) 項目。

## <a name="scripts"></a>指令碼

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

其在 MSBuild 中的對應項是 [targets](/visualstudio/msbuild/msbuild-targets)：

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```


## <a name="runtimeoptions"></a>runtimeOptions

```json
{
  "runtimeOptions": {
    "configProperties": {
      "System.GC.Server": true,
      "System.GC.Concurrent": true,
      "System.GC.RetainVM": true,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

除了 "System.GC.Server" 屬性，此群組中的所有其他設定都會放置在專案資料夾中名為 *runtimeconfig.template.json* 的檔案，其選項會在移轉程序期間上移至根物件：

```json
{
  "configProperties": {
    "System.GC.Concurrent": true,
    "System.GC.RetainVM": true,
    "System.Threading.ThreadPool.MinThreads": 4,
    "System.Threading.ThreadPool.MaxThreads": 25
  }
}
```

"System.GC.Server" 屬性會移轉至 csproj 檔案：
```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

不過，您可以在 csproj as 中設定上述所有值及 MSBuild 屬性：
```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a>共用
```json
{
  "shared": "shared/**/*.cs"
}
```

在 csproj 中不支援。 您必須改為在 *.nuspec* 檔案中建立包含內容檔。 如需詳細資訊，請參閱[包含內容檔](/nuget/schema/nuspec#including-content-files)。

## <a name="files"></a>個檔案

在 *project.json* 中，可擴充組建和套件以從其他資料夾進行編譯和內嵌。
在 MSBuild 中，這會使用[目](/visualstudio/msbuild/common-msbuild-project-items)來完成。 以下是常見慣例範例：

```json
{
  "buildOptions": {
    "compile": {
      "copyToOutput": "notes.txt",
      "include": "../Shared/*.cs",
      "exclude": "../Shared/Not/*.cs"
    },
    "embed": {
      "include": "../Shared/*.resx"
    }
  },
  "packOptions": {
    "include": "Views/",
    "mappings": {
      "some/path/in/project.txt": "in/package.txt"
    }
  },
  "publishOptions": {
    "include": [
      "files/",
      "publishnotes.txt"
    ]
  }
}
```

```xml
<ItemGroup>
  <Compile Include="..\Shared\*.cs" Exclude="..\Shared\Not\*.cs" />
  <EmbeddedResource Include="..\Shared\*.resx" />
  <Content Include="Views\**\*" PackagePath="%(Identity)" />
  <None Include="some/path/in/project.txt" Pack="true" PackagePath="in/package.txt" />
  
  <None Include="notes.txt" CopyToOutputDirectory="Always" />
  <!-- CopyToOutputDirectory = { Always, PreserveNewest, Never } -->

  <Content Include="files\**\*" CopyToPublishDirectory="PreserveNewest" />
  <None Include="publishnotes.txt" CopyToPublishDirectory="Always" />
  <!-- CopyToPublishDirectory = { Always, PreserveNewest, Never } -->
</ItemGroup>
```

> [!NOTE]
> .NET Core SDK 會自動新增許多預設 [Glob 模式](https://en.wikipedia.org/wiki/Glob_(programming))。
> 如需詳細資訊，請參閱 [Default Compile Item Values](https://aka.ms/sdkimplicititems) (預設編譯項目值)。

所有 MSBuild `ItemGroup` 項目都支援 `Include`、`Exclude` 和 `Remove`。

您可以使用 `PackagePath="path"` 修改 .nupkg 內的套件配置。

除了 `Content`，大多數項目群組都需要明確地新增 `Pack="true"`，以包含在套件中。 因為 MSBuild `<IncludeContentInPack>` 屬性預設會設定為 `true`，所以會將 `Content` 放在套件的 *content* 資料夾中。 如需詳細資訊，請參閱 [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package) (在套件中包含內容)。

`PackagePath="%(Identity)"` 是將套件路徑設定為專案相關檔案路徑的捷徑。

## <a name="testrunner"></a>testRunner

### <a name="xunit"></a>xUnit

```json
{
  "testRunner": "xunit",
  "dependencies": {
    "dotnet-test-xunit": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="xunit" Version="2.2.0-*" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0-*" />
</ItemGroup>
```

### <a name="mstest"></a>MSTest

```json
{
  "testRunner": "mstest",
  "dependencies": {
    "dotnet-test-mstest": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.12-*" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.11-*" />
</ItemGroup>
```

## <a name="see-also"></a>請參閱

[CLI 中變更的高階概觀](../tools/cli-msbuild-architecture.md)
