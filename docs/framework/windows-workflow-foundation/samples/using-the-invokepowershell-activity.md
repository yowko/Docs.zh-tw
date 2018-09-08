---
title: 使用 InvokePowerShell 活動
ms.date: 03/30/2017
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
ms.openlocfilehash: fa42cddd930b755e9938a02a137ee77ee273fad0
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137729"
---
# <a name="using-the-invokepowershell-activity"></a><span data-ttu-id="80081-102">使用 InvokePowerShell 活動</span><span class="sxs-lookup"><span data-stu-id="80081-102">Using the InvokePowerShell Activity</span></span>
<span data-ttu-id="80081-103">InvokePowerShell 範例示範如何使用 `InvokePowerShell` 活動叫用 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="80081-103">The InvokePowerShell sample demonstrates how to invoke Windows PowerShell commands using the `InvokePowerShell` activity.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="80081-104">示範</span><span class="sxs-lookup"><span data-stu-id="80081-104">Demonstrates</span></span>  
  
-   <span data-ttu-id="80081-105">Windows PowerShell 命令的簡單引動過程。</span><span class="sxs-lookup"><span data-stu-id="80081-105">Simple innovation of Windows PowerShell commands.</span></span>  
  
-   <span data-ttu-id="80081-106">從 Windows PowerShell 輸出管線擷取值，並將值儲存在工作流程變數中。</span><span class="sxs-lookup"><span data-stu-id="80081-106">Retrieve values from the Windows PowerShell output pipeline and store them in workflow variables.</span></span>  
  
-   <span data-ttu-id="80081-107">將資料當做執行命令的輸入管線傳遞至 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="80081-107">Pass data into windows PowerShell as input pipeline for an executing command.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="80081-108">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="80081-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="80081-109">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="80081-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="80081-110">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="80081-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="80081-111">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="80081-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a><span data-ttu-id="80081-112">討論</span><span class="sxs-lookup"><span data-stu-id="80081-112">Discussion</span></span>  
 <span data-ttu-id="80081-113">這個範例包含下列三個專案。</span><span class="sxs-lookup"><span data-stu-id="80081-113">This sample contains the following three projects.</span></span>  
  
