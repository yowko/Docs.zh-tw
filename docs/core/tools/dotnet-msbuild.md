---
title: dotnet msbuild 命令
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
ms.date: 02/14/2020
ms.openlocfilehash: 88e85868e2d7de564b2e4c90ce6e78bde4cb350e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463617"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**本文適用於:✔️** .NET Core 2.x SDK 和更高版本

## <a name="name"></a>名稱

`dotnet msbuild` - 建置專案和其所有相依性。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a>描述

`dotnet msbuild` 命令可存取完整功能的 MSBuild。

該命令具有與僅針對 SDK 樣式專案的現有 MSBuild 命令行用戶端完全相同的功能。 選項完全一樣。 有關可用選項的詳細資訊,請參閱[MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。

[dotnet build](dotnet-build.md) 命令等同於 `dotnet msbuild -restore -target:Build`。 [dotnet 產生](dotnet-build.md)更通常用於產生項目,但由於它總是執行產生目標,因此可以在不想產生專案時`dotnet msbuild`使用 。 例如,如果您有要在不生成項目的情況下運行的特定目標,請使用`dotnet msbuild`並指定目標。

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
