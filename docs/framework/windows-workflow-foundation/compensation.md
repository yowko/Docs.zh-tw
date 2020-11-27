---
title: 補償
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 60e2789c4bbd29185af50eaf6555307b894d3902
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289187"
---
# <a name="compensation"></a><span data-ttu-id="77f83-102">補償</span><span class="sxs-lookup"><span data-stu-id="77f83-102">Compensation</span></span>

<span data-ttu-id="77f83-103">Windows Workflow Foundation (WF) 中的補償是先前完成的工作可以復原或補償 (遵循應用) 程式在發生後續失敗時所定義的邏輯的機制。</span><span class="sxs-lookup"><span data-stu-id="77f83-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="77f83-104">本節描述如何在工作流程中使用補償。</span><span class="sxs-lookup"><span data-stu-id="77f83-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="77f83-105">補償與交易</span><span class="sxs-lookup"><span data-stu-id="77f83-105">Compensation vs. Transactions</span></span>  

 <span data-ttu-id="77f83-106">異動可讓您將多項作業結合成單一工作單位。</span><span class="sxs-lookup"><span data-stu-id="77f83-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="77f83-107">如果異動處理序的任何部分中發生錯誤，使用異動可讓應用程式中止 (回復) 在異動內部執行的所有變更。</span><span class="sxs-lookup"><span data-stu-id="77f83-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="77f83-108">然而，如果屬於長期執行的工作，可能就不適合使用異動。</span><span class="sxs-lookup"><span data-stu-id="77f83-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="77f83-109">例如，假設有一項旅遊計劃應用程式實作為工作流程。</span><span class="sxs-lookup"><span data-stu-id="77f83-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="77f83-110">工作流程的步驟包括預訂班機、等待經理核准，然後繳交班機費用。</span><span class="sxs-lookup"><span data-stu-id="77f83-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="77f83-111">這些處理程序可能要耗費許多天，因此讓預定班機與繳交班機費用的步驟都在同一個異動中，會是一個不實際的選擇。</span><span class="sxs-lookup"><span data-stu-id="77f83-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="77f83-112">在此類型案例中，如果處理程序稍後失敗，則可以使用補償復原工作流程的預定班機步驟。</span><span class="sxs-lookup"><span data-stu-id="77f83-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77f83-113">本主題介紹工作流程中的補償。</span><span class="sxs-lookup"><span data-stu-id="77f83-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="77f83-114">如需有關工作流程中交易的詳細資訊，請參閱 [交易](workflow-transactions.md) 和 <xref:System.Activities.Statements.TransactionScope> 。</span><span class="sxs-lookup"><span data-stu-id="77f83-114">For more information about transactions in workflows, see [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="77f83-115">如需交易的詳細資訊，請參閱 <xref:System.Transactions?displayProperty=nameWithType> 和 <xref:System.Transactions.Transaction?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="77f83-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="77f83-116">使用 CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="77f83-116">Using CompensableActivity</span></span>  

 <span data-ttu-id="77f83-117"><xref:System.Activities.Statements.CompensableActivity> 是 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 中的核心補償活動。</span><span class="sxs-lookup"><span data-stu-id="77f83-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="77f83-118">任何執行可能需補償之工作的活動，都會置放在 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 的 <xref:System.Activities.Statements.CompensableActivity> 中。</span><span class="sxs-lookup"><span data-stu-id="77f83-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="77f83-119">在此範例中，購買機票的預定步驟會置放在 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 的 <xref:System.Activities.Statements.CompensableActivity> 中，而預定取消則會置放在 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 中。</span><span class="sxs-lookup"><span data-stu-id="77f83-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="77f83-120">工作流程中的 <xref:System.Activities.Statements.CompensableActivity> 之後緊接著兩個活動，這兩個活動會等候經理核准，然後完成機票購買步驟。</span><span class="sxs-lookup"><span data-stu-id="77f83-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="77f83-121">如果錯誤狀況導致在 <xref:System.Activities.Statements.CompensableActivity> 順利完成之後取消工作流程，則會排定 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 處理常式中的活動，並取消班機。</span><span class="sxs-lookup"><span data-stu-id="77f83-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="77f83-122">下列範例是 XAML 中的工作流程。</span><span class="sxs-lookup"><span data-stu-id="77f83-122">The following example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="77f83-123">當叫用此工作流程時，主控台就會顯示下列輸出。</span><span class="sxs-lookup"><span data-stu-id="77f83-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="77f83-124">**ReserveFlight: Ticket is reserved.**</span><span class="sxs-lookup"><span data-stu-id="77f83-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="77f83-125">**ManagerApproval：已收到管理員核准。** 
