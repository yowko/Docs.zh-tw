---
title: 編譯設定
description: 瞭解設定 JIT 編譯程式如何使用 .NET Core 應用程式的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: e5f9e1245b749864787fb808527d022665197edf
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654838"
---
# <a name="run-time-configuration-options-for-compilation"></a>編譯的執行時間設定選項

## <a name="tiered-compilation"></a>階層式編譯

- 設定及時 (JIT) 編譯器是否使用 [分層式編譯](../whats-new/dotnet-core-3-0.md#tiered-compilation)。 階層式編譯會透過兩個層級轉換方法：
  - 第一層會更快速地產生程式碼 ([快速 JIT](#quick-jit)) ，或 ([ReadyToRun](#readytorun)) 載入預先編譯的程式碼。
  - 第二層會在背景產生優化程式碼 ( 「優化 JIT」 ) 。
- 在 .NET Core 3.0 和更新版本中，依預設會啟用分層式編譯。
- 在 .NET Core 2.1 和2.2 中，階層式編譯預設為停用。
- 如需詳細資訊，請參閱 [分層式編譯指南](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md)。

| | 設定名稱 | 值 |
| - | - | - |
| **runtimeconfig.js開啟** | `System.Runtime.TieredCompilation` | `true` -已啟用<br/>`false` -已停用 |
| **MSBuild 屬性** | `TieredCompilation` | `true` -已啟用<br/>`false` -已停用 |
| **環境變數** | `COMPlus_TieredCompilation` | `1` -已啟用<br/>`0` -已停用 |

### <a name="examples"></a>範例

*runtimeconfig.json* file：

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

- 設定 JIT 編譯程式是否使用 *快速 jit*。 對於不包含迴圈的方法以及無法使用預先編譯的程式碼，快速 JIT 編譯它們的速度更快，但不含優化。
- 啟用快速 JIT 可縮短啟動時間，但可以產生效能較差的程式碼。 例如，程式碼可能會使用更多堆疊空間、配置更多記憶體，且執行速度較慢。
- 如果已停用快速 JIT，但已啟用階層式 [編譯](#tiered-compilation) ，則只有預先編譯的程式碼會參與分層式編譯。 如果未使用 [ReadyToRun](#readytorun)預先編譯方法，JIT 行為就會如同已停用階層式 [編譯](#tiered-compilation) 一樣。
- 在 .NET Core 3.0 和更新版本中，預設會啟用快速 JIT。
- 在 .NET Core 2.1 和2.2 中，預設會停用快速 JIT。

| | 設定名稱 | 值 |
| - | - | - |
| **runtimeconfig.js開啟** | `System.Runtime.TieredCompilation.QuickJit` | `true` -已啟用<br/>`false` -已停用 |
| **MSBuild 屬性** | `TieredCompilationQuickJit` | `true` -已啟用<br/>`false` -已停用 |
| **環境變數** | `COMPlus_TC_QuickJit` | `1` -已啟用<br/>`0` -已停用 |

### <a name="examples"></a>範例

*runtimeconfig.json* file：

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

- 設定 JIT 編譯程式是否在包含迴圈的方法上使用快速 JIT。
- 啟用快速 JIT for 迴圈可能會改善啟動效能。 不過，長時間執行的迴圈可能會停滯在較不優化的程式碼中長時間。
- 如果停用 [快速 JIT](#quick-jit) ，此設定不會有任何作用。
- 如果您省略這個設定，就不會將快速 JIT 用於包含迴圈的方法。 這相當於將值設定為 `false` 。

| | 設定名稱 | 值 |
| - | - | - |
| **runtimeconfig.js開啟** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false` -已停用<br/>`true` -已啟用 |
| **MSBuild 屬性** | `TieredCompilationQuickJitForLoops` | `false` -已停用<br/>`true` -已啟用 |
| **環境變數** | `COMPlus_TC_QuickJitForLoops` | `0` -已停用<br/>`1` -已啟用 |

### <a name="examples"></a>範例

*runtimeconfig.json* file：

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
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a>ReadyToRun

- 設定 .NET Core 執行時間是否針對具有可用 ReadyToRun 資料的映射使用預先編譯的程式碼。 停用此選項會強制執行時間以 JIT 編譯架構程式碼。
- 如需詳細資訊，請參閱 [準備執行](../deploying/ready-to-run.md)。
- 如果您省略此設定，.NET 會使用 ReadyToRun 資料（如果有的話）。 這相當於將值設定為 `1` 。

| | 設定名稱 | 值 |
| - | - | - |
| **環境變數** | `COMPlus_ReadyToRun` | `1` -已啟用<br/>`0` -已停用 |
