---
title: "非同步方法的傳回類型 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 703d3fc3f503017edf38521d77f9b15a92d0ebf3
ms.lasthandoff: 03/13/2017

---
# <a name="async-return-types-visual-basic"></a>非同步方法的傳回類型 (Visual Basic)
非同步方法有三種可能的傳回類型︰ <xref:System.Threading.Tasks.Task%601>， <xref:System.Threading.Tasks.Task>，和 void。</xref:System.Threading.Tasks.Task> </xref:System.Threading.Tasks.Task%601> 在 Visual Basic 中寫入 void 的傳回型別為[Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)程序。 如需非同步方法的詳細資訊，請參閱[使用 Async 和 Await (Visual Basic) 進行非同步程式設計](../../../../visual-basic/programming-guide/concepts/async/index.md)。  
  
 每個傳回型別在下列其中一節探討，您可以在主題結尾處找到使用全部三種類型的完整範例。  
  
> [!NOTE]
>  若要執行此範例，您必須擁有 Visual Studio 2012 或較新和.NET Framework 4.5 或更新版本安裝在電腦上。  
  
##  <a name="BKMK_TaskTReturnType"></a>Task(T) 傳回型別  
 <xref:System.Threading.Tasks.Task%601>傳回型別用於非同步方法，其中包含[傳回](../../../../visual-basic/language-reference/statements/return-statement.md)陳述式中運算元的型別`TResult`。</xref:System.Threading.Tasks.Task%601>  
  
 在下列範例中，`TaskOfT_MethodAsync`非同步方法包含傳回一個整數的 return 陳述式。 因此，在方法宣告必須指定傳回類型為`Task(Of Integer)`。  
  
```vb  
' TASK(OF T) EXAMPLE  
Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.FromResult is a placeholder for actual work that returns a string.  
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
    ' The method then can process the result in some way.  
    Dim leisureHours As Integer  
    If today.First() = "S" Then  
        leisureHours = 16  
    Else  
        leisureHours = 5  
    End If  
  
    ' Because the return statement specifies an operand of type Integer, the   
    ' method must have a return type of Task(Of Integer).   
    Return leisureHours  
End Function  
```  
  
 當`TaskOfT_MethodAsync`呼叫從 await 運算式 await 運算式擷取的整數值 (值`leisureHours`) 均會儲存在工作中，由`TaskOfT_MethodAsync`。 如需詳細資訊 await 運算式，請參閱[Await 運算子](../../../../visual-basic/language-reference/operators/await-operator.md)。  
  
 下列程式碼會呼叫並等候方法`TaskOfT_MethodAsync`。 將結果指派至`result1`變數。  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 您可以深入了解這種運作方式區隔呼叫`TaskOfT_MethodAsync`的應用程式從`Await`，如下列程式碼所示。 方法的呼叫`TaskOfT_MethodAsync`，這並不立即等候的傳回`Task(Of Integer)`，如您所預期之方法的宣告。 指派工作給`integerTask`變數中的範例。 因為`integerTask`是<xref:System.Threading.Tasks.Task%601>，它包含<xref:System.Threading.Tasks.Task%601.Result>型別的屬性`TResult`。</xref:System.Threading.Tasks.Task%601.Result> </xref:System.Threading.Tasks.Task%601> 在此情況下，TResult 代表整數類型。 當`Await`套用至`integerTask`，await 運算式評估的內容為<xref:System.Threading.Tasks.Task%601.Result%2A>屬性`integerTask`。</xref:System.Threading.Tasks.Task%601.Result%2A> 此值指派給`result2`變數。  
  
> [!WARNING]
>  <xref:System.Threading.Tasks.Task%601.Result%2A>屬性是封鎖的屬性。</xref:System.Threading.Tasks.Task%601.Result%2A> 如果您嘗試在其工作完成之前先存取它，目前使用中的執行緒會封鎖，直到工作完成並且有可用的值為止。 在大部分情況下，您應該使用存取值`Await`而不是直接存取的屬性。  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 下列程式碼顯示陳述式驗證的值`result1`變數，`result2`變數，和`Result`是相同的屬性。 請記住，`Result`屬性是封鎖的屬性，而且不應該存取之前尚未等候其工作。  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
##  <a name="BKMK_TaskReturnType"></a>工作的傳回型別  
 非同步方法，其中不包含 return 陳述式或包含 return 陳述式通常不會傳回運算元具有<xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task>的傳回類型 這種方法將會[Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)如果設為同步執行撰寫程序。 如果您使用`Task`傳回型別可以使用非同步方法呼叫的方法`Await`運算子暫停直到完成呼叫的非同步方法的呼叫者完成。  
  
 在下列範例中，非同步方法`Task_MethodAsync`不包含 return 陳述式。 因此，您指定的傳回型別`Task`方法，可讓`Task_MethodAsync`來等候。 定義`Task`型別不包含`Result`來儲存傳回值的屬性。  
  
```vb  
' TASK EXAMPLE  
Async Function Task_MethodAsync() As Task  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.Delay is a placeholder for actual work.  
    Await Task.Delay(2000)  
    textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
    ' This method has no return statement, so its return type is Task.   
End Function  
```  
  
 `Task_MethodAsync`呼叫並使用 await 陳述式，而不是 await 運算式，類似於同步呼叫的陳述式等候`Sub`或傳回 void 的方法。 應用程式的`Await`運算子在此情況下不會產生值。  
  
 下列程式碼會呼叫並等候方法`Task_MethodAsync`。  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 如先前所示<xref:System.Threading.Tasks.Task%601>範例中，您可以將呼叫`Task_MethodAsync`的應用程式從`Await`運算子，如下列程式碼所示。</xref:System.Threading.Tasks.Task%601> 不過，請記住，`Task`沒有`Result`屬性，並會產生任何值，當 await 運算子套用至`Task`。  
  
 下列程式碼分隔呼叫`Task_MethodAsync`從等候工作，`Task_MethodAsync`傳回。  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
