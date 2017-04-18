---
title: "HOW TO：建立自訂非持續性參與者 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# HOW TO：建立自訂非持續性參與者
下列程序包含建立持續性參與者的步驟。如需持續性參與者的實作範例，請參閱[參與持續性](http://go.microsoft.com/fwlink/?LinkID=177735) \(英文\) 範例與[存放區擴充性](../../../docs/framework/windows-workflow-foundation//store-extensibility.md)主題。  
  
1.  建立從 <xref:System.Activities.Persistence.PersistenceParticipant> 或 <xref:System.Activities.Persistence.PersistenceIOParticipant> 類別衍生的類別。除了能夠參與 IO 作業外，PersistenceIOParticipant 類別與 PersistenceParticipant 類別提供相同的擴充點。請依照下列其中一個或多個步驟進行。  
  
2.  實作 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 方法。**CollectValues** 方法具有兩個字典參數，一個用於儲存讀取\/寫入值，另一個則用於儲存唯寫值 \(稍後用於查詢中\)。在這個方法中，您應在這些字典內填入持續性參與者專屬的資料。每個字典均包含值的名稱做為索引鍵，而值的本身則做為 <xref:System.Runtime.DurableInstancing.InstanceValue> 物件。  
  
     readWriteValues 字典中的值會封裝為 **InstanceValue** 物件。唯寫字典中的值會封裝為設定了 InstanceValueOptions.Optional 及 InstanceValueOption.WriteOnly 的 **InstanceValue** 物件。跨所有持續性參與者的 **CollectValues** 實作所提供的每個 **InstanceValue** 都必須具有唯一的名稱。  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
  
    ```  
  
3.  實作 <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 方法。**MapValues** 方法會採用兩個參數，這兩個參數類似於 **CollectValues** 方法所接收的參數。在 **CollectValues** 階段收集到的所有值都會透過這些字典參數傳遞。**MapValues** 階段所加入的新值會加入至唯讀值中。唯寫字典用於提供資料給與執行個體值資料之間不具關聯性的外部資源。跨所有持續性參與者的 **MapValues** 方法實作所提供的每個值都必須具有唯一的名稱。  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 方法提供 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 不提供的功能，可允許與另一個尚未經 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 處理過的持續性參與者所提供的值產生相依性。  
  
4.  實作 **PublishValues** 方法。**PublishValues** 方法會接收字典，該字典包含從持續性存放區載入的所有值。  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
  
    ```  
  
5.  如果參與者是持續性 IO 參與者，請實作 **BeginOnSave** 方法。系統會在儲存作業期間呼叫這個方法。在這個方法中，您應執行附屬於持續性 \(儲存中\) 工作流程執行個體的 IO。如果主機使用對應持續性命令的交易，則同樣的交易會在 Transaction.Current 中提供。此外，PersistenceIOParticipants 可能會通告交易一致性需求，此時，主機會為持續性時段建立交易 \(如果未使用任何交易\)。  
  
    ```  
  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  如果參與者是持續性 IO 參與者，請實作 **BeginOnLoad** 方法。系統會在載入作業期間呼叫這個方法。在這個方法中，您應執行附屬於工作流程執行個體載入作業的 IO。如果主機使用對應持續性命令的交易，則同樣的交易會在 Transaction.Current 中提供。此外，PersistenceIO 參與者可能會通告交易一致性需求，此時，主機會為持續性時段建立交易 \(如果未使用任何交易\)。  
  
    ```  
  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
  
    ```