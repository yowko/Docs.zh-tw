---
title: "dotnet-pack 命令 - .NET Core CLI"
description: "dotnet-pack 命令會建立 .NET Core 專案的 NuGet 套件。"
keywords: "dotnet-pack, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8dbbb3f7-b817-4161-a6c8-a3489d05e051
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 04b967fdf6578098caae8c21604c5d6160eb6775
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-pack"></a>dotnet-pack

## <a name="name"></a>名稱

`dotnet-pack` - 將程式碼封裝到 NuGet 套件。

## <a name="synopsis"></a>概要

`dotnet pack [<PROJECT>] [-o|--output] [--no-build] [--include-symbols] [--include-source] [-c|--configuration] [--version-suffix <VERSION_SUFFIX>] [-s|--serviceable] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>描述

`dotnet pack` 命令會建置專案，並建立 NuGet 套件。 此命令的結果是 NuGet 套件。 如果有 `--include-symbols` 選項，會建立另一個包含偵錯符號的套件。 

封裝專案的 NuGet 相依性會新增至 *.nuspec* 檔案，因此在安裝套件時可以正確地解析它們。 專案對專案參考不會封裝到專案內。 目前，如果您有專案對專案相依性，則必須一個專案各一個套件。

`dotnet pack` 預設會先建置專案。 如果您想要避免這種行為，請傳遞 `--no-build` 選項。 這通常適用於您知道先前剛建立程式碼的持續整合 (CI) 組建案例。

您可以提供 MSBuild 屬性給 `dotnet pack` 命令來壓縮程序。 如需詳細資訊，請參閱 [NuGet 中繼資料屬性](csproj.md#nuget-metadata-properties)和 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。

## <a name="arguments"></a>引數

`PROJECT` 
    
要封裝的專案。 它可以是 [csproj 檔案](csproj.md)或目錄的路徑。 如果省略，則會預設為目前目錄。 

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。  

`-o|--output <OUTPUT_DIRECTORY>`

將已建置的套件放置在指定的目錄中。 

`--no-build`

請不要在封裝之前建置專案。 

`--include-symbols`

產生符號 `nupkg`。 

`--include-source`

將原始程式檔納入 NuGet 套件。 原始程式檔包含在 `nupkg` 中的 `src` 資料夾。 

`-c|--configuration <CONFIGURATION>`

要在建置專案時使用的組態。 如果未指定，組態預設值為 `Debug`。

`--version-suffix <VERSION_SUFFIX>`

在專案中定義 `$(VersionSuffix)` MSBuild 屬性的值。

`-s|--serviceable`

在套件中設定可提供服務的旗標。 如需詳細資訊，請參閱 [.NET 部落格︰.NET 4.5.1 支援適用於 .NET NuGet 程式庫的 Microsoft 安全性更新 (英文)](https://aka.ms/nupkgservicing)。

`--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

## <a name="examples"></a>範例

封裝目前目錄中的專案：

`dotnet pack`

封裝 `app1` 專案：

`dotnet pack ~/projects/app1/project.csproj`
    
封裝目前目錄中的專案，並將產生的套件放置到 `nupkgs` 資料夾中：

`dotnet pack --output nupkgs`

將目前目錄中的專案封裝到 `nupkgs` 資料夾，並略過建置步驟︰

`dotnet pack --no-build --output nupkgs`

在 *.csproj* 檔案中將專案的版本尾碼設定為 `<VersionSuffix>$(VersionSuffix)</VersionSuffix>`，封裝目前的專案並使用指定尾碼更新產生的套件版本︰

`dotnet pack --version-suffix "ci-1234"`

使用 `PackageVersion` MSBuild 屬性將封裝版本設定為 `2.1.0`：

`dotnet pack /p:PackageVersion=2.1.0`

