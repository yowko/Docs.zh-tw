---
title: "活動關聯性驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d527b728d0b4ac86a8dd98afb45a09585bd0c96
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="activity-relationships-validation"></a><span data-ttu-id="a02fa-102">活動關聯性驗證</span><span class="sxs-lookup"><span data-stu-id="a02fa-102">Activity Relationships Validation</span></span>
<span data-ttu-id="a02fa-103">這個範例包含三個活動：`CreateCity`、`CreateState` 和 `CreateCountry`。</span><span class="sxs-lookup"><span data-stu-id="a02fa-103">This sample consists of three activities, `CreateCity`, `CreateState`, and `CreateCountry`.</span></span> <span data-ttu-id="a02fa-104">`CreateCity` 必須在 `CreateState` 活動內部，而 `CreateState` 必須在 `CreateCountry` 活動內部。</span><span class="sxs-lookup"><span data-stu-id="a02fa-104">`CreateCity` must be inside a `CreateState` activity, and `CreateState` must be inside a `CreateCountry` activity.</span></span> <span data-ttu-id="a02fa-105">基於此範例的目的，`CreateState` 活動的驗證邏輯為程式碼形式，而 `CreateCity` 活動的驗證邏輯為 XAML 形式。</span><span class="sxs-lookup"><span data-stu-id="a02fa-105">For the purpose of this sample, the validation logic is in code for the `CreateState` activity, and in XAML for the `CreateCity` activity.</span></span> <span data-ttu-id="a02fa-106">這兩個條件約束有相同的行為。</span><span class="sxs-lookup"><span data-stu-id="a02fa-106">Both constraints have the same behavior.</span></span>  
  
 <span data-ttu-id="a02fa-107">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 提供下列三個協助程式活動，可讓開發人員驗證活動之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="a02fa-107">The [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] provides the following three helper activities that allow the developer to validate relationships between activities:</span></span>  
  
 <xref:System.Activities.Validation.GetParentChain>  
 <span data-ttu-id="a02fa-108">提供屬於目前節點父系之所有活動的集合</span><span class="sxs-lookup"><span data-stu-id="a02fa-108">Provides the collection of all activities that belong to the parent of the current node</span></span>  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 <span data-ttu-id="a02fa-109">提供屬於目前節點子樹狀結構所有活動的集合，但排除目前節點</span><span class="sxs-lookup"><span data-stu-id="a02fa-109">Provides the collection of all activities that belong to the sub-tree of the current node, excluding the current node</span></span>  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 <span data-ttu-id="a02fa-110">提供和目前節點位於相同樹狀結構之所有活動的集合</span><span class="sxs-lookup"><span data-stu-id="a02fa-110">Provides the collection of all activities in the same tree as the current node</span></span>  
  
 <span data-ttu-id="a02fa-111">在此範例中，<xref:System.Activities.Statements.ForEach%601> 活動是用來逐一查核 <xref:System.Activities.Validation.GetParentChain> 所傳回的集合。</span><span class="sxs-lookup"><span data-stu-id="a02fa-111">In the sample, a <xref:System.Activities.Statements.ForEach%601> activity is used to walk through the collection returned by <xref:System.Activities.Validation.GetParentChain>.</span></span> <span data-ttu-id="a02fa-112">針對集合中的每個元素，其類型會與 `CreateCountry` 比較 (如果是驗證 `CreateState`，則為 `CreateCity`)，如果找到相符元素，結果旗標會設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a02fa-112">For every element in the collection, its type is compared to `CreateCountry` (or `CreateState` if `CreateCity` is being validated), and when a match is found the result flag is set to `true`.</span></span> <span data-ttu-id="a02fa-113">最後，如果結果旗標設為 <xref:System.Activities.Validation.AssertValidation>，`false` 會用來產生驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="a02fa-113">Finally, an <xref:System.Activities.Validation.AssertValidation> is used to generate a validation error if the result flag is set to `false`.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="a02fa-114">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="a02fa-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="a02fa-115">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 ContainmentValidation.sln 範例方案。</span><span class="sxs-lookup"><span data-stu-id="a02fa-115">Open the ContainmentValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="a02fa-116">建置方案。</span><span class="sxs-lookup"><span data-stu-id="a02fa-116">Build the solution.</span></span>  
  
3.  <span data-ttu-id="a02fa-117">按 CTRL+F5 啟動程式。</span><span class="sxs-lookup"><span data-stu-id="a02fa-117">Press CTRL + F5 to launch the program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a02fa-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a02fa-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a02fa-119">請先檢查下列 (預設) 目錄，然後再繼續：</span><span class="sxs-lookup"><span data-stu-id="a02fa-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a02fa-120">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="a02fa-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a02fa-121">此範例位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="a02fa-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
