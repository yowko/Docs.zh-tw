---
title: 動態更新
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: e28a34e500034eec6cf250d94cf7631ca85a7d40
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653882"
---
# <a name="dynamic-update"></a><span data-ttu-id="e997f-102">動態更新</span><span class="sxs-lookup"><span data-stu-id="e997f-102">Dynamic Update</span></span>

<span data-ttu-id="e997f-103">動態更新提供的機制可讓工作流程應用程式開發人員更新持續性工作流程執行個體的工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="e997f-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="e997f-104">這可以是實作錯誤修復、新要求，或是適應突如其來的變化。</span><span class="sxs-lookup"><span data-stu-id="e997f-104">This can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="e997f-105">本主題提供 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中引進的動態更新功能概觀。</span><span class="sxs-lookup"><span data-stu-id="e997f-105">This topic provides an overview of the dynamic update functionality introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>

## <a name="dynamic-update"></a><span data-ttu-id="e997f-106">動態更新</span><span class="sxs-lookup"><span data-stu-id="e997f-106">Dynamic Update</span></span>

<span data-ttu-id="e997f-107">若要將動態更新套用於持續性的工作流程執行個體，需建立<xref:System.Activities.DynamicUpdate.DynamicUpdateMap>，其中包含執行階段指示，描述如何修改保存的工作流程執行個體以反映所需的變更。</span><span class="sxs-lookup"><span data-stu-id="e997f-107">To apply dynamic updates to a persisted workflow instance, a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> is created that contains instructions for the runtime that describe how to modify the persisted workflow instance to reflect the desired changes.</span></span> <span data-ttu-id="e997f-108">建立更新對應之後，會將其套用至所需保存的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="e997f-108">Once the update map is created, it is applied to the desired persisted workflow instances.</span></span> <span data-ttu-id="e997f-109">套用動態更新後，可以使用新更新的工作流程定義繼續工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="e997f-109">Once the dynamic update is applied, the workflow instance may be resumed using the new updated workflow definition.</span></span> <span data-ttu-id="e997f-110">建立及套用更新對應需要四個步驟。</span><span class="sxs-lookup"><span data-stu-id="e997f-110">There are four steps required to create and apply an update map.</span></span>

