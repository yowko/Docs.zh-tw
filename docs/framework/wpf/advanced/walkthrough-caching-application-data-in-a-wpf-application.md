---
title: "逐步解說：在 WPF 應用程式中快取應用程式資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81d808b982852d5cc6dc187a3c8389748a0dc0bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>逐步解說：在 WPF 應用程式中快取應用程式資料
快取可讓您將資料儲存在記憶體中，以進行快速存取。 一次存取資料時，應用程式可以從快取，而要擷取的原始來源取得資料。 這可以改善效能和延展性。 此外，暫時無法使用資料來源時，快取可讓資料可用。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]提供類別，可讓您使用中的快取[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]應用程式。 這些類別位於<xref:System.Runtime.Caching>命名空間。  
  
> [!NOTE]
>  <xref:System.Runtime.Caching>命名空間的新[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。 此命名空間可讓快取可供所有[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]應用程式。 在舊版 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中，快取只能用於 <xref:System.Web> 命名空間中，因此需要與 ASP.NET 類別的相依性。  
  
 本逐步解說會示範如何使用所提供的快取功能[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]一部分[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式。 逐步解說中，您快取之文字檔的內容。  
  
 本逐步解說所述的工作包括下列各項：  
  
-   建立 WPF 應用程式專案。  
  
-   將參考加入至[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
-   正在初始化快取。  
  
-   加入快取項目包含文字檔案的內容。  
  
-   快取項目的提供的收回原則。  
  
-   監視快取檔案的路徑與通知有關的快取執行個體變更受監視的項目。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]。  
  
-   包含少量文字的文字檔案。 （您會在訊息方塊中顯示文字檔案的內容）。逐步解說中所述的程式碼會假設您使用下列檔案：  
  
     `c:\cache\cacheText.txt`  
  
     不過，您可以使用任何文字檔案，並在本逐步解說的程式碼中進行小量變更。  
  
## <a name="creating-a-wpf-application-project"></a>建立 WPF 應用程式專案  
 您將開始建立 WPF 應用程式專案。  
  
#### <a name="to-create-a-wpf-application"></a>建立 WPF 應用程式  
  
1.  啟動 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]。  
  
2.  在**檔案**功能表上，按一下 **新增**，然後按一下 **新專案**。  
  
     [新增專案] 對話方塊隨即出現。  
  
3.  在下**已安裝的範本**，選取您想要使用的程式設計語言 (**Visual Basic**或**Visual C#**)。  
  
4.  在**新專案**對話方塊中，選取**WPF 應用程式**。  
  
    > [!NOTE]
    >  如果您沒有看到**WPF 應用程式**範本，請確定您的目標版本[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]支援 WPF。 在**新專案**對話方塊中，選取[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]從清單中。  
  
5.  在**名稱**文字方塊中，輸入您的專案名稱。 例如，您可以輸入**WPFCaching**。  
  
6.  選取**為方案建立目錄**核取方塊。  
  
7.  按一下 [確定 **Deploying Office Solutions**]。  
  
     WPF 設計工具會在中開啟**設計**檢視，並顯示 MainWindow.xaml 檔案。 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]建立**我的專案**資料夾、 Application.xaml 檔案和 MainWindow.xaml 檔案。  
  
## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>以.NET Framework 為目標，並加入快取的組件的參考  
 根據預設，WPF 應用程式目標[!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]。 若要使用<xref:System.Runtime.Caching>WPF 應用程式中的命名空間，應用程式必須為目標[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)](不[!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)])，而且必須包含命名空間的參考。  
  
 因此下, 一個步驟為變更.NET Framework 目標，並將參考加入<xref:System.Runtime.Caching>命名空間。  
  
> [!NOTE]
>  變更.NET Framework 目標的程序是不同的 Visual C# 專案和 Visual Basic 專案中。  
  
#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>若要變更的目標.NET Framework 在 Visual Basic 中  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下專案名稱，然後按**屬性**。  
  
     應用程式的 [屬性] 視窗會顯示。  
  
2.  按一下 [編譯] 索引標籤。  
  
3.  在視窗底部，按一下 **進階編譯選項...**.  
  
     **進階編譯器設定**對話方塊隨即出現。  
  