##  <a name="BKMK_VoidReturnType"></a>Void 傳回型別  
 主要用途`Sub`程序是在事件處理常式，其中沒有傳回型別 （稱為 void 的傳回型別，以其他語言）。 void 傳回也可用來覆寫傳回 void 的方法，或執行可分類為「射後不理」(fire and forget) 之活動的方法。 不過，您應該會傳回`Task`可能的話，因為無法等候傳回 void 的非同步方法。 這種方法的任何呼叫端必須要能夠繼續完成而不需等待呼叫的非同步方法完成，且呼叫端必須與非同步方法產生的任何值或例外狀況無關。  
  
 傳回 void 的非同步方法的呼叫端無法攔截方法擲回的例外狀況，這類未處理的例外狀況有可能造成應用程式失敗。 如果例外狀況就會發生在非同步方法會傳回<xref:System.Threading.Tasks.Task>或<xref:System.Threading.Tasks.Task%601>，儲存在傳回的工作，並會等候工作時再次擲回例外狀況。</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task> 因此，請確定任何可能會產生例外狀況的非同步方法具有傳回類型為<xref:System.Threading.Tasks.Task>或<xref:System.Threading.Tasks.Task%601>和方法的呼叫會等候。</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task>  
  
 如需如何攔截非同步方法中的例外狀況的詳細資訊，請參閱[試...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
 下列程式碼會定義非同步事件處理常式。  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
##  <a name="BKMK_Example"></a>完整範例  
 下列 Windows Presentation Foundation (WPF) 專案包含本土的程式碼範例。  
  
 若要執行專案，請執行下列步驟：  
  
1.  啟動 Visual Studio。  
  
2.  在功能表列上，選擇 [檔案] ****、[新增] ****、[專案] ****。  
  
     [ **新增專案** ] 對話方塊隨即開啟。  
  
3.  在**已安裝**，**範本**類別中，選擇  **Visual Basic**，然後選擇  **Windows**。 選擇**WPF 應用程式**從專案類型清單。  
  
4.  輸入`AsyncReturnTypes`做為專案名稱，然後選擇 [**確定**] 按鈕。  
  
     新的專案會出現在**方案總管 中**。  
  
5.  在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。  
  
     如果看不到索引標籤上，開啟捷徑功能表中的 mainwindow.xaml**方案總管] 中**，然後選擇 [**開啟**。  
  
6.  在**XAML** MainWindow.xaml，視窗的程式碼取代下列程式碼。  
  
    ```vb  
    <Window x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>  
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
  
        </Grid>  
    </Window>  
  
    ```  
  
     包含文字方塊和按鈕的簡單視窗會出現在**設計**MainWindow.xaml 的視窗。  
  
7.  在**方案總管] 中**MainWindow.xaml.vb，開啟捷徑功能表，然後選擇 [**檢視程式碼**。  
  
8.  以下列程式碼取代 MainWindow.xaml.vb 中的程式碼。  
  
    ```vb  
    Class MainWindow  
  
        ' SUB EXAMPLE  
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
            textBox1.Clear()  
  
            ' Start the process and await its completion. DriverAsync is a   
            ' Task-returning async method.  
            Await DriverAsync()  
  
            ' Say goodbye.  
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
        End Sub  
  
        Async Function DriverAsync() As Task  
  
            ' Task(Of T)   
            ' Call and await the Task(Of T)-returning async method in the same statement.  
            Dim result1 As Integer = Await TaskOfT_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
            ' You can do other work that does not rely on resultTask before awaiting.  
            textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
            Dim result2 As Integer = Await integerTask  
  
            ' Display the values of the result1 variable, the result2 variable, and  
            ' the resultTask.Result property.  
            textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
            textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
            textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
  
            ' Task   
            ' Call and await the Task-returning async method in the same statement.  
            Await Task_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim simpleTask As Task = Task_MethodAsync()  
  
            ' You can do other work that does not rely on simpleTask before awaiting.  
            textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
            Await simpleTask  
        End Function  
  
        ' TASK(OF T) EXAMPLE  
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.FromResult is a placeholder for actual work that returns a string.  
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
            ' The method then can process the result in some way.  
            Dim leisureHours As Integer  
            If today.First() = "S" Then  
                leisureHours = 16  
            Else  
                leisureHours = 5  
            End If  
  
            ' Because the return statement specifies an operand of type Integer, the   
            ' method must have a return type of Task(Of Integer).   
            Return leisureHours  
        End Function  
  
        ' TASK EXAMPLE  
        Async Function Task_MethodAsync() As Task  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.Delay is a placeholder for actual work.  
            Await Task.Delay(2000)  
            textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
            ' This method has no return statement, so its return type is Task.   
        End Function  
  
    End Class  
    ```  
  
9. 選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。  
  
     應該出現下列輸出。  
  
    ```  
    Application can continue working while the Task<T> runs. . . .   
  
    Value of result1 variable:   5  
    Value of result2 variable:   5  
    Value of integerTask.Result: 5  
  
    Sorry for the delay. . . .  
  
    Application can continue working while the Task runs. . . .  
  
    Sorry for the delay. . . .  
  
    All done, exiting button-click event handler.  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Tasks.Task.FromResult%2A></xref:System.Threading.Tasks.Task.FromResult%2A>   
 [逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [非同步程式 (Visual Basic) 中的控制流程](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)   
 [非同步處理](../../../../visual-basic/language-reference/modifiers/async.md)   
 [Await 運算子](../../../../visual-basic/language-reference/operators/await-operator.md)