|<span data-ttu-id="80081-114">專案名稱</span><span class="sxs-lookup"><span data-stu-id="80081-114">Project Name</span></span>|<span data-ttu-id="80081-115">描述</span><span class="sxs-lookup"><span data-stu-id="80081-115">Description</span></span>|<span data-ttu-id="80081-116">主要檔案</span><span class="sxs-lookup"><span data-stu-id="80081-116">Main Files</span></span>|  
|------------------|-----------------|----------------|  
|<span data-ttu-id="80081-117">CodedClient</span><span class="sxs-lookup"><span data-stu-id="80081-117">CodedClient</span></span>|<span data-ttu-id="80081-118">使用 PowerShell 活動的範例用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="80081-118">A sample client application that uses the PowerShell activity.</span></span>|<span data-ttu-id="80081-119">-   **Program.cs**： 以程式設計方式建立循序工作流程可呼叫 InvokePowerShell 活動。</span><span class="sxs-lookup"><span data-stu-id="80081-119">-   **Program.cs**: Programmatically creates a sequence-based workflow that calls the InvokePowerShell activity.</span></span>|  
|<span data-ttu-id="80081-120">DesignerClient</span><span class="sxs-lookup"><span data-stu-id="80081-120">DesignerClient</span></span>|<span data-ttu-id="80081-121">包含 `InvokePowerShell` 自訂活動和其他自訂活動在內的一組自訂活動，以及使用它們的工作流程。</span><span class="sxs-lookup"><span data-stu-id="80081-121">A set of custom activities that contain the `InvokePowerShell` custom activity and other miscellaneous custom activities, and a workflow that uses them.</span></span>|<ul><li><span data-ttu-id="80081-122">活動：</span><span class="sxs-lookup"><span data-stu-id="80081-122">Activities:</span></span><br /><br /> <ul><li><span data-ttu-id="80081-123">**PrintCollection.cs**： 協助程式活動列印至主控台的集合中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="80081-123">**PrintCollection.cs**: A helper activity that prints all the items in a collection to the console.</span></span></li><li><span data-ttu-id="80081-124">**ReadLine.cs**： 從主控台讀取輸入的協助程式活動。</span><span class="sxs-lookup"><span data-stu-id="80081-124">**ReadLine.cs**: A helper activity for reading input from the console.</span></span></li></ul></li><li><span data-ttu-id="80081-125">檔案系統：</span><span class="sxs-lookup"><span data-stu-id="80081-125">File System:</span></span><br /><br /> <ul><li><span data-ttu-id="80081-126">**Copy.xaml**： 將檔案複製的活動。</span><span class="sxs-lookup"><span data-stu-id="80081-126">**Copy.xaml**: An activity that copies a file.</span></span></li><li><span data-ttu-id="80081-127">**CreateFile.xaml**： 建立檔案的活動。</span><span class="sxs-lookup"><span data-stu-id="80081-127">**CreateFile.xaml**: An activity that creates a file.</span></span></li><li><span data-ttu-id="80081-128">**DeleteFile.xaml**： 刪除檔案活動。</span><span class="sxs-lookup"><span data-stu-id="80081-128">**DeleteFile.xaml**: An activity that deletes a file.</span></span></li><li><span data-ttu-id="80081-129">**MakeDir.xaml**： 建立目錄的活動。</span><span class="sxs-lookup"><span data-stu-id="80081-129">**MakeDir.xaml**: An activity that creates a directory.</span></span></li><li><span data-ttu-id="80081-130">**Move.xaml**： 移動檔案的活動。</span><span class="sxs-lookup"><span data-stu-id="80081-130">**Move.xaml**: An activity that moves a file.</span></span></li><li><span data-ttu-id="80081-131">**ReadFile.xaml**： 讀取的檔案，並傳回其內容的活動。</span><span class="sxs-lookup"><span data-stu-id="80081-131">**ReadFile.xaml**: An activity that reads a file and returns its contents.</span></span></li><li><span data-ttu-id="80081-132">**TestPath.xaml**： 測試路徑是否存在的活動。</span><span class="sxs-lookup"><span data-stu-id="80081-132">**TestPath.xaml**: An activity that tests for the existence of a path.</span></span></li></ul></li><li><span data-ttu-id="80081-133">處理序：</span><span class="sxs-lookup"><span data-stu-id="80081-133">Process:</span></span><br /><br /> <ul><li><span data-ttu-id="80081-134">**GetProcess.xaml**: 活動，取得執行程序的清單。</span><span class="sxs-lookup"><span data-stu-id="80081-134">**GetProcess.xaml**: An activity that gets a list of running processes.</span></span></li><li><span data-ttu-id="80081-135">**StopProcess.xaml**： 停止特定處理序的活動。</span><span class="sxs-lookup"><span data-stu-id="80081-135">**StopProcess.xaml**: An activity that stops a specific process.</span></span></li></ul></li><li><span data-ttu-id="80081-136">**Program.cs**： 呼叫 Sequence1 工作流程。</span><span class="sxs-lookup"><span data-stu-id="80081-136">**Program.cs**: Calls the Sequence1 workflow.</span></span></li><li><span data-ttu-id="80081-137">**Sequence1.xaml**： 循序工作流程。</span><span class="sxs-lookup"><span data-stu-id="80081-137">**Sequence1.xaml**: A sequence-based workflow.</span></span></li></ul>|  
|<span data-ttu-id="80081-138">PowerShell</span><span class="sxs-lookup"><span data-stu-id="80081-138">PowerShell</span></span>|<span data-ttu-id="80081-139">`InvokePowerShell` 活動及其相關聯的設計工具。</span><span class="sxs-lookup"><span data-stu-id="80081-139">The `InvokePowerShell` activity and its associated designers.</span></span>|<span data-ttu-id="80081-140">活動檔案</span><span class="sxs-lookup"><span data-stu-id="80081-140">Activity Files</span></span><br /><br /> <span data-ttu-id="80081-141">-   **ExecutePowerShell.cs**: 活動的主要執行邏輯。</span><span class="sxs-lookup"><span data-stu-id="80081-141">-   **ExecutePowerShell.cs**: The main execution logic of the activity.</span></span><br /><span data-ttu-id="80081-142">-   **InvokePowerShell.cs**： 主要執行邏輯，其中包含泛型 （傳回值） 版本和非泛型 （非傳回值） 版本的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="80081-142">-   **InvokePowerShell.cs**: The wrapper around the main execution logic, which contains a generic (return value) version and a non-generic (non-return value) version.</span></span> <span data-ttu-id="80081-143">這是活動的公用介面。</span><span class="sxs-lookup"><span data-stu-id="80081-143">This is the public interface for the activity.</span></span><br /><span data-ttu-id="80081-144">-   **NoPersistZone.cs**： 此活動可防止任何子活動保存。</span><span class="sxs-lookup"><span data-stu-id="80081-144">-   **NoPersistZone.cs**: This activity prevents any child activities from persisting.</span></span> <span data-ttu-id="80081-145">在 `InvokePowerShell` 活動實作中使用這個類別，以防止活動於執行中保存。</span><span class="sxs-lookup"><span data-stu-id="80081-145">This class is used within the `InvokePowerShell` activity implementation to prevent the activity from being persisted mid-execution.</span></span><br /><br /> <span data-ttu-id="80081-146">設計工具檔案：</span><span class="sxs-lookup"><span data-stu-id="80081-146">Designer files:</span></span><br /><br /> <span data-ttu-id="80081-147">1.**ArgumentDictionaryEditor.cs**: Windows 對話方塊，可讓使用者編輯的引數`InvokePowerShell`活動。</span><span class="sxs-lookup"><span data-stu-id="80081-147">1.  **ArgumentDictionaryEditor.cs**: A Windows dialog that allows the user to edit the arguments of the `InvokePowerShell` activity.</span></span><br /><span data-ttu-id="80081-148">2.**GenericInvokePowerShellDesigner.xaml**並**GenericInvokePowerShellDesigner.xaml.cs**： 定義的泛型出現`InvokePowerShell`中的活動[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="80081-148">2.  **GenericInvokePowerShellDesigner.xaml** and **GenericInvokePowerShellDesigner.xaml.cs**: Defines the appearance of the generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span><br /><span data-ttu-id="80081-149">3.**InvokePowerShellDesigner.xaml**並**InvokePowerShellDesigner.cs**： 定義非泛型的外觀`InvokePowerShell`中的活動[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="80081-149">3.  **InvokePowerShellDesigner.xaml** and **InvokePowerShellDesigner.cs**: Defines the appearance of the non-generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>|  
  
 <span data-ttu-id="80081-150">先討論用戶端專案，因為了解 PowerShell 活動的用法後，就會比較容易了解其內部功能。</span><span class="sxs-lookup"><span data-stu-id="80081-150">The client projects are discussed first, as it is easier to understand the internal functionality of the PowerShell activity once its use is understood.</span></span>  
  
## <a name="using-this-sample"></a><span data-ttu-id="80081-151">使用這個範例</span><span class="sxs-lookup"><span data-stu-id="80081-151">Using This Sample</span></span>  
 <span data-ttu-id="80081-152">下列章節描述如何使用範例中的三個專案。</span><span class="sxs-lookup"><span data-stu-id="80081-152">The following sections describe how to use the three projects in the sample.</span></span>  
  
### <a name="using-the-coded-client-project"></a><span data-ttu-id="80081-153">使用程式碼用戶端專案</span><span class="sxs-lookup"><span data-stu-id="80081-153">Using the Coded Client Project</span></span>  
 <span data-ttu-id="80081-154">範例用戶端以程式設計方式建立序列活動，其中包含使用 `InvokePowerShell` 活動的數個不同方法範例。</span><span class="sxs-lookup"><span data-stu-id="80081-154">The sample client programmatically creates a sequence activity, which contains examples of several different methods of using the `InvokePowerShell` activity.</span></span> <span data-ttu-id="80081-155">第一個引動過程會啟動記事本。</span><span class="sxs-lookup"><span data-stu-id="80081-155">The first invocation launches Notepad.</span></span>  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 <span data-ttu-id="80081-156">第二個引動過程取得本機電腦上執行中處理序的清單。</span><span class="sxs-lookup"><span data-stu-id="80081-156">The second invocation gets a list of the processes running on the local machine.</span></span>  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 <span data-ttu-id="80081-157">`Output` 是用來儲存命令輸出的變數。</span><span class="sxs-lookup"><span data-stu-id="80081-157">`Output` is the variable used to store the output of the command.</span></span>  
  
 <span data-ttu-id="80081-158">下一個呼叫示範如何針對 PowerShell 叫用的每個個別輸出執行後置處理步驟。</span><span class="sxs-lookup"><span data-stu-id="80081-158">The next call demonstrates how to run a post-processing step on each individual output of the PowerShell invocation.</span></span> <span data-ttu-id="80081-159">`InitializationAction` 設為函式，會輸出每個處理序的字串表示法。</span><span class="sxs-lookup"><span data-stu-id="80081-159">`InitializationAction` is set to the function that outputs a string representation for each process.</span></span> <span data-ttu-id="80081-160">由 `Output` 活動將這些字串的集合傳回到 `InvokePowerShell<string>` 變數中。</span><span class="sxs-lookup"><span data-stu-id="80081-160">The collection of these strings is returned in the `Output` variable by the `InvokePowerShell<string>` activity.</span></span>  
  
 <span data-ttu-id="80081-161">後續 `InvokePowerShell` 呼叫示範如何將資料傳遞至活動，並取得輸出和錯誤。</span><span class="sxs-lookup"><span data-stu-id="80081-161">The succeeding `InvokePowerShell` calls demonstrate passing data into the activity and getting outputs and errors out.</span></span>  
  
### <a name="using-the-designer-client-project"></a><span data-ttu-id="80081-162">使用設計工具用戶端專案</span><span class="sxs-lookup"><span data-stu-id="80081-162">Using the Designer Client Project</span></span>  
 <span data-ttu-id="80081-163">DesignerClient 專案包含一組自訂活動，其中大部分活動在建置中包含 `InvokePowerShell` 活動。</span><span class="sxs-lookup"><span data-stu-id="80081-163">The DesignerClient project consists of a set of custom activities, almost all of which are built containing the `InvokePowerShell` activity.</span></span> <span data-ttu-id="80081-164">大部分活動會呼叫非泛型 `InvokePowerShell` 活動版本，而且不預期接收傳回值。</span><span class="sxs-lookup"><span data-stu-id="80081-164">Most of the activities call the non-generic version of the `InvokePowerShell` activity, and do not expect a return value.</span></span> <span data-ttu-id="80081-165">其他活動會使用泛型 `InvokePowerShell` 活動版本，而且使用 `InitializationAction` 引數，對結果進行後置處理。</span><span class="sxs-lookup"><span data-stu-id="80081-165">Other activities use the generic version of the `InvokePowerShell` activity, and use the `InitializationAction` argument to post-process the results.</span></span>  
  
## <a name="using-the-powershell-project"></a><span data-ttu-id="80081-166">使用 PowerShell 專案</span><span class="sxs-lookup"><span data-stu-id="80081-166">Using the PowerShell Project</span></span>  
 <span data-ttu-id="80081-167">活動的主要動作發生於 `ExecutePowerShell` 類別。</span><span class="sxs-lookup"><span data-stu-id="80081-167">The main action of the activity takes place in the `ExecutePowerShell` class.</span></span> <span data-ttu-id="80081-168">因為 PowerShell 命令執行不應該封鎖主要工作流程執行緒，所以活動會繼承自 <xref:System.Activities.AsyncCodeActivity> 類別，建立成為非同步活動。</span><span class="sxs-lookup"><span data-stu-id="80081-168">Because the execution of PowerShell commands should not block the main workflow thread, the activity is created to be an asynchronous activity by inheriting from the <xref:System.Activities.AsyncCodeActivity> class.</span></span>  
  
 <span data-ttu-id="80081-169">工作流程執行階段呼叫 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> 方法，開始執行活動。</span><span class="sxs-lookup"><span data-stu-id="80081-169">The <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> method is called by the workflow runtime to begin running the activity.</span></span> <span data-ttu-id="80081-170">開始時先呼叫 PowerShell API 以建立 PowerShell 管線。</span><span class="sxs-lookup"><span data-stu-id="80081-170">It starts by calling PowerShell APIs to create a PowerShell pipeline.</span></span>  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 <span data-ttu-id="80081-171">接著建立 PowerShell 命令，並以參數和變數來擴展命令。</span><span class="sxs-lookup"><span data-stu-id="80081-171">It then creates a PowerShell command and populates it with parameters and variables.</span></span>  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 <span data-ttu-id="80081-172">透過管道傳入的輸入此時也會傳送至管線。</span><span class="sxs-lookup"><span data-stu-id="80081-172">The inputs piped in are also sent to the pipeline at this point.</span></span> <span data-ttu-id="80081-173">最後，將管線包裝在 `PipelineInvokerAsyncResult` 物件中並予以傳回。</span><span class="sxs-lookup"><span data-stu-id="80081-173">Finally, the pipeline is wrapped in a `PipelineInvokerAsyncResult` object and returned.</span></span> <span data-ttu-id="80081-174">`PipelineInvokerAsyncResult` 物件會註冊接聽程式並叫用管線。</span><span class="sxs-lookup"><span data-stu-id="80081-174">The `PipelineInvokerAsyncResult` object registers a listener and invokes the pipeline.</span></span>  
  
```  
pipeline.InvokeAsync();  
```  
  
 <span data-ttu-id="80081-175">執行完成時，輸出和錯誤會儲存在相同的 `PipelineInvokerAsyncResult` 物件中，並透過呼叫原先傳遞至 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> 的回呼方法，讓控制權回到工作流程執行階段。</span><span class="sxs-lookup"><span data-stu-id="80081-175">When execution finishes, output and errors are stored within the same `PipelineInvokerAsyncResult` object, and control is handed back to the workflow runtime by calling the callback method originally passed to <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.</span></span>  
  
 <span data-ttu-id="80081-176">在方法執行結束時，工作流程執行階段會呼叫活動的 <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="80081-176">At the end of the method's execution, the workflow runtime calls the activity’s <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> method.</span></span>  
  
 <span data-ttu-id="80081-177">`InvokePowerShell` 類別會包裝 `ExecutePowerShellCommand` 類別，並建立活動的兩個版本：泛型版本和非泛型版本。</span><span class="sxs-lookup"><span data-stu-id="80081-177">The `InvokePowerShell` class wraps the `ExecutePowerShellCommand` class and creates two versions of the activity; a generic version and a non-generic version.</span></span> <span data-ttu-id="80081-178">非泛型版本會直接傳回 PowerShell 執行的輸出，而泛型版本會將個別結果轉換成泛型類型。</span><span class="sxs-lookup"><span data-stu-id="80081-178">The non-generic version returns the output of the PowerShell execution directly, whereas the generic version transforms the individual results to the generic type.</span></span>  
  
 <span data-ttu-id="80081-179">活動的泛型版本是當做會呼叫 `ExecutePowerShellCommand` 並對其結果進行後置處理的循序工作流程來實作。</span><span class="sxs-lookup"><span data-stu-id="80081-179">The generic version of the activity is implemented as a sequential workflow that calls `ExecutePowerShellCommand` and post-processes its results.</span></span> <span data-ttu-id="80081-180">針對結果集合中的每個項目，如果設定 `InitializationAction`，後置處理步驟就會呼叫它，</span><span class="sxs-lookup"><span data-stu-id="80081-180">For each element in the result collection, the post-processing step calls `InitializationAction` if it is set.</span></span> <span data-ttu-id="80081-181">否則會執行簡單轉型。</span><span class="sxs-lookup"><span data-stu-id="80081-181">Otherwise, it does a simple cast.</span></span>  
  
```  
new ForEach<PSObject>  
{  
    Values = psObjects,  
    Body = new ActivityAction<PSObject>  
    {  
        Argument = psObject,  
        Handler = new Sequence  
        {  
            Activities =  
            {  
                new If  
                {  
                    Condition = // Is InitializationAction set?  
                    Then = new InvokeFunc<PSObject, TResult>  
                    {  
                        Argument = psObject,  
                        Result = outputObject,  
                        Func = this.InitializationAction  
                    },  
                    Else = new Assign<TResult>  
                    {  
                        To = outputObject,  
                        Value = new InArgument<TResult>(ctx => (TResult) psObject.Get(ctx).BaseObject),  
                    }  
                },  
                new AddToCollection<TResult>  
                {  
                    Collection = outputObjects,  
                    Item = outputObject  
                },  
            }  
        }  
    }  
},  
```  
  
 <span data-ttu-id="80081-182">針對兩個 `InvokePowerShell` 活動 (泛型和非泛型)，分別建立一個設計工具。</span><span class="sxs-lookup"><span data-stu-id="80081-182">For each of the two `InvokePowerShell` activities (generic, and non-generic), a designer was created.</span></span> <span data-ttu-id="80081-183">InvokePowerShellDesigner.xaml 及其相關聯的 .cs 檔案定義非泛型 [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] 活動版本在 `InvokePowerShell` 中的外觀。</span><span class="sxs-lookup"><span data-stu-id="80081-183">InvokePowerShellDesigner.xaml and its associated .cs file define the appearance in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] for the non-generic version of the `InvokePowerShell` activity.</span></span> <span data-ttu-id="80081-184">在 InvokePowerShellDesigner.xaml 中，<xref:System.Windows.Controls.DockPanel> 是用來代表圖形介面。</span><span class="sxs-lookup"><span data-stu-id="80081-184">Inside InvokePowerShellDesigner.xaml, a <xref:System.Windows.Controls.DockPanel> is used to represent the graphical interface.</span></span>  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 <span data-ttu-id="80081-185">請注意，文字方塊的 `Text` 屬性是雙向繫結，可確保活動的 `CommandText` 屬性值相當於設計工具中的輸入值。</span><span class="sxs-lookup"><span data-stu-id="80081-185">Note that the `Text` property of the text box is a two-way binding that ensures that the value of the activity’s `CommandText` property is equivalent to the value input into the designer.</span></span>  
  
 <span data-ttu-id="80081-186">GenericInvokePowerShellDesigner.xaml 及其相關聯的 .cs 檔案定義泛型 `InvokePowerShell` 活動的圖形介面。</span><span class="sxs-lookup"><span data-stu-id="80081-186">GenericInvokePowerShellDesigner.xaml and its associated .cs file define the graphical interface for the generic `InvokePowerShell` activity.</span></span> <span data-ttu-id="80081-187">此設計工具略為複雜，因為它可讓使用者設定 `InitializationAction`。</span><span class="sxs-lookup"><span data-stu-id="80081-187">The designer is slightly more complicated because it allows users to set an `InitializationAction`.</span></span> <span data-ttu-id="80081-188">關鍵項目是 <xref:System.Activities.Presentation.WorkflowItemPresenter> 允許子活動拖放至 `InvokePowerShell` 設計工具介面上的使用方式。</span><span class="sxs-lookup"><span data-stu-id="80081-188">The key element is the usage of <xref:System.Activities.Presentation.WorkflowItemPresenter> to allow drag and drop of child activities onto the `InvokePowerShell` designer surface.</span></span>  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 <span data-ttu-id="80081-189">設計工具自訂並不止於在設計畫布上定義活動外觀的 .xaml 檔案。</span><span class="sxs-lookup"><span data-stu-id="80081-189">The designer customization does not stop with the .xaml files that define the appearance of the activity on the design canvas.</span></span> <span data-ttu-id="80081-190">用來顯示活動參數的對話方塊也可以自訂。</span><span class="sxs-lookup"><span data-stu-id="80081-190">The dialog boxes used to display the parameters of the activity can also be customized.</span></span> <span data-ttu-id="80081-191">這些參數和 PowerShell 變數會影響 PowerShell 命令的行為。</span><span class="sxs-lookup"><span data-stu-id="80081-191">These parameters and PowerShell variables affect the behavior of PowerShell commands.</span></span> <span data-ttu-id="80081-192">活動將它們做為公開<!--zz <xref:System.Collections.Generic.Dictionary%601>-->`System.Collections.Generic.Dictionary`型別。</span><span class="sxs-lookup"><span data-stu-id="80081-192">The activity exposes them as <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` types.</span></span> <span data-ttu-id="80081-193">ArgumentDictionaryEditor.cs、PropertyEditorResources.xaml 和 PropertyEditorResources.cs 定義可讓您編輯這些類型的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="80081-193">ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml and PropertyEditorResources.cs define the dialog box that allows you to edit these types.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="80081-194">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="80081-194">To set up, build, and run the sample</span></span>  
 <span data-ttu-id="80081-195">您必須安裝 Windows PowerShell，才能執行這個範例。</span><span class="sxs-lookup"><span data-stu-id="80081-195">You must install Windows PowerShell to run this sample.</span></span> <span data-ttu-id="80081-196">Windows PowerShell 可以從下列位置安裝： [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=150383)。</span><span class="sxs-lookup"><span data-stu-id="80081-196">Windows PowerShell can be installed from this location: [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=150383).</span></span>  
  
#### <a name="to-run-the-coded-client"></a><span data-ttu-id="80081-197">若要執行程式碼用戶端</span><span class="sxs-lookup"><span data-stu-id="80081-197">To run the coded client</span></span>  
  
1.  <span data-ttu-id="80081-198">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 PowerShell.sln。</span><span class="sxs-lookup"><span data-stu-id="80081-198">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="80081-199">以滑鼠右鍵按一下方案，建置此方案。</span><span class="sxs-lookup"><span data-stu-id="80081-199">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="80081-200">以滑鼠右鍵按一下**CodedClient**專案，然後選取**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="80081-200">Right-click the **CodedClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="80081-201">按 CTRL+F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80081-201">Press CTRL+F5 to run the application.</span></span>  
  
#### <a name="to-run-the-designer-client"></a><span data-ttu-id="80081-202">若要執行設計工具用戶端</span><span class="sxs-lookup"><span data-stu-id="80081-202">To run the designer client</span></span>  
  
1.  <span data-ttu-id="80081-203">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 PowerShell.sln。</span><span class="sxs-lookup"><span data-stu-id="80081-203">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="80081-204">以滑鼠右鍵按一下方案，建置此方案。</span><span class="sxs-lookup"><span data-stu-id="80081-204">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="80081-205">以滑鼠右鍵按一下**DesignerClient**專案，然後選取**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="80081-205">Right-click the **DesignerClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="80081-206">按 CTRL+F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80081-206">Press CTRL+F5 to run the application.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="80081-207">已知問題</span><span class="sxs-lookup"><span data-stu-id="80081-207">Known Issues</span></span>  
  
1.  <span data-ttu-id="80081-208">如果因為從另一個專案參考 `InvokePowerShell` 活動組件或專案而造成建置錯誤，您可能需要將 `<SpecificVersion>True</SpecificVersion>` 項目手動加入至新專案 .csproj 檔案中參考 `InvokePowerShell` 的程式行底下。</span><span class="sxs-lookup"><span data-stu-id="80081-208">If referencing the `InvokePowerShell` activity assembly or project from another project results in a build error, you may need to manually add the `<SpecificVersion>True</SpecificVersion>` element to the .csproj file of the new project under the line that references `InvokePowerShell`.</span></span>  
  
2.  <span data-ttu-id="80081-209">當您新增如果未安裝 Windows PowerShell，將下列的錯誤訊息會顯示在 Visual Studio 中`InvokePowerShell`至工作流程活動： `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span><span class="sxs-lookup"><span data-stu-id="80081-209">If Windows PowerShell is not installed, the following error message is displayed in Visual Studio as soon as you add an `InvokePowerShell` activity onto a workflow: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span></span>  
  
3.  <span data-ttu-id="80081-210">在 Windows PowerShell 2.0 中，以程式設計方式呼叫 `$input.MoveNext()` 會失敗，而且使用 `$input.MoveNext()` 的程式碼會產生非預期的錯誤和結果。</span><span class="sxs-lookup"><span data-stu-id="80081-210">In Windows PowerShell 2.0, programmatically calling `$input.MoveNext()` fails and scripts using `$input.MoveNext()` produce unintended errors and results.</span></span> <span data-ttu-id="80081-211">若要解決此問題，逐一查看陣列時，請考慮使用 PowerShell 動詞命令 `foreach`，而不要呼叫 `MoveNext()`。</span><span class="sxs-lookup"><span data-stu-id="80081-211">To work around this issue, consider using the PowerShell verb `foreach` instead of calling `MoveNext()` when iterating an array.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="80081-212">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="80081-212">The samples may already be installed on your machine.</span></span> <span data-ttu-id="80081-213">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="80081-213">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="80081-214">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="80081-214">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="80081-215">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="80081-215">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`