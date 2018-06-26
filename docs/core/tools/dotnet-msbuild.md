---
title: dotnet msbuild 命令 - .NET Core CLI
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 58aac2a5314758b8711c0b014154022168fb671c
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696841"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet msbuild` - 建置專案和其所有相依性。

## <a name="synopsis"></a>概要

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>描述

`dotnet msbuild` 命令可存取完整功能的 MSBuild。

命令與現有的 MSBuild 命令列用戶端具有完全相同的功能。 選項完全一樣。 如需可用選項的詳細資訊，請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。

## <a name="examples"></a>範例

建置專案和其相依性：

`dotnet msbuild`

使用發行組態來建置專案和其相依性︰

`dotnet msbuild /p:Configuration=Release`

執行發行目標並針對 `osx.10.11-x64` RID 發行：

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

查看整個專案和 SDK 包含的所有目標：

`dotnet msbuild /pp`
