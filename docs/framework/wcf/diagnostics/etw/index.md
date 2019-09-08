---
title: 具有 ETW 的分析追蹤
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: dd745730ca186b9489c547f790c546e95bf96372
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798085"
---
# <a name="analytic-tracing-with-etw"></a>具有 ETW 的分析追蹤
Windows Communication Foundation （WCF）分析追蹤提供在 WCF 服務執行期間捕捉診斷資訊的方法。 WCF 分析追蹤事件會在 WCF 堆疊的關鍵點發出，以允許在生產環境中進行 WCF 服務的疑難排解。 Wcf 服務的分析追蹤對於裝載[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF 服務之產品伺服器的效能影響最小，因為這些事件非常有效率地發出至 Windows 事件追蹤（ETW）會話。  
  
## <a name="in-this-section"></a>本節內容  
 [分析追蹤概觀](analytic-tracing-overview.md)  
 討論 WCF 分析追蹤在中的[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]運作方式。  
  
 [動態地啟用分析追蹤](dynamically-enabling-analytic-tracing.md)  
 討論如何啟用或停用 ETW 動態追蹤。  
  
 [設定訊息流程追蹤](configuring-message-flow-tracing.md)  
 說明如何設定訊息流程追蹤。  
  
 [分析追蹤事件參考](analytic-trace-event-reference.md)  
 顯示一份資料表，列出事件識別碼，並附上事件層級、事件訊息及關鍵字。  
  
## <a name="see-also"></a>另請參閱

- [WCF 服務和 Windows 的事件追蹤](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [在 Windows 事件追蹤中追蹤事件](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
