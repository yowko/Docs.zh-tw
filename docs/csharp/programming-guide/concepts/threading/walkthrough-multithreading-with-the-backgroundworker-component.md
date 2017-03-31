---
title: "逐步解說：使用 BackgroundWorker 元件進行多執行緒處理 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: ff670fbf-a0ac-40c1-ab08-9ed53768f880
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1a27591c62e55295b3cf2b9716776b25d984865a
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-c"></a>逐步解說：使用 BackgroundWorker 元件進行多執行緒處理 (C#)
本逐步解說示範如何建立多執行緒的 Windows Forms 應用程式，以搜尋文字檔案中某個文字的出現次數。 其會示範：  
  
-   使用可由 <xref:System.ComponentModel.BackgroundWorker> 元件呼叫的方法，來定義類別。  
  
-   處理由 <xref:System.ComponentModel.BackgroundWorker> 元件所引發的事件。  
  
-   啟動 <xref:System.ComponentModel.BackgroundWorker> 元件，以執行方法。  
  
-   實作 `Cancel` 按鈕以停止 <xref:System.ComponentModel.BackgroundWorker> 元件。  
  
### <a name="to-create-the-user-interface"></a>若要建立使用者介面  
  
1.  開啟新的 C# Windows Forms 應用程式專案，並建立名為 `Form1` 的表單。  
  
2.  將兩個按鈕和四個文字方塊新增至 `Form1`。  
  
3.  依照下表所示的方式，命名物件。  
  
    |物件|屬性|設定|  
    |------------|--------------|-------------|  
    |第一個按鈕|`Name`, `Text`|Start, Start|  
    |第二個按鈕|`Name`, `Text`|Cancel, Cancel|  
    |第一個文字方塊|`Name`, `Text`|SourceFile, ""|  
    |第二個文字方塊|`Name`, `Text`|CompareString, ""|  
    |第三個文字方塊|`Name`, `Text`|WordsCounted, "0"|  
    |第四個文字方塊|`Name`, `Text`|LinesCounted, "0"|  
  
4.  將標籤新增至每個文字方塊旁。 依照下表所示的方式，設定每個標籤的 `Text` 屬性。  
  
    |物件|屬性|設定|  
    |------------|--------------|-------------|  
    |第一個標籤|`Text`|原始程式檔|  
    |第二個標籤|`Text`|比較字串|  
    |第三個標籤|`Text`|符合的文字|  
    |第四個標籤|`Text`|計算的行數|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a>建立 BackgroundWorker 元件，並訂閱其事件  
  
1.  從 [ToolBox]**** 的 [元件]**** 區段，將 <xref:System.ComponentModel.BackgroundWorker> 元件新增至表單。 隨即顯示在表單的元件匣中。  
  
2.  設定 backgroundWorker1 物件的下列屬性。  
  
    |屬性|設定|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|True|  
    |`WorkerSupportsCancellation`|True|  
  
3.  訂閱 backgroundWorker1 物件的事件。 在 [屬性]**** 視窗頂端，按一下**事件**圖示。 按兩下 `RunWorkerCompleted` 事件，建立事件處理常式方法。 針對 `ProgressChanged` 和 `DoWork` 事件，執行相同的動作。  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>若要定義會在不同執行緒上執行的方法  
  
1.  從 [專案]**** 功能表上，選擇 [加入類別]****，將類別新增至專案。 隨即顯示 [ 新增項目]**** 對話方塊。  
  
2.  從範本視窗選取 [類別]****，並在名稱欄位中輸入 `Words.cs`。  
  
3.  按一下 [加入] ****。 隨即顯示 `Words`。  
  
4.  將下列程式碼加入 `Words` 類別：  
  
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
  
### <a name="to-handle-events-from-the-thread"></a>若要處理來自執行緒的事件  
  
-   將下列事件處理常式新增至您的主要表單：  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>若要開始並呼叫新的執行緒，以執行 WordCount 方法  
  
1.  將下列程序加入您的程式中：  
  
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
  
2.  從表單上的 `Start` 按鈕，呼叫 `StartThread` 方法：  
  
    ```csharp  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>若要實作 Cancel 按鈕，以停止執行緒  
  
    -   從 `Click` 事件處理常式，呼叫 `Cancel` 按鈕的 `StopThread` 程序。  
  
        ```csharp  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
        ```  
  
## <a name="testing"></a>測試  
 您現在可以測試應用程式，確定它運作正常。  
  
#### <a name="to-test-the-application"></a>若要測試應用程式  
  
1.  按 F5 執行應用程式。  
  
2.  顯示表單時，請輸入您想要在 `sourceFile` 方塊中測試之檔案的檔案路徑。 例如，假設您的測試檔名為 Test.txt，請輸入 C:\Test.txt。  
  
3.  在第二個文字方塊中，輸入文字或片語來搜尋文字檔案中的應用程式。  
  
4.  按一下 `Start` 按鈕。 `LinesCounted` 按鈕應該開始立即遞增。 完成時，應用程式就會顯示「完成計數」訊息。  
  
#### <a name="to-test-the-cancel-button"></a>若要測試 Cancel 按鈕  
  
1.  按 F5 以啟動應用程式，輸入檔案名稱，並依據先前的程序所述來搜尋文字。 請確定您選擇的檔案夠大，才能在程序完成之前進行取消。  
  
2.  按一下 `Start` 按鈕，以啟動應用程式。  
  
3.  按一下 `Cancel` 按鈕。 應用程式應該立刻停止計數。  
  
## <a name="next-steps"></a>後續步驟  
 此應用程式包含一些基本錯誤處理。 它會偵測空白的搜尋字串。 您可以藉由處理其他錯誤 (例如計算超過上限的文字或行數)，讓此程式更穩固。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒處理 (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)   
 [如何：訂閱及取消訂閱事件](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
