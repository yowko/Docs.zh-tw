---
title: 具有 ETW 的分析追蹤
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: 4bb31eeac7c5d3c8c30f66090b07de9f8af4d5a4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274617"
---
# <a name="analytic-tracing-with-etw"></a>具有 ETW 的分析追蹤

Windows Communication Foundation (WCF) 分析追蹤可在 WCF 服務執行期間提供一種方法來捕捉診斷資訊。 Wcf 分析追蹤事件會在 WCF 堆疊的關鍵點發出，以允許在生產環境中進行 WCF 服務的疑難排解。 WCF 服務的分析追蹤對裝載 WCF 服務的產品伺服器效能造成最大的影響， [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] 因為這些事件非常有效率地發出至 Windows (ETW) 會話的事件追蹤。  
  
## <a name="in-this-section"></a>本節內容  

 [分析追蹤的概觀](analytic-tracing-overview.md)  
 討論 WCF 分析追蹤的運作方式 [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] 。  
  
 [動態地啟用分析的追蹤](dynamically-enabling-analytic-tracing.md)  
 討論如何啟用或停用 ETW 動態追蹤。  
  
 [設定訊息流程追蹤](configuring-message-flow-tracing.md)  
 說明如何設定訊息流程追蹤。  
  
 [分析的追蹤事件參考](analytic-trace-event-reference.md)  
 顯示一份資料表，列出事件識別碼，並附上事件層級、事件訊息及關鍵字。  
  
## <a name="see-also"></a>另請參閱

- [WCF 服務及 Windows 的事件追蹤](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [在 Windows 事件追蹤中追蹤事件](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
