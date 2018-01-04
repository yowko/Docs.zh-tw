---
title: "WorkflowServiceHost 中的並存版本控制"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db8f79fcdc1398b891933f5fef9f07410e5de11e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="693e4-102">WorkflowServiceHost 中的並存版本控制</span><span class="sxs-lookup"><span data-stu-id="693e4-102">Side by Side Versioning in WorkflowServiceHost</span></span>
<span data-ttu-id="693e4-103">在 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 中引入的 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] 並存版本控制提供可在單一端點上裝載多個工作流程服務版本的功能。</span><span class="sxs-lookup"><span data-stu-id="693e4-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="693e4-104">提供的並存功能可讓工作流程服務進行設定，以便工作流程服務的新執行個體是使用新的工作流程定義所建立，而執行中的執行個體則是使用現有的定義完成。</span><span class="sxs-lookup"><span data-stu-id="693e4-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="693e4-105">本主題提供使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 並存執行工作流程服務的概觀。</span><span class="sxs-lookup"><span data-stu-id="693e4-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="693e4-106">若要下載的範例，並觀看影片逐步解說的工作流程服務的並存版本控制，請參閱[web 託管之 Xamlx 工作流程服務並存版本控制](http://go.microsoft.com/fwlink/?LinkId=393746)。</span><span class="sxs-lookup"><span data-stu-id="693e4-106">To download a sample and watch a video walkthrough of workflow service side-by-side versioning, see [Side by Side Versioning with a Web-Hosted Xamlx Workflow Service](http://go.microsoft.com/fwlink/?LinkId=393746).</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="693e4-107">在工作流程服務中裝載多個版本</span><span class="sxs-lookup"><span data-stu-id="693e4-107">Hosting Multiple Versions in a Workflow Service</span></span>  
 <span data-ttu-id="693e4-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> 包含兩個可設定為讓多個工作流程版本能夠並存執行的屬性：<xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> 和 <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>。</span><span class="sxs-lookup"><span data-stu-id="693e4-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="693e4-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> 包含受支援的工作流程服務版本，而 <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> 可用來唯一識別每個工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="693e4-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="693e4-110">將 <xref:System.Activities.WorkflowIdentity> 與工作流程服務產生關聯，即可達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="693e4-110">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="693e4-111"><xref:System.Activities.WorkflowIdentity> 包含三項識別資訊。</span><span class="sxs-lookup"><span data-stu-id="693e4-111">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="693e4-112"><xref:System.Activities.WorkflowIdentity.Name%2A> 和 <xref:System.Activities.WorkflowIdentity.Version%2A> 包含名稱及 <xref:System.Version>，兩者都是必要項，而 <xref:System.Activities.WorkflowIdentity.Package%2A> 則是選用項，可用來指定包含資訊 (例如組件名稱或其他所需資訊) 的其他字串。</span><span class="sxs-lookup"><span data-stu-id="693e4-112"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="693e4-113"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> 集合中所包含的每個工作流程服務都必須具有唯一的 <xref:System.Activities.WorkflowIdentity>。</span><span class="sxs-lookup"><span data-stu-id="693e4-113">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="693e4-114">如果 <xref:System.Activities.WorkflowIdentity> 的三個屬性中有任何屬性與另一個 <xref:System.Activities.WorkflowIdentity> 的不同，則其為唯一識別。</span><span class="sxs-lookup"><span data-stu-id="693e4-114">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="693e4-115">A `null` <xref:System.Activities.WorkflowIdentity>是允許的值<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>，但是只有一個舊版工作流程服務可能會有`null` <xref:System.Activities.WorkflowIdentity>。</span><span class="sxs-lookup"><span data-stu-id="693e4-115">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="693e4-116"><xref:System.Activities.WorkflowIdentity> 不應包含任何個人可識別資訊 (PII)。</span><span class="sxs-lookup"><span data-stu-id="693e4-116">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="693e4-117"><xref:System.Activities.WorkflowIdentity> 包含三個部分：<xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>)、<xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) 和 <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>)。</span><span class="sxs-lookup"><span data-stu-id="693e4-117"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="693e4-118">執行階段會在數個不同的活動生命週期點，將有關<xref:System.Activities.WorkflowIdentity> (用來建立執行個體) 的資訊發出到任何已設定的追蹤服務。</span><span class="sxs-lookup"><span data-stu-id="693e4-118">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="693e4-119">WF 追蹤沒有任何機制可隱藏 PII (機密的使用者資料)。</span><span class="sxs-lookup"><span data-stu-id="693e4-119">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="693e4-120">因此，<xref:System.Activities.WorkflowIdentity> 執行個體不應包含任何 PII 資料，因為執行階段會在追蹤記錄中發出這項資訊，因此存取檢視追蹤記錄的人有可能看見這項資訊。</span><span class="sxs-lookup"><span data-stu-id="693e4-120">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="693e4-121">裝載多個工作流服務版本的規則</span><span class="sxs-lookup"><span data-stu-id="693e4-121">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  
 <span data-ttu-id="693e4-122">當使用者將其他版本加入至 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 時，必須符合幾個條件，才能使用一組相同的端點和描述來裝載工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="693e4-122">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="693e4-123">如果有任何其他版本未能滿足這些條件，在呼叫 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 時，`Open` 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="693e4-123">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="693e4-124">提供給主機做為其他版本的各項工作流程定義必須滿足下列需求 (其中主要版本是提供給主機建構函式的工作流程服務定義)。</span><span class="sxs-lookup"><span data-stu-id="693e4-124">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="693e4-125">其他工作流程版本必須：</span><span class="sxs-lookup"><span data-stu-id="693e4-125">The additional workflow version must:</span></span>  
  
