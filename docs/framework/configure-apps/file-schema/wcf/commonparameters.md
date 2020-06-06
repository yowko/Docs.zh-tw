---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 73d8549f68e8ca77115619431c857c4a2aac3fdf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153018"
---
# \<commonParameters>
代表參數集合，這些參數可跨多項服務全域使用。 這個集合通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<add>](add-of-commonparameters.md)|將服務所使用的一般名稱/值組參數加入至集合。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<workflowRuntime>](workflowruntime.md)|<xref:System.Workflow.Runtime.WorkflowRuntime>針對裝載以工作流程為基礎的 Windows Communication Foundation （WCF）服務，指定實例的設定。|  
  
## <a name="remarks"></a>備註  
 `<commonParameters>` 項目定義全球多種服務間使用的所有參數，例如在使用 `ConnectionString` 時的 <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>。  
  
> [!NOTE]
> 如果 `ConnectionString` 區段中指定了 SQL 追蹤服務，則此 SQL 追蹤服務就不會統一使用 `<commonParameters>` 值。 這項服務的某些作業 (例如擷取 `StateMachineWorkflowInstance.StateHistory` 屬性 (Property)) 可能會失敗。 若要解決這個問題，請在組態區段中指定追蹤提供者的 `ConnectionString` 屬性 (Attribute)，如下列範例所示。  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 針對認可工作批次持續儲存的服務 (例如 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> 及 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>)，您可以使用 `EnableRetries` 參數允許它們重試交易，如下列範例所示：  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime,
               Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 請注意，您 `EnableRetries` 可以在全域層級（如*CommonParameters*一節所示），或針對支援的個別服務 `EnableRetries` （如 [*服務*] 區段中所示）設定參數。  
  
 下列範例程式碼示範如何以程式設計方式變更一般參數：
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 如需使用設定檔控制 <xref:System.Workflow.Runtime.WorkflowRuntime> Windows Workflow Foundation 主應用程式之物件行為的詳細資訊，請參閱[工作流程設定檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))。  
  
## <a name="example"></a>範例  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- [工作流程組態檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
- [\<add>](add-of-commonparameters.md)
