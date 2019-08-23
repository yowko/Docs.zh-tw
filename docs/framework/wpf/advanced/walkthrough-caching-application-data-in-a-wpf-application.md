---
title: 逐步解說：在 WPF 應用程式中快取應用程式資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: 2609a54ce8ba2076c35567fe5bc1d9961f6fef3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942066"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>逐步解說：在 WPF 應用程式中快取應用程式資料
快取可讓您將資料儲存在記憶體中，以進行快速存取。 重新存取資料時，應用程式可以從快取中取得資料，而不是從原始來源進行擷取。 這可以改善效能和延展性。 此外，暫時無法使用資料來源時，快取可讓資料可用。

 .NET Framework 提供的類別可讓您在 .NET Framework 應用程式中使用快取。 這些類別位於<xref:System.Runtime.Caching>命名空間中。

> [!NOTE]
> <xref:System.Runtime.Caching>命名空間是 .NET Framework 4 中的新功能。 這個命名空間可讓所有 .NET Framework 應用程式使用快取。 在舊版的 .NET Framework 中, 快取僅適用于<xref:System.Web>命名空間, 因此需要 ASP.NET 類別的相依性。

 本逐步解說將示範如何使用 .NET Framework 中提供的快取功能作為[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式的一部分。 在此逐步解說中, 您會快取文字檔的內容。

 本逐步解說所述的工作包括下列各項：

- 建立 WPF 應用程式專案。

- 將參考加入至 .NET Framework 4。

- 初始化快取。

- 加入包含文字檔內容的快取專案。

- 提供快取專案的收回原則。

- 監視快取檔案的路徑, 並通知快取實例有關受監視專案的變更。

## <a name="prerequisites"></a>必要條件
 若要完成這個逐步解說，您將需要：

- Microsoft Visual Studio 2010。

- 包含少量文字的文字檔。 (您會在訊息方塊中顯示文字檔的內容)。本逐步解說中說明的程式碼假設您正在使用下列檔案:

     `c:\cache\cacheText.txt`

     不過, 您可以使用任何文字檔, 並對此逐步解說中的程式碼進行較小的變更。

## <a name="creating-a-wpf-application-project"></a>建立 WPF 應用程式專案
 您將從建立 WPF 應用程式專案開始。

#### <a name="to-create-a-wpf-application"></a>建立 WPF 應用程式

1. 啟動 Visual Studio。

2. 在 [檔案] 功能表中, 按一下 [**新增**], 然後按一下 [**新增專案**]。

     [新增專案] 對話方塊隨即出現。

3. 在 [**已安裝的範本**] 底下, 選取您想要使用的程式設計語言 (**Visual Basic**或**視覺效果C#** )。

4. 在 [**新增專案**] 對話方塊中, 選取 [ **WPF 應用程式**]。

    > [!NOTE]
    > 如果您看不到 [ **Wpf 應用程式**] 範本, 請確定您的目標是支援 WPF 的 .NET Framework 版本。 在 [**新增專案**] 對話方塊中, 從清單中選取 [.NET Framework 4]。

5. 在 [**名稱**] 文字方塊中, 輸入專案的名稱。 例如, 您可以輸入**WPFCaching**。

6. 選取 [為解決方案建立目錄] 核取方塊。

7. 按一下 [確定 **Deploying Office Solutions**]。

     WPF 設計工具會在**設計**視圖中開啟, 並顯示 mainwindow.xaml。 Visual Studio 會建立 [**我的專案**] 資料夾、應用程式 .xaml 檔案和 mainwindow.xaml。

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>以 .NET Framework 為目標並加入快取元件的參考
 根據預設, WPF 應用程式會[!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]以為目標。 若要在<xref:System.Runtime.Caching> WPF 應用程式中使用命名空間, 應用程式必須將目標設為 .NET Framework [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]4 (而不是), 而且必須包含命名空間的參考。

 因此, 下一個步驟是變更 .NET Framework 目標, 並加入<xref:System.Runtime.Caching>命名空間的參考。

> [!NOTE]
> 在 Visual Basic 專案和 Visual C#專案中, 變更 .NET Framework 目標的程式會有所不同。

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>若要在 Visual Basic 中變更目標 .NET Framework

1. 在 [**方案瀏覽器**] 中, 以滑鼠右鍵按一下專案名稱, 然後按一下 [**屬性**]。

     應用程式的 [屬性] 視窗隨即顯示。

2. 按一下 [編譯] 索引標籤。

3. 在視窗底部, 按一下 [**高級編譯選項 ...** ]。

     [ **Advanced 編譯器設定**] 對話方塊隨即顯示。

4. 在 [**目標 framework (所有設定)** ] 清單中, 選取 [.NET Framework 4]。 (請勿選取[!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)])。

5. 按一下 [確定 **Deploying Office Solutions**]。

     [目標 Framework 變更] 對話方塊隨即出現。

6. 在 [**目標 Framework 變更**] 對話方塊中, 按一下 **[是**]。

     專案已關閉, 然後重新開啟。

7. 依照下列步驟, 新增對快取元件的參考:

    1. 在**方案總管**中, 以滑鼠右鍵按一下專案的名稱, 然後按一下 [**加入參考**]。

    2. 選取 [ **.net** ] 索引卷`System.Runtime.Caching`標, 選取 [], 然後按一下 **[確定]** 。

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>變更視覺效果C#專案中的目標 .NET Framework

1. 在**方案總管**中, 以滑鼠右鍵按一下專案名稱, 然後按一下 [**屬性**]。

     應用程式的 [屬性] 視窗隨即顯示。

2. 按一下 [應用程式] 索引標籤。

3. 在 [**目標 framework** ] 清單中, 選取 [.NET Framework 4]。 (請勿選取 [ **.NET Framework 4 用戶端設定檔**])。

4. 依照下列步驟, 新增對快取元件的參考:

    1. 以滑鼠右鍵按一下 [**參考**] 資料夾, 然後按一下 [**加入參考**]。

    2. 選取 [ **.net** ] 索引卷`System.Runtime.Caching`標, 選取 [], 然後按一下 **[確定]** 。

## <a name="adding-a-button-to-the-wpf-window"></a>將按鈕加入至 WPF 視窗
 接下來, 您將加入按鈕控制項, 並為按鈕的`Click`事件建立事件處理常式。 稍後您會將程式碼加入至, 當您按一下按鈕時, 就會快取並顯示文字檔的內容。

#### <a name="to-add-a-button-control"></a>若要加入按鈕控制項

1. 在**方案總管**中, 按兩下 [mainwindow.xaml] 檔案以開啟它。

2. 從 [**工具箱** `MainWindow` ] 的 [**通用 WPF 控制項**] 底下`Button` , 將控制項拖曳至視窗。

3. 在 [**屬性**] 視窗中, `Content`將`Button`控制項的屬性設定為 [**取得快取**]。

## <a name="initializing-the-cache-and-caching-an-entry"></a>初始化快取並快取專案
 接下來, 您將新增程式碼來執行下列工作:

- 建立 cache 類別的實例, 也就是您將具現化新<xref:System.Runtime.Caching.MemoryCache>的物件。

- 指定快取使用<xref:System.Runtime.Caching.HostFileChangeMonitor>物件來監視文字檔中的變更。

- 讀取文字檔, 並將其內容快取為快取專案。

- 顯示快取文字檔的內容。

#### <a name="to-create-the-cache-object"></a>若要建立快取物件

1. 按兩下您剛才加入的按鈕, 以便在 MainWindow.xaml.cs 或 Mainwindow.xaml 中建立事件處理常式。

2. 在檔案的頂端 (在類別宣告之前), 加入下列`Imports` (Visual Basic) 或`using` (C#) 語句:

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. 在事件處理常式中, 新增下列程式碼以具現化 cache 物件:

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <xref:System.Runtime.Caching.ObjectCache>類別是一種內建類別, 可提供記憶體中的物件快取。

4. 新增下列程式碼, 以讀取名為`filecontents`之快取專案的內容:

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. 新增下列程式碼, 以檢查名為`filecontents`的快取專案是否存在:

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     如果指定的快取專案不存在, 您必須讀取文字檔, 並將它當做快取專案新增至快取。

6. 在區塊中新增下列程式碼, 以建立新<xref:System.Runtime.Caching.CacheItemPolicy>的物件, 指定快取專案在10秒後到期。 `if/then`

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     如果未提供收回或到期資訊, 預設值為<xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, 這表示快取專案永遠不會根據絕對時間過期。 相反地, 只有在發生記憶體壓力時, 快取專案才會過期。 最佳做法是一律明確地提供絕對或滑動期限。

7. `if/then`在區塊內, 並遵循您在上一個步驟中新增的程式碼, 新增下列程式碼來建立您要監視之檔案路徑的集合, 並將文字檔的路徑新增至集合:

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    > 如果您想要使用的文字檔不`c:\cache\cacheText.txt`是, 請指定您要使用之文字檔的路徑。

8. 在您于上一個步驟中新增的程式碼之後, 新增下列程式碼, 以<xref:System.Runtime.Caching.HostFileChangeMonitor>將新的物件新增至快取專案的變更監視集合:

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <xref:System.Runtime.Caching.HostFileChangeMonitor>物件會監視文字檔的路徑, 並在發生變更時通知快取。 在此範例中, 如果檔案的內容變更, 快取專案就會過期。

9. 遵循您在上一個步驟中新增的程式碼, 新增下列程式碼來讀取文字檔的內容:

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     新增日期和時間時間戳記, 讓您能夠查看快取專案何時到期。

10. 在您于上一個步驟中新增的程式碼之後, 新增下列程式碼, 以將檔案的內容插入快取物件中<xref:System.Runtime.Caching.CacheItem>作為實例:

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     您可以藉由傳遞<xref:System.Runtime.Caching.CacheItemPolicy>您稍早建立的物件作為參數, 來指定快取專案應如何收回的相關資訊。

11. `if/then`在區塊之後, 新增下列程式碼, 以在訊息方塊中顯示快取檔案內容:

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. 在 [**建立**] 功能表中, 按一下 [**建立 WPFCaching** ] 來建立您的專案。

## <a name="testing-caching-in-the-wpf-application"></a>在 WPF 應用程式中測試快取
 您現在可以測試應用程式。

#### <a name="to-test-caching-in-the-wpf-application"></a>若要在 WPF 應用程式中測試快取

1. 按 CTRL+F5 執行應用程式。

     `MainWindow`視窗隨即顯示。

2. 按一下 [**取得快取**]。

     文字檔中的快取內容會顯示在訊息方塊中。 請注意檔案上的時間戳記。

3. 關閉訊息方塊, 然後按一下 [**取得快取**]。

     時間戳記不變。 這表示會顯示快取的內容。

4. 等待10秒或以上, 然後再按一下 [**取得快取**]。

     這次會顯示新的時間戳記。 這表示原則讓快取專案到期, 並顯示新的快取內容。

5. 在文字編輯器中, 開啟您所建立的文字檔。 尚未進行任何變更。

6. 關閉訊息方塊, 然後按一下 [**取得快取**]。

     請再次注意時間戳記。

7. 對文字檔進行變更, 然後儲存檔案。

8. 關閉訊息方塊, 然後按一下 [**取得快取**]。

     此訊息方塊包含來自文字檔的更新內容和新的時間戳記。 這表示當您變更檔案時, 主機檔案變更監視器會立即收回快取專案, 即使絕對的超時時間尚未過期也一樣。

    > [!NOTE]
    > 您可以將收回時間增加為20秒以上, 讓您有更多時間在檔案中進行變更。

## <a name="code-example"></a>程式碼範例
 完成本逐步解說之後, 您所建立之專案的程式碼會如下列範例所示。

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [.NET Framework 應用程式中的快取](../../performance/caching-in-net-framework-applications.md)
