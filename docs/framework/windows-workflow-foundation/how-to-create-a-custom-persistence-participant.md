---
title: HOW TO：建立自訂非持續性參與者
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: 8daf4924db48c79486e85660357e3b28a2583836
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855838"
---
# <a name="how-to-create-a-custom-persistence-participant"></a>HOW TO：建立自訂非持續性參與者
下列程序包含建立持續性參與者的步驟。 請參閱[參與持續性](https://go.microsoft.com/fwlink/?LinkID=177735)範例並[存放區擴充性](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)持續性參與者的實作範例的主題。  
  
1.  建立從 <xref:System.Activities.Persistence.PersistenceParticipant> 或 <xref:System.Activities.Persistence.PersistenceIOParticipant> 類別衍生的類別。 外，PersistenceIOParticipant 類別會提供相同的擴充點，與 PersistenceParticipant 類別，除了能夠參與 I/O 作業。 請依照下列其中一個或多個步驟進行。  
  
2.  實作 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 方法。 **CollectValues**方法有兩個字典參數，一個用於儲存讀取/寫入值，另一個則用於儲存唯寫值 （稍後在查詢中使用）。 在這個方法中，您應在這些字典內填入持續性參與者專屬的資料。 每個字典均包含值的名稱做為索引鍵，而值的本身則做為 <xref:System.Runtime.DurableInstancing.InstanceValue> 物件。  
  
     ReadWriteValues 字典中的值會封裝為**InstanceValue**物件。 唯寫字典中的值會封裝為**InstanceValue**了 InstanceValueOptions.Optional 及 InstanceValueOption.WriteOnly 的集合物件。 每個**InstanceValue**所提供**CollectValues**跨所有持續性參與者的實作必須有唯一的名稱。  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3.  實作 <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 方法。 **MapValues**方法會採用類似的參數的兩個參數的**CollectValues**方法會接收。 中的所有值都收集**CollectValues**階段會透過這些字典參數傳遞。 所加入的新值**MapValues**階段所加入的唯寫值。  唯寫字典可用來提供資料給與執行個體值沒有直接關聯性的外部資源。 實作所提供的每個值**MapValues**跨所有持續性參與者的方法必須有唯一的名稱。  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 方法提供 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 不提供的功能，可允許與另一個尚未經 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 處理過的持續性參與者所提供的值產生相依性。  
  
4.  實作**PublishValues**方法。 **PublishValues**方法會接收字典，其中包含從持續性存放區載入的所有值。  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5.  實作**BeginOnSave**如果參與者是持續性 I/O 參與者的方法。 系統會在儲存作業期間呼叫這個方法。 在此方法中，您應該執行 I/O 附屬於持續性 （儲存） 工作流程執行個體。  如果主機使用對應持續性命令的異動，則同樣的異動會在 Transaction.Current 中提供。  此外，PersistenceIOParticipants 可能會通告異動一致性需求，此時，主機會為持續性時段建立異動 (如果未使用任何異動)。  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  實作**BeginOnLoad**如果參與者是持續性 I/O 參與者的方法。 系統會在載入作業期間呼叫這個方法。 在此方法中，您應該執行 I/O 的工作流程執行個體載入輔助。 如果主機使用對應持續性命令的異動，則同樣的異動會在 Transaction.Current 中提供。 此外，持續性 I/O 參與者可能會通告異動一致性需求，如果其中一個會不使用建立持續性時段交易的情況下主應用程式。  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
