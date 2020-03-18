---
title: dotnet build-server 命令
description: dotnet build-server 命令會與組建所啟動的伺服器互動。
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503773"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet build-server` - 與組建所啟動的伺服器互動。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>命令

- **`shutdown`**

  將透過 dotnet 啟動的組建伺服器關機。 根據預設，所有伺服器都會關機。

## <a name="options"></a>選項。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--msbuild`**

  將 MSBuild 組建伺服器關機。

- **`--razor`**

  將 Razor 組建伺服器關機。

- **`--vbcscompiler`**

  將 VB/C# 編譯器組建伺服器關機。
