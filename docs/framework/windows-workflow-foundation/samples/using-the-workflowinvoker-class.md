---
title: "使用 WorkflowInvoker 類別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8bb6c4049b56702c8fad226c20884ff581ec6203
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-workflowinvoker-class"></a><span data-ttu-id="14705-102">使用 WorkflowInvoker 類別</span><span class="sxs-lookup"><span data-stu-id="14705-102">Using the WorkflowInvoker Class</span></span>
<span data-ttu-id="14705-103">這個範例示範如何使用 <xref:System.Activities.WorkflowInvoker> 類別如同方法一般叫用活動。</span><span class="sxs-lookup"><span data-stu-id="14705-103">This sample demonstrates how to use the <xref:System.Activities.WorkflowInvoker> class to invoke an activity as if it were a method.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="14705-104">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="14705-104">Sample Details</span></span>  
 <span data-ttu-id="14705-105">使用 <xref:System.Activities.WorkflowInvoker> 類別是執行活動的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="14705-105">Using the <xref:System.Activities.WorkflowInvoker> class is the simplest way to execute an activity.</span></span> <span data-ttu-id="14705-106">其設計在於如同方法一般直接執行活動。</span><span class="sxs-lookup"><span data-stu-id="14705-106">It is designed for directly running an activity as if it were a method call.</span></span> <span data-ttu-id="14705-107">它是一個輕量型、高效能且易用的 API，可在活動的執行不需要其他裝載變化提供的控制項基礎結構的情況下使用。</span><span class="sxs-lookup"><span data-stu-id="14705-107">It is a lightweight, high-performing, easy to use API for use in scenarios where an activity’s execution does not require the control infrastructure provided by other hosting variations.</span></span>  
  
 <span data-ttu-id="14705-108">此範例會使用自訂活動衍生自<xref:System.Activities.CodeActivity%601>< Int32\>名為`Add`會加入兩個<xref:System.Activities.InArgument%601>，`X`和`Y`，並傳回`Result` <xref:System.Activities.OutArgument%601>。</span><span class="sxs-lookup"><span data-stu-id="14705-108">The sample uses a custom activity that derives from <xref:System.Activities.CodeActivity%601><Int32\> named `Add` that adds two <xref:System.Activities.InArgument%601>, `X` and `Y`, and returns a `Result`<xref:System.Activities.OutArgument%601>.</span></span> <span data-ttu-id="14705-109">(<xref:System.Activities.CodeActivity%601>\<T > 是衍生自<xref:System.Activities.Activity%601>< T\>，其具有<xref:System.Activities.OutArgument%601> \<T > 名為`Result`。)A `Dictionary`\<字串、 物件 > 用來將引數傳遞到透過叫用活動<xref:System.Activities.WorkflowInvoker>。</span><span class="sxs-lookup"><span data-stu-id="14705-109">(<xref:System.Activities.CodeActivity%601>\<T> derives from <xref:System.Activities.Activity%601><T\>, which has an <xref:System.Activities.OutArgument%601>\<T> named `Result`.) A `Dictionary`\<string, object> is used to pass arguments into an activity being invoked through <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="14705-110">字典的索引鍵會對應到所叫用活動上引數的名稱。</span><span class="sxs-lookup"><span data-stu-id="14705-110">The key of the dictionary corresponds to the name of an argument on the invoked activity.</span></span> <span data-ttu-id="14705-111">與特殊索引鍵相關聯的值會繫結至索引鍵識別的引數。</span><span class="sxs-lookup"><span data-stu-id="14705-111">The value associated with a particular key is bound to the argument identified by the key.</span></span>  
  
 <span data-ttu-id="14705-112">此範例會呼叫 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 並且傳遞包含 `X` 和 `Y` 之值的字典。</span><span class="sxs-lookup"><span data-stu-id="14705-112">The sample calls <xref:System.Activities.WorkflowInvoker.Invoke%2A> and passes a dictionary that contains values for `X` and `Y`.</span></span> <span data-ttu-id="14705-113"><xref:System.Activities.WorkflowInvoker> 類別會將這些值繫結至 `Add` 活動的引數、執行活動，並且傳回結果。</span><span class="sxs-lookup"><span data-stu-id="14705-113">The <xref:System.Activities.WorkflowInvoker> class binds these values to the `Add` activity’s arguments, executes the activity, and returns the result.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="14705-114">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="14705-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="14705-115">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 [Invoker.sln] 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="14705-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Invoker.sln solution file.</span></span>  
  
2.  <span data-ttu-id="14705-116">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="14705-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="14705-117">若要執行此方案，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="14705-117">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="14705-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="14705-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="14705-119">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="14705-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="14705-120">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="14705-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="14705-121">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="14705-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`