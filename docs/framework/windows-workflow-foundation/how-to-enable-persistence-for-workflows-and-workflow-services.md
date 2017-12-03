---
title: "HOW TO：啟用工作流程與工作流程服務的持續性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1db45ecad833c4c05ba240569da9c85271e0b69e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>HOW TO：啟用工作流程與工作流程服務的持續性
本主題描述如何啟用工作流程與工作流程服務的持續性。  
  
## <a name="enable-persistence-for-workflows"></a>啟用工作流程的持續性  
 您可以建立關聯的執行個體存放區**WorkflowApplication**使用<xref:System.Activities.WorkflowApplication.InstanceStore%2A>屬性<xref:System.Activities.WorkflowApplication>類別。 <xref:System.Activities.WorkflowApplication.Persist%2A> 方法會將工作流程儲存或保存在與應用程式相關的執行個體存放區中。 <xref:System.Activities.WorkflowApplication.Unload%2A> 方法會將工作流程保存在執行個體存放區中，然後從記憶體卸載該執行個體。 **負載**方法會將工作流程載入到記憶體中使用的執行個體持續性存放區中的工作流程資料。  
  
 **保存**方法會執行下列步驟：  
  
1.  暫停工作流程排程器，直到工作流程進入閒置狀態為止。  
  
2.  將工作流程保存或儲存在持續性存放區中。  
  
3.  恢復工作流程排程器。  
  
 **卸載**方法會執行下列步驟：  
  
1.  暫停工作流程排程器，直到工作流程進入閒置狀態為止。  
  
2.  將工作流程保存或儲存在持續性存放區中。  
  
3.  處置記憶體中的工作流程執行個體。  
  
 這兩個**保存**和**卸載**方法將會封鎖直到工作流程離開不保存區域工作流程是在非保存區域時。 不保存區完成後，此方法會繼續進行保存或卸載作業。 如果不保存區未在逾時時間過去前完成，或者持續性處理序所花的時間過長，就會擲回 TimeoutException。  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a>在程式碼中啟用工作流程服務的持續性  
 **DurableInstancingOptions**隸屬<xref:System.ServiceModel.WorkflowServiceHost>類別具有內容，名為**InstanceStore**可用來建立關聯的執行個體存放區**WorkflowServiceHost**.  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 當**WorkflowServiceHost**已開啟，持續性會自動啟用如果**DurableInstancingOptions.InstanceStore**不是 null。  
  
 一般來說，服務行為會提供具象執行個體存放區搭配使用工作流程服務主機**InstanceStore**屬性。 例如，SqlWorkflowInstanceStoreBehavior 會建立的執行個體**SqlWorkflowInstanceStore**、 加以設定，然後將其指派給**DurableInstancingOptions.InstanceStore**。  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>使用應用程式組態檔啟用工作流程服務的持續性  
 在 app.config 或 web.config 檔案中加入下列程式碼，即可使用應用程式組態檔啟用持續性：  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="myBehavior">  
          <SqlWorkflowInstanceStore connectionString="Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase">  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
```
