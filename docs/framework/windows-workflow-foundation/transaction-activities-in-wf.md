---
title: WF 中的交易活動
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: c40799f7f0456a13ab975a766a36e9425a2144df
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293334"
---
# <a name="transaction-activities-in-wf"></a>WF 中的交易活動

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 有幾種系統提供的活動，用於模型化異動、補償和取消。 這些程式設計模型允許在商務邏輯和錯誤處理發生變更事件時，工作流程可繼續執行。 如需交易、補償和取消的詳細資訊，請參閱 [交易](workflow-transactions.md)、 [補償](compensation.md)和 [取消](modeling-cancellation-behavior-in-workflows.md)。  
  
## <a name="transaction-activities"></a>異動活動  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|將取消邏輯 (採活動形式) 與執行主要路徑 (也使用活動表示) 產生關聯。|  
|<xref:System.Activities.Statements.CompensableActivity>|支援其子活動的補償。|  
|<xref:System.Activities.Statements.Compensate>|明確叫用 <xref:System.Activities.Statements.CompensableActivity> 的補償處理常式。|  
|<xref:System.Activities.Statements.Confirm>|明確叫用 <xref:System.Activities.Statements.CompensableActivity> 的確認處理常式。|  
|<xref:System.Activities.Statements.TransactionScope>|區分異動界限。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|範圍為接收之訊息所啟始的異動存留時間。 異動可能會流動至初始訊息上的工作流程，或是在接收到訊息時由發送器所建立。 **注意：** <xref:System.ServiceModel.Activities.TransactedReceiveScope>位於 [**工具箱**] 的 [**訊息**] 區段中。|
