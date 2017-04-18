---
title: "&lt;commonParameters&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;commonParameters&gt;
代表參數集合，這些參數可跨多項服務全域使用。  這個集合通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。  
  
## 語法  
  
```  
  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|將服務所使用的一般名稱\/值組參數加入至集合。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<workflowRuntime\>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|指定 <xref:System.Workflow.Runtime.WorkflowRuntime> 之執行個體的設定，以裝載工作流程架構的 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務。|  
  
## 備註  
 `<commonParameters>` 項目定義全球多種服務間使用的所有參數，例如在使用 <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService> 時的 `ConnectionString`。  
  
> [!NOTE]
>  如果 `<commonParameters>` 區段中指定了 SQL 追蹤服務，則此 SQL 追蹤服務就不會統一使用 `ConnectionString` 值。  這項服務的某些作業 \(例如擷取 `StateMachineWorkflowInstance.StateHistory` 屬性 \(Property\)\) 可能會失敗。  若要解決這個問題，請在組態區段中指定追蹤提供者的 `ConnectionString` 屬性 \(Attribute\)，如下列範例所示。  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 針對認可工作批次持續儲存的服務 \(例如 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> 及 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>\)，您可以使用 `EnableRetries` 參數允許它們重試交易，如下列範例所示：  
  
```  
<WorkflowRuntime Name="SampleApplication" UnloadOnIdle="false">  
    <commonParameters>  
        <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
        <add name="EnableRetries" value="True" />  
    </commonParameters>  
    <Services>  
        <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" EnableRetries="False" />   
     </Services>  
</WorkflowRuntime>  
```  
  
 請注意，您可以在全域層級設定 `EnableRetries` 參數 \(如 *CommonParameters* 區段所示\)，或針對支援 `EnableRetries` 的個別服務加以設定 \(如 *Services* 區段所示\)。  
  
 下列範例程式碼會示範如何以程式設計方式變更常見的參數。  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 如需使用組態檔控制 Windows Workflow Foundation 主應用程式之 <xref:System.Workflow.Runtime.WorkflowRuntime> 物件行為的詳細資訊，請參閱[Workflow Configuration Files](http://msdn.microsoft.com/zh-tw/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)。  
  
## 範例  
  
```  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>   
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>   
 <xref:System.Workflow.Runtime.WorkflowRuntime>   
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>   
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>   
 [Workflow Configuration Files](http://msdn.microsoft.com/zh-tw/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)   
 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)