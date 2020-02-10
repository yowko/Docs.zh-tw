---
title: 執行緒模型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text on buttons [WPF], updating
- message processing [WPF], nested
- blocking operations [WPF]
- Common Language Runtime (CLR), locking mechanism
- locking mechanism of Common Language Runtime (CLR)
- threading model [WPF]
- Word [WPF], spelling checking
- button text [WPF], updating
- spelling checking in Word [WPF]
- asynchronous behavior [WPF], exposing
- nested message processing [WPF]
- reentrancy [WPF]
ms.assetid: 02d8fd00-8d7c-4604-874c-58e40786770b
ms.openlocfilehash: 87dcfa22bcce730c5a9b61721c3a846a08146475
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094497"
---
# <a name="threading-model"></a>執行緒模型
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 是設計來避免開發人員遇到執行緒的難題。 因此，大部分的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 開發人員都不需要撰寫使用一個以上執行緒的介面。 由於多執行緒的程式非常複雜且很難偵錯，因此，若有單一執行緒解決方案，就應避免使用多執行緒程式。

 不過，無論架構的結構如何，都不 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 架構也能夠為每種問題提供單一執行緒的解決方案。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 已關閉，但仍有多個執行緒改善 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 回應性或應用程式效能的情況。 討論一些背景資料之後，本文將說明這其中的一些情況，然後以一些較低層級詳細資訊的討論來做出結論。

> [!NOTE]
> 本主題將討論使用 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 方法進行非同步呼叫的執行緒。 您也可以呼叫 <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> 方法來進行非同步呼叫，這會採用 <xref:System.Action> 或 <xref:System.Func%601> 做為參數。  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> 方法會傳回具有 <xref:System.Windows.Threading.DispatcherOperation.Task%2A> 屬性的 <xref:System.Windows.Threading.DispatcherOperation> 或 <xref:System.Windows.Threading.DispatcherOperation%601>。 您可以使用 `await` 關鍵字搭配 <xref:System.Windows.Threading.DispatcherOperation> 或相關聯的 <xref:System.Threading.Tasks.Task>。 如果您需要以同步方式等候 <xref:System.Windows.Threading.DispatcherOperation> 或 <xref:System.Windows.Threading.DispatcherOperation%601>所傳回的 <xref:System.Threading.Tasks.Task>，請呼叫 <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> 擴充方法。  呼叫 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 將會導致鎖死。 如需使用 <xref:System.Threading.Tasks.Task> 執行非同步作業的詳細資訊，請參閱工作平行處理原則。  <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 方法也具有可接受 <xref:System.Action> 或 <xref:System.Func%601> 作為參數的多載。  您可以使用 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 方法，藉由傳入委派、<xref:System.Action> 或 <xref:System.Func%601>來進行同步呼叫。

