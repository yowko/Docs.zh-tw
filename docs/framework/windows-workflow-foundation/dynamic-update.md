---
title: 動態更新
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: dea930de2103a24aa48b1d0a31a3cbf5fc0ae26c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43455766"
---
# <a name="dynamic-update"></a>動態更新
動態更新提供的機制可讓工作流程應用程式開發人員更新持續性工作流程執行個體的工作流程定義。 這可以是實作錯誤修復、新要求，或是適應突如其來的變化。 本主題提供 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中引進的動態更新功能概觀。  
  
## <a name="dynamic-update"></a>動態更新  
 若要將動態更新套用於持續性的工作流程執行個體，需建立<xref:System.Activities.DynamicUpdate.DynamicUpdateMap>，其中包含執行階段指示，描述如何修改保存的工作流程執行個體以反映所需的變更。 建立更新對應之後，會將其套用至所需保存的工作流程執行個體。 套用動態更新後，可以使用新更新的工作流程定義繼續工作流程執行個體。 建立及套用更新對應需要四個步驟。  
  
1.  [準備動態更新工作流程定義](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Prepare)  
  
2.  [更新工作流程定義，以反映所需的變更](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Update)  
  
3.  [建立更新對應](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Create)  
  
4.  [將更新對應套用至所需的持續性工作流程執行個體](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Apply)  
  
> [!NOTE]
>  請注意，步驟 1 到 3 涵蓋更新對應的建立程序，不需套用更新也可執行。 工作流程開發人員常會離線建立更新對應，之後再由管理員套用更新。  
  
 本主題提供動態更新流程概觀，說明如何將新活動加入到已編譯 XAML 工作流程內持續性的執行個體中。  
  
###  <a name="Prepare"></a> 準備動態更新工作流程定義  
 動態更新程序中的第一步，是準備更新所需的工作流程定義。 呼叫 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> 方法並傳入要修改的工作流程定義，即可準備完成。 這個方法會先驗證再一一查核工作流程樹狀結構，找出所有需要標記的物件 (例如公用活動和變數)，之後可將這些物件與修改過的工作流程定義進行比較。 完成此步驟後，會複製工作流程樹狀結構，並將其附加到原始的工作流程定義。 建立更新對應時，會比較更新版工作流程定義與原始工作流程定義，並根據差異產生更新對應。  
  
 為準備 XAML 工作流程以進行動態更新，會將其載入到 <xref:System.Activities.ActivityBuilder> 中，然後將 <xref:System.Activities.ActivityBuilder> 傳遞到 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> 中。  
  
> [!NOTE]
>  如需有關使用序列化工作流程並<xref:System.Activities.ActivityBuilder>，請參閱 <<c2> [ 序列化工作流程和活動與 XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md)。  
  
 以下範例中，會將 `MortgageWorkflow` 定義 (包含有數個子活動的 <xref:System.Activities.Statements.Sequence>) 載入到 <xref:System.Activities.ActivityBuilder> 中，然後準備進行動態更新。 方法傳回後，<xref:System.Activities.ActivityBuilder> 會包含原始工作流程定義及複本。  
  
```csharp  
// Load the MortgageWorkflow definition from Xaml into  
// an ActivityBuilder.  
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()  
{  
    LocalAssembly = Assembly.GetExecutingAssembly()  
};  
  
XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefitinions\MortgageWorkflow.xaml",   
    readerSettings);  
  
ActivityBuilder ab = XamlServices.Load(  
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;  
  
// Prepare the workflow definition for dynamic update.  
DynamicUpdateServices.PrepareForUpdate(ab);  
```  
  
