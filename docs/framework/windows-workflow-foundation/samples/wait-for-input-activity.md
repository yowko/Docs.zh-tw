---
title: "等候輸入活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d58c344e-9ee8-4ce2-b199-75b3fe45237f
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 145a71ff7d1ca07112ab91aa46ec4efb10429713
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="wait-for-input-activity"></a><span data-ttu-id="9c721-102">等候輸入活動</span><span class="sxs-lookup"><span data-stu-id="9c721-102">Wait For Input Activity</span></span>
<span data-ttu-id="9c721-103">此範例示範如何在工作流程中建立具名書籤。</span><span class="sxs-lookup"><span data-stu-id="9c721-103">This sample demonstrates how to create named bookmarks in a workflow.</span></span> [!INCLUDE[wf](../../../../includes/wf-md.md)]<span data-ttu-id="9c721-104"> 不提供用於以宣告式建立書籤的活動。</span><span class="sxs-lookup"><span data-stu-id="9c721-104"> does not provide an activity for declarative bookmark creation.</span></span> <span data-ttu-id="9c721-105">因此，當您想要在工作流程中建立書籤時，您必須撰寫可建立書籤的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="9c721-105">Therefore, when you want to create a bookmark in your workflow, you must write a custom activity that creates it.</span></span> <span data-ttu-id="9c721-106">此範例中定義的 `WaitForInput` 活動會提供這個功能，所以使用者可在工作流程中以宣告方式建立書籤。</span><span class="sxs-lookup"><span data-stu-id="9c721-106">The `WaitForInput` activity defined in this sample provides this functionality, so that users can create bookmarks declaratively within a workflow.</span></span>  
  
## <a name="projects-in-this-sample"></a><span data-ttu-id="9c721-107">這個範例中的專案</span><span class="sxs-lookup"><span data-stu-id="9c721-107">Projects in this sample</span></span>  
  
|<span data-ttu-id="9c721-108">**專案名稱**</span><span class="sxs-lookup"><span data-stu-id="9c721-108">**Project Name**</span></span>|<span data-ttu-id="9c721-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="9c721-109">**Description**</span></span>|<span data-ttu-id="9c721-110">**主要檔案**</span><span class="sxs-lookup"><span data-stu-id="9c721-110">**Main Files**</span></span>|  
|-|-|-|  
|<span data-ttu-id="9c721-111">WaitForInput</span><span class="sxs-lookup"><span data-stu-id="9c721-111">WaitForInput</span></span>|<span data-ttu-id="9c721-112">包含 `WaitForInput` 活動和其設計工具</span><span class="sxs-lookup"><span data-stu-id="9c721-112">Contains `WaitForInput` activity and its designer</span></span>|<span data-ttu-id="9c721-113">WaitForInput.cs</span><span class="sxs-lookup"><span data-stu-id="9c721-113">WaitForInput.cs</span></span><br /><br /> <span data-ttu-id="9c721-114">`WaitForInput` 活動定義。</span><span class="sxs-lookup"><span data-stu-id="9c721-114">`WaitForInput` activity definition.</span></span>|  
|||<span data-ttu-id="9c721-115">WaitForInputDesigner.xaml</span><span class="sxs-lookup"><span data-stu-id="9c721-115">WaitForInputDesigner.xaml</span></span><br /><br /> <span data-ttu-id="9c721-116">`WaitForInput` 活動的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="9c721-116">Custom designer for the `WaitForInput` activity.</span></span>|  
|||<span data-ttu-id="9c721-117">TypeToFirstGenericArgumentConverter.cs</span><span class="sxs-lookup"><span data-stu-id="9c721-117">TypeToFirstGenericArgumentConverter.cs</span></span><br /><br /> <span data-ttu-id="9c721-118">WPF 型別轉換子，用來在設計工具內更新活動的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="9c721-118">WPF type converter used to update the generic type of the activity in the designer.</span></span>|  
|<span data-ttu-id="9c721-119">WaitForInputTestClient</span><span class="sxs-lookup"><span data-stu-id="9c721-119">WaitForInputTestClient</span></span>|<span data-ttu-id="9c721-120">範例用戶端應用程式，可透過工作流程設計工具來設定及執行使用幾個 WaitForInput 活動的工作流程。</span><span class="sxs-lookup"><span data-stu-id="9c721-120">Sample client application that configures and runs a workflow using several WaitForInput activities using the workflow designer.</span></span>|<span data-ttu-id="9c721-121">Sequence1.xaml</span><span class="sxs-lookup"><span data-stu-id="9c721-121">Sequence1.xaml</span></span><br /><br /> <span data-ttu-id="9c721-122">使用 `WaitForInput` 活動的循序工作流程。</span><span class="sxs-lookup"><span data-stu-id="9c721-122">A sequential workflow that uses the `WaitForInput` activity.</span></span>|  
|||<span data-ttu-id="9c721-123">Program.cs</span><span class="sxs-lookup"><span data-stu-id="9c721-123">Program.cs</span></span><br /><br /> <span data-ttu-id="9c721-124">執行 Sequence1.xaml 中定義的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="9c721-124">Runs an instance of the workflow defined in Sequence1.xaml.</span></span>|  
  
