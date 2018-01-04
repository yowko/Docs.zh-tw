---
title: "補償"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dd56b41b7b661b58446219d426be1a19edba059
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="compensation"></a>補償
[!INCLUDE[wf](../../../includes/wf-md.md)] 中的「補償」，是一種在發生後續錯誤時，能讓先前完成的工作復原或得到補償 (依照應用程式定義的邏輯) 的機制。 本節描述如何在工作流程中使用補償。  
  
## <a name="compensation-vs-transactions"></a>補償與異動  
 交易可讓您將多項作業結合成單一工作單位。 如果交易處理序的任何部分中發生錯誤，使用交易可讓應用程式中止 (回復) 在交易內部執行的所有變更。 然而，如果屬於長期執行的工作，可能就不適合使用交易。 例如，假設有一項旅遊計劃應用程式實作為工作流程。 工作流程的步驟包括預訂班機、等待經理核准，然後繳交班機費用。 這些處理程序可能要耗費許多天，因此讓預定班機與繳交班機費用的步驟都在同一個交易中，會是一個不實際的選擇。 在此類型案例中，如果處理程序稍後失敗，則可以使用補償復原工作流程的預定班機步驟。  
  
> [!NOTE]
>  本主題介紹工作流程中的補償。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]交易的工作流程，請參閱[交易](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)和<xref:System.Activities.Statements.TransactionScope>。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]交易，請參閱 <xref:System.Transactions?displayProperty=nameWithType> 和 <xref:System.Transactions.Transaction?displayProperty=nameWithType>。  
  
