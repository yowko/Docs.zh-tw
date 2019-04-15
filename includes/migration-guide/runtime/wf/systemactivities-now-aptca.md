---
ms.openlocfilehash: 6cc1c65a95238e758f99090794f5e50b830d9667
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235333"
---
### <a name="systemactivities-is-now-aptca"></a>System.Activities 現在是 APTCA

|   |   |
|---|---|
|詳細資料|組件會以 <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=name> 屬性標記。|
|建議|衍生類別無法以 <xref:System.Security.SecurityCriticalAttribute?displayProperty=name> 標記。 以往衍生類型必須以 <xref:System.Security.SecurityCriticalAttribute?displayProperty=name> 標記。 不過，這項變更應該不會產生實際影響。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