## <a name="waitforinput-activity"></a><span data-ttu-id="9c721-125">WaitForInput 活動</span><span class="sxs-lookup"><span data-stu-id="9c721-125">WaitForInput Activity</span></span>  
 <span data-ttu-id="9c721-126">`WaitForInput` 活動會在工作流程中建立具名的書籤。</span><span class="sxs-lookup"><span data-stu-id="9c721-126">The `WaitForInput` activity creates a named bookmark in a workflow.</span></span> <span data-ttu-id="9c721-127">此書籤會等候信號，並接收其設定之型別的資料。</span><span class="sxs-lookup"><span data-stu-id="9c721-127">The bookmark waits for a signal and receives data of its configured type.</span></span> <span data-ttu-id="9c721-128">當書籤繼續之後，傳入工作流程的資料可透過 `Result` 屬性來使用。</span><span class="sxs-lookup"><span data-stu-id="9c721-128">After the bookmark is resumed the data passed into the workflow is available through the `Result` property.</span></span>  
  
 <span data-ttu-id="9c721-129">`WaitForInput` 活動衍生自 <xref:System.Activities.NativeActivity> 類別，因為它必須建立只能透過 <xref:System.Activities.NativeActivityContext> 類別存取的書籤。</span><span class="sxs-lookup"><span data-stu-id="9c721-129">The `WaitForInput` activity derives from the <xref:System.Activities.NativeActivity> class because it must create bookmarks, which are only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>  
  
 <span data-ttu-id="9c721-130">此活動有三個套用的屬性，可繫結設計工具、加入可以更新的泛型引數功能，以及將預設泛型型別設定為字串。</span><span class="sxs-lookup"><span data-stu-id="9c721-130">The activity has three attributes applied to it for binding a designer, adding the generic argument feature that can be updated, and setting the default generic type to string.</span></span> <span data-ttu-id="9c721-131">此活動也有列於下表的引數。</span><span class="sxs-lookup"><span data-stu-id="9c721-131">The activity also has the arguments  listed in the following table.</span></span>  
  
