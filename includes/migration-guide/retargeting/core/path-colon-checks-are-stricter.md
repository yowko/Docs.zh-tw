---
ms.openlocfilehash: 6af63c0a58a3273aa98fa70f22e3637b481806b4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497877"
---
### <a name="path-colon-checks-are-stricter"></a>路徑冒號檢查更嚴格

#### <a name="details"></a>詳細資料

在 .NET Framework 4.6.2 中，為了支援先前所不支援的路徑 (就長度和格式兩方面) 而有數項變更。 檢查是否有適當的磁片磁碟機分隔符號 (冒號) 語法是否更正確，它的副作用是在一些先前容許的特定路徑 Api 中封鎖某些 URI 路徑。

#### <a name="suggestion"></a>建議

如果傳遞 URI 給受影響的 API，請先將字串修改為合法的路徑。

- 以手動方式從 Url 移除配置 (例如， `file://` 從 url 移除) 。

- 將 URI 傳遞給 <xref:System.Uri> 類別，並使用 <xref:System.Uri.LocalPath> 。

或者，您可以藉由將 AppCoNtext 參數設定為，退出宣告新的路徑正規化 `Switch.System.IO.UseLegacyPathHandling` `true` 。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   | Edge        |
| 版本 | 4.6.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
