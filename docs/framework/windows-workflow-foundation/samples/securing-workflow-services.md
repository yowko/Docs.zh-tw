---
title: "保護工作流程服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba98ac3e64d7dcbf52ed6363d44487af54128437
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="securing-workflow-services"></a><span data-ttu-id="5ba0a-102">保護工作流程服務</span><span class="sxs-lookup"><span data-stu-id="5ba0a-102">Securing Workflow Services</span></span>
<span data-ttu-id="5ba0a-103">安全工作流程服務範例示範下列程序：</span><span class="sxs-lookup"><span data-stu-id="5ba0a-103">The Secured Workflow Service sample shows the following procedures:</span></span>  
  
-   <span data-ttu-id="5ba0a-104">使用 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動建立基本工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-104">Creating a basic workflow service using the <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
-   <span data-ttu-id="5ba0a-105">使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 組態，定義工作流程服務所用的安全端點。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-105">Using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] configuration to define secure endpoints for use by the workflow service.</span></span>  
  
-   <span data-ttu-id="5ba0a-106">在自訂原則中建立宣告，並使用 <xref:System.ServiceModel.ServiceAuthorizationManager> 驗證宣告。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-106">Creating claims inside a custom policy and using the <xref:System.ServiceModel.ServiceAuthorizationManager> to validate claims.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5ba0a-107">示範</span><span class="sxs-lookup"><span data-stu-id="5ba0a-107">Demonstrates</span></span>  
 <span data-ttu-id="5ba0a-108">使用 WCF 安全性保護用戶端和工作流程服務之間的通訊、宣告架構的授權</span><span class="sxs-lookup"><span data-stu-id="5ba0a-108">Using WCF security to secure communication between client and Workflow service, Claims based authorization</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5ba0a-109">討論</span><span class="sxs-lookup"><span data-stu-id="5ba0a-109">Discussion</span></span>  
 <span data-ttu-id="5ba0a-110">這個範例示範如何使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 安全性基礎結構來保護工作流程服務，就像保護一般 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務一樣。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-110">This sample demonstrates the use of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security infrastructure to secure a workflow service just like you would with a normal [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="5ba0a-111">特別是對授權使用自訂宣告。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-111">Specifically, it uses a custom claim for authorization.</span></span> <span data-ttu-id="5ba0a-112">在這個範例中，會使用 <xref:System.ServiceModel.WSHttpBinding> 和訊息模式安全性搭配 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-112">In this case, it uses <xref:System.ServiceModel.WSHttpBinding> and message mode security with Windows credentials.</span></span>  
  
 <span data-ttu-id="5ba0a-113">自訂 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) 會檢查用戶端的 Windows 使用者名稱和特定字元。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-113">The custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) checks the client's Windows username and for a specific character.</span></span> <span data-ttu-id="5ba0a-114">如果該字元存在，則會建立宣告並將它加入至 <xref:System.IdentityModel.Policy.EvaluationContext>。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-114">If that character is present, it creates and adds the claim to the <xref:System.IdentityModel.Policy.EvaluationContext>.</span></span> <span data-ttu-id="5ba0a-115">透過這種方式，自訂原則表示用戶端的使用者名稱中有這個字元。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-115">By doing this, the custom policy is making the statement that the client has this character in the username.</span></span> <span data-ttu-id="5ba0a-116">在呼叫的存留期間，可以查詢這個宣告。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-116">This claim can be queried throughout the lifetime of the call.</span></span> <span data-ttu-id="5ba0a-117">您可以在 `Constants.cs` 中找到該字元。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-117">You can find that character in `Constants.cs`.</span></span>  
  
 <span data-ttu-id="5ba0a-118">授權原則會在 `SecureWorkFlowAuthZManager` 中尋找宣告。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-118">The authorization policy looks for the claim inside the `SecureWorkFlowAuthZManager`.</span></span> <span data-ttu-id="5ba0a-119">如果找到，會傳回 `true` 並允許工作流程繼續執行。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-119">If it finds it, it returns `true` and allow the workflow to proceed.</span></span> <span data-ttu-id="5ba0a-120">否則會傳回 `false`，導致「拒絕存取」訊息傳回至用戶端。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-120">Otherwise, it returns `false`, which causes an 'Access Denied' message to be returned to the client.</span></span> <span data-ttu-id="5ba0a-121">其他宣告存在於此內容中，也可以在 `SecureWorkFlowAuthZManager` 中進行檢查。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-121">Other claims are present in the context and can be examined as well inside the `SecureWorkFlowAuthZManager`.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="5ba0a-122">若要執行這個範例</span><span class="sxs-lookup"><span data-stu-id="5ba0a-122">To run this sample</span></span>  
  
1.  <span data-ttu-id="5ba0a-123">以系統管理員權限執行 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-123">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="5ba0a-124">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入 SecuringWorkflowServices.sln。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-124">Load SecuringWorkflowServices.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="5ba0a-125">按 CTRL+SHIFT+B 以編譯方案。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-125">Press CTRL+SHIFT+B to compile the solution.</span></span>  
  
4.  <span data-ttu-id="5ba0a-126">將 Service 專案設定為方案的啟始專案。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-126">Set the Service project as the start-up project for the solution.</span></span>  
  
5.  <span data-ttu-id="5ba0a-127">按 CTRL+F5 啟動服務但不偵錯。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-127">Press CTRL+F5 to start the service without debugging.</span></span>  
  
6.  <span data-ttu-id="5ba0a-128">將 Client 專案設定為方案的啟始專案。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-128">Set the Client project as the start-up project for the solution.</span></span>  
  
7.  <span data-ttu-id="5ba0a-129">按 CTRL+F5 啟動用戶端但不偵錯。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-129">Press CTRL+F5 to start the client without debugging.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5ba0a-130">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5ba0a-131">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5ba0a-132">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5ba0a-133">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="5ba0a-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
