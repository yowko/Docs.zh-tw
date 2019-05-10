---
title: 因為未等候此呼叫，所以在呼叫完成之前會繼續執行目前方法
ms.date: 07/20/2015
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
ms.openlocfilehash: c4704fb09e9519c14f29365b2cf7f536bbbc5dca
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619554"
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a>因為未等候此呼叫，所以在呼叫完成之前會繼續執行目前方法
因為未等候此呼叫，所以在呼叫完成之前會繼續執行目前的方法。 請考慮將 'Await' 運算子套用至呼叫的結果。  
  
 目前的方法會呼叫傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 且不會將 [Await](../../../visual-basic/language-reference/operators/await-operator.md) 運算子套用至結果的非同步方法。 非同步方法的呼叫會啟動非同步工作。 不過，由於不會套用任何 `Await` 運算子，因此程式會繼續執行，而不等候工作完成。 在大部分情況下，不應該有此行為。 通常呼叫方法的其他方面取決於呼叫的結果，或至少被呼叫的方法必須完成，才能從包含呼叫的方法傳回。  
  
 同樣重要的問題是，在呼叫的非同步方法中引發的例外狀況會發生什麼情形。 在傳回 <xref:System.Threading.Tasks.Task> 或  <xref:System.Threading.Tasks.Task%601> 的方法中引發的例外狀況會儲存到傳回的工作中。 如果您未等候工作，也未明確檢查例外狀況，例外狀況就會遺失。 如果您等候工作，則其例外狀況會再次擲回。  
  
 因此最佳做法是一律等候呼叫。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC42358  
  
### <a name="to-address-this-warning"></a>解決這個警告  
  
- 只有在您確定不要等候非同步呼叫完成，而且被呼叫的方法不會引發任何例外狀況時，才應考慮隱藏警告。 在這種情況下，您可以藉由將呼叫的工作結果指定至變數來隱藏警告。  
  
     下列範例將示範如何產生警告、如何隱藏警告，以及如何等候呼叫。  
  
    ```vb  
    Async Function CallingMethodAsync() As Task  
  
        ResultsTextBox.Text &= vbCrLf & "  Entering calling method."  
  
        ' Variable delay is used to slow down the called method so that you  
        ' can distinguish between awaiting and not awaiting in the program's output.   
        ' You can adjust the value to produce the output that this topic shows   
        ' after the code.  
        Dim delay = 5000  
  
        ' Call #1.  
        ' Call an async method. Because you don't await it, its completion isn't   
        ' coordinated with the current method, CallingMethodAsync.  
        ' The following line causes the warning.  
        CalledMethodAsync(delay)  
  
        ' Call #2.  
        ' To suppress the warning without awaiting, you can assign the   
        ' returned task to a variable. The assignment doesn't change how  
        ' the program runs. However, the recommended practice is always to  
        ' await a call to an async method.  
        ' Replace Call #1 with the following line.  
        'Task delayTask = CalledMethodAsync(delay)  
  
        ' Call #3  
        ' To contrast with an awaited call, replace the unawaited call   
        ' (Call #1 or Call #2) with the following awaited call. The best   
        ' practice is to await the call.  
  
        'Await CalledMethodAsync(delay)  
  
        ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync  
        ' continues to run and, in this example, finishes its work and returns  
        ' to its caller.  
        ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."  
    End Function  
  
    Async Function CalledMethodAsync(howLong As Integer) As Task  
  
        ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."  
        ' Slow the process down a little so you can distinguish between awaiting  
        ' and not awaiting. Adjust the value for howLong if necessary.  
        Await Task.Delay(howLong)  
        ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."  
    End Function  
    ```  
  
     在此範例中，如果您選擇呼叫 #1 或呼叫 #2，則未等候的非同步方法 (`CalledMethodAsync`) 會在其呼叫端 (`CallingMethodAsync`) 和呼叫端的呼叫端 (`StartButton_Click`) 都完成之後才完成。 下列輸出的最後一行將顯示被呼叫的方法完成的時間。 輸入中會標記在完整範例中進入和結束呼叫 `CallingMethodAsync` 的事件處理常式。  
  
    ```  
    Entering the Click event handler.  
      Entering calling method.  
        Entering called method, starting and awaiting Task.Delay.  
      Returning from calling method.  
    Exiting the Click event handler.  
        Task.Delay is finished--returning from called method.  
    ```  
  
