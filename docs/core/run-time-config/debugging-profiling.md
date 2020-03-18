---
title: 調試分析配置設置
description: 瞭解配置 .NET Core 應用的調試和分析的運行時設置。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802796"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>用於調試和分析的運行時配置選項

## <a name="enable-diagnostics"></a>啟用診斷

- 配置調試器、探測器和事件管道診斷是啟用還是禁用。
- 預設值： 已`1`啟用 （ 。

| | 設定名稱 | 值 |
| - | - | - |
| **運行時配置.json** | N/A | N/A |
| **環境變數** | `COMPlus_EnableDiagnostics` | `1`- 已啟用<br/>`0`- 禁用 |

## <a name="enable-profiling"></a>啟用分析

- 配置是否為當前正在運行的進程啟用了分析。
- 預設值： 已`0`禁用 （ 。

| | 設定名稱 | 值 |
| - | - | - |
| **運行時配置.json** | N/A | N/A |
| **環境變數** | `CORECLR_ENABLE_PROFILING` | `0`- 禁用<br/>`1`- 已啟用 |

## <a name="profiler-guid"></a>探測器 GUID

- 指定要載入到當前正在運行的進程中的探測器的 GUID。

| | 設定名稱 | 值 |
| - | - | - |
| **運行時配置.json** | N/A | N/A |
| **環境變數** | `CORECLR_PROFILER` | *字串吉德* |

## <a name="profiler-location"></a>探測器位置

- 指定探測器 DLL 的路徑以載入到當前正在運行的進程（或 32 位或 64 位進程）。
- 如果設置了多個變數，則位級特定變數優先。 它們指定要載入的探測器的位數。
- 有關詳細資訊，請參閱[查找探測器庫](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md)。

| | 設定名稱 | 值 |
| - | - | - |
| **環境變數** | `CORECLR_PROFILER_PATH` | *字串路徑* |
| **環境變數** | `CORECLR_PROFILER_PATH_32` | *字串路徑* |
| **環境變數** | `CORECLR_PROFILER_PATH_64` | *字串路徑* |

## <a name="write-perf-map"></a>寫入 perf 地圖

- 啟用或禁用在 Linux 系統上寫入 */tmp/perf-$pid.map。*
- 預設值： 已`0`禁用 （ 。

| | 設定名稱 | 值 |
| - | - | - |
| **運行時配置.json** | N/A | N/A |
| **環境變數** | `COMPlus_PerfMapEnabled` | `0`- 禁用<br/>`1`- 已啟用 |

## <a name="perf-log-markers"></a>Perf 日誌標記

- 設置為`COMPlus_PerfMapEnabled`時`1`，啟用或禁用指定信號，以在 perf 日誌中作為標記接受和忽略。
- 預設值： 已`0`禁用 （ 。

| | 設定名稱 | 值 |
| - | - | - |
| **運行時配置.json** | N/A | N/A |
| **環境變數** | `COMPlus_PerfMapIgnoreSignal` | `0`- 禁用<br/>`1`- 已啟用 |
