---
ms.openlocfilehash: 8c739d8f355ffa6a6e09cbe4c531b188acede5bd
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720295"
---
### <a name="osplatform-attributes-renamed-or-removed"></a>OSPlatform 屬性已重新命名或移除

已移除或重新命名 .NET 5.0 Preview 8 中引進的下列屬性： `MinimumOSPlatformAttribute` 、 `RemovedInOSPlatformAttribute` 和 `ObsoletedInOSPlatformAttribute` 。

#### <a name="change-description"></a>變更描述

.NET 5.0 Preview 8 在命名空間中引進了下列屬性 <xref:System.Runtime.Versioning> ：

- `MinimumOSPlatformAttribute`
- `RemovedInOSPlatformAttribute`
- `ObsoletedInOSPlatformAttribute`

在 .NET 5.0 Preview 8 中，當專案的目標為 .NET 5 的 OS 特定類別時，會使用 [目標 framework 標記](../../../../docs/standard/frameworks.md) （例如 `net5.0-windows` ），而組建會加入元件層級的 `System.Runtime.Versioning.MinimumOSPlatformAttribute` 屬性。

在 .NET 5.0 RC1 中，已移除，且已重新命名，如下所示 `ObsoletedInOSPlatformAttribute` `MinimumOSPlatformAttribute` `RemovedInOSPlatformAttribute` ：

| Preview 8 名稱 | RC1 和更新的名稱 |
| - | - |
| `MinimumOSPlatformAttribute` | <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> |
| `RemovedInOSPlatformAttribute` | <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> |

在 .NET 5.0 RC1 和更新版本中，當專案以 .NET 5 的 OS 特定類別為目標時，會使用 [目標 framework 的標記](../../../../docs/standard/frameworks.md) （例如 `net5.0-windows` ），而組建會加入元件層級 <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 屬性。

#### <a name="reason-for-change"></a>變更的原因

.NET 5.0 Preview 8 引進中的屬性 <xref:System.Runtime.Versioning> ，以指定 api 支援的平臺。 當平臺特定 Api 在不支援這些 Api 的平臺上取用時， [平臺相容性分析器](../../../../docs/core/compatibility/code-analysis.md#ca1416-platform-compatibility) 會使用這些屬性來產生組建警告。

針對 .NET 5.0 RC1，平臺相容性分析器已新增其他功能來排除平臺。 這項功能可讓 Api 在作業系統平臺上標示為完全不受支援。 這項功能會提示變更屬性，包括使用更適合的名稱。 `ObsoletedInOSPlatformAttribute`已移除，因為不再需要它。

#### <a name="version-introduced"></a>引進的版本

5.0 RC1

#### <a name="recommended-action"></a>建議的動作

當您將專案從 .NET 5.0 Preview 8 重定目標為 .NET 5.0 RC1 時，可能會因為這些變更而遇到組建或執行階段錯誤。 例如，的重新命名 `MinimumOSPlatformAttribute` 可能會產生錯誤，因為屬性會在組建階段套用至平臺特定的元件，而舊的組建成品仍會參考舊的 API 名稱。

組建時期錯誤範例：

- **錯誤 CS0246：找不到類型或命名空間名稱 ' MinimumOSPlatformAttribute ' (您是否遺漏 using 指示詞或元件參考？ ) **
- **錯誤 CS0246：找不到類型或命名空間名稱 ' RemovedInOSPlatformAttribute ' (您是否遺漏 using 指示詞或元件參考？ ) **
- **錯誤 CS0246：找不到類型或命名空間名稱 ' ObsoletedInOSPlatformAttribute ' (您是否遺漏 using 指示詞或元件參考？ ) **

執行階段錯誤範例：

**未處理的例外狀況。TypeLoadException：無法從元件 ' System. Runtime，Version = 5.0.0.0，Culture = 中性，PublicKeyToken = b03f5f7f11d50a3a ' 載入類型 ' MinimumOSPlatformAttribute '。**

若要解決這些錯誤：

- 將的任何參考更新 `MinimumOSPlatformAttribute` 為 <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 。
- 將的任何參考更新 `RemovedInOSPlatformAttribute` 為 <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> 。
- 移除的任何參考 `ObsoletedInOSPlatformAttribute` 。
- 重建您的專案 (或執行 [清除 + 組建]) ，以刪除舊的組建成品。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- `System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `System.Runtime.Versioning.RemovedInOSPlatformAttribute`

<!--

#### Affected APIs

- `T:System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `T:System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `T:System.Runtime.Versioning.RemovedInOSPlatformAttribute`

-->
