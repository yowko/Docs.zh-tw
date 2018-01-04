---
title: "使用 Send 的通道快取"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b12ebe4cc15629125627253200a95b1f8353bbc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="channel-caching-with-send"></a><span data-ttu-id="11ee4-102">使用 Send 的通道快取</span><span class="sxs-lookup"><span data-stu-id="11ee4-102">Channel Caching with Send</span></span>
<span data-ttu-id="11ee4-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> 可讓使用者利用 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.SendParametersContent> 活動來擁有不同層級的通道快取。</span><span class="sxs-lookup"><span data-stu-id="11ee4-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> enables users to have different levels of channel caching with <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.SendParametersContent> activities.</span></span> <span data-ttu-id="11ee4-104">預設會啟用執行個體層級的快取，而這個範例會示範下列功能：</span><span class="sxs-lookup"><span data-stu-id="11ee4-104">Instance-level caching is enabled by default and this sample demonstrates the following features:</span></span>  
  
1.  <span data-ttu-id="11ee4-105">跨應用程式定義域共用 <xref:System.ServiceModel.Activities.SendMessageChannelCache>。</span><span class="sxs-lookup"><span data-stu-id="11ee4-105">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> across an application domain.</span></span>  
  
2.  <span data-ttu-id="11ee4-106">停用通道快取。</span><span class="sxs-lookup"><span data-stu-id="11ee4-106">Disable channel caching.</span></span>  
  
3.  <span data-ttu-id="11ee4-107">在 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 中的工作流程執行個體之間共用 <xref:System.ServiceModel.Activities.WorkflowServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="11ee4-107">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> among workflow instances in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="11ee4-108">示範</span><span class="sxs-lookup"><span data-stu-id="11ee4-108">Demonstrates</span></span>  
 <span data-ttu-id="11ee4-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache> 延伸、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.ReceiveContent> 和 <xref:System.ServiceModel.Activities.SendReply> 活動。</span><span class="sxs-lookup"><span data-stu-id="11ee4-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache> extension, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="11ee4-110">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="11ee4-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="11ee4-111">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入專案方案，然後建立專案。</span><span class="sxs-lookup"><span data-stu-id="11ee4-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="11ee4-112">執行 \EchoWorkflowService\bin\debug 中產生的 EchoWorkflowService 應用程式。</span><span class="sxs-lookup"><span data-stu-id="11ee4-112">Run the EchoWorkflowService application generated in \EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="11ee4-113">執行 \EchoWorkflowClient\bin\debug 中產生的 EchoWorkflowClient 應用程式。</span><span class="sxs-lookup"><span data-stu-id="11ee4-113">Run the EchoWorkflowClient application generated in .\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="11ee4-114">用戶端會在服務上呼叫 Echo 作業並列印結果。</span><span class="sxs-lookup"><span data-stu-id="11ee4-114">The client calls the Echo operation on the service and prints the results.</span></span> <span data-ttu-id="11ee4-115">當結果已經列印之後，按下 ENTER 結束用戶端，再結束服務。</span><span class="sxs-lookup"><span data-stu-id="11ee4-115">When the results have been printed, press ENTER to exit the client and the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="11ee4-116">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="11ee4-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="11ee4-117">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="11ee4-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="11ee4-118">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="11ee4-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="11ee4-119">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="11ee4-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
