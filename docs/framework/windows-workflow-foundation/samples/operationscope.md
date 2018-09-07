---
title: OperationScope
ms.date: 03/30/2017
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
ms.openlocfilehash: 562fd9c8ff964cb997012d49600bce73d4441465
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075627"
---
# <a name="operationscope"></a><span data-ttu-id="cce5b-102">OperationScope</span><span class="sxs-lookup"><span data-stu-id="cce5b-102">OperationScope</span></span>
<span data-ttu-id="cce5b-103">這個範例示範 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 訊息活動如何用來將現有自訂活動公開成為工作流程服務中的作業。</span><span class="sxs-lookup"><span data-stu-id="cce5b-103">This sample demonstrates how the messaging activities, <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> can be used to expose an existing custom activity as an operation in a workflow service.</span></span> <span data-ttu-id="cce5b-104">這個範例包含一個名為 `OperationScope` 的新自訂活動。</span><span class="sxs-lookup"><span data-stu-id="cce5b-104">This sample includes a new custom activity called an `OperationScope`.</span></span> <span data-ttu-id="cce5b-105">它可讓使用者將作業主體分別撰寫成自訂活動，然後使用 `OperationScope` 活動，將它們輕鬆公開為服務作業，以便於開發工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="cce5b-105">It is intended to ease the development of a workflow service by allowing users to author the body of their operations separately as custom activities and then easily exposing them as service operations using the `OperationScope` activity.</span></span> <span data-ttu-id="cce5b-106">例如，接收兩個 `Add` 引數並傳回一個 `in` 引數的自訂 `out` 活動，可以藉由放置在 `Add` 中，公開為工作流程服務的 `OperationScope` 作業。</span><span class="sxs-lookup"><span data-stu-id="cce5b-106">For example, a custom `Add` activity that takes two `in` arguments and returns one `out` argument could be exposed as an `Add` operation on the workflow service by dropping it into an `OperationScope`.</span></span>  
  
 <span data-ttu-id="cce5b-107">範圍的運作方式是檢查當成主體提供的活動。</span><span class="sxs-lookup"><span data-stu-id="cce5b-107">The scope works by inspecting the activity provided as its body.</span></span> <span data-ttu-id="cce5b-108">任何未繫結的 `in` 引數都會假定為傳入訊息中的輸入。</span><span class="sxs-lookup"><span data-stu-id="cce5b-108">Any unbound `in` arguments are assumed to be inputs from the incoming message.</span></span> <span data-ttu-id="cce5b-109">所有 `out` 引數，不論是否繫結，都會假定為後續回覆訊息中的輸出。</span><span class="sxs-lookup"><span data-stu-id="cce5b-109">All `out` arguments, regardless of whether they are bound, are assumed to be outputs in the subsequent reply message.</span></span> <span data-ttu-id="cce5b-110">公開作業名稱是取自 `OperationScope` 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="cce5b-110">The exposed operation’s name is taken from the display name of the `OperationScope` activity.</span></span> <span data-ttu-id="cce5b-111">最終結果是主體活動包裝在 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 中，其中來自訊息的參數繫結至活動的引數。</span><span class="sxs-lookup"><span data-stu-id="cce5b-111">The end result is that the body activity is wrapped in a <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> with the parameters from the messages bound to the arguments of the activity.</span></span>  
  
 <span data-ttu-id="cce5b-112">這個範例使用 HTTP 端點公開工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="cce5b-112">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="cce5b-113">若要執行，必須加入 URL ACL。</span><span class="sxs-lookup"><span data-stu-id="cce5b-113">To run, proper URL ACLs must be added.</span></span> <span data-ttu-id="cce5b-114">如需詳細資訊，請參閱 <<c0> [ 設定 HTTP 和 HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353)。</span><span class="sxs-lookup"><span data-stu-id="cce5b-114">For more information, see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="cce5b-115">執行下列命令，在提升權限提示字元中加入適當 Acl (請確定您的網域和使用者名稱取代 %網域 %\\%username%)。</span><span class="sxs-lookup"><span data-stu-id="cce5b-115">Executing the following command at an elevated prompt adds the appropriate ACLs (ensure that your Domain and Username are substituted for %DOMAIN%\\%UserName%).</span></span>  
  
 <span data-ttu-id="cce5b-116">**netsh http add urlacl =http://+:8000/使用者 = %網域 %\\%username%**</span><span class="sxs-lookup"><span data-stu-id="cce5b-116">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="cce5b-117">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="cce5b-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="cce5b-118">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 OperationScope.sln 方案。</span><span class="sxs-lookup"><span data-stu-id="cce5b-118">Open the OperationScope.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="cce5b-119">設定多個啟始專案，以滑鼠右鍵按一下方案總管 中的方案，然後選取**設定啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="cce5b-119">Set multiple start-up projects by right-clicking the solution in Solution Explorer and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="cce5b-120">加入 Scenario 和 Scenario_Client (依此順序) 做為多個啟始專案。</span><span class="sxs-lookup"><span data-stu-id="cce5b-120">Add Scenario and Scenario_Client (in that order) as multiple start-up projects.</span></span>  
  
3.  <span data-ttu-id="cce5b-121">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="cce5b-121">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="cce5b-122">由於自訂活動 `OperationScope`，需要這個步驟，才能檢視 BankService.xaml 工作流程。</span><span class="sxs-lookup"><span data-stu-id="cce5b-122">This step is required to view the BankService.xaml workflow due to the custom activity `OperationScope`.</span></span>  
  
4.  <span data-ttu-id="cce5b-123">按 CTRL+F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="cce5b-123">Press CTRL+F5 to run the application.</span></span> <span data-ttu-id="cce5b-124">Scenario_Client 主控台會提示您輸入，而且在 Scenario 主控台會顯示對應輸出。</span><span class="sxs-lookup"><span data-stu-id="cce5b-124">The Scenario_Client console prompts you for inputs and the corresponding output is seen in the Scenario console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cce5b-125">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="cce5b-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cce5b-126">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="cce5b-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cce5b-127">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="cce5b-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cce5b-128">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="cce5b-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`