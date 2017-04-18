---
title: "HOW TO：啟用工作流程與工作流程服務的持續性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HOW TO：啟用工作流程與工作流程服務的持續性
本主題描述如何啟用工作流程與工作流程服務的持續性。  
  
## 啟用工作流程的持續性  
 您可以將執行個體存放區與 **WorkflowApplication**關聯，方法是使用 <xref:System.Activities.WorkflowApplication> 類別的 <xref:System.Activities.WorkflowApplication.InstanceStore%2A> 屬性。<xref:System.Activities.WorkflowApplication.Persist%2A> 方法會將工作流程儲存或保存在與應用程式相關的執行個體存放區中。<xref:System.Activities.WorkflowApplication.Unload%2A> 方法會將工作流程保存在執行個體存放區中，然後從記憶體卸載該執行個體。**Load**方法會使用儲存在執行個體持續性存放區中的工作流程資料，將工作流程載入至記憶體中。  
  
 **Persist** 方法會執行下列步驟：  
  
1.  暫停工作流程排程器，直到工作流程進入閒置狀態為止。  
  
2.  將工作流程保存或儲存在持續性存放區中。  
  
3.  恢復工作流程排程器。  
  
 **Unload** 方法會執行下列步驟：  
  
1.  暫停工作流程排程器，直到工作流程進入閒置狀態為止。  
  
2.  將工作流程保存或儲存在持續性存放區中。  
  
3.  處置記憶體中的工作流程執行個體。  
  
 工作流程位於不保存區時，**Persist** 和 **Unload** 方法都會封鎖，直到該工作流程離開不保存區為止。不保存區完成後，此方法會繼續進行保存或卸載作業。如果不保存區未在逾時時間過去前完成，或者持續性處理序所花的時間過長，就會擲回 TimeoutException。  
  
## 在程式碼中啟用工作流程服務的持續性  
 <xref:System.ServiceModel.WorkflowServiceHost> 類別的 **DurableInstancingOptions** 成員具有名為 **InstanceStore** 的屬性，此屬性可讓您用於關聯具有 **WorkflowServiceHost**的執行個體存放區。  
  
```  
  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
  
```  
  
 開啟 **WorkflowServiceHost** 時，如果 **DurableInstancingOptions.InstanceStore** 不是 Null，就會自動啟用持續性。  
  
 一般來說，服務行為會使用 **InstanceStore** 屬性，提供搭配工作流程服務使用的具體執行個體存放區。例如，SqlWorkflowInstanceStoreBehavior 會建立 **SqlWorkflowInstanceStore** 的執行個體、加以設定，然後予以指派至 **DurableInstancingOptions.InstanceStore**。  
  
## 使用應用程式組態檔啟用工作流程服務的持續性  
 在 app.config 或 web.config 檔案中加入下列程式碼，即可使用應用程式組態檔啟用持續性：  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name=”myBehavior”>  
          <SqlWorkflowInstanceStore connectionString=”Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase”>  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
  
```