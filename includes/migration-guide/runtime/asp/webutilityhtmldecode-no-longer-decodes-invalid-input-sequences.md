---
ms.openlocfilehash: ef3114a4eb9f62030c3ec36d3b463d07ccd59f6d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496364"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>WebUtility.HtmlDecode 不再將無效的輸入序列解碼

#### <a name="details"></a>詳細資料

根據預設，解碼方法不再將無效的輸入序列解碼為無效的 UTF-16 字串， 而是改為傳回原始輸入。

#### <a name="suggestion"></a>建議

解碼器輸出的變更只有在您於字串中儲存二進位資料而不是 UTF-16 資料時才相關。 若要明確控制這個行為，請將 [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) 項目的 <code>aspnet:AllowRelaxedUnicodeDecoding</code> 屬性設為 <code>true</code> 以啟用舊版行為，或是設為 <code>false</code> 以啟用目前的行為。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Net.WebUtility.HtmlDecode(System.String)`
- `M:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)`
- `M:System.Net.WebUtility.UrlDecode(System.String)`

-->
