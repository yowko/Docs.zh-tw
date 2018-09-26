---
title: NoPersistScope 活動
ms.date: 03/30/2017
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
ms.openlocfilehash: 6543756594b6734aec39bf22c5ab6215605341b1
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216198"
---
# <a name="nopersistscope-activity"></a><span data-ttu-id="cf215-102">NoPersistScope 活動</span><span class="sxs-lookup"><span data-stu-id="cf215-102">NoPersistScope Activity</span></span>
<span data-ttu-id="cf215-103">這個範例示範如何在工作流程中操作不可序列化和可處置的狀態。</span><span class="sxs-lookup"><span data-stu-id="cf215-103">This sample shows how to manipulate a non-serializable and disposable state within a workflow.</span></span> <span data-ttu-id="cf215-104">重要的是工作流程不會嘗試保存不可序列化的狀態，同樣重要的是可處置的物件在工作流程中使用之後一定要清除。</span><span class="sxs-lookup"><span data-stu-id="cf215-104">It is important that workflows do not attempt to persist non-serializable state and it is also important for disposable objects to be cleaned up after they are used in workflow.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="cf215-105">示範</span><span class="sxs-lookup"><span data-stu-id="cf215-105">Demonstrates</span></span>  
 <span data-ttu-id="cf215-106">`NoPersistScope` 自訂活動和設計工具。</span><span class="sxs-lookup"><span data-stu-id="cf215-106">`NoPersistScope` custom activity and designer.</span></span>  
  
## <a name="using-the-nopersistzone-activity"></a><span data-ttu-id="cf215-107">使用 NoPersistZone 活動</span><span class="sxs-lookup"><span data-stu-id="cf215-107">Using the NoPersistZone activity</span></span>  
 <span data-ttu-id="cf215-108">當範例工作流程執行時，名為 `CreateTextWriter` 的自訂活動會建立 <xref:System.IO.TextWriter> 型別的物件，並將它儲存在工作流程變數中。</span><span class="sxs-lookup"><span data-stu-id="cf215-108">When the sample workflow runs, a custom activity called `CreateTextWriter` creates an object of type <xref:System.IO.TextWriter> and saves it into a workflow variable.</span></span> <span data-ttu-id="cf215-109"><xref:System.IO.TextWriter> 是 <xref:System.IDisposable> 物件。</span><span class="sxs-lookup"><span data-stu-id="cf215-109"><xref:System.IO.TextWriter> is an <xref:System.IDisposable> object.</span></span> <span data-ttu-id="cf215-110">這個 <xref:System.IO.TextWriter> 設定會在執行範例的目錄中寫入至 'out.txt' 檔案，<xref:System.Activities.Statements.WriteLine> 活動在回應您於主控台輸入的任何文字時使用這個物件。</span><span class="sxs-lookup"><span data-stu-id="cf215-110">This <xref:System.IO.TextWriter>, which is configured to write to a file named ‘out.txt’ in the directory in which the sample runs, is used by a <xref:System.Activities.Statements.WriteLine> activity as it echoes any text you type in at the console.</span></span>  
  
 <span data-ttu-id="cf215-111">回應邏輯執行於 `NoPersistScope` 活動中 (其程式碼也是這個範例的一部分)，可防止工作流程保存。</span><span class="sxs-lookup"><span data-stu-id="cf215-111">The echo logic runs within a `NoPersistScope` activity (the code for which is also part of this sample), which prevents the workflow from being persisted.</span></span> <span data-ttu-id="cf215-112">如果您輸入 contosovm`unload`在主控台中，主機會嘗試保存工作流程執行個體，但這項作業會逾時，因為工作流程保留在`NoPersistScope`。</span><span class="sxs-lookup"><span data-stu-id="cf215-112">If you type in `unload` at the console, the host attempts to persist the workflow instance but this operation times out because the workflow remains within a `NoPersistScope`.</span></span> <span data-ttu-id="cf215-113">當工作流程完成使用 `Dispose` 時，工作流程也會利用名為 <xref:System.IO.TextWriter> 的自訂活動來處置此物件。</span><span class="sxs-lookup"><span data-stu-id="cf215-113">The workflow also utilizes a custom activity called `Dispose` to dispose the <xref:System.IO.TextWriter> object when the workflow is finished using it.</span></span> <span data-ttu-id="cf215-114">`Dispose` 活動是放置在宣告 <xref:System.Activities.Statements.TryCatch.Finally%2A> 變數之 <xref:System.Activities.Statements.TryCatch> 活動的 <xref:System.IO.TextWriter> 區塊中，以確保 Try 區塊執行期間即使發生例外狀況，也會執行此活動。</span><span class="sxs-lookup"><span data-stu-id="cf215-114">The `Dispose` activity is placed within the <xref:System.Activities.Statements.TryCatch.Finally%2A> block of the <xref:System.Activities.Statements.TryCatch> activity in which the <xref:System.IO.TextWriter> variable is declared, to ensure that it runs even if an exception should occur during execution of the Try block.</span></span>  
  
 <span data-ttu-id="cf215-115">您可以輸入`exit`以完成工作流程執行個體並結束程式。</span><span class="sxs-lookup"><span data-stu-id="cf215-115">You can type in `exit` to complete the workflow instance and exit the program.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="cf215-116">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="cf215-116">To run the sample</span></span>  
  
1.  <span data-ttu-id="cf215-117">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 NoPersistZone.sln 方案。</span><span class="sxs-lookup"><span data-stu-id="cf215-117">Open the NoPersistZone.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="cf215-118">若要建置方案，請按 CTRL + SHIFT + B 或選取**建置方案**從**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="cf215-118">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="cf215-119">成功組建後，按 F5 或選取**開始偵錯**從**偵錯**功能表或者，您可以按 CTRL + F5 或選取**啟動但不偵錯**從**偵錯**執行，而不偵錯 功能表。</span><span class="sxs-lookup"><span data-stu-id="cf215-119">Once the build has succeeded, press F5 or select **Start Debugging** from the **Debug** menu alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="cf215-120">若要清除 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="cf215-120">To cleanup (optional)</span></span>  
  
1.  <span data-ttu-id="cf215-121">若要移除 SQL 執行個體存放區，請執行 Cleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="cf215-121">To remove the SQL Instance Store, run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cf215-122">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="cf215-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cf215-123">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="cf215-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cf215-124">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="cf215-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cf215-125">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="cf215-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`