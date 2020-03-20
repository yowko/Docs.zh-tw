---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803253"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>無法再將 EnableViewStateMac 設定為 false

|   |   |
|---|---|
|詳細資料|ASP.NET 不再允許開發人員指定 <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> 或 <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>。 檢視狀態訊息驗證碼 (MAC) 現在會強制所有要求內嵌檢視狀態。 只會影響將 EnableViewStateMac 屬性明確設定為 <code>false</code> 的應用程式。|
|建議|啟用ViewStateMac必須假定為 true，並且必須解決任何生成的 MAC 錯誤（如[本指南](https://support.microsoft.com/kb/2915218)中所述，其中包含多個解析度，具體取決於導致 MAC 錯誤的原因）。|
|影響範圍|主要|
|版本|4.5.2|
|類型|執行階段|
