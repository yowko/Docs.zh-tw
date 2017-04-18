---
title: "WorkflowHostingEndpoint 的書籤解析程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# WorkflowHostingEndpoint 的書籤解析程式
這個範例示範 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> 如何與 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 搭配使用以建立工作流程執行個體。  
  
## 示範  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>,<xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## 討論  
 這個範例使用 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> 建立使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 裝載的工作流程執行個體。<xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> 是  <xref:System.ServiceModel.Activities.WorkflowServiceHost> 的擴充點，可用於以下情形：  
  
-   建立新的工作流程執行個體。  
  
-   在裝載於 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 的工作流程執行個體中繼續使用書籤。  
  
 包含的範例端點會公開合約，以提供作業來建立工作流程，以及傳回執行個體識別碼或建立具有特定識別碼的執行個體。範例主控台應用程式會建立具有工作流程定義的 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 執行個體，並將 `CreationEndpoint` 加入至主機。接著會在端點上呼叫 `Create` 作業，以建立新的工作流程執行個體。  
  
#### 若要安裝、建置及執行範例  
  
1.  建置方案。  
  
2.  執行應用程式。建立工作流程執行個體之後，`CreationEndpoint` 主控台會顯示包含執行個體識別碼的訊息。工作流程執行個體會列印 "Hello World\!" 訊息。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`