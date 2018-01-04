---
title: "使用編輯範圍"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6f20ff0577e43106886f5910b8f6a69578d1b3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-editing-scope"></a><span data-ttu-id="18632-102">使用編輯範圍</span><span class="sxs-lookup"><span data-stu-id="18632-102">Using Editing Scope</span></span>
<span data-ttu-id="18632-103">這個範例示範如何批次處理一組變更，以便在單一不可部分完成的單位中復原這些變更。</span><span class="sxs-lookup"><span data-stu-id="18632-103">This sample demonstrates how to batch a set of changes so that they can be undone in a single atomic unit.</span></span> <span data-ttu-id="18632-104">根據預設，活動設計工具作者所執行的動作會自動整合至復原/取消復原系統。</span><span class="sxs-lookup"><span data-stu-id="18632-104">By default, the actions taken by an activity designer author are automatically integrated into the Undo/Redo system.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="18632-105">示範</span><span class="sxs-lookup"><span data-stu-id="18632-105">Demonstrates</span></span>  
 <span data-ttu-id="18632-106">編輯範圍以及恢復與重做。</span><span class="sxs-lookup"><span data-stu-id="18632-106">Editing scope and Undo and Redo.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="18632-107">討論</span><span class="sxs-lookup"><span data-stu-id="18632-107">Discussion</span></span>  
 <span data-ttu-id="18632-108">這個範例示範如何在單一工作單位中批次處理對 <xref:System.Activities.Presentation.Model.ModelItem> 樹狀結構的一組變更。</span><span class="sxs-lookup"><span data-stu-id="18632-108">This sample demonstrates how to batch a set of changes to the <xref:System.Activities.Presentation.Model.ModelItem> tree within a single unit of work.</span></span> <span data-ttu-id="18632-109">請注意，從 WPF 設計工具直接繫結至 <xref:System.Activities.Presentation.Model.ModelItem> 值時，系統會自動套用變更。</span><span class="sxs-lookup"><span data-stu-id="18632-109">Note that when binding to <xref:System.Activities.Presentation.Model.ModelItem> values directly from a WPF designer, changes are applied automatically.</span></span> <span data-ttu-id="18632-110">這個範例示範當透過命令式程式碼進行多個要批次處理的變更 (而不是單一變更) 時，所必須完成的工作。</span><span class="sxs-lookup"><span data-stu-id="18632-110">This sample demonstrates what must be done when multiple changes to be batched are being made through imperative code, rather than a single change.</span></span>  
  
 <span data-ttu-id="18632-111">在這個範例中，會加入三個活動。</span><span class="sxs-lookup"><span data-stu-id="18632-111">In this sample, three activities are added.</span></span> <span data-ttu-id="18632-112">當編輯開始時，會呼叫 <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> 執行個體上的 <xref:System.Activities.Presentation.Model.ModelItem>。</span><span class="sxs-lookup"><span data-stu-id="18632-112">When editing begins, <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> is called on an instance of <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="18632-113">在此編輯範圍內，對 <xref:System.Activities.Presentation.Model.ModelItem> 樹狀結構的變更會批次處理。</span><span class="sxs-lookup"><span data-stu-id="18632-113">Changes made to the <xref:System.Activities.Presentation.Model.ModelItem> tree within this editing scope are batched.</span></span> <span data-ttu-id="18632-114"><xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> 命令會傳回可用於控制此執行個體的 <xref:System.Activities.Presentation.Model.EditingScope>。</span><span class="sxs-lookup"><span data-stu-id="18632-114">The <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> command returns an <xref:System.Activities.Presentation.Model.EditingScope>, which can be used to control this instance.</span></span> <span data-ttu-id="18632-115">可呼叫 <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> 或 <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A>，以認可或還原編輯範圍。</span><span class="sxs-lookup"><span data-stu-id="18632-115">Either <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> or <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> can be called to either commit or revert the editing scope.</span></span>  
  
 <span data-ttu-id="18632-116">您也可以巢狀處理 <xref:System.Activities.Presentation.Model.EditingScope> 物件，允許在更大的編輯範圍內追蹤多組變更，以及個別控制這些變更。</span><span class="sxs-lookup"><span data-stu-id="18632-116">You can also nest <xref:System.Activities.Presentation.Model.EditingScope> objects, which allows for multiple sets of changes to be tracked as part of a larger editing scope and can be controlled individually.</span></span> <span data-ttu-id="18632-117">可能使用此功能的狀況是當來自多個對話方塊的變更必須分別認可或還原，而所有變更是以單一不可部分完成作業的方式來處理。</span><span class="sxs-lookup"><span data-stu-id="18632-117">A scenario that may use this feature would be when changes from multiple dialogs must be committed or reverted separately, with all changes being treated as a single atomic operation.</span></span> <span data-ttu-id="18632-118">在這個範例中，編輯範圍是使用 <xref:System.Collections.ObjectModel.ObservableCollection%601> 類型的 <xref:System.Activities.Presentation.Model.ModelEditingScope> 進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="18632-118">In this sample, the editing scopes are stacked using an <xref:System.Collections.ObjectModel.ObservableCollection%601> of type <xref:System.Activities.Presentation.Model.ModelEditingScope>.</span></span> <span data-ttu-id="18632-119">使用了 <xref:System.Collections.ObjectModel.ObservableCollection%601>，如此，可以在設計介面上觀察巢狀深度。</span><span class="sxs-lookup"><span data-stu-id="18632-119">The <xref:System.Collections.ObjectModel.ObservableCollection%601> is used so that the depth of the nesting can be observed on the designer surface.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="18632-120">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="18632-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="18632-121">建置及執行範例，然後使用左側按鈕修改工作流程。</span><span class="sxs-lookup"><span data-stu-id="18632-121">Build and run the sample, and then use the buttons on the left to modify the workflow.</span></span>  
  
