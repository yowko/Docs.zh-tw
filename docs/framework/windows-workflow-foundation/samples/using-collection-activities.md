---
title: 使用集合活動
ms.date: 03/30/2017
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
ms.openlocfilehash: a92208583ddf1c0d5d85b5af6a250a15ac8851b9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422623"
---
# <a name="using-collection-activities"></a><span data-ttu-id="d3cca-102">使用集合活動</span><span class="sxs-lookup"><span data-stu-id="d3cca-102">Using Collection Activities</span></span>
<span data-ttu-id="d3cca-103">這個範例會示範如何透過實作 <xref:System.Activities.Statements.AddToCollection%601> 介面的類別使用集合活動 (<xref:System.Activities.Statements.ClearCollection%601>、<xref:System.Activities.Statements.ExistsInCollection%601>、<xref:System.Activities.Statements.RemoveFromCollection%601> 和 <xref:System.Collections.ICollection>)，以及如何建立自訂活動，以便逐一查看集合以列印集合中每一個項目的內容。</span><span class="sxs-lookup"><span data-stu-id="d3cca-103">This sample demonstrates how to use the collection activities (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, and <xref:System.Activities.Statements.RemoveFromCollection%601>) with a class that implements the <xref:System.Collections.ICollection> interface and how to create a custom activity that iterates over a collection to print out the contents of each element in the collection.</span></span> <span data-ttu-id="d3cca-104">名為 `PrintCollection` 的自訂活動會將名為 `Numbers` 之集合的項目成員列印到主控台。</span><span class="sxs-lookup"><span data-stu-id="d3cca-104">The custom activity, which is named `PrintCollection`, prints to the console the item members of a collection named `Numbers`.</span></span>  
  
 <span data-ttu-id="d3cca-105">下表描述四個活動，這些活動會提供工作流程的集合操作。</span><span class="sxs-lookup"><span data-stu-id="d3cca-105">The following table describes the four activities that provide collection manipulation for workflows.</span></span>  
  
|<span data-ttu-id="d3cca-106">活動名稱</span><span class="sxs-lookup"><span data-stu-id="d3cca-106">Activity name</span></span>|<span data-ttu-id="d3cca-107">描述</span><span class="sxs-lookup"><span data-stu-id="d3cca-107">Description</span></span>|  
|-------------------|-----------------|  
|<xref:System.Activities.Statements.AddToCollection%601>|<span data-ttu-id="d3cca-108">將項目加入至集合。</span><span class="sxs-lookup"><span data-stu-id="d3cca-108">Adds an item to a collection.</span></span>|  
|<xref:System.Activities.Statements.ClearCollection%601>|<span data-ttu-id="d3cca-109">清除集合中的所有項目</span><span class="sxs-lookup"><span data-stu-id="d3cca-109">Clears all items in a collection</span></span>|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|<span data-ttu-id="d3cca-110">如果指定的項目存在於集合中，則傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="d3cca-110">Returns `true` if specified item exists in collection.</span></span>|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|<span data-ttu-id="d3cca-111">從集合中移除項目。</span><span class="sxs-lookup"><span data-stu-id="d3cca-111">Removes an item from a collection.</span></span>|  
  
 <span data-ttu-id="d3cca-112">此範例是由兩個方案所組成，一個位於 CodedWorkflow 目錄底下，另一個位於 DesignerWorkflow 目錄底下。</span><span class="sxs-lookup"><span data-stu-id="d3cca-112">The sample consists of two solutions, one under the CodedWorkflow directory and the other under the DesignerWorkflow directory.</span></span> <span data-ttu-id="d3cca-113">這兩個方案會示範針對相同的用途使用活動的兩個不同方式。</span><span class="sxs-lookup"><span data-stu-id="d3cca-113">They demonstrate two different ways of using the activities for the same purposes.</span></span>  
  
|<span data-ttu-id="d3cca-114">方案</span><span class="sxs-lookup"><span data-stu-id="d3cca-114">Solution</span></span>|<span data-ttu-id="d3cca-115">描述</span><span class="sxs-lookup"><span data-stu-id="d3cca-115">Description</span></span>|<span data-ttu-id="d3cca-116">主要檔案</span><span class="sxs-lookup"><span data-stu-id="d3cca-116">Main Files</span></span>|  
|-|-|-|  
|<span data-ttu-id="d3cca-117">CodedWorkflow</span><span class="sxs-lookup"><span data-stu-id="d3cca-117">CodedWorkflow</span></span>|<span data-ttu-id="d3cca-118">範例用戶端應用程式，可示範如何以程式設計方式叫用集合活動。</span><span class="sxs-lookup"><span data-stu-id="d3cca-118">Sample client application that demonstrates how to invoke the collection activities programmatically.</span></span>|<span data-ttu-id="d3cca-119">**PrintCollection.cs**： 列印到主控台每個項目集合中的協助程式活動。</span><span class="sxs-lookup"><span data-stu-id="d3cca-119">**PrintCollection.cs**: helper activity to print out to the console every item in a collection.</span></span><br /><br /> <span data-ttu-id="d3cca-120">**Program.cs**： 以程式設計方式建立序列活動，會包含一系列集合活動，並執行它。</span><span class="sxs-lookup"><span data-stu-id="d3cca-120">**Program.cs**: programmatically builds a sequence activity that contains a series of collection activities, and executes it.</span></span>|  
|<span data-ttu-id="d3cca-121">DesignerWorkflow</span><span class="sxs-lookup"><span data-stu-id="d3cca-121">DesignerWorkflow</span></span>|<span data-ttu-id="d3cca-122">範例用戶端應用程式，可示範如何以宣告方式在工作流程設計工具中使用集合活動。</span><span class="sxs-lookup"><span data-stu-id="d3cca-122">Sample client application that demonstrates how to use the collection activities declaratively in the workflow designer.</span></span>|<span data-ttu-id="d3cca-123">**CollectionWorkflow.xaml**： 以宣告方式建立與使用集合活動設計工具的工作流程。</span><span class="sxs-lookup"><span data-stu-id="d3cca-123">**CollectionWorkflow.xaml**: a workflow created declaratively with the designer that uses the collection activities.</span></span><br /><br /> <span data-ttu-id="d3cca-124">**PrintCollection.cs**： 列印到主控台每個項目集合中的協助程式活動。</span><span class="sxs-lookup"><span data-stu-id="d3cca-124">**PrintCollection.cs**: helper activity to print out to the console every item in a collection.</span></span><br /><br /> <span data-ttu-id="d3cca-125">**Program.cs**： 叫用 CollectionWorkflow.xaml 中所述的工作流程。</span><span class="sxs-lookup"><span data-stu-id="d3cca-125">**Program.cs**: invokes the workflow described in CollectionWorkflow.xaml.</span></span>|  
  
 <span data-ttu-id="d3cca-126">在示範中，將會使用稱為 `Numbers` 的自訂活動，將 `PrintCollection` 集合的項目成員列印到主控台。</span><span class="sxs-lookup"><span data-stu-id="d3cca-126">In the demonstration, the item members of collection `Numbers` are printed on the console using a custom-defined activity called `PrintCollection`.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d3cca-127">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="d3cca-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="d3cca-128">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 Collection.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="d3cca-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Collection.sln solution file.</span></span>  
  
2.  <span data-ttu-id="d3cca-129">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="d3cca-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="d3cca-130">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="d3cca-130">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d3cca-131">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d3cca-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d3cca-132">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="d3cca-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d3cca-133">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="d3cca-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d3cca-134">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="d3cca-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`