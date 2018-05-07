---
title: 具有 ETW 的分析追蹤
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: a0e3e3d27283e588b161e2209c5a682558d18f79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="analytic-tracing-with-etw"></a>具有 ETW 的分析追蹤
Windows Communication Foundation (WCF) 的分析追蹤會提供一種方式在執行期間擷取診斷資訊[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]服務。 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 分析追蹤事件會在 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 堆疊中的關鍵點發出，以便在實際執行環境中處理 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務的疑難排解。 分析追蹤[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]服務最少對效能造成影響的產品伺服器裝載[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)][!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]為這些事件會非常有效率的方式發出 Windows 事件追蹤 (ETW) 工作階段 services。  
  
## <a name="in-this-section"></a>本節內容  
 [分析追蹤概觀](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 討論 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 分析追蹤如何在 [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] 中運作。  
  
 [動態地啟用分析追蹤](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 討論如何啟用或停用 ETW 動態追蹤。  
  
 [設定訊息流程追蹤](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 說明如何設定訊息流程追蹤。  
  
 [分析追蹤事件參考](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 顯示一份資料表，列出事件識別碼，並附上事件層級、事件訊息及關鍵字。  
  
## <a name="see-also"></a>另請參閱  
 [WCF 服務和 Windows 的事件追蹤](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [在 Windows 事件追蹤中追蹤事件](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
