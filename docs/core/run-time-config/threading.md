---
title: 執行緒配置設定
description: 瞭解設定 .NET Core 應用程式之執行緒的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 1c7c16993a07ef95223481791153b75ab2f61533
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761924"
---
# <a name="run-time-configuration-options-for-threading"></a>執行緒的執行時間設定選項

## <a name="cpu-groups"></a>CPU 群組

- 設定是否要在 CPU 群組之間自動散發執行緒。
- 如果您省略此設定，則不會在 CPU 群組之間散發執行緒。 這相當於將值設定為 `0` 。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | N/A | N/A |
| **環境變數** | `COMPlus_Thread_UseAllCpuGroups` | `0`-已停用<br/>`1`-已啟用 |

## <a name="minimum-threads"></a>執行緒數下限

- 指定背景工作執行緒集區的執行緒數目下限。
- 對應至 <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> 方法。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `System.Threading.ThreadPool.MinThreads` | 整數，表示執行緒的最小數目 |
| **MSBuild 屬性** | `ThreadPoolMinThreads` | 整數，表示執行緒的最小數目 |
| **環境變數** | N/A | N/A |

### <a name="examples"></a>範例

*.runtimeconfig.json json*檔案：

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

- 指定背景工作執行緒集區的執行緒數目上限。
- 對應至 <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> 方法。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `System.Threading.ThreadPool.MaxThreads` | 表示執行緒數目上限的整數。 |
| **MSBuild 屬性** | `ThreadPoolMaxThreads` | 表示執行緒數目上限的整數。 |
| **環境變數** | N/A | N/A |

### <a name="examples"></a>範例

*.runtimeconfig.json json*檔案：

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
