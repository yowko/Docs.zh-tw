---
title: 多執行緒的 BackgroundWorker 元件 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: e4cd9b2a-f924-470e-a16e-50274709b40e
ms.openlocfilehash: 07700aa526866729f1ba1a8d846f22ce333c356d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a>逐步解說： 使用 BackgroundWorker 元件 (Visual Basic) 進行多執行緒處理
本逐步解說示範如何建立多執行緒的 Windows Forms 應用程式，以搜尋文字檔案中某個文字的出現次數。 其會示範：  
  
-   使用 <xref:System.ComponentModel.BackgroundWorker> 元件可呼叫的方法來定義類別。  
  
-   處理 <xref:System.ComponentModel.BackgroundWorker> 元件所引發的事件。  
  
-   啟動 <xref:System.ComponentModel.BackgroundWorker> 元件來執行方法。  
  
-   實作 `Cancel` 按鈕，以停止 <xref:System.ComponentModel.BackgroundWorker> 元件。  
  
### <a name="to-create-the-user-interface"></a>若要建立使用者介面  
  
1.  開啟新的 Visual Basic Windows Forms 應用程式專案，並建立名為表單`Form1`。  
  
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
  
    |Object|屬性|設定|  
    |------------|--------------|-------------|  
    |第一個標籤|`Text`|原始程式檔|  
    |第二個標籤|`Text`|比較字串|  
    |第三個標籤|`Text`|符合的文字|  
    |第四個標籤|`Text`|計算的行數|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a>建立 BackgroundWorker 元件，並訂閱其事件  
  
1.  將 <xref:System.ComponentModel.BackgroundWorker> 元件從 [工具箱] 的 [元件] 區段新增至表單。 隨即顯示在表單的元件匣中。  
  
2.  設定下列屬性 BackgroundWorker1 物件。  
  
    |屬性|設定|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|True|  
    |`WorkerSupportsCancellation`|True|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>若要定義會在不同執行緒上執行的方法  
  
1.  從 [專案] 功能表上，選擇 [加入類別]，將類別新增至專案。 隨即顯示 [ 新增項目] 對話方塊。  
  
2.  從範本視窗選取 [類別]，並在名稱欄位中輸入 `Words.vb`。  
  
3.  按一下 [加入] 。 隨即顯示 `Words`。  
  
