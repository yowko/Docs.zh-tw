---
title: WF 中的交易活動
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: 7ffd64abdc6edf45174d4b756833d65ec0ef747c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670257"
---
# <a name="transaction-activities-in-wf"></a><span data-ttu-id="da652-102">WF 中的交易活動</span><span class="sxs-lookup"><span data-stu-id="da652-102">Transaction Activities in WF</span></span>
<span data-ttu-id="da652-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 有幾種系統提供的活動，用於模型化異動、補償和取消。</span><span class="sxs-lookup"><span data-stu-id="da652-103">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] has several system-provided activities for modeling transactions, compensation, and cancellation.</span></span> <span data-ttu-id="da652-104">這些程式設計模型允許在商務邏輯和錯誤處理發生變更事件時，工作流程可繼續執行。</span><span class="sxs-lookup"><span data-stu-id="da652-104">These programming models allow the workflow to continue forward progress in the event of changes in business logic and error handling.</span></span> <span data-ttu-id="da652-105">如需交易、 補償和取消的詳細資訊，請參閱[交易](workflow-transactions.md)，[補償](compensation.md)，並[取消](modeling-cancellation-behavior-in-workflows.md)。</span><span class="sxs-lookup"><span data-stu-id="da652-105">For more information about transactions, compensation, and cancellation, see [Transactions](workflow-transactions.md), [Compensation](compensation.md), and [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
## <a name="transaction-activities"></a><span data-ttu-id="da652-106">異動活動</span><span class="sxs-lookup"><span data-stu-id="da652-106">Transaction Activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|<span data-ttu-id="da652-107">將取消邏輯 (採活動形式) 與執行主要路徑 (也使用活動表示) 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="da652-107">Associates cancellation logic, in the form of an activity, with a main path of execution, also expressed as an activity.</span></span>|  
|<xref:System.Activities.Statements.CompensableActivity>|<span data-ttu-id="da652-108">支援其子活動的補償。</span><span class="sxs-lookup"><span data-stu-id="da652-108">Supports compensation of its child activities.</span></span>|  
|<xref:System.Activities.Statements.Compensate>|<span data-ttu-id="da652-109">明確叫用 <xref:System.Activities.Statements.CompensableActivity> 的補償處理常式。</span><span class="sxs-lookup"><span data-stu-id="da652-109">Explicitly invokes the compensation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.Confirm>|<span data-ttu-id="da652-110">明確叫用 <xref:System.Activities.Statements.CompensableActivity> 的確認處理常式。</span><span class="sxs-lookup"><span data-stu-id="da652-110">Explicitly invokes the confirmation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.TransactionScope>|<span data-ttu-id="da652-111">區分異動界限。</span><span class="sxs-lookup"><span data-stu-id="da652-111">Demarcates a transaction boundary.</span></span>|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|<span data-ttu-id="da652-112">範圍為接收之訊息所啟始的異動存留時間。</span><span class="sxs-lookup"><span data-stu-id="da652-112">Scopes the lifetime of a transaction that is initiated by a received message.</span></span> <span data-ttu-id="da652-113">異動可能會流動至初始訊息上的工作流程，或是在接收到訊息時由發送器所建立。</span><span class="sxs-lookup"><span data-stu-id="da652-113">The transaction may be flowed into the workflow on the initiating message, or created by the dispatcher when the message is received.</span></span> <span data-ttu-id="da652-114">**注意：** <xref:System.ServiceModel.Activities.TransactedReceiveScope>位於**Messaging**一節**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="da652-114">**Note:**  The <xref:System.ServiceModel.Activities.TransactedReceiveScope> is located in the **Messaging** section of the **Toolbox**.</span></span>|
