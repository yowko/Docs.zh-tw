---
title: "存取 Web 使用 Async 和 Await (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
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
ms.openlocfilehash: 643fff648336c664961ad7956308acbaea262f61
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>逐步解說：使用 Async 和 Await 存取 Web (Visual Basic)
您可以使用所導入的功能撰寫非同步程式更容易、 更直覺[!INCLUDE[vs_dev11_long](../../../../csharp/includes/vs_dev11_long_md.md)]。 您可以撰寫非同步程式碼，使其看起來像是同步程式碼，讓編譯器處理困難的回呼函式和非同步程式碼通常需要的接續。  
  
 如需非同步功能的詳細資訊，請參閱[使用 Async 和 Await (Visual Basic) 進行非同步程式設計](../../../../visual-basic/programming-guide/concepts/async/index.md)。  
  
 本逐步解說從同步化 Windows Presentation Foundation (WPF) 應用程式開始，該應用程式會加總網站清單中的位元組數目。 然後逐步解說會藉由使用新功能，將應用程式轉換為非同步解決方案。  
  
 如果您不想要自行建置的應用程式，您可以下載 「 非同步範例︰ 存取 Web 逐步解說 （C# 和 Visual Basic） 」 從[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)。  
  
 在這個逐步解說中，您將完成下列工作：  
  
