---
title: 分析設定檔設定
description: 瞭解設定 .NET Core 應用程式之偵測和分析的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 5efd0f776da4b7ce6ff7f3bdfda24feec6e00f79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761989"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>用於進行偵錯工具和分析的執行時間設定選項

## <a name="enable-diagnostics"></a>啟用診斷

- 設定是否啟用或停用偵錯工具、分析工具和 EventPipe 診斷。
- 如果您省略此設定，就會啟用診斷。 這相當於將值設定為 `1` 。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | N/A | N/A |
| **環境變數** | `COMPlus_EnableDiagnostics` | `1`-已啟用<br/>`0`-已停用 |

## <a name="enable-profiling"></a>啟用分析

- 設定是否針對目前正在執行的進程啟用分析。
- 如果您省略此設定，就會停用分析。 這相當於將值設定為 `0` 。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | N/A | N/A |
| **環境變數** | `CORECLR_ENABLE_PROFILING` | `0`-已停用<br/>`1`-已啟用 |

## <a name="profiler-guid"></a>Profiler GUID

- 指定要載入目前正在執行之進程中的分析工具 GUID。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | N/A | N/A |
| **環境變數** | `CORECLR_PROFILER` | *字串-guid* |

## <a name="profiler-location"></a>Profiler 位置

- 指定要載入目前正在執行之進程（或32位或64位進程）的 profiler DLL 路徑。
- 如果設定了一個以上的變數，則會優先使用位特定變數。 它們會指定要載入的 profiler 位。
- 如需詳細資訊，請參閱[尋找 profiler 程式庫](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md)。

| | 設定名稱 | 值 |
| - | - | - |
| **環境變數** | `CORECLR_PROFILER_PATH` | *字串-路徑* |
| **環境變數** | `CORECLR_PROFILER_PATH_32` | *字串-路徑* |
| **環境變數** | `CORECLR_PROFILER_PATH_64` | *字串-路徑* |

## <a name="write-perf-map"></a>撰寫 perf map

- 在 Linux 系統上啟用或停用寫入 */tmp/perf-$pid。*
- 如果您省略此設定，則會停用寫入效能對應。 這相當於將值設定為 `0` 。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | N/A | N/A |
| **環境變數** | `COMPlus_PerfMapEnabled` | `0`-已停用<br/>`1`-已啟用 |

## <a name="perf-log-markers"></a>效能記錄檔標記

- 啟用或停用指定的信號，以作為效能記錄檔中的標記接受並予以忽略。
- 如果您省略此設定，則不會忽略指定的信號。 這相當於將值設定為 `0` 。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | N/A | N/A |
| **環境變數** | `COMPlus_PerfMapIgnoreSignal` | `0`-已停用<br/>`1`-已啟用 |

> [!NOTE]
> 如果[COMPlus_PerfMapEnabled](#write-perf-map)省略或設為 `0` （也就是已停用），則會忽略此設定。
