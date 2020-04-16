---
title: dotnet build-server 命令
description: dotnet build-server 命令會與組建所啟動的伺服器互動。
ms.date: 02/14/2020
ms.openlocfilehash: 882b697c07aac0e20266f3ad4e6c11888a0b7acc
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463729"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**本文適用於:✔️** .NET 核心 2.1 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet build-server` - 與組建所啟動的伺服器互動。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]

dotnet build-server shutdown -h|--help

dotnet build-server -h|--help
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
