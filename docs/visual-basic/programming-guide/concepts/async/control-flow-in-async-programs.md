---
title: "控制流程中非同步程式 (Visual Basic) |Microsoft 文件"
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
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
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
ms.openlocfilehash: 15e02fbc023db9ae2f3ee9f40598faa7c9c027a0
ms.lasthandoff: 03/13/2017

---
# <a name="control-flow-in-async-programs-visual-basic"></a>非同步程式 (Visual Basic) 中的控制流程
您可以撰寫並使用更輕鬆地維護非同步程式`Async`和`Await`關鍵字。 不過，結果可能會讓您大吃一驚如果您不了解您的程式的運作方式。 透過簡單的非同步程式以顯示其中一種方法從控制項移到另一個與哪些資訊時的控制流程的每次傳送這個主題追蹤。  
  
> [!NOTE]
>  `Async` 和 `Await` 關鍵字是在 Visual Studio 2012 中引入。  
  
 一般情況下，您將標記包含與非同步程式碼的方法[非同步](../../../../visual-basic/language-reference/modifiers/async.md)修飾詞。 在加上 async 修飾詞的方法，您可以使用[Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md)運算子來指定位置的方法會暫停等候呼叫的非同步處理序完成。 如需詳細資訊，請參閱[使用 Async 和 Await (Visual Basic) 進行非同步程式設計](../../../../visual-basic/programming-guide/concepts/async/index.md)。  
  
 下列範例會使用非同步方法，以指定的網站，做為字串的內容下載並顯示字串的長度。 這個範例包含下列兩種方法。  
  
-   `startButton_Click`其呼叫`AccessTheWebAsync`，並顯示結果。  
  
-   `AccessTheWebAsync`因為它會下載網站，以做為字串的內容，並傳回字串的長度。 `AccessTheWebAsync`使用非同步<xref:System.Net.Http.HttpClient>方法， <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>、 內容下載。</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> </xref:System.Net.Http.HttpClient>  
  
 編號線出現在整個程式，協助您了解如何在程式執行，並且說明會標示每個點會發生什麼情況的策略點的顯示。 顯示程式碼行標示為 「 一 」 到 「 六個。 」 標籤表示程式達到這行程式碼的順序。  
  
 下列程式碼顯示大綱的程式。  
  
```vb  
Class MainWindow  
  
    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click  
  
        ' ONE  
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
  
        ' FOUR  
        Dim contentLength As Integer = Await getLengthTask  
  
        ' SIX  
        ResultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
    End Sub  
  
    Async Function AccessTheWebAsync() As Task(Of Integer)  
  
        ' TWO  
        Dim client As HttpClient = New HttpClient()   
        Dim getStringTask As Task(Of String) =   
            client.GetStringAsync("http://msdn.microsoft.com")  
  
        ' THREE  
        Dim urlContents As String = Await getStringTask  
  
        ' FIVE  
        Return urlContents.Length  
    End Function  
  
End Class  
  
```  
  
 每個標記的位置，「 一 」 到 「&6;，"會顯示程式的目前狀態的相關資訊。 會產生下列輸出。  
  
```  
  
ONE:   Entering startButton_Click.  
           Calling AccessTheWebAsync.  
  
TWO:   Entering AccessTheWebAsync.  
           Calling HttpClient.GetStringAsync.  
  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
  
Length of the downloaded string: 33946.  
```  
  
## <a name="set-up-the-program"></a>將程式設定  
 您可以從 MSDN 下載本主題所使用的程式碼，或它可以自行建立。  
  
> [!NOTE]
>  若要執行此範例，您必須擁有 Visual Studio 2012 或較新和.NET Framework 4.5 或更新版本安裝在電腦上。  
  
