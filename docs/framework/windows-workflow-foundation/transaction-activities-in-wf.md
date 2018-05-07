---
title: WF 中的異動活動
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: f2709601fc4fd88a1c5223a5a3e97e139ceca954
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-activities-in-wf"></a>WF 中的異動活動
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 有幾種系統提供的活動，用於模型化交易、補償和取消。 這些程式設計模型允許在商務邏輯和錯誤處理發生變更事件時，工作流程可繼續執行。 如需交易、 補償和取消作業的詳細資訊，請參閱[交易](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)，[補償](../../../docs/framework/windows-workflow-foundation/compensation.md)，和[取消](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)。  
  
## <a name="transaction-activities"></a>異動活動  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|將取消邏輯 (採活動形式) 與執行主要路徑 (也使用活動表示) 產生關聯。|  
|<xref:System.Activities.Statements.CompensableActivity>|支援其子活動的補償。|  
|<xref:System.Activities.Statements.Compensate>|明確叫用 <xref:System.Activities.Statements.CompensableActivity> 的補償處理常式。|  
|<xref:System.Activities.Statements.Confirm>|明確叫用 <xref:System.Activities.Statements.CompensableActivity> 的確認處理常式。|  
|<xref:System.Activities.Statements.TransactionScope>|區分交易界限。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|範圍為接收之訊息所啟始的交易存留時間。 異動可能會流動至初始訊息上的工作流程，或是在接收到訊息時由發送器所建立。 **注意：** <xref:System.ServiceModel.Activities.TransactedReceiveScope>位於**傳訊**區段**工具箱**。|
