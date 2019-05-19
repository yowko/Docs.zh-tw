---
title: dotnet msbuild 命令
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
ms.date: 12/03/2018
ms.openlocfilehash: 983fae6f4ecf875da0b155a668009984b5df50de
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632034"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet msbuild` - 建置專案和其所有相依性。

## <a name="synopsis"></a>概要

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>說明

`dotnet msbuild` 命令可存取完整功能的 MSBuild。

此命令與現有的 MSBuild 命令列用戶端僅針對 SDK 樣式專案具有完全相同的功能。 選項完全一樣。 如需可用選項的詳細資訊，請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。

[dotnet build](dotnet-build.md) 命令等同於 `dotnet msbuild -restore -target:Build`。 `dotnet build` 較常用來建置專案，但 `dotnet msbuild` 可提供您較多的控制權。 例如，如果您有想要執行的特定目標 (但不執行建置目標)，您可能會想要使用 `dotnet msbuild`。

## <a name="examples"></a>範例

* 建置專案和其相依性：

  ```console
  dotnet msbuild
  ```

* 使用發行組態來建置專案和其相依性︰

  ```console
  dotnet msbuild -p:Configuration=Release
  ```

* 執行發行目標並針對 `osx.10.11-x64` RID 發行：

  ```console
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* 查看整個專案和 SDK 包含的所有目標：

  ```console
  dotnet msbuild -pp
  ```
