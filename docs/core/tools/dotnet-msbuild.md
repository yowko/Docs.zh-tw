---
title: dotnet msbuild 命令
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503674"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**本文適用于：✔️** .NET Core 2.x SDK 和更高版本

## <a name="name"></a>名稱

`dotnet msbuild` - 建置專案和其所有相依性。

## <a name="synopsis"></a>概要

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>描述

`dotnet msbuild` 命令可存取完整功能的 MSBuild。

該命令具有與僅針對 SDK 樣式專案的現有 MSBuild 命令列用戶端完全相同的功能。 選項完全一樣。 有關可用選項的詳細資訊，請參閱[MSBuild 命令列引用](/visualstudio/msbuild/msbuild-command-line-reference)。

[dotnet build](dotnet-build.md) 命令等同於 `dotnet msbuild -restore -target:Build`。 [dotnet 生成](dotnet-build.md)更通常用於生成專案，但由於它總是運行生成目標，因此可以在不想生成專案時使用`dotnet msbuild`。 例如，如果您有要在不生成專案的情況下運行的特定目標，請使用`dotnet msbuild`並指定目標。

## <a name="examples"></a>範例

- 建置專案和其相依性：

  ```dotnetcli
  dotnet msbuild
  ```

- 使用發行組態來建置專案和其相依性︰

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- 執行發行目標並針對 `osx.10.11-x64` RID 發行：

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- 查看整個專案和 SDK 包含的所有目標：

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
