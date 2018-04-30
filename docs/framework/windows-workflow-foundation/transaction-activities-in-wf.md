---
title: WF 中的異動活動
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0fecea701313f21813935518ca0301a369aa09a6
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="transaction-activities-in-wf"></a><span data-ttu-id="cea6c-102">WF 中的異動活動</span><span class="sxs-lookup"><span data-stu-id="cea6c-102">Transaction Activities in WF</span></span>
<span data-ttu-id="cea6c-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 有幾種系統提供的活動，用於模型化交易、補償和取消。</span><span class="sxs-lookup"><span data-stu-id="cea6c-103">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] has several system-provided activities for modeling transactions, compensation, and cancellation.</span></span> <span data-ttu-id="cea6c-104">這些程式設計模型允許在商務邏輯和錯誤處理發生變更事件時，工作流程可繼續執行。</span><span class="sxs-lookup"><span data-stu-id="cea6c-104">These programming models allow the workflow to continue forward progress in the event of changes in business logic and error handling.</span></span> <span data-ttu-id="cea6c-105">如需交易、 補償和取消作業的詳細資訊，請參閱[交易](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)，[補償](../../../docs/framework/windows-workflow-foundation/compensation.md)，和[取消](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)。</span><span class="sxs-lookup"><span data-stu-id="cea6c-105">For more information about transactions, compensation, and cancellation, see [Transactions](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md), [Compensation](../../../docs/framework/windows-workflow-foundation/compensation.md), and [Cancellation](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
## <a name="transaction-activities"></a><span data-ttu-id="cea6c-106">異動活動</span><span class="sxs-lookup"><span data-stu-id="cea6c-106">Transaction Activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|<span data-ttu-id="cea6c-107">將取消邏輯 (採活動形式) 與執行主要路徑 (也使用活動表示) 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="cea6c-107">Associates cancellation logic, in the form of an activity, with a main path of execution, also expressed as an activity.</span></span>|  
|<xref:System.Activities.Statements.CompensableActivity>|<span data-ttu-id="cea6c-108">支援其子活動的補償。</span><span class="sxs-lookup"><span data-stu-id="cea6c-108">Supports compensation of its child activities.</span></span>|  
|<xref:System.Activities.Statements.Compensate>|<span data-ttu-id="cea6c-109">明確叫用 <xref:System.Activities.Statements.CompensableActivity> 的補償處理常式。</span><span class="sxs-lookup"><span data-stu-id="cea6c-109">Explicitly invokes the compensation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.Confirm>|<span data-ttu-id="cea6c-110">明確叫用 <xref:System.Activities.Statements.CompensableActivity> 的確認處理常式。</span><span class="sxs-lookup"><span data-stu-id="cea6c-110">Explicitly invokes the confirmation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.TransactionScope>|<span data-ttu-id="cea6c-111">區分交易界限。</span><span class="sxs-lookup"><span data-stu-id="cea6c-111">Demarcates a transaction boundary.</span></span>|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|<span data-ttu-id="cea6c-112">範圍為接收之訊息所啟始的交易存留時間。</span><span class="sxs-lookup"><span data-stu-id="cea6c-112">Scopes the lifetime of a transaction that is initiated by a received message.</span></span> <span data-ttu-id="cea6c-113">異動可能會流動至初始訊息上的工作流程，或是在接收到訊息時由發送器所建立。</span><span class="sxs-lookup"><span data-stu-id="cea6c-113">The transaction may be flowed into the workflow on the initiating message, or created by the dispatcher when the message is received.</span></span> <span data-ttu-id="cea6c-114">**注意：** <xref:System.ServiceModel.Activities.TransactedReceiveScope>位於**傳訊**區段**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="cea6c-114">**Note:**  The <xref:System.ServiceModel.Activities.TransactedReceiveScope> is located in the **Messaging** section of the **Toolbox**.</span></span>|
