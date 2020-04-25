---
title: dotnet 新增參考命令
description: dotnet add reference 命令提供方便的選項，以新增專案對專案參考。
ms.date: 02/14/2020
ms.openlocfilehash: b261e24ed6a9d5bd489d317d2663b1420b5c34ff
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158316"
---
# <a name="dotnet-add-reference"></a>dotnet add reference

**本文適用于：** ✔️ .net CORE 2.x SDK 和更新版本

## <a name="name"></a>名稱

`dotnet add reference` - 新增專案對專案 (P2P) 參考。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet add [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     [--interactive] <PROJECT_REFERENCES>

dotnet add reference -h|--help
```

## <a name="description"></a>描述

`dotnet add reference` 命令提供方便的選項，將專案參考新增至專案。 執行命令之後，系統就會將 `<ProjectReference>` 元素新增至專案檔。

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>引數

- **`PROJECT`**

  指定專案檔。 如果未指定，命令會在目前的目錄中搜尋一個專案檔。

- **`PROJECT_REFERENCES`**

  要新增的專案對專案 (P2P) 參考。 指定一個或多個專案。 Unix/Linux 系統支援 [Glob 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。

## <a name="options"></a>選項。

- **`-f|--framework <FRAMEWORK>`**

  只有在以使用 TFM 格式的特定[架構](../../standard/frameworks.md)為目標時，才會加入專案參考。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--interactive`**

  允許命令停止並等候使用者輸入或動作（通常用來完成驗證）。 自 .NET Core 3.0 SDK 起提供。

## <a name="examples"></a>範例

- 新增專案參考：

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- 新增目前目錄中專案的多個專案參考：

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- 在 Linux/Unix 上使用 Glob 模式新增多個專案參考：

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
