---
title: 作法：建立自訂持續性參與者
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: 47283375b618422d91a6279ee9049fae469f540a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989673"
---
# <a name="how-to-create-a-custom-persistence-participant"></a><span data-ttu-id="9c550-102">作法：建立自訂持續性參與者</span><span class="sxs-lookup"><span data-stu-id="9c550-102">How to: Create a Custom Persistence Participant</span></span>
<span data-ttu-id="9c550-103">下列程序包含建立持續性參與者的步驟。</span><span class="sxs-lookup"><span data-stu-id="9c550-103">The following procedure has steps to create a persistence participant.</span></span> <span data-ttu-id="9c550-104">如需持續性參與者的範例執行，請參閱[參與持續](https://go.microsoft.com/fwlink/?LinkID=177735)性範例和[儲存](store-extensibility.md)擴充性主題。</span><span class="sxs-lookup"><span data-stu-id="9c550-104">See the [Participating in Persistence](https://go.microsoft.com/fwlink/?LinkID=177735) sample and [Store Extensibility](store-extensibility.md) topic for sample implementations of persistence participants.</span></span>  
  
1. <span data-ttu-id="9c550-105">建立從 <xref:System.Activities.Persistence.PersistenceParticipant> 或 <xref:System.Activities.Persistence.PersistenceIOParticipant> 類別衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="9c550-105">Create a class deriving from the <xref:System.Activities.Persistence.PersistenceParticipant> or the <xref:System.Activities.Persistence.PersistenceIOParticipant> class.</span></span> <span data-ttu-id="9c550-106">除了能夠參與 i/o 作業外，PersistenceIOParticipant 類別還提供與 PersistenceParticipant 類別相同的擴充點。</span><span class="sxs-lookup"><span data-stu-id="9c550-106">The PersistenceIOParticipant class offers the same extensibility points as the PersistenceParticipant class in addition to being able to participate in I/O operations.</span></span> <span data-ttu-id="9c550-107">請依照下列其中一個或多個步驟進行。</span><span class="sxs-lookup"><span data-stu-id="9c550-107">Follow one or more of the following steps.</span></span>  
  
2. <span data-ttu-id="9c550-108">實作 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9c550-108">Implement the <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> method.</span></span> <span data-ttu-id="9c550-109">**CollectValues**方法有兩個字典參數，一個用於儲存讀取/寫入值，另一個用於儲存僅限寫入的值（稍後用於查詢中）。</span><span class="sxs-lookup"><span data-stu-id="9c550-109">The **CollectValues** method has two dictionary parameters, one for storing read/write values and the other one for storing write-only values (used later in queries).</span></span> <span data-ttu-id="9c550-110">在這個方法中，您應在這些字典內填入持續性參與者專屬的資料。</span><span class="sxs-lookup"><span data-stu-id="9c550-110">In this method, you should populate these dictionaries with data that is specific to a persistence participant.</span></span> <span data-ttu-id="9c550-111">每個字典均包含值的名稱做為索引鍵，而值的本身則做為 <xref:System.Runtime.DurableInstancing.InstanceValue> 物件。</span><span class="sxs-lookup"><span data-stu-id="9c550-111">Each dictionary contains the name of the value as the key and the value itself as an <xref:System.Runtime.DurableInstancing.InstanceValue> object.</span></span>  
  
    <span data-ttu-id="9c550-112">ReadWriteValues 字典中的值會封裝為**InstanceValue**物件。</span><span class="sxs-lookup"><span data-stu-id="9c550-112">The values in the readWriteValues dictionary are packaged as **InstanceValue** objects.</span></span> <span data-ttu-id="9c550-113">僅限寫入字典中的值會封裝為具有 InstanceValueOptions 的**InstanceValue**物件和 InstanceValueOption 集。</span><span class="sxs-lookup"><span data-stu-id="9c550-113">The values in the write-only dictionary are packaged as **InstanceValue** objects with InstanceValueOptions.Optional and InstanceValueOption.WriteOnly set.</span></span> <span data-ttu-id="9c550-114">所有持續性參與者的**CollectValues**實施所提供的每個**InstanceValue**都必須有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c550-114">Each **InstanceValue** provided by the **CollectValues** implementations across all persistence participants must have a unique name.</span></span>
  
    ```csharp  
    protected virtual void CollectValues(out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
3. <span data-ttu-id="9c550-115">實作 <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9c550-115">Implement the <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> method.</span></span> <span data-ttu-id="9c550-116">**MapValues**方法會採用兩個參數，與**CollectValues**方法所接收的參數類似。</span><span class="sxs-lookup"><span data-stu-id="9c550-116">The **MapValues** method takes two parameters that are similar to the parameters that the **CollectValues** method receives.</span></span> <span data-ttu-id="9c550-117">**CollectValues**階段中收集的所有值都會透過這些字典參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="9c550-117">All the values collected in the **CollectValues** stage are passed through these dictionary parameters.</span></span> <span data-ttu-id="9c550-118">**MapValues**階段新增的新值會加入至僅限寫入的值。</span><span class="sxs-lookup"><span data-stu-id="9c550-118">The new values added by the **MapValues** stage are added to the write-only values.</span></span>  <span data-ttu-id="9c550-119">唯寫字典可用來提供資料給與執行個體值沒有直接關聯性的外部資源。</span><span class="sxs-lookup"><span data-stu-id="9c550-119">The write-only dictionary is used to provide data to an external source not directly associated with the instance values.</span></span> <span data-ttu-id="9c550-120">跨所有持續性參與者的**MapValues**方法的執行所提供的每個值都必須有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c550-120">Each value provided by implementations of the **MapValues** method across all persistence participants must have a unique name.</span></span>  
  
    ```csharp  
    protected virtual IDictionary<XName,Object> MapValues(IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
     <span data-ttu-id="9c550-121"><xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 方法提供 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 不提供的功能，可允許與另一個尚未經 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 處理過的持續性參與者所提供的值產生相依性。</span><span class="sxs-lookup"><span data-stu-id="9c550-121">The <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> method provides functionality that <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> does not, in that it allows for a dependency on another value provided by another persistence participant that hasn’t been processed by <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> yet.</span></span>  
  
4. <span data-ttu-id="9c550-122">執行**PublishValues**方法。</span><span class="sxs-lookup"><span data-stu-id="9c550-122">Implement the **PublishValues** method.</span></span> <span data-ttu-id="9c550-123">**PublishValues**方法會接收字典，其中包含從持續性存放區載入的所有值。</span><span class="sxs-lookup"><span data-stu-id="9c550-123">The **PublishValues** method receives a dictionary containing all the values loaded from the persistence store.</span></span>  
  
    ```csharp  
    protected virtual void PublishValues(IDictionary<XName,Object> readWriteValues)
    {
    }
    ```  
  
5. <span data-ttu-id="9c550-124">如果參與者是持續性 i/o 參與者，請執行**BeginOnSave**方法。</span><span class="sxs-lookup"><span data-stu-id="9c550-124">Implement the **BeginOnSave** method if the participant is a persistence I/O participant.</span></span> <span data-ttu-id="9c550-125">系統會在儲存作業期間呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="9c550-125">This method is called during a Save operation.</span></span> <span data-ttu-id="9c550-126">在此方法中，您應該執行附屬於保存（儲存）工作流程實例的 i/o。</span><span class="sxs-lookup"><span data-stu-id="9c550-126">In this method, you should perform I/O adjunct to the persisting (saving) workflow instances.</span></span>  <span data-ttu-id="9c550-127">如果主機使用對應持續性命令的異動，則同樣的異動會在 Transaction.Current 中提供。</span><span class="sxs-lookup"><span data-stu-id="9c550-127">If the host is using a transaction for the corresponding persistence command, the same transaction is provided in Transaction.Current.</span></span>  <span data-ttu-id="9c550-128">此外，PersistenceIOParticipants 可能會通告交易一致性需求，此時，主機會為持續性時段建立交易 (如果未使用任何交易)。</span><span class="sxs-lookup"><span data-stu-id="9c550-128">Additionally, PersistenceIOParticipants may advertise a transactional consistency requirement, in which case the host creates a transaction for the persistence episode if one would not otherwise be used.</span></span>  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnSave(IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```  
  
6. <span data-ttu-id="9c550-129">如果參與者是持續性 i/o 參與者，請執行**BeginOnLoad**方法。</span><span class="sxs-lookup"><span data-stu-id="9c550-129">Implement the **BeginOnLoad** method if the participant is a persistence I/O participant.</span></span> <span data-ttu-id="9c550-130">系統會在載入作業期間呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="9c550-130">This method is called during a Load operation.</span></span> <span data-ttu-id="9c550-131">在此方法中，您應該執行與載入工作流程實例有關的 i/o。</span><span class="sxs-lookup"><span data-stu-id="9c550-131">In this method, you should perform I/O adjunct to the loading of workflow instances.</span></span> <span data-ttu-id="9c550-132">如果主機使用對應持續性命令的異動，則同樣的異動會在 Transaction.Current 中提供。</span><span class="sxs-lookup"><span data-stu-id="9c550-132">If the host is using a transaction for the corresponding persistence command, the same transaction is provided in Transaction.Current.</span></span> <span data-ttu-id="9c550-133">此外，持續性 i/o 參與者可能會通告交易一致性需求，在這種情況下，主機會為持續性集建立交易（如果未使用的話）。</span><span class="sxs-lookup"><span data-stu-id="9c550-133">Additionally, Persistence I/O participants may advertise a transactional consistency requirement, in which case the host creates a transaction for the persistence episode if one would not otherwise be used.</span></span>  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnLoad(IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```