<a name="threading_overview"></a>
## <a name="overview-and-the-dispatcher"></a>概觀和發送器
 一般來說，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式會從兩個執行緒開始：一個用於處理轉譯，另一個則用於管理 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 轉譯執行緒會在背景中有效地執行，而 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒會接收輸入、處理事件、繪製螢幕，以及執行應用程式程式碼。 大部分的應用程式都使用單一 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒，不過在某些情況下，最好是使用數個。 我們稍後將使用範例來討論這一點。

 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒會將名為 <xref:System.Windows.Threading.Dispatcher>之物件內的工作專案排入佇列。 <xref:System.Windows.Threading.Dispatcher> 會依優先權選取工作項目，並逐一執行以完成每個工作項目。  每個 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒都必須至少有一個 <xref:System.Windows.Threading.Dispatcher>，而且每個 <xref:System.Windows.Threading.Dispatcher> 只能在一個執行緒中執行工作專案。

 建立回應式且方便使用的應用程式的訣竅，是讓工作專案保持在最大的 <xref:System.Windows.Threading.Dispatcher> 輸送量。 如此一來，在等候處理的 <xref:System.Windows.Threading.Dispatcher> 佇列中，專案永遠不會過時。 輸入與回應之間任何可察覺到的延遲都能讓使用者感到挫折。

 那麼，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式應該如何處理大型作業呢？ 如果您的程式碼牽涉到大型計算，或需要查詢某些遠端伺服器上的資料庫，又該怎麼做？ 通常，答案是在不同的執行緒中處理 big 作業，讓 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒可以自由地在 <xref:System.Windows.Threading.Dispatcher> 佇列中的專案上運作。 當 big 作業完成時，它可以將其結果回報給 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的執行緒以供顯示。

 在過去，Windows 只允許透過建立 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 專案的執行緒來存取這些專案。 這表示負責某些長時間執行工作的背景執行緒無法在完成時更新文字方塊。 Windows 會執行此工作，以確保 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 元件的完整性。 如果背景執行緒已在繪製期間更新了清單方塊的內容，則該清單方塊看起來可能很奇怪。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 有個內建的互斥機制，會強制執行這項協調。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的大部分類別都是衍生自 <xref:System.Windows.Threading.DispatcherObject>。 在結構上，<xref:System.Windows.Threading.DispatcherObject> 會儲存連結至目前執行中線程之 <xref:System.Windows.Threading.Dispatcher> 的參考。 實際上，<xref:System.Windows.Threading.DispatcherObject> 會與建立它的執行緒產生關聯。 在程式執行期間，<xref:System.Windows.Threading.DispatcherObject> 可以呼叫其公用 <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> 方法。 <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> 檢查與目前線程相關聯的 <xref:System.Windows.Threading.Dispatcher>，並將其與在結構中儲存的 <xref:System.Windows.Threading.Dispatcher> 參考進行比較。 如果兩者不相符，<xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> 會擲回例外狀況。 <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> 的目的是要在每個屬於 <xref:System.Windows.Threading.DispatcherObject>的方法開頭進行呼叫。

 如果只有一個執行緒可以修改 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，背景執行緒如何與使用者互動？ 背景執行緒可以要求 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒代表它執行作業。 其方式是向 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒的 <xref:System.Windows.Threading.Dispatcher> 註冊工作專案。 <xref:System.Windows.Threading.Dispatcher> 類別提供兩種註冊工作專案的方法： <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 和 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>。 這兩種方法都會排程要執行的委派。 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 是同步呼叫，也就是說，在 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒實際完成執行委派之前，它不會傳回。 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 是非同步，而且會立即傳回。

 <xref:System.Windows.Threading.Dispatcher> 依優先順序排序其佇列中的元素。 將專案新增至 <xref:System.Windows.Threading.Dispatcher> 的佇列時，可以指定十個層級。 這些優先順序會在 <xref:System.Windows.Threading.DispatcherPriority> 列舉中維護。 <xref:System.Windows.Threading.DispatcherPriority> 層級的詳細資訊可在 Windows SDK 檔中找到。

<a name="samples"></a>
## <a name="threads-in-action-the-samples"></a>執行中的執行緒︰範例

