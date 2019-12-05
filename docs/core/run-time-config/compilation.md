---
title: 編譯 config 設定
description: 瞭解執行時間設定，其可設定 JIT 編譯程式適用于 .NET Core 應用程式的方式。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bcc445b6edc48d9432ee614b0b19c9c25621f4a0
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802817"
---
# <a name="run-time-configuration-options-for-compilation"></a>編譯的執行時間設定選項

## <a name="tiered-compilation"></a>階層式編譯

- 設定 JIT 編譯程式是否使用[分層式編譯](../whats-new/dotnet-core-3-0.md#tiered-compilation)。
- 在 .NET Core 3.0 和更新版本中，預設會啟用階層式編譯。
- 在 .NET Core 2.1 和2.2 中，階層式編譯預設為停用。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `System.Runtime.TieredCompilation` | 已啟用 `true`<br/>`false`-已停用 |
| **環境變數** | `COMPlus_TieredCompilation` | 已啟用 `1`<br/>`0`-已停用 |
