---
title: 工作流程管理端點範例
ms.date: 03/30/2017
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
ms.openlocfilehash: e34a23f76edbd957b1be7caff1b18f6934b1588b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517090"
---
# <a name="workflow-management-endpoint-sample"></a><span data-ttu-id="ed890-102">工作流程管理端點範例</span><span class="sxs-lookup"><span data-stu-id="ed890-102">Workflow Management Endpoint Sample</span></span>
<span data-ttu-id="ed890-103">這個範例示範如何使用工作流程控制端點，在本機和遠端建立及執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="ed890-103">This sample shows how a workflow control endpoint can be used to create and run workflows both locally and remotely.</span></span> <span data-ttu-id="ed890-104">此範例也示範如何裝載控制端點，以及撰寫用戶端來呼叫該控制端點以建立及執行工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="ed890-104">The sample demonstrates how to host a control endpoint and write clients that call the control endpoint to create and run the instance of a workflow.</span></span> <span data-ttu-id="ed890-105">此工作流程不是服務。</span><span class="sxs-lookup"><span data-stu-id="ed890-105">The workflow is not a service.</span></span>  
  
 <span data-ttu-id="ed890-106">在範例的服務端，工作流程裝載於 WorkflowServiceHost，並且加入 WorkflowControlEndpoint，讓用戶端可以執行控制作業 (暫停、啟動等)。</span><span class="sxs-lookup"><span data-stu-id="ed890-106">On the service side of the sample a workflow is hosted with WorkflowServiceHost and a WorkflowControlEndpoint is added so that clients can perform control operations (Suspend, Start, etc).</span></span> <span data-ttu-id="ed890-107">另外也加入使用者定義的 CreationEndpoint，以便建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="ed890-107">A user-defined CreationEndpoint is also added to allow the workflow to be created.</span></span> <span data-ttu-id="ed890-108">接著該服務會使用這些端點啟動暫停中狀態的工作流程，然後恢復該工作流程。</span><span class="sxs-lookup"><span data-stu-id="ed890-108">The service then uses these endpoints to start the workflow in a suspended state and then resume the workflow.</span></span> <span data-ttu-id="ed890-109">用戶端會執行相同的作業，但會來自用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed890-109">The client performs the same operations but from the client code.</span></span> <span data-ttu-id="ed890-110">如需有關這些介面，請參閱[流程控制端點](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)和[How to： 裝載在 IIS 中的非服務工作流程](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span><span class="sxs-lookup"><span data-stu-id="ed890-110">For more information about these interfaces see, [Workflow Control Endpoint](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) and [How to: Host a non-service workflow in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="ed890-111">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="ed890-111">To run the sample</span></span>  
  
1.  <span data-ttu-id="ed890-112">以系統管理員權限執行 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ed890-112">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="ed890-113">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 ManagementEndpoint.sln 方案。</span><span class="sxs-lookup"><span data-stu-id="ed890-113">Open the ManagementEndpoint.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="ed890-114">若要建置此方案，請按 CTRL + SHIFT + B 或選取**建置方案**從**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="ed890-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
4.  <span data-ttu-id="ed890-115">啟動 ManagementEndpoint.exe 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed890-115">Start the ManagementEndpoint.exe application.</span></span>  
  
5.  <span data-ttu-id="ed890-116">啟動 Client.exe 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed890-116">Start the Client.exe application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed890-117">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ed890-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ed890-118">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="ed890-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ed890-119">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="ed890-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ed890-120">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="ed890-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`