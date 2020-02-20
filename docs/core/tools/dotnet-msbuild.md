---
title: dotnet msbuild 命令
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503674"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**本文適用于：** ✔️ .net CORE 2.x SDK 和更新版本

## <a name="name"></a>名稱

`dotnet msbuild` - 建置專案和其所有相依性。

## <a name="synopsis"></a>概要

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>描述

`dotnet msbuild` 命令可存取完整功能的 MSBuild。

此命令與僅適用于 SDK 樣式專案的現有 MSBuild 命令列用戶端具有完全相同的功能。 選項完全一樣。 如需可用選項的詳細資訊，請參閱[MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。

[dotnet build](dotnet-build.md) 命令等同於 `dotnet msbuild -restore -target:Build`。 [dotnet build](dotnet-build.md)較常用來建立專案，但因為它一律會執行組建目標，所以當您不想要建立專案時，可以使用 `dotnet msbuild`。 例如，如果您有想要執行而不建立專案的特定目標，請使用 `dotnet msbuild` 並指定目標。

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
