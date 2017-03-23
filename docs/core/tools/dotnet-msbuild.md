---
title: "dotnet-msbuild 命令 | Microsoft Docs"
description: "dotnet-msbuild 命令提供對 MSBuild 命令列的存取。"
keywords: "dotnet-msmsbuild, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: ffdc40ba-ef33-463e-aa35-b0af1fe615a2
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: a000e49a8672affe5b3bb9bd8a5f7e8095ab0aa9
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-msbuild"></a>dotnet-msbuild

## <a name="name"></a>名稱

`dotnet-msbuild` - 建置專案和其所有相依性。

## <a name="synopsis"></a>概要

```
dotnet msbuild <msbuild_arguments>
dotnet msbuild [-h]
```

## <a name="description"></a>說明

`dotnet msbuild` 命令可存取完整功能的 MSBuild 

命令與現有的 MSBuild 命令列用戶端具有完全相同的功能。 選項完全一樣。 您可以使用 [MSBuild 命令列參考](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference)以熟悉選項。 

## <a name="examples"></a>範例

建置專案和其相依性：

`dotnet msbuild`

使用發行組態來建置專案和其相依性︰

`dotnet msbuild /p:Configuration=Release`

執行發行目標並針對 `osx.10.11-x64` RID 發行：

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`