<a name="prime_number"></a>
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>單一執行緒應用程式與長時間執行的計算
 大部分的圖形化使用者介面（Gui）都會在等候使用者互動時所產生的事件時，花費大量時間閒置的部分。 有了謹慎的程式設計，就可以建設性使用此閒置時間，而不會影響 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]的回應能力。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 執行緒模型不允許輸入中斷 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒中發生的作業。 這表示您必須務必定期返回 <xref:System.Windows.Threading.Dispatcher>，以處理擱置中的輸入事件，然後才會過時。

 請考慮下列範例：

 ![顯示質數執行緒的螢幕擷取畫面。](./media/threading-model/threading-prime-numbers.png)

 這個簡單的應用程式會從三開始向上計算，以搜尋質數。 當使用者按一下 [**開始**] 按鈕時，就會開始搜尋。 當程式找到質數時，會使用它的發現來更新使用者介面。 使用者隨時都能停止搜尋。

 雖然夠簡單，但質數搜尋會永無止盡的繼續執行，其中會遇到一些難題。  如果我們在按鈕的 click 事件處理常式內處理整個搜尋，就不會讓 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒有機會處理其他事件。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 將無法回應輸入或處理訊息。 它永遠不會重新繪製，而且永遠不會回應按鈕 Click。

 我們可以在個別執行緒中管理質數搜尋，但接著需要處理同步問題。 使用單一執行緒的方法，我們可以直接更新標籤，以列出所找到的最大質數。

 如果我們將計算的工作分解成可管理的區塊，我們可以定期返回 <xref:System.Windows.Threading.Dispatcher> 和處理事件。 我們可以讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 重新繪製和處理輸入的機會。

 在計算與事件處理之間分割處理時間的最佳方式，是從 <xref:System.Windows.Threading.Dispatcher>管理計算。 藉由使用 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 方法，我們可以在 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 事件繪製所在的相同佇列中排程質數檢查。 在範例中，我們一次只會排程單一質數檢查。 質數檢查完成之後，我們會立即排程下次檢查。 只有在處理暫止的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 事件之後，才會進行這種檢查。

 ![顯示發送器佇列的螢幕擷取畫面。](./media/threading-model/threading-dispatcher-queue.png)

 Microsoft Word 會使用此機制來完成拼寫檢查。 拼寫檢查會在背景中使用 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒的閒置時間來完成。 讓我們看看程式碼。

 下列範例顯示建立使用者介面的 XAML。

 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]

 下列範例顯示程式碼後置。

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]

 下列範例會顯示 <xref:System.Windows.Controls.Button>的事件處理常式。

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]

 除了更新 <xref:System.Windows.Controls.Button>上的文字，此處理程式還會負責將委派加入至 <xref:System.Windows.Threading.Dispatcher> 佇列，以排程第一個質數檢查。 在此事件處理常式完成其工作之後，<xref:System.Windows.Threading.Dispatcher> 將會選取此委派以進行執行。

 如先前所述，<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 是用來排程執行委派的 <xref:System.Windows.Threading.Dispatcher> 成員。 在此情況下，我們會選擇 <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> 優先權。 只有在沒有要處理的重要事件時，<xref:System.Windows.Threading.Dispatcher> 才會執行此委派。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 回應性比數字檢查更重要。 我們也會傳遞新的委派來代表數字檢查常式。

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]

 這個方法會檢查下一個奇數是否為質數。 如果是質數，方法會直接更新 `bigPrime`<xref:System.Windows.Controls.TextBlock> 以反映其探索。 由於計算會發生在用來建立元件的相同執行緒中，因此我們可以執行這項操作。 我們已選擇使用個別的執行緒來進行計算，我們必須使用更複雜的同步處理機制，並在 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒中執行更新。 接下來我們將示範這種情況。

 如需此範例的完整原始程式碼，請參閱[具有長時間執行計算範例的單一執行緒應用程式](https://github.com/Microsoft/WPF-Samples/tree/master/Threading/SingleThreadedApplication)

<a name="weather_sim"></a>
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>利用背景執行緒處理封鎖作業
 處理圖形應用程式中的封鎖作業可能很困難。 我們不想從事件處理常式中呼叫封鎖方法，因為應用程式將呈現凍結狀態。 我們可以使用個別的執行緒來處理這些作業，但當我們完成時，我們必須與 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒同步，因為我們無法直接從背景工作執行緒修改 GUI。 我們可以使用 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 或 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>，將委派插入 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒的 <xref:System.Windows.Threading.Dispatcher> 中。 最後，這些委派將會執行，並具有修改 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 元素的許可權。

 在此範例中，我們模仿遠端程序呼叫來擷取氣象預報。 我們會使用個別的背景工作執行緒來執行此呼叫，並在完成時，在 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒的 <xref:System.Windows.Threading.Dispatcher> 中排程更新方法。

 ![顯示天氣 UI 的螢幕擷取畫面。](./media/threading-model/threading-weather-ui.png)

 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]

 以下是一些要注意的詳細資料。

- 建立按鈕處理常式

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]

 按一下按鈕時，我們會顯示時鐘圖案並開始以動畫顯示它。 我們停用按鈕。 我們會在新的執行緒中叫用 `FetchWeatherFromServer` 方法，然後傳回，讓 <xref:System.Windows.Threading.Dispatcher> 在等候收集氣象預報時處理事件。

- 擷取氣象

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]

 為了簡單起見，我們並未在此範例中實際使用任何網路程式碼。 相反地，我們讓新的執行緒進入睡眠狀態 4 秒，藉以模擬網路存取延遲。 此時，原始 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒仍在執行中，並回應事件。 為了顯示此情況，我們讓動畫持續執行，並讓最小化及最大化按鈕也能繼續運作。

 當延遲完成，而且我們隨機選取了氣象預報之後，就可以向後回報到 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的往來文章。 我們的作法是使用該執行緒的 <xref:System.Windows.Threading.Dispatcher>來排程 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒中 `UpdateUserInterface` 的呼叫。 我們將描述氣象的字串傳遞到這個排程的方法呼叫。

