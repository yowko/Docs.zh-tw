---
ms.openlocfilehash: 3e4a5936bbac4e77efc5f7e68b55ddf49bae5d43
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614349"
---
### <a name="path-colon-checks-are-stricter"></a>路徑冒號檢查更嚴格

#### <a name="details"></a>詳細資料

在 .NET Framework 4.6.2 中，為了支援先前所不支援的路徑 (就長度和格式兩方面) 而有數項變更。 對於適當磁碟機分隔符號 (冒號) 語法的檢查更為正確，副作用則是會封鎖一些選取路徑 API 中的某些 URI 路徑，而在過去都會容許它們。

#### <a name="suggestion"></a>建議

如果傳遞 URI 給受影響的 API，請先將字串修改為合法的路徑。<ul><li>以手動方式從 URL 移除配置 (例如從 URL 移除 `file://`)

- 將 URI 傳遞給 <xref:System.Uri> 類別，並且使用 <xref:System.Uri.LocalPath>

或者，將 `Switch.System.IO.UseLegacyPathHandling` AppContext 參數設為 true，以選擇退出新的路徑正規化。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.6.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