**PurchaseFlight：已購買票證。** 
**工作流程已順利完成，狀態：已關閉。**</span><span class="sxs-lookup"><span data-stu-id="77f83-125">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**Workflow completed successfully with status: Closed.**</span></span>
> [!NOTE]
> <span data-ttu-id="77f83-126">本主題中的範例活動 (例如 `ReserveFlight`) 會將其名稱和目的顯示到主控台，以協助說明發生補償時活動的執行順序。</span><span class="sxs-lookup"><span data-stu-id="77f83-126">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="77f83-127">預設的工作流程補償</span><span class="sxs-lookup"><span data-stu-id="77f83-127">Default Workflow Compensation</span></span>  

 <span data-ttu-id="77f83-128">根據預設，如果取消工作流程，會執行任何已順利完成且尚未確認或補償之可補償活動的補償邏輯。</span><span class="sxs-lookup"><span data-stu-id="77f83-128">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77f83-129"><xref:System.Activities.Statements.CompensableActivity>*確認* 之後，就無法再叫用活動的補償。</span><span class="sxs-lookup"><span data-stu-id="77f83-129">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="77f83-130">本節稍後會描述補償程序。</span><span class="sxs-lookup"><span data-stu-id="77f83-130">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="77f83-131">在此範例中，會在預定班機之後、經理核准步驟之前擲出例外狀況。</span><span class="sxs-lookup"><span data-stu-id="77f83-131">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="77f83-132">本範例是 XAML 中的工作流程。</span><span class="sxs-lookup"><span data-stu-id="77f83-132">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:SimulatedErrorCondition />  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 [!code-csharp[CFX_CompensationExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 <span data-ttu-id="77f83-133">當叫用工作流程時，<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 中的主應用程式會處理模擬的錯誤條件例外狀況、取消工作流程，然後叫用補償邏輯。</span><span class="sxs-lookup"><span data-stu-id="77f83-133">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="77f83-134">**ReserveFlight: Ticket is reserved.**</span><span class="sxs-lookup"><span data-stu-id="77f83-134">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="77f83-135">**SimulatedErrorCondition：擲回 ApplicationException。** 
**工作流程未處理的例外狀況：** 
**ApplicationException：工作流程中的模擬錯誤條件。** 
**CancelFlight：票證已取消。** 
**工作流程已順利完成，狀態：已取消。**</span><span class="sxs-lookup"><span data-stu-id="77f83-135">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Canceled.**</span></span>

### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="77f83-136">取消和 CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="77f83-136">Cancellation and CompensableActivity</span></span>  

 <span data-ttu-id="77f83-137">如果 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 之 <xref:System.Activities.Statements.CompensableActivity> 中的活動尚未完成，而活動已取消時，則會執行 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 中的活動。</span><span class="sxs-lookup"><span data-stu-id="77f83-137">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77f83-138"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 只有在 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 之 <xref:System.Activities.Statements.CompensableActivity> 中的活動尚未完成，而活動已取消時才會叫用。</span><span class="sxs-lookup"><span data-stu-id="77f83-138">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="77f83-139"><xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 只有在 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 之 <xref:System.Activities.Statements.CompensableActivity> 中的活動已順利完成，而且後續在活動上叫用補償時才會執行。</span><span class="sxs-lookup"><span data-stu-id="77f83-139">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="77f83-140"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 讓工作流程作者有機會提供任何適當的取消邏輯。</span><span class="sxs-lookup"><span data-stu-id="77f83-140">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="77f83-141">在下列範例中，<xref:System.Activities.Statements.CompensableActivity.Body%2A> 執行期間會擲回例外狀況，接著叫用 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>。</span><span class="sxs-lookup"><span data-stu-id="77f83-141">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
