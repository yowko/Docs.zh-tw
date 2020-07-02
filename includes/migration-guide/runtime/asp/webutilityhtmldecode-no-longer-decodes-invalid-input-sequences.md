---
ms.openlocfilehash: 0b7d6d9543035ab0a8fdda675ae71572ace12a1f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619934"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>WebUtility.HtmlDecode 不再將無效的輸入序列解碼

#### <a name="details"></a>詳細資料

根據預設，解碼方法不再將無效的輸入序列解碼為無效的 UTF-16 字串， 而是改為傳回原始輸入。

#### <a name="suggestion"></a>建議

解碼器輸出的變更只有在您於字串中儲存二進位資料而不是 UTF-16 資料時才相關。 若要明確控制這個行為，請將 [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) 項目的 <code>aspnet:AllowRelaxedUnicodeDecoding</code> 屬性設為 <code>true</code> 以啟用舊版行為，或是設為 <code>false</code> 以啟用目前的行為。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
