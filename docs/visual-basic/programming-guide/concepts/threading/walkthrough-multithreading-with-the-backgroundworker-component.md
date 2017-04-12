---
title: "多執行緒處理和 BackgroundWorker 元件 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: e4cd9b2a-f924-470e-a16e-50274709b40e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3686eb230349876f6cfffd2ad94ed1f547779ab1
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a>逐步解說︰ 使用 BackgroundWorker 元件 (Visual Basic) 的多執行緒處理
本逐步解說示範如何建立多執行緒的 Windows Form 應用程式，以搜尋相符項目文字的文字檔案。 它會示範︰  
  
-   定義類別的方法，可由呼叫<xref:System.ComponentModel.BackgroundWorker>元件。</xref:System.ComponentModel.BackgroundWorker>  
  
-   處理所引發的事件<xref:System.ComponentModel.BackgroundWorker>元件。</xref:System.ComponentModel.BackgroundWorker>  
  
-   啟動<xref:System.ComponentModel.BackgroundWorker>元件來執行方法。</xref:System.ComponentModel.BackgroundWorker>  
  
-   實作`Cancel`停止按鈕<xref:System.ComponentModel.BackgroundWorker>元件。</xref:System.ComponentModel.BackgroundWorker>  
  
### <a name="to-create-the-user-interface"></a>若要建立使用者介面  
  
1.  開啟新的 Visual Basic Windows Form 應用程式專案，並建立名為的表單`Form1`。  
  
2.  將兩個按鈕和四個文字方塊來加入`Form1`。  
  
3.  下表所示，為物件命名。  
  
    |物件|屬性|設定|  
    |------------|--------------|-------------|  
    |第一個按鈕|`Name`, `Text`|[開始] 開始|  
    |第二個按鈕|`Name`, `Text`|[取消]，[取消]|  
    |第一個文字方塊|`Name`, `Text`|SourceFile，""|  
    |第二個文字方塊|`Name`, `Text`|CompareString，""|  
    |第三個文字方塊|`Name`, `Text`|WordsCounted，"0"|  
    |第四個文字方塊|`Name`, `Text`|LinesCounted，"0"|  
  
4.  加入每個文字方塊旁邊的標籤。 設定`Text`每一個標籤，如下表所示的屬性。  
  
    |物件|屬性|設定|  
    |------------|--------------|-------------|  
    |第一個標籤|`Text`|原始程式檔|  
    |第二個標籤|`Text`|比較字串|  
    |第三個標籤|`Text`|符合的文字|  
    |第四個標籤|`Text`|計算程式碼行|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a>若要建立 BackgroundWorker 元件，並訂閱其事件  
  
1.  新增<xref:System.ComponentModel.BackgroundWorker>元件從**元件**區段**工具箱**至表單。</xref:System.ComponentModel.BackgroundWorker> 它會顯示在表單的元件匣。  
  
2.  設定下列屬性 BackgroundWorker1 物件。  
  
    |屬性|設定|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|True|  
    |`WorkerSupportsCancellation`|True|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>定義會在個別的執行緒執行的方法  
  
1.  從**專案**] 功能表上，選擇 [**加入類別**將類別加入至專案。 **加入新項目**對話方塊隨即出現。  
  
2.  選取**類別**從 [範本] 視窗並輸入`Words.vb`[名稱] 欄位中。  
  
3.  按一下 [加入] ****。 `Words`類別會顯示。  
  
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
  
### <a name="to-handle-events-from-the-thread"></a>處理執行緒中的事件  
  
-   將下列事件處理常式加入至您的主要表單︰  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>若要開始，並呼叫新的執行緒可執行的 WordCount 方法  
  
1.  將下列程序新增至您的程式︰  
  
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
  
2.  呼叫`StartThread`方法從`Start`表單上的按鈕︰  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>若要實作 [取消] 按鈕，停止執行緒  
  
-   呼叫`StopThread`程序從`Click`事件處理常式`Cancel` 按鈕。  
  
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
  
2.  顯示表單時，請輸入您想要在測試的檔案的檔案路徑`sourceFile`方塊。 例如，假設您的測試檔名為 Test.txt，輸入 C:\Test.txt。  
  
3.  在第二個文字方塊中，輸入單字或片語來搜尋文字檔案中的應用程式。  
  
4.  按一下 `Start` 按鈕。 `LinesCounted`按鈕應該開始立即遞增。 在完成時，應用程式就會顯示 「 完成計數 」 訊息。  
  
#### <a name="to-test-the-cancel-button"></a>若要測試的 [取消] 按鈕  
  
1.  按 F5 以啟動應用程式，並輸入檔案名稱，並搜尋文字中先前的程序所述。 請確定您選擇的檔案夠大，以確定您有時間完成之前取消此程序。  
  
2.  按一下 [ `Start` ] 按鈕以啟動應用程式。  
  
3.  按一下 `Cancel` 按鈕。 應用程式應該立刻停止計數。  
  
## <a name="next-steps"></a>後續步驟  
 此應用程式包含一些基本錯誤處理。 它會偵測空白的搜尋字串。 您可以讓程式更穩固處理其他錯誤，例如超過文字或程式行，就可以計算的最大數目。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒處理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)   
 [逐步解說︰ 撰寫簡單的多執行緒的元件，使用 Visual Basic](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)   
 [如何：訂閱及取消訂閱事件](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