## <a name="example"></a>範例  
 下列 Windows Presentation Foundation (WPF) 應用程式包含了前述範例的方法。 下列步驟將會設定應用程式。  
  
1. 建立 WPF 應用程式，並將其命名為 `AsyncWarning`。  
  
2. 在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。  
  
     如果未顯示索引標籤，請在 [ **方案總管**] 中開啟 MainWindow.xaml 的捷徑功能表，然後選擇 [ **檢視程式碼**]。  
  
3. 在 MainWindow.xaml 的 [ **XAML** ] 檢視中，將程式碼取代為下列程式碼。  
  
    ```vb  
    <Window x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="StartButton_Click" />  
            <TextBox x:Name="ResultsTextBox" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
        </Grid>  
    </Window>  
    ```  
  
     包含按鈕和文字方塊的簡單視窗會出現在 MainWindow.xaml 的 [ **設計** ] 檢視中。  
  
     如需 XAML 設計工具的詳細資訊，請參閱[使用 XAML 設計工具建立 UI](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio)。 如需如何建置屬於您自己的簡單 UI 資訊，請參閱＜建立 WPF 應用程式＞和＜設計簡單的 WPF MainWindow＞這兩節，其位於[逐步解說：使用 Async 和 Await 存取 Web](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。  
  
4. 以下列程式碼取代 MainWindow.xaml.vb 中的程式碼。  
  
    ```vb  
    Class MainWindow   
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
            ResultsTextBox.Text &= vbCrLf & "Entering the Click event handler."  
            Await CallingMethodAsync()  
            ResultsTextBox.Text &= vbCrLf & "Exiting the Click event handler."  
        End Sub  
  
        Async Function CallingMethodAsync() As Task  
  
            ResultsTextBox.Text &= vbCrLf & "  Entering calling method."  
  
            ' Variable delay is used to slow down the called method so that you  
            ' can distinguish between awaiting and not awaiting in the program's output.   
            ' You can adjust the value to produce the output that this topic shows   
            ' after the code.  
            Dim delay = 5000  
  
            ' Call #1.  
            ' Call an async method. Because you don't await it, its completion isn't   
            ' coordinated with the current method, CallingMethodAsync.  
            ' The following line causes the warning.  
            CalledMethodAsync(delay)  
  
            ' Call #2.  
            ' To suppress the warning without awaiting, you can assign the   
            ' returned task to a variable. The assignment doesn't change how  
            ' the program runs. However, the recommended practice is always to  
            ' await a call to an async method.  
  
            ' Replace Call #1 with the following line.  
            'Task delayTask = CalledMethodAsync(delay)  
  
            ' Call #3  
            ' To contrast with an awaited call, replace the unawaited call   
            ' (Call #1 or Call #2) with the following awaited call. The best   
            ' practice is to await the call.  
  
            'Await CalledMethodAsync(delay)  
  
            ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync  
            ' continues to run and, in this example, finishes its work and returns  
            ' to its caller.  
            ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."  
        End Function  
  
        Async Function CalledMethodAsync(howLong As Integer) As Task  
  
            ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."  
            ' Slow the process down a little so you can distinguish between awaiting  
            ' and not awaiting. Adjust the value for howLong if necessary.  
            Await Task.Delay(howLong)  
            ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."  
        End Function  
  
    End Class  
  
    ' Output  
  
    ' Entering the Click event handler.  
    '   Entering calling method.  
    '     Entering called method, starting and awaiting Task.Delay.  
    '   Returning from calling method.  
    ' Exiting the Click event handler.  
    '     Task.Delay is finished--returning from called method.  
  
    ' Output  
  
    ' Entering the Click event handler.  
    '   Entering calling method.  
    '     Entering called method, starting and awaiting Task.Delay.  
    '     Task.Delay is finished--returning from called method.  
    '   Returning from calling method.  
    ' Exiting the Click event handler.  
    ```  
  
5. 選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。  
  
     預期的輸出會出現在程式碼結尾。  
  
## <a name="see-also"></a>另請參閱

- [Await 運算子](../../../visual-basic/language-reference/operators/await-operator.md)
- [使用 Async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)
