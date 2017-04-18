---
title: "逐步解說：在 WPF 應用程式中快取應用程式資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "快取 [.NET Framework]"
  - "快取 [WPF]"
  - "逐步解說 [WPF], 快取"
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# 逐步解說：在 WPF 應用程式中快取應用程式資料
快取可讓您將資料儲存在記憶體中，以進行快速存取。  再次存取資料時，應用程式可以從快取取得資料，而不需要從原始來源擷取資料。  這樣可以改善效能和延展性。  此外，當資料來源暫時無法使用時，快取也可讓資料可供使用。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]提供類別，可讓您使用中的快取[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]應用程式。  這些類別都位於<xref:System.Runtime.Caching>命名空間。  
  
> [!NOTE]
>  <xref:System.Runtime.Caching> 命名空間是 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 所新增的。  這個命名空間會讓快取可供所有 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 應用程式使用。  在舊版 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中，快取僅能從 <xref:System.Web> 命名空間中使用，因此需要相依於 ASP.NET 類別。  
  
 這個逐步解說會示範如何使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中，當做 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式之一部分提供的快取功能。  在此逐步解說中，您會快取文字檔案的內容。  
  
 本逐步解說所述的工作包括下列各項：  
  
-   建立 WPF 應用程式專案。  
  
-   加入 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 的參考。  
  
-   初始化快取。  
  
-   加入包含文字檔內容的快取項目。  
  
-   為快取項目提供收回原則。  
  
-   監控快取檔案的路徑，並向快取執行個體通知受監控之項目的變更。  
  
## 必要條件  
 若要完成這個逐步解說，您必須要有：  
  
-   Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]。  
  
-   包含少量文字的文字檔。  \(您將會在訊息方塊中顯示這個文字檔的內容。\) 本逐步解說中的程式碼將假設您正在使用下列檔案：  
  
     `c:\cache\cacheText.txt`  
  
     但是，您可以使用任何文字檔，並對此逐步解說中的程式碼進行小幅變更。  
  
## 建立 WPF 應用程式專案  
 您一開始會建立 WPF 應用程式專案。  
  
#### 若要建立 WPF 應用程式  
  
1.  啟動 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]。  
  
2.  依序按一下 \[**檔案**\] 功能表中的 \[**新增**\] 和 \[**新增專案**\]。  
  
     \[**新增專案**\] 對話方塊隨即出現。  
  
