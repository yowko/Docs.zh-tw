---
title: "Windows 工作流程架構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed13d7885cb8abd760aed6bd5812cb8b7c75bc02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="windows-workflow-architecture"></a><span data-ttu-id="23c38-102">Windows 工作流程架構</span><span class="sxs-lookup"><span data-stu-id="23c38-102">Windows Workflow Architecture</span></span>
[!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="23c38-103"> 會引發開發互動式長期執行應用程式的抽象層級。</span><span class="sxs-lookup"><span data-stu-id="23c38-103"> raises the abstraction level for developing interactive long-running applications.</span></span> <span data-ttu-id="23c38-104">工作的單元會封裝為活動。</span><span class="sxs-lookup"><span data-stu-id="23c38-104">Units of work are encapsulated as activities.</span></span> <span data-ttu-id="23c38-105">活動會在環境中執行，該環境會為流程控制、例外狀況處理、錯誤傳播、狀態資料保存、從記憶體載入及卸載處理中的工作流程、追蹤，以及交易流程提供機能。</span><span class="sxs-lookup"><span data-stu-id="23c38-105">Activities run in an environment that provides facilities for flow control, exception handling, fault propagation, persistence of state data, loading and unloading of in-progress workflows from memory, tracking, and transaction flow.</span></span>  
  
## <a name="activity-architecture"></a><span data-ttu-id="23c38-106">活動架構</span><span class="sxs-lookup"><span data-stu-id="23c38-106">Activity Architecture</span></span>  
 <span data-ttu-id="23c38-107">活動會開發成衍生自 <xref:System.Activities.Activity>、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 或 <xref:System.Activities.NativeActivity> 的 CLR 型別，或者其傳回 <xref:System.Activities.Activity%601>、<xref:System.Activities.CodeActivity%601>、<xref:System.Activities.AsyncCodeActivity%601> 或 <xref:System.Activities.NativeActivity%601> 等值的變數。</span><span class="sxs-lookup"><span data-stu-id="23c38-107">Activities are developed as CLR types that derive from either <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>, or their variants that return a value, <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601>, or <xref:System.Activities.NativeActivity%601>.</span></span> <span data-ttu-id="23c38-108">開發衍生自 <xref:System.Activities.Activity> 的活動，可讓使用者組合預先存在的活動，以快速建立在工作流程環境中執行的工作單位。</span><span class="sxs-lookup"><span data-stu-id="23c38-108">Developing activities that derive from <xref:System.Activities.Activity> allows the user to assemble pre-existing activities to quickly create units of work that execute in the workflow environment.</span></span> <span data-ttu-id="23c38-109">另一方面，<xref:System.Activities.CodeActivity> 則可讓使用者能夠使用主要用於存取活動引數的 <xref:System.Activities.CodeActivityContext>，在 Managed 程式碼中撰寫執行邏輯。</span><span class="sxs-lookup"><span data-stu-id="23c38-109"><xref:System.Activities.CodeActivity>, on the other hand, enables execution logic to be authored in managed code using <xref:System.Activities.CodeActivityContext> primarily for access to activity arguments.</span></span> <span data-ttu-id="23c38-110"><xref:System.Activities.AsyncCodeActivity> 類似 <xref:System.Activities.CodeActivity>，但可用來實作非同步工作。</span><span class="sxs-lookup"><span data-stu-id="23c38-110"><xref:System.Activities.AsyncCodeActivity> is similar to <xref:System.Activities.CodeActivity> except that it can be used to implement asynchronous tasks.</span></span> <span data-ttu-id="23c38-111">開發衍生自 <xref:System.Activities.NativeActivity> 的活動，可讓使用者透過 <xref:System.Activities.NativeActivityContext> 來存取執行階段，以進行排定子系、建立書籤、叫用非同步工作、註冊交易等功能。</span><span class="sxs-lookup"><span data-stu-id="23c38-111">Developing activities that derive from <xref:System.Activities.NativeActivity> allows users to access the runtime through the <xref:System.Activities.NativeActivityContext> for functionality like scheduling children, creating bookmarks, invoking asynchronous work, registering transactions, and more.</span></span>  
  
 <span data-ttu-id="23c38-112">撰寫衍生自 <xref:System.Activities.Activity> 的活動是宣告式的，而且可在 XAML 中撰寫這些活動。</span><span class="sxs-lookup"><span data-stu-id="23c38-112">Authoring activities that derive from <xref:System.Activities.Activity> is declarative and these activities can be authored in XAML.</span></span> <span data-ttu-id="23c38-113">在下列範例中，會使用其他活動做為執行主體來建立稱為 `Prompt` 的活動。</span><span class="sxs-lookup"><span data-stu-id="23c38-113">In the following example, an activity called `Prompt` is created using other activities for the execution body.</span></span>  
  
```xml  
<Activity x:Class='Prompt'  
  xmlns:x='http://schemas.microsoft.com/winfx/2006/xaml'  
    xmlns:z='http://schemas.microsoft.com/netfx/2008/xaml/schema'  
xmlns:my='clr-namespace:XAMLActivityDefinition;assembly=XAMLActivityDefinition'  
xmlns:s="clr-namespace:System;assembly=mscorlib"  
xmlns="http://schemas.microsoft.com/2009/workflow">  
<z:SchemaType.Members>  
    <z:SchemaType.SchemaProperty Name='Text' Type=' InArgument(s:String)' />  
  <z:SchemaType.SchemaProperty Name='Response' Type='OutArgument(s:String)' />  
</z:SchemaType.Members>  
  <Sequence>  
    <my:WriteLine Text='[Text]' />  
    <my:ReadLine BookmarkName='r1' Result='[Response]' />  
  </Sequence>  
</Activity>  
```  
  
## <a name="activity-context"></a><span data-ttu-id="23c38-114">活動內容</span><span class="sxs-lookup"><span data-stu-id="23c38-114">Activity Context</span></span>  
 <span data-ttu-id="23c38-115"><xref:System.Activities.ActivityContext> 是活動作者的工作流程執行階段介面，可提供存取執行階段各種豐富的功能。</span><span class="sxs-lookup"><span data-stu-id="23c38-115">The <xref:System.Activities.ActivityContext> is the activity author's interface to the workflow runtime and provides access to the runtime's wealth of features.</span></span> <span data-ttu-id="23c38-116">下列範例會定義使用執行內容建立書籤的活動 (這種機制可讓活動在其執行中註冊持續點，以供傳遞資料至活動的主機繼續)。</span><span class="sxs-lookup"><span data-stu-id="23c38-116">In the following example, an activity is defined that uses the execution context to create a bookmark (the mechanism that allows an activity to register a continuation point in its execution that can be resumed by a host passing data into the activity).</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a><span data-ttu-id="23c38-117">活動開發週期</span><span class="sxs-lookup"><span data-stu-id="23c38-117">Activity Life Cycle</span></span>  
 <span data-ttu-id="23c38-118">活動的執行個體會在 <xref:System.Activities.ActivityInstanceState.Executing> 狀態中啟動。</span><span class="sxs-lookup"><span data-stu-id="23c38-118">An instance of an activity starts out in the <xref:System.Activities.ActivityInstanceState.Executing> state.</span></span> <span data-ttu-id="23c38-119">除非發生例外狀況，否則活動的執行個體會維持在這個狀態中，直到所有子活動皆執行完畢，而且其他所有暫止中的工作 (例如 <xref:System.Activities.Bookmark> 物件) 皆已完成，此時，該執行個體就會轉換成 <xref:System.Activities.ActivityInstanceState.Closed> 狀態。</span><span class="sxs-lookup"><span data-stu-id="23c38-119">Unless exceptions are encountered, it remains in this state until all child activities are finished executing and any other pending work (<xref:System.Activities.Bookmark> objects, for instance) is completed, at which point it transitions to the <xref:System.Activities.ActivityInstanceState.Closed> state.</span></span> <span data-ttu-id="23c38-120">活動執行個體的父系可以要求子系取消，如果子系可以取消，則會在 <xref:System.Activities.ActivityInstanceState.Canceled> 狀態下完成。</span><span class="sxs-lookup"><span data-stu-id="23c38-120">The parent of an activity instance can request a child to cancel; if the child is able to be canceled it completes in the <xref:System.Activities.ActivityInstanceState.Canceled> state.</span></span> <span data-ttu-id="23c38-121">如果在執行期間擲回例外狀況，執行階段會將活動設為 <xref:System.Activities.ActivityInstanceState.Faulted> 狀態，並將例外狀況向上傳播至活動的父鏈結。</span><span class="sxs-lookup"><span data-stu-id="23c38-121">If an exception is thrown during execution, the runtime puts the activity into the <xref:System.Activities.ActivityInstanceState.Faulted> state and propagates the exception up the parent chain of activities.</span></span> <span data-ttu-id="23c38-122">以下是活動的三種完成狀態：</span><span class="sxs-lookup"><span data-stu-id="23c38-122">Following are the three completion states of an activity:</span></span>  
  
-   <span data-ttu-id="23c38-123">**關閉：**活動已完成其工作並結束。</span><span class="sxs-lookup"><span data-stu-id="23c38-123">**Closed:** The activity has completed its work and exited.</span></span>  
  
-   <span data-ttu-id="23c38-124">**已取消：**活動已正常放棄其工作並結束。</span><span class="sxs-lookup"><span data-stu-id="23c38-124">**Canceled:** The activity has gracefully abandoned its work and exited.</span></span> <span data-ttu-id="23c38-125">進入此狀態時，不會明確地復原工作。</span><span class="sxs-lookup"><span data-stu-id="23c38-125">Work is not explicitly rolled back when this state is entered.</span></span>  
  
-   <span data-ttu-id="23c38-126">**發生錯誤：**活動而發生錯誤，並已結束而不會完成其工作。</span><span class="sxs-lookup"><span data-stu-id="23c38-126">**Faulted:** The activity has encountered an error and has exited without completing its work.</span></span>  
  
 <span data-ttu-id="23c38-127">當活動被保存或卸載時，會繼續處於 <xref:System.Activities.ActivityInstanceState.Executing> 狀態。</span><span class="sxs-lookup"><span data-stu-id="23c38-127">Activities remain in the <xref:System.Activities.ActivityInstanceState.Executing> state when they are persisted or unloaded.</span></span>
