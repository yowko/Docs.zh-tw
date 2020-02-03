---
title: WPF 4.5 版的新功能
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 8eff8da7746047c450b2e23af63d43b13f3b970c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746927"
---
# <a name="whats-new-in-wpf-version-45"></a>WPF 4.5 版的新功能
<a name="introduction"></a>本主題包含 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 版本4.5 中新增和增強功能的相關資訊。  
  
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
 WPF 4.5 隨附一個 <xref:System.Windows.Controls.Ribbon.Ribbon> 控制項，它會裝載快速存取工具列、應用程式功能表和索引標籤。  如需詳細資訊，請參閱[功能區概觀](/visualstudio/vsto/ribbon-overview)。  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>顯示大型群組資料集合時改善效能  
 UI 虛擬化會在使用者介面 (UI) 元素的子集從大量資料項目，根據可在畫面上看到的項目來產生時發生。 <xref:System.Windows.Controls.VirtualizingPanel> 會定義 <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> 附加屬性，以啟用群組資料的 UI 虛擬化。  如需群組資料的詳細資訊，請參閱「如何：使用 XAML 中的檢視排序和分組資料」。  如需虛擬化群組資料的詳細資訊，請參閱 <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> 附加屬性。  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>VirtualizingPanel 的新功能  
  
1. 您可以使用 <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> 附加屬性來指定 <xref:System.Windows.Controls.VirtualizingPanel>（例如 <xref:System.Windows.Controls.VirtualizingStackPanel>）是否會顯示部分專案。 如果 <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> 設定為 [<xref:System.Windows.Controls.ScrollUnit.Item>]，則 <xref:System.Windows.Controls.VirtualizingPanel> 只會顯示完全可見的專案。 如果 <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> 設定為 [<xref:System.Windows.Controls.ScrollUnit.Pixel>]，<xref:System.Windows.Controls.VirtualizingPanel> 可以顯示部分可見的專案。  
  
2. 您可以使用 <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> 附加屬性，在 <xref:System.Windows.Controls.VirtualizingPanel> 進行虛擬化時，指定視口前後的快取大小。  快取是不虛擬化項目之高於或低於檢視區的空間量。  使用快取以避免產生 UI 元素，因為它們捲動至檢視中可以改善效能。 填入快取的優先順序較低，讓應用程式在作業期間不會變成沒有回應。 <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> 屬性會決定 <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>所使用的度量單位。  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>繫結至靜態屬性  
 您可以使用靜態屬性做為資料繫結的來源。 資料繫結引擎會辨識當引發靜態事件時，屬性的值何時變更。  例如，如果類別 `SomeClass` 定義靜態屬性，稱為 `MyProperty`，`SomeClass` 可以定義為靜態事件，該事件在 `MyProperty` 的值變更時引發。  靜態事件可以使用下列簽章。  
  
- `public static event EventHandler MyPropertyChanged;`  
  
