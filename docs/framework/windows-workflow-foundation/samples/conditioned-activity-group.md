---
title: ConditionedActivityGroup
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0df4ddc6f2cc5404c8153b30df66cda41487691
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="conditioned-activity-group"></a><span data-ttu-id="bd77d-102">ConditionedActivityGroup</span><span class="sxs-lookup"><span data-stu-id="bd77d-102">Conditioned Activity Group</span></span>
<span data-ttu-id="bd77d-103">本範例會示範旅遊預約應用程式。</span><span class="sxs-lookup"><span data-stu-id="bd77d-103">The sample demonstrates a travel booking application.</span></span> <span data-ttu-id="bd77d-104"><xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) 具有兩個程式碼活動：Car 活動與 Airline 活動。</span><span class="sxs-lookup"><span data-stu-id="bd77d-104">The <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) has two code activities: a Car activity and an Airline activity.</span></span> <span data-ttu-id="bd77d-105">在 `SimpleCAGWorkflow` 建構函式 (Constructor) 中，"travelNeedType" ArrayList 物件中會填入 (Populate) 所需的旅遊預約類型。</span><span class="sxs-lookup"><span data-stu-id="bd77d-105">In the `SimpleCAGWorkflow` constructor, a "travelNeedType" ArrayList object is populated with the types of travel bookings that are required.</span></span> <span data-ttu-id="bd77d-106">藉由將一個或兩個 `travelNeeds.Add` 陳述式標記為註解，您便可以修改 CAG 行為。</span><span class="sxs-lookup"><span data-stu-id="bd77d-106">By commenting out one or both of the `travelNeeds.Add` statements, you modify the CAG behavior accordingly.</span></span> <span data-ttu-id="bd77d-107">Car 與 Airline 活動兩者都有已填入 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> 的 <xref:System.Workflow.Activities.CodeCondition> 條件。</span><span class="sxs-lookup"><span data-stu-id="bd77d-107">Both the Car and Airline activities have their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> condition populated with a <xref:System.Workflow.Activities.CodeCondition>.</span></span> <span data-ttu-id="bd77d-108">Car 活動只會在 `travelNeeds` 集合具有 `TravelNeeds.Car` 項目時執行。Airline 活動則只會在 `travelNeeds` 集合具有 `TravelNeeds.Airline` 項目時執行。</span><span class="sxs-lookup"><span data-stu-id="bd77d-108">The Car activity executes only if the `travelNeeds` collection has a `TravelNeeds.Car` entry, and the Airline activity executes only if the `travelNeeds` collection has a `TravelNeeds.Airline` entry.</span></span>  
  
 <span data-ttu-id="bd77d-109">每個活動的執行都會從集合中移除對應的項目。</span><span class="sxs-lookup"><span data-stu-id="bd77d-109">The execution of each activity removes the corresponding entry from the collection.</span></span> <span data-ttu-id="bd77d-110">預設的 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> 條件會指定當沒有子系執行或是準備執行時 (根據其 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> 條件)，CAG 便應該結束。</span><span class="sxs-lookup"><span data-stu-id="bd77d-110">The default <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> condition specifies that the CAG should exit when no children are executing or are ready for execution (based on their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> conditions).</span></span> <span data-ttu-id="bd77d-111">這表示在此範例中，當 `travelNeeds` 為空集合時，CAG 便會結束。</span><span class="sxs-lookup"><span data-stu-id="bd77d-111">In this sample, this means that the CAG exits when the `travelNeeds` collection is empty.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="bd77d-112">若要建置範例</span><span class="sxs-lookup"><span data-stu-id="bd77d-112">To build the sample</span></span>  
  
1.  <span data-ttu-id="bd77d-113">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟方案。</span><span class="sxs-lookup"><span data-stu-id="bd77d-113">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="bd77d-114">按 CTRL+SHIFT+B 建置此方案。</span><span class="sxs-lookup"><span data-stu-id="bd77d-114">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="bd77d-115">按 CTRL+F5 執行方案，但不進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="bd77d-115">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="bd77d-116">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="bd77d-116">To run the sample</span></span>  
  
-   <span data-ttu-id="bd77d-117">在 [SDK 命令提示字元] 視窗中，於 SimpleCAG\bin\debug 資料夾 (若是 Visual Basic 版本的範例，則是 SimpleCAG\bin 資料夾) 中執行此 .exe 檔案，該資料夾位於此範例的主要資料夾下方。</span><span class="sxs-lookup"><span data-stu-id="bd77d-117">In the SDK Command Prompt window, run the .exe file in the SimpleCAG\bin\debug folder (or the SimpleCAG\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bd77d-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="bd77d-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bd77d-119">請先檢查下列 (預設) 目錄，然後再繼續：</span><span class="sxs-lookup"><span data-stu-id="bd77d-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bd77d-120">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="bd77d-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bd77d-121">此範例位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="bd77d-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a><span data-ttu-id="bd77d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd77d-122">See Also</span></span>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
