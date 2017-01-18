---
title: "使用 MSBuild 建置 .NET Core 專案"
description: "使用 MSBuild 建置 .NET Core 專案"
keywords: .NET, .NET Core
author: dsplaisted
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13c66464-4f14-4db6-aa8b-06f25e7ba894
translationtype: Human Translation
ms.sourcegitcommit: a04755da6417bb28bad5f28a18ead9feeba2d957
ms.openlocfilehash: ee8f409bf11f4b4a7136b886114616b233bc2cc0

---

# <a name="using-msbuild-to-build-net-core-projects"></a>使用 MSBuild 建置 .NET Core 專案

.NET Core 工具即將[從 project.json 移到 MSBuild 專案](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/)。
我們預期使用 MSBuild 的第一版 .NET Core 工具會與下一版 Visual Studio 一起出貨。  不過，您可以立即針對 .NET Core 專案使用 MSBuild，此頁面即顯示其方式。

我們建議目前「新」專案以 .NET Core 為目標的大多數人，能使用預設的 project.json 工具經驗，原因如下︰

- MSBuild 還不支援 project.json 的許多優點
- 許多 ASP.NET 架構工具目前無法用於 MSBuild 專案
- 當我們發行使用 MSBuild 的 .NET Core 工具時，將能夠自動從 project.json 轉換為 MSBuild 專案 

針對已經使用 MSBuild 且打算移植到 .NET Core 的現有專案，或者針對 project.json 專案不太支援的案例中，在組建使用 MSBuild 的擴充性時，您可能會想要使用 MSBuild 來設定 .NET Core 為目標。

## <a name="prerequisites"></a>必要條件

