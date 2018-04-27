---
title: .NET Framework 4.5 中的原則活動
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8e375e0c-d7c1-4d69-88ab-36d52db0aa7e
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d8457182b666570853953830a92c3f2380a0eb85
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="policy-activity-in-net-framework-45"></a><span data-ttu-id="6ee53-102">.NET Framework 4.5 中的原則活動</span><span class="sxs-lookup"><span data-stu-id="6ee53-102">Policy Activity in .NET Framework 4.5</span></span>
<span data-ttu-id="6ee53-103">Policy4 活動可讓 Windows Workflow Foundation [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5)<xref:System.Workflow.Activities.Rules.RuleSet>物件使用中 Windows Workflow Foundation [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) 是直接使用 WF 3.5 隨附的規則引擎。</span><span class="sxs-lookup"><span data-stu-id="6ee53-103">The Policy4 activity allows Windows Workflow Foundation in [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects to be used in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span> <span data-ttu-id="6ee53-104">您可以使用這個活動來建立及執行 WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet>。</span><span class="sxs-lookup"><span data-stu-id="6ee53-104">By using this activity, you can create and execute a WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet>.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="6ee53-105">包含在 Windows Workflow Foundation 中之 WF 3.5 規則引擎的詳細資訊，請參閱＜Windows Workflow Foundation 規則引擎簡介＞。</span><span class="sxs-lookup"><span data-stu-id="6ee53-105"> WF 3.5 Rules Engine included as part of Windows Workflow Foundation, please read Introduction to the Windows Workflow Foundation Rules Engine.</span></span> <span data-ttu-id="6ee53-106">如需有關移轉到 WF 中的規則[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]，請閱讀[移轉指引](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md)。</span><span class="sxs-lookup"><span data-stu-id="6ee53-106">For more information about migrating rules to WF in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], please read [Migration Guidance](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6ee53-107">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6ee53-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6ee53-108">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6ee53-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6ee53-109">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="6ee53-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6ee53-110">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="6ee53-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-Policy4`  
  
## <a name="projects-in-this-sample"></a><span data-ttu-id="6ee53-111">這個範例中的專案</span><span class="sxs-lookup"><span data-stu-id="6ee53-111">Projects in this Sample</span></span>  
  
|<span data-ttu-id="6ee53-112">專案名稱</span><span class="sxs-lookup"><span data-stu-id="6ee53-112">Project Name</span></span>|<span data-ttu-id="6ee53-113">描述</span><span class="sxs-lookup"><span data-stu-id="6ee53-113">Description</span></span>|<span data-ttu-id="6ee53-114">主要檔案</span><span class="sxs-lookup"><span data-stu-id="6ee53-114">Main Files</span></span>|  
|------------------|-----------------|----------------|  
|<span data-ttu-id="6ee53-115">Policy4</span><span class="sxs-lookup"><span data-stu-id="6ee53-115">Policy4</span></span>|<span data-ttu-id="6ee53-116">包含 Policy4 活動及其 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 設計工具。</span><span class="sxs-lookup"><span data-stu-id="6ee53-116">Contains the Policy4 activity and its [!INCLUDE[wf1](../../../../includes/wf1-md.md)] designer.</span></span>|<span data-ttu-id="6ee53-117">**Policy4.cs**: Policy4 活動定義。</span><span class="sxs-lookup"><span data-stu-id="6ee53-117">**Policy4.cs**: Policy4 activity definition.</span></span><br /><br /> <span data-ttu-id="6ee53-118">**PolicyDesigner.xaml**: Policy4 活動的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="6ee53-118">**PolicyDesigner.xaml**: Custom designer for Policy4 activity.</span></span> <span data-ttu-id="6ee53-119">它會使用規則編輯器 ([RuleSetDialog 類別](http://go.microsoft.com/fwlink/?LinkId=150378)) 從[!INCLUDE[wf1](../../../../includes/wf1-md.md)]規則引擎。</span><span class="sxs-lookup"><span data-stu-id="6ee53-119">It uses the rules editor ([RuleSetDialog Class](http://go.microsoft.com/fwlink/?LinkId=150378)) from [!INCLUDE[wf1](../../../../includes/wf1-md.md)] rules engine.</span></span>|  
|<span data-ttu-id="6ee53-120">ImperativeCodeClientSample</span><span class="sxs-lookup"><span data-stu-id="6ee53-120">ImperativeCodeClientSample</span></span>|<span data-ttu-id="6ee53-121">範例用戶端應用程式，透過使用命令式 C# 程式碼 (未使用 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 設計工具) 的 Policy4 應用程式，來設定及執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="6ee53-121">Sample client application that configures and runs a workflow using a Policy4 application using imperative C# code (no [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Designer used).</span></span>|<span data-ttu-id="6ee53-122">**ApplyDiscount.rules**： 檔案與[!INCLUDE[wf1](../../../../includes/wf1-md.md)]規則定義。</span><span class="sxs-lookup"><span data-stu-id="6ee53-122">**ApplyDiscount.rules**: File with [!INCLUDE[wf1](../../../../includes/wf1-md.md)] rule definitions.</span></span><br /><br /> <span data-ttu-id="6ee53-123">**Order.cs**： 代表客戶訂單的類型。</span><span class="sxs-lookup"><span data-stu-id="6ee53-123">**Order.cs**: Type that represents a customer order.</span></span> <span data-ttu-id="6ee53-124">規則套用至這個類型的物件。</span><span class="sxs-lookup"><span data-stu-id="6ee53-124">Rules are applied to objects of this type.</span></span><br /><br /> <span data-ttu-id="6ee53-125">**Program.cs**： 設定及執行工作流程，其中有 Policy4 活動套用至 Order 物件執行個體 ApplyDiscount.rules 中定義的規則。</span><span class="sxs-lookup"><span data-stu-id="6ee53-125">**Program.cs**: Configures and runs a workflow that has a Policy4 activity to apply rules defined in ApplyDiscount.rules to instances of Order objects.</span></span><br /><br /> <span data-ttu-id="6ee53-126">**App.config**： 具有規則檔路徑的組態檔。</span><span class="sxs-lookup"><span data-stu-id="6ee53-126">**App.config**: Configuration file with the path of the rules file.</span></span>|  
|<span data-ttu-id="6ee53-127">DesignerClientSample</span><span class="sxs-lookup"><span data-stu-id="6ee53-127">DesignerClientSample</span></span>|<span data-ttu-id="6ee53-128">範例用戶端應用程式，透過使用 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 設計工具的 Policy4 應用程式，來設定及執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="6ee53-128">Sample client application that configures and runs a workflow using a Policy4 application in the [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Designer.</span></span>|<span data-ttu-id="6ee53-129">**Sequence1.xaml**： 使用 Policy4 活動執行規則評估的循序工作流程。</span><span class="sxs-lookup"><span data-stu-id="6ee53-129">**Sequence1.xaml**: Sequential workflow that uses a Policy4 activity to perform rule evaluations.</span></span><br /><br /> <span data-ttu-id="6ee53-130">`Program.cs`：執行 Sequence1.xaml 中定義的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ee53-130">`Program.cs`: Runs an instance of the workflow defined in Sequence1.xaml.</span></span>|  
  
## <a name="the-policy4-activity"></a><span data-ttu-id="6ee53-131">Policy4 活動</span><span class="sxs-lookup"><span data-stu-id="6ee53-131">The Policy4 Activity</span></span>  
 <span data-ttu-id="6ee53-132">Policy4 活動是衍生自 <xref:System.Activities.NativeActivity%601> 的類別，允許工作流程執行 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] RuleSets。</span><span class="sxs-lookup"><span data-stu-id="6ee53-132">The Policy4 activity is a class that derives from <xref:System.Activities.NativeActivity%601> that allows workflows to execute [!INCLUDE[wf1](../../../../includes/wf1-md.md)] RuleSets.</span></span> <span data-ttu-id="6ee53-133">下列程式碼範例是活動的公用 OM 簡化定義。</span><span class="sxs-lookup"><span data-stu-id="6ee53-133">The following code example is a simplified definition of the public OM of the activity.</span></span>  
  
```csharp  
public class Policy4Activity<TResult>: NativeActivity<TResult>  
{  
    public RuleSet RuleSet  
  
    [IsRequired]  
    public InArgument Input  
  
    public OutArgument<ValidationErrorCollection> ValidationErrors  
}  
```  
  
|<span data-ttu-id="6ee53-134">屬性</span><span class="sxs-lookup"><span data-stu-id="6ee53-134">Property</span></span>|<span data-ttu-id="6ee53-135">描述</span><span class="sxs-lookup"><span data-stu-id="6ee53-135">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="6ee53-136">RuleSet</span><span class="sxs-lookup"><span data-stu-id="6ee53-136">RuleSet</span></span>|<span data-ttu-id="6ee53-137">在 WF [RuleSet 類別](http://go.microsoft.com/fwlink/?LinkId=150379)的.NET Framework 3.5，才能在活動執行時進行評估。</span><span class="sxs-lookup"><span data-stu-id="6ee53-137">The WF [RuleSet Class](http://go.microsoft.com/fwlink/?LinkId=150379) for .NET Framework 3.5 to be evaluated when the activity is executed.</span></span>|  
|<span data-ttu-id="6ee53-138">TargetObject</span><span class="sxs-lookup"><span data-stu-id="6ee53-138">TargetObject</span></span>|<span data-ttu-id="6ee53-139">針對物件中的規則[RuleSet 類別](http://go.microsoft.com/fwlink/?LinkId=150379)會進行評估。</span><span class="sxs-lookup"><span data-stu-id="6ee53-139">The object against which the Rules in the [RuleSet Class](http://go.microsoft.com/fwlink/?LinkId=150379) are evaluated.</span></span>|  
|<span data-ttu-id="6ee53-140">ValidationError</span><span class="sxs-lookup"><span data-stu-id="6ee53-140">ValidationError</span></span>|<span data-ttu-id="6ee53-141">所傳回的驗證錯誤的清單[!INCLUDE[wf1](../../../../includes/wf1-md.md)]適用於驗證時，.NET Framework 3.5 規則引擎[RuleSet 類別](http://go.microsoft.com/fwlink/?LinkId=150379)對目標物件之前執行。</span><span class="sxs-lookup"><span data-stu-id="6ee53-141">The list of validation errors returned by the [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Rule Engine for .NET Framework 3.5 when validating the [RuleSet Class](http://go.microsoft.com/fwlink/?LinkId=150379) against the target object before execution.</span></span>|  
  
## <a name="policy4-activity-designer"></a><span data-ttu-id="6ee53-142">Policy4 活動設計工具</span><span class="sxs-lookup"><span data-stu-id="6ee53-142">Policy4 Activity Designer</span></span>  
 <span data-ttu-id="6ee53-143">在不需要撰寫程式碼的情況下，Policy4 設計工具加入設定 Policy4 活動的功能。</span><span class="sxs-lookup"><span data-stu-id="6ee53-143">The Policy4 designer adds the capability to configure a Policy4 activity without the need to write code.</span></span> <span data-ttu-id="6ee53-144">建置方案之後, 它位於工具箱的區段中**Microsoft.Samples.Activities.Rules**。</span><span class="sxs-lookup"><span data-stu-id="6ee53-144">After building the solution, it can be found in the toolbox in the section **Microsoft.Samples.Activities.Rules**.</span></span>  
  
 <span data-ttu-id="6ee53-145">WF 設計工具可讓您設定目標物件和 RuleSet。</span><span class="sxs-lookup"><span data-stu-id="6ee53-145">The WF Designer allows you to configure a target object and a RuleSet.</span></span> <span data-ttu-id="6ee53-146">當**Edit RuleSet**按一下按鈕時，WF [RuleSetDialog 類別](http://go.microsoft.com/fwlink/?LinkId=150378)如[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]隨即出現。</span><span class="sxs-lookup"><span data-stu-id="6ee53-146">When the **Edit RuleSet** button is clicked, the WF [RuleSetDialog Class](http://go.microsoft.com/fwlink/?LinkId=150378) for [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] is displayed.</span></span> <span data-ttu-id="6ee53-147">這個對話方塊是重新裝載的 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 規則編輯器。</span><span class="sxs-lookup"><span data-stu-id="6ee53-147">This dialog is the re-hosted [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] Rules Editor.</span></span> <span data-ttu-id="6ee53-148">使用此編輯器來建立及編輯 Policy4 活動執行的規則。</span><span class="sxs-lookup"><span data-stu-id="6ee53-148">Use the editor to create and edit the rules that the Policy4 activity executes.</span></span>  
  
## <a name="using-this-sample"></a><span data-ttu-id="6ee53-149">使用這個範例</span><span class="sxs-lookup"><span data-stu-id="6ee53-149">Using this Sample</span></span>  
 <span data-ttu-id="6ee53-150">不需要特殊設定即可執行此範例。</span><span class="sxs-lookup"><span data-stu-id="6ee53-150">No special set up is required to run this sample.</span></span> <span data-ttu-id="6ee53-151">只要在 Visual Studio 中開啟方案，然後按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6ee53-151">Just open the solution in Visual Studio, and press F5 to run the application.</span></span>  
  
 <span data-ttu-id="6ee53-152">這個範例包含兩個用戶端應用程式：ImperativeCodeClientSample 和 DesignerClientSample。</span><span class="sxs-lookup"><span data-stu-id="6ee53-152">This sample contains two client applications: ImperativeCodeClientSample and DesignerClientSample.</span></span> <span data-ttu-id="6ee53-153">ImperativeCodeClientSample 用戶端示範如何透過 C# 命令式程式碼來設定及執行 Policy4 活動。</span><span class="sxs-lookup"><span data-stu-id="6ee53-153">The ImperativeCodeClientSample client shows how to configure and run the Policy40 activity using C# imperative code.</span></span> <span data-ttu-id="6ee53-154">DesignerClientSample 示範如何透過設計工具來設定及執行 Policy4 活動。</span><span class="sxs-lookup"><span data-stu-id="6ee53-154">The DesignerClientSample shows how to configure and run the Policy4 activity using the designer.</span></span>  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a><span data-ttu-id="6ee53-155">若要執行 ImperativeCodeClientSample 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="6ee53-155">To run the ImperativeCodeClientSample client application</span></span>  
  
1.  <span data-ttu-id="6ee53-156">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 Policy4Sample.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="6ee53-156">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Policy4Sample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="6ee53-157">在**方案總管 中**，以滑鼠右鍵按一下**ImperativeCodeClientSample**專案，然後選取**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="6ee53-157">In **Solution Explorer**, right-click the **ImperativeCodeClientSample** project and then select **Set as startup project**.</span></span>  
  
3.  <span data-ttu-id="6ee53-158">若要執行專案，請按 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="6ee53-158">To run the project, press CTRL+F5.</span></span>  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a><span data-ttu-id="6ee53-159">若要執行 ImperativeCodeClientSample 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="6ee53-159">To run the ImperativeCodeClientSample client application</span></span>  
  
1.  <span data-ttu-id="6ee53-160">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 Policy4Sample.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="6ee53-160">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Policy4Sample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="6ee53-161">在**方案總管 中**，以滑鼠右鍵按一下**DesignerClientSample**專案。</span><span class="sxs-lookup"><span data-stu-id="6ee53-161">In **Solution Explorer**, right-click the **DesignerClientSample** project.</span></span>  
  
    -   <span data-ttu-id="6ee53-162">選取**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="6ee53-162">Select **Set as startup project**.</span></span>  
  
3.  <span data-ttu-id="6ee53-163">若要編譯專案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="6ee53-163">To compile the project, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="6ee53-164">若要執行專案，請按 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="6ee53-164">To run the project, press CTRL+F5.</span></span>