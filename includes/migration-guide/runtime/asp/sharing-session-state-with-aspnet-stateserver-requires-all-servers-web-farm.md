---
ms.openlocfilehash: 958a89015420ce5632d596688963d576c40b4cb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235163"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>與 Asp.Net StateServer 共用工作階段狀態需要 Web 伺服陣列中的所有伺服器使用相同的 .NET Framework 版本

|   |   |
|---|---|
|詳細資料|啟用 <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> 工作階段狀態時，指定之 Web 伺服陣列中的所有伺服器必須使用相同版本的 .NET Framework，才能正確共用狀態。|
|建議|請務必將共用狀態之 Web 伺服器上的 .NET Framework 版本同時升級。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
