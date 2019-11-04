---
title: HOW TO：啟用工作流程與工作流程服務的持續性
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 5d0eeb8ad40f2f4f3349ab48487316014a561a1b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460887"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>HOW TO：啟用工作流程與工作流程服務的持續性

本主題描述如何啟用工作流程與工作流程服務的持續性。

## <a name="enable-persistence-for-workflows"></a>啟用工作流程的持續性

您可以使用 <xref:System.Activities.WorkflowApplication> 類別的 <xref:System.Activities.WorkflowApplication.InstanceStore%2A> 屬性，將實例存放區與**WorkflowApplication**產生關聯。 <xref:System.Activities.WorkflowApplication.Persist%2A> 方法會將工作流程儲存或保存在與應用程式相關的執行個體存放區中。 <xref:System.Activities.WorkflowApplication.Unload%2A> 方法會將工作流程保存在執行個體存放區中，然後從記憶體卸載該執行個體。 **Load**方法會使用儲存在實例持續性存放區中的工作流程資料，將工作流程載入記憶體中。

**保存**方法會執行下列步驟：

1. 暫停工作流程排程器，直到工作流程進入閒置狀態為止。

2. 將工作流程保存或儲存在持續性存放區中。

3. 恢復工作流程排程器。

 **Unload**方法會執行下列步驟：

1. 暫停工作流程排程器，直到工作流程進入閒置狀態為止。

2. 將工作流程保存或儲存在持續性存放區中。

3. 處置記憶體中的工作流程執行個體。

當工作流程在不保存區域中時，**保存** **和卸載**方法都會遭到封鎖，直到工作流程離開不保存區域為止。 不保存區完成後，此方法會繼續進行保存或卸載作業。 如果不保存區未在逾時時間過去前完成，或者持續性處理序所花的時間過長，就會擲回 TimeoutException。

## <a name="enable-persistence-for-workflow-services-in-code"></a>在程式碼中啟用工作流程服務的持續性

<xref:System.ServiceModel.WorkflowServiceHost> 類別的**DurableInstancingOptions**成員具有名為**InstanceStore**的屬性，可讓您用來建立實例存放區與**WorkflowServiceHost**的關聯。

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

當**WorkflowServiceHost**開啟時，如果**DurableInstancingOptions**不是 null，就會自動啟用持續性。

一般而言，服務行為會提供具象實例存放區，以搭配使用**InstanceStore**屬性與工作流程服務主機。 例如，SqlWorkflowInstanceStoreBehavior 會建立**SqlWorkflowInstanceStore**的實例、設定它，並將它指派給**DurableInstancingOptions**。

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>使用應用程式組態檔啟用工作流程服務的持續性

在 app.config 或 web.config 檔案中加入下列程式碼，即可使用應用程式組態檔啟用持續性：

```xml
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="myBehavior">
          <sqlWorkflowInstanceStore connectionString="Data Source=myDatabaseServer;Initial Catalog=myPersistenceDatabase" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```