4.  將下列程式碼加入 `Words` 類別：  
  
    ```vb  
    Public Class Words  
        ' Object to store the current state, for passing to the caller.  
        Public Class CurrentState  
            Public LinesCounted As Integer  
            Public WordsMatched As Integer  
        End Class  
  
        Public SourceFile As String  
        Public CompareString As String  
        Private WordCount As Integer = 0  
        Private LinesCounted As Integer = 0  
  
        Public Sub CountWords(  
            ByVal worker As System.ComponentModel.BackgroundWorker,  
            ByVal e As System.ComponentModel.DoWorkEventArgs  
        )  
            ' Initialize the variables.  
            Dim state As New CurrentState  
            Dim line = ""  
            Dim elapsedTime = 20  
            Dim lastReportDateTime = Now  
  
            If CompareString Is Nothing OrElse  
               CompareString = System.String.Empty Then  
  
               Throw New Exception("CompareString not specified.")  
            End If  
  
            Using myStream As New System.IO.StreamReader(SourceFile)  
  
                ' Process lines while there are lines remaining in the file.  
                Do While Not myStream.EndOfStream  
                    If worker.CancellationPending Then  
                        e.Cancel = True  
                        Exit Do  
                    Else  
                        line = myStream.ReadLine  
                        WordCount += CountInString(line, CompareString)  
                        LinesCounted += 1  
  
                        ' Raise an event so the form can monitor progress.  
                        If Now > lastReportDateTime.AddMilliseconds(elapsedTime) Then  
                            state.LinesCounted = LinesCounted  
                            state.WordsMatched = WordCount  
                            worker.ReportProgress(0, state)  
                            lastReportDateTime = Now  
                        End If  
  
                        ' Uncomment for testing.  
                        'System.Threading.Thread.Sleep(5)  
                    End If  
                Loop  
  
                ' Report the final count values.  
                state.LinesCounted = LinesCounted  
                state.WordsMatched = WordCount  
                worker.ReportProgress(0, state)  
            End Using  
        End Sub  
  
        Private Function CountInString(  
            ByVal SourceString As String,  
            ByVal CompareString As String  
        ) As Integer  
            ' This function counts the number of times  
            ' a word is found in a line.  
            If SourceString Is Nothing Then  
                Return 0  
            End If  
  
            Dim EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString)  
  
            ' To count all occurrences of the string, even within words, remove  
            ' both instances of "\b".  
            Dim regex As New System.Text.RegularExpressions.Regex(  
                "\b" + EscapedCompareString + "\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase)  
  
            Dim matches As System.Text.RegularExpressions.MatchCollection  
            matches = regex.Matches(SourceString)  
            Return matches.Count  
        End Function  
    End Class  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a>若要處理來自執行緒的事件  
  
-   將下列事件處理常式新增至您的主要表單：  
  
    ```vb  
    Private Sub BackgroundWorker1_RunWorkerCompleted(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
      ) Handles BackgroundWorker1.RunWorkerCompleted  
  
        ' This event handler is called when the background thread finishes.  
        ' This method runs on the main thread.  
        If e.Error IsNot Nothing Then  
            MessageBox.Show("Error: " & e.Error.Message)  
        ElseIf e.Cancelled Then  
            MessageBox.Show("Word counting canceled.")  
        Else  
            MessageBox.Show("Finished counting words.")  
        End If  
    End Sub  
  
    Private Sub BackgroundWorker1_ProgressChanged(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.ProgressChangedEventArgs  
      ) Handles BackgroundWorker1.ProgressChanged  
  
        ' This method runs on the main thread.  
        Dim state As Words.CurrentState =   
            CType(e.UserState, Words.CurrentState)  
        Me.LinesCounted.Text = state.LinesCounted.ToString  
        Me.WordsCounted.Text = state.WordsMatched.ToString  
    End Sub  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>若要開始並呼叫新的執行緒，以執行 WordCount 方法  
  
1.  將下列程序加入您的程式中：  
  
    ```vb  
    Private Sub BackgroundWorker1_DoWork(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.DoWorkEventArgs  
      ) Handles BackgroundWorker1.DoWork  
  
        ' This event handler is where the actual work is done.  
        ' This method runs on the background thread.  
  
        ' Get the BackgroundWorker object that raised this event.  
        Dim worker As System.ComponentModel.BackgroundWorker  
        worker = CType(sender, System.ComponentModel.BackgroundWorker)  
  
        ' Get the Words object and call the main method.  
        Dim WC As Words = CType(e.Argument, Words)  
        WC.CountWords(worker, e)  
    End Sub  
  
    Sub StartThread()  
        ' This method runs on the main thread.  
        Me.WordsCounted.Text = "0"  
  
        ' Initialize the object that the background worker calls.  
        Dim WC As New Words  
        WC.CompareString = Me.CompareString.Text  
        WC.SourceFile = Me.SourceFile.Text  
  
        ' Start the asynchronous operation.  
        BackgroundWorker1.RunWorkerAsync(WC)  
    End Sub  
    ```  
  
2.  從表單上的 `Start` 按鈕，呼叫 `StartThread` 方法：  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>若要實作 Cancel 按鈕，以停止執行緒  
  
-   從 `Click` 事件處理常式，呼叫 `Cancel` 按鈕的 `StopThread` 程序。  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
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
 [執行緒 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [逐步解說： 撰寫簡單的多執行緒的元件使用 Visual Basic](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)  
 [如何：訂閱及取消訂閱事件](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