- [Visual Studio 2015 Update 3](https://www.visualstudio.com/en-us/news/releasenotes/vs2015-update3-vs) 或更高版本
- [適用於 Visual Studio 的 .NET Core 工具](https://www.visualstudio.com/downloads/download-visual-studio-vs)
- NuGet Visual Studio 擴充功能 [v3.5.0-beta](https://dist.nuget.org/visualstudio-2015-vsix/v3.5.0-beta/NuGet.Tools.vsix) 或更新版本

## <a name="creating-a-library-targeting-net-core"></a>建立以 .NET Core 為目標的程式庫

1. 在 Visual Studio 功能表列中，選擇 [檔案] |  [新增] |  [專案]，然後選取 [類別庫 (可攜式)]

  ![新增專案](./media/target-dotnetcore-with-msbuild/new-project-dialog-class-library-portable.png)

2. 選擇專案的名稱和位置，然後按一下 [確定]

3. 會出現 [新增可攜式類別庫] 對話方塊。  選取 [.NET Framework 4.6] 和 [ASP.NET Core 1.0] 作為目標，然後按一下 [確定]

  ![可攜式目標對話方塊](./media/target-dotnetcore-with-msbuild/pcl-targets-dialog-net46-aspnetcore10.png)

4. 在方案總管中，以滑鼠右鍵按一下專案，然後選擇 [屬性]。
5. 在專案屬性的 [程式庫] 索引標籤中，按一下 [以 .NET 平台標準為目標] 連結，然後在顯示的對話方塊按一下 [是]
6. 在專案中開啟 `project.json` 檔案，並進行下列變更︰
    - 將 `NETStandard.Library` 套件的版本號碼變更為 `1.6.0` (這是套件的 .NET Core 1.0 版本)
    - 將下面 `imports` 定義新增於 `netstandard1.6` 架構定義內。  這可讓您的專案參考 .NET Core 相容，且尚未更新到以 .NET 標準為目標的 NuGet 套件

        ```json
        "netstandard1.6": {
            "imports": [ "dnxcore50", "portable-net452" ]
        }
        ```

## <a name="creating-a-net-core-console-application"></a>建立 .NET Core 主控台應用程式
建置 .NET Core 的主控台應用程式需要對 MSBuild 建置程序進行一些自訂。  您可以在 [corefxlab](https://github.com/dotnet/corefxlab) 儲存機制中，找到 .NET Core 主控台應用程式的範例專案，稱為 [CoreApp](https://github.com/dotnet/corefxlab/tree/master/samples/NetCoreSample/CoreApp)。  另一個不錯的選項是從 [coretemplate](https://github.com/mellinoe/coretemplate) 開始，它使用不同的 MSBuild 目標檔案來以 .NET Core 為目標，而不是直接將變更放在專案檔案中。  

此外，也可以藉由在 Visual Studio 中建立專案，並修改它以 .NET Core 為目標來開始。  下列指示顯示讓這發揮作用的最少步驟。  相對於 [CoreApp](https://github.com/dotnet/corefxlab/tree/master/samples/NetCoreSample/CoreApp) 或 [coretemplate](https://github.com/mellinoe/coretemplate)，以這種方式建立的專案不會包含以 Linux 和 macOS 為目標的組態。

1. 在 Visual Studio 功能表列中，選擇 [檔案] |  [新增] |  [專案]，然後選取 [主控台應用程式]
2. 選擇專案的名稱和位置，然後按一下 [確定]
3. 在方案總管中，以滑鼠右鍵按一下專案，然後選擇 [屬性]，再前往 [建置] 索引標籤。
4. 在 [組態] 下拉式清單 (在 [屬性] 頁面的頂端) 中，選取 [所有組態]，然後將 [平台目標] 變更為 [x64]
5. 從專案刪除 `app.config` 檔
6. 新增 `project.json` 檔案到專案中，內容如下︰

    ```json
    {
        "dependencies": {
            "Microsoft.NETCore.App": "1.0.0-rc2-3002702"
        },
        "runtimes": {
            "win7-x64": { },
            "ubuntu.14.04-x64": { },
            "osx.10.10-x64": { }
        },
        "frameworks": {
            "netcoreapp1.0": {
                "imports": [ "dnxcore50", "portable-net452" ]
            }
        }
    }
    ```

7. 在方案總管中，以滑鼠右鍵按一下專案，選擇 [卸載專案]，然後再以滑鼠右鍵按一下並選擇 [編輯 _MyProj.csproj_]，並進行下列變更
    - 移除所有的預設 `Reference` 項目 (`System`、`System.Core` 等等)。
    - 將下列屬性新增至專案中的第一個 `PropertyGroup`︰

        ```xml
        <TargetFrameworkIdentifier>.NETCoreApp</TargetFrameworkIdentifier>
        <TargetFrameworkVersion>v1.0</TargetFrameworkVersion>
        <BaseNuGetRuntimeIdentifier>win7</BaseNuGetRuntimeIdentifier>
        <NoStdLib>true</NoStdLib>
        <NoWarn>$(NoWarn);1701</NoWarn>
        ```

    - 在檔案結尾新增下列內容 (匯入 `Microsoft.CSharp.Targets` 之後)：

        ```xml
        <PropertyGroup>
            <!-- We don't use any of MSBuild's resolution logic for resolving the framework, so just set these two
                    properties to any folder that exists to skip the GetReferenceAssemblyPaths task (not target) and
                    to prevent it from outputting a warning (MSB3644).
                -->
            <_TargetFrameworkDirectories>$(MSBuildThisFileDirectory)</_TargetFrameworkDirectories>
            <_FullFrameworkReferenceAssemblyPaths>$(MSBuildThisFileDirectory)</_FullFrameworkReferenceAssemblyPaths>

            <!-- MSBuild thinks all EXEs need binding redirects, not so for CoreCLR! -->
            <AutoUnifyAssemblyReferences>true</AutoUnifyAssemblyReferences>
            <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>

            <!-- Set up debug options to run with host, and to use the CoreCLR debug engine -->
            <StartAction>Program</StartAction>
            <StartProgram>$(TargetDir)dotnet.exe</StartProgram>
            <StartArguments>$(TargetPath)</StartArguments>
            <DebugEngines>{2E36F1D4-B23C-435D-AB41-18E608940038}</DebugEngines>
        </PropertyGroup>
        ```

    - 關閉 .csproj 檔案，並在 Visual Studio 中重新載入專案

8. 您應該能夠在 Visual Studio 中使用 F5 執行程式，或從命令列的輸出資料夾中使用`dotnet MyApp.exe` 



<!--HONumber=Nov16_HO3-->


