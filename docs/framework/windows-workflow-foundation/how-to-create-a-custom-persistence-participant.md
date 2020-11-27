---
title: 作法：建立自訂持續性參與者
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: 633961ac12eed593613eba75862cbc81f2fa68c6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275810"
---
# <a name="how-to-create-a-custom-persistence-participant"></a>作法：建立自訂持續性參與者

下列程序包含建立持續性參與者的步驟。 如需持續性參與者的範例執行，請參閱 [參與持續](/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100)) 性範例和 [儲存](store-extensibility.md) 擴充性主題。  
  
1. 建立從 <xref:System.Activities.Persistence.PersistenceParticipant> 或 <xref:System.Activities.Persistence.PersistenceIOParticipant> 類別衍生的類別。 PersistenceIOParticipant 類別除了能夠參與 i/o 作業之外，還提供與 PersistenceParticipant 類別相同的擴充點。 請依照下列其中一個或多個步驟進行。  
  
2. 實作 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 方法。 **CollectValues** 方法有兩個字典參數，一個用於儲存讀取/寫入值，另一個用於儲存僅限寫入值 (稍後在查詢) 中使用。 在這個方法中，您應在這些字典內填入持續性參與者專屬的資料。 每個字典均包含值的名稱做為索引鍵，而值的本身則做為 <xref:System.Runtime.DurableInstancing.InstanceValue> 物件。  
  
    ReadWriteValues 字典中的值會封裝為 **InstanceValue** 物件。 僅限寫入字典中的值會封裝為具有 InstanceValueOptions 的 **InstanceValue** 物件，並設定 InstanceValueOption. WriteOnly。 跨所有持續性參與者的 **CollectValues** 執行所提供的每個 **InstanceValue** 都必須有唯一的名稱。
  
    ```csharp  
    protected virtual void CollectValues(out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
3. 實作 <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 方法。 **MapValues** 方法會採用兩個類似于 **CollectValues** 方法所接收之參數的參數。 **CollectValues** 階段中收集到的所有值都會透過這些字典參數傳遞。 **MapValues** 階段加入的新值會加入至僅限寫入的值。  唯寫字典可用來提供資料給與執行個體值沒有直接關聯性的外部資源。 跨所有持續性參與者的 **MapValues** 方法執行所提供的每個值都必須有唯一的名稱。  
  
    ```csharp  
    protected virtual IDictionary<XName,Object> MapValues(IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
     <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 方法提供 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 不提供的功能，可允許與另一個尚未經 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 處理過的持續性參與者所提供的值產生相依性。  
  
4. 執行 **PublishValues** 方法。 **PublishValues** 方法會接收包含從持續性存放區載入之所有值的字典。  
  
    ```csharp  
    protected virtual void PublishValues(IDictionary<XName,Object> readWriteValues)
    {
    }
    ```  
  
5. 如果參與者是持續性 i/o 參與者，請執行 **BeginOnSave** 方法。 系統會在儲存作業期間呼叫這個方法。 在這個方法中，您應該執行與保存 (儲存) 工作流程實例的 i/o 附屬。  如果主機使用對應持續性命令的異動，則同樣的異動會在 Transaction.Current 中提供。  此外，PersistenceIOParticipants 可能會通告交易一致性需求，此時，主機會為持續性時段建立交易 (如果未使用任何交易)。  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnSave(IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```  
  
6. 如果參與者是持續性 i/o 參與者，請執行 **BeginOnLoad** 方法。 系統會在載入作業期間呼叫這個方法。 在這個方法中，您應該執行附屬於工作流程實例載入的 i/o。 如果主機使用對應持續性命令的異動，則同樣的異動會在 Transaction.Current 中提供。 此外，持續性的 i/o 參與者可能會通告交易一致性需求，在這種情況下，主機會為持續性集建立交易（如果沒有其他用途的話）。  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnLoad(IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```
