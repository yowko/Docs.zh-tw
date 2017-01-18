---
title: "dotnet-msbuild 命令 | .NET Core SDK"
description: "dotnet-msmsbuild 命令提供對 MSmsbuild 命令列的存取"
keywords: "dotnet-msmsbuild, CLI, CLI 命令, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: ffdc40ba-ef33-463e-aa35-b0af1fe615a2
translationtype: Human Translation
ms.sourcegitcommit: cde9d9577246a9025d646ce2a6d574a18512146e
ms.openlocfilehash: 51a3afdcf591b8147790d78471c6fee63ceb7f2d

---

#<a name="dotnet-msbuild"></a>dotnet-msbuild

## <a name="name"></a>名稱 
dotnet-msbuild -- 建置專案和其所有相依性 

## <a name="synopsis"></a>概要

`dotnet msbuild <msbuild_arguments>`

## <a name="description"></a>說明
`dotnet msbuild` 命令可存取完整功能的 MSBuild 

命令與現有的 MSBuild 命令列用戶端具有完全相同的功能。 選項完全一樣。 您可以使用[現有文件](https://msdn.microsoft.com/en-us/library/ms164311.aspx)來熟悉命令參考。 

## <a name="examples"></a>範例

建置專案和其相依性：

`dotnet msbuild`

使用發行組態來建置專案和其相依性︰

`dotnet msbuild /p:Configuration=Release`

執行發行目標並針對 `osx.10.11-x64` RID 發行：

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`



<!--HONumber=Nov16_HO3-->


