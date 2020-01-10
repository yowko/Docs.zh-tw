---
title: 垃圾收集行程 config 設定
description: 瞭解用來設定垃圾收集行程如何管理 .NET Core 應用程式記憶體的執行時間設定。
ms.date: 11/13/2019
ms.topic: reference
ms.openlocfilehash: 41157db7770a89f4402fa6675f7031c508f33aca
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740554"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>用於垃圾收集的執行時間設定選項

此頁面包含可在執行時間變更之垃圾收集行程（GC）設定的相關資訊。 如果您正嘗試達到執行中應用程式的尖峰效能，請考慮使用這些設定。 不過，在一般情況下，預設值可為大部分的應用程式提供最佳效能。

這些設定會依此頁面的群組排列。 每個群組內的設定通常會彼此搭配使用，以達成特定結果。

> [!NOTE]
>
> - 這些設定也可以在應用程式執行時動態變更，因此您設定的任何執行時間設定可能會遭到覆寫。
> - 某些設定（例如[延遲層級](../../standard/garbage-collection/latency.md)）通常只會在設計階段透過 API 進行設定。 此頁面會省略這類設定。
> - 針對 [數值]，使用十進位標記法做為 *.runtimeconfig.json*檔案中的設定，並針對環境變數設定使用十六進位標記法。

## <a name="flavors-of-garbage-collection"></a>垃圾收集的種類

垃圾收集的兩個主要類別是工作站 GC 和伺服器 GC。 如需兩者之間差異的詳細資訊，請參閱[垃圾收集的基本](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)概念。

垃圾收集的 subflavors 是背景和非並行的。

使用下列設定來選取垃圾收集的種類：

### <a name="systemgcservercomplus_gcserver"></a>System.web/COMPlus_gcServer

- 設定應用程式是否使用工作站垃圾收集或伺服器垃圾收集。
- 預設值：工作站垃圾收集（`false`）。

