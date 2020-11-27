---
title: 活動樹狀結構檢查
ms.date: 03/30/2017
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
ms.openlocfilehash: 044dcbbe7f22b1026dbc4dc14ab87da4f5a9d0ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289148"
---
# <a name="activity-tree-inspection"></a><span data-ttu-id="e5990-102">活動樹狀結構檢查</span><span class="sxs-lookup"><span data-stu-id="e5990-102">Activity Tree Inspection</span></span>

<span data-ttu-id="e5990-103">活動樹狀檢查可供工作流程應用程式作者用於檢查應用程式所裝載的工作流程。</span><span class="sxs-lookup"><span data-stu-id="e5990-103">Activity tree inspection is used by workflow application authors to inspect the workflows hosted by the application.</span></span> <span data-ttu-id="e5990-104">使用 <xref:System.Activities.WorkflowInspectionServices>，即可針對特定子活動搜尋工作流程、列舉個別活動及其屬性，以及在特定時間快取活動的執行階段中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e5990-104">By using <xref:System.Activities.WorkflowInspectionServices>, workflows can be searched for specific child activities, individual activities and their properties can be enumerated, and runtime metadata of the activities can be cached at a specific time.</span></span> <span data-ttu-id="e5990-105">本主題提供 <xref:System.Activities.WorkflowInspectionServices> 的概觀，並且說明如何利用它來檢查活動樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="e5990-105">This topic provides an overview of <xref:System.Activities.WorkflowInspectionServices> and how to use it to inspect an activity tree.</span></span>  
  
## <a name="using-workflowinspectionservices"></a><span data-ttu-id="e5990-106">使用 WorkflowInspectionServices</span><span class="sxs-lookup"><span data-stu-id="e5990-106">Using WorkflowInspectionServices</span></span>  

 <span data-ttu-id="e5990-107"><xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 方法用於列舉指定活動樹狀中的所有活動。</span><span class="sxs-lookup"><span data-stu-id="e5990-107">The <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> method is used to enumerate all of the activities in the specified activity tree.</span></span> <span data-ttu-id="e5990-108"><xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 會傳回可列舉項目，該項目會觸及樹狀結構中的所有活動，包括子系、委派處理常式、預設變數及引數運算式。</span><span class="sxs-lookup"><span data-stu-id="e5990-108"><xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> returns an enumerable that touches all activities within the tree including children, delegate handlers, variable defaults, and argument expressions.</span></span> <span data-ttu-id="e5990-109">在下列範例中，工作流程定義是使用 <xref:System.Activities.Statements.Sequence>、<xref:System.Activities.Statements.While>、<xref:System.Activities.Statements.ForEach%601>、<xref:System.Activities.Statements.WriteLine> 和運算式所建立。</span><span class="sxs-lookup"><span data-stu-id="e5990-109">In the following example, a workflow definition is created by using a <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.WriteLine>, and expressions.</span></span> <span data-ttu-id="e5990-110">建立工作流程定義之後，就會叫用該工作流程，然後呼叫 `InspectActivity` 方法。</span><span class="sxs-lookup"><span data-stu-id="e5990-110">After the workflow definition is created, it is invoked and then the `InspectActivity` method is called.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 <span data-ttu-id="e5990-111">為了列舉活動，會在根活動上呼叫 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>，然後再次以遞迴方式在每個傳回的活動上呼叫。</span><span class="sxs-lookup"><span data-stu-id="e5990-111">To enumerate the activities, the <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> is called on the root activity, and again recursively on each returned activity.</span></span> <span data-ttu-id="e5990-112">在下列範例中，會將活動樹狀中每個活動和運算式的 <xref:System.Activities.Activity.DisplayName%2A> 寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="e5990-112">In the following example, the <xref:System.Activities.Activity.DisplayName%2A> of each activity and expression in the activity tree is written to the console.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 <span data-ttu-id="e5990-113">這個範例程式碼會提供下列輸出。</span><span class="sxs-lookup"><span data-stu-id="e5990-113">This sample code provides the following output.</span></span>  
  
 <span data-ttu-id="e5990-114">**清單項目 1**</span><span class="sxs-lookup"><span data-stu-id="e5990-114">**List Item 1**</span></span>  
