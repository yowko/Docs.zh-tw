---
title: WorkflowServiceHost 中的並存版本控制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: 3ac8b2260e5da1e91c167e3e9ef91039deb983b2
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380237"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a>WorkflowServiceHost 中的並存版本控制
<xref:System.ServiceModel.Activities.WorkflowServiceHost> .NET Framework 4.5 中引進的並排顯示版本控制提供裝載在單一端點上的工作流程服務的多個版本的功能。 提供的並存功能可讓工作流程服務進行設定，以便工作流程服務的新執行個體是使用新的工作流程定義所建立，而執行中的執行個體則是使用現有的定義完成。 本主題提供使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 並存執行工作流程服務的概觀。  
  
> [!NOTE]
>  若要下載的範例，並觀看影片逐步解說的工作流程服務的並存版本控制，請參閱[web 託管之 Xamlx 工作流程服務並存版本控制](https://go.microsoft.com/fwlink/?LinkId=393746)。  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>在工作流程服務中裝載多個版本  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 包含兩個可設定為讓多個工作流程版本能夠並存執行的屬性：<xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> 和 <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>。 <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> 包含受支援的工作流程服務版本，而 <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> 可用來唯一識別每個工作流程服務。 將 <xref:System.Activities.WorkflowIdentity> 與工作流程服務產生關聯，即可達到這個目的。 <xref:System.Activities.WorkflowIdentity> 包含三項識別資訊。 <xref:System.Activities.WorkflowIdentity.Name%2A> 和 <xref:System.Activities.WorkflowIdentity.Version%2A> 包含名稱及 <xref:System.Version>，兩者都是必要項，而 <xref:System.Activities.WorkflowIdentity.Package%2A> 則是選用項，可用來指定包含資訊 (例如組件名稱或其他所需資訊) 的其他字串。 <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> 集合中所包含的每個工作流程服務都必須具有唯一的 <xref:System.Activities.WorkflowIdentity>。 如果 <xref:System.Activities.WorkflowIdentity> 的三個屬性中有任何屬性與另一個 <xref:System.Activities.WorkflowIdentity> 的不同，則其為唯一識別。 A `null` <xref:System.Activities.WorkflowIdentity>可允許的值，如<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>，但只有一個舊版工作流程服務可能`null` <xref:System.Activities.WorkflowIdentity>。  
  
> [!IMPORTANT]
>  <xref:System.Activities.WorkflowIdentity> 不應包含任何個人可識別資訊 (PII)。 <xref:System.Activities.WorkflowIdentity> 包含三個部分：<xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>)、<xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) 和 <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>)。 執行階段會在數個不同的活動生命週期點，將有關<xref:System.Activities.WorkflowIdentity> (用來建立執行個體) 的資訊發出到任何已設定的追蹤服務。 WF 追蹤沒有任何機制可隱藏 PII (機密的使用者資料)。 因此，<xref:System.Activities.WorkflowIdentity> 執行個體不應包含任何 PII 資料，因為執行階段會在追蹤記錄中發出這項資訊，因此存取檢視追蹤記錄的人有可能看見這項資訊。  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>裝載多個工作流服務版本的規則  
 當使用者將其他版本加入至 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 時，必須符合幾個條件，才能使用一組相同的端點和描述來裝載工作流程服務。 如果有任何其他版本未能滿足這些條件，在呼叫 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 時，`Open` 會擲回例外狀況。 提供給主機做為其他版本的各項工作流程定義必須滿足下列需求 (其中主要版本是提供給主機建構函式的工作流程服務定義)。 其他工作流程版本必須：  
  
- 具有與工作流程服務主要版本相同的 <xref:System.ServiceModel.Activities.WorkflowService.Name%2A>。  
  
- 在其 <xref:System.ServiceModel.Activities.Receive> 中，不得包含任何不在主要版本中的 <xref:System.ServiceModel.Activities.SendReply> 或 <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> 活動，而且這些活動必須符合作業合約。  
  
