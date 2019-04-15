---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236626"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>無法再將 EnableViewStateMac 設定為 false

|   |   |
|---|---|
|詳細資料|ASP.NET 不再允許開發人員指定 <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> 或 <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>。 檢視狀態訊息驗證碼 (MAC) 現在會強制所有要求內嵌檢視狀態。 只會影響將 EnableViewStateMac 屬性明確設定為 <code>false</code> 的應用程式。|
|建議|EnableViewStateMac 必須假設為 true，而且必須解決任何產生的 MAC 錯誤 (如[這個指引](https://support.microsoft.com/kb/2915218)中所述，其中包含多個解決方法，視造成 MAC 錯誤的特定原因而定)。|
|範圍|主要|
|版本|4.5.2|
|類型|執行階段|
