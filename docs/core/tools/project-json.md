---
title: "project.json 參考"
description: "project.json 參考"
keywords: .NET, .NET Core, project.json
author: aL3891
ms.author: mairaw
manager: wpickett
ms.date: 09/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3aef32bd-ee2a-4e24-80f8-a2b615e0336d
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: f870dc601a1df5dd663cd165bc19f70df9aa57f4

---

# <a name="projectjson-reference"></a>project.json 參考

project.json 檔案用於 .NET Core 專案中，用來定義專案中繼資料、編譯資訊和相依性。 在本參考主題中，您會看到可在 project.json 檔案中定義的所有屬性清單。

> [!NOTE]
> 在未來版本中，.NET Core 工具即將從 project.json 移到 MSBuild 專案。 因為發行工具時，會有將專案轉換成 MSBuild 的路徑，所以建議新的 .NET Core 專案仍然使用 project.json 檔案。
>
> 如需詳細資訊，請參閱 .NET 部落格上的 [Changes to project.json](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/) (project.json 變更) 文章以及[使用 MSBuild 建置 .NET Core 專案](../tutorials/target-dotnetcore-with-msbuild.md)主題。

## <a name="overview"></a>概觀

```
{
    "name": String,
    "version": String,
    "description": String,
    "copyright": String,
    "title": String,
    "entryPoint": String,
    "testRunner": String,
    "authors": String[],
    "language": String,
    "embedInteropTypes": Boolean,
    "preprocess": String or String[],
    "shared": String or String[],
    "dependencies": Object {
        version: String,
        type: String,
        target: String,
        include: String,
        exclude: String,
        suppressParent: String
    },
    "tools": Object,
    "scripts": Object,
    "buildOptions": Object {
        "define": String[],
        "nowarn": String[],
        "additionalArguments": String[],
        "warningsAsErrors": Boolean,
        "allowUnsafe": Boolean,
        "emitEntryPoint": Boolean,
        "optimize": Boolean,
        "platform": String,
        "languageVersion": String,
        "keyFile": String,
        "delaySign": Boolean,
        "publicSign": Boolean,
        "debugType": String,
        "xmlDoc": Boolean,
        "preserveCompilationContext": Boolean,
        "outputName": String,
        "compilerName": String,
        "compile": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        },
        "embed": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        },
        "copyToOutput": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        }
    },
    "publishOptions": Object {
        "include": String or String[],
        "exclude": String or String[],
        "includeFiles": String or String[],
        "excludeFiles": String or String[],
        "builtIns": Object,
        "mappings": Object
    },
    "runtimeOptions": Object {
        "configProperties": Object {
            "System.GC.Server": Boolean,
            "System.GC.Concurrent": Boolean,
            "System.GC.RetainVM": Boolean,
            "System.Threading.ThreadPool.MinThreads": Integer,
            "System.Threading.ThreadPool.MaxThreads": Integer
        },
        "framework": Object {
            "name": String,
            "version": String,
        },
        "applyPatches": Boolean
    },
    "packOptions": Object {
        "summary": String,
        "tags": String[],
        "owners": String[],
        "releaseNotes": String,
        "iconUrl": String,
        "projectUrl": String,
        "licenseUrl": String,
        "requireLicenseAcceptance": Boolean,
        "repository": Object {
            "type": String,
            "url": String
        },
        "files": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        }
    },
    "analyzerOptions": Object {
        "languageId": String
    },
    "configurations": Object,
    "frameworks": Object {
        "dependencies": Object {
            version: String,
            type: String,
            target: String,
            include: String,
            exclude: String,
            suppressParent: String
        },        
        "frameworkAssemblies": Object,
        "wrappedProject": String,
        "bin": Object {
            assembly: String
        }
    },
    "runtimes": Object,
    "userSecretsId": String
}
```

## <a name="name"></a>name
類型：String

專案的名稱，用於組件名稱和套件名稱。 如果未指定這個屬性，則會使用最上層資料夾名稱。

