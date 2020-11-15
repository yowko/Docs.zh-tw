---
title: dotnet 工具搜尋命令
description: Dotnet 工具搜尋命令會搜尋發行至 NuGet.org 的 .NET 工具。
ms.date: 11/11/2020
ms.openlocfilehash: e0289e651ec4a439c791c8c948bef2d85d9c3794
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634138"
---
# <a name="dotnet-tool-search"></a>dotnet 工具搜尋

本文 **適用于：** ✔️ .NET 5.0 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet tool search` -搜尋所有已發佈至 NuGet 的 [.net 工具](global-tools.md) 。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet tool search [--detail]  [--prerelease]
    [--skip <NUMBER>] [--take <NUMBER>] <SEARCH TERM>

dotnet tool search -h|--help
```

## <a name="description"></a>描述

此 `dotnet tool search` 命令會提供一種方式，讓您在 NuGet 中搜尋可作為 .net 全域、工具路徑或本機工具使用的工具。 此命令會搜尋工具名稱和中繼資料，例如標題、描述和標記。

此命令會使用 [NuGet 搜尋 API](/nuget/api/search-query-service-resource#search-for-packages)。 它會篩選 `packageType=dotnettool` 以僅選取 .net 工具套件。

## <a name="options"></a>選項

- **`--detail`**

  顯示查詢的詳細結果。

- **`--prerelease`**

  包含發行前版本的套件。

- **`--skip <NUMBER>`**

  指定要略過的查詢結果數目。 用於分頁。

- **`--take <NUMBER>`**

  指定要顯示的查詢結果數目。 用於分頁。

- **`-h|--help`**

  顯示命令列說明。

## <a name="examples"></a>範例

- 在套件名稱或描述中使用 "format" 的 .NET 工具搜尋 NuGet.org：

  ```dotnetcli
  dotnet tool search format
  ```

  輸出看起來會像下列範例：

  ```output
  Package ID                              Latest Version      Authors                                                                     Downloads      Verified
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------
  dotnet-format                           4.1.131201          Microsoft                                                                   496746
  bsoa.generator                          1.0.0               Microsoft                                                                   533
  ```

- 在套件名稱或中繼資料中使用 "format" 的 .NET 工具搜尋 NuGet.org，只顯示第一個結果，並顯示詳細的觀點。

  ```dotnetcli
  dotnet tool search format --take 1 --detail
  ```

  輸出看起來會像下列範例：

  ```output
  ----------------
  dotnet-format
  Latest Version: 4.1.131201
  Authors: Microsoft
  Tags:
  Downloads: 496746
  Verified: False
  Description: Command line tool for formatting C# and Visual Basic code files based on .editorconfig settings.
  Versions:
          3.0.2 Downloads: 1973
          3.0.4 Downloads: 9064
          3.1.37601 Downloads: 114730
          3.2.107702 Downloads: 13423
          3.3.111304 Downloads: 131195
          4.0.130203 Downloads: 78610
          4.1.131201 Downloads: 145927
  ```

## <a name="see-also"></a>另請參閱

- [.NET 工具](global-tools.md)
- [教學課程：使用 .NET CLI 安裝和使用 .NET 通用工具](global-tools-how-to-use.md)
- [教學課程：使用 .NET CLI 安裝和使用 .NET 本機工具](local-tools-how-to-use.md)