<span data-ttu-id="e5990-115">**清單專案 2** 
**清單專案 3** 
**清單專案 4** 
**清單專案 5** 
**加入至集合的專案。** 
**序列\*\*\*\*常值<\<String> > 清單**</span><span class="sxs-lookup"><span data-stu-id="e5990-115">**List Item 2**
**List Item 3**
**List Item 4**
**List Item 5**
**Items added to collection.**
**Sequence** **Literal<List\<String>>**</span></span>  
 <span data-ttu-id="e5990-116">**While**</span><span class="sxs-lookup"><span data-stu-id="e5990-116">**While**</span></span>  
 <span data-ttu-id="e5990-117">**AddToCollection\<String>**</span><span class="sxs-lookup"><span data-stu-id="e5990-117">**AddToCollection\<String>**</span></span>  
 <span data-ttu-id="e5990-118">**VariableValue<ICollection\<String>>**</span><span class="sxs-lookup"><span data-stu-id="e5990-118">**VariableValue<ICollection\<String>>**</span></span>  
 <span data-ttu-id="e5990-119">**LambdaValue\<String>**</span><span class="sxs-lookup"><span data-stu-id="e5990-119">**LambdaValue\<String>**</span></span>  
 <span data-ttu-id="e5990-120">**LocationReferenceValue<清單\<String>>**</span><span class="sxs-lookup"><span data-stu-id="e5990-120">**LocationReferenceValue<List\<String>>**</span></span>  
 <span data-ttu-id="e5990-121">**LambdaValue\<Boolean>**</span><span class="sxs-lookup"><span data-stu-id="e5990-121">**LambdaValue\<Boolean>**</span></span>  
 <span data-ttu-id="e5990-122">**LocationReferenceValue<清單\<String>>**</span><span class="sxs-lookup"><span data-stu-id="e5990-122">**LocationReferenceValue<List\<String>>**</span></span>  
 <span data-ttu-id="e5990-123">**Foreach\<String>**</span><span class="sxs-lookup"><span data-stu-id="e5990-123">**ForEach\<String>**</span></span>  
 <span data-ttu-id="e5990-124">**VariableValue<IEnumerable\<String>>**</span><span class="sxs-lookup"><span data-stu-id="e5990-124">**VariableValue<IEnumerable\<String>>**</span></span>  
 <span data-ttu-id="e5990-125">**WriteLine**</span><span class="sxs-lookup"><span data-stu-id="e5990-125">**WriteLine**</span></span>  
 <span data-ttu-id="e5990-126">**DelegateArgumentValue\<String>**</span><span class="sxs-lookup"><span data-stu-id="e5990-126">**DelegateArgumentValue\<String>**</span></span>  
 <span data-ttu-id="e5990-127">**序列**</span><span class="sxs-lookup"><span data-stu-id="e5990-127">**Sequence**</span></span>  
 <span data-ttu-id="e5990-128">**WriteLine**</span><span class="sxs-lookup"><span data-stu-id="e5990-128">**WriteLine**</span></span>  
 <span data-ttu-id="e5990-129">**常 \<String>** 值 若要取得特定的活動，而不是列舉所有活動， <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> 則會使用。</span><span class="sxs-lookup"><span data-stu-id="e5990-129">**Literal\<String>**  To retrieve a specific activity instead of enumerating all of the activities, <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> is used.</span></span> <span data-ttu-id="e5990-130">如果先前尚未呼叫過 <xref:System.Activities.WorkflowInspectionServices.Resolve%2A>，<xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 和 `WorkflowInspectionServices.CacheMetadata` 都會執行中繼資料快取。</span><span class="sxs-lookup"><span data-stu-id="e5990-130">Both <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> and <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> perform metadata caching if `WorkflowInspectionServices.CacheMetadata` has not been previously called.</span></span> <span data-ttu-id="e5990-131">如果已經呼叫過 <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>，則 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 會以現有的中繼資料為基礎。</span><span class="sxs-lookup"><span data-stu-id="e5990-131">If <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> has been called then <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> is based on the existing metadata.</span></span> <span data-ttu-id="e5990-132">因此，自上次呼叫 <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> 以來，如果樹狀結構進行過變更，<xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 可能會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="e5990-132">Therefore, if tree changes have been made since the last call to <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> might give unexpected results.</span></span> <span data-ttu-id="e5990-133">如果在呼叫後對工作流程進行了變更 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> ，則可以藉由呼叫方法來重新快取中繼資料 <xref:System.Activities.Validation.ActivityValidationServices> <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 。</span><span class="sxs-lookup"><span data-stu-id="e5990-133">If changes have been made to the workflow after calling <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>, metadata can be re-cached by calling the <xref:System.Activities.Validation.ActivityValidationServices> <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> method.</span></span> <span data-ttu-id="e5990-134">下一節將討論快取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e5990-134">Caching metadata is discussed in the next section.</span></span>  
  
### <a name="caching-metadata"></a><span data-ttu-id="e5990-135">快取中繼資料</span><span class="sxs-lookup"><span data-stu-id="e5990-135">Caching Metadata</span></span>  

 <span data-ttu-id="e5990-136">快取活動的中繼資料會建置並驗證活動之引數、變數、子活動和活動委派的描述。</span><span class="sxs-lookup"><span data-stu-id="e5990-136">Caching the metadata for an activity builds and validates a description of the activity’s arguments, variables, child activities, and activity delegates.</span></span> <span data-ttu-id="e5990-137">根據預設，中繼資料會在預備執行活動時由執行階段快取。</span><span class="sxs-lookup"><span data-stu-id="e5990-137">Metadata, by default, is cached by the runtime when an activity is prepared for execution.</span></span> <span data-ttu-id="e5990-138">如果工作流程主機作者想要在此之前快取活動或活動樹狀的中繼資料，例如要預先取得成本，可以使用 <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>，在任何時間快取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e5990-138">If a workflow host author wants to cache the metadata for an activity or activity tree before this, for example to take all of the cost upfront, then <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> can be used to cache the metadata at the desired time.</span></span>