## <a name="using-compensableactivity"></a>使用 CompensableActivity  
 <xref:System.Activities.Statements.CompensableActivity> 是 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 中的核心補償活動。 任何執行可能需補償之工作的活動，都會置放在 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 的 <xref:System.Activities.Statements.CompensableActivity> 中。 在此範例中，購買機票的預定步驟會置放在 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 的 <xref:System.Activities.Statements.CompensableActivity> 中，而預定取消則會置放在 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 中。 工作流程中的 <xref:System.Activities.Statements.CompensableActivity> 之後緊接著兩個活動，這兩個活動會等候經理核准，然後完成機票購買步驟。 如果錯誤狀況導致在 <xref:System.Activities.Statements.CompensableActivity> 順利完成之後取消工作流程，則會排定 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 處理常式中的活動，並取消班機。  
  
 [!code-csharp[CFX_CompensationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 下列範例是 XAML 中的工作流程。  
  
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
  
 當叫用此工作流程時，主控台就會顯示下列輸出。  
  
 **ReserveFlight： 票證已保留。**  
**收到 ManagerApproval： 管理員核准。**   
**PurchaseFlight： 購買票證。**   
**工作流程已成功完成，狀態： 已關閉。**    
> [!NOTE]
>  本主題中的範例活動 (例如 `ReserveFlight`) 會將其名稱和目的顯示到主控台，以協助說明發生補償時活動的執行順序。  
  
### <a name="default-workflow-compensation"></a>預設的工作流程補償  
 根據預設，如果取消工作流程，會執行任何已順利完成且尚未確認或補償之可補償活動的補償邏輯。  
  
> [!NOTE]
>  當<xref:System.Activities.Statements.CompensableActivity>是*確認*，補償的活動不會再叫用。 本節稍後會描述補償程序。  
  
 在此範例中，會在預定班機之後、經理核准步驟之前擲出例外狀況。  
  
 [!code-csharp[CFX_CompensationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 本範例是 XAML 中的工作流程。  
  
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
  
 [!code-csharp[CFX_CompensationExample#100](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 當叫用工作流程時，<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 中的主應用程式會處理模擬的錯誤條件例外狀況、取消工作流程，然後叫用補償邏輯。  
  
 **ReserveFlight： 票證已保留。**  
**SimulatedErrorCondition： 擲回 ApplicationException。**   
**工作流程未處理的例外狀況：**   
**System.ApplicationException： 工作流程中模擬的錯誤條件。**   
**CancelFlight： 票證已取消。**   
**工作流程已成功完成，狀態： 已取消。**    
### <a name="cancellation-and-compensableactivity"></a>取消和 CompensableActivity  
 如果 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 之 <xref:System.Activities.Statements.CompensableActivity> 中的活動尚未完成，而活動已取消時，則會執行 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 中的活動。  
  
> [!NOTE]
>  <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 只有在 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 之 <xref:System.Activities.Statements.CompensableActivity> 中的活動尚未完成，而活動已取消時才會叫用。 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 只有在 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 之 <xref:System.Activities.Statements.CompensableActivity> 中的活動已順利完成，而且後續在活動上叫用補償時才會執行。  
  
 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 讓工作流程作者有機會提供任何適當的取消邏輯。 在下列範例中，<xref:System.Activities.Statements.CompensableActivity.Body%2A> 執行期間會擲回例外狀況，接著叫用 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>。  
  
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
  
 本範例是 XAML 中的工作流程。  
  
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
  
 當叫用工作流程時，<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 中的主應用程式會處理模擬的錯誤條件例外狀況、取消工作流程，然後叫用 <xref:System.Activities.Statements.CompensableActivity> 的取消邏輯。 在此範例中，補償邏輯和取消邏輯有不同的目標。 如果 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 成功完成，表示會透過信用卡扣款並預訂航班，因此補償應該會復原這兩個步驟。 (在這個範例中，取消航班會自動取消信用卡收費。)但是，如果取消 <xref:System.Activities.Statements.CompensableActivity>，表示 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 未完成，因此 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 的邏輯需要能夠判斷如何做出最好的取消處理。 在此範例中，<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 會取消信用卡收費，但由於 `ReserveFlight` 是 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 中的最後一個活動，因此不會嘗試取消航班。 因為 `ReserveFlight` 是 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 中的最後一個活動，所以如果其順利完成，則 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 已完成，而且無法取消。  
  
 **ChargeCreditCard： 電量航班信用卡。**  
**SimulatedErrorCondition： 擲回 ApplicationException。**   
**工作流程未處理的例外狀況：**   
**System.ApplicationException： 工作流程中模擬的錯誤條件。**   
**CancelCreditCard： 取消信用卡收費。**   
**工作流程已成功完成，狀態： 已取消。**  [!INCLUDE[crabout](../../../includes/crabout-md.md)]取消作業，請參閱[取消](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)。  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>使用補償活動的明確補償  
 上一節的說明涵蓋了隱含補償。 隱含補償適用於簡單的案例，旦若因排定補償處理而需較明確的控制，則可以使用 <xref:System.Activities.Statements.Compensate> 活動。 若要以 <xref:System.Activities.Statements.Compensate> 活動啟動補償程序，就會使用需要補償之 <xref:System.Activities.Statements.CompensationToken> 的 <xref:System.Activities.Statements.CompensableActivity>。 <xref:System.Activities.Statements.Compensate> 活動可用於在任何已完成但尚未確認或補償之 <xref:System.Activities.Statements.CompensableActivity> 上啟動補償。 例如，<xref:System.Activities.Statements.Compensate> 活動可用於 <xref:System.Activities.Statements.TryCatch.Catches%2A> 活動的 <xref:System.Activities.Statements.TryCatch> 區段，或在 <xref:System.Activities.Statements.CompensableActivity> 完成後的任何時間點。 在此範例中，<xref:System.Activities.Statements.Compensate> 活動的 <xref:System.Activities.Statements.TryCatch.Catches%2A> 區段中會使用 <xref:System.Activities.Statements.TryCatch> 活動，以反轉 <xref:System.Activities.Statements.CompensableActivity> 的動作。  
  
 [!code-csharp[CFX_CompensationExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 本範例是 XAML 中的工作流程。  
  
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
  
 當叫用此工作流程時，主控台就會顯示下列輸出。  
  
 **ReserveFlight： 票證已保留。**  
**SimulatedErrorCondition： 擲回 ApplicationException。**   
**CancelFlight： 票證已取消。**   
**工作流程已成功完成，狀態： 已關閉。**    
### <a name="confirming-compensation"></a>確認補償  
 根據預設，可補償的活動可在活動完成之後隨時補償。 但在某些情況下，可能不太合適這麼做。 在上一個範例中，預訂機票的補償是取消預定。 不過，該班機完成之後，這個補償步驟就不再有效。 確認可補償的活動會叫用 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 所指定的活動。 這個動作可能的用法之一，就是允許釋放執行補償所必要的任何資源。 確認可補償的活動之後，就不能補償該活動，如果嘗試這麼做，則會擲回 <xref:System.InvalidOperationException> 例外狀況。 當工作流程順利完成時，所有已順利完成但未確認及未補償的可補償活動均會依完成的順序進行反向確認。 在此範例中，會預定班機、購買機票、完成，然後確認可補償的活動。 若要確認 <xref:System.Activities.Statements.CompensableActivity>，請使用 <xref:System.Activities.Statements.Confirm> 活動並指定欲確認之 <xref:System.Activities.Statements.CompensationToken> 的 <xref:System.Activities.Statements.CompensableActivity>。  
  
 [!code-csharp[CFX_CompensationExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 本範例是 XAML 中的工作流程。  
  
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
  
 當叫用此工作流程時，主控台就會顯示下列輸出。  
  
 **ReserveFlight： 票證已保留。**  
**收到 ManagerApproval： 管理員核准。**   
**PurchaseFlight： 購買票證。**   
**TakeFlight： 飛行已完成。**   
**ConfirmFlight： 飛行已有人使用，無任何補償可能。**   
**工作流程已成功完成，狀態： 已關閉。**   
## <a name="nesting-compensation-activities"></a>巢狀補償活動  
 <xref:System.Activities.Statements.CompensableActivity> 可置於另一個 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 的 <xref:System.Activities.Statements.CompensableActivity> 區段中。 不可將 <xref:System.Activities.Statements.CompensableActivity> 放在另一個 <xref:System.Activities.Statements.CompensableActivity> 的處理常式中。 父 <xref:System.Activities.Statements.CompensableActivity> 必須確保一旦取消、確認或補償父活動後，就必須在父系完成取消、確認或補償之前確認或補償所有可補償的子活動 (已成功完成且尚未確認或補償)。 若無法明確建立模型，父 <xref:System.Activities.Statements.CompensableActivity> 會隱含補償可補償的子活動 (若父活動收到取消或補償信號)。 如果父活動收到確認信號，就會隱含確認可補償的子活動。 如果在父 <xref:System.Activities.Statements.CompensableActivity> 的處理常式中明確建立處理取消、確認或補償邏輯的模型，則會隱含確認所有未明確處理的子活動。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Activities.Statements.CompensableActivity>  
 <xref:System.Activities.Statements.Compensate>  
 <xref:System.Activities.Statements.Confirm>  
 <xref:System.Activities.Statements.CompensationToken>  
 [可補償的活動](../../../docs/framework/windows-workflow-foundation/samples/compensable-activity-sample.md)