- 具有唯一的 <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>。 一個 (且僅限一個) 工作流程定義可以有 `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>。  
  
 允許部分變更。 版本之間的下列項目可能不同：  
  
- <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> 的名稱和封裝可能不同於主要版本。  
  
- <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 值可能和主要版本不同。  
  
- <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> 可能和主要版本不同。  
  
- <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> 可能和主要版本不同。  
  
### <a name="configuring-the-definitionidentity"></a>設定 DefinitionIdentity  
 使用工作流程設計工具中，建立工作流程服務時<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>會使用來設定**屬性**視窗。 按一下 選取工作流程服務，然後選擇 設計工具中的服務的根活動以外**屬性 視窗**從**檢視**功能表。 選取  **WorkflowIdentity**從下拉式清單旁邊會出現**DefinitionIdentity**屬性，然後展開並指定所需<xref:System.Activities.WorkflowIdentity>屬性。 在下列範例中<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>設有<xref:System.Activities.WorkflowIdentity.Name%2A>`MortgageWorkflow`並<xref:System.Activities.WorkflowIdentity.Version%2A>的`1.0.0.0`。 <xref:System.Activities.WorkflowIdentity.Package%2A> 是選擇項，在這個範例中為 `null`。  
  
 ![如果螢幕擷取畫面顯示 DefinitionIdentity 屬性。](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 當工作流程服務是自我裝載的服務時，<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> 會在工作流程服務建構期間進行設定。 在下列範例中，<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>已使用上述範例中，相同的值與<xref:System.Activities.WorkflowIdentity.Name%2A>`MortgageWorkflow`並<xref:System.Activities.WorkflowIdentity.Name%2A>的`1.0.0.0`。  
  
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
  
 A<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>不必要的但只有一個工作流程服務版本可以有**null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>。  
  
> [!NOTE]
>  如果服務在最初部署中沒有設定 <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>，而又建立更新版本，那麼這種做法會很有用。  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>將新版本加入至 Web 主控工作流程服務  
 在 Web 主控服務中設定新版工作流程服務的第一步，就是在 `App_Code` 資料夾中建立與服務檔同名的新資料夾。 如果服務的 `xamlx` 檔案命名為 `MortgageWorkflow.xamlx`，該資料夾也必須命名為 `MortgageWorkflow`。 將原始服務的 `xamlx` 檔案複本放在這個資料夾中，並重新命名為新的名稱，例如 `MortgageWorkflowV1.xamlx`。 對主要服務進行所需的變更，更新其 <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>，然後部署服務。 在下列範例中，<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> 已經以 <xref:System.Activities.WorkflowIdentity.Name%2A> 的 `MortageWorkflow` 和 <xref:System.Activities.WorkflowIdentity.Version%2A> 的 `2.0.0.0` 進行更新。  
  
 ![如果螢幕擷取畫面顯示 DefinitionIdentity 的 WorkflowIdentity。](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 當服務重新啟動時，舊版本會自動加入至 <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> 集合，因為其位於指定的 `App_Code` 子資料夾中。 請注意，如果工作流程服務的主要版本具有`null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>將不會加入先前的版本。 一個版本可以有 `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>，但如果有多個版本，則主要版本不可以是具有 `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> 的版本，否則舊版本都不會加入至 <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> 集合。  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>將新版本加入至自我裝載工作流程服務  
 將新版本加入至自我裝載工作流程服務時，<xref:System.ServiceModel.Activities.WorkflowServiceHost> 會使用工作流程服務的主要版本進行設定，而舊的版本必須明確加入至 <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> 集合。 在下列範例中，<xref:System.ServiceModel.Activities.WorkflowServiceHost> 會透過使用 `MortgageWorkflowV2` 工作流程定義的主要工作流程服務進行設定，而使用 `MortgageWorkflowV1` 工作流程定義所設定的工作流程服務會加入至 <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> 集合。 每個工作流程服務都會透過反映工作流程定義版本的唯一 <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> 來進行設定。  
  
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
