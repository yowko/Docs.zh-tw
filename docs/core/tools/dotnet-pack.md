---
title: "dotnet-pack 命令 | Microsoft Docs"
description: "dotnet-pack 命令會建立 .NET Core 專案的 NuGet 套件。"
keywords: "dotnet-pack, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8dbbb3f7-b817-4161-a6c8-a3489d05e051
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 88289a09a22bf20ec9089ec6a74269cd682a305b
ms.lasthandoff: 03/07/2017

---

#<a name="dotnet-pack"></a>dotnet-pack

## <a name="name"></a>名稱

`dotnet-pack` - 將程式碼封裝到 NuGet 套件。

## <a name="synopsis"></a>概要

```
dotnet pack [project] [-o|--output] [--no-build] [--include-symbols] [--include-source] [-c|--configuration] [--version-suffix] [-s|--serviceable] [-v|--verbosity]
dotnet pack [-h|--help]
```

## <a name="description"></a>描述

`dotnet pack` 命令會建置專案，並建立 NuGet 套件。 此命令的結果是 NuGet 套件。 如果有 `--include-symbols` 選項，將會建立另一個包含偵錯符號的套件。 

正在封裝之專案的 NuGet 相依性會新增至 `nuspec` 檔案，因此可以在安裝套件時進行解析。 專案對專案參考不會封裝到專案內。 目前，如果您有專案對專案相依性，則一個專案需要有一個套件。

`dotnet pack` 預設會先建置專案。 如果您想要避免這種情況，請傳遞 `--no-build` 選項。 例如，這可能適用於您知道先前剛建立程式碼的持續整合 (CI) 組建案例。 

## <a name="arguments"></a>引數

`project` 
    
要封裝的專案。 它可以是 [csproj 檔案](csproj.md)或目錄的路徑。 省略時，將預設為目前的目錄。 

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。  

`-o|--output <OUTPUT_DIRECTORY>`

將已建置的套件放置在指定的目錄中。 

`--no-build`

請不要在封裝之前建置專案。 

`--include-symbols`

產生符號 nupkg。 

`--include-source`

將原始程式檔納入 NuGet 套件。 原始程式檔包含在 `nupkg` 中的 `src` 資料夾。 

`-c|--configuration <Debug|Release>`

要在建置專案時使用的組態。 如果未指定，將預設為 `Debug`。

`--version-suffix <VERSION_SUFFIX>`

在專案中定義 $(VersionSuffix) MSBuild 屬性的值。

`-s|--serviceable`

在套件中設定可提供服務的旗標。 如需詳細資訊，請參閱 https://aka.ms/nupkgservicing。

`--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

## <a name="examples"></a>範例

封裝目前目錄中的專案：

`dotnet pack`

封裝 app1 專案：

`dotnet pack ~/projects/app1/project.csproj`
    
封裝目前目錄中的專案，並將產生的套件放置到指定的資料夾中：

`dotnet pack --output nupkgs`

將目前目錄中的專案封裝到指定的資料夾，並略過建置步驟︰

`dotnet pack --no-build --output nupkgs`

封裝目前的專案，並使用指定的尾碼來更新產生的套件版本。 專案的版本尾碼會在 *.csproj* 檔案中設定為 `<VersionSuffix>$(VersionSuffix)</VersionSuffix>`。

`dotnet pack --version-suffix "ci-1234"`
