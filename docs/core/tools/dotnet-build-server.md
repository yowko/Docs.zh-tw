---
title: dotnet build-server 命令 - .NET Core CLI
description: dotnet build-server 命令會與組建所啟動的伺服器互動。
ms.date: 12/04/2018
ms.openlocfilehash: 2746ade12cc819089258483e84a8c0f02a64c755
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125674"
---
# <a name="dotnet-build-server"></a>dotnet build-server

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>名稱

`dotnet build-server` - 與組建所啟動的伺服器互動。

## <a name="synopsis"></a>概要

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>命令

* **`shutdown`**

  將透過 dotnet 啟動的組建伺服器關機。 根據預設，所有伺服器都會關機。

## <a name="options"></a>選項

* **`-h|--help`**

  印出命令的簡短說明。

* **`--msbuild`**

  將 MSBuild 組建伺服器關機。

* **`--razor`**

  將 Razor 組建伺服器關機。

* **`--vbcscompiler`**

  將 VB/C# 編譯器組建伺服器關機。