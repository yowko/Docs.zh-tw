---
title: "&lt;commonParameters&gt; 的 &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;commonParameters&gt; 的 &lt;add&gt;
指定跨多項服務全域使用之名稱\/值組的參數。  這個參數通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。  
  
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
  
|屬性|描述|  
|--------|--------|  
|name|為服務指定的參數名稱。|  
|value|為服務指定的參數值。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<commonParameters\>](http://msdn.microsoft.com/zh-tw/d0e1e6fc-985a-4713-b7da-194e30dfab4c)|服務所使用的一般參數集合。  這個集合通常會包含資料庫連線字串，這個字串可能會由長期服務所共用。|  
  
## 備註  
 `<commonParameters>` 項目定義全球多種服務間使用的所有參數，例如在使用 <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService> 時的 `ConnectionString`。  
  
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
 [\<commonParameters\>](http://msdn.microsoft.com/zh-tw/d0e1e6fc-985a-4713-b7da-194e30dfab4c)