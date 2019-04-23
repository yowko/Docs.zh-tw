---
ms.openlocfilehash: 891c29b731214fb0028e960256b79cfc267d86b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235129"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>還原序列化跨應用程式網域的物件會失敗

|   |   |
|---|---|
|詳細資料|在某些情況下，當應用程式使用具有不同應用程式基底的兩個或多個應用程式網域時，嘗試在邏輯呼叫內容中還原序列化跨應用程式網域的物件會擲回例外狀況。|
|建議|請參閱[風險降低：在應用程式定義域之間將物件還原序列化](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)|
|範圍|Edge|
|版本|4.5.1|
|類型|執行階段|