3.  在 \[**已安裝的範本**\] 底下，選取您要使用的程式語言 \(\[**Visual Basic**\] 或 \[**Visual C\#**\]\)。  
  
4.  在 \[**新增專案**\] 對話方塊中，選取 \[**WPF 應用程式**\]。  
  
    > [!NOTE]
    >  如果您沒有看到 \[**WPF 應用程式**\] 範本，請確定將目標設定為支援 WPF 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 版本。  請在 \[**新增專案**\] 對話方塊的清單中選取 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
5.  在 \[**名稱**\] 文字方塊中，輸入專案的名稱。  例如，您可輸入 WPFCaching。  
  
6.  選取 \[**為方案建立目錄**\] 核取方塊。  
  
7.  按一下 \[**確定**\]。  
  
     WPF 設計工具會在 \[**設計**\] 檢視中開啟，並顯示 MainWindow.xaml 檔案。  [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 會建立 \[**我的專案**\] 資料夾、Application.xaml 檔案和 MainWindow.xaml 檔案。  
  
## 以 .NET Framework 為目標並加入快取組件的參考  
 預設情況下，WPF 應用程式會以 [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)] 為目標。  若要在 WPF 應用程式中使用 <xref:System.Runtime.Caching> 命名空間，應用程式必須以 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 為目標 \(而非 [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]\)，且必須包含此命名空間的參考。  
  
 因此，下一個步驟是變更 .NET Framework 目標，並加入 <xref:System.Runtime.Caching> 命名空間的參考。  
  
> [!NOTE]
>  在 Visual Basic 專案和 Visual C\# 專案中變更 .NET Framework 目標的程序不一樣。  
  
#### 若要在 Visual Basic 中變更目標 .NET Framework  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下專案名稱，然後按一下 \[**屬性**\]。  
  
     應用程式的 \[屬性\] 視窗隨即顯示。  
  
2.  按一下 \[**編譯**\] 索引標籤。  
  
3.  在視窗底部，按一下 \[**進階編譯選項**\]。  
  
     \[**進階編譯選項**\] 對話方塊隨即顯示。  
  
4.  在**目標 framework \(所有組態\)** 清單中，選取[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  \(請勿選取 \[ [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]。\)  
  
5.  按一下 \[**確定**\]。  
  
     \[**目標 Framework 變更**\] 對話方塊隨即顯示。  
  
6.  按一下 \[**目標 Framework 變更**\] 對話方塊中的 \[**是**\]。  
  
     專案隨即關閉再重新開啟。  
  
7.  依照下列步驟，加入快取組件的參考：  
  
    1.  以滑鼠右鍵按一下 \[**方案總管**\] 中的專案名稱，然後按一下 \[**加入參考**\]。  
  
    2.  依序選取 \[**.NET**\] 索引標籤和 \[`System.Runtime.Caching`\]，然後按一下 \[**確定**\]。  
  
#### 若要在 Visual C\# 專案中變更目標 .NET Framework  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下專案名稱，然後按一下 \[**屬性**\]。  
  
     應用程式的 \[屬性\] 視窗隨即顯示。  
  
2.  按一下 \[**應用程式**\] 索引標籤。  
  
3.  選取 \[**目標 Framework**\] 清單中的 \[[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]\]   \(請勿選取 \[**.NET Framework 4 Client Profile**\]\)。  
  
4.  依照下列步驟，加入快取組件的參考：  
  
    1.  以滑鼠右鍵按一下 \[**參考**\] 資料夾，然後按一下 \[**加入參考**\]。  
  
    2.  依序選取 \[**.NET**\] 索引標籤和 \[`System.Runtime.Caching`\]，然後按一下 \[**確定**\]。  
  
## 將按鈕加入至 WPF 視窗  
 接下來，您會加入按鈕，並建立按鈕 `Click` 事件的事件處理常式。  稍後，您會加入程式碼，以便在按下按鈕時會快取並顯示文字檔的內容。  
  
#### 若要加入按鈕控制項  
  
1.  在 \[**方案總管**\] 中，按兩下 MainWindow.xaml 檔案將它開啟。  
  
2.  從 \[**工具箱**\] 的 \[**通用 WPF 控制項**\] 底下，將 `Button` 控制項拖曳至 `MainWindow` 視窗。  
  
3.  在 \[**屬性**\] 視窗中，設定 `Button` 控制項的 `Content` 屬性為 \[取得快取\]。  
  
## 初始化快取及將項目快取  
 接下來，您會加入程式碼來執行下列工作：  
  
-   建立快取類別的執行個體，也就是說，您會具現化新的 <xref:System.Runtime.Caching.MemoryCache> 物件。  
  
-   指定快取使用 <xref:System.Runtime.Caching.HostFileChangeMonitor> 物件來監控文字檔的變更。  
  
-   讀取文字檔，並快取其內容當做快取項目。  
  
-   顯示快取文字檔的內容。  
  
#### 若要建立快取物件  
  
1.  按兩下您剛才加入的按鈕，以便在 MainWindow.xaml.cs 或 MainWindow.Xaml.vb 檔案中建立事件處理常式。  
  
2.  在檔案最上方 \(類別宣告之前\) 加入下列 `Imports` \(Visual Basic\) 或 `using` \(C\#\) 陳述式：  
  
    ```csharp  
    using System.Runtime.Caching;  
    using System.IO;  
    ```  
  
    ```vb  
    Imports System.Runtime.Caching  
    Imports System.IO  
    ```  
  
3.  在事件處理常式中，加入下列程式碼來具現化快取物件：  
  
    ```csharp  
    ObjectCache cache = MemoryCache.Default;  
    ```  
  
    ```vb  
    Dim cache As ObjectCache = MemoryCache.Default  
    ```  
  
     <xref:System.Runtime.Caching.ObjectCache> 類別是內建類別，可提供記憶體中物件快取。  
  
4.  加入下列程式碼，以讀取名為 `filecontents` 的快取項目的內容：  
  
    ```vb  
    Dim fileContents As String = TryCast(cache("filecontents"), String)  
    ```  
  
    ```csharp  
    string fileContents = cache["filecontents"] as string;  
    ```  
  
5.  加入下列程式碼，以檢查名為 `filecontents` 的快取項目是否存在：  
  
    ```vb  
    If fileContents Is Nothing Then  
  
    End If  
    ```  
  
    ```csharp  
    if (fileContents == null)  
    {  
  
    }  
    ```  
  
     如果指定的快取項目不存在，您必須讀取此文字檔，並將它當做快取項目加入至快取。  
  
6.  在 `if/then` 區塊中加入下列程式碼來建立新的 <xref:System.Runtime.Caching.CacheItemPolicy> 物件，該物件指定快取項目在 10 秒鐘之後到期。  
  
    ```vb  
    Dim policy As New CacheItemPolicy()  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)  
    ```  
  
    ```csharp  
    CacheItemPolicy policy = new CacheItemPolicy();  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);  
    ```  
  
     如果未提供任何收回或到期資訊，預設值會是 <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>，這表示快取項目的到期時間不是根據絕對時間。  只有當有記憶體壓力時，快取項目才會到期。  最佳作法是永遠都要明確提供絕對或側線到期。  
  
7.  在 `if/then` 區塊內您於上一個步驟加入的程式碼後面加入下列程式碼，以建立您想要監控之檔案路徑的集合，並將文字檔的路徑加入至集合中：  
  
    ```vb  
    Dim filePaths As New List(Of String)()  
    filePaths.Add("c:\cache\cacheText.txt")  
    ```  
  
    ```csharp  
    List<string> filePaths = new List<string>();  
    filePaths.Add("c:\\cache\\cacheText.txt");  
    ```  
  
    > [!NOTE]
    >  如果您想要使用的文字檔不是 `c:\cache\cacheText.txt`，請指定您要使用之文字檔的路徑。  
  
8.  在您於前一個步驟加入的程式碼後面加入下列程式碼，以便將新的 <xref:System.Runtime.Caching.HostFileChangeMonitor> 物件加入至快取項目的變更監視器集合中：  
  
    ```vb  
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))  
    ```  
  
    ```csharp  
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));  
    ```  
  
     <xref:System.Runtime.Caching.HostFileChangeMonitor> 物件會監控文字檔的路徑，並通知快取是否發生變更。  在此範例中，如果檔案的內容變更，快取項目就會到期。  
  
9. 在您於前一個步驟加入的程式碼後面，加入下列程式碼來讀取文字檔的內容：  
  
    ```vb  
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()  
    ```  
  
    ```csharp  
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + + "\n" + DateTime.Now;   
    ```  
  
     加入日期和時間的時間戳記，是為了讓您可以查看快取項目何時到期。  
  
10. 在您於前一個步驟加入的程式碼後面加入下列程式碼，以便將檔案內容當做 <xref:System.Runtime.Caching.CacheItem> 執行個體加入快取物件中：  
  
    ```vb  
    cache.Set("filecontents", fileContents, policy)  
    ```  
  
    ```csharp  
    cache.Set("filecontents", fileContents, policy);  
    ```  
  
     藉由將稍早建立的 <xref:System.Runtime.Caching.CacheItemPolicy> 物件當做參數進行傳遞，即可指定有關應該如何收回快取項目的資訊。  
  
11. 在 `if/then` 區塊後面加入下列程式碼，以便在訊息方塊中顯示快取檔案內容：  
  
    ```vb  
    MessageBox.Show(fileContents)  
    ```  
  
    ```csharp  
    MessageBox.Show(fileContents);  
    ```  
  
12. 在 \[**建置**\] 功能表上，按一下 \[**建置 WPFCaching**\] 建置專案。  
  
## 測試 WPF 應用程式中的快取  
 現在，可以開始測試應用程式。  
  
#### 若要測試 WPF 應用程式中的快取  
  
1.  按 CTRL\+F5 執行應用程式。  
  
     `MainWindow` 視窗隨即顯示。  
  
2.  按一下 \[**取得快取**\]。  
  
     文字檔中的快取內容就會顯示在訊息方塊內。  請注意檔案上的時間戳記。  
  
3.  關閉訊息方塊，然後再次按下 \[**取得快取**\]**。**  
  
     時間戳記維持不變。  這表示會顯示快取內容。  
  
4.  等候 10 秒鐘或更長的時間，然後再次按一下 \[**取得快取**\]。  
  
     這次會顯示新的時間戳記。  這表示此原則讓快取項目到期，並顯示新的快取內容。  
  
5.  在文字編輯器中開啟您建立的文字檔。  還不要做任何變更。  
  
6.  關閉訊息方塊，然後再次按下 \[**取得快取**\]**。**  
  
     再次注意時間戳記。  
  
7.  對文字檔進行變更，然後儲存檔案。  
  
8.  關閉訊息方塊，然後再次按下 \[**取得快取**\]。  
  
     此訊息方塊就會包含文字檔中的更新內容以及新的時間戳記。  這表示當您變更檔案時，即使絕對逾時期間尚未到期，主機檔案變更監視器也會立即收回快取項目。  
  
    > [!NOTE]
    >  您可以將收回時間提高為 20 秒或更長的時間，讓您有更多時間可以在檔案中進行變更。  
  
## 程式碼範例  
 當您完成本逐步解說之後，您所建立之專案的程式碼將會與下列範例類似。  
  
 [!code-csharp[CachingWPFApplications#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]  
  
## 請參閱  
 <xref:System.Runtime.Caching.MemoryCache>   
 <xref:System.Runtime.Caching.ObjectCache>   
 <xref:System.Runtime.Caching>   
 [.NET Framework 應用程式中的快取](../../../../docs/framework/performance/caching-in-net-framework-applications.md)