|<span data-ttu-id="9c721-132">**Name**</span><span class="sxs-lookup"><span data-stu-id="9c721-132">**Name**</span></span>|<span data-ttu-id="9c721-133">**Type**</span><span class="sxs-lookup"><span data-stu-id="9c721-133">**Type**</span></span>|<span data-ttu-id="9c721-134">**說明**</span><span class="sxs-lookup"><span data-stu-id="9c721-134">**Description**</span></span>|  
|-|-|-|  
|<span data-ttu-id="9c721-135">TResult</span><span class="sxs-lookup"><span data-stu-id="9c721-135">TResult</span></span>|<span data-ttu-id="9c721-136">泛型引數 (TResult)</span><span class="sxs-lookup"><span data-stu-id="9c721-136">Generic argument (TResult)</span></span>|<span data-ttu-id="9c721-137">書籤的型別。</span><span class="sxs-lookup"><span data-stu-id="9c721-137">Type of the bookmark.</span></span> <span data-ttu-id="9c721-138">這是當書籤繼續時要傳遞給書籤的資料型別。</span><span class="sxs-lookup"><span data-stu-id="9c721-138">This is the type of the data to be passed to the bookmark when resumed.</span></span>|  
|<span data-ttu-id="9c721-139">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="9c721-139">BookmarkName</span></span>|<span data-ttu-id="9c721-140">InArgument\<字串 ></span><span class="sxs-lookup"><span data-stu-id="9c721-140">InArgument\<string></span></span>|<span data-ttu-id="9c721-141">書籤的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c721-141">Name of the bookmark.</span></span>|  
|<span data-ttu-id="9c721-142">結果</span><span class="sxs-lookup"><span data-stu-id="9c721-142">Result</span></span>|<span data-ttu-id="9c721-143">InArgument\<TResult ></span><span class="sxs-lookup"><span data-stu-id="9c721-143">InArgument\<TResult></span></span>|<span data-ttu-id="9c721-144">當書籤繼續時傳遞給活動的資料。</span><span class="sxs-lookup"><span data-stu-id="9c721-144">Data passed to the activity when the bookmark is resumed.</span></span>|  
  
## <a name="waitforinput-activity-designer"></a><span data-ttu-id="9c721-145">WaitForInput 活動設計工具</span><span class="sxs-lookup"><span data-stu-id="9c721-145">WaitForInput activity designer</span></span>  
 <span data-ttu-id="9c721-146">`WaitForInput` 活動設計工具會在 WaitForInputDesigner.xaml 檔案中實作。</span><span class="sxs-lookup"><span data-stu-id="9c721-146">The `WaitForInput` activity designer is implemented in the WaitForInputDesigner.xaml file.</span></span> <span data-ttu-id="9c721-147">`WaitForInput` 活動和它的設計工具會包含在相同的組件中。</span><span class="sxs-lookup"><span data-stu-id="9c721-147">The `WaitForInput` activity and its designer are included in the same assembly.</span></span> <span data-ttu-id="9c721-148">下圖顯示工具箱中某個分類的 `WaitForInput` 活動，該分類的名稱與組件相同。</span><span class="sxs-lookup"><span data-stu-id="9c721-148">The following graphic shows the `WaitForInput` activity in the toolbox within a category that has the same name as the assembly.</span></span>  
  
 <span data-ttu-id="9c721-149">![WaitForInput 工具箱螢幕擷取畫面](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputtoolbox.jpg "WaitForInputToolbox")</span><span class="sxs-lookup"><span data-stu-id="9c721-149">![WaitForInput toolbox screenshot](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputtoolbox.jpg "WaitForInputToolbox")</span></span>  
  
 <span data-ttu-id="9c721-150">下圖顯示 `WaitForInput` 設計工具。</span><span class="sxs-lookup"><span data-stu-id="9c721-150">The following graphic shows the `WaitForInput` designer.</span></span> <span data-ttu-id="9c721-151">因為 `WaitForInput` 活動非常基本，所以設計工具允許直接在設計工具介面中設定它的所有引數。</span><span class="sxs-lookup"><span data-stu-id="9c721-151">Because, the `WaitForInput` activity is very basic, the designer allows setting all its arguments directly in the designer surface.</span></span>  
  
 <span data-ttu-id="9c721-152">![WaitForInput 活動設計工具](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputdesigner.jpg "WaitForInputDesigner")</span><span class="sxs-lookup"><span data-stu-id="9c721-152">![WaitForInput Activity Designer](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputdesigner.jpg "WaitForInputDesigner")</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="9c721-153">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="9c721-153">To use this sample</span></span>  
  
1.  <span data-ttu-id="9c721-154">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 WaitForInput.sln 檔。</span><span class="sxs-lookup"><span data-stu-id="9c721-154">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WaitForInput.sln file.</span></span>  
  
2.  <span data-ttu-id="9c721-155">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="9c721-155">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="9c721-156">若要啟動範例而不執行偵錯，請按 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="9c721-156">To start the sample without debugging, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9c721-157">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="9c721-157">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9c721-158">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="9c721-158">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9c721-159">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="9c721-159">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9c721-160">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="9c721-160">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\WaitForInput`