2.  <span data-ttu-id="18632-122">按一下**開啟編輯範圍**。</span><span class="sxs-lookup"><span data-stu-id="18632-122">Click **Open Editing Scope**.</span></span>  
  
    1.  <span data-ttu-id="18632-123">這個命令會呼叫 <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>，用於建立編輯範圍並將其發送至編輯堆疊上。</span><span class="sxs-lookup"><span data-stu-id="18632-123">This command calls <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> that creates an editing scope and pushes it onto the editing stack.</span></span>  
  
    2.  <span data-ttu-id="18632-124">三個活動接著會加入至選取的 <xref:System.Activities.Presentation.Model.ModelItem>。</span><span class="sxs-lookup"><span data-stu-id="18632-124">Three activities are then added to the selected <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="18632-125">請注意，如果編輯範圍尚未使用 <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> 開啟，三個新活動會出現在設計工具畫布上。</span><span class="sxs-lookup"><span data-stu-id="18632-125">Note that if the editing scope had not been opened with <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, three new activities would appear on the designer canvas.</span></span> <span data-ttu-id="18632-126">因為這項作業在 <xref:System.Activities.Presentation.Model.EditingScope> 中仍為暫止，所以設計工具尚未更新。</span><span class="sxs-lookup"><span data-stu-id="18632-126">Because this operation is still pending within the <xref:System.Activities.Presentation.Model.EditingScope>, the designer is not yet updated.</span></span>  
  
3.  <span data-ttu-id="18632-127">按**關閉編輯範圍**認可編輯範圍。</span><span class="sxs-lookup"><span data-stu-id="18632-127">Press **Close Editing Scope** to commit the editing scope.</span></span> <span data-ttu-id="18632-128">三個活動隨即出現在設計工具中。</span><span class="sxs-lookup"><span data-stu-id="18632-128">Three activities appear in the designer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="18632-129">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="18632-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="18632-130">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="18632-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="18632-131">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="18632-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="18632-132">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="18632-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`