- 更新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]

 當 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒中的 <xref:System.Windows.Threading.Dispatcher> 有時間時，它會對 `UpdateUserInterface`執行排程的呼叫。 這個方法會停止時鐘動畫，並選擇影像來說明氣象。 它會顯示此影像，並還原 [Fetch Forecast (擷取預報)] 按鈕。

<a name="multi_browser"></a>
### <a name="multiple-windows-multiple-threads"></a>多個視窗，多個執行緒
 某些 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式需要多個最上層視窗。 一個執行緒/<xref:System.Windows.Threading.Dispatcher> 組合可以完全接受，以管理多個視窗，但有時候有數個執行緒會有更好的工作。 如果有可能發生某一個視窗將獨佔執行緒的情況，這特別適用。

 Windows Explorer 以這種方式運作。 每個新的檔案總管視窗都屬於原始的程序，但會在獨立執行緒的控制下建立它。

 藉由使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Frame> 控制項，我們可以顯示網頁。 我們可以輕鬆地建立簡單的 Internet Explorer 替代方案。 我們從一個重要功能開始︰開啟新檔案總管視窗的能力。 當使用者按一下 [New Window (新視窗)] 按鈕時，我們會在另一個執行緒中啟動視窗複本。 如此一來，在其中一個視窗中長時間執行或封鎖的作業就不會鎖定所有其他視窗。

 事實上，網頁瀏覽器模型有它自己的複雜執行緒模型。 我們選擇它是因為大多數讀者應該都已熟悉它。

 下列範例顯示此程式碼。

 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]

 此程式碼的下列執行緒區段是我們在此內容中最感興趣的部分：

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]

 按下 [New Window (新視窗)] 按鈕時會呼叫此方法。 它會建立新的執行緒，並以非同步方式啟動它。

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]

 這個方法是新執行緒的起點。 我們在此執行緒的控制下建立新視窗。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會自動建立新的 <xref:System.Windows.Threading.Dispatcher> 來管理新的執行緒。 為了讓視窗發揮作用，我們只需要啟動 <xref:System.Windows.Threading.Dispatcher>。

<a name="stumbling_points"></a>
## <a name="technical-details-and-stumbling-points"></a>技術詳細資料與困難點

### <a name="writing-components-using-threading"></a>使用執行緒撰寫元件
 《 Microsoft .NET Framework 開發人員指南》會說明元件如何將非同步行為公開給其用戶端的模式（請參閱[事件架構非同步模式總覽](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)）。 比方說，假設我們想要將 `FetchWeatherFromServer` 方法封裝成可重複使用的 nongraphical 元件。 遵循標準的 Microsoft .NET Framework 模式，這看起來會像下面這樣。

 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]

 `GetWeatherAsync` 會使用上述其中一種技術 (例如建立背景執行緒)，以非同步方式執行工作，而不需封鎖呼叫執行緒。

 此模式最重要的部分之一，就是在呼叫*方法`Async`* 方法的相同執行緒上呼叫*方法`Completed` 方法*，以開始使用。 您可以透過儲存 <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>，輕鬆地使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，但 nongraphical 元件只能用在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中，而不能用於 Windows Forms 或 ASP.NET 程式中。

 <xref:System.Windows.Threading.DispatcherSynchronizationContext> 類別可以滿足這項需求，也就是可與其他 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 架構搭配使用的簡化版 <xref:System.Windows.Threading.Dispatcher>。

 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]

