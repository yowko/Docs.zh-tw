---
title: "逐步解說：使用 BackgroundWorker 元件進行多執行緒處理 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ff670fbf-a0ac-40c1-ab08-9ed53768f880
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 72d6e9ab42ca270ebe0691be23ebe181b973620d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-c"></a><span data-ttu-id="e9ed4-102">逐步解說：使用 BackgroundWorker 元件進行多執行緒處理 (C#)</span><span class="sxs-lookup"><span data-stu-id="e9ed4-102">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>
<span data-ttu-id="e9ed4-103">本逐步解說示範如何建立多執行緒的 Windows Forms 應用程式，以搜尋文字檔案中某個文字的出現次數。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="e9ed4-104">其會示範：</span><span class="sxs-lookup"><span data-stu-id="e9ed4-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="e9ed4-105">使用 <xref:System.ComponentModel.BackgroundWorker> 元件可呼叫的方法來定義類別。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="e9ed4-106">處理 <xref:System.ComponentModel.BackgroundWorker> 元件所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="e9ed4-107">啟動 <xref:System.ComponentModel.BackgroundWorker> 元件來執行方法。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="e9ed4-108">實作 `Cancel` 按鈕，以停止 <xref:System.ComponentModel.BackgroundWorker> 元件。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="e9ed4-109">若要建立使用者介面</span><span class="sxs-lookup"><span data-stu-id="e9ed4-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="e9ed4-110">開啟新的 C# Windows Forms 應用程式專案，並建立名為 `Form1` 的表單。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-110">Open a new C# Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="e9ed4-111">將兩個按鈕和四個文字方塊新增至 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="e9ed4-112">依照下表所示的方式，命名物件。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="e9ed4-113">物件</span><span class="sxs-lookup"><span data-stu-id="e9ed4-113">Object</span></span>|<span data-ttu-id="e9ed4-114">屬性</span><span class="sxs-lookup"><span data-stu-id="e9ed4-114">Property</span></span>|<span data-ttu-id="e9ed4-115">設定</span><span class="sxs-lookup"><span data-stu-id="e9ed4-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="e9ed4-116">第一個按鈕</span><span class="sxs-lookup"><span data-stu-id="e9ed4-116">First button</span></span>|<span data-ttu-id="e9ed4-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="e9ed4-117">`Name`, `Text`</span></span>|<span data-ttu-id="e9ed4-118">Start, Start</span><span class="sxs-lookup"><span data-stu-id="e9ed4-118">Start, Start</span></span>|  
    |<span data-ttu-id="e9ed4-119">第二個按鈕</span><span class="sxs-lookup"><span data-stu-id="e9ed4-119">Second button</span></span>|<span data-ttu-id="e9ed4-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="e9ed4-120">`Name`, `Text`</span></span>|<span data-ttu-id="e9ed4-121">Cancel, Cancel</span><span class="sxs-lookup"><span data-stu-id="e9ed4-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="e9ed4-122">第一個文字方塊</span><span class="sxs-lookup"><span data-stu-id="e9ed4-122">First text box</span></span>|<span data-ttu-id="e9ed4-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="e9ed4-123">`Name`, `Text`</span></span>|<span data-ttu-id="e9ed4-124">SourceFile, ""</span><span class="sxs-lookup"><span data-stu-id="e9ed4-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="e9ed4-125">第二個文字方塊</span><span class="sxs-lookup"><span data-stu-id="e9ed4-125">Second text box</span></span>|<span data-ttu-id="e9ed4-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="e9ed4-126">`Name`, `Text`</span></span>|<span data-ttu-id="e9ed4-127">CompareString, ""</span><span class="sxs-lookup"><span data-stu-id="e9ed4-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="e9ed4-128">第三個文字方塊</span><span class="sxs-lookup"><span data-stu-id="e9ed4-128">Third text box</span></span>|<span data-ttu-id="e9ed4-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="e9ed4-129">`Name`, `Text`</span></span>|<span data-ttu-id="e9ed4-130">WordsCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="e9ed4-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="e9ed4-131">第四個文字方塊</span><span class="sxs-lookup"><span data-stu-id="e9ed4-131">Fourth text box</span></span>|<span data-ttu-id="e9ed4-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="e9ed4-132">`Name`, `Text`</span></span>|<span data-ttu-id="e9ed4-133">LinesCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="e9ed4-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="e9ed4-134">將標籤新增至每個文字方塊旁。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-134">Add a label next to each text box.</span></span> <span data-ttu-id="e9ed4-135">依照下表所示的方式，設定每個標籤的 `Text` 屬性。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="e9ed4-136">物件</span><span class="sxs-lookup"><span data-stu-id="e9ed4-136">Object</span></span>|<span data-ttu-id="e9ed4-137">屬性</span><span class="sxs-lookup"><span data-stu-id="e9ed4-137">Property</span></span>|<span data-ttu-id="e9ed4-138">設定</span><span class="sxs-lookup"><span data-stu-id="e9ed4-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="e9ed4-139">第一個標籤</span><span class="sxs-lookup"><span data-stu-id="e9ed4-139">First label</span></span>|`Text`|<span data-ttu-id="e9ed4-140">原始程式檔</span><span class="sxs-lookup"><span data-stu-id="e9ed4-140">Source File</span></span>|  
    |<span data-ttu-id="e9ed4-141">第二個標籤</span><span class="sxs-lookup"><span data-stu-id="e9ed4-141">Second label</span></span>|`Text`|<span data-ttu-id="e9ed4-142">比較字串</span><span class="sxs-lookup"><span data-stu-id="e9ed4-142">Compare String</span></span>|  
    |<span data-ttu-id="e9ed4-143">第三個標籤</span><span class="sxs-lookup"><span data-stu-id="e9ed4-143">Third label</span></span>|`Text`|<span data-ttu-id="e9ed4-144">符合的文字</span><span class="sxs-lookup"><span data-stu-id="e9ed4-144">Matching Words</span></span>|  
    |<span data-ttu-id="e9ed4-145">第四個標籤</span><span class="sxs-lookup"><span data-stu-id="e9ed4-145">Fourth label</span></span>|`Text`|<span data-ttu-id="e9ed4-146">計算的行數</span><span class="sxs-lookup"><span data-stu-id="e9ed4-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="e9ed4-147">建立 BackgroundWorker 元件，並訂閱其事件</span><span class="sxs-lookup"><span data-stu-id="e9ed4-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="e9ed4-148">將 <xref:System.ComponentModel.BackgroundWorker> 元件從 [工具箱] 的 [元件] 區段新增至表單。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="e9ed4-149">隨即顯示在表單的元件匣中。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="e9ed4-150">設定 backgroundWorker1 物件的下列屬性。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-150">Set the following properties for the backgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="e9ed4-151">屬性</span><span class="sxs-lookup"><span data-stu-id="e9ed4-151">Property</span></span>|<span data-ttu-id="e9ed4-152">設定</span><span class="sxs-lookup"><span data-stu-id="e9ed4-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="e9ed4-153">True</span><span class="sxs-lookup"><span data-stu-id="e9ed4-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="e9ed4-154">True</span><span class="sxs-lookup"><span data-stu-id="e9ed4-154">True</span></span>|  
  