- `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 請注意，在第一個案例中，類別會公開名為*PropertyName*`Changed` 的靜態事件，將 <xref:System.EventArgs> 傳遞給事件處理常式。  在第二個案例中，類別會公開名為 `StaticPropertyChanged` 的靜態事件，將 <xref:System.ComponentModel.PropertyChangedEventArgs> 傳遞給事件處理常式。 實作靜態屬性的類別，可以選擇使用任一種方法引發屬性變更通知。  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>存取非 UI 執行緒上的集合  
 WPF 可讓您存取和修改在執行緒上的資料集合，不是建立集合的執行緒。  這可讓您使用背景執行緒從外部來源 (例如資料庫) 接收資料，並且在 UI 執行緒上顯示資料。  藉由使用另一個執行緒來修改集合，您的使用者介面仍然能夠保持對使用者互動回應。  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>同步和非同步驗證資料  
 <xref:System.ComponentModel.INotifyDataErrorInfo> 介面可讓資料實體類別執行自訂驗證規則，並以非同步方式公開驗證結果。 此介面也支援自訂錯誤物件、每個屬性多個錯誤、跨屬性錯誤，以及實體層級錯誤。  如需詳細資訊，請參閱 <xref:System.ComponentModel.INotifyDataErrorInfo>。  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>自動更新資料繫結的來源  
 如果您使用資料系結來更新資料來源，您可以使用 [<xref:System.Windows.Data.BindingBase.Delay%2A>] 屬性，指定在來源更新之前，在目標上進行屬性變更之後所要傳遞的時間量。  例如，假設您有一個 <xref:System.Windows.Controls.Slider>，其 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> 屬性資料雙向系結至資料物件的屬性，且 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性設定為 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。  在此範例中，當使用者移動 <xref:System.Windows.Controls.Slider>時，<xref:System.Windows.Controls.Slider> 所移動之每個圖元的來源會更新。  來源物件通常只有在滑杆的 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> 停止變更時，才需要滑杆的值。  若要防止經常更新來源，請使用 <xref:System.Windows.Data.BindingBase.Delay%2A> 指定來源不應更新，直到捲動方塊停止移動之後的特定時間量過期為止。  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>繫結至實作 ICustomTypeProvider 的型別  
 WPF 支援將資料系結至執行 <xref:System.Reflection.ICustomTypeProvider>的物件，也稱為自訂類型。  您可以在下列情況下使用自訂型別。  
  
1. 做為資料系結中的 <xref:System.Windows.PropertyPath>。 例如，<xref:System.Windows.Data.Binding> 的 <xref:System.Windows.Data.Binding.Path%2A> 屬性可以參考自訂類型的屬性。  
  
2. 做為 <xref:System.Windows.DataTemplate.DataType%2A> 屬性的值。  
  
3. 做為決定 <xref:System.Windows.Controls.DataGrid>中自動產生之資料行的類型。  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>從繫結運算式擷取資料繫結資訊  
 在某些情況下，您可能會取得 <xref:System.Windows.Data.Binding> 的 <xref:System.Windows.Data.BindingExpression>，而且需要系結之來源和目標物件的相關資訊。  新的 API 已新增，可讓您取得來源或目標物件或相關聯的屬性。  當您有 <xref:System.Windows.Data.BindingExpression>時，請使用下列 Api 來取得目標和來源的相關資訊。  
  
|若要尋找繫結的此值|使用此 API|  
|---------------------------------------|------------------|  
|目標物件|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|目標屬性|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|來源物件|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|來源屬性|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Data.BindingExpression> 是否屬於 <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Data.BindingGroup> 的擁有者|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>檢查有效的 DataContext 物件  
 在某些情況下，<xref:System.Windows.Controls.ItemsControl> 中的專案容器 <xref:System.Windows.FrameworkElement.DataContext%2A> 會中斷連接。  專案容器是在 <xref:System.Windows.Controls.ItemsControl>中顯示專案的 UI 元素。  當 <xref:System.Windows.Controls.ItemsControl> 系結至集合的資料時，會針對每個專案產生專案容器。 在某些情況下，項目容器會從視覺化樹狀結構移除。 從基礎集合中移除專案，以及在 <xref:System.Windows.Controls.ItemsControl>上啟用虛擬化時，會移除專案容器的兩個典型案例。 在這些情況下，專案容器的 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性會設定為 <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> 靜態屬性所傳回的 sentinel 物件。  在存取專案容器的 <xref:System.Windows.FrameworkElement.DataContext%2A> 之前，您應該先檢查 <xref:System.Windows.FrameworkElement.DataContext%2A> 是否等於 <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> 物件。  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>隨著資料值變更重新調整資料的位置 (即時繪圖)  
 資料的集合可以分組、排序或篩選。 WPF 4.5 可讓資料在修改時重新排列。 例如，假設應用程式使用 <xref:System.Windows.Controls.DataGrid> 來列出股票市場中的股票，而股票則依股票值排序。 若在股票的 <xref:System.Windows.Data.CollectionView>上啟用即時排序，則庫存的 <xref:System.Windows.Controls.DataGrid> 位置會在庫存的值變得大於或小於另一個股票值時移動。   如需詳細資訊，請參閱 <xref:System.ComponentModel.ICollectionViewLiveShaping> 介面。  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>建立事件弱式參考的加強支援  
 實作弱式事件模式現在更加容易，因為事件訂閱者可以參與它而不用實作額外的介面。  一般 <xref:System.Windows.WeakEventManager> 類別也可以讓訂閱者參與弱式事件模式（如果特定的 <xref:System.Windows.WeakEventManager> 不存在於某個事件）。  如需詳細資訊，請參閱[弱式事件模式](../advanced/weak-event-patterns.md)。  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Dispatcher 類別的新方法  
 Dispatcher 類別會定義同步和非同步作業的新方法。  同步 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 方法會定義接受 <xref:System.Action> 或 <xref:System.Func%601> 參數的多載。 新的非同步方法 <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>也會採用 <xref:System.Action> 或 <xref:System.Func%601> 做為回呼參數，並傳回 <xref:System.Windows.Threading.DispatcherOperation> 或 <xref:System.Windows.Threading.DispatcherOperation%601>。   <xref:System.Windows.Threading.DispatcherOperation> 和 <xref:System.Windows.Threading.DispatcherOperation%601> 類別會定義 <xref:System.Threading.Tasks.Task> 屬性。  當您呼叫 <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>時，您可以使用 `await` 關鍵字搭配 <xref:System.Windows.Threading.DispatcherOperation> 或相關聯的 <xref:System.Threading.Tasks.Task>。 如果您需要以同步方式等候 <xref:System.Windows.Threading.DispatcherOperation> 或 <xref:System.Windows.Threading.DispatcherOperation%601>所傳回的 <xref:System.Threading.Tasks.Task>，請呼叫 <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> 擴充方法。 如果作業在呼叫執行緒上排入佇列，則呼叫 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 將會導致鎖死。 如需使用 <xref:System.Threading.Tasks.Task> 執行非同步作業的詳細資訊，請參閱工作平行處理原則[（工作平行程式庫）](../../../standard/parallel-programming/task-based-asynchronous-programming.md)。  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>事件的標記延伸  
 WPF 4.5 支援事件的標記延伸。  WPF 不會定義要用於事件的標記延伸，協力廠商可以建立可與事件一起使用的標記延伸。  
  
## <a name="see-also"></a>另請參閱

- [.NET Framework 的新功能](../../whats-new/index.md)
