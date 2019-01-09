---
title: '&lt;commonParameters&gt;'
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: d16807d9faae427d8c22aafc1e1f4f04e5cb13b7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149458"
---
# <a name="ltcommonparametersgt"></a>&lt;commonParameters&gt;
代表參數集合，這些參數可跨多項服務全域使用。 這個集合通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。  
  
 \<system.ServiceModel>  
\<行為 >  
\<serviceBehaviors>  
\<行為 >  
\<workflowRuntime>  
\<commonParameters>  
  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|將服務所使用的一般名稱/值組參數加入至集合。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<workflowRuntime>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|指定的執行個體設定<xref:System.Workflow.Runtime.WorkflowRuntime>用於裝載工作流程為基礎的 Windows Communication Foundation (WCF) 服務。|  
  
## <a name="remarks"></a>備註  
 `<commonParameters>` 項目定義全球多種服務間使用的所有參數，例如在使用 `ConnectionString` 時的 <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>。  
  
> [!NOTE]
>  如果 `ConnectionString` 區段中指定了 SQL 追蹤服務，則此 SQL 追蹤服務就不會統一使用 `<commonParameters>` 值。 這項服務的某些作業 (例如擷取 `StateMachineWorkflowInstance.StateHistory` 屬性 (Property)) 可能會失敗。 若要解決這個問題，請在組態區段中指定追蹤提供者的 `ConnectionString` 屬性 (Attribute)，如下列範例所示。  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
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
  
 請注意，`EnableRetries`參數可以設定在全域層級 (如中所示*CommonParameters*一節) 或針對個別支援的服務`EnableRetries`(如中所示*Services*一節)。  
  
 下列範例程式碼會示範如何以程式設計方式變更常見的參數。  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 如需使用組態檔來控制行為的詳細資訊<xref:System.Workflow.Runtime.WorkflowRuntime>物件的 Windows Workflow Foundation 主應用程式，請參閱[工作流程組態檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))。  
  
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
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 [工作流程組態檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)