> [!NOTE]
>  若要下載本主題相關的範例程式碼，請參閱[動態更新範例程式碼](https://go.microsoft.com/fwlink/?LinkId=227905)。  
  
###  <a name="Update"></a> 更新工作流程定義，以反映所需的變更  
 準備好用於更新的工作流程定義後，即可進行所需的修改。 您可以新增或移除活動；新增、移動或刪除公用變數；新增或移除引數，也可以變更活動委派的特徵標記。 您不能移除執行中的活動，也不能變更執行中委派的特徵標記。 您可以使用程式碼進行這些變更，也可以在重新裝載的工作流程設計工具中進行。 下列範例中，會將自訂的 `VerifyAppraisal` 活動加入序列中，這個序列組成上一個範例中 `MortgageWorkflow` 的主體。  
  
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
  
###  <a name="Create"></a> 建立更新對應  
 準備用於更新的工作流程定義修改完畢之後，就可以建立更新對應。 為了建立動態更新對應，會叫用 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> 方法。 這樣會傳回 <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>，其中包含執行階段修改持續性的工作流程執行個體，使其能夠以新工作流程定義載入及繼續所需的資訊。 下列範例中，會以在上一個範例中修改過的 `MortgageWorkflow` 定義建立動態對應。  
  
```csharp  
// Create the update map.  
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);  
```  
  
 此更新對應可以立即用於修改持續性的工作流程執行個體，較常見的做法是加以儲存，並於稍後進行更新。 儲存更新對應的其中一個方法是將它序列化成檔案，如下列範例所示。  
  
```csharp  
// Serialize the update map to a file.  
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Create))  
{  
    serializer.WriteObject(fs, map);  
}  
```  
  
 當 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> 傳回時，會移除加入到 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> 呼叫中的工作流程定義複本和其他動態更新資訊，然後可以儲存修改過的工作流程定義，之後用於繼續更新過的工作流程執行個體。 在下列範例中，修改過的工作流程定義會儲存至 `MortgageWorkflow_v2.xaml`。  
  
```csharp  
// Save the modified workflow definition.  
StreamWriter sw = File.CreateText(@"C:\WorkflowDefitinions\MortgageWorkflow_v1.1.xaml");  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw, ab);  
sw.Close();  
```  
  
###  <a name="Apply"></a> 將更新對應套用至所需的持續性工作流程執行個體  
 建立更新對應之後，隨時可以套用。 您可以立即使用 <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> 傳回的 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> 執行個體套用更新對應，也可以之後再使用儲存的更新對應複本進行。 若要更新工作流程執行個體，請使用 <xref:System.Activities.WorkflowApplicationInstance> 將它載入至 <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>。 接下來，請使用更新過的工作流程定義及所需的 <xref:System.Activities.WorkflowApplication>，以建立 <xref:System.Activities.WorkflowIdentity>。 這個 <xref:System.Activities.WorkflowIdentity> 可能不同於用於保存原始工作流程者，而且通常是為了反映出此持續性的個體已經過修改。 建立 <xref:System.Activities.WorkflowApplication> 之後，會使用 <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> 的多載 (採用 <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>) 載入，然後呼叫 <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType> 來進行卸載。 這樣可以套用動態更新並保存更新過的工作流程執行個體。  
  
```csharp  
// Load the serialized update map.  
DynamicUpdateMap map;  
using (FileStream fs = File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Open))  
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
  
### <a name="resuming-an-updated-workflow-instance"></a>繼續更新的工作流程執行個體  
 套用動態更新之後，即可繼續該工作流程執行個體。 請注意，必須使用更新過的新定義和 <xref:System.Activities.WorkflowIdentity>。  
  
> [!NOTE]
>  如需使用詳細資訊<xref:System.Activities.WorkflowApplication>並<xref:System.Activities.WorkflowIdentity>，請參閱[使用 WorkflowIdentity 與版本控制](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md)。  
  
 在下列範例中，上一個範例中的 `MortgageWorkflow_v1.1.xaml` 工作流程已編譯完畢，並且已使用更新過的工作流程定義載入及繼續。  
  
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
>  若要下載本主題相關的範例程式碼，請參閱[動態更新範例程式碼](https://go.microsoft.com/fwlink/?LinkId=227905)。
