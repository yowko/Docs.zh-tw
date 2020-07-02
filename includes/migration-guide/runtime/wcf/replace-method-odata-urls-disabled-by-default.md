---
ms.openlocfilehash: b2fcacdb02c411c4dcb12051bf0c6759faccdea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620066"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>OData URL 中的 Replace 方法預設為停用

#### <a name="details"></a>詳細資料

從 .NET Framework 4.5 開始，OData URL 中的 Replace 方法預設為停用。 當 OData Replace 停用 (現在為預設) 時，任何包含取代功能的使用者要求 (不常見) 將會失敗。

#### <a name="suggestion"></a>建議

如果需要 Replace 方法 (不常見)，可以透過組態設定 (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName>) 將它重新啟用。 不過，已啟用的 Replace 方法可能會有資訊安全漏洞，因此只有在仔細檢閱之後才能使用。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
