---
title: WF 中的交易活動
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: 7ffd64abdc6edf45174d4b756833d65ec0ef747c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714771"
---
# <a name="transaction-activities-in-wf"></a>WF 中的交易活動

  [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 有幾種系統提供的活動，用於模型化異動、補償和取消。 這些程式設計模型允許在商務邏輯和錯誤處理發生變更事件時，工作流程可繼續執行。 如需交易、 補償和取消的詳細資訊，請參閱[交易](workflow-transactions.md)，[補償](compensation.md)，並[取消](modeling-cancellation-behavior-in-workflows.md)。  
  
## <a name="transaction-activities"></a>異動活動  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|將取消邏輯 (採活動形式) 與執行主要路徑 (也使用活動表示) 產生關聯。|  
|<xref:System.Activities.Statements.CompensableActivity>|支援其子活動的補償。|  
|<xref:System.Activities.Statements.Compensate>|明確叫用 <xref:System.Activities.Statements.CompensableActivity> 的補償處理常式。|  
|<xref:System.Activities.Statements.Confirm>|明確叫用 <xref:System.Activities.Statements.CompensableActivity> 的確認處理常式。|  
|<xref:System.Activities.Statements.TransactionScope>|區分交易界限。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|範圍為接收之訊息所啟始的交易存留時間。 異動可能會流動至初始訊息上的工作流程，或是在接收到訊息時由發送器所建立。 **注意：**<xref:System.ServiceModel.Activities.TransactedReceiveScope>位於**Messaging**一節**工具箱**。|
