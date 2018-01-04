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
# <a name="how-to-create-a-custom-persistence-participant"></a><span data-ttu-id="f96da-102">HOW TO：建立自訂非持續性參與者</span><span class="sxs-lookup"><span data-stu-id="f96da-102">How to: Create a Custom Persistence Participant</span></span>
<span data-ttu-id="f96da-103">下列程序包含建立持續性參與者的步驟。</span><span class="sxs-lookup"><span data-stu-id="f96da-103">The following procedure has steps to create a persistence participant.</span></span> <span data-ttu-id="f96da-104">請參閱[參與持續性](http://go.microsoft.com/fwlink/?LinkID=177735)範例和[存放區擴充性](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)的持續性參與者的範例實作的主題。</span><span class="sxs-lookup"><span data-stu-id="f96da-104">See the [Participating in Persistence](http://go.microsoft.com/fwlink/?LinkID=177735) sample and [Store Extensibility](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) topic for sample implementations of persistence participants.</span></span>  
  
1.  <span data-ttu-id="f96da-105">建立從 <xref:System.Activities.Persistence.PersistenceParticipant> 或 <xref:System.Activities.Persistence.PersistenceIOParticipant> 類別衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="f96da-105">Create a class deriving from the <xref:System.Activities.Persistence.PersistenceParticipant> or the <xref:System.Activities.Persistence.PersistenceIOParticipant> class.</span></span> <span data-ttu-id="f96da-106">除了能夠參與 IO 作業外，PersistenceIOParticipant 類別與 PersistenceParticipant 類別提供相同的擴充點。</span><span class="sxs-lookup"><span data-stu-id="f96da-106">The PersistenceIOParticipant class offers the same extensibility points as the PersistenceParticipant class in addition to being able to participate in IO operations.</span></span> <span data-ttu-id="f96da-107">請依照下列其中一個或多個步驟進行。</span><span class="sxs-lookup"><span data-stu-id="f96da-107">Follow one or more of the following steps.</span></span>  
  
2.  <span data-ttu-id="f96da-108">實作 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f96da-108">Implement the <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> method.</span></span> <span data-ttu-id="f96da-109">**CollectValues**方法有兩個字典參數，一個用於儲存讀取/寫入值，另一個則用於儲存唯寫值 （稍後用於查詢中）。</span><span class="sxs-lookup"><span data-stu-id="f96da-109">The **CollectValues** method has two dictionary parameters, one for storing read/write values and the other one for storing write-only values (used later in queries).</span></span> <span data-ttu-id="f96da-110">在這個方法中，您應在這些字典內填入持續性參與者專屬的資料。</span><span class="sxs-lookup"><span data-stu-id="f96da-110">In this method, you should populate these dictionaries with data that is specific to a persistence participant.</span></span> <span data-ttu-id="f96da-111">每個字典均包含值的名稱做為索引鍵，而值的本身則做為 <xref:System.Runtime.DurableInstancing.InstanceValue> 物件。</span><span class="sxs-lookup"><span data-stu-id="f96da-111">Each dictionary contains the name of the value as the key and the value itself as an <xref:System.Runtime.DurableInstancing.InstanceValue> object.</span></span>  
  
     <span data-ttu-id="f96da-112">ReadWriteValues 字典中的值會封裝為**InstanceValue**物件。</span><span class="sxs-lookup"><span data-stu-id="f96da-112">The values in the readWriteValues dictionary are packaged as **InstanceValue** objects.</span></span> <span data-ttu-id="f96da-113">唯寫字典中的值會封裝為**InstanceValue** InstanceValueOptions.Optional 及 InstanceValueOption.WriteOnly 的集合物件。</span><span class="sxs-lookup"><span data-stu-id="f96da-113">The values in the write-only dictionary are packaged as **InstanceValue** objects with InstanceValueOptions.Optional and InstanceValueOption.WriteOnly set.</span></span> <span data-ttu-id="f96da-114">每個**InstanceValue**提供**CollectValues**跨所有持續性參與者實作必須有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="f96da-114">Each **InstanceValue** provided by the **CollectValues** implementations across all persistence participants must have a unique name.</span></span>  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3.  <span data-ttu-id="f96da-115">實作 <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f96da-115">Implement the <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> method.</span></span> <span data-ttu-id="f96da-116">**MapValues**方法採用兩個類似的參數的參數， **CollectValues**方法會接收。</span><span class="sxs-lookup"><span data-stu-id="f96da-116">The **MapValues** method takes two parameters that are similar to the parameters that the **CollectValues** method receives.</span></span> <span data-ttu-id="f96da-117">在收集到的所有值**CollectValues**階段都會透過這些字典參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="f96da-117">All the values collected in the **CollectValues** stage are passed through these dictionary parameters.</span></span> <span data-ttu-id="f96da-118">所加入的新值**MapValues**階段會加入到唯寫值。</span><span class="sxs-lookup"><span data-stu-id="f96da-118">The new values added by the **MapValues** stage are added to the write-only values.</span></span>  <span data-ttu-id="f96da-119">唯寫字典可用來提供資料給與執行個體值沒有直接關聯性的外部資源。</span><span class="sxs-lookup"><span data-stu-id="f96da-119">The write-only dictionary is used to provide data to an external source not directly associated with the instance values.</span></span> <span data-ttu-id="f96da-120">實作所提供的每個值**MapValues**跨所有持續性參與者的方法必須有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="f96da-120">Each value provided by implementations of the **MapValues** method across all persistence participants must have a unique name.</span></span>  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     <span data-ttu-id="f96da-121"><xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 方法提供 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 不提供的功能，可允許與另一個尚未經 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 處理過的持續性參與者所提供的值產生相依性。</span><span class="sxs-lookup"><span data-stu-id="f96da-121">The <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> method provides functionality that <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> does not, in that it allows for a dependency on another value provided by another persistence participant that hasn’t been processed by <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> yet.</span></span>  
  
4.  <span data-ttu-id="f96da-122">實作**PublishValues**方法。</span><span class="sxs-lookup"><span data-stu-id="f96da-122">Implement the **PublishValues** method.</span></span> <span data-ttu-id="f96da-123">**PublishValues**方法會接收字典，其中包含從持續性存放區載入的所有值。</span><span class="sxs-lookup"><span data-stu-id="f96da-123">The **PublishValues** method receives a dictionary containing all the values loaded from the persistence store.</span></span>  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5.  <span data-ttu-id="f96da-124">實作**BeginOnSave**方法如果參與者是持續性 IO 參與者。</span><span class="sxs-lookup"><span data-stu-id="f96da-124">Implement the **BeginOnSave** method if the participant is a persistence IO participant.</span></span> <span data-ttu-id="f96da-125">系統會在儲存作業期間呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="f96da-125">This method is called during a Save operation.</span></span> <span data-ttu-id="f96da-126">在這個方法中，您應執行附屬於持續性 (儲存中) 工作流程執行個體的 IO。</span><span class="sxs-lookup"><span data-stu-id="f96da-126">In this method, you should perform IO adjunct to the persisting (saving) workflow instances.</span></span>  <span data-ttu-id="f96da-127">如果主機使用對應持續性命令的交易，則同樣的交易會在 Transaction.Current 中提供。</span><span class="sxs-lookup"><span data-stu-id="f96da-127">If the host is using a transaction for the corresponding persistence command, the same transaction is provided in Transaction.Current.</span></span>  <span data-ttu-id="f96da-128">此外，PersistenceIOParticipants 可能會通告異動一致性需求，此時，主機會為持續性時段建立異動 (如果未使用任何異動)。</span><span class="sxs-lookup"><span data-stu-id="f96da-128">Additionally, PersistenceIOParticipants may advertise a transactional consistency requirement, in which case the host creates a transaction for the persistence episode if one would not otherwise be used.</span></span>  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  <span data-ttu-id="f96da-129">實作**BeginOnLoad**方法如果參與者是持續性 IO 參與者。</span><span class="sxs-lookup"><span data-stu-id="f96da-129">Implement the **BeginOnLoad** method if the participant is a persistence IO participant.</span></span> <span data-ttu-id="f96da-130">系統會在載入作業期間呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="f96da-130">This method is called during a Load operation.</span></span> <span data-ttu-id="f96da-131">在這個方法中，您應執行附屬於工作流程執行個體載入作業的 IO。</span><span class="sxs-lookup"><span data-stu-id="f96da-131">In this method, you should perform IO adjunct to the loading of workflow instances.</span></span> <span data-ttu-id="f96da-132">如果主機使用對應持續性命令的交易，則同樣的交易會在 Transaction.Current 中提供。</span><span class="sxs-lookup"><span data-stu-id="f96da-132">If the host is using a transaction for the corresponding persistence command, the same transaction is provided in Transaction.Current.</span></span> <span data-ttu-id="f96da-133">此外，PersistenceIO 參與者可能會通告交易一致性需求，此時，主機會為持續性時段建立交易 (如果未使用任何交易)。</span><span class="sxs-lookup"><span data-stu-id="f96da-133">Additionally, Persistence IO participants may advertise a transactional consistency requirement, in which case the host creates a transaction for the persistence episode if one would not otherwise be used.</span></span>  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