```csharp  
Activity wf = new Sequence()  
{  
    Activities =  
    {  
        new CompensableActivity  
        {  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new ChargeCreditCard(),  
                    new SimulatedErrorCondition(),  
                    new ReserveFlight()  
                }  
            },  
            CompensationHandler = new CancelFlight(),  
            CancellationHandler = new CancelCreditCard()  
        },  
        new ManagerApproval(),  
        new PurchaseFlight()  
    }  
};  
```  
  
 <span data-ttu-id="77f83-142">本範例是 XAML 中的工作流程。</span><span class="sxs-lookup"><span data-stu-id="77f83-142">This example is the workflow in XAML</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <Sequence>  
      <c:ChargeCreditCard />  
      <c:SimulatedErrorCondition />  
      <c:ReserveFlight />  
    </Sequence>  
    <CompensableActivity.CancellationHandler>  
      <c:CancelCreditCard />  
    </CompensableActivity.CancellationHandler>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="77f83-143">當叫用工作流程時，<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 中的主應用程式會處理模擬的錯誤條件例外狀況、取消工作流程，然後叫用 <xref:System.Activities.Statements.CompensableActivity> 的取消邏輯。</span><span class="sxs-lookup"><span data-stu-id="77f83-143">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="77f83-144">在此範例中，補償邏輯和取消邏輯有不同的目標。</span><span class="sxs-lookup"><span data-stu-id="77f83-144">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="77f83-145">如果 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 成功完成，表示會透過信用卡扣款並預訂航班，因此補償應該會復原這兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="77f83-145">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="77f83-146"> (在此範例中，取消航班會自動取消信用卡費用。 ) 不過，如果取消了 <xref:System.Activities.Statements.CompensableActivity> ，這表示未完成， <xref:System.Activities.Statements.CompensableActivity.Body%2A> 因此的邏輯必須能夠 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 判斷如何以最佳的方式處理取消。</span><span class="sxs-lookup"><span data-stu-id="77f83-146">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="77f83-147">在此範例中，<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 會取消信用卡收費，但由於 `ReserveFlight` 是 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 中的最後一個活動，因此不會嘗試取消航班。</span><span class="sxs-lookup"><span data-stu-id="77f83-147">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="77f83-148">因為 `ReserveFlight` 是 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 中的最後一個活動，所以如果其順利完成，則 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 已完成，而且無法取消。</span><span class="sxs-lookup"><span data-stu-id="77f83-148">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="77f83-149">**ChargeCreditCard：航班信用卡收費。**</span><span class="sxs-lookup"><span data-stu-id="77f83-149">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="77f83-150">**SimulatedErrorCondition：擲回 ApplicationException。** 