-   <span data-ttu-id="693e4-126">具有與工作流程服務主要版本相同的 <xref:System.ServiceModel.Activities.WorkflowService.Name%2A>。</span><span class="sxs-lookup"><span data-stu-id="693e4-126">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
-   <span data-ttu-id="693e4-127">在其 <xref:System.ServiceModel.Activities.Receive> 中，不得包含任何不在主要版本中的 <xref:System.ServiceModel.Activities.SendReply> 或 <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> 活動，而且這些活動必須符合作業合約。</span><span class="sxs-lookup"><span data-stu-id="693e4-127">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
-   <span data-ttu-id="693e4-128">具有唯一的 <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>。</span><span class="sxs-lookup"><span data-stu-id="693e4-128">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="693e4-129">可能只有一個工作流程定義`null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>。</span><span class="sxs-lookup"><span data-stu-id="693e4-129">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="693e4-130">允許部分變更。</span><span class="sxs-lookup"><span data-stu-id="693e4-130">Some changes are permitted.</span></span> <span data-ttu-id="693e4-131">版本之間的下列項目可能不同：</span><span class="sxs-lookup"><span data-stu-id="693e4-131">The following items may be different between the versions:</span></span>  
  
-   <span data-ttu-id="693e4-132"><xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> 的名稱和封裝可能不同於主要版本。</span><span class="sxs-lookup"><span data-stu-id="693e4-132">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
-   <span data-ttu-id="693e4-133"><xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 值可能和主要版本不同。</span><span class="sxs-lookup"><span data-stu-id="693e4-133">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
-   <span data-ttu-id="693e4-134"><xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> 可能和主要版本不同。</span><span class="sxs-lookup"><span data-stu-id="693e4-134">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
-   <span data-ttu-id="693e4-135"><xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> 可能和主要版本不同。</span><span class="sxs-lookup"><span data-stu-id="693e4-135">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="693e4-136">設定 DefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="693e4-136">Configuring the DefinitionIdentity</span></span>  
 <span data-ttu-id="693e4-137">使用工作流程設計工具中，建立工作流程服務時<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>使用設定**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="693e4-137">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="693e4-138">按一下 選取工作流程服務，然後選擇 設計工具中的服務的根活動以外**屬性 視窗**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="693e4-138">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="693e4-139">選取**WorkflowIdentity**旁邊會出現下拉式清單從**DefinitionIdentity**屬性，然後展開並指定所需<xref:System.Activities.WorkflowIdentity>屬性。</span><span class="sxs-lookup"><span data-stu-id="693e4-139">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="693e4-140">在下列範例中<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>設有<xref:System.Activities.WorkflowIdentity.Name%2A>`MortgageWorkflow`和<xref:System.Activities.WorkflowIdentity.Version%2A>的`1.0.0.0`。</span><span class="sxs-lookup"><span data-stu-id="693e4-140">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="693e4-141"><xref:System.Activities.WorkflowIdentity.Package%2A> 是選擇項，在這個範例中為 `null`。</span><span class="sxs-lookup"><span data-stu-id="693e4-141"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 <span data-ttu-id="693e4-142">![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv1.bmp "WorkflowServiceDefinitionIdentityv1")</span><span class="sxs-lookup"><span data-stu-id="693e4-142">![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv1.bmp "WorkflowServiceDefinitionIdentityv1")</span></span>  
  
 <span data-ttu-id="693e4-143">當工作流程服務是自我裝載的服務時，<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> 會在工作流程服務建構期間進行設定。</span><span class="sxs-lookup"><span data-stu-id="693e4-143">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="693e4-144">在下列範例中，<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>與相同的值與前一個範例中，設定與<xref:System.Activities.WorkflowIdentity.Name%2A>`MortgageWorkflow`和<xref:System.Activities.WorkflowIdentity.Name%2A>的`1.0.0.0`。</span><span class="sxs-lookup"><span data-stu-id="693e4-144">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
```csharp  
WorkflowService service = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflow(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
```  
  
```vb  
Dim service As New WorkflowService  
With service  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflow  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
```  
  
 <span data-ttu-id="693e4-145">A<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>並非必要，不過只有一個版本的工作流程服務可能需要**null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>。</span><span class="sxs-lookup"><span data-stu-id="693e4-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="693e4-146">如果服務在最初部署中沒有設定 <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>，而又建立更新版本，那麼這種做法會很有用。</span><span class="sxs-lookup"><span data-stu-id="693e4-146">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="693e4-147">將新版本加入至 Web 主控工作流程服務</span><span class="sxs-lookup"><span data-stu-id="693e4-147">Adding a New Version to a Web-hosted Workflow Service</span></span>  
 <span data-ttu-id="693e4-148">在 Web 主控服務中設定新版工作流程服務的第一步，就是在 `App_Code` 資料夾中建立與服務檔同名的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="693e4-148">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="693e4-149">如果服務的 `xamlx` 檔案命名為 `MortgageWorkflow.xamlx`，該資料夾也必須命名為 `MortgageWorkflow`。</span><span class="sxs-lookup"><span data-stu-id="693e4-149">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="693e4-150">將原始服務的 `xamlx` 檔案複本放在這個資料夾中，並重新命名為新的名稱，例如 `MortgageWorkflowV1.xamlx`。</span><span class="sxs-lookup"><span data-stu-id="693e4-150">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="693e4-151">對主要服務進行所需的變更，更新其 <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>，然後部署服務。</span><span class="sxs-lookup"><span data-stu-id="693e4-151">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="693e4-152">在下列範例中，<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> 已經以 <xref:System.Activities.WorkflowIdentity.Name%2A> 的 `MortageWorkflow` 和 <xref:System.Activities.WorkflowIdentity.Version%2A> 的 `2.0.0.0` 進行更新。</span><span class="sxs-lookup"><span data-stu-id="693e4-152">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 <span data-ttu-id="693e4-153">![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv2.bmp "WorkflowServiceDefinitionIdentityv2")</span><span class="sxs-lookup"><span data-stu-id="693e4-153">![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv2.bmp "WorkflowServiceDefinitionIdentityv2")</span></span>  
  
 <span data-ttu-id="693e4-154">當服務重新啟動時，舊版本會自動加入至 <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> 集合，因為其位於指定的 `App_Code` 子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="693e4-154">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="693e4-155">請注意，如果工作流程服務的主要版本具有`null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>將不會加入先前的版本。</span><span class="sxs-lookup"><span data-stu-id="693e4-155">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="693e4-156">一個版本可以有 `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>，但如果有多個版本，則主要版本不可以是具有 `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> 的版本，否則舊版本都不會加入至 <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="693e4-156">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="693e4-157">將新版本加入至自我裝載工作流程服務</span><span class="sxs-lookup"><span data-stu-id="693e4-157">Adding a New Version to a Self-hosted Workflow Service</span></span>  
 <span data-ttu-id="693e4-158">將新版本加入至自我裝載工作流程服務時，<xref:System.ServiceModel.Activities.WorkflowServiceHost> 會使用工作流程服務的主要版本進行設定，而舊的版本必須明確加入至 <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="693e4-158">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="693e4-159">在下列範例中，<xref:System.ServiceModel.Activities.WorkflowServiceHost> 會透過使用 `MortgageWorkflowV2` 工作流程定義的主要工作流程服務進行設定，而使用 `MortgageWorkflowV1` 工作流程定義所設定的工作流程服務會加入至 <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="693e4-159">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="693e4-160">每個工作流程服務都會透過反映工作流程定義版本的唯一 <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> 來進行設定。</span><span class="sxs-lookup"><span data-stu-id="693e4-160">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
```csharp  
// Create the primary version of the workflow service.  
WorkflowService serviceV2 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV2(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(2, 0, 0, 0)  
    }  
};  
  
// Configure the WorkflowServiceHost with the current version  
// of the workflow service. This code requires Administrator  
// privileges to function correctly. If running from Visual  
// Studio, Visual Studio must be run with Administrator privileges.  
WorkflowServiceHost host = new WorkflowServiceHost(serviceV2,   
    new Uri("http://localhost:8080/MortgageWorkflowService"));  
  
// Create the previous version of the workflow service.  
WorkflowService serviceV1 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV1(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
  
// Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1);  
```  
  
```vb  
'Create the primary version of the workflow service  
Dim serviceV2 As New WorkflowService  
With serviceV2  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV2  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(2, 0, 0, 0) _  
    }  
End With  
  
'Configure the WorkflowServiceHost with the current version  
'of the workflow service. This code requires Administrator  
'privileges to function correctly. If running from Visual  
'Studio, Visual Studio must be run with Administrator privileges.  
  
Dim host As New WorkflowServiceHost(serviceV2, _  
    New Uri("http://localhost:8080/MortgageWorkflowService"))  
  
'Create the previous version of the workflow service.  
Dim serviceV1 As New WorkflowService  
With serviceV1  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV1  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
  
'Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1)  
```