| | 設定名稱 | 值 | 引進的版本 |
| - | - | - | - |
| **.runtimeconfig.json json** | `System.GC.Server` | `false`-工作站<br/>`true`-伺服器 | .NET Core 1.0 |
| **環境變數** | `COMPlus_gcServer` | `0`-工作站<br/>`1`-伺服器 | .NET Core 1.0 |
| **.NET Framework 的 app.config** | [GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false`-工作站<br/>`true`-伺服器 |  |

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System.web/COMPlus_gcConcurrent

- 設定是否啟用背景（並行）垃圾收集。
- 預設：啟用（`true`）。
- 如需詳細資訊，請參閱[背景垃圾收集](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)和[背景伺服器垃圾收集](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection)。

| | 設定名稱 | 值 | 引進的版本 |
| - | - | - | - |
| **.runtimeconfig.json json** | `System.GC.Concurrent` | `true`-背景 GC<br/>`false`-非並行 GC | .NET Core 1.0 |
| **環境變數** | `COMPlus_gcConcurrent` | `true`-背景 GC<br/>`false`-非並行 GC | .NET Core 1.0 |
| **.NET Framework 的 app.config** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true`-背景 GC<br/>`false`-非並行 GC |  |

## <a name="manage-resource-usage"></a>管理資源使用量

使用本節所述的設定來管理垃圾收集行程的記憶體和處理器使用量。

如需有關這些設定的詳細資訊，請參閱[工作站與伺服器 GC 之間的中間](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/)專案 blog。

### <a name="systemgcheapcountcomplus_gcheapcount"></a>HeapCount/COMPlus_GCHeapCount

- 限制垃圾收集行程所建立的堆積數目。
- 僅適用于伺服器垃圾收集（GC）。
- 如果已啟用 GC 處理器親和性（這是預設值），則堆積計數設定會如何 `n` GC 堆積/執行緒到第一個 `n` 處理器。 （使用將相似化為 mask 或將相似化為範圍設定，以確切指定要將相似化為的處理器）。
- 如果停用 GC 處理器親和性，這項設定會限制 GC 堆積的數目。
- 如需詳細資訊，請參閱[GCHeapCount 備註](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)。

| | 設定名稱 | 值 | 引進的版本 |
| - | - | - | - |
| **.runtimeconfig.json json** | `System.GC.HeapCount` | *十進位值* | .NET Core 3.0 |
| **環境變數** | `COMPlus_GCHeapCount` | *十六進位值* | .NET Core 3.0 |
| **.NET Framework 的 app.config** | [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *十進位值* | 4.6.2 |

> [!TIP]
> 如果您要在 *.runtimeconfig.json*中設定選項，請指定十進位值。 如果您要將選項設定為環境變數，請指定十六進位值。 例如，若要將堆積數目限制為16，JSON 檔案的值會是16，而環境變數的值會是10。

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask

- 指定垃圾收集行程執行緒應該使用的確切處理器。
- 如果藉由將 `System.GC.NoAffinitize` 設定為 `true`來停用處理器親和性，則會忽略此設定。
- 僅適用于伺服器垃圾收集（GC）。
- 值是一個位元遮罩，用來定義進程可用的處理器。 例如，十進位值1023（如果您使用環境變數，則為3FF 的十六進位值）是 0011 1111 1111 （二進位標記法）。 這會指定要使用前10個處理器。 若要指定接下來的10個處理器（也就是處理器10-19），請指定十進位值1047552（或 FFC00 的十六進位值），這相當於二進位值 1111 1111 1100 0000 0000。

| | 設定名稱 | 值 | 引進的版本 |
| - | - | - | - |
| **.runtimeconfig.json json** | `System.GC.HeapAffinitizeMask` | *十進位值* | .NET Core 3.0 |
| **環境變數** | `COMPlus_GCHeapAffinitizeMask` | *十六進位值* | .NET Core 3.0 |
| **.NET Framework 的 app.config** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *十進位值* | 4.6.2 |

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a>GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges

- 指定要用於垃圾收集行程執行緒的處理器清單。
- 此設定類似于 `System.GC.HeapAffinitizeMask`，但它可讓您指定64個以上的處理器。
- 若是 Windows 作業系統，請在處理器編號或範圍前面加上對應的[CPU 群組](/windows/win32/procthread/processor-groups)，例如 "0： 1-10，0：12，1： 50-52，1： 70"。
- 如果藉由將 `System.GC.NoAffinitize` 設定為 `true`來停用處理器親和性，則會忽略此設定。
- 僅適用于伺服器垃圾收集（GC）。
- 如需詳細資訊，請參閱 Maoni Stephens 的 blog 上的[針對具有 > 64 cpu 的電腦，讓 CPU 設定更好用於 GC](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) 。

| | 設定名稱 | 值 | 引進的版本 |
| - | - | - | - |
| **.runtimeconfig.json json** | `System.GC.GCHeapAffinitizeRanges` | 以逗號分隔的處理器編號或處理器編號範圍清單。<br/>Unix 範例： "1-10，12，50-52，70"<br/>Windows 範例： "0： 1-10，0：12，1： 50-52，1： 70" | .NET Core 3.0 |
| **環境變數** | `COMPlus_GCHeapAffinitizeRanges` | 以逗號分隔的處理器編號或處理器編號範圍清單。<br/>Unix 範例： "1-10，12，50-52，70"<br/>Windows 範例： "0： 1-10，0：12，1： 50-52，1： 70" | .NET Core 3.0 |

### <a name="complus_gccpugroup"></a>COMPlus_GCCpuGroup

- 設定垃圾收集行程是否使用[CPU 群組](/windows/win32/procthread/processor-groups)。

  當64位 Windows 電腦具有多個 CPU 群組（也就是，有超過64個處理器）時，啟用這個元素會延伸所有 CPU 群組的垃圾收集。 垃圾收集行程會使用所有核心來建立和平衡堆積。

- 僅適用于64位 Windows 作業系統上的伺服器垃圾收集（GC）。
- 預設：停用（`0`）。
- 如需詳細資訊，請參閱 Maoni Stephens 的 blog 上的[針對具有 > 64 cpu 的電腦，讓 CPU 設定更好用於 GC](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) 。

| | 設定名稱 | 值 | 引進的版本 |
| - | - | - | - |
| **.runtimeconfig.json json** | N/A | N/A | N/A |
| **環境變數** | `COMPlus_GCCpuGroup` | `0`-已停用<br/>已啟用 `1` | .NET Core 1.0 |
| **.NET Framework 的 app.config** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false`-已停用<br/>已啟用 `true` |  |

> [!NOTE]
> 若要將 common language runtime （CLR）設定為同時將執行緒集區中的執行緒散發到所有 CPU 群組，請啟用 [ [Thread_UseAllCpuGroups 元素](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)] 選項。 針對 .NET Core 應用程式，您可以將 `COMPlus_Thread_UseAllCpuGroups` 環境變數的值設定為 `1`來啟用此選項。

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>NoAffinitize/COMPlus_GCNoAffinitize

- 指定是否要使用處理器*將相似化為*垃圾收集執行緒。 若要將相似化為 GC 執行緒，這表示它只能在其特定的 CPU 上執行。 會針對每個 GC 執行緒建立堆積。
- 僅適用于伺服器垃圾收集（GC）。
- 預設值：使用處理器（`false`）將相似化為垃圾收集執行緒。

| | 設定名稱 | 值 | 引進的版本 |
| - | - | - | - |
| **.runtimeconfig.json json** | `System.GC.NoAffinitize` | `false`-將相似化為<br/>`true`-不將相似化為 | .NET Core 3.0 |
| **環境變數** | `COMPlus_GCNoAffinitize` | `0`-將相似化為<br/>`1`-不將相似化為 | .NET Core 3.0 |
| **.NET Framework 的 app.config** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false`-將相似化為<br/>`true`-不將相似化為 | 4.6.2 |

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a>HeapHardLimit/COMPlus_GCHeapHardLimit

- 指定 GC 堆積和 GC 簿記的認可大小上限（以位元組為單位）。

| | 設定名稱 | 值 | 引進的版本 |
| - | - | - | - |
| **.runtimeconfig.json json** | `System.GC.HeapHardLimit` | *十進位值* | .NET Core 3.0 |
| **環境變數** | `COMPlus_GCHeapHardLimit` | *十六進位值* | .NET Core 3.0 |

> [!TIP]
> 如果您要在 *.runtimeconfig.json*中設定選項，請指定十進位值。 如果您要將選項設定為環境變數，請指定十六進位值。 例如，若要指定80000個位元組的堆積固定限制，JSON 檔案的值會是80000，而針對環境變數則是13880。

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- 將 GC 堆積使用量指定為總記憶體的百分比。

| | 設定名稱 | 值 | 引進的版本 |
| - | - | - | - |
| **.runtimeconfig.json json** | `System.GC.HeapHardLimitPercent` | *十進位值* | .NET Core 3.0 |
| **環境變數** | `COMPlus_GCHeapHardLimitPercent` | *十六進位值* | .NET Core 3.0 |

> [!TIP]
> 如果您要在 *.runtimeconfig.json*中設定選項，請指定十進位值。 如果您要將選項設定為環境變數，請指定十六進位值。 例如，若要將堆積使用量限制為30%，JSON 檔案的值會是30，而針對環境變數則是1E。

### <a name="systemgcretainvmcomplus_gcretainvm"></a>RetainVM/COMPlus_GCRetainVM

- 設定是否要將應該刪除的區段放在待命清單上以供日後使用，或發行回作業系統（OS）。
- 預設值：將區段釋放回作業系統（`false`）。

| | 設定名稱 | 值 | 引進的版本 |
| - | - | - | - |
| **.runtimeconfig.json json** | `System.GC.RetainVM` | `false`-發行至 OS<br/>`true`-put 待命| .NET Core 1.0 |
| **環境變數** | `COMPlus_GCRetainVM` | `0`-發行至 OS<br/>`1`-put 待命 | .NET Core 1.0 |

## <a name="large-pages"></a>大型頁面

### <a name="complus_gclargepages"></a>COMPlus_GCLargePages

- 指定在設定堆積固定限制時是否應該使用大型分頁。
- 預設：停用（`0`）。
- 這是實驗性設定。

| | 設定名稱 | 值 | 引進的版本 |
| - | - | - | - |
| **.runtimeconfig.json json** | N/A | N/A | N/A |
| **環境變數** | `COMPlus_GCLargePages` | `0`-已停用<br/>已啟用 `1` | .NET Core 3.0 |

## <a name="large-objects"></a>大型物件

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- 針對大小總計大於 2 gb 的陣列，設定64位平臺上的垃圾收集行程支援。
- 預設：啟用（`1`）。
- 在未來的 .NET 版本中，此選項可能會過時。

| | 設定名稱 | 值 | 引進的版本 |
| - | - | - | - |
| **.runtimeconfig.json json** | N/A | N/A | N/A |
| **環境變數** | `COMPlus_gcAllowVeryLargeObjects` | 已啟用 `1`<br/> `0`-已停用 | .NET Core 1.0 |
| **.NET Framework 的 app.config** | [Gcallowverylargeobjects>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | 已啟用 `1`<br/> `0`-已停用 | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>大型物件堆積閾值

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a>LOHThreshold/COMPlus_GCLOHThreshold

- 指定導致物件在大型物件堆積（LOH）上執行的閾值大小（以位元組為單位）。
- 預設閾值為85000個位元組。
- 您指定的值必須大於預設閾值。

| | 設定名稱 | 值 | 引進的版本 |
| - | - | - | - |
| **.runtimeconfig.json json** | `System.GC.LOHThreshold` | *十進位值* | .NET Core 1.0 |
| **環境變數** | `COMPlus_GCLOHThreshold` | *十六進位值* | .NET Core 1.0 |
| **.NET Framework 的 app.config** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | *十進位值* | .NET Framework 4.8 |

> [!TIP]
> 如果您要在 *.runtimeconfig.json*中設定選項，請指定十進位值。 如果您要將選項設定為環境變數，請指定十六進位值。 例如，若要設定120000個位元組的閾值大小，JSON 檔案的值會是120000，而針對環境變數則是1D4C0。

## <a name="standalone-gc"></a>獨立 GC

### <a name="complus_gcname"></a>COMPlus_GCName

- 指定包含執行時間打算載入之垃圾收集行程的程式庫路徑。
- 如需詳細資訊，請參閱[獨立 GC 載入器設計](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md)。

| | 設定名稱 | 值 | 引進的版本 |
| - | - | - | - |
| **.runtimeconfig.json json** | N/A | N/A | N/A |
| **環境變數** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