**工作流程未處理的例外狀況：** 
**ApplicationException：工作流程中的模擬錯誤條件。** 
**CancelCreditCard：取消信用卡費用。** 
**工作流程已順利完成，狀態：已取消。**</span><span class="sxs-lookup"><span data-stu-id="77f83-150">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelCreditCard: Cancel credit card charges.**
**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="77f83-151">如需取消的詳細資訊，請參閱 [取消](modeling-cancellation-behavior-in-workflows.md)。</span><span class="sxs-lookup"><span data-stu-id="77f83-151">For more information about cancellation, see [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="77f83-152">使用補償活動的明確補償</span><span class="sxs-lookup"><span data-stu-id="77f83-152">Explicit Compensation Using the Compensate Activity</span></span>  

 <span data-ttu-id="77f83-153">上一節的說明涵蓋了隱含補償。</span><span class="sxs-lookup"><span data-stu-id="77f83-153">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="77f83-154">隱含補償適用於簡單的案例，旦若因排定補償處理而需較明確的控制，則可以使用 <xref:System.Activities.Statements.Compensate> 活動。</span><span class="sxs-lookup"><span data-stu-id="77f83-154">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="77f83-155">若要以 <xref:System.Activities.Statements.Compensate> 活動啟動補償程序，就會使用需要補償之 <xref:System.Activities.Statements.CompensationToken> 的 <xref:System.Activities.Statements.CompensableActivity>。</span><span class="sxs-lookup"><span data-stu-id="77f83-155">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="77f83-156"><xref:System.Activities.Statements.Compensate> 活動可用於在任何已完成但尚未確認或補償之 <xref:System.Activities.Statements.CompensableActivity> 上啟動補償。</span><span class="sxs-lookup"><span data-stu-id="77f83-156">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="77f83-157">例如，<xref:System.Activities.Statements.Compensate> 活動可用於 <xref:System.Activities.Statements.TryCatch.Catches%2A> 活動的 <xref:System.Activities.Statements.TryCatch> 區段，或在 <xref:System.Activities.Statements.CompensableActivity> 完成後的任何時間點。</span><span class="sxs-lookup"><span data-stu-id="77f83-157">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="77f83-158">在此範例中，<xref:System.Activities.Statements.Compensate> 活動的 <xref:System.Activities.Statements.TryCatch.Catches%2A> 區段中會使用 <xref:System.Activities.Statements.TryCatch> 活動，以反轉 <xref:System.Activities.Statements.CompensableActivity> 的動作。</span><span class="sxs-lookup"><span data-stu-id="77f83-158">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="77f83-159">本範例是 XAML 中的工作流程。</span><span class="sxs-lookup"><span data-stu-id="77f83-159">This example is the workflow in XAML.</span></span>  
  
```xaml  
<TryCatch  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:s="clr-namespace:System;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <TryCatch.Variables>  
    <Variable  
       x:TypeArguments="CompensationToken"  
       x:Name="__ReferenceID0"  
       Name="token1" />  
  </TryCatch.Variables>  
  <TryCatch.Try>  
    <Sequence>  
      <CompensableActivity>  
        <CompensableActivity.Result>  
          <OutArgument  
             x:TypeArguments="CompensationToken">  
            <VariableReference  
               x:TypeArguments="CompensationToken"  
               Variable="{x:Reference __ReferenceID0}">  
              <VariableReference.Result>  
                <OutArgument  
                   x:TypeArguments="Location(CompensationToken)" />  
              </VariableReference.Result>  
            </VariableReference>  
          </OutArgument>  
        </CompensableActivity.Result>  
        <CompensableActivity.CompensationHandler>  
          <c:CancelFlight />  
        </CompensableActivity.CompensationHandler>  
        <CompensableActivity.ConfirmationHandler>  
          <c:ConfirmFlight />  
        </CompensableActivity.ConfirmationHandler>  
        <c:ReserveFlight />  
      </CompensableActivity>  
      <c:SimulatedErrorCondition />  
      <c:ManagerApproval />  
      <c:PurchaseFlight />  
    </Sequence>  
  </TryCatch.Try>  
  <TryCatch.Catches>  
    <Catch  
       x:TypeArguments="s:ApplicationException">  
      <ActivityAction  
         x:TypeArguments="s:ApplicationException">  
        <Compensate>  
          <Compensate.Target>  
            <InArgument  
               x:TypeArguments="CompensationToken">  
              <VariableValue  
                 x:TypeArguments="CompensationToken"  
                 Variable="{x:Reference __ReferenceID0}">  
                <VariableValue.Result>  
                  <OutArgument  
                     x:TypeArguments="CompensationToken" />  
                </VariableValue.Result>  
              </VariableValue>  
            </InArgument>  
          </Compensate.Target>  
        </Compensate>  
      </ActivityAction>  
    </Catch>  
  </TryCatch.Catches>  
</TryCatch>  
```  
  
 <span data-ttu-id="77f83-160">當叫用此工作流程時，主控台就會顯示下列輸出。</span><span class="sxs-lookup"><span data-stu-id="77f83-160">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="77f83-161">**ReserveFlight: Ticket is reserved.**</span><span class="sxs-lookup"><span data-stu-id="77f83-161">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="77f83-162">**SimulatedErrorCondition：擲回 ApplicationException。** 
**CancelFlight：票證已取消。** 
**工作流程已順利完成，狀態：已關閉。**</span><span class="sxs-lookup"><span data-stu-id="77f83-162">**SimulatedErrorCondition: Throwing an ApplicationException.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Closed.**</span></span>

### <a name="confirming-compensation"></a><span data-ttu-id="77f83-163">確認補償</span><span class="sxs-lookup"><span data-stu-id="77f83-163">Confirming Compensation</span></span>  

 <span data-ttu-id="77f83-164">根據預設，可補償的活動可在活動完成之後隨時補償。</span><span class="sxs-lookup"><span data-stu-id="77f83-164">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="77f83-165">但在某些情況下，可能不太合適這麼做。</span><span class="sxs-lookup"><span data-stu-id="77f83-165">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="77f83-166">在上一個範例中，預訂機票的補償是取消預定。</span><span class="sxs-lookup"><span data-stu-id="77f83-166">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="77f83-167">不過，該班機完成之後，這個補償步驟就不再有效。</span><span class="sxs-lookup"><span data-stu-id="77f83-167">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="77f83-168">確認可補償的活動會叫用 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 所指定的活動。</span><span class="sxs-lookup"><span data-stu-id="77f83-168">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="77f83-169">這個動作可能的用法之一，就是允許釋放執行補償所必要的任何資源。</span><span class="sxs-lookup"><span data-stu-id="77f83-169">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="77f83-170">確認可補償的活動之後，就不能補償該活動，如果嘗試這麼做，則會擲回 <xref:System.InvalidOperationException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="77f83-170">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="77f83-171">當工作流程順利完成時，所有已順利完成但未確認及未補償的可補償活動均會依完成的順序進行反向確認。</span><span class="sxs-lookup"><span data-stu-id="77f83-171">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="77f83-172">在此範例中，會預定班機、購買機票、完成，然後確認可補償的活動。</span><span class="sxs-lookup"><span data-stu-id="77f83-172">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="77f83-173">若要確認 <xref:System.Activities.Statements.CompensableActivity>，請使用 <xref:System.Activities.Statements.Confirm> 活動並指定欲確認之 <xref:System.Activities.Statements.CompensationToken> 的 <xref:System.Activities.Statements.CompensableActivity>。</span><span class="sxs-lookup"><span data-stu-id="77f83-173">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="77f83-174">本範例是 XAML 中的工作流程。</span><span class="sxs-lookup"><span data-stu-id="77f83-174">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
  </Sequence.Variables>  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken">  
        <VariableReference  
           x:TypeArguments="CompensationToken">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(CompensationToken)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="CompensationToken"  
               x:Name="__ReferenceID0"  
               Name="token1" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <CompensableActivity.ConfirmationHandler>  
      <c:ConfirmFlight />  
    </CompensableActivity.ConfirmationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
  <c:TakeFlight />  
  <Confirm>  
    <Confirm.Target>  
      <InArgument  
         x:TypeArguments="CompensationToken">  
        <VariableValue  
           x:TypeArguments="CompensationToken"  
           Variable="{x:Reference __ReferenceID0}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="CompensationToken" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </Confirm.Target>  
  </Confirm>  
</Sequence>  
```  
  
<span data-ttu-id="77f83-175">當叫用此工作流程時，主控台就會顯示下列輸出。</span><span class="sxs-lookup"><span data-stu-id="77f83-175">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="77f83-176">**ReserveFlight: Ticket is reserved.**</span><span class="sxs-lookup"><span data-stu-id="77f83-176">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="77f83-177">**ManagerApproval：已收到管理員核准。** 
**PurchaseFlight：已購買票證。** 
**TakeFlight：航班已完成。** 
**ConfirmFlight：已採取航班，無法進行補償。** 
**工作流程已順利完成，狀態：已關閉。**</span><span class="sxs-lookup"><span data-stu-id="77f83-177">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**TakeFlight: Flight is completed.**
**ConfirmFlight: Flight has been taken, no compensation possible.**
**Workflow completed successfully with status: Closed.**</span></span>

## <a name="nesting-compensation-activities"></a><span data-ttu-id="77f83-178">巢狀補償活動</span><span class="sxs-lookup"><span data-stu-id="77f83-178">Nesting Compensation Activities</span></span>  

<span data-ttu-id="77f83-179"><xref:System.Activities.Statements.CompensableActivity> 可置於另一個 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 的 <xref:System.Activities.Statements.CompensableActivity> 區段中。</span><span class="sxs-lookup"><span data-stu-id="77f83-179">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="77f83-180">不可將 <xref:System.Activities.Statements.CompensableActivity> 放在另一個 <xref:System.Activities.Statements.CompensableActivity> 的處理常式中。</span><span class="sxs-lookup"><span data-stu-id="77f83-180">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="77f83-181">父 <xref:System.Activities.Statements.CompensableActivity> 必須確保一旦取消、確認或補償父活動後，就必須在父系完成取消、確認或補償之前確認或補償所有可補償的子活動 (已成功完成且尚未確認或補償)。</span><span class="sxs-lookup"><span data-stu-id="77f83-181">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="77f83-182">若無法明確建立模型，父 <xref:System.Activities.Statements.CompensableActivity> 會隱含補償可補償的子活動 (若父活動收到取消或補償信號)。</span><span class="sxs-lookup"><span data-stu-id="77f83-182">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="77f83-183">如果父活動收到確認信號，就會隱含確認可補償的子活動。</span><span class="sxs-lookup"><span data-stu-id="77f83-183">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="77f83-184">如果在父 <xref:System.Activities.Statements.CompensableActivity> 的處理常式中明確建立處理取消、確認或補償邏輯的模型，則會隱含確認所有未明確處理的子活動。</span><span class="sxs-lookup"><span data-stu-id="77f83-184">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f83-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77f83-185">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