### <a name="download-the-program"></a>下載程式  
 您可以下載的應用程式的相關主題的[非同步範例︰ 非同步程式中的控制流程](http://go.microsoft.com/fwlink/?LinkId=255285)。 下列步驟會開啟並執行程式。  
  
1.  解壓縮下載的檔案，然後再啟動 Visual Studio。  
  
2.  在功能表列上，依序選擇 [檔案] ****、[開啟舊檔] ****及 [專案/方案] ****。  
  
3.  瀏覽至解壓縮的範例程式碼所在的資料夾，開啟方案 (.sln) 檔，然後選擇 F5 鍵以建置並執行專案。  
  
### <a name="build-the-program-yourself"></a>自行建立程式  
 下列 Windows Presentation Foundation (WPF) 專案包含本主題的程式碼範例。  
  
 若要執行專案，請執行下列步驟：  
  
1.  啟動 Visual Studio。  
  
2.  在功能表列上，選擇 [檔案] ****、[新增] ****、[專案] ****。  
  
     [ **新增專案** ] 對話方塊隨即開啟。  
  
3.  在**已安裝的範本** 窗格中，選擇  **Visual Basic**，然後選擇  **WPF 應用程式**從專案類型清單。  
  
4.  輸入`AsyncTracer`做為專案名稱，然後選擇 [**確定**] 按鈕。  
  
     新的專案會出現在**方案總管 中**。  
  
5.  在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。  
  
     如果看不到索引標籤上，開啟捷徑功能表中的 mainwindow.xaml**方案總管] 中**，然後選擇 [**檢視程式碼**。  
  
6.  在**XAML** MainWindow.xaml 的檢視，請以下列程式碼取代程式碼。  
  
    ```vb  
    <Window  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"  
        Title="Control Flow Trace" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>  
  
        </Grid>  
    </Window>  
  
    ```  
  
     包含文字方塊和按鈕的簡單視窗會出現在**設計**MainWindow.xaml 的檢視。  
  
7.  加入<xref:System.Net.Http>.</xref:System.Net.Http>的參考  
  
8.  在**方案總管] 中**MainWindow.xaml.vb，開啟捷徑功能表，然後選擇 [**檢視程式碼**。  
  
9. 在 MainWindow.xaml.vb，取代下列程式碼中的程式碼。  
  
    ```vb  
    ' Add an Imports statement and a reference for System.Net.Http.  
    Imports System.Net.Http  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click  
  
            ' The display lines in the example lead you through the control shifts.  
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &  
                "           Calling AccessTheWebAsync." & vbCrLf  
  
            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
  
            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &  
                "           Task getLengthTask is started." & vbCrLf &  
                "           About to await getLengthTask -- no caller to return to." & vbCrLf  
  
            Dim contentLength As Integer = Await getLengthTask  
  
            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &  
                "           Task getLengthTask is finished." & vbCrLf &  
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &  
                "           About to display contentLength and exit." & vbCrLf  
  
            ResultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
        End Sub  
  
        Async Function AccessTheWebAsync() As Task(Of Integer)  
  
            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."  
  
            ' Declare an HttpClient object.  
            Dim client As HttpClient = New HttpClient()  
  
            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf  
  
            ' GetStringAsync returns a Task(Of String).   
            Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &  
                "           Task getStringTask is started."  
  
            ' AccessTheWebAsync can continue to work until getStringTask is awaited.  
  
            ResultsTextBox.Text &=  
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf  
  
            ' Retrieve the website contents when task is complete.  
            Dim urlContents As String = Await getStringTask  
  
            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &  
                vbCrLf & "           Task getStringTask is complete." &  
                vbCrLf & "           Processing the return statement." &  
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf  
  
            Return urlContents.Length  
        End Function  
  
    End Class  
    ```  
  
10. 選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。  
  
     應該出現下列輸出。  
  
    ```  
    ONE:   Entering startButton_Click.  
               Calling AccessTheWebAsync.  
  
    TWO:   Entering AccessTheWebAsync.  
               Calling HttpClient.GetStringAsync.  
  
    THREE: Back in AccessTheWebAsync.  
               Task getStringTask is started.  
               About to await getStringTask & return a Task<int> to startButton_Click.  
  
    FOUR:  Back in startButton_Click.  
               Task getLengthTask is started.  
               About to await getLengthTask -- no caller to return to.  
  
    FIVE:  Back in AccessTheWebAsync.  
               Task getStringTask is complete.  
               Processing the return statement.  
               Exiting from AccessTheWebAsync.  
  
    SIX:   Back in startButton_Click.  
               Task getLengthTask is finished.  
               Result from AccessTheWebAsync is stored in contentLength.  
               About to display contentLength and exit.  
  
    Length of the downloaded string: 33946.  
    ```  
  
## <a name="trace-the-program"></a>追蹤程式  
  
### <a name="steps-one-and-two"></a>步驟一和二  
 前兩個顯示線條追蹤做為路徑`startButton_Click`呼叫`AccessTheWebAsync`，和`AccessTheWebAsync`呼叫非同步<xref:System.Net.Http.HttpClient>方法<xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> </xref:System.Net.Http.HttpClient> 下圖概述在方法的呼叫。  
  
 ![步驟&1; 和&2;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")  
  
 兩者的傳回型別`AccessTheWebAsync`和`client.GetStringAsync`為<xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> 如`AccessTheWebAsync`，TResult 是一個整數。 如`GetStringAsync`，TResult 是字串。 如需非同步方法的傳回類型的詳細資訊，請參閱[非同步傳回類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。  
  
 切換回呼叫端的控制時的工作傳回非同步方法會傳回工作執行個體。 控制從非同步方法傳回至呼叫端時`Await`運算子中被呼叫的方法或被呼叫的方法結束時出現。 顯示程式碼行標記為"3"透過 「&6; 」 會追蹤此程序的一部分。  
  
### <a name="step-three"></a>步驟三  
 在`AccessTheWebAsync`，非同步方法<xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>稱為目標網頁的內容下載。</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> 控制權會傳回從`client.GetStringAsync`至`AccessTheWebAsync`時`client.GetStringAsync`傳回。  
  
 `client.GetStringAsync`方法傳回的字串指派給工作`getStringTask`變數中`AccessTheWebAsync`。 下列行中的範例程式示範如何呼叫`client.GetStringAsync`和指派。  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 您可以將工作的一項承諾所視為`client.GetStringAsync`最後會產生實際的字串。 在此同時，如果`AccessTheWebAsync`有工作来做的承諾字串不依賴`client.GetStringAsync`，可以繼續工作時`client.GetStringAsync`等待。 在範例中，下列幾行的輸出，會標示為 「&3; 」，代表有機會進行獨立的工作  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
 下列陳述式會暫止中的進度`AccessTheWebAsync`時`getStringTask`會等候。  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 下圖顯示從控制流程`client.GetStringAsync`要指派給`getStringTask`和從建立`getStringTask`Await 運算子的應用程式。  
  
 ![步驟三](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace 三")  
  
 Await 運算式會暫止`AccessTheWebAsync`直到`client.GetStringAsync`傳回。 在此同時，控制項會返回至呼叫端的`AccessTheWebAsync`， `startButton_Click`。  
  
> [!NOTE]
>  一般而言，您呼叫非同步方法立即等候。 例如，下列指派可以取代先前的程式碼會建立並再等候`getStringTask`:`Dim urlContents As String = Await client.GetStringAsync("http://msdn.microsoft.com")`  
>   
>  本主題中，await 運算子會更新版本才能容納標記透過計劃的控制流程的輸出行套用。  
  
### <a name="step-four"></a>步驟四  
 宣告的傳回型別`AccessTheWebAsync`是`Task(Of Integer)`。 因此，當`AccessTheWebAsync`是暫止，它會傳回工作的整數到`startButton_Click`。 您應該了解傳回的工作不是`getStringTask`。 傳回的工作是一項新工作的整數，表示還保留在已暫停方法中， `AccessTheWebAsync`。 工作可保證一定會從`AccessTheWebAsync`工作完成時產生的整數。  
  
 下列陳述式會指派此工作以`getLengthTask`變數。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 如同`AccessTheWebAsync`，`startButton_Click`非同步工作的結果不相依的工作可以繼續 (`getLengthTask`) 之前會等候工作。 下列的輸出行代表該工作。  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 在`startButton_Click`時暫止`getLengthTask`會等候。 下列設定陳述式會暫停`startButton_Click`直到`AccessTheWebAsync`已完成。  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 在下圖中，箭頭會顯示從 await 運算式中的控制流程`AccessTheWebAsync`之值的指派`getLengthTask`，後面接著在正常處理`startButton_Click`直到`getLengthTask`會等候。  
  
 ![步驟四](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace 四")  
  
### <a name="step-five"></a>步驟五  
 當`client.GetStringAsync`訊號已完成作業，以處理`AccessTheWebAsync`發行從擱置，而且可以繼續過去的 await 陳述式。 下列程式行輸出表示繼續處理。  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 Return 陳述式中，運算元`urlContents.Length`，儲存在工作的`AccessTheWebAsync`傳回。 Await 運算式會擷取此值`getLengthTask`中`startButton_Click`。  
  
 下圖顯示的控制項之後傳送`client.GetStringAsync`(和`getStringTask`) 都已完成。  
  
 ![步驟五](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace 五")  
  
 `AccessTheWebAsync`執行到完成和控制項傳回給`startButton_Click`，它正在等待完成。  
  
### <a name="step-six"></a>步驟六  
 當`AccessTheWebAsync`await 陳述式中可以繼續完成處理的訊號`startButton_Async`。 事實上，程式有多個不需採取行動。  
  
 下列程式行輸出代表繼續中處理`startButton_Async`:  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
 Await 運算式擷取`getLengthTask`是 return 陳述式中運算元的整數值`AccessTheWebAsync`。 下列陳述式，將值指派至`contentLength`變數。  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
 下圖顯示從控制項傳回`AccessTheWebAsync`到`startButton_Click`。  
  
 ![步驟六](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace 六")  
  
## <a name="see-also"></a>另請參閱  
 [非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [非同步方法的傳回類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)   
 [逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [非同步範例︰ 非同步程式 （C# 和 Visual Basic） 中的控制流程](http://go.microsoft.com/fwlink/?LinkId=255285)
