---
title: 編譯 config 設定
description: 瞭解執行時間設定，其可設定 JIT 編譯程式適用于 .NET Core 應用程式的方式。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: adf1f01dba7387b89ee56784e33653d6a132c0e3
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092885"
---
# <a name="run-time-configuration-options-for-compilation"></a>編譯的執行時間設定選項

## <a name="tiered-compilation"></a>階層式編譯

- 設定即時（JIT）編譯器是否使用[分層式編譯](../whats-new/dotnet-core-3-0.md#tiered-compilation)。 階層式編譯會透過兩個層級轉換方法：
  - 第一層會更快速地產生程式碼（[快速 JIT](#quick-jit)），或載入預先編譯的程式碼（[ReadyToRun](#readytorun)）。
  - 第二層會在背景產生優化的程式碼（「優化 JIT」）。
- 在 .NET Core 3.0 和更新版本中，預設會啟用階層式編譯。
- 在 .NET Core 2.1 和2.2 中，階層式編譯預設為停用。
- 如需詳細資訊，請參閱階層式[編譯指南](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md)。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `System.Runtime.TieredCompilation` | 已啟用 `true`<br/>`false`-已停用 |
| **MSBuild 屬性** | `TieredCompilation` | 已啟用 `true`<br/>`false`-已停用 |
| **環境變數** | `COMPlus_TieredCompilation` | 已啟用 `1`<br/>`0`-已停用 |

### <a name="examples"></a>範例

*.runtimeconfig.json json*檔案：

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

- 設定 JIT 編譯程式是否使用*快速 jit*。 對於不包含迴圈的方法，以及無法使用預先編譯的程式碼，快速 JIT 會更快速地編譯它們，但不會進行優化。
- 啟用快速 JIT 可減少啟動時間，但可能會產生效能特性降低的程式碼。 例如，程式碼可能會使用更多堆疊空間、配置更多記憶體，且執行速度較慢。
- 如果已停用快速 JIT，但已啟用[分層編譯](#tiered-compilation)，則只有預先編譯的程式碼會參與階層式編譯。 如果未使用[ReadyToRun](#readytorun)預先編譯方法，則 JIT 行為會與已停用階層式[編譯](#tiered-compilation)相同。
- 在 .NET Core 3.0 和更新版本中，預設會啟用 [快速 JIT]。
- 在 .NET Core 2.1 和2.2 中，預設會停用 [快速 JIT]。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `System.Runtime.TieredCompilation.QuickJit` | 已啟用 `true`<br/>`false`-已停用 |
| **MSBuild 屬性** | `TieredCompilationQuickJit` | 已啟用 `true`<br/>`false`-已停用 |
| **環境變數** | `COMPlus_TC_QuickJit` | 已啟用 `1`<br/>`0`-已停用 |

### <a name="examples"></a>範例

*.runtimeconfig.json json*檔案：

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

## <a name="quick-jit-for-loops"></a>快速 JIT for 迴圈

- 設定 JIT 編譯程式是否針對包含迴圈的方法使用快速 JIT。
- 啟用快速 JIT for 迴圈可能會改善啟動效能。 不過，長時間執行的迴圈可能會停滯在較不優化的程式碼中。
- 如果已停用[快速 JIT](#quick-jit) ，此設定就不會有任何作用。
- 預設：停用（`false`）。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false`-已停用<br/>已啟用 `true` |
| **MSBuild 屬性** | `TieredCompilationQuickJitForLoops` | `false`-已停用<br/>已啟用 `true` |
| **環境變數** | `COMPlus_TC_QuickJitForLoops` | `0`-已停用<br/>已啟用 `1` |

### <a name="examples"></a>範例

*.runtimeconfig.json json*檔案：

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

## <a name="readytorun"></a>ReadyToRun

- 設定 .NET Core 執行時間是否針對具有可用 ReadyToRun 資料的影像使用預先編譯的程式碼。 停用這個選項會強制執行時間執行 JIT 編譯架構程式碼。
- 如需詳細資訊，請參閱[ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)。
- 預設：啟用（`1`）。

| | 設定名稱 | 值 |
| - | - | - |
| **環境變數** | `COMPlus_ReadyToRun` | 已啟用 `1`<br/>`0`-已停用 |
