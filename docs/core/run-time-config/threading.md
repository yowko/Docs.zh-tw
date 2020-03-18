---
title: 執行緒配置設置
description: 瞭解為 .NET Core 應用配置執行緒的運行時設置。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789858"
---
# <a name="run-time-configuration-options-for-threading"></a>用於執行緒的運行時配置選項

## <a name="cpu-groups"></a>CPU 組

- 配置執行緒是否自動分佈在 CPU 組中。
- 預設值： 已`0`禁用 （ 。

| | 設定名稱 | 值 |
| - | - | - |
| **運行時配置.json** | N/A | N/A |
| **環境變數** | `COMPlus_Thread_UseAllCpuGroups` | `0`- 禁用<br/>`1`- 已啟用 |

## <a name="minimum-threads"></a>最小線程

- 指定輔助執行緒池的最小線程數。
- 對應于 方法<xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>。

| | 設定名稱 | 值 |
| - | - | - |
| **運行時配置.json** | `System.Threading.ThreadPool.MinThreads` | 表示最小線程數的整數 |
| **MSBuild 屬性** | `ThreadPoolMinThreads` | 表示最小線程數的整數 |
| **環境變數** | N/A | N/A |

### <a name="examples"></a>範例

*運行時配置.json*檔：

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

專案檔：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a>最大執行緒數

- 指定輔助執行緒池的最大執行緒數。
- 對應于 方法<xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>。

| | 設定名稱 | 值 |
| - | - | - |
| **運行時配置.json** | `System.Threading.ThreadPool.MaxThreads` | 表示最大執行緒數的整數 |
| **MSBuild 屬性** | `ThreadPoolMaxThreads` | 表示最大執行緒數的整數 |
| **環境變數** | N/A | N/A |

### <a name="examples"></a>範例

*運行時配置.json*檔：

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

專案檔：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