### <a name="nested-pumping"></a>巢狀提取
 有時候，完全鎖定 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒並不可行。 讓我們考慮 <xref:System.Windows.MessageBox> 類別的 <xref:System.Windows.MessageBox.Show%2A> 方法。 在使用者按一下 [確定] 按鈕之前，<xref:System.Windows.MessageBox.Show%2A> 不會傳回。 不過，它會建立必須有訊息迴圈才能互動的視窗。 雖然我們正在等待使用者按下 [OK (確定)]，但原始的應用程式視窗並不會回應使用者輸入。 不過，它會繼續處理繪製訊息。 原始視窗會在涵蓋並顯示時自行重新繪製。

 ![顯示含有 [確定] 按鈕之 MessageBox 的螢幕擷取畫面](./media/threading-model/threading-message-loop.png)

 有些執行緒必須負責訊息方塊視窗。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 只會針對訊息方塊視窗建立新的執行緒，但這個執行緒無法在原始視窗中繪製已停用的元素 (請記住先前討論過的互斥)。 相反地，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會使用嵌套的訊息處理系統。 <xref:System.Windows.Threading.Dispatcher> 類別包含稱為 <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>的特殊方法，它會儲存應用程式的目前執行點，然後開始新的訊息迴圈。 當 nested 訊息迴圈完成時，會在原始 <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> 呼叫之後繼續執行。

 在此情況下，<xref:System.Windows.Threading.Dispatcher.PushFrame%2A> 會在呼叫 <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType>時維護程式內容，並啟動新的訊息迴圈來重新繪製背景視窗，並處理訊息方塊視窗的輸入。 當使用者按一下 [確定] 並清除快顯視窗時，嵌套的迴圈會結束，並在 <xref:System.Windows.MessageBox.Show%2A>的呼叫之後繼續控制。

### <a name="stale-routed-events"></a>過時的路由事件
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的路由事件系統會在引發事件時通知整個樹狀結構。

 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]

 在橢圓形上按下滑鼠左鍵時，會執行 `handler2`。 在 `handler2` 完成之後，事件會傳遞到 <xref:System.Windows.Controls.Canvas> 物件，而此物件會使用 `handler1` 來處理它。 只有當 `handler2` 未明確地將事件物件標示為已處理時，才會發生這種情況。

 `handler2` 可能需要大量時間來處理此事件。 `handler2` 可能會使用 <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> 來開始不會傳回小時的嵌套訊息迴圈。 如果 `handler2` 不會在此訊息迴圈完成時將事件標示為已處理，則會將事件傳遞到樹狀結構中，即使它非常舊也一樣。

### <a name="reentrancy-and-locking"></a>重新進入和鎖定
 通用語言執行時間（CLR）的鎖定機制，其行為不會與想像的完全相同;要求鎖定時，可能會預期執行緒完全停止作業。 實際上，執行緒會繼續接收和處理高優先順序的訊息。 這有助於防止發生鎖死，並讓介面進行最低限度的回應，但它也會造成發生輕微 Bug 的可能性。  在大部分的情況下，您不需要知道這方面的任何內容，但在罕見的情況下（通常牽涉到 Win32 視窗訊息或 COM STA 元件），這很值得了解。

 大部分介面不是以執行緒安全的方式建立的，因為開發人員會在假設沒有一個以上的執行緒存取 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的情況下工作。 在此情況下，該單一執行緒可能會在非預期的時間進行環境變更，而導致 <xref:System.Windows.Threading.DispatcherObject> 相互排除機制應該會解決這些不正確的影響。 請考慮下列虛擬程式碼：

 ![顯示執行緒重新進入的圖表。](./media/threading-model/threading-reentrancy.png "ThreadingReentrancy")

 在大部分的情況下，這是正確的事，但有時 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 這類非預期的重新進入可能會造成問題。 因此，在某些索引鍵的時間，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會呼叫 <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>，這會變更該執行緒的鎖定指令，以使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的重新進入免費鎖定，而不是一般的 CLR 鎖定。

 那麼，為什麼 CLR 小組選擇此行為呢？ 它必須使用 STA COM 物件和完成項執行緒來執行。 當物件進行垃圾收集時，其 `Finalize` 方法會在專用的完成項執行緒上執行，而不是在 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的執行緒上執行。 而這就是問題所在，因為在 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒上建立的 COM STA 物件只能在 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒上處置。 CLR 會執行對等的 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> （在此案例中使用 Win32 `SendMessage`）。 但是，如果 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒忙碌中，完成項執行緒就會停止，而且無法處置 COM STA 物件，這會造成嚴重的記憶體流失。 因此，CLR 小組進行了很難的呼叫，讓鎖定的執行方式。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的工作是避免非預期的重新進入，而不重新介紹基於記憶體流失，這就是為什麼我們不會封鎖任何地方的重新進入。

## <a name="see-also"></a>另請參閱

- [單一執行緒應用程式與長期執行的計算範例](https://github.com/Microsoft/WPF-Samples/tree/master/Threading/SingleThreadedApplication)
