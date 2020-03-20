---
title: WorkflowHostingEndpoint 繼續書籤
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: d393a26dd29624765e01b139e818de8a41f73e06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182735"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="24ff7-102">WorkflowHostingEndpoint 繼續書籤</span><span class="sxs-lookup"><span data-stu-id="24ff7-102">WorkflowHostingEndpoint Resume Bookmark</span></span>
<span data-ttu-id="24ff7-103">這個範例示範 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> 如何與 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 搭配使用以建立工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="24ff7-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="24ff7-104">示範</span><span class="sxs-lookup"><span data-stu-id="24ff7-104">Demonstrates</span></span>  
 <span data-ttu-id="24ff7-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="24ff7-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="24ff7-106">討論區</span><span class="sxs-lookup"><span data-stu-id="24ff7-106">Discussion</span></span>  
 <span data-ttu-id="24ff7-107">這個範例使用 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> 來建立以 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 裝載的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="24ff7-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="24ff7-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> 是 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 的擴充點，可用於以下情形：</span><span class="sxs-lookup"><span data-stu-id="24ff7-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="24ff7-109">建立新的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="24ff7-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="24ff7-110">在裝載於 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 的工作流程執行個體中繼續使用書籤。</span><span class="sxs-lookup"><span data-stu-id="24ff7-110">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="24ff7-111">包含的範例端點會公開合約，以提供作業來建立工作流程，以及傳回執行個體識別碼或建立具有特定識別碼的執行個體。</span><span class="sxs-lookup"><span data-stu-id="24ff7-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="24ff7-112">範例主控台應用程式會建立具有基本工作流程定義的 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 執行個體，並將 `CreationEndpoint` 加入至主機。</span><span class="sxs-lookup"><span data-stu-id="24ff7-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="24ff7-113">接著會在端點上呼叫 `Create` 作業，以建立新的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="24ff7-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="24ff7-114">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="24ff7-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="24ff7-115">建置方案。</span><span class="sxs-lookup"><span data-stu-id="24ff7-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="24ff7-116">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="24ff7-116">Run the application.</span></span> <span data-ttu-id="24ff7-117">建立工作流程執行個體之後，`CreationEndpoint` 主控台會顯示包含執行個體識別碼的訊息。</span><span class="sxs-lookup"><span data-stu-id="24ff7-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="24ff7-118">留言"你好世界！</span><span class="sxs-lookup"><span data-stu-id="24ff7-118">The message "Hello World!"</span></span> <span data-ttu-id="24ff7-119">由工作流列印成功恢復書簽。</span><span class="sxs-lookup"><span data-stu-id="24ff7-119">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="24ff7-120">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="24ff7-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="24ff7-121">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="24ff7-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="24ff7-122">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="24ff7-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="24ff7-123">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="24ff7-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
