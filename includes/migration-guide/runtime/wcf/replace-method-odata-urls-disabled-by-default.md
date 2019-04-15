---
ms.openlocfilehash: 6dc3669433804a4524c18d5a932f9879343ab508
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235128"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>OData URL 中的 Replace 方法預設為停用

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.5 開始，OData URL 中的 Replace 方法預設為停用。 當 OData Replace 停用 (現在為預設) 時，任何包含取代功能的使用者要求 (不常見) 將會失敗。|
|建議|如果需要 Replace 方法 (不常見)，可以透過組態設定 (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>) 將它重新啟用。 不過，已啟用的 Replace 方法可能會有資訊安全漏洞，因此只有在仔細檢閱之後才能使用。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
