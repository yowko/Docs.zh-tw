---
title: "工具箱服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 294c530072b2d694f9aeb54d04b36d72bb6da637
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="toolbox-service"></a><span data-ttu-id="c22a7-102">工具箱服務</span><span class="sxs-lookup"><span data-stu-id="c22a7-102">Toolbox Service</span></span>
<span data-ttu-id="c22a7-103">這個範例示範如何根據工作流程的內容來更新 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 工具箱活動。</span><span class="sxs-lookup"><span data-stu-id="c22a7-103">This sample demonstrates how to update the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] Toolbox activities based on the context of the workflow.</span></span> <span data-ttu-id="c22a7-104">此範例包含會隨著自訂活動是否選取而變更工具箱內容的工作流程。</span><span class="sxs-lookup"><span data-stu-id="c22a7-104">The sample contains a workflow that changes the toolbox contents based on whether a custom activity is selected.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c22a7-105">討論</span><span class="sxs-lookup"><span data-stu-id="c22a7-105">Discussion</span></span>  
 <span data-ttu-id="c22a7-106">在工作流程撰寫期間，客戶通常希望工具箱是與內容相關的。</span><span class="sxs-lookup"><span data-stu-id="c22a7-106">During workflow authoring, customers generally want their Toolbox to be context sensitive.</span></span> <span data-ttu-id="c22a7-107">例如，使用者可能想要確認當特定活動加入至工作流程時，工具箱會顯示一些其他活動。</span><span class="sxs-lookup"><span data-stu-id="c22a7-107">For example, the user may want to ensure that the Toolbox shows a few additional activities when a specific activity is added to the workflow.</span></span> <span data-ttu-id="c22a7-108">如果從工作流程移除活動，工具箱應該根據網域需求適當回應。</span><span class="sxs-lookup"><span data-stu-id="c22a7-108">If the activities are removed from the workflow, the toolbox should react appropriately based on the domain requirements.</span></span>  
  
 <span data-ttu-id="c22a7-109">在重新裝載的工作流程設計工具中，您可以控制工具箱控制項，並確認主機會根據工作流程中的模型變更來觸發工具箱控制項中的適當變更。</span><span class="sxs-lookup"><span data-stu-id="c22a7-109">In a re-hosted workflow designer, you control the Toolbox control and can ensure that based on the Model changes in the workflow, the host triggers appropriate changes in the Toolbox control.</span></span> <span data-ttu-id="c22a7-110">不過，在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中，工具箱不是由使用者控制，因此需要介面來修改其內容。</span><span class="sxs-lookup"><span data-stu-id="c22a7-110">However, in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], the toolbox is not controlled by the user and thus an interface is required to modify its contents.</span></span> <span data-ttu-id="c22a7-111">`IActivityToolboxService` 就是該介面。</span><span class="sxs-lookup"><span data-stu-id="c22a7-111">`IActivityToolboxService` is that interface.</span></span>  
  
 <span data-ttu-id="c22a7-112">API 提供下列四個方法。</span><span class="sxs-lookup"><span data-stu-id="c22a7-112">The API provides the following four methods.</span></span>  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c22a7-113">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="c22a7-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c22a7-114">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 WorkflowSimulator.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="c22a7-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WorkflowSimulator.sln solution file.</span></span>  
  
2.  <span data-ttu-id="c22a7-115">按 CTRL+SHIFT+B 建置此方案。</span><span class="sxs-lookup"><span data-stu-id="c22a7-115">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="c22a7-116">開啟 Workflow.xaml 檔案。</span><span class="sxs-lookup"><span data-stu-id="c22a7-116">Open the Workflow.xaml file.</span></span>  
  
4.  <span data-ttu-id="c22a7-117">新增**CustomActivity**藉由拖放從 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="c22a7-117">Add a **CustomActivity** by dragging and dropping it from the toolbox.</span></span> <span data-ttu-id="c22a7-118">請注意，額外的工具箱類別目錄名稱為：**新增 WF 類別目錄**具有額外的活動**指派**。</span><span class="sxs-lookup"><span data-stu-id="c22a7-118">Notice that an additional Toolbox category called: **New WF Category** with an additional activity **Assign**.</span></span>  
  
5.  <span data-ttu-id="c22a7-119">現在請取消選取**CustomActivity**將另一個活動拖曳至其中。</span><span class="sxs-lookup"><span data-stu-id="c22a7-119">Now unselect the **CustomActivity** by dragging another activity into it.</span></span>  
  
6.  <span data-ttu-id="c22a7-120">項目**指派**分類中**新增 WF 類別目錄**現在已移除工具箱底下。</span><span class="sxs-lookup"><span data-stu-id="c22a7-120">The item **Assign** in the category **New WF Category** under Toolbox is now removed.</span></span> <span data-ttu-id="c22a7-121">此外，因為類別目錄中沒有其他項目，類別目錄也會移除。</span><span class="sxs-lookup"><span data-stu-id="c22a7-121">Also, because there are no more items left in the category, the category is removed as well.</span></span>  
  
7.  <span data-ttu-id="c22a7-122">選取**CustomActivity**一次，類別目錄和**指派**活動就會重新加入。</span><span class="sxs-lookup"><span data-stu-id="c22a7-122">Select the **CustomActivity** again and the category and **Assign** activity is added back.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c22a7-123">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="c22a7-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c22a7-124">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="c22a7-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c22a7-125">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="c22a7-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c22a7-126">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="c22a7-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
