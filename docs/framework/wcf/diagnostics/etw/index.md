---
title: 具有 ETW 的分析追蹤
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: cff13439995d8a90da15b7afa15723f21574e35e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193710"
---
# <a name="analytic-tracing-with-etw"></a>具有 ETW 的分析追蹤
Windows Communication Foundation (WCF) 的分析追蹤提供 WCF 服務的執行期間擷取診斷資訊的方法。 WCF 分析追蹤事件會在生產環境中的 WCF 服務的疑難排解 WCF 堆疊中的關鍵點發出。 分析追蹤 WCF 服務的影響降到最低的產品伺服器效能裝載[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]這些事件是非常有效率的方式發出 Windows 事件追蹤 (ETW) 工作階段的 WCF 服務。  
  
## <a name="in-this-section"></a>本節內容  
 [分析追蹤的概觀](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 WCF 分析追蹤中的運作方式的討論[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]。  
  
 [動態地啟用分析的追蹤](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 討論如何啟用或停用 ETW 動態追蹤。  
  
 [設定訊息流程追蹤](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 說明如何設定訊息流程追蹤。  
  
 [分析的追蹤事件參考](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 顯示一份資料表，列出事件識別碼，並附上事件層級、事件訊息及關鍵字。  
  
## <a name="see-also"></a>另請參閱

- [WCF 服務及 Windows 的事件追蹤](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
- [在 Windows 事件追蹤中追蹤事件](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
