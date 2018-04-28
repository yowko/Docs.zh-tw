---
title: dotnet-add reference 命令 - .NET Core CLI
description: dotnet add reference 命令提供方便的選項，以新增專案對專案參考。
author: mairaw
ms.author: mairaw
ms.date: 09/19/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: c82696eee2fbe4bbad86e59cf5de1c2e74d048f6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-add-reference"></a>dotnet-add reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet add reference` - 新增專案對專案 (P2P) 參考。

## <a name="synopsis"></a>概要

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>描述

`dotnet add reference` 命令提供方便的選項，將專案參考新增至專案。 執行命令之後，系統就會將 [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) 元素新增至專案檔。

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>引數

`PROJECT`

指定專案檔。 如果未指定，命令會在目前的目錄中搜尋一個專案檔。

`PROJECT_REFERENCES`

要新增的專案對專案 (P2P) 參考。 指定一個或多個專案。 Unix/Linux 系統支援 [Glob 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

`-f|--framework <FRAMEWORK>`

只有在以特定[架構](../../standard/frameworks.md)為目標時，才能新增專案參考。

## <a name="examples"></a>範例

新增專案參考：

`dotnet add app/app.csproj reference lib/lib.csproj`

新增目前目錄中專案的多個專案參考：

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

在 Linux/Unix 上使用 Glob 模式新增多個專案參考：

`dotnet add app/app.csproj reference **/*.csproj`
