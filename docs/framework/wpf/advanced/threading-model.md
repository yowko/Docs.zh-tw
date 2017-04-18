---
title: "執行緒模型 | Microsoft Docs"
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
  - "在更新按鈕上的文字"
  - "訊息處理，巢狀結構"
  - "封鎖作業"
  - "Dispatcher 類別"
  - "Common Language Runtime (CLR)，鎖定機制"
  - "Common Language Runtime (CLR) 的鎖定機制"
  - "執行緒模型"
  - "DependencyObject 類別"
  - "Word、 拼字檢查"
  - "按鈕的文字，更新"
  - "Word 的拼字檢查"
  - "非同步行為，公開"
  - "DependencyObject 類別"
  - "巢狀訊息處理"
  - "發送器的類別"
  - "可重新進入性"
ms.assetid: 02d8fd00-8d7c-4604-874c-58e40786770b
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 32
---
# 執行緒模型
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]可用來儲存開發人員從執行緒的問題。 如此一來，大部分的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]開發人員不需要撰寫的介面，會使用一個以上的執行緒。 多執行緒的程式並不複雜且難以偵錯，因為它們應該避免在單一執行緒解決方案時。  
  
 不論如何良好的架構設計，不過，沒有[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]framework 曾經可以提供每種問題的單一執行緒的解決方案。              [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是關閉的但仍有多個執行緒，改善的情況下[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]回應能力或應用程式的效能。 討論過一些背景資料之後, 本文將進一步說明這些情況下，並討論一些較低層級詳細資料的目的。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
> [!NOTE]
>  本主題討論使用執行緒<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>非同步呼叫的方法。 您也可以藉由呼叫來進行非同步呼叫<xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>方法，採取<xref:System.Action>或<xref:System.Func%601>做為參數。  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>方法會傳回<xref:System.Windows.Threading.DispatcherOperation>或<xref:System.Windows.Threading.DispatcherOperation%601>，其具有<xref:System.Windows.Threading.DispatcherOperation.Task%2A>屬性。 您可以使用`await`關鍵字使用<xref:System.Windows.Threading.DispatcherOperation>或相關聯<xref:System.Threading.Tasks.Task>。 如果您需要同步等候<xref:System.Threading.Tasks.Task>所傳回的<xref:System.Windows.Threading.DispatcherOperation>或<xref:System.Windows.Threading.DispatcherOperation%601>，呼叫<xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A>擴充方法。  呼叫<xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=fullName>會造成死結。 如需有關使用<xref:System.Threading.Tasks.Task>執行非同步作業，請參閱工作平行處理原則。  <xref:System.Windows.Threading.Dispatcher.Invoke%2A>方法也會有多載會接受<xref:System.Action>或<xref:System.Func%601>做為參數。  您可以使用<xref:System.Windows.Threading.Dispatcher.Invoke%2A>方法來進行同步呼叫的委派，傳入<xref:System.Action>或<xref:System.Func%601>。  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>概觀和發送器  
 一般而言，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式開始兩個執行緒︰ 一個用於處理呈現和另一個用於管理[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 有效地呈現執行緒執行時在背景中隱藏[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒會收到輸入、 處理事件、 繪製畫面，並執行應用程式程式碼。 大部分的應用程式使用單一[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒，但在某些情況下最好使用數個。 我們稍後會討論這一個範例。  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒佇列工作項目，稱為物件內<xref:System.Windows.Threading.Dispatcher>。 <xref:System.Windows.Threading.Dispatcher>選取優先權為基礎的工作項目，並執行到完成每一個。  每個[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]的執行緒必須具備至少一個<xref:System.Windows.Threading.Dispatcher>，而且每個<xref:System.Windows.Threading.Dispatcher>可以在一個執行緒中執行的工作項目。  
  
 建立回應靈敏且容易使用的應用程式的技巧是要最大化<xref:System.Windows.Threading.Dispatcher>輸送量保留小的工作項目。 此方式的項目永遠不會過時坐在<xref:System.Windows.Threading.Dispatcher>佇列中等候處理。 輸入與回應之間的任何感知延遲可以感到挫折的使用者。  
  
 如何則[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式應該要處理大量作業？ 如果您的程式碼牽涉到大型計算，或需要查詢某些遠端伺服器上的資料庫嗎？ 通常，答案是處理中個別的執行緒，而保留的大操作[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒可用傾向於中的項目<xref:System.Windows.Threading.Dispatcher>佇列。 大量作業完成時，它可以報告其結果傳回給[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]顯示的執行緒。  
  
 在過去，[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]允許[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]只能由建立它們的執行緒存取的項目。 這表示背景執行緒負責某些長時間執行的工作無法更新文字方塊中，在完成時。                  [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]沒有此選項可確保完整性，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]元件。 清單方塊看起來可能很奇怪，如果在繪製背景執行緒更新其內容。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]有個內建的互斥機制，會強制執行這項協調。 在大部分類別[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]衍生自<xref:System.Windows.Threading.DispatcherObject>。 在建構， <xref:System.Windows.Threading.DispatcherObject>儲存參考<xref:System.Windows.Threading.Dispatcher>連結至目前執行的執行緒。 實際上， <xref:System.Windows.Threading.DispatcherObject>建立它的執行緒產生關聯。 在程式執行期間<xref:System.Windows.Threading.DispatcherObject>可以呼叫其公用<xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>方法。                  <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>檢查<xref:System.Windows.Threading.Dispatcher>與目前執行緒相關聯，並將其以比較<xref:System.Windows.Threading.Dispatcher>參考儲存在建構期間。 如果兩者不符， <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>擲回例外狀況。                  <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>呼叫屬於每個方法的開頭<xref:System.Windows.Threading.DispatcherObject>。  
  
 如果只有一個執行緒可以修改[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，如何執行背景執行緒與使用者互動？ 背景執行緒可以要求[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]代替它執行的執行緒。 其作法是註冊的工作項目<xref:System.Windows.Threading.Dispatcher>的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒。 <xref:System.Windows.Threading.Dispatcher>類別提供兩種方法註冊的工作項目︰ <xref:System.Windows.Threading.Dispatcher.Invoke%2A>和<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>。 這兩種方法會排程執行的委派。                  <xref:System.Windows.Threading.Dispatcher.Invoke%2A>是同步呼叫 – 也就是它不會傳回之前[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒實際完成執行委派。                  <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>為非同步且立即傳回。  
  
 <xref:System.Windows.Threading.Dispatcher>依優先順序排序其佇列中的項目。 有十個新增項目時指定的層級<xref:System.Windows.Threading.Dispatcher>佇列。 這些優先順序保存在<xref:System.Windows.Threading.DispatcherPriority>列舉型別。 有關詳細資訊<xref:System.Windows.Threading.DispatcherPriority>層級位於[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]文件。  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>執行中的執行緒︰ 範例  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>使用長時間執行計算的單一執行緒應用程式  
 大部分[!INCLUDE[TLA#tla_gui#plural](../../../../includes/tlasharptla-guisharpplural-md.md)]花費大量時間等待以回應使用者互動所產生的事件閒置。 小心程式設計閒置時間可用態度，而不會影響的回應能力[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]執行緒模型不允許輸入插斷作業中發生的事情[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒。 這表示您必須確定返回<xref:System.Windows.Threading.Dispatcher>以處理輸入事件之前取得過時擱置。  
  
 參考下列範例：  
  
 ![質數螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/threadingprimenumberscreenshot.PNG "ThreadingPrimeNumberScreenShot")  
  
 這個簡單的應用程式中三個搜尋質數的計數向上。 當使用者按一下**啟動** 按鈕，開始搜尋。 當程式找到質數時，它會更新使用者介面使用。 在任何時間點，使用者也可以停止搜尋。  
  
 雖然簡單，但是質數搜尋無法下去，其中會提供一些問題。  如果我們處理整個搜尋按鈕的 click 事件處理常式內，我們就永遠不會提供給[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒有機會處理其他事件。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]無法回應輸入或處理訊息。 它會永遠不會重新繪製，而且永遠不會回應按下按鈕後。  
  
 進行質數搜尋在個別的執行緒，但需要處理同步處理問題。 使用單一執行緒的方法，我們可以直接更新，以列出找到的最大質數的標籤。  
  
 如果我們分解成可管理多個區塊的計算的工作時，我們可以定期返回<xref:System.Windows.Threading.Dispatcher>和處理事件。 我們可以給[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]有機會重新繪製，並處理輸入。  
  
 將計算和事件處理之間的處理時間，最好是管理從計算<xref:System.Windows.Threading.Dispatcher>。 使用<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>方法中，我們可以質數檢查排定在相同的佇列[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]取自 < 事件。 在範例中，我們排定只有一項質數檢查一次。 質數檢查完成之後，我們排定下次檢查立即。 這項檢查之後才會繼續暫止[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]已處理的事件。  
  
 ![發送器佇列圖例](../../../../docs/framework/wpf/advanced/media/threadingdispatcherqueue.PNG "ThreadingDispatcherQueue")  
  
 [!INCLUDE[TLA#tla_word](../../../../includes/tlasharptla-word-md.md)]完成拼字檢查使用這項機制。 拼字檢查是在背景使用的閒置時間[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒。 讓我們看看程式碼。  
  
 下列範例會建立使用者介面的 XAML。  
  
 [!code-xml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 下列範例程式碼後置。  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 下列範例顯示的事件處理常式<xref:System.Windows.Controls.Button>。  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 除了更新文字上<xref:System.Windows.Controls.Button>，此處理常式是負責排程所加入的委派的第一個質數檢查<xref:System.Windows.Threading.Dispatcher>佇列。 之後的事件處理常式已完成其工作時，有時<xref:System.Windows.Threading.Dispatcher>會選擇執行這個委派。  
  
 如前所述， <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>是<xref:System.Windows.Threading.Dispatcher>成員用來排定執行的委派。 在此情況下，我們選擇<xref:System.Windows.Threading.DispatcherPriority>優先順序。 <xref:System.Windows.Threading.Dispatcher>沒有重要的事件處理時，才會執行這個委派。                          [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]回應速度會比數字檢查更重要。 我們也會傳遞新的委派表示的數字檢查常式。  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 這個方法會檢查下一個奇數是否為質數。 如果是主要，此方法來直接更新`bigPrime` <xref:System.Windows.Controls.TextBlock>以反映其探索。 我們可以執行這項操作，因為計算發生在相同的執行緒用來建立元件。 我們已選擇要用於計算的另一個執行緒，我們必須使用更複雜的同步處理機制，並執行中的更新[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒。 接下來我們將示範這種情況。  
  
 此範例的完整原始程式碼，請參閱[單一執行緒應用程式與長時間執行的計算範例](http://go.microsoft.com/fwlink/?LinkID=160038)  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>處理背景執行緒的封鎖作業  
 處理圖形的應用程式中的封鎖作業可能很困難。 我們不想要從事件處理常式呼叫封鎖的方法，因為應用程式會凍結。 我們可以使用個別的執行緒來處理這些作業，但是當我們完成時，我們必須同步處理與[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒因為我們無法直接修改[!INCLUDE[TLA2#tla_gui](../../../../includes/tla2sharptla-gui-md.md)]從我們的背景工作執行緒。 我們可以使用<xref:System.Windows.Threading.Dispatcher.Invoke%2A>或<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>插入到委派<xref:System.Windows.Threading.Dispatcher>的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒。 最後，這些委派就會使用修改的權限執行[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]項目。  
  
 在此範例中，我們會模仿擷取天氣預報的遠端程序呼叫。 我們使用不同的背景工作執行緒執行，這個呼叫，我們排定更新方法中的<xref:System.Windows.Threading.Dispatcher>的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]當我們完成執行緒。  
  
 ![天氣 UI 螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/threadingweatheruiscreenshot.png "ThreadingWeatherUIScreenShot")  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 以下是一些要注意的詳細資料。  
  
-   建立按鈕處理常式  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 按一下按鈕時，我們會顯示時鐘圖案，並啟動動畫。 我們停用按鈕。 我們叫用`FetchWeatherFromServer`新執行緒，然後我們方法傳回時，允許<xref:System.Windows.Threading.Dispatcher>當我們收集氣象預報等待時處理事件。  
  
-   擷取天氣  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 為了簡單起見，我們實際上沒有任何網路的程式碼在此範例中。 相反地，我們模擬網路存取延遲的時間讓新執行緒進入睡眠狀態&4; 秒。 在這次請原始[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒執行並回應事件。 顯示這個情況，我們省略了讓動畫持續執行，而且最小化及最大化按鈕也會繼續運作。  
  
 當延遲完成後，我們會隨機選取我們的氣象預報，就可以回報給[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒。 執行此作業，排程呼叫`UpdateUserInterface`中[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒使用該執行緒<xref:System.Windows.Threading.Dispatcher>。 我們將傳遞字串，描述此排程的方法呼叫天氣。  
  
-   更新[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 當<xref:System.Windows.Threading.Dispatcher>中[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒都具有時間，它會執行排程的呼叫`UpdateUserInterface`。 這個方法會停止時鐘動畫，並選擇映像來描述氣象。 它會顯示此映像，並還原 「 提取預測 」 按鈕。  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>多個視窗中，多個執行緒  
 某些[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式需要多個最上層視窗。 它是完全可以接受的一個執行緒 /<xref:System.Windows.Threading.Dispatcher>組合來管理多個視窗，但有時幾個執行緒進行更好。 特別是如果有任何可能發生其中一種 windows 會獨佔執行緒。  
  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]總管適用於以這種方式。 每個新的瀏覽器視窗屬於原始的程序，但它會建立獨立的執行緒控制。  
  
 使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Frame>控制項中，我們可以顯示 Web 網頁。 我們可以輕鬆地建立簡單的[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]取代。 我們開始一項重要功能︰ 開啟新的瀏覽器視窗的能力。 當使用者按一下 「 新視窗 」 按鈕，我們推出一份視窗的另一個執行緒。 如此一來，在其中一個視窗中的長時間執行或封鎖作業就不會鎖定所有其他的視窗。  
  
 事實上，Web 瀏覽器模型有它自己的複雜執行緒模型。 因為它應該已熟悉大多數的讀者，我們已選擇它。  
  
 下列範例顯示的程式碼。  
  
 [!code-xml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 此程式碼的下列執行緒區段是最需要注意我們在此內容中︰  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 這個方法時，會呼叫 「 新視窗 」 按鈕。 它會建立新的執行緒，並以非同步方式啟動它。  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 這個方法是在新執行緒的起始點。 我們建立新的視窗，在此執行緒的控制之下。                          [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]自動建立新<xref:System.Windows.Threading.Dispatcher>來管理新的執行緒。 我們只需要建立視窗的功能是啟動<xref:System.Windows.Threading.Dispatcher>。  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>技術詳細資料和困難點  
  
### <a name="writing-components-using-threading"></a>使用執行緒撰寫元件  
 [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)]開發人員指南說明如何元件可以公開給其用戶端的非同步行為的模式 (請參閱[事件架構非同步模式概觀](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md))。 比方說，假設您想要封裝`FetchWeatherFromServer`成可重複使用、 程元件的方法。 遵循標準[!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)]模式，這看起來可能如下所示。  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 `GetWeatherAsync`會使用其中一個上述技術，例如建立背景執行緒，以非同步方式執行的工作不會封鎖呼叫執行緒。  
  
 其中一個最重要的組件，此模式呼叫*MethodName* `Completed`方法呼叫的相同執行緒上*MethodName* `Async`方法，即可使用。 您可以使用執行此[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]輕鬆，藉由儲存<xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>— 然後程元件可能只在使用中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，不在[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]或[!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]程式。  
  
 <xref:System.Windows.Threading.DispatcherSynchronizationContext>類別來對付這個需求 — 的簡化版做著<xref:System.Windows.Threading.Dispatcher>的運作方式與其他[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]以及架構。  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>巢狀提取  
 有時不可行，完全鎖住[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒。 我們來看一下<xref:System.Windows.MessageBox.Show%2A>方法<xref:System.Windows.MessageBox>類別。                          <xref:System.Windows.MessageBox.Show%2A>不會在使用者按一下 [確定] 按鈕之前傳回。 它，不過，建立必須的訊息迴圈，才能進行互動的視窗。 雖然我們正在等待使用者按下 [確定]，原始的應用程式視窗不會回應使用者輸入。 不過，它，請繼續處理繪製訊息。 原始的視窗重繪本身涵蓋後顯示。  
  
 ![包含 「 確定 」 按鈕的 MessageBox](../../../../docs/framework/wpf/advanced/media/threadingnestedpumping.png "ThreadingNestedPumping")  
  
 有些執行緒必須負責訊息方塊視窗中。                          [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]無法建立新的執行緒只會針對訊息方塊視窗中，但這個執行緒將無法繪製在原始的視窗中已停用的項目 （請記住先前討論過的互斥）。 相反地，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用巢狀的訊息處理系統。 <xref:System.Windows.Threading.Dispatcher>類別包含特殊的方法呼叫<xref:System.Windows.Threading.Dispatcher.PushFrame%2A>，它會儲存應用程式的目前執行點再開始新的訊息迴圈。 原始之後的巢狀的訊息迴圈完成時，請繼續執行<xref:System.Windows.Threading.Dispatcher.PushFrame%2A>呼叫。  
  
 在此情況下， <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>會維護程式內容，在呼叫<xref:System.Windows.MessageBox>。                         <xref:System.Windows.MessageBox.Show%2A>，而且開始新的訊息迴圈，以重新繪製背景視窗，並處理輸入訊息方塊視窗。 當使用者按一下 [確定]，並清除 快顯視窗中時，控制與巢狀的迴圈結束之後繼續呼叫<xref:System.Windows.MessageBox.Show%2A>。  
  
### <a name="stale-routed-events"></a>過時路由事件  
 路由的事件系統中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]引發事件時通知整個樹狀結構。  
  
 [!code-xml[InputOvw#ThreadingArticleStaticRoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 橢圓形上按下滑鼠左鍵時`handler2`執行。 之後`handler2`完成時，事件會傳遞至<xref:System.Windows.Controls.Canvas>物件使用`handler1`來處理它。 只有當此時`handler2`不未明確標記事件的物件為已處理。  
  
 它可供使用，`handler2`會花費很長的時間處理此事件。                          `handler2`可能會使用<xref:System.Windows.Threading.Dispatcher.PushFrame%2A>開始不會傳回小時內的巢狀的訊息迴圈。 如果`handler2`不的標記事件為已處理這個訊息迴圈時完成，即使是很舊樹狀結構中向上傳遞事件。  
  
### <a name="reentrancy-and-locking"></a>重新進入和鎖定  
 鎖定機制[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]不完全相同的行為可能有人; 其中一個可能預期高優先權時要求鎖定的執行緒。 實際上，執行緒會繼續接收和處理高優先順序的訊息。 這有助於防止發生鎖死，並加速介面的最低限度的方式回應，但也會造成微妙的 bug 的可能性。  大部分情況下您不需要知道的任何項目，這個問題，但在極少數的情況下 (通常涉及[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗訊息或 STA COM 元件) 這可以是值得一提。  
  
 因為開發人員假設並非大部分介面建置考慮到執行緒安全性，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]永遠不會透過多個執行緒。 在此情況下，單一執行緒可能會發生環境變更，在非預期的時間，導致這些錯誤效果<xref:System.Windows.Threading.DispatcherObject>互斥機制應該解決。 請考慮下列虛擬程式碼︰  
  
 ![執行緒重新進入圖表](../../../../docs/framework/wpf/advanced/media/threadingreentrancy.png "ThreadingReentrancy")  
  
 大部分的時間是正確的事，但有時候在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，這類非預期的重新進入可能真的會造成問題。 是，在特定索引鍵的時候，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]呼叫<xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>，變更使用該執行緒的鎖定指示[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]重新進入釋放鎖定，而非平常[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]鎖定。  
  
 那麼，為什麼沒有[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]小組選擇這種行為？ 它必須使用 STA COM 物件和完成項執行緒執行。 當物件被回收，其`Finalize`方法上執行時，在專用的完成項執行緒不[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒。 其中是問題，因為 COM STA 物件上建立[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒只會處置上[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]執行緒。 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]沒有相當於<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (在此情況下使用 Win32 的`SendMessage`)。 但如果[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]忙碌執行緒、 完成項執行緒已停止，STA COM 物件無法處置，這樣就可以建立有嚴重的記憶體流失。 因此[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]小組呼叫並不容易進行鎖定的運作方式一樣。  
  
 針對工作[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是為了避免非預期的重新進入而不重新導入以記憶體流失，這就是為什麼我們不會封鎖所有的重新進入。  
  
## <a name="see-also"></a>另請參閱  
 [單一執行緒應用程式與長時間執行的計算範例](http://go.microsoft.com/fwlink/?LinkID=160038)