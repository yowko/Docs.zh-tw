---
title: dotnet msbuild 命令 - .NET Core CLI
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: c51c058391de4925afd4339fe84e28500d692e1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet msbuild` - 建置專案和其所有相依性。

## <a name="synopsis"></a>概要

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>描述

`dotnet msbuild` 命令可存取完整功能的 MSBuild。

命令與現有的 MSBuild 命令列用戶端具有完全相同的功能。 選項完全一樣。 使用 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)來取得可用選項的資訊。 

## <a name="examples"></a>範例

建置專案和其相依性：

`dotnet msbuild`

使用發行組態來建置專案和其相依性︰

`dotnet msbuild /p:Configuration=Release`

執行發行目標並針對 `osx.10.11-x64` RID 發行：

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

查看整個專案和 SDK 包含的所有目標：

`dotnet msbuild /pp`
