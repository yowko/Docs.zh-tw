---
title: "HOW TO：建立自訂非持續性參與者"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ebc83f100b4303b73ba2e6d3dc41d0f82e8f2c22
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-persistence-participant"></a>HOW TO：建立自訂非持續性參與者
下列程序包含建立持續性參與者的步驟。 請參閱[參與持續性](http://go.microsoft.com/fwlink/?LinkID=177735)範例和[存放區擴充性](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)的持續性參與者的範例實作的主題。  
  
1.  建立從 <xref:System.Activities.Persistence.PersistenceParticipant> 或 <xref:System.Activities.Persistence.PersistenceIOParticipant> 類別衍生的類別。 除了能夠參與 IO 作業外，PersistenceIOParticipant 類別與 PersistenceParticipant 類別提供相同的擴充點。 請依照下列其中一個或多個步驟進行。  
  
2.  實作 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 方法。 **CollectValues**方法有兩個字典參數，一個用於儲存讀取/寫入值，另一個則用於儲存唯寫值 （稍後用於查詢中）。 在這個方法中，您應在這些字典內填入持續性參與者專屬的資料。 每個字典均包含值的名稱做為索引鍵，而值的本身則做為 <xref:System.Runtime.DurableInstancing.InstanceValue> 物件。  
  
     ReadWriteValues 字典中的值會封裝為**InstanceValue**物件。 唯寫字典中的值會封裝為**InstanceValue** InstanceValueOptions.Optional 及 InstanceValueOption.WriteOnly 的集合物件。 每個**InstanceValue**提供**CollectValues**跨所有持續性參與者實作必須有唯一的名稱。  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3.  實作 <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 方法。 **MapValues**方法採用兩個類似的參數的參數， **CollectValues**方法會接收。 在收集到的所有值**CollectValues**階段都會透過這些字典參數傳遞。 所加入的新值**MapValues**階段會加入到唯寫值。  唯寫字典可用來提供資料給與執行個體值沒有直接關聯性的外部資源。 實作所提供的每個值**MapValues**跨所有持續性參與者的方法必須有唯一的名稱。  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 方法提供 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 不提供的功能，可允許與另一個尚未經 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 處理過的持續性參與者所提供的值產生相依性。  
  
4.  實作**PublishValues**方法。 **PublishValues**方法會接收字典，其中包含從持續性存放區載入的所有值。  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5.  實作**BeginOnSave**方法如果參與者是持續性 IO 參與者。 系統會在儲存作業期間呼叫這個方法。 在這個方法中，您應執行附屬於持續性 (儲存中) 工作流程執行個體的 IO。  如果主機使用對應持續性命令的交易，則同樣的交易會在 Transaction.Current 中提供。  此外，PersistenceIOParticipants 可能會通告異動一致性需求，此時，主機會為持續性時段建立異動 (如果未使用任何異動)。  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  實作**BeginOnLoad**方法如果參與者是持續性 IO 參與者。 系統會在載入作業期間呼叫這個方法。 在這個方法中，您應執行附屬於工作流程執行個體載入作業的 IO。 如果主機使用對應持續性命令的交易，則同樣的交易會在 Transaction.Current 中提供。 此外，PersistenceIO 參與者可能會通告交易一致性需求，此時，主機會為持續性時段建立交易 (如果未使用任何交易)。  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
