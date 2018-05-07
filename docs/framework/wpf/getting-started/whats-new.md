---
title: WPF 4.5 版的新功能
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 4e022f75808de36666e53d3e58a0806e4f6d15ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="what39s-new-in-wpf-version-45"></a>WPF 4.5 版的新功能
<a name="introduction"></a> 本主題包含新功能和增強功能的相關資訊[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]4.5 版。  
  
 此主題包括下列章節：  
  
-   [功能區控制項](#ribbon_control)  
  
-   [顯示大型群組資料集合時改善效能](#grouped_virtualization)  
  
-   [VirtualizingPanel 的新功能](#VirtualizingPanel)  
  
-   [繫結至靜態屬性](#static_properties)  
  
-   [存取非 UI 執行緒上的集合](#xthread_access)  
  
-   [同步和非同步驗證資料](#INotifyDataErrorInfo)  
  
-   [自動更新資料繫結的來源](#delay)  
  
-   [繫結至實作 ICustomTypeProvider 的型別](#ICustomTypeProvider)  
  
-   [從繫結運算式擷取資料繫結資訊](#binding_state)  
  
-   [檢查有效的 DataContext 物件](#DisconnectedSource)  
  
-   [隨著資料值變更重新調整資料的位置 (即時繪圖)](#live_shaping)  
  
-   [建立事件弱式參考的加強支援](#weak_event_pattern)  
  
-   [Dispatcher 類別的新方法](#async)  
  
-   [事件的標記延伸](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a>功能區控制項  
 WPF 4.5 隨附<xref:System.Windows.Controls.Ribbon.Ribbon>裝載了 快速存取工具列、 應用程式功能表 及 索引標籤的控制項。  如需詳細資訊，請參閱[功能區概觀](/visualstudio/vsto/ribbon-overview)。  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>顯示大型群組資料集合時改善效能  
 UI 虛擬化會在使用者介面 (UI) 元素的子集從大量資料項目，根據可在畫面上看到的項目來產生時發生。 <xref:System.Windows.Controls.VirtualizingPanel>定義<xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A>附加 UI 虛擬化讓群組資料的屬性。  如需群組資料的詳細資訊，請參閱「如何：使用 XAML 中的檢視排序和分組資料」。  如需有關虛擬化分組資料，請參閱 <<c0> <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> 附加屬性。  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>VirtualizingPanel 的新功能  
  
1.  您可以指定是否<xref:System.Windows.Controls.VirtualizingPanel>，例如<xref:System.Windows.Controls.VirtualizingStackPanel>，藉由顯示部分項目<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>附加屬性。 如果<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>設<xref:System.Windows.Controls.ScrollUnit.Item>、<xref:System.Windows.Controls.VirtualizingPanel>只會顯示完整的看見的項目。 如果<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>設<xref:System.Windows.Controls.ScrollUnit.Pixel>、<xref:System.Windows.Controls.VirtualizingPanel>可以顯示有部分顯示的項目。  
  
2.  檢視區的前後，您可以指定快取大小時<xref:System.Windows.Controls.VirtualizingPanel>正在使用虛擬化<xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A>附加屬性。  快取是不虛擬化項目之高於或低於檢視區的空間量。  使用快取以避免產生 UI 元素，因為它們捲動至檢視中可以改善效能。 填入快取的優先順序較低，讓應用程式在作業期間不會變成沒有回應。 <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType>屬性會決定所使用的度量單位<xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>。  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>繫結至靜態屬性  
 您可以使用靜態屬性做為資料繫結的來源。 資料繫結引擎會辨識當引發靜態事件時，屬性的值何時變更。  例如，如果類別 `SomeClass` 定義靜態屬性，稱為 `MyProperty`，`SomeClass` 可以定義為靜態事件，該事件在 `MyProperty` 的值變更時引發。  靜態事件可以使用下列簽章。  
  
-   `public static event EventHandler MyPropertyChanged;`  
  
-   `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 請注意，在第一個案例中，這個類別會公開靜態事件，名為*PropertyName* `Changed`傳遞之任何<xref:System.EventArgs>事件處理常式。  在第二個案例中，這個類別會公開靜態事件，名為`StaticPropertyChanged`傳遞之任何<xref:System.ComponentModel.PropertyChangedEventArgs>事件處理常式。 實作靜態屬性的類別，可以選擇使用任一種方法引發屬性變更通知。  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>存取非 UI 執行緒上的集合  
 WPF 可讓您存取和修改在執行緒上的資料集合，不是建立集合的執行緒。  這可讓您使用背景執行緒從外部來源 (例如資料庫) 接收資料，並且在 UI 執行緒上顯示資料。  藉由使用另一個執行緒來修改集合，您的使用者介面仍然能夠保持對使用者互動回應。  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>同步和非同步驗證資料  
 <xref:System.ComponentModel.INotifyDataErrorInfo>介面可讓資料實體類別，實作自訂驗證規則，並以非同步方式公開 （expose） 驗證結果。 此介面也支援自訂錯誤物件、每個屬性多個錯誤、跨屬性錯誤，以及實體層級錯誤。  如需詳細資訊，請參閱<xref:System.ComponentModel.INotifyDataErrorInfo>。  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>自動更新資料繫結的來源  
 如果您使用資料繫結來更新資料來源時，您可以使用<xref:System.Windows.Data.BindingBase.Delay%2A>屬性來指定要傳遞之前來源更新目標上的屬性變更之後的時間量。  例如，假設您有<xref:System.Windows.Controls.Slider>具有其<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>屬性資料雙向繫結至資料物件的屬性和<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性設定為<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。  在此範例中，當使用者將<xref:System.Windows.Controls.Slider>，每個像素的來源更新的<xref:System.Windows.Controls.Slider>移動。  來源物件通常需要滑桿的值只有當滑桿的<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>停止變更。  若要避免太過頻繁更新來源，請使用<xref:System.Windows.Data.BindingBase.Delay%2A>指定軸之捲動方塊就會停止移動經過一段時間之前，不應更新來源。  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>繫結至實作 ICustomTypeProvider 的型別  
 WPF 支援實作物件的資料繫結<xref:System.Reflection.ICustomTypeProvider>，也稱為自訂型別。  您可以在下列情況下使用自訂型別。  
  
1.  做為<xref:System.Windows.PropertyPath>資料繫結中。 例如，<xref:System.Windows.Data.Binding.Path%2A>屬性<xref:System.Windows.Data.Binding>可以參考自訂類型的屬性。  
  
2.  值為<xref:System.Windows.DataTemplate.DataType%2A>屬性。  
  
3.  為決定自動產生的資料行中的型別<xref:System.Windows.Controls.DataGrid>。  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>從繫結運算式擷取資料繫結資訊  
 在某些情況下，您可能會收到<xref:System.Windows.Data.BindingExpression>的<xref:System.Windows.Data.Binding>，而且需要來源和目標物件的繫結的相關資訊。  新的 API 已新增，可讓您取得來源或目標物件或相關聯的屬性。  當您有<xref:System.Windows.Data.BindingExpression>，使用下列 Api 來取得有關目標和來源的資訊。  
  
|若要尋找繫結的此值|使用此 API|  
|---------------------------------------|------------------|  
|目標物件|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|目標屬性|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|來源物件|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|來源屬性|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|是否<xref:System.Windows.Data.BindingExpression>屬於 <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|擁有者 <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>檢查有效的 DataContext 物件  
 某些情況下其中<xref:System.Windows.FrameworkElement.DataContext%2A>項目容器中的<xref:System.Windows.Controls.ItemsControl>中斷連接。  項目容器是顯示的項目中的 UI 項目<xref:System.Windows.Controls.ItemsControl>。  當<xref:System.Windows.Controls.ItemsControl>是資料繫結至集合，項目容器會產生每個項目。 在某些情況下，項目容器會從視覺化樹狀結構移除。 移除項目容器的所在的兩種一般情況下會從基礎集合中移除項目時，當已啟用虛擬化<xref:System.Windows.Controls.ItemsControl>。 在這些情況下，<xref:System.Windows.FrameworkElement.DataContext%2A>的項目容器的屬性將設定成傳回 sentinel 物件<xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType>靜態屬性。  您應該檢查是否<xref:System.Windows.FrameworkElement.DataContext%2A>等於<xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A>之前存取物件<xref:System.Windows.FrameworkElement.DataContext%2A>的項目容器。  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>隨著資料值變更重新調整資料的位置 (即時繪圖)  
 資料的集合可以分組、排序或篩選。 WPF 4.5 可讓資料在修改時重新排列。 例如，假設應用程式使用<xref:System.Windows.Controls.DataGrid>列出股票市場的股票和股票依存貨值排序。 如果啟用即時排序股票 '<xref:System.Windows.Data.CollectionView>中的內建的位置<xref:System.Windows.Controls.DataGrid>移當股票價格的值會變成大於或小於另一個內建值。   如需詳細資訊，請參閱<xref:System.ComponentModel.ICollectionViewLiveShaping>介面。  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>建立事件弱式參考的加強支援  
 實作弱式事件模式現在更加容易，因為事件訂閱者可以參與它而不用實作額外的介面。  泛型<xref:System.Windows.WeakEventManager>類別也可讓訂閱者參與的弱式事件模式，如果是專用<xref:System.Windows.WeakEventManager>不存在的特定事件。  如需詳細資訊，請參閱[弱式事件模式](../../../../docs/framework/wpf/advanced/weak-event-patterns.md)。  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Dispatcher 類別的新方法  
 Dispatcher 類別會定義同步和非同步作業的新方法。  同步<xref:System.Windows.Threading.Dispatcher.Invoke%2A>方法所定義，採用多載<xref:System.Action>或<xref:System.Func%601>參數。 新的非同步方法， <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>，也會採用<xref:System.Action>或<xref:System.Func%601>做為回呼參數並傳回<xref:System.Windows.Threading.DispatcherOperation>或<xref:System.Windows.Threading.DispatcherOperation%601>。   <xref:System.Windows.Threading.DispatcherOperation>和<xref:System.Windows.Threading.DispatcherOperation%601>類別定義<xref:System.Threading.Tasks.Task>屬性。  當您呼叫<xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>，您可以使用`await`關鍵字使用<xref:System.Windows.Threading.DispatcherOperation>或相關聯<xref:System.Threading.Tasks.Task>。 如果您要同步等候<xref:System.Threading.Tasks.Task>所傳回<xref:System.Windows.Threading.DispatcherOperation>或<xref:System.Windows.Threading.DispatcherOperation%601>，呼叫<xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A>擴充方法。 呼叫<xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>如果呼叫執行緒上的作業會排入佇列，會導致死結。 如需有關使用<xref:System.Threading.Tasks.Task>為了執行非同步作業，請參閱[工作平行處理原則 （工作平行程式庫）](../../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)。  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>事件的標記延伸  
 WPF 4.5 支援事件的標記延伸。  WPF 不會定義要用於事件的標記延伸，協力廠商可以建立可與事件一起使用的標記延伸。  
  
## <a name="see-also"></a>另請參閱  
 [.NET Framework 的新功能](../../../../docs/framework/whats-new/index.md)
