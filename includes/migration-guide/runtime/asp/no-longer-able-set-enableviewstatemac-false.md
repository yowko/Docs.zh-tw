---
ms.openlocfilehash: cecb7b2abd4f57fdaacb0ea373cc19dc3cd9b24a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619935"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>無法再將 EnableViewStateMac 設定為 false

#### <a name="details"></a>詳細資料

ASP.NET 不再允許開發人員指定 <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> 或 <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>。 檢視狀態訊息驗證碼 (MAC) 現在會強制所有要求內嵌檢視狀態。 只會影響將 EnableViewStateMac 屬性明確設定為 <code>false</code> 的應用程式。

#### <a name="suggestion"></a>建議

EnableViewStateMac 必須假設為 true，而且必須解決任何產生的 MAC 錯誤（如[本指南](https://support.microsoft.com/kb/2915218)中所述，其中包含多個解決方法，視造成 MAC 錯誤的細節而定）。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |主要|
|版本|4.5.2|
|類型|執行階段|