例如: 

```json
{
    "name": "MyLibrary"
}
```

## <a name="version"></a>版本
類型：String

[Semver](http://semver.org/spec/v1.0.0.html) 版本的專案，也用於 NuGet 套件。

例如: 

```json
{
    "version": "1.0.0-*"
}
```

## <a name="description"></a>說明
類型：String

專案的較長描述。 用於組件屬性中。

例如: 

```json
{
    "description": "This is my library and it's really great!"
}
```

## <a name="copyright"></a>Copyright
類型：String

專案的著作權資訊。 用於組件屬性中。

例如: 

```json
{
    "copyright": "Fabrikam 2016"
}
```

## <a name="title"></a>標題
類型：String

專案的易記名稱，可以包含使用 `name` 屬性時不允許的空格和特殊字元。 用於組件屬性中。

例如: 

```json
{
    "title": "My Library"
}
```

## <a name="entrypoint"></a>entryPoint
類型：String

專案的進入點方法。 預設為 `Main`。

例如：

```json
{
    "entryPoint": "ADifferentMethod"
}
```
    
## <a name="testrunner"></a>testRunner
類型：String

與這個專案搭配使用的測試執行器名稱 (例如 [NUnit](http://nunit.org/) 或 [xUnit](http://xunit.github.io/))。 設定這個項目也會將專案標示為測試專案。

例如: 

```json
{
    "testRunner": "NUnit"
}
```

## <a name="authors"></a>authors
類型：String[]

具有專案作者名稱的字串陣列。

例如: 

```json
{
    "authors": ["Anne", "Bob"]
}
```

## <a name="language"></a>語言
類型：String

專案 (人類) 語言。 對應至 "neutral-language" 編譯器引數。

例如: 

```json
{
    "language": "en-US"
}
```

## <a name="embedinteroptypes"></a>embedInteropTypes
類型：布林值

`false` 會在組件內嵌 COM interop 類型；否則為 `true`。 

例如：

```json
{
    "embedInteropTypes": true
}
```

## <a name="preprocess"></a>preprocess
類型：具有萬用字元模式的 String 或 String[]

指定包含在前置處理中的檔案。

例如: 

```json
{
    "preprocess": "compiler/preprocess/**/*.cs"
}
```

## <a name="shared"></a>共用
類型：具有萬用字元模式的 String 或 String[]

指定共用的檔案，而這用於程式庫匯出。

例如: 

```json
{
    "shared": "shared/**/*.cs"
}
```

## <a name="dependencies"></a>相依性
類型：Object

定義專案套件相依性的物件，這個物件的每個索引鍵都是套件的名稱，而且每個值都包含版本資訊。
如需詳細資訊，請參閱 NuGet 文件網站上的 [Dependency resolution](https://docs.nuget.org/ndocs/consume-packages/dependency-resolution#dependency-resolution-in-nuget-3-x) 文章。

例如: 

```json
    "dependencies": {
        "System.Reflection.Metadata": "1.3.0",
        "Microsoft.Extensions.JsonParser.Sources": {
          "type": "build",
          "version": "1.0.0-rc2-20221"
        },
        "Microsoft.Extensions.HashCodeCombiner.Sources": {
          "type": "build",
          "version": "1.1.0-alpha1-21456"
        },
        "Microsoft.Extensions.DependencyModel": "1.0.0-*"
    }
```

### <a name="version"></a>版本
類型：String

指定相依性的版本或版本範圍。 使用 \* 萬用字元來指定 [floating dependency version](https://docs.nuget.org/ndocs/consume-packages/dependency-resolution#floating-versions)。

例如: 

```json
"dependencies": { 
    "Newtonsoft.Json": { 
        "version": "9.0.1" 
    }
}
```

### <a name="type"></a>類型
類型：String

指定相依性的類型。 它可以為下列其中一個值：`default`、`build` 或 `platform`。 預設值是 `default`。

`build` 稱為開發相依性，僅適用於建置階段。 這表示套件不應該發行或新增為輸出 `.nupkg` 檔案的相依性。 它的效果與將 [supressParent](#supressparent) 設定為 `all` 相同。

`platform` 參考共用 SDK。 如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)主題的＜部署具有協力廠商相依性的架構相依部署＞一節。

例如：

```json
 "dependencies": {
   "Microsoft.NETCore.App": {
     "type": "platform",
     "version": "1.0.0"
   }
 }
```

### <a name="target"></a>target
類型：String

限制相依性，使其只符合 `project` 或 `package`。

### <a name="include"></a>include
類型：String

包含相依性套件的組件。 它可以使用下列一個或多個旗標：`all`、`runtime`、`compile`、`build`、`contentFiles`、`native`、`analyzers` 或 `none`。
以逗號分隔清單形式定義多個旗標。
如需詳細資訊，請參閱 NuGet 存放庫上的[管理相依性套件資產](https://github.com/NuGet/Home/wiki/%5BSpec%5D-Managing-dependency-package-assets)規格。

例如: 

```json
{
  "dependencies": {
    "packageA": {
      "version": "1.0.0",
      "include": "runtime"
    }
  }
}
```

### <a name="exclude"></a>exclude
類型：String

排除相依性套件的組件。 它可以是下列一個或多個旗標：`all`、`runtime`、`compile`、`build`、`contentFiles`、`native`、`analyzers` 或 `none`。
以逗號分隔清單形式定義多個旗標。
如需詳細資訊，請參閱 NuGet 存放庫上的[管理相依性套件資產](https://github.com/NuGet/Home/wiki/%5BSpec%5D-Managing-dependency-package-assets)規格。

例如: 

```json
{
  "dependencies": {
    "packageA": {
      "version": "1.0.0",
      "exclude": "contentFiles"
    }
  }
}
```

### <a name="supressparent"></a>supressParent
類型：String

定義專案消費者的額外排除。 它可以是下列其中一個旗標：`all`、`runtime`、`compile`、`build`、`contentFiles`、`native`、`analyzers` 或 `none`。
如需詳細資訊，請參閱 NuGet 存放庫上的[管理相依性套件資產](https://github.com/NuGet/Home/wiki/%5BSpec%5D-Managing-dependency-package-assets)規格。

```json
{
  "dependencies": {
    "packageA": {
      "version": "1.0.0",
      "suppressParent": "compile"
    }
  }
}
```

## <a name="tools"></a>工具
類型：Object

定義套件相依性的物件，而相依性是作為目前專案的工具，而非參考。 這裡定義的套件可以在建置流程期間執行的指令碼中使用，但專案本身中的程式碼無法進行存取。 例如，工具可以包含程式碼產生器或執行封裝相關工作的建置後工具。

例如: 

```json
{
    "tools": {
    "MyObfuscator": "1.2.4"
    }
}
```

## <a name="scripts"></a>指令碼
類型：Object

定義在建置流程期間執行的指令碼的物件。 這個物件中的每個索引鍵都會識別指令碼在建置中的執行位置。 每個值都是具有要執行之指令碼的字串，或包含依序執行之指令碼的字串陣列。
支援的事件如下︰
* precompile
* postcompile
* prepublish
* postpublish

例如: 

```json
{
    "scripts": {
        "precompile": "generateCode.cmd",
        "postcompile": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
    }
}
```

## <a name="buildoptions"></a>buildOptions
類型：Object

其屬性控制編譯各部分的物件。 有效屬性如下所列。 也可以根據目標架構指定 (如[架構小節](#frameworks)中所述)。

例如: 

```json
    "buildOptions": {
      "allowUnsafe": true,
      "emitEntryPoint": true
    }
```

### <a name="define"></a>define
類型：String[]

可用於程式碼中條件式編譯的 define 清單 (例如 "DEBUG" 或 "TRACE")。

例如: 

```json
{
    "buildOptions": {
        "define": ["TEST", "OTHERCONDITION"]
    }
}
```

### <a name="nowarn"></a>nowarn
類型：String[]

要忽略的警告清單。

例如：

```json
{
    "buildOptions": {
        "nowarn": ["CS0168", "CS0219"]
    }
}
```

這會忽略警告 `The variable 'var' is assigned but its value is never used` 和 `The variable 'var' is assigned but its value is never used`

### <a name="additionalarguments"></a>additionalArguments
類型：String[]

將傳遞給編譯器的額外引數清單。

例如: 

```json
{
    "buildOptions": {
        "additionalArguments": ["/parallel", "/nostdlib"]
    }
}
```

### <a name="warningsaserrors"></a>warningsAsErrors
類型：布林值

`true` 將所有警告視為錯誤；否則為 `false`。 預設為 `false`。

例如: 

```json
{
    "buildOptions": {
        "warningsAsErrors": true
    }
}
```

### <a name="allowunsafe"></a>allowUnsafe
類型：布林值

`true` 允許這個專案中不安全的程式碼；否則為 `false`。 預設為 `false`。

例如: 

```json
{
    "buildOptions": {
        "allowUnsafe": true
    }
}
```

### <a name="emitentrypoint"></a>emitEntryPoint
類型：布林值

`true` 會建立可執行檔；`false` 則會產生程式庫。 預設為 `false`。

例如: 

```json
{
    "buildOptions": {
        "emitEntryPoint": true
    }
}
```

### <a name="optimize"></a>optimize
類型：布林值

`true` 讓編譯器將這個專案中的程式碼最佳化；否則為 `false`。 預設為 `false`。

例如: 

```json
{
    "buildOptions": {
        "optimize": true
    }
}
```

### <a name="platform"></a>platform
類型：String

目標平台名稱，例如 AnyCpu、x86 或 x64。

例如: 

```json
{
    "buildOptions": {
        "platform": "x64"
    }
}
```

### <a name="languageversion"></a>languageVersion
類型：String

編譯器所使用語言的版本︰ISO-1、ISO-2、3、4、5、6 或 Default。

例如: 

```json
{
    "buildOptions": {
        "languageVersion": "5"
    }
}
```

### <a name="keyfile"></a>keyFile
類型：String

用來簽署這個組件之金鑰檔案的路徑。

例如: 

```json
{
    "buildOptions": {
        "keyFile": "../keyfile.snk"
    }
}
```

### <a name="delaysign"></a>delaySign
類型：布林值

`true` 會延遲簽署；否則為 `false`。 預設為 `false`。

例如: 

```json
{
    "buildOptions": {
        "delaySign": true
    }
}
```

### <a name="publicsign"></a>publicSign
類型：布林值

`true` 允許簽署所產生的組件；否則為 `false`。 預設為 `false`。

例如: 

```json
{
    "buildOptions": {
        "publicSign": true
    }
}
```

### <a name="debugtype"></a>debugType
類型：String

表示要產生的符號檔 (PDB 檔案) 類型。 選項是「可攜式」(適用於 .NET Core 專案) 還是「完整」(傳統僅限 Windows 的 PDB 檔案)。

例如: 

```json
{
    "buildOptions": {
        "debugType": "portable"
    }
}
```

### <a name="xmldoc"></a>xmlDoc
類型：布林值

`true` 會從原始程式碼中的三個斜線註解產生 XML 文件；否則為 `false`。 預設為 `false`。

例如: 

```json
{
    "buildOptions": {
        "xmlDoc": true
    }
}
```

### <a name="preservecompilationcontext"></a>preserveCompilationContext
類型：布林值

`true` 會保留參考組件和其他內容資料，以允許進行執行階段編譯；否則為 `false`。 預設為 `false`。

例如: 

```json
{
    "buildOptions": {
        "preserveCompilationContext": true
    }
}
```

### <a name="outputname"></a>outputName
類型：String

變更輸出檔案的名稱。 

例如: 

```json
{
    "buildOptions": {
        "outputName": "MyApp"
    }
}
```

### <a name="compilername"></a>compilerName
類型：String

用於這個專案的編譯器名稱。 預設為 `csc`。 目前支援 `csc` (C# 編譯器) 或 `fsc` (F# 編譯器)。
 
例如: 

```json
{
    "compilerName": "fsc"
}
```
    
### <a name="compile"></a>compile
類型：Object

包含編譯組態屬性的物件。

#### <a name="include"></a>include
類型：具有萬用字元模式的 String 或 String[]。

指定要包含在建置中的檔案。 模式的根目錄位於專案資料夾中。 預設為 none。

例如: 

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
類型：具有萬用字元模式的 String 或 String[]。

指定要從建置中排除的檔案。 排除模式的優先順序高於包含模式，因此將會排除在兩者中找到的檔案。 模式的根目錄位於專案資料夾中。 預設為 none。

例如: 

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

類型：具有萬用字元模式的 String 或 String[]。

要包含的檔案路徑清單。 路徑的根目錄位於專案資料夾中。 這份清單的優先順序高於包含和排除萬用字元模式，因此仍會包含這裡和排除萬用字元模式中所列的檔案。 預設為 none。

例如: 

```json
{
    "includeFiles": []
}
```

#### <a name="excludefiles"></a>excludeFiles

類型：具有萬用字元模式的 String 或 String[]。

要排除的檔案路徑清單。 路徑的根目錄位於專案資料夾中。 這份清單的優先順序高於萬用字元模式和包含路徑，因此會排除在所有項目中找到的檔案。 預設為 none。

例如: 

```json
{
    "excludeFiles":[],
}
```

#### <a name="builtins"></a>builtIns

類型：Object

系統所提供的預設值。 它可以有與 `include` 和 `exclude` 屬性的對應值合併的 `include` 和 `exclude` 萬用字元模式。

例如: 

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>對應
類型：Object

物件的索引鍵代表輸出配置中的目的地路徑。

值為字串或物件，代表要包含之檔案的來源路徑。  物件呈現可以有它自己的 `include`、`exclude`、`includeFiles` 和 `excludeFiles` 區段。

String 範例：

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Object 範例：

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

### <a name="embed"></a>embed
類型：Object

包含編譯組態屬性的物件。

#### <a name="include"></a>include
類型：具有萬用字元模式的 String 或 String[]。

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
類型：具有萬用字元模式的 String 或 String[]。

指定要從建置中排除的檔案。

例如: 

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

類型：具有萬用字元模式的 String 或 String[]。

```json
{
    "includeFiles":[],
}
```

#### <a name="excludefiles"></a>excludeFiles

類型：具有萬用字元模式的 String 或 String[]。

```json
{
    "excludeFiles":[],
}
```

#### <a name="builtins"></a>builtIns
類型：Object

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>對應
類型：Object

物件的索引鍵代表輸出配置中的目的地路徑。

值為字串或物件，代表要包含之檔案的來源路徑。  物件呈現可以有它自己的 `include`、`exclude`、`includeFiles` 和 `excludeFiles` 區段。

String 範例：

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Object 範例：

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

### <a name="copytooutput"></a>copyToOutput
類型：Object

包含編譯組態屬性的物件。

#### <a name="include"></a>include
類型：具有萬用字元模式的 String 或 String[]。

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
類型：具有萬用字元模式的 String 或 String[]。

指定要從建置中排除的檔案。

例如: 

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

類型：具有萬用字元模式的 String 或 String[]。

```json
{
    "includeFiles":[],
}
```

#### <a name="excludefiles"></a>excludeFiles

類型：具有萬用字元模式的 String 或 String[]。

```json
{
    "excludeFiles":[],
}
```

#### <a name="builtins"></a>builtIns
類型：Object

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>對應
類型：Object

物件的索引鍵代表輸出配置中的目的地路徑。

值為字串或物件，代表要包含之檔案的來源路徑。  物件呈現可以有它自己的 `include`、`exclude`、`includeFiles` 和 `excludeFiles` 區段。

String 範例：

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Object 範例：

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

## <a name="publishoptions"></a>publishOptions
類型：Object

包含編譯組態屬性的物件。

### <a name="include"></a>include
類型：具有萬用字元模式的 String 或 String[]。

```json
{
    "include":["wwwroot", "Views"]
}
```

### <a name="exclude"></a>exclude
類型：具有萬用字元模式的 String 或 String[]。

指定要從建置中排除的檔案。

例如: 

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

### <a name="includefiles"></a>includeFiles

類型：具有萬用字元模式的 String 或 String[]。

```json
{
    "includeFiles":[],
}
```

### <a name="excludefiles"></a>excludeFiles

類型：具有萬用字元模式的 String 或 String[]。

```json
{
    "excludeFiles":[],
}
```

### <a name="builtins"></a>builtIns
類型：Object

```json
{
    "builtIns":{}
}
```

### <a name="mappings"></a>對應
類型：Object

物件的索引鍵代表輸出配置中的目的地路徑。

值為字串或物件，代表要包含之檔案的來源路徑。  物件呈現可以有它自己的 `include`、`exclude`、`includeFiles` 和 `excludeFiles` 區段。

String 範例：

```json
{
    "mappings": {
        "dest/file": "./src/file",
        "dest/folder/": "./src/folder/**/*"
    }
}
```

Object 範例：

```json
{
    "mappings": {
        "dest/file":{
            "include":"./src/file"
        },
        "dest/folder/":{
            "include":"./src/folder/**/*"
        }
    }
}
```

## <a name="runtimeoptions"></a>runtimeOptions
類型：Object

指定要在初始化期間提供給執行階段的參數。

### <a name="configproperties"></a>configProperties
類型：Object

包含用來設定執行階段和架構的組態屬性。

#### <a name="systemgcserver"></a>System.GC.Server
類型：布林值

`true` 允許伺服器記憶體回收；否則為 `false`。 預設為 `false`。

例如: 

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.Server": true
        }
    }
}
```

#### <a name="systemgcconcurrent"></a>System.GC.Concurrent
類型：布林值

`true` 允許並行記憶體回收；否則為 `false`。 預設為 `false`。

例如: 

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.Concurrent": true
        }
    }
}
```

#### <a name="systemgcretainvm"></a>System.GC.RetainVM
類型：布林值

`true` 會將應該刪除的區段放在待命清單上以供日後使用，而不是將其釋回作業系統 (OS)；否則為 `false`。
預設為 `false`。

例如: 

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.RetainVM": true
        }
    }
}
```

#### <a name="systemthreadingthreadpoolminthreads"></a>System.Threading.ThreadPool.MinThreads
類型：Integer

覆寫 ThreadPool 背景工作集區的執行緒數目下限。

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.Threading.ThreadPool.MinThreads": 4
        }
    }
}
```

#### <a name="systemthreadingthreadpoolmaxthreads"></a>System.Threading.ThreadPool.MaxThreads
類型：Integer

覆寫 ThreadPool 背景工作集區的執行緒數目上限。

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.Threading.ThreadPool.MaxThreads": 25
        }
    }
}
```

### <a name="framework"></a>架構
類型：Object

包含要在啟用應用程式時使用的共用架構屬性。 具有本區段表示應用程式是設計成使用共用可轉散發架構的可攜式應用程式。

#### <a name="name"></a>name
類型：String

共用架構的名稱。

```json
{
    "runtimeOptions": {
        "framework": {
            "name": "Microsoft.DotNetCore"
        }
    }
}
```

#### <a name="version"></a>版本
類型：String

共用架構的版本。

```json
{
    "runtimeOptions": {
        "framework": {
            "version": "1.0.1"
        }
    }
}
```

### <a name="applypatches"></a>applyPatches
類型：布林值

`true` 會使用相同或較高版本中只在 `SemVer` 修補程式欄位中不同的架構。 `false` 讓主機僅使用正確的 Framework 版本。 預設為 `true`。

```json
{
    "runtimeOptions": {
        "applyPatches": false
    }
}
```

## <a name="packoptions"></a>packOptions
類型：Object

定義將專案輸出封裝到 NuGet 套件的相關選項。

### <a name="summary"></a>摘要
類型：String

專案的簡短描述。

例如: 

```json
{
    "packOptions": {
        "summary": "This is my library."
    }
}
```

### <a name="tags"></a>標記
類型：String[]

具有專案標記的字串陣列，用於在 NuGet 中進行搜尋。

例如: 

```json
{
    "packOptions": {
        "tags": ["hyperscale", "cats"]
    }
}
```

### <a name="owners"></a>owners
類型：String[]

具有專案擁有者名稱的字串陣列。

例如: 

```json
{
    "packOptions": {
        "owners": ["Fabrikam", "Microsoft"]
    }
}
```

### <a name="releasenotes"></a>releaseNotes
類型：String

專案的版本資訊。

例如: 

```json
{
    "packOptions": {
        "releaseNotes": "Initial version, implemented flimflams."
    }
}
```

### <a name="iconurl"></a>iconUrl
類型：String

將用於各個位置 (例如套件總管) 的圖示 URL。

例如: 

```json
{
    "packOptions": {
        "iconUrl": "http://www.mylibrary.gov/favicon.ico"
    }
}
```

### <a name="projecturl"></a>projectUrl
類型：String

專案首頁的 URL。

例如: 

```json
{
    "packOptions": {
        "projectUrl": "http://www.mylibrary.gov"
    }
}
```

### <a name="licenseurl"></a>licenseUrl
類型：String

專案所使用授權的 URL。

例如: 

```json
{
    "packOptions": {
        "licenseUrl": "http://www.mylibrary.gov/licence"
    }
}
```

### <a name="requirelicenseacceptance"></a>requireLicenseAcceptance
類型：布林值

`true` 會顯示在安裝套件時接受套件授權的提示；否則為 `false`。 僅用於 NuGet 套件，其他情況則予以忽略。 預設為 `false`。

例如: 

```json
{
    "packOptions": {
        "requireLicenseAcceptance": true
    }
}
```
   
### <a name="repository"></a>儲存機制
類型：Object

包含在其中儲存專案之存放庫的相關資訊。

#### <a name="type"></a>類型
類型：String

存放庫的類型。 預設值是 "git"。

例如: 

```json
{
    "packOptions": {
        "repository": {
            "type": "git"
        }
    }
}
```

#### <a name="url"></a>URL
類型：String

在其中儲存專案之存放庫的 URL。

例如: 

```json
{
    "packOptions": {
        "repository": {
            "url": "http://github.com/dotnet/corefx"
        }
    }
}
```

### <a name="files"></a>個檔案
類型：Object

#### <a name="include"></a>include
類型：具有萬用字元模式的 String 或 String[]。

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
類型：具有萬用字元模式的 String 或 String[]。

指定要從建置中排除的檔案。

例如: 

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

類型：具有萬用字元模式的 String 或 String[]。

```json
{
    "includeFiles":[]
}
```

#### <a name="excludefiles"></a>excludeFiles

類型：具有萬用字元模式的 String 或 String[]。

```json
{
    "excludeFiles":[]
}
```

#### <a name="builtins"></a>builtIns
類型：Object

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>對應
類型：Object

物件的索引鍵代表輸出配置中的目的地路徑。

值為字串或物件，代表要包含之檔案的來源路徑。  物件呈現可以有它自己的 `include`、`exclude`、`includeFiles` 和 `excludeFiles` 區段。 

String 範例：

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Object 範例：

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

## <a name="analyzeroptions"></a>analyzerOptions
類型：Object

具有程式碼分析器所使用屬性的物件。

例如: 

```json
{
    "analyzerOptions": { }
}
```

### <a name="languageid"></a>languageId
類型：String

要分析的語言識別碼。 "cs" 代表 C#、"vb" 代表 Visual Basic，而 "fs" 代表 F#。

例如: 

```json
"analyzerOptions": {
    "languageId": "vb"
}
```

## <a name="configurations"></a>組態
類型：Object

其屬性定義這個專案之不同組態的物件 (例如「偵錯」和「發行」)。 每個值都是一個物件，而物件可以包含具有這個組態特有選項的 `buildOptions` 物件。

例如: 

```json
"configurations": {
    "Release": {
        "buildOptions": {
            "allowUnsafe": false
        }
    }
}
```

## <a name="frameworks"></a>frameworks
類型：Object

指定這個專案所支援的架構 (例如 .NET Framework 或通用 Windows 平台 (UWP))。 必須是有效的目標 Framework Moniker (TFM)。 每個值都是一個物件，而物件可以包含這個架構特有資訊 (例如 `buildOptions`、`analyzerOptions`、`dependencies` 以及下列各節中的屬性)。

例如: 

```json
"frameworks": {
    "netcoreapp1.0": {
        "buildOptions": {
            "define": ["FOO", "BIZ"]
        }
    }
}
```

### <a name="dependencies"></a>相依性
類型：Object

這個架構特有的相依性。 這適用於您不能只指定跨所有目標的套件層級相依性。 這麼做的原因可以包含一個目標，這個目標缺乏其他目標具有的內建支援，或需要與其他目標不同的相依性版本。 若要查看這個節點的其他屬性清單，請參閱先前的[相依性](#dependencies)小節。

例如: 

```json
    "frameworks": {
        "netstandard1.5": {
        "dependencies": {
            "Microsoft.Extensions.JsonParser.Sources": "1.0.0-rc2-20221"
        }
    }
}
```

### <a name="frameworkassemblies"></a>frameworkAssemblies
類型：Object

與相依性類似，但包含 GAC 中不是 NuGet 套件的組件的參考。 也可以指定要使用的版本以及相依性類型。 這用於將目標設為 .NET Framework 和可攜式類別庫 (PCL) 目標時。 您只能建置在 Windows 上指定這個項目的專案。

例如: 

```json
"frameworks": {
    "net451": {
        "frameworkAssemblies": {
            "System.Runtime": {
                "type": "build",
                "version": "4.0.0"
            }
        }
    }
}
```

### <a name="wrappedproject"></a>wrappedProject
類型：String

指定相依性專案的位置。 

例如: 

```json
"frameworks": {
    "net451": {
        "wrappedProject": "MyProject.csproj"
    }
}
```

### <a name="bin"></a>bin
類型：Object

這用來包裝 DLL 檔案。 您可以參考並產生包含這個 DLL 的套件。 

它包含值為組件路徑的單一 String 屬性 `assembly`。   

例如: 

```json
"frameworks": {
    "netcoreapp1.0": {
        "bin": {
            "assembly": "c:/otherProject/otherdll.dll"
        }
    }
}
```

## <a name="runtimes"></a>runtimes
類型：Object

專案所支援的[執行階段識別項 (RID)](../rid-catalog.md) 清單 (在發行[獨立部署](../deploying/index.md#self-contained-deployments-scd)時使用)。

例如: 

```json
"runtimes": {
    "win7-x64": {},
    "win8-x64": {},
    "win81-x64": {},
    "win10-x64": {},
    "osx.10.11-x64": {},
    "ubuntu.16.04-x64": {}
}
```

## <a name="usersecretsid"></a>userSecretsId
類型：String

指定要在開發階段使用的使用者密碼識別碼。 如需詳細資訊，請參閱 [Safe storage of app secrets during development](https://docs.asp.net/en/latest/security/app-secrets.html) (在開發期間安全儲存應用程式密碼)。

例如: 

```json
{
    "userSecretsId": "aspnet-WebApp1-c23d27a4-eb88-4b18-9b77-2a93f3b15119"
}
```



<!--HONumber=Nov16_HO1-->


