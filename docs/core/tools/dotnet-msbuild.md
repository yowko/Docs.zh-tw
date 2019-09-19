---
title: dotnet msbuild 命令
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
ms.date: 12/03/2018
ms.openlocfilehash: b83f1272cdd4c5fcdb6b1e34aef7692e9acc01cd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117702"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet msbuild` - 建置專案和其所有相依性。

## <a name="synopsis"></a>概要

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>描述

`dotnet msbuild` 命令可存取完整功能的 MSBuild。

此命令與現有的 MSBuild 命令列用戶端僅針對 SDK 樣式專案具有完全相同的功能。 選項完全一樣。 如需可用選項的詳細資訊，請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。

[dotnet build](dotnet-build.md) 命令等同於 `dotnet msbuild -restore -target:Build`。 `dotnet build` 較常用來建置專案，但 `dotnet msbuild` 可提供您較多的控制權。 例如，如果您有想要執行的特定目標 (但不執行建置目標)，您可能會想要使用 `dotnet msbuild`。

## <a name="examples"></a>範例

* 建置專案和其相依性：

  ```dotnetcli
  dotnet msbuild
  ```

* 使用發行組態來建置專案和其相依性︰

  ```dotnetcli
  dotnet msbuild -p:Configuration=Release
  ```

* 執行發行目標並針對 `osx.10.11-x64` RID 發行：

  ```dotnetcli
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* 查看整個專案和 SDK 包含的所有目標：

  ```dotnetcli
  dotnet msbuild -pp
  ```