3.  <span data-ttu-id="e9ed4-155">訂閱 backgroundWorker1 物件的事件。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-155">Subscribe to the events of the backgroundWorker1 object.</span></span> <span data-ttu-id="e9ed4-156">在 [屬性] 視窗頂端，按一下**事件**圖示。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-156">At the top of the **Properties** window, click the **Events** icon.</span></span> <span data-ttu-id="e9ed4-157">按兩下 `RunWorkerCompleted` 事件，建立事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-157">Double-click the `RunWorkerCompleted` event to create an event handler method.</span></span> <span data-ttu-id="e9ed4-158">針對 `ProgressChanged` 和 `DoWork` 事件，執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-158">Do the same for the `ProgressChanged` and `DoWork` events.</span></span>  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="e9ed4-159">若要定義會在不同執行緒上執行的方法</span><span class="sxs-lookup"><span data-stu-id="e9ed4-159">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="e9ed4-160">從 [專案] 功能表上，選擇 [加入類別]，將類別新增至專案。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-160">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="e9ed4-161">隨即顯示 [ 新增項目] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-161">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="e9ed4-162">從範本視窗選取 [類別]，並在名稱欄位中輸入 `Words.cs`。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-162">Select **Class** from the templates window and enter `Words.cs` in the name field.</span></span>  
  