1. [<span data-ttu-id="e997f-111">準備動態更新工作流程定義</span><span class="sxs-lookup"><span data-stu-id="e997f-111">Prepare the workflow definition for dynamic update</span></span>](dynamic-update.md#Prepare)

2. [<span data-ttu-id="e997f-112">更新工作流程定義，以反映所需的變更</span><span class="sxs-lookup"><span data-stu-id="e997f-112">Update the workflow definition to reflect the desired changes</span></span>](dynamic-update.md#Update)

3. [<span data-ttu-id="e997f-113">建立更新對應</span><span class="sxs-lookup"><span data-stu-id="e997f-113">Create the update map</span></span>](dynamic-update.md#Create)

4. [<span data-ttu-id="e997f-114">將更新對應套用至所需的持續性工作流程執行個體</span><span class="sxs-lookup"><span data-stu-id="e997f-114">Apply the update map to the desired persisted workflow instances</span></span>](dynamic-update.md#Apply)

> [!NOTE]
> <span data-ttu-id="e997f-115">請注意，步驟 1 到 3 涵蓋更新對應的建立程序，不需套用更新也可執行。</span><span class="sxs-lookup"><span data-stu-id="e997f-115">Note that steps 1 through 3, which cover the creation of the update map, may be performed independently of applying the update.</span></span> <span data-ttu-id="e997f-116">常見的案例，工作流程開發人員會建立更新對應離線時，，然後以系統管理員將會套用在稍後更新。</span><span class="sxs-lookup"><span data-stu-id="e997f-116">A common scenario that the workflow developer will create the update map offline, and then an administrator will apply the update at a later time.</span></span>

<span data-ttu-id="e997f-117">本主題提供動態更新流程概觀，說明如何將新活動加入到已編譯 XAML 工作流程內持續性的執行個體中。</span><span class="sxs-lookup"><span data-stu-id="e997f-117">This topic provides an overview of the dynamic update process of adding a new activity to a persisted instance of a compiled Xaml workflow.</span></span>

### <a name="Prepare"></a> <span data-ttu-id="e997f-118">準備動態更新工作流程定義</span><span class="sxs-lookup"><span data-stu-id="e997f-118">Prepare the workflow definition for dynamic update</span></span>

<span data-ttu-id="e997f-119">動態更新程序中的第一步，是準備更新所需的工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="e997f-119">The first step in the dynamic update process is to prepare the desired workflow definition for update.</span></span> <span data-ttu-id="e997f-120">呼叫 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> 方法並傳入要修改的工作流程定義，即可準備完成。</span><span class="sxs-lookup"><span data-stu-id="e997f-120">This is done by calling the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method and passing in the workflow definition to modify.</span></span> <span data-ttu-id="e997f-121">這個方法會先驗證再一一查核工作流程樹狀，找出所有需要標記的物件 (例如公用活動和變數)，之後可將這些物件與修改過的工作流程定義進行比較。</span><span class="sxs-lookup"><span data-stu-id="e997f-121">This method validates and then walks the workflow tree to identify all of the objects such as public activities and variables that need to be tagged so they can be compared later with the modified workflow definition.</span></span> <span data-ttu-id="e997f-122">完成此步驟後，會複製工作流程樹狀，並將其附加到原始的工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="e997f-122">When this is complete, the workflow tree is cloned and attached to the original workflow definition.</span></span> <span data-ttu-id="e997f-123">建立更新對應時，會比較更新版工作流程定義與原始工作流程定義，並根據差異產生更新對應。</span><span class="sxs-lookup"><span data-stu-id="e997f-123">When the update map is created, the updated version of the workflow definition is compared with the original workflow definition and the update map is generated based on the differences.</span></span>

<span data-ttu-id="e997f-124">為準備 XAML 工作流程以進行動態更新，會將其載入到 <xref:System.Activities.ActivityBuilder> 中，然後將 <xref:System.Activities.ActivityBuilder> 傳遞到 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> 中。</span><span class="sxs-lookup"><span data-stu-id="e997f-124">To prepare a Xaml workflow for dynamic update it may be loaded into an <xref:System.Activities.ActivityBuilder>, and then the <xref:System.Activities.ActivityBuilder> is passed into <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="e997f-125">如需有關使用序列化工作流程並<xref:System.Activities.ActivityBuilder>，請參閱 <<c2> [ 序列化工作流程和活動與 XAML](serializing-workflows-and-activities-to-and-from-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="e997f-125">For more information about working with serialized workflows and <xref:System.Activities.ActivityBuilder>, see [Serializing Workflows and Activities to and from XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

<span data-ttu-id="e997f-126">以下範例中，會將 `MortgageWorkflow` 定義 (包含有數個子活動的 <xref:System.Activities.Statements.Sequence>) 載入到 <xref:System.Activities.ActivityBuilder> 中，然後準備進行動態更新。</span><span class="sxs-lookup"><span data-stu-id="e997f-126">In the following example, a `MortgageWorkflow` definition (that consists of a <xref:System.Activities.Statements.Sequence> with several child activities) is loaded into an <xref:System.Activities.ActivityBuilder>, and then prepared for dynamic update.</span></span> <span data-ttu-id="e997f-127">方法傳回後，<xref:System.Activities.ActivityBuilder> 會包含原始工作流程定義及複本。</span><span class="sxs-lookup"><span data-stu-id="e997f-127">After the method returns, the <xref:System.Activities.ActivityBuilder> contains the original workflow definition as well as a copy.</span></span>

```csharp
// Load the MortgageWorkflow definition from Xaml into
// an ActivityBuilder.
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
{
    LocalAssembly = Assembly.GetExecutingAssembly()
};

XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefinitions\MortgageWorkflow.xaml",
    readerSettings);

ActivityBuilder ab = XamlServices.Load(
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;

// Prepare the workflow definition for dynamic update.
DynamicUpdateServices.PrepareForUpdate(ab);
```

> [!NOTE]
> <span data-ttu-id="e997f-128">若要下載本主題相關的範例程式碼，請參閱[動態更新範例程式碼](https://go.microsoft.com/fwlink/?LinkId=227905)。</span><span class="sxs-lookup"><span data-stu-id="e997f-128">To download the sample code that accompanies this topic, see [Dynamic Update sample code](https://go.microsoft.com/fwlink/?LinkId=227905).</span></span>

### <a name="Update"></a> <span data-ttu-id="e997f-129">更新工作流程定義，以反映所需的變更</span><span class="sxs-lookup"><span data-stu-id="e997f-129">Update the workflow definition to reflect the desired changes</span></span>

<span data-ttu-id="e997f-130">準備好用於更新的工作流程定義後，即可進行所需的修改。</span><span class="sxs-lookup"><span data-stu-id="e997f-130">Once the workflow definition has been prepared for updating, the desired changes can be made.</span></span> <span data-ttu-id="e997f-131">您可以新增或移除活動；新增、移動或刪除公用變數；新增或移除引數，也可以變更活動委派的特徵標記。</span><span class="sxs-lookup"><span data-stu-id="e997f-131">You can add or remove activities, add, move or delete public variables, add or remove arguments, and make changes to the signature of activity delegates.</span></span> <span data-ttu-id="e997f-132">您不能移除執行中的活動，也不能變更執行中委派的特徵標記。</span><span class="sxs-lookup"><span data-stu-id="e997f-132">You cannot remove a running activity or change the signature of a running delegate.</span></span> <span data-ttu-id="e997f-133">您可以使用程式碼進行這些變更，也可以在重新裝載的工作流程設計工具中進行。</span><span class="sxs-lookup"><span data-stu-id="e997f-133">These changes may be made using code, or in a re-hosted workflow designer.</span></span> <span data-ttu-id="e997f-134">下列範例中，會將自訂的 `VerifyAppraisal` 活動加入序列中，這個序列組成上一個範例中 `MortgageWorkflow` 的主體。</span><span class="sxs-lookup"><span data-stu-id="e997f-134">In the following example, a custom `VerifyAppraisal` activity is added to the Sequence that makes up the body of the `MortgageWorkflow` from the previous example.</span></span>

```csharp
// Make desired changes to the definition. In this example, we are
// inserting a new VerifyAppraisal activity as the 3rd child of the root Sequence.
VerifyAppraisal va = new VerifyAppraisal
{
    Result = new VisualBasicReference<bool>("LoanCriteria")
};

// Get the Sequence that makes up the body of the workflow.
Sequence s = ab.Implementation as Sequence;

// Insert the new activity into the Sequence.
s.Activities.Insert(2, va);
```

### <a name="Create"></a> <span data-ttu-id="e997f-135">建立更新對應</span><span class="sxs-lookup"><span data-stu-id="e997f-135">Create the update map</span></span>

<span data-ttu-id="e997f-136">準備用於更新的工作流程定義修改完畢之後，就可以建立更新對應。</span><span class="sxs-lookup"><span data-stu-id="e997f-136">Once the workflow definition that was prepared for update has been modified, the update map can be created.</span></span> <span data-ttu-id="e997f-137">為了建立動態更新對應，會叫用 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="e997f-137">To create a dynamic update map, the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> method is invoked.</span></span> <span data-ttu-id="e997f-138">這樣會傳回 <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>，其中包含執行階段修改持續性的工作流程執行個體，使其能夠以新工作流程定義載入及繼續所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="e997f-138">This returns a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> that contains the information the runtime needs to modify a persisted workflow instance so that it may be loaded and resumed with the new workflow definition.</span></span> <span data-ttu-id="e997f-139">下列範例中，會以在上一個範例中修改過的 `MortgageWorkflow` 定義建立動態對應。</span><span class="sxs-lookup"><span data-stu-id="e997f-139">In the following example, a dynamic map is created for the modified `MortgageWorkflow` definition from the previous example.</span></span>

```csharp
// Create the update map.
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);
```

<span data-ttu-id="e997f-140">此更新對應可以立即用於修改持續性的工作流程執行個體，較常見的做法是加以儲存，並於稍後進行更新。</span><span class="sxs-lookup"><span data-stu-id="e997f-140">This update map can immediately be used to modify persisted workflow instances, or more typically it can be saved and the updates applied later.</span></span> <span data-ttu-id="e997f-141">儲存更新對應的其中一個方法是將它序列化成檔案，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e997f-141">One way to save the update map is to serialize it to a file, as shown in the following example.</span></span>

```csharp
// Serialize the update map to a file.
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Create))
{
    serializer.WriteObject(fs, map);
}
```

<span data-ttu-id="e997f-142">當 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> 傳回時，會移除加入到 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> 呼叫中的工作流程定義複本和其他動態更新資訊，然後可以儲存修改過的工作流程定義，之後用於繼續更新過的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="e997f-142">When <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> returns, the cloned workflow definition and other dynamic update information that was added in the call to <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> is removed, and the modified workflow definition is ready to be saved so that it can be used later when resuming updated workflow instances.</span></span> <span data-ttu-id="e997f-143">在下列範例中，修改過的工作流程定義會儲存至 `MortgageWorkflow_v1.1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="e997f-143">In the following example, the modified workflow definition is saved to `MortgageWorkflow_v1.1.xaml`.</span></span>

```csharp
// Save the modified workflow definition.
StreamWriter sw = File.CreateText(@"C:\WorkflowDefinitions\MortgageWorkflow_v1.1.xaml");
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
sw.Close();
```

### <a name="Apply"></a> <span data-ttu-id="e997f-144">將更新對應套用至所需的持續性工作流程執行個體</span><span class="sxs-lookup"><span data-stu-id="e997f-144">Apply the update map to the desired persisted workflow instances</span></span>

<span data-ttu-id="e997f-145">建立更新對應之後，隨時可以套用。</span><span class="sxs-lookup"><span data-stu-id="e997f-145">Applying the update map can be done at any time after creating it.</span></span> <span data-ttu-id="e997f-146">您可以立即使用 <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> 傳回的 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> 執行個體套用更新對應，也可以之後再使用儲存的更新對應複本進行。</span><span class="sxs-lookup"><span data-stu-id="e997f-146">It can be done right away using the <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instance that was returned by <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, or it can be done later using a saved copy of the update map.</span></span> <span data-ttu-id="e997f-147">若要更新工作流程執行個體，請使用 <xref:System.Activities.WorkflowApplicationInstance> 將它載入至 <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e997f-147">To update a workflow instance, load it into a <xref:System.Activities.WorkflowApplicationInstance> using <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e997f-148">接下來，請使用更新過的工作流程定義及所需的 <xref:System.Activities.WorkflowApplication>，以建立 <xref:System.Activities.WorkflowIdentity>。</span><span class="sxs-lookup"><span data-stu-id="e997f-148">Next, create a <xref:System.Activities.WorkflowApplication> using the updated workflow definition, and the desired <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="e997f-149">這個 <xref:System.Activities.WorkflowIdentity> 可能不同於用於保存原始工作流程者，而且通常是為了反映出此持續性的個體已經過修改。</span><span class="sxs-lookup"><span data-stu-id="e997f-149">This <xref:System.Activities.WorkflowIdentity> may be different than the one that was used to persist the original workflow, and typically is in order to reflect that the persisted instance has been modified.</span></span> <span data-ttu-id="e997f-150">建立 <xref:System.Activities.WorkflowApplication> 之後，會使用 <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> 的多載 (採用 <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>) 載入，然後呼叫 <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType> 來進行卸載。</span><span class="sxs-lookup"><span data-stu-id="e997f-150">Once the <xref:System.Activities.WorkflowApplication> is created, it is loaded using the overload of <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> that takes a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, and then unloaded with a call to <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e997f-151">這樣可以套用動態更新並保存更新過的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="e997f-151">This applies the dynamic update and persists the updated workflow instance.</span></span>

```csharp
// Load the serialized update map.
DynamicUpdateMap map;
using (FileStream fs = File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Open))
{
    DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
    object updateMap = serializer.ReadObject(fs);
    if (updateMap == null)
    {
        throw new ApplicationException("DynamicUpdateMap is null.");
    }

    map = (DynamicUpdateMap)updateMap;
}

// Retrieve a list of workflow instance ids that corresponds to the
// workflow instances to update. This step is the responsibility of
// the application developer.
List<Guid> ids = GetPersistedWorkflowIds();
foreach (Guid id in ids)
{
    // Get a proxy to the persisted workflow instance.
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(id, store);

    // If desired, you can inspect the WorkflowIdentity of the instance
    // using the DefinitionIdentity property to determine whether to apply
    // the update.
    Console.WriteLine(instance.DefinitionIdentity);

    // Create a workflow application. You must specify the updated workflow definition, and
    // you may provide an updated WorkflowIdentity if desired to reflect the update.
    WorkflowIdentity identity = new WorkflowIdentity
    {
        Name = "MortgageWorkflow v1.1",
        Version = new Version(1, 1, 0, 0)
    };

    // Load the persisted workflow instance using the updated workflow definition
    // and with an updated WorkflowIdentity. In this example the MortgageWorkflow class
    // contains the updated definition.
    WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

    // Apply the dynamic update on the loaded instance.
    wfApp.Load(instance, map);

    // Unload the updated instance.
    wfApp.Unload();
}
```

### <a name="resuming-an-updated-workflow-instance"></a><span data-ttu-id="e997f-152">繼續更新的工作流程執行個體</span><span class="sxs-lookup"><span data-stu-id="e997f-152">Resuming an Updated Workflow Instance</span></span>

<span data-ttu-id="e997f-153">套用動態更新之後，即可繼續該工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="e997f-153">Once dynamic update has been applied, the workflow instance may be resumed.</span></span> <span data-ttu-id="e997f-154">請注意，必須使用更新過的新定義和 <xref:System.Activities.WorkflowIdentity>。</span><span class="sxs-lookup"><span data-stu-id="e997f-154">Note that the new updated definition and <xref:System.Activities.WorkflowIdentity> must be used.</span></span>

> [!NOTE]
> <span data-ttu-id="e997f-155">如需使用詳細資訊<xref:System.Activities.WorkflowApplication>並<xref:System.Activities.WorkflowIdentity>，請參閱[使用 WorkflowIdentity 與版本控制](using-workflowidentity-and-versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="e997f-155">For more information about working with <xref:System.Activities.WorkflowApplication> and <xref:System.Activities.WorkflowIdentity>, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

<span data-ttu-id="e997f-156">在下列範例中，上一個範例中的 `MortgageWorkflow_v1.1.xaml` 工作流程已編譯完畢，並且已使用更新過的工作流程定義載入及繼續。</span><span class="sxs-lookup"><span data-stu-id="e997f-156">In the following example, the `MortgageWorkflow_v1.1.xaml` workflow from the previous example has been compiled, and is loaded and resumed using the updated workflow definition.</span></span>

```csharp
// Load the persisted workflow instance using the updated workflow definition
// and updated WorkflowIdentity.
WorkflowIdentity identity = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1.1",
    Version = new Version(1, 1, 0, 0)
};

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

// Configure persistence and desired workflow event handlers.
// (Omitted for brevity.)
ConfigureWorkflowApplication(wfApp);

// Load the persisted workflow instance.
wfApp.Load(InstanceId);

// Resume the workflow.
// wfApp.ResumeBookmark(...);
```

> [!NOTE]
> <span data-ttu-id="e997f-157">若要下載本主題相關的範例程式碼，請參閱[動態更新範例程式碼](https://go.microsoft.com/fwlink/?LinkId=227905)。</span><span class="sxs-lookup"><span data-stu-id="e997f-157">To download the sample code that accompanies this topic, see [Dynamic Update sample code](https://go.microsoft.com/fwlink/?LinkId=227905).</span></span>