4.  在**目標 framework （所有組態）**清單中，選取[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。 (請勿選取[!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]。)  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
     **目標 Framework 變更**對話方塊隨即出現。  
  
6.  在**目標 Framework 變更**對話方塊中，按一下 **是**。  
  
     專案已關閉，並再重新開啟。  
  
7.  新增快取的組件的參考，依照下列步驟：  
  
    1.  在**方案總管 中**，以滑鼠右鍵按一下專案名稱，然後按一下**加入參考**。  
  
    2.  選取**.NET**索引標籤上，選取`System.Runtime.Caching`，然後按一下 **確定**。  
  
#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>若要變更 Visual C# 專案中的目標.NET Framework  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下專案名稱，然後按一下**屬性**。  
  
     應用程式的 [屬性] 視窗會顯示。  
  
2.  按一下 [應用程式]  索引標籤。  
  
3.  在**目標 framework**清單中，選取[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。 (請勿選取**.NET Framework 4 Client Profile**。)  
  
4.  新增快取的組件的參考，依照下列步驟：  
  
    1.  以滑鼠右鍵按一下**參考**資料夾，然後按一下**加入參考**。  
  
    2.  選取**.NET**索引標籤上，選取`System.Runtime.Caching`，然後按一下 **確定**。  
  
## <a name="adding-a-button-to-the-wpf-window"></a>將按鈕加入至 WPF 視窗  
 接下來，您會在 加入按鈕控制項，以及建立的按鈕的事件處理常式`Click`事件。 稍後您將加入程式碼，因此當您按一下按鈕時，會快取文字檔案的內容，並顯示。  
  
#### <a name="to-add-a-button-control"></a>若要將按鈕控制項  
  
1.  在**方案總管 中**，按兩下 MainWindow.xaml 檔案，將它開啟。  
  
2.  從**工具箱**下**一般 WPF 控制項**，拖曳`Button`控制權傳輸至`MainWindow`視窗。  
  
3.  在**屬性**視窗中，將`Content`屬性`Button`控制權傳輸至**取得快取**。  
  
## <a name="initializing-the-cache-and-caching-an-entry"></a>初始化快取和快取項目  
 接下來，您將加入程式碼執行下列工作：  
  
-   建立快取類別的執行個體 — 也就是您會具現化新<xref:System.Runtime.Caching.MemoryCache>物件。  
  
-   指定快取佔用<xref:System.Runtime.Caching.HostFileChangeMonitor>物件來監視在文字檔案中的變更。  
  
-   讀取文字檔並快取其內容為快取項目。  
  
-   顯示快取的文字檔的內容。  
  
#### <a name="to-create-the-cache-object"></a>建立快取物件  
  
1.  按兩下您剛才加入才能 MainWindow.xaml.cs 或 MainWindow.Xaml.vb 檔案中建立事件處理常式的按鈕。  
  
2.  （之前在類別宣告中） 的檔案頂端新增下列`Imports`(Visual Basic) 或`using`(C#) 陳述式：  
  
    ```csharp  
    using System.Runtime.Caching;  
    using System.IO;  
    ```  
  
    ```vb  
    Imports System.Runtime.Caching  
    Imports System.IO  
    ```  
  
3.  在此事件處理常式，加入下列程式碼來具現化的快取物件：  
  
    ```csharp  
    ObjectCache cache = MemoryCache.Default;  
    ```  
  
    ```vb  
    Dim cache As ObjectCache = MemoryCache.Default  
    ```  
  
     <xref:System.Runtime.Caching.ObjectCache>類別是內建的類別，提供記憶體中物件快取。  
  
4.  加入下列程式碼會讀取名為快取項目的內容`filecontents`:  
  
    ```vb  
    Dim fileContents As String = TryCast(cache("filecontents"), String)  
    ```  
  
    ```csharp  
    string fileContents = cache["filecontents"] as string;  
    ```  
  
5.  加入下列程式碼，檢查是否快取項目名稱`filecontents`存在：  
  
    ```vb  
    If fileContents Is Nothing Then  
  
    End If  
    ```  
  
    ```csharp  
    if (fileContents == null)  
    {  
  
    }  
    ```  
  
     如果指定的快取項目不存在，您必須閱讀文字檔案，並將它當做快取項目加入至快取。  
  
6.  在`if/then`封鎖，加入下列程式碼來建立新的<xref:System.Runtime.Caching.CacheItemPolicy>物件，指定快取項目，在 10 秒後到期。  
  
    ```vb  
    Dim policy As New CacheItemPolicy()  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)  
    ```  
  
    ```csharp  
    CacheItemPolicy policy = new CacheItemPolicy();  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);  
    ```  
  
     如果未不提供任何收回或到期資訊，則預設值是<xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>，這表示快取項目永遠不過期根據只在絕對時間。 相反地，快取項目過期時，才有記憶體不足的壓力。 最佳做法，您應該一律明確地提供絕對或板到期。  
  
7.  內部`if/then`區塊並遵循您在上一個步驟中加入的程式碼，加入下列程式碼來建立您想要監視，並將文字檔的路徑新增至集合的檔案路徑的集合：  
  
    ```vb  
    Dim filePaths As New List(Of String)()  
    filePaths.Add("c:\cache\cacheText.txt")  
    ```  
  
    ```csharp  
    List<string> filePaths = new List<string>();  
    filePaths.Add("c:\\cache\\cacheText.txt");  
    ```  
  
    > [!NOTE]
    >  如果您想要使用的文字檔不`c:\cache\cacheText.txt`，指定文字檔案是您想要使用的路徑。  
  
8.  遵循您在上一個步驟中，加入的程式碼加入下列程式碼，將新<xref:System.Runtime.Caching.HostFileChangeMonitor>的變更集合的物件會監視快取項目：  
  
    ```vb  
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))  
    ```  
  
    ```csharp  
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));  
    ```  
  
     <xref:System.Runtime.Caching.HostFileChangeMonitor>物件監控文字檔案的路徑，以及通知的快取，如果發生變更。 在此範例中，如果檔案的內容變更時，將到期快取項目。  
  
9. 您在上一個步驟中加入的程式碼之後, 加入下列程式碼讀取文字檔的內容：  
  
    ```vb  
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()  
    ```  
  
    ```csharp  
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + + "\n" + DateTime.Now;   
    ```  
  
     讓您將能夠看到快取項目過期時，會加入日期和時間戳記。  
  
10. 遵循您在上一個步驟中，加入的程式碼加入下列程式碼，將檔案的內容插入至快取物件，做為<xref:System.Runtime.Caching.CacheItem>執行個體：  
  
    ```vb  
    cache.Set("filecontents", fileContents, policy)  
    ```  
  
    ```csharp  
    cache.Set("filecontents", fileContents, policy);  
    ```  
  
     指定有關如何收回快取項目藉由傳遞資訊<xref:System.Runtime.Caching.CacheItemPolicy>您稍早建立做為參數的物件。  
  
11. 之後`if/then`封鎖，加入下列程式碼顯示在訊息方塊中的快取的檔案內容：  
  
    ```vb  
    MessageBox.Show(fileContents)  
    ```  
  
    ```csharp  
    MessageBox.Show(fileContents);  
    ```  
  
12. 在**建置**功能表上，按一下 **建置 WPFCaching**建置專案。  
  
## <a name="testing-caching-in-the-wpf-application"></a>測試 WPF 應用程式中的快取  
 您現在可以測試應用程式。  
  
#### <a name="to-test-caching-in-the-wpf-application"></a>若要測試的 WPF 應用程式中的快取  
  
1.  按 CTRL+F5 執行應用程式。  
  
     `MainWindow`  視窗隨即顯示。  
  
2.  按一下**取得快取**。  
  
     從文字檔案快取的內容會顯示在訊息方塊。 請注意，在檔案上的時間戳記。  
  
3.  關閉訊息方塊，然後按一下 **取得快取**再次**。**  
  
     時間戳記不變。 這表示會顯示快取的內容。  
  
4.  等候 10 秒或更久，然後按**取得快取**一次。  
  
     此時會顯示新的時間戳記。 這表示此原則可讓過期的快取項目，而且會顯示新的快取的內容。  
  
5.  在文字編輯器中，開啟您所建立的文字檔案。 還不要進行任何變更。  
  
6.  關閉訊息方塊，然後按一下 **取得快取**再次**。**  
  
     再次注意時間戳記。  
  
7.  變更文字檔案，然後儲存檔案。  
  
8.  關閉訊息方塊，然後按一下 **取得快取**一次。  
  
     此訊息方塊包含的文字檔案與新時間戳記更新的內容。 這表示，主機檔案變更監視器收回快取項目立即當您變更該檔案，即使絕對逾時期間已過期。  
  
    > [!NOTE]
    >  您可以增加到 20 秒或更久允許更多的時間，讓您在檔案中變更的收回時間。  
  
## <a name="code-example"></a>程式碼範例  
 您已經完成此逐步解說之後，您所建立的專案的程式碼將類似下列範例。  
  
 [!code-csharp[CachingWPFApplications#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Runtime.Caching.MemoryCache>  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching>  
 [.NET Framework 應用程式中的快取](../../../../docs/framework/performance/caching-in-net-framework-applications.md)