3.  <span data-ttu-id="e9ed4-163">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-163">Click **Add**.</span></span> <span data-ttu-id="e9ed4-164">隨即顯示 `Words`。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-164">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="e9ed4-165">將下列程式碼加入 `Words` 類別：</span><span class="sxs-lookup"><span data-stu-id="e9ed4-165">Add the following code to the `Words` class:</span></span>  
  
    ```csharp  
    public class Words  
    {  
        // Object to store the current state, for passing to the caller.  
        public class CurrentState  
        {  
            public int LinesCounted;  
            public int WordsMatched;  
        }  
  
        public string SourceFile;  
        public string CompareString;  
        private int WordCount;  
        private int LinesCounted;  
  
        public void CountWords(  
            System.ComponentModel.BackgroundWorker worker,  
            System.ComponentModel.DoWorkEventArgs e)  
        {  
            // Initialize the variables.  
            CurrentState state = new CurrentState();  
            string line = "";  
            int elapsedTime = 20;  
            DateTime lastReportDateTime = DateTime.Now;  
  
            if (CompareString == null ||  
                CompareString == System.String.Empty)  
            {  
                throw new Exception("CompareString not specified.");  
            }  
  
            // Open a new stream.  
            using (System.IO.StreamReader myStream = new System.IO.StreamReader(SourceFile))  
            {  
                // Process lines while there are lines remaining in the file.  
                while (!myStream.EndOfStream)  
                {  
                    if (worker.CancellationPending)  
                    {  
                        e.Cancel = true;  
                        break;  
                    }  
                    else  
                    {  
                        line = myStream.ReadLine();  
                        WordCount += CountInString(line, CompareString);  
                        LinesCounted += 1;  
  
                        // Raise an event so the form can monitor progress.  
                        int compare = DateTime.Compare(  
                            DateTime.Now, lastReportDateTime.AddMilliseconds(elapsedTime));  
                        if (compare > 0)  
                        {  
                            state.LinesCounted = LinesCounted;  
                            state.WordsMatched = WordCount;  
                            worker.ReportProgress(0, state);  
                            lastReportDateTime = DateTime.Now;  
                        }  
                    }  
                    // Uncomment for testing.  
                    //System.Threading.Thread.Sleep(5);  
                }  
  
                // Report the final count values.  
                state.LinesCounted = LinesCounted;  
                state.WordsMatched = WordCount;  
                worker.ReportProgress(0, state);  
            }  
        }  
  
        private int CountInString(  
            string SourceString,  
            string CompareString)  
        {  
            // This function counts the number of times  
            // a word is found in a line.  
            if (SourceString == null)  
            {  
                return 0;  
            }  
  
            string EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString);  
  
            System.Text.RegularExpressions.Regex regex;  
            regex = new System.Text.RegularExpressions.Regex(   
                // To count all occurrences of the string, even within words, remove  
                // both instances of @"\b" from the following line.  
                @"\b" + EscapedCompareString + @"\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase);  
  
            System.Text.RegularExpressions.MatchCollection matches;  
            matches = regex.Matches(SourceString);  
            return matches.Count;  
        }  
  
    }  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="e9ed4-166">若要處理來自執行緒的事件</span><span class="sxs-lookup"><span data-stu-id="e9ed4-166">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="e9ed4-167">將下列事件處理常式新增至您的主要表單：</span><span class="sxs-lookup"><span data-stu-id="e9ed4-167">Add the following event handlers to your main form:</span></span>  
  
    ```csharp  
    private void backgroundWorker1_RunWorkerCompleted(object sender, RunWorkerCompletedEventArgs e)  
    {  
    // This event handler is called when the background thread finishes.  
    // This method runs on the main thread.  
    if (e.Error != null)  
        MessageBox.Show("Error: " + e.Error.Message);  
    else if (e.Cancelled)  
        MessageBox.Show("Word counting canceled.");  
    else  
        MessageBox.Show("Finished counting words.");  
    }  
  
    private void backgroundWorker1_ProgressChanged(object sender, ProgressChangedEventArgs e)  
    {  
        // This method runs on the main thread.  
        Words.CurrentState state =  
            (Words.CurrentState)e.UserState;  
        this.LinesCounted.Text = state.LinesCounted.ToString();  
        this.WordsCounted.Text = state.WordsMatched.ToString();  
    }  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="e9ed4-168">若要開始並呼叫新的執行緒，以執行 WordCount 方法</span><span class="sxs-lookup"><span data-stu-id="e9ed4-168">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="e9ed4-169">將下列程序加入您的程式中：</span><span class="sxs-lookup"><span data-stu-id="e9ed4-169">Add the following procedures to your program:</span></span>  
  
    ```csharp  
    private void backgroundWorker1_DoWork(object sender, DoWorkEventArgs e)  
    {  
        // This event handler is where the actual work is done.  
        // This method runs on the background thread.  
  
        // Get the BackgroundWorker object that raised this event.  
        System.ComponentModel.BackgroundWorker worker;  
        worker = (System.ComponentModel.BackgroundWorker)sender;  
  
        // Get the Words object and call the main method.  
        Words WC = (Words)e.Argument;  
        WC.CountWords(worker, e);  
    }  
  
    private void StartThread()  
    {  
        // This method runs on the main thread.  
        this.WordsCounted.Text = "0";  
  
        // Initialize the object that the background worker calls.  
        Words WC = new Words();  
        WC.CompareString = this.CompareString.Text;  
        WC.SourceFile = this.SourceFile.Text;  
  
        // Start the asynchronous operation.  
        backgroundWorker1.RunWorkerAsync(WC);  
    }  
    ```  
  
