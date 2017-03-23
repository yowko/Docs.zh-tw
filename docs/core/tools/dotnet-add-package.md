---
title: "dotnet-add package 命令 | Microsoft Docs"
description: "dotnet-add package 命令提供方便的選項，將 NuGet 套件參考新增至專案。"
keywords: "dotnet-add, CLI, CLI 命令, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 88e0da69-a5ea-46cc-8b46-5493242b7af9
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 806f4383452cb250f302dc30ab2d59f7e4772026
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-add-package"></a>dotnet-add package

## <a name="name"></a>名稱

`dotnet-add package` - 將套件參考新增至專案檔。

## <a name="synopsis"></a>概要

```
dotnet add [project] package <package_name> [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory]
dotnet add package [-h|--help]
```

## <a name="description"></a>說明

`dotnet add package` 提供方便的選項，將套件參考新增至專案檔。 執行命令之後，可透過相容性檢查，確保嘗試新增的套件與專案中的所有架構皆相容。 如果通過檢查，就會執行 [restore](dotnet-restore.md) 並將 `<PackageReference>` 片段新增至專案檔。

例如，將 `Newtonsoft.Json` 新增至*ToDo.csproj* 會產生類似如下的輸出：

```
Microsoft (R) Build Engine version 15.1.545.13942
Copyright (C) Microsoft Corporation. All rights reserved.

  Writing /var/folders/gj/1mgg_4jx7mbdqbhw1kgcpcjr0000gn/T/tmpm0kTMD.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'ToDo.csproj'.
log  : Restoring packages for ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 119ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/9.0.1/newtonsoft.json.9.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/9.0.1/newtonsoft.json.9.0.1.nupkg 27ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '9.0.1' added to file 'ToDo.csproj'.
```

*ToDo.csproj* 檔案現在會包含參考套件的 [`<PackageReference>`](https://docs.microsoft.com/nuget/consume-packages/package-references-in-project-files) 片段。

```xml
<PackageReference Include="Newtonsoft.Json">
  <Version>9.0.1</Version>
</PackageReference>
```

## <a name="arguments"></a>引數

`project`

要處理的專案檔。 如果未指定，命令會在目前的目錄中搜尋一個專案檔。

`package_name`

要新增的套件參考。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

`-v|--version <VERSION>`

套件的版本。

`-f|--framework <FRAMEWORK>`

只有在以特定架構為目標時，才能新增套件參考。

`-n|--no-restore`

新增套件參考，而不執行還原預覽和相容性檢查。

`-s|--source <SOURCE>`

使用要在還原作業期間使用的特定 NuGet 套件來源。

`--package-directory <PACKAGE_DIRECTORY>`

將套件還原至指定的目錄。

## <a name="examples"></a>範例

將 `Newtonsoft.Json` NuGet 套件新增至專案：

`dotnet add package Newtonsoft.Json`

將特定版本的套件新增至專案：

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

使用特定 NuGet 來源新增套件：

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`

