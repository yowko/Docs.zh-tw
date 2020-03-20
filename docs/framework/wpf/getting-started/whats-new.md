---
title: WPF 4.5 版的新功能
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 708b2fc231bfe7a9bc1f52872a0ec41c91931f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174702"
---
# <a name="whats-new-in-wpf-version-45"></a>WPF 4.5 版的新功能
<a name="introduction"></a>本主題包含有關版本 4.5 中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]新增功能和增強功能的資訊。  
  
 本主題包含下列幾節：  
  
- [功能區控制項](#ribbon_control)  
  
- [顯示大型群組資料集合時改善效能](#grouped_virtualization)  
  
- [VirtualizingPanel 的新功能](#VirtualizingPanel)  
  
- [繫結至靜態屬性](#static_properties)  
  
- [存取非 UI 執行緒上的集合](#xthread_access)  
  
- [同步和非同步驗證資料](#INotifyDataErrorInfo)  
  
- [自動更新資料繫結的來源](#delay)  
  
- [繫結至實作 ICustomTypeProvider 的型別](#ICustomTypeProvider)  
  
- [從繫結運算式擷取資料繫結資訊](#binding_state)  
  
- [檢查有效的 DataContext 物件](#DisconnectedSource)  
  
- [隨著資料值變更重新調整資料的位置 (即時繪圖)](#live_shaping)  
  
- [建立事件弱式參考的加強支援](#weak_event_pattern)  
  
- [Dispatcher 類別的新方法](#async)  
  
- [事件的標記延伸](#events_markup_extenions)  
  
<a name="ribbon_control"></a>
## <a name="ribbon-control"></a>功能區控制項  
 WPF 4.5 附帶<xref:System.Windows.Controls.Ribbon.Ribbon>一個控制項，該控制項承載快速存取工具列、應用程式功能表和選項卡。  如需詳細資訊，請參閱[功能區概觀](/visualstudio/vsto/ribbon-overview)。  
  
<a name="grouped_virtualization"></a>
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>顯示大型群組資料集合時改善效能  
 UI 虛擬化會在使用者介面 (UI) 元素的子集從大量資料項目，根據可在畫面上看到的項目來產生時發生。 定義<xref:System.Windows.Controls.VirtualizingPanel><xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A>支援分組資料的 UI 虛擬化的附加屬性。  如需群組資料的詳細資訊，請參閱「如何：使用 XAML 中的檢視排序和分組資料」。  有關虛擬化分組資料的詳細資訊，請參閱<xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A>附加屬性。  
  
<a name="VirtualizingPanel"></a>
## <a name="new-features-for-the-virtualizingpanel"></a>VirtualizingPanel 的新功能  
  
1. 可以使用<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>附加屬性指定<xref:System.Windows.Controls.VirtualizingPanel>是否 顯示<xref:System.Windows.Controls.VirtualizingStackPanel>，如 。 如果<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>設置為<xref:System.Windows.Controls.ScrollUnit.Item>，<xref:System.Windows.Controls.VirtualizingPanel>將僅顯示完全可見的項。 如果<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>設置為<xref:System.Windows.Controls.ScrollUnit.Pixel>，<xref:System.Windows.Controls.VirtualizingPanel>可以顯示部分可見的項。  
  
2. 當 使用<xref:System.Windows.Controls.VirtualizingPanel><xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A>附加屬性虛擬化 時，可以指定視口前後緩存的大小。  快取是不虛擬化項目之高於或低於檢視區的空間量。  使用快取以避免產生 UI 元素，因為它們捲動至檢視中可以改善效能。 填入快取的優先順序較低，讓應用程式在作業期間不會變成沒有回應。 屬性<xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType>確定 所使用的<xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>度量單位。  
  
<a name="static_properties"></a>
## <a name="binding-to-static-properties"></a>繫結至靜態屬性  
 您可以使用靜態屬性做為資料繫結的來源。 資料繫結引擎會辨識當引發靜態事件時，屬性的值何時變更。  例如，如果類別 `SomeClass` 定義靜態屬性，稱為 `MyProperty`，`SomeClass` 可以定義為靜態事件，該事件在 `MyProperty` 的值變更時引發。  靜態事件可以使用下列簽章。  
  
- `public static event EventHandler MyPropertyChanged;`  
  
- `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 請注意，在第一種情況下，類公開一個名為*屬性Name*`Changed`的靜態事件，該事件傳遞給<xref:System.EventArgs>事件處理常式。  在第二種情況下，類公開一個名為傳遞給`StaticPropertyChanged`<xref:System.ComponentModel.PropertyChangedEventArgs>事件處理常式的靜態事件。 實作靜態屬性的類別，可以選擇使用任一種方法引發屬性變更通知。  
  
<a name="xthread_access"></a>
## <a name="accessing-collections-on-non-ui-threads"></a>存取非 UI 執行緒上的集合  
 WPF 可讓您存取和修改在執行緒上的資料集合，不是建立集合的執行緒。  這可讓您使用背景執行緒從外部來源 (例如資料庫) 接收資料，並且在 UI 執行緒上顯示資料。  藉由使用另一個執行緒來修改集合，您的使用者介面仍然能夠保持對使用者互動回應。  
  
<a name="INotifyDataErrorInfo"></a>
## <a name="synchronously-and-asynchronously-validating-data"></a>同步和非同步驗證資料  
 該<xref:System.ComponentModel.INotifyDataErrorInfo>介面使資料實體類能夠實現自訂驗證規則，並非同步公開驗證結果。 此介面也支援自訂錯誤物件、每個屬性多個錯誤、跨屬性錯誤，以及實體層級錯誤。  如需詳細資訊，請參閱 <xref:System.ComponentModel.INotifyDataErrorInfo>。  
  
<a name="delay"></a>
## <a name="automatically-updating-the-source-of-a-data-binding"></a>自動更新資料繫結的來源  
 如果使用資料繫結更新資料來源，則可以使用 屬性<xref:System.Windows.Data.BindingBase.Delay%2A>指定在源更新之前對目標的屬性進行更改後要經過的時間量。  例如，<xref:System.Windows.Controls.Slider>假設您有一個具有其<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>屬性資料的雙向綁定到資料物件的屬性，<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>並且該屬性設置為<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。  在此示例中，當使用者移動 的<xref:System.Windows.Controls.Slider>源將更新移動的每個<xref:System.Windows.Controls.Slider>圖元。  源物件通常僅在滑塊<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>停止更改時才需要滑塊的值。  為了防止過於頻繁地更新源，請使用<xref:System.Windows.Data.BindingBase.Delay%2A>指定在拇指停止移動後經過一段時間之前不應更新源。  
  
<a name="ICustomTypeProvider"></a>
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>繫結至實作 ICustomTypeProvider 的型別  
 WPF 支援對實現<xref:System.Reflection.ICustomTypeProvider>（ 也稱為自訂類型） 的物件綁定的資料。  您可以在下列情況下使用自訂型別。  
  
1. 作為資料<xref:System.Windows.PropertyPath>綁定中的一個。 例如，<xref:System.Windows.Data.Binding.Path%2A>屬性<xref:System.Windows.Data.Binding>可以引用自訂類型的屬性。  
  
2. 作為<xref:System.Windows.DataTemplate.DataType%2A>屬性的值。  
  
3. 作為確定 中自動生成的列的類型<xref:System.Windows.Controls.DataGrid>。  
  
<a name="binding_state"></a>
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>從繫結運算式擷取資料繫結資訊  
 在某些情況下，您可能會獲得 和<xref:System.Windows.Data.BindingExpression><xref:System.Windows.Data.Binding>需要有關綁定的源和目標物件的資訊。  新的 API 已新增，可讓您取得來源或目標物件或相關聯的屬性。  當您有 時<xref:System.Windows.Data.BindingExpression>，請使用以下 API 獲取有關目標和源的資訊。  
  
|若要尋找繫結的此值|使用此 API|  
|---------------------------------------|------------------|  
|目標物件|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|目標屬性|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|來源物件|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|來源屬性|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|是否<xref:System.Windows.Data.BindingExpression>屬於<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|擁有者<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>
## <a name="checking-for-a-valid-datacontext-object"></a>檢查有效的 DataContext 物件  
 在某些情況下，<xref:System.Windows.FrameworkElement.DataContext%2A>中項容器的 已<xref:System.Windows.Controls.ItemsControl>斷開連接。  項容器是在 中顯示項的<xref:System.Windows.Controls.ItemsControl>UI 元素。  當<xref:System.Windows.Controls.ItemsControl>資料繫結到集合時，將為每個項生成一個項容器。 在某些情況下，項目容器會從視覺化樹狀結構移除。 刪除項容器的兩個典型情況是，從基礎集合中刪除項時，在 上啟用虛擬化<xref:System.Windows.Controls.ItemsControl>。 在這些情況下，<xref:System.Windows.FrameworkElement.DataContext%2A>項容器的屬性將設置為靜態屬性返回的<xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType>哨點物件。  在訪問項容器 之前<xref:System.Windows.FrameworkElement.DataContext%2A><xref:System.Windows.FrameworkElement.DataContext%2A>，應檢查<xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A>是否等於物件。  
  
<a name="live_shaping"></a>
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>隨著資料值變更重新調整資料的位置 (即時繪圖)  
 資料的集合可以分組、排序或篩選。 WPF 4.5 可讓資料在修改時重新排列。 例如，假設應用程式使用 在<xref:System.Windows.Controls.DataGrid>股票市場中列出股票，並且股票按股票價值排序。 如果在股票上啟用即時排序<xref:System.Windows.Data.CollectionView>，當股票價值大於或小於其他股票的價值時<xref:System.Windows.Controls.DataGrid>，股票在移動中的位置。   有關詳細資訊，請參閱介面<xref:System.ComponentModel.ICollectionViewLiveShaping>。  
  
<a name="weak_event_pattern"></a>
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>建立事件弱式參考的加強支援  
 實作弱式事件模式現在更加容易，因為事件訂閱者可以參與它而不用實作額外的介面。  泛型<xref:System.Windows.WeakEventManager>類還允許訂閱者參與弱事件模式（如果特定事件不存在專用<xref:System.Windows.WeakEventManager>事件）。  如需詳細資訊，請參閱[弱式事件模式](../advanced/weak-event-patterns.md)。  
  
<a name="async"></a>
## <a name="new-methods-for-the-dispatcher-class"></a>Dispatcher 類別的新方法  
 Dispatcher 類別會定義同步和非同步作業的新方法。  同步<xref:System.Windows.Threading.Dispatcher.Invoke%2A>方法定義採用<xref:System.Action>或<xref:System.Func%601>參數的重載。 新的非同步<xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>方法 ， 也採用<xref:System.Action>或<xref:System.Func%601>作為回檔參數並返回 或<xref:System.Windows.Threading.DispatcherOperation><xref:System.Windows.Threading.DispatcherOperation%601>。   <xref:System.Windows.Threading.DispatcherOperation>和<xref:System.Windows.Threading.DispatcherOperation%601>類定義屬性<xref:System.Threading.Tasks.Task>。  調用<xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>時，可以將`await`關鍵字與<xref:System.Windows.Threading.DispatcherOperation>或 關聯的<xref:System.Threading.Tasks.Task>。 如果需要同步<xref:System.Threading.Tasks.Task>等待 由<xref:System.Windows.Threading.DispatcherOperation>或<xref:System.Windows.Threading.DispatcherOperation%601>返回的 調用<xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A>擴充方法。 如果<xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>操作在調用執行緒上排隊，則調用將導致鎖死。 有關使用<xref:System.Threading.Tasks.Task>執行非同步作業的詳細資訊，請參閱[任務並行性（任務並行庫）。](../../../standard/parallel-programming/task-based-asynchronous-programming.md)  
  
<a name="events_markup_extenions"></a>
## <a name="markup-extensions-for-events"></a>事件的標記延伸  
 WPF 4.5 支援事件的標記延伸。  WPF 不會定義要用於事件的標記延伸，協力廠商可以建立可與事件一起使用的標記延伸。  
  
## <a name="see-also"></a>另請參閱

- [.NET 框架中的新增功能](../../whats-new/index.md)