2.  <span data-ttu-id="e9ed4-170">從表單上的 `Start` 按鈕，呼叫 `StartThread` 方法：</span><span class="sxs-lookup"><span data-stu-id="e9ed4-170">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```csharp  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="e9ed4-171">若要實作 Cancel 按鈕，以停止執行緒</span><span class="sxs-lookup"><span data-stu-id="e9ed4-171">To implement a Cancel button that stops the thread</span></span>  
  
    -   <span data-ttu-id="e9ed4-172">從 `Click` 事件處理常式，呼叫 `Cancel` 按鈕的 `StopThread` 程序。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-172">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
        ```csharp  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
        ```  
  
## <a name="testing"></a><span data-ttu-id="e9ed4-173">測試</span><span class="sxs-lookup"><span data-stu-id="e9ed4-173">Testing</span></span>  
 <span data-ttu-id="e9ed4-174">您現在可以測試應用程式，確定它運作正常。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-174">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="e9ed4-175">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="e9ed4-175">To test the application</span></span>  
  
1.  <span data-ttu-id="e9ed4-176">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-176">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="e9ed4-177">顯示表單時，請輸入您想要在 `sourceFile` 方塊中測試之檔案的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-177">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="e9ed4-178">例如，假設您的測試檔名為 Test.txt，請輸入 C:\Test.txt。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-178">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="e9ed4-179">在第二個文字方塊中，輸入文字或片語來搜尋文字檔案中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-179">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="e9ed4-180">按一下 `Start` 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-180">Click the `Start` button.</span></span> <span data-ttu-id="e9ed4-181">`LinesCounted` 按鈕應該開始立即遞增。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-181">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="e9ed4-182">完成時，應用程式就會顯示「完成計數」訊息。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-182">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="e9ed4-183">若要測試 Cancel 按鈕</span><span class="sxs-lookup"><span data-stu-id="e9ed4-183">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="e9ed4-184">按 F5 以啟動應用程式，輸入檔案名稱，並依據先前的程序所述來搜尋文字。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-184">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="e9ed4-185">請確定您選擇的檔案夠大，才能在程序完成之前進行取消。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-185">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="e9ed4-186">按一下 `Start` 按鈕，以啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-186">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="e9ed4-187">按一下 `Cancel` 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-187">Click the `Cancel` button.</span></span> <span data-ttu-id="e9ed4-188">應用程式應該立刻停止計數。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-188">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e9ed4-189">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e9ed4-189">Next Steps</span></span>  
 <span data-ttu-id="e9ed4-190">此應用程式包含一些基本錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-190">This application contains some basic error handling.</span></span> <span data-ttu-id="e9ed4-191">它會偵測空白的搜尋字串。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-191">It detects blank search strings.</span></span> <span data-ttu-id="e9ed4-192">您可以藉由處理其他錯誤 (例如計算超過上限的文字或行數)，讓此程式更穩固。</span><span class="sxs-lookup"><span data-stu-id="e9ed4-192">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9ed4-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9ed4-193">See Also</span></span>  
 [<span data-ttu-id="e9ed4-194">執行緒 (C#)</span><span class="sxs-lookup"><span data-stu-id="e9ed4-194">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="e9ed4-195">如何：訂閱及取消訂閱事件</span><span class="sxs-lookup"><span data-stu-id="e9ed4-195">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
