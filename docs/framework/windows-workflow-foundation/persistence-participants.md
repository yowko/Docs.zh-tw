---
title: 持續性參與者
ms.date: 03/30/2017
ms.assetid: f84d2d5d-1c1b-4f19-be45-65b552d3e9e3
ms.openlocfilehash: 0bff6cc8fafb1832dc4d0e33b754fe3adb81dcf6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246104"
---
# <a name="persistence-participants"></a>持續性參與者

持續性參與者可參與由應用程式主機所觸發的持續性作業 (「儲存」或「載入」)。 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]隨附了兩個抽象類別： **PersistenceParticipant** 和 **PersistenceIOParticipant**，可讓您用來建立持續性參與者。 持續性參與者會衍生自這些類別的其中一個、實作感興趣的方法，然後將類別的執行個體加入至 <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> 上的 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 集合。 應用程式主機保存工作流程執行個體時，可能會尋找此類工作流程擴充功能，並且在適當的時間於持續性參與者上叫用適當的方法。  
  
 以下清單描述持續性子系統在不同階段的「保存」(儲存) 作業時所執行的工作。 持續性參與者會用於第三與第四階段。 如果參與者是 i/o 參與者 (同時參與 i/o 作業) 的持續性參與者，則在第六個階段也會使用參與者。  
  
1. 收集內建值，包含工作流程狀態、書籤、對應的變數以及時間戳記。  
  
2. 收集加入至與工作流程執行個體相關之擴充集合的所有持續性參與者。  
  
3. 叫用由所有持續性參與者實作的 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 方法。  
  
4. 叫用由所有持續性參與者實作的 <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 方法。  
  
5. 保存工作流程，或將工作流程儲存至持續性存放區中。  
  
6. <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnSave%2A>在所有持續性 i/o 參與者上叫用方法。 如果參與者不是 i/o 參與者，則會略過此工作。 如果持續性的時段屬於交易性質，則交易會在 Transaction.Current 屬性中提供。  
  
7. 等候所有持續性參與者完成。 如果所有參與者成功保存執行個體資料，則認可異動。  
  
 持續性參與者衍生自 **PersistenceParticipant** 類別，而且可能會執行 **CollectValues** 和 **MapValues** 方法。 持續性 i/o 參與者衍生自 **PersistenceIOParticipant** 類別，而且除了執行 **CollectValues** 和 **MapValues** 方法之外，還可以執行 **BeginOnSave** 方法。  
  
 每個階段都會先完成，再開始進行下一個階段。 例如，系統會從第一個階段中的 **所有** 持續性參與者收集值。 然後，會將在第一階段中收集到的所有值提供給第二階段中的所有持續性參與者，以進行對應。 接著，會將在第一和第二階段中收集到的所有值提供給第三階段中的所有持續性參與者，以進行對應，依此類推。  
  
 以下清單描述持續性子系統在不同階段的「載入」作業時所執行的工作。 持續性參與者會用於第四階段。 也會在第三個階段中使用持續性的 i/o 參與者 (持續性參與者，也會參與 i/o 作業) 。  
  
1. 收集加入至與工作流程執行個體相關之擴充集合的所有持續性參與者。  
  
2. 自持續性存放區載入工作流程。  
  
3. <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnLoad%2A>在所有持續性 i/o 參與者上叫用，並等候所有持續性參與者完成。 如果持續性的時段屬於異動性質，則異動會在 Transaction.Current 中提供。  
  
4. 根據從持續性存放區所擷取的資料，載入記憶體中的工作流程執行個體。  
  
5. 叫用每個持續性參與者上的 <xref:System.Activities.Persistence.PersistenceParticipant.PublishValues%2A>。  
  
 持續性參與者衍生自 **PersistenceParticipant** 類別，而且可能會執行 **PublishValues** 方法。 持續性 i/o 參與者衍生自 **PersistenceIOParticipant** 類別，而且除了執行 **PublishValues** 方法之外，還可以執行 **BeginOnLoad** 方法。  
  
 載入工作流程執行個體時，持續性提供者會建立該執行個體的鎖定。 這可防止在多節點的案例中，多個主機載入執行個體。 如果您試圖載入已鎖定的工作流程執行個體，您將看到像下列的例外狀況：例外狀況 "System.ServiceModel.Persistence.InstanceLockException: 無法完成要求的作業，因為無法取得執行個體 '00000000-0000-0000-0000-000000000000' 的鎖定"。 當下列任一情形發生時，就會發生這個錯誤：  
  
- 在多節點的案例中，執行個體是由另一個主機載入。  有幾個不同的方法來解決這些類型的衝突：將處理轉送到擁有鎖定的節點然後重試，或是強制載入，這會導致其他主機無法儲存它們的工作。  
  
- 在單一節點的案例中且主機毀損。  當主機再次啟動時 (處理序回收或建立新的持續性提供者處理站)，新主機嘗試載入執行個體，但此執行個體仍被舊主機鎖定，因為鎖定尚未到期。  
  
- 在單一節點的案例中，出現問題的執行個體已在某個時間點中止，新的持續性提供者執行個體已建立，其具有不同的主機 ID。  
  
 鎖定逾時值預設為 5 分鐘，您可以在呼叫 <xref:System.ServiceModel.Persistence.PersistenceProvider.Load%2A> 時指定不同的逾時值。  
  
## <a name="in-this-section"></a>本節內容  
  
- [作法：建立自訂持續性參與者](how-to-create-a-custom-persistence-participant.md)  
  
## <a name="see-also"></a>另請參閱

- [存放區擴充性](store-extensibility.md)
