---
title: "dotnet-msbuild 命令 - .NET Core CLI | Microsoft Docs"
description: "dotnet-msbuild 命令提供對 MSBuild 命令列的存取。"
keywords: "dotnet-msmsbuild, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 05/24/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: ffdc40ba-ef33-463e-aa35-b0af1fe615a2
ms.translationtype: Human Translation
ms.sourcegitcommit: df4b2ddd322e4bd2ebaf444439107e88a983f988
ms.openlocfilehash: 2267ef0b5785959456ea443405b6708a423d00ba
ms.contentlocale: zh-tw
ms.lasthandoff: 05/30/2017

---

# dotnet-msbuild
<a id="dotnet-msbuild" class="xliff"></a>

## 名稱
<a id="name" class="xliff"></a>

`dotnet-msbuild` - 建置專案和其所有相依性。

## 概要
<a id="synopsis" class="xliff"></a>

`dotnet msbuild <msbuild_arguments> [-h]`

## 描述
<a id="description" class="xliff"></a>

`dotnet msbuild` 命令可存取完整功能的 MSBuild。

命令與現有的 MSBuild 命令列用戶端具有完全相同的功能。 選項完全一樣。 使用 [MSBuild 命令列參考](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference)來取得可用選項的資訊。 

## 範例
<a id="examples" class="xliff"></a>

建置專案和其相依性：

`dotnet msbuild`

使用發行組態來建置專案和其相依性︰

`dotnet msbuild /p:Configuration=Release`

執行發行目標並針對 `osx.10.11-x64` RID 發行：

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

查看整個專案和 SDK 包含的所有目標：

`dotnet msbuild /pp`