-   [若要建立 WPF 應用程式](#CreateWPFApp)  
  
-   [若要設計簡單的 WPF MainWindow](#MainWindow)  
  
-   [若要加入的參考](#AddRef)  
  
-   [加入必要的 Imports 陳述式](#ImportsState)  
  
-   [若要建立同步應用程式](#synchronous)  
  
-   [若要測試同步方案](#testSynch)  
  
-   [若要將 GetURLContents 轉換非同步方法](#GetURLContents)  
  
-   [若要將 SumPageSizes 轉換非同步方法](#SumPageSizes)  
  
-   [若要將 startButton_Click 轉換非同步方法](#startButton)  
  
-   [若要測試非同步方案](#testAsynch)  
  
-   [若要使用.NET Framework 方法來取代方法 GetURLContentsAsync](#GetURLContentsAsync)  
  
-   [範例](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a>必要條件  
 在您的電腦上必須安裝 visual Studio 2012 或更新版本。 如需詳細資訊，請參閱[Microsoft 網站](http://go.microsoft.com/fwlink/?LinkId=235233)。  
  
###  <a name="CreateWPFApp"></a>若要建立 WPF 應用程式  
  
1.  啟動 Visual Studio。  
  
2.  在功能表列上，選擇 [檔案] ****、[新增] ****、[專案] ****。  
  
     [ **新增專案** ] 對話方塊隨即開啟。  
  
3.  在**已安裝的範本**] 窗格中，選擇 [Visual Basic 中，並選擇**WPF 應用程式**從專案類型清單。  
  
4.  在**名稱**文字中，輸入`AsyncExampleWPF`，然後選擇 **確定**按鈕。  
  
     新的專案會出現在**方案總管 中**。  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a>若要設計簡單的 WPF MainWindow  
  
1.  在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。  
  
2.  如果**工具箱** 視窗未顯示，開啟**檢視** 功能表上，然後選擇 **工具箱**。  
  
3.  新增**按鈕**控制項和**文字方塊**，來控制對**MainWindow**視窗。  
  
4.  反白顯示**文字方塊**控制項並在**屬性** 視窗中，設定下列值︰  
  
    -   設定**名稱**屬性`resultsTextBox`。  
  
    -   設定**高度**屬性為 250。  
  
    -   設定**寬度**500 的屬性。  
  
    -   在**文字**索引標籤上，指定等寬字型，例如新細明體或全域等寬。  
  
5.  反白顯示**按鈕**控制項並在**屬性** 視窗中，設定下列值︰  
  
    -   設定**名稱**屬性`startButton`。  
  
    -   值變更**內容**屬性從**按鈕**至**啟動**。  
  
6.  將文字方塊和按鈕，同時出現在**MainWindow**視窗。  
  
     如需 WPF 的 XAML 設計工具的詳細資訊，請參閱[使用 XAML 設計工具建立 UI](https://docs.microsoft.com/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio)。  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a>若要加入的參考  
  
1.  在**方案總管 中**，反白顯示您的專案名稱。  
  
2.  在功能表列上選擇 **專案**，**加入參考**。  
  
     **參考管理員** 對話方塊隨即出現。  
  
3.  在對話方塊頂端，請確認您的專案的目標為.NET Framework 4.5 或更高版本。  
  
4.  在**組件**區域中，選擇  **Framework**如果它已經不選擇。  
  
5.  在名稱的清單中選取**System.Net.Http**核取方塊。  
  
6.  選擇**確定** 按鈕以關閉對話方塊。  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="ImportsState"></a>加入必要的 Imports 陳述式  
  
1.  在**方案總管] 中**MainWindow.xaml.vb，開啟捷徑功能表，然後選擇 [**檢視程式碼**。  
  
2.  新增下列`Imports`尚不存在的程式碼檔案頂端的陳述式。  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a>若要建立同步應用程式  
  
1.  在 設計 視窗，MainWindow.xaml，連按兩下**啟動** 按鈕以建立`startButton_Click`MainWindow.xaml.vb 中的事件處理常式。  
  
2.  在 MainWindow.xaml.vb，將下列程式碼複製到本文`startButton_Click`:  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     程式碼會呼叫方法，該方法會驅動應用程式 `SumPageSizes`，並且在控制項返回 `startButton_Click` 時顯示訊息。  
  
3.  同步方案的程式碼包含下列四種方法：  
  
    -   `SumPageSizes`，會從 `SetUpURLList` 取得網頁 URL 的清單，然後呼叫 `GetURLContents` 和 `DisplayResults` 以處理每個 URL。  
  
    -   `SetUpURLList`，會製作並傳回網址清單。  
  
    -   `GetURLContents`，會下載每個網站的內容，並傳回內容做為位元組陣列。  
  
    -   `DisplayResults`，會顯示每個 URL 的位元組陣列中的位元組數目。  
  
     複製下列四種方法，然後再貼入下`startButton_Click`MainWindow.xaml.vb 中的事件處理常式︰  
  
    ```vb  
    Private Sub SumPageSizes()  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetURLContents returns the contents of url as a byte array.  
            Dim urlContents As Byte() = GetURLContents(url)  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)  
    End Sub  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Function GetURLContents(url As String) As Byte()  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        Using response As WebResponse = webReq.GetResponse()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <a name="testSynch"></a>若要測試同步方案  
  
1.  選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。  
  
     應該會顯示如下列清單的輸出。  
  
    ```  
  
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832  
    msdn.microsoft.com                                            33964  
    msdn.microsoft.com/library/hh290136.aspx               225793  
    msdn.microsoft.com/library/ee256749.aspx               143577  
    msdn.microsoft.com/library/hh290138.aspx               237372  
    msdn.microsoft.com/library/hh290140.aspx               128279  
    msdn.microsoft.com/library/dd470362.aspx               157649  
    msdn.microsoft.com/library/aa578028.aspx               204457  
    msdn.microsoft.com/library/ms404677.aspx               176405  
    msdn.microsoft.com/library/ff730837.aspx               143474  
  
    Total bytes returned:  1834802  
  
    Control returned to startButton_Click.  
  
    ```  
  
     請注意，需要花費幾秒鐘以顯示計數。 在這段期間，在等候下載要求資源的同時，會封鎖 UI 執行緒。 如此一來，您無法移動、 最大化、 最小化，或甚至關閉顯示在視窗中，選擇之後**啟動** 按鈕。 這些努力會失敗，直到位元組計數開始出現為止。 如果網站沒有回應，也不會指出失敗的站台。 甚至難以停止等候以及關閉程式。  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a>若要將 GetURLContents 轉換非同步方法  
  
1.  若要轉換為非同步方案同步的方案，開始的最佳位置是在`GetURLContents`因為呼叫<xref:System.Net.HttpWebRequest>方法<xref:System.Net.HttpWebRequest.GetResponse%2A>和<xref:System.IO.Stream>方法<xref:System.IO.Stream.CopyTo%2A>會在應用程式存取 web。</xref:System.IO.Stream.CopyTo%2A> </xref:System.IO.Stream> </xref:System.Net.HttpWebRequest.GetResponse%2A> </xref:System.Net.HttpWebRequest> .NET Framework 會讓轉換變得簡單，方法是提供這兩種方法的非同步版本。  
  
     如需有關中所使用的方法`GetURLContents`，請參閱<xref:System.Net.WebRequest>。</xref:System.Net.WebRequest>  
  
    > [!NOTE]
    >  當您依照本逐步解說中的步驟時，會出現數個編譯器錯誤。 您可以略過它們，並繼續進行本逐步解說。  
  
     變更方法呼叫中的第三行`GetURLContents`從`GetResponse`非同步工作基礎<xref:System.Net.WebRequest.GetResponseAsync%2A>方法。</xref:System.Net.WebRequest.GetResponseAsync%2A>  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  `GetResponseAsync`傳回<xref:System.Threading.Tasks.Task%601>。</xref:System.Threading.Tasks.Task%601> 在此情況下，*工作傳回變數*， `TResult`，具有類型<xref:System.Net.WebResponse>。</xref:System.Net.WebResponse> 工作承諾會在已下載要求的資料及工作執行完成之後，產生實際 `WebResponse` 物件。  
  
     要擷取`WebResponse`值從工作，請套用[Await](../../../../visual-basic/language-reference/operators/await-operator.md)運算子來呼叫`GetResponseAsync`，如下列程式碼所示。  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
     `Await`運算子會暫停目前的方法，執行`GetURLContents`，直到等候的工作完成為止。 同時，控制項會返回非同步方法的呼叫端。 在此範例中，目前方法是 `GetURLContents`，呼叫端是 `SumPageSizes`。 當工作完成時，承諾的 `WebResponse` 物件會以等候工作之值的形式產生，而且會指派給變數 `response`。  
  
     The previous statement can be separated into the following two statements to clarify what happens.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
     對 `webReq.GetResponseAsync` 的呼叫會傳回 `Task(Of WebResponse)` 或 `Task<WebResponse>`。 然後`Await`運算子會套用至擷取工作`WebResponse`值。  
  
     If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied. For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  因為您將新增`Await`運算子上一個步驟中的，編譯器就會發生錯誤。 運算子只能用於與標記的方法，[非同步](../../../../visual-basic/language-reference/modifiers/async.md)修飾詞。 當您重複轉換步驟以將對 `CopyTo` 的呼叫取代為對 `CopyToAsync` 的呼叫時，略過錯誤。  
  
    -   變更至<xref:System.IO.Stream.CopyToAsync%2A>。</xref:System.IO.Stream.CopyToAsync%2A>呼叫的方法名稱  
  
    -   `CopyTo` 或 `CopyToAsync` 方法會將位元組複製到其引數，`content`，並不會傳回有意義的值。 在同步版本中，呼叫 `CopyTo` 是簡單的陳述式，不會傳回值。 非同步版本， `CopyToAsync`，傳回<xref:System.Threading.Tasks.Task>。</xref:System.Threading.Tasks.Task> 工作函式，例如 "Task(void)"，讓方法等候。 將 `Await` 或 `await` 套用至對 `CopyToAsync` 的呼叫，如下列程式碼所示。  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
         前一個陳述式縮寫下列兩行程式碼。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
4.  `GetURLContents` 中還需要完成的工作是調整方法簽章。 您可以使用`Await`運算子只能在方法中會標示[非同步](../../../../visual-basic/language-reference/modifiers/async.md)修飾詞。 新增修飾詞來標記方法，做為*非同步方法*，如下列程式碼所示。  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
5.  非同步方法的傳回型別只能<xref:System.Threading.Tasks.Task>， <xref:System.Threading.Tasks.Task%601>。</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task> 在 Visual Basic 中，方法必須是 `Function`，會傳回 `Task` 或 `Task(Of T)`，或者方法必須是 `Sub`。 一般而言，`Sub`方法只適用於非同步事件處理常式，其中`Sub`需要。 在其他情況下，您會使用`Task(T)`完成的方法有[傳回](../../../../visual-basic/language-reference/statements/return-statement.md)陳述式所傳回的值型別 T，而且您使用`Task`如果完成的方法不會傳回有意義的值。  
  
     如需詳細資訊，請參閱[非同步傳回類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。  
  
     方法 `GetURLContents` 有 return 陳述式，陳述式會傳回位元組陣列。 因此，非同步版本的傳回類型是 Task(T)，其中 T 是位元組陣列。 在方法簽章中進行下列變更：  
  
    -   傳回的型別變更`Task(Of Byte())`。  
  
    -   依照慣例，非同步方法的名稱會以 "Async" 結尾，所以重新命名方法 `GetURLContentsAsync`。  
  
     下列程式碼會顯示這些變更。  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     只要這幾個變更，`GetURLContents` 至非同步方法的轉換就能完成。  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a>若要將 SumPageSizes 轉換非同步方法  
  
1.  針對 `SumPageSizes` 重複上述程序的步驟。 首先，將對 `GetURLContents` 的呼叫變更為非同步呼叫。  
  
    -   如果您尚未這麼做，請變更方法的名稱，該方法是從 `GetURLContents` 呼叫至 `GetURLContentsAsync`。  
  
    -   套用`Await`工作，`GetURLContentsAsync`傳回取得位元組陣列值。  
  
     下列程式碼會顯示這些變更。  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     前一個指派縮寫下列兩行程式碼。  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
  
    ```  
  
2.  在方法簽章中進行下列變更：  
  
    -   方法標`Async`修飾詞。  
  
    -   將 "Async" 加入至方法名稱。  
  
    -   這次沒有任何工作傳回變數，T，因為 `SumPageSizesAsync` 並未傳回 T 的值。(此方法沒有任何`Return`陳述式。)不過，方法必須傳回 `Task` 才可以等候。 因此，變更方法型別從`Sub`到`Function`。 函式的傳回類型是 `Task`。  
  
     下列程式碼會顯示這些變更。  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     `SumPageSizes` 至 `SumPageSizesAsync` 的轉換完成。  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a>若要將 startButton_Click 轉換非同步方法  
  
1.  如果您尚未這麼做，請在事件處理常式中，將呼叫方法的名稱從 `SumPageSizes` 變更為 `SumPageSizesAsync`。  
  
2.  因為 `SumPageSizesAsync` 是非同步方法，在事件處理常式中變更程式碼以等候結果。  
  
     對 `SumPageSizesAsync` 的呼叫會鏡射 `GetURLContentsAsync` 中對 `CopyToAsync` 的呼叫。 呼叫會傳回 `Task`，而不是 `Task(T)`。  
  
     如同先前的程序，您可以使用一個陳述式或兩個陳述式轉換呼叫。 下列程式碼會顯示這些變更。  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  若要避免不小心重新輸入此作業，將下列陳述式加入頂端`startButton_Click`停用**啟動** 按鈕。  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     您可以在事件處理常式結尾重新啟用按鈕。  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     如需重新進入的詳細資訊，請參閱[處理非同步應用程式 (Visual Basic) 中的重新進入](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)。  
  
4.  最後，加入`Async`修飾詞新增至宣告，讓事件處理常式可以等候`SumPagSizesAsync`。  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     一般而言，事件處理常式的名稱並沒有改變。 傳回的型別並不會變更為`Task`因為事件處理常式必須是`Sub`在 Visual Basic 中的程序。  
  
     專案從同步到非同步處理的轉換已完成。  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a>若要測試非同步方案  
  
1.  選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。  
  
2.  類似同步方案的輸出應該會顯示。 但是，請注意下列差異。  
  
    -   處理完成之後，結果不會同時發生。 例如，這兩個程式在 `startButton_Click` 中都包含程式碼行，會清除文字方塊。 目的是要清除文字方塊中，執行之間，如果您選擇**啟動**按鈕後出現結果集中的第二個時間。 在同步版本中，當下載完成且 UI 執行緒可以執行其他工作時，會在第二次顯示計數之前，清除文字方塊。 非同步版本，在文字方塊中會清除您選擇之後，立即**啟動** 按鈕。  
  
    -   最重要的是，不會在下載期間封鎖 UI 執行緒。 您可以移動視窗或調整其大小，同時下載、計算及顯示 Web 資源。 如果其中一個網站變慢，或沒有回應，您可以取消作業選擇**關閉**按鈕 (在右上角的紅色欄位 x)。  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a>若要使用.NET Framework 方法來取代方法 GetURLContentsAsync  
  
1.  .NET Framework 4.5 提供許多您可以使用的非同步方法。 其中，<xref:System.Net.Http.HttpClient>方法<xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>，並在這個逐步解說什麼需要。</xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29> </xref:System.Net.Http.HttpClient> 您可以使用這個方法，而不是 `GetURLContentsAsync` 方法，這是您在先前的程序中建立的方法。  
  
     第一個步驟是在方法 `SumPageSizesAsync` 中建立 `HttpClient` 物件。 在方法的開頭，加入下列宣告。  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  在 `SumPageSizesAsync,` 中將對 `GetURLContentsAsync` 方法的呼叫取代為對 `HttpClient` 方法的呼叫。  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  移除或取消註解您撰寫的 `GetURLContentsAsync` 方法。  
  
4.  選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。  
  
     此版本之專案的行為應該符合「測試非同步方案」程序描述的行為，而且您只需要投入較少的精力。  
  
##  <a name="BKMK_CompleteCodeExamples"></a>範例  
 下列程式碼包含使用您撰寫的 `GetURLContentsAsync` 方法，從同步轉換為非同步方案的完整範例。 請注意，它極為類似原始的同步方案。  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        ' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
            ' The previous line abbreviates the following two assignment statements.  
  
            '//<snippet21>  
            ' GetURLContentsAsync returns a task. At completion, the task  
            ' produces a byte array.  
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
  
            ' The previous statement abbreviates the following two statements.  
  
            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
            'Using response As WebResponse = Await responseTask  
  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                Await responseStream.CopyToAsync(content)  
  
                ' The previous statement abbreviates the following two statements.  
  
                ' CopyToAsync returns a Task, not a Task<T>.  
                'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
                ' When copyTask is completed, content contains a copy of  
                ' responseStream.  
                'Await copyTask  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
 下列程式碼包含使用 `HttpClient` 方法 `GetByteArrayAsync` 之方案的完整範例。  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetByteArrayAsync returns a task. At completion, the task  
            ' produces a byte array.  
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
            ' The following two lines can replace the previous assignment statement.  
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a>另請參閱  
 [非同步範例︰ 存取 Web 逐步解說 （C# 和 Visual Basic）](http://go.microsoft.com/fwlink/?LinkId=255191)   
 [Await 運算子](../../../../visual-basic/language-reference/operators/await-operator.md)   
 [非同步處理](../../../../visual-basic/language-reference/modifiers/async.md)   
 [非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [非同步方法的傳回類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)   
 [工作為基礎的非同步程式設計 (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847)   
 [如何︰ 使用 Task.WhenAll (Visual Basic) 來擴充非同步逐步解說](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)   
 [如何︰ 同時發出多個 Web 要求使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
