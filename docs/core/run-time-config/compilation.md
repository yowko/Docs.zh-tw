---
title: 編譯設定設定
description: 瞭解配置 JIT 編譯器如何為 .NET Core 應用工作的運行時設置。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: ac51aa13254b2f2b1fdd8d1dd9c52559831a1659
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989112"
---
# <a name="run-time-configuration-options-for-compilation"></a>以編譯的執行時設定選項

## <a name="tiered-compilation"></a>階層式編譯

- 設定即時 (JIT) 編譯器是否使用[分層編譯](../whats-new/dotnet-core-3-0.md#tiered-compilation)。 階層編譯透過兩層轉換方法:
  - 第一層產生代碼更快 ([快速 JIT)](#quick-jit)或載入預編譯代碼 ([ReadyToRun](#readytorun))。
  - 第二層在後台生成優化的代碼("優化 JIT")。
- 在 .NET Core 3.0 及更高版本中,默認情況下啟用分層編譯。
- 在 .NET Core 2.1 和 2.2 中,默認情況下禁用分層編譯。
- 有關詳細資訊,請參閱[分層編譯指南](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md)。

| | 設定名稱 | 值 |
| - | - | - |
| **執行時設定.json** | `System.Runtime.TieredCompilation` | `true`- 已開啟<br/>`false`- 停用 |
| **MSBuild 屬性** | `TieredCompilation` | `true`- 已開啟<br/>`false`- 停用 |
| **環境變數** | `COMPlus_TieredCompilation` | `1`- 已開啟<br/>`0`- 停用 |

### <a name="examples"></a>範例

*執行時設定.json*檔:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

專案檔：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a>快速 JIT

- 設定 JIT 編譯器是否使用*快速 JIT*。 對於不包含迴圈且預編譯代碼不可用的方法,快速 JIT 可以更快地編譯它們,但無需優化。
- 啟用快速 JIT 可縮短啟動時間,但可以生成性能降低的代碼。 例如,程式碼可能使用更多的堆疊空間、分配更多記憶體和運行速度較慢。
- 如果禁用快速 JIT,但啟用[分層編譯](#tiered-compilation),則只有預編譯代碼參與分層編譯。 如果未使用[ReadyToRun](#readytorun)預編譯方法,則 JIT 行為與禁用[分層編譯](#tiered-compilation)相同。
- 在 .NET 核心 3.0 及更高版本中,默認情況下啟用快速 JIT。
- 在 .NET 核心 2.1 和 2.2 中,默認情況下禁用快速 JIT。

| | 設定名稱 | 值 |
| - | - | - |
| **執行時設定.json** | `System.Runtime.TieredCompilation.QuickJit` | `true`- 已開啟<br/>`false`- 停用 |
| **MSBuild 屬性** | `TieredCompilationQuickJit` | `true`- 已開啟<br/>`false`- 停用 |
| **環境變數** | `COMPlus_TC_QuickJit` | `1`- 已開啟<br/>`0`- 停用 |

### <a name="examples"></a>範例

*執行時設定.json*檔:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

專案檔：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a>將快速 JIT

- 配置 JIT 編譯器是否對包含迴圈的方法使用快速 JIT。
- 為迴圈啟用快速 JIT 可以提高啟動性能。 但是,長時間運行的循環可能會長時間卡在不太優化的代碼中。
- 如果禁用[快速 JIT,](#quick-jit)則此設定不起作用。
- 預設值:`false`已關閉 ( 。

| | 設定名稱 | 值 |
| - | - | - |
| **執行時設定.json** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false`- 停用<br/>`true`- 已開啟 |
| **MSBuild 屬性** | `TieredCompilationQuickJitForLoops` | `false`- 停用<br/>`true`- 已開啟 |
| **環境變數** | `COMPlus_TC_QuickJitForLoops` | `0`- 停用<br/>`1`- 已開啟 |

### <a name="examples"></a>範例

*執行時設定.json*檔:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

專案檔：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a>準備執行

- 配置 .NET Core 執行時是否對具有可用 ReadyToRun 資料的圖像使用預編譯代碼。 關閉這個選項將強制執行時為 JIT 編譯框架代碼。
- 有關詳細資訊,請參閱["準備運行](../whats-new/dotnet-core-3-0.md#readytorun-images)"。
- 預設值:`1`已開啟 ( 。

| | 設定名稱 | 值 |
| - | - | - |
| **環境變數** | `COMPlus_ReadyToRun` | `1`- 已開啟<br/>`0`- 停用 |
