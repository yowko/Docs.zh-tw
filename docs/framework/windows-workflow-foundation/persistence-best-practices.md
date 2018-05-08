---
title: 持續性的最佳作法
ms.date: 03/30/2017
ms.assetid: 6974c5a4-1af8-4732-ab53-7d694608a3a0
ms.openlocfilehash: 68164cc937c1c718df39c96c3d6ac490ab025fae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="persistence-best-practices"></a>持續性的最佳作法
本文件包含與工作流程持續性相關之工作流程設計與組態的最佳作法。  
  
## <a name="design-and-implementation-of-durable-workflows"></a>設計及實作永久性工作流程  
 一般來說，工作流程會在時間交錯的短期內工作，因為工作流程在這段期間內正在等候事件，所以會處於閒置狀態。 這個事件可以是訊息或到期計時器等項目。 為了要能夠在工作流程執行個體閒置時將它卸載，服務主機必須保存工作流程執行個體。 只有當工作流程執行個體不在非保存區域時才可行 (例如，正在等候交易完成或等候非同步回呼)。 若要允許卸載閒置的工作流程執行個體，工作流程作者應該只針對短期的動作使用交易範圍和非同步活動。 特別是，作者應該將這些非保存區域中的延遲活動盡量縮短。  
  
 只有當工作流程所使用的所有資料型別都可序列化時，才能保存工作流程。 此外，保存之工作流程中所使用的自訂型別必須可以使用 <xref:System.Runtime.Serialization.NetDataContractSerializer> 來序列化，才能由 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 保存。  
  
 萬一主機或電腦故障，如果工作流程執行個體尚未保存就無法復原。 一般來說，我們建議您在工作流程生命週期的早期保存工作流程執行個體。  
  
 如果您的工作流程會忙碌一段很長的時間，我們建議您在整段忙碌期間定期保存工作流程執行個體。 若要這樣做，請在維持工作流程執行個體忙碌的整個活動序列中加入 <xref:System.Activities.Statements.Persist> 活動。 如此一來，應用程式定義域回收、主機故障或電腦故障就不會造成系統必須回復到忙碌期間的開頭。 請注意，將 <xref:System.Activities.Statements.Persist> 活動加入至您的工作流程可能會造成效能的降低。  
  
 Windows Server App Fabric 會大幅簡化持續性的組態與使用。 如需詳細資訊，請參閱[Windows Server App Fabric 持續性](http://go.microsoft.com/fwlink/?LinkID=201200&clcid=0x409)  
  
## <a name="configuration-of-scalability-parameters"></a>延展性參數的組態  
 延展性和效能需求會決定以下參數的設定：  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>  
  
-   <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A>  
  
 這些參數應該根據目前的情況，依照以下方式設定。  
  
### <a name="scenario-a-small-number-of-workflow-instances-that-require-optimal-response-time"></a>案例：需要最佳回應時間的少量工作流程執行個體  
 在此案例中，當所有工作流程執行個體閒置時，都應該維持已載入的狀態。 請將 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 設定為大的值。 使用這項設定會防止工作流程執行個體在電腦之間移動。 只有當下列其中一個或多個條件成立時，才能使用這項設定：  
  
-   工作流程執行個體在它的整個存留期都會收到單一訊息。  
  
-   所有工作流程執行個體都在單一電腦上執行  
  
-   工作流程執行個體所接收的所有訊息都會由同一部電腦所接收。  
  
 請使用 <xref:System.Activities.Statements.Persist> 活動或是將 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> 設定為 0，以便在服務主機或電腦故障之後復原您的工作流程執行個體。  
  
### <a name="scenario-workflow-instances-are-idle-for-long-periods-of-time"></a>案例：工作流程執行個體閒置很長的期間  
 在此案例中，將 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 設定為 0 來盡快釋出資源。  
  
### <a name="scenario-workflow-instances-receive-multiple-messages-in-a-short-period-of-time"></a>案例：工作流程執行個體在短期內收到多個訊息  
 在此案例中，如果這些訊息是由同一部電腦所接收，請將 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 設定為 60 秒。 這樣會避免卸載及載入工作流程執行個體的快速序列。 這樣也讓執行個體不會保存在記憶體中太久。  
  
 如果這些訊息可能會由不同電腦收到，請將 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 設定為 0，並將 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A> 設定為 BasicRetry 或 AggressiveRetry。 如此可讓工作流程執行個體由另一部電腦所載入。  
  
### <a name="scenario-workflow-uses-delay-activities-with-short-durations"></a>案例：工作流程使用短期間的延遲活動  
 在此案例中，<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 會定期輪詢持續性資料庫，以找出因為過期的 <xref:System.Activities.Statements.Delay> 活動所應該載入的執行個體。 如果 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 找到一個計時器將於下一個輪詢間隔到期，SQL 工作流程執行個體存放區會縮短輪詢間隔。 然後在計時器到期之後，將會立刻發生下一次輪詢。 如此一來，SQL 工作流程執行個體存放區會達到計時器的高精確度，且計時器的執行時間要比輪詢間隔來得長，輪詢間隔是由 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> 所設定。 為了能夠及時處理較短的延遲，工作流程執行個體停留在記憶體中的時間至少必須達到一個輪詢間隔的長度。  
  
 請將 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> 設定為 0，將到期時間寫入持續性資料庫。  
  
 請將 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 設定為大於或等於 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> 的時間長度，好讓執行個體停留在記憶體中的時間至少達到一個輪詢間隔的長度。  
  
 我們不建議您降低 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>，因為這樣會導致持續性資料庫的負載增加。 使用 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 的每一部服務主機在每個偵測期間都會輪詢資料庫一次。 如果服務主機的數目很大，將 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> 設定為太短的時間間隔，則可能會導致系統的效能降低。  
  
## <a name="configuring-the-sql-workflow-instance-store"></a>設定 SQL 工作流程執行個體存放區  
 SQL 工作流程執行個體存放區具有下列組態參數：  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceEncodingOption%2A>  
 這個參數會指示 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 壓縮工作流程執行個體狀態。 壓縮會減少儲存在持續性資料庫中的資料數量，並在持續性資料庫位於專用資料庫伺服器時減少網路流量。 如果使用壓縮，則需要計算資源來壓縮及擷取執行個體狀態。 在大部分情況下，壓縮會導致效能提高。  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceCompletionAction%2A>  
 這個參數會指示 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 保留或刪除完成的執行個體。 保留完成的執行個體會使得持續性資料庫的儲存需求增加，並導致資料表變大，而這樣會增加資料表查詢時間。 除非偵錯或稽核需要完成的執行個體，否則最好指示 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 刪除完成的執行個體。 只有當使用者建立處理序以便最後移除刪除的執行個體時，才應該保留刪除的執行個體。 請注意，只要完成的工作流程執行個體位於執行個體存放區，就不能重複使用相互關聯索引鍵。  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>  
 這個參數會定義 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 輪詢持續性資料庫所使用的最長間隔，以找出 <xref:System.Activities.Statements.Delay> 活動到期時應該載入的執行個體。 如果 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 找到一個計時器將於下一個輪詢間隔到期，它就會縮短輪詢間隔，以便在計時器到期之後立刻發生下一次輪詢。 如此一來，SQL 工作流程執行個體存放區會達到計時器的高精確度，且計時器的執行時間要比 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> 來得長。  
  
 我們不建議您降低 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>，因為這樣會導致持續性資料庫的負載增加。 使用 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 的每一部服務主機在每個偵測期間都會輪詢資料庫一次。 如果服務主機的數目很大，將 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> 設定為太短的時間間隔，則可能會導致系統的效能降低。  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>  
 這個參數會定義主機在持續性資料庫中更新其鎖定的間隔。 將此間隔縮短會在主機或電腦故障時更快復原工作流程執行個體。 另一方面，較短的鎖定更新期間也會增加持續性資料庫的負載。 使用 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 的每一部服務主機在每個更新期間都會更新其在資料庫中的鎖定一次。 如果電腦執行許多服務主機，請確定鎖定更新所產生的負載不會降低系統的效能。 如果會的話，請考慮增加 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>。  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>  
 如果啟用的話，<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 會在接下來的 30 秒鐘內重試載入鎖定的執行個體。 如果工作流程在短期內收到多個訊息，而且這些訊息是由不同電腦所接收，請將 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> 設定為 BasicRetry 或 AggressiveRetry。  
  
 只要未嘗試載入重試，載入重試機制就不會導致任何效能負擔，所以應該要一直啟用 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>。
