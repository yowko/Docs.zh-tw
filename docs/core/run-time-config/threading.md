---
title: 執行緒配置設定
description: 瞭解設定 .NET Core 應用程式之執行緒的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6a920dbc301830e3f4c95bf637ff3de6d4f464ff
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802761"
---
# <a name="run-time-configuration-options-for-threading"></a>執行緒的執行時間設定選項

## <a name="cpu-groups"></a>CPU 群組

- 設定是否要在 CPU 群組之間自動散發執行緒。
- 預設：停用（`0`）。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | N/A | N/A |
| **環境變數** | `COMPlus_Thread_UseAllCpuGroups` | `0`-已停用<br/>已啟用 `1` |

## <a name="minimum-threads"></a>執行緒數下限

- 指定背景工作執行緒集區的執行緒數目下限。
- 對應至 <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> 方法。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `System.Threading.ThreadPool.MinThreads` | 整數，表示執行緒的最小數目 |
| **環境變數** | N/A | N/A |

## <a name="maximum-threads"></a>最大執行緒數

- 指定背景工作執行緒集區的執行緒數目上限。
- 對應至 <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> 方法。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `System.Threading.ThreadPool.MaxThreads` | 表示執行緒數目上限的整數。 |
| **環境變數** | N/A | N/A |
