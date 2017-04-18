---
title: "WPF 4.5 版的新功能 | Microsoft Docs"
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
  - "Windows Presentation Foundation, 新功能"
  - "WPF, 新功能"
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
caps.latest.revision: 55
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 55
---
# WPF 4.5 版的新功能
<a name="introduction"></a> 本主題包含 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 4.5 版中新功能和增強功能的相關資訊。  
  
 此主題包括下列章節：  
  
-   [功能區控制項](#ribbon_control)  
  
-   [提高效能，同時顯示大量分組資料時](#grouped_virtualization)  
  
-   [VirtualizingPanel 的新功能](#VirtualizingPanel)  
  
-   [繫結至靜態屬性](#static_properties)  
  
-   [在非 UI 執行緒存取集合。](#xthread_access)  
  
-   [同步和非同步驗證資料](#INotifyDataErrorInfo)  
  
-   [自動更新資料繫結的來源。](#delay)  
  
-   [繫結至實作的型別 ICustomTypeProvider](#ICustomTypeProvider)  
  
-   [擷取資料繫結資訊從一個繫結運算式](#binding_state)  
  
-   [檢查有效 DataContext 物件](#DisconnectedSource)  
  
-   [將資料當做資料值變更 \(Live 模型\)](#live_shaping)  
  
-   [改良的支援建立事件的弱式參考](#weak_event_pattern)  
  
-   [發送器類別中的新方法](#async)  
  
-   [事件的標記延伸](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## 功能區控制項  
 WPF 4.5 隨附於裝載一個快速存取工具列、應用程式功能表和 索引標籤上的 <xref:System.Windows.Controls.Ribbon.Ribbon> 控制項。  如需詳細資訊，請參閱[功能區概觀](../Topic/Ribbon%20Overview.md)。  
  
<a name="grouped_virtualization"></a>   
## 提高效能，同時顯示大量分組資料時  
 UI 虛擬化，發生於使用者介面項目 \(UI\) 的子集資料項目的最大數字 \(根據哪些項目產生是顯示在螢幕上。  <xref:System.Windows.Controls.VirtualizingPanel> 定義可分組之資料的 UI 虛擬化的 <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> 附加屬性。  如需群組資料的詳細資訊，請參閱\<HOW TO:使用 XAML 檢視中，已排序和分組。  如需有效群組資料的詳細資訊，請參閱 <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> 附加屬性。  
  
<a name="VirtualizingPanel"></a>   
## VirtualizingPanel 的新功能  
  
1.  您可以指定 <xref:System.Windows.Controls.VirtualizingPanel>，例如 <xref:System.Windows.Controls.VirtualizingStackPanel>，使用 <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> 附加屬性，是否僅顯示部分項目。  如果 <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> 設為 <xref:System.Windows.Controls.ScrollUnit>， <xref:System.Windows.Controls.VirtualizingPanel> 只會顯示完全可見的項目。  如果 <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> 設為 <xref:System.Windows.Controls.ScrollUnit>， <xref:System.Windows.Controls.VirtualizingPanel> 可顯示部分可見的項目。  
  
2.  您可以使用 <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> 附加屬性時，在中，當 <xref:System.Windows.Controls.VirtualizingPanel> 有效，您可以指定快取的大小在檢視區之前或之後。  快取是間距\] 或 項目所含的檢視區的上方。  使用快取以避免產生 UI 項目，是項目被捲動到檢視可以改善效能。  快取填入在較低優先權，如此應用程式就變得沒有回應在作業期間。  <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=fullName> 屬性 <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=fullName>決定使用的度量單位。  
  
<a name="static_properties"></a>   
## 繫結至靜態屬性  
 您可以使用靜態屬性為資料繫結的來源。  資料繫結引擎辨認屬性的值變更時，如果靜態事件會引發事件。  例如，如果類別， `SomeClass` 定義呼叫 `MyProperty`的靜態屬性， `SomeClass` 可以定義引發的靜態事件，當 `MyProperty` 的值變更時。  靜態事件可使用下列簽章之一。  
  
-   `public static event EventHandler MyPropertyChanged;`  
  
-   `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 請注意，在第一種情況下，類別會公開 <xref:System.EventArgs> 傳遞至事件處理常式 *屬性名稱*名為的靜態事件`Changed` 。  在第二種情況下，類別會公開 <xref:System.ComponentModel.PropertyChangedEventArgs> 傳遞至事件處理常式 `StaticPropertyChanged` 名為的靜態事件。  實作這個靜態屬性使用任一方法的類別，可以選擇引發屬性變更通知。  
  
<a name="xthread_access"></a>   
## 在非 UI 執行緒存取集合。  
 WPF 可讓您存取和修改在執行緒進行資料收集。除了建立集合的其他。  這可讓您使用背景執行緒上接收到來自外部來源的資料，例如資料庫，並將資料顯示在 UI 執行緒的資料。  您可以使用修改集合的另一個執行緒，您的使用者介面保持回應使用者互動。  
  
<a name="INotifyDataErrorInfo"></a>   
## 同步和非同步驗證資料  
 <xref:System.ComponentModel.INotifyDataErrorInfo> 介面可讓資料實體類別實作自訂驗證規則和公開驗證結果非同步。  這個介面也支援自訂錯誤物件、多個錯誤每個屬性，跨屬性錯誤和實體層級錯誤。  如需詳細資訊，請參閱<xref:System.ComponentModel.INotifyDataErrorInfo>。  
  
<a name="delay"></a>   
## 自動更新資料繫結的來源。  
 如果您使用資料繫結更新資料來源，您可以使用 <xref:System.Windows.Data.BindingBase.Delay%2A> 屬性指定一次傳遞中，在目標屬性變更時，在來源更新之前。  例如，假設有自己的屬性 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> 雙向資料繫結至資料物件屬性，並 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性設為的 <xref:System.Windows.Data.UpdateSourceTrigger>您有 <xref:System.Windows.Controls.Slider> 。  在此範例中，會使用，在使用者移動 <xref:System.Windows.Controls.Slider>， <xref:System.Windows.Controls.Slider> 移動的每個像素的來源更新。  只有在滑桿的 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> 停止變更時，來源物件通常需要滑桿的值。  若要防止太通常會更新來源，請使用 <xref:System.Windows.Data.BindingBase.Delay%2A> 指定不應該更新來源，直到大量的時間長度，在捲動方塊停止移動之後。  
  
<a name="ICustomTypeProvider"></a>   
## 繫結至實作的型別 ICustomTypeProvider  
 WPF 支援資料繫結 <xref:System.Reflection.ICustomTypeProvider>實作的物件，也稱為自訂型別。  您可以在下列情況下使用自訂型別。  
  
1.  做為 <xref:System.Windows.PropertyPath> 在資料繫結中。  例如， <xref:System.Windows.Data.Binding> 的 <xref:System.Windows.Data.Binding.Path%2A> 屬性可參考自訂型別的屬性。  
  
2.  <xref:System.Windows.DataTemplate.DataType%2A> 做為屬性的值。  
  
3.  以判斷在 <xref:System.Windows.Controls.DataGrid>的自動產生之資料行的型別。  
  
<a name="binding_state"></a>   
## 擷取資料繫結資訊從一個繫結運算式  
 在某些情況下，您可能會取得 <xref:System.Windows.Data.Binding> 的 <xref:System.Windows.Data.BindingExpression> 和所需的繫結來源和目標物件的相關資訊。  加入新的 API 可讓您取得來源或目標物件或相關聯的屬性。  當您有 <xref:System.Windows.Data.BindingExpression>時，請使用下列 API 取得有關目標和來源的資訊。  
  
|尋找繫結的這個值。|使用這個 API|  
|---------------|--------------|  
|目標物件|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=fullName>|  
|目標屬性|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=fullName>|  
|來源物件|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=fullName>|  
|來源屬性|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=fullName>|  
|<xref:System.Windows.Data.BindingExpression> 是否屬於 <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=fullName>|  
|<xref:System.Windows.Data.BindingGroup>的擁有者。|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## 檢查有效 DataContext 物件  
 具有項目容器 <xref:System.Windows.FrameworkElement.DataContext%2A> 在 <xref:System.Windows.Controls.ItemsControl> 的變成不相關的情況。  項目容器是顯示在 <xref:System.Windows.Controls.ItemsControl>的某個項目的 UI 項目。  當 <xref:System.Windows.Controls.ItemsControl> 都會繫結至集合時，項目容器為每個項目產生。  在某些情況下，項目容器自視覺化樹狀結構中移除。  項目容器移除的兩個常見的情況是項目從基礎集合中移除，而且會在虛擬 <xref:System.Windows.Controls.ItemsControl>時啟用。  在這些情況下，項目容器的 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性會設定為由 <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=fullName> 靜態屬性所傳回的 Sentinel 物件。  您應該確認是否 <xref:System.Windows.FrameworkElement.DataContext%2A> 與 <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> 物件等於在存取項目容器的 <xref:System.Windows.FrameworkElement.DataContext%2A> 之前。  
  
<a name="live_shaping"></a>   
## 將資料當做資料值變更 \(Live 模型\)  
 資料可以群組，排序或篩選。  當修改時， WPF 4.5 可讓資料重新整理資料。  例如，假設應用程式會在股市上使用 <xref:System.Windows.Controls.DataGrid> 股票清單，並共用由內建值排序。  使用排序在共用的 <xref:System.Windows.Data.CollectionView>有效，則 <xref:System.Windows.Controls.DataGrid> 的共用位置移動，所共用的值大於另一個共用的值為大於或小於。  如需詳細資訊，請參閱 <xref:System.ComponentModel.ICollectionViewLiveShaping> 介面。  
  
<a name="weak_event_pattern"></a>   
## 改良的支援建立事件的弱式參考  
 實作弱式事件模式現在變得更加容易，因為事件的訂閱者可以參與，而不需要實作額外的介面。  如果專屬的 <xref:System.Windows.WeakEventManager> 提供一些事件，不存在 <xref:System.Windows.WeakEventManager> 泛型類別也可讓訂閱者參與弱式事件模式。  如需詳細資訊，請參閱[弱式事件模式](../../../../docs/framework/wpf/advanced/weak-event-patterns.md)。  
  
<a name="async"></a>   
## 發送器類別中的新方法  
 發送器類別定義同步和非同步作業的新方法。  同步處理 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 方法會定義接受 <xref:System.Action> 或 <xref:System.Func%601> 參數的多載。  新的非同步方法， <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>，也會接受 <xref:System.Action> 或 <xref:System.Func%601> 做為回呼參數並傳回 <xref:System.Windows.Threading.DispatcherOperation> 或 <xref:System.Windows.Threading.DispatcherOperation%601>。  <xref:System.Windows.Threading.DispatcherOperation> 和 <xref:System.Windows.Threading.DispatcherOperation%601> 類別定義 <xref:System.Threading.Tasks.Task> 屬性。  當您呼叫 <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>時，您可以使用 <xref:System.Windows.Threading.DispatcherOperation> 或相關聯的 <xref:System.Threading.Tasks.Task>的 `await` 關鍵字。  如果由 <xref:System.Windows.Threading.DispatcherOperation> 或 <xref:System.Windows.Threading.DispatcherOperation%601>傳回需要同步處理 <xref:System.Threading.Tasks.Task> 等等，請呼叫 <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> 擴充方法。  如果作業在呼叫的執行緒，佇列呼叫 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=fullName> 造成死結 \(Deadlock\)。  如需使用的 <xref:System.Threading.Tasks.Task> 執行非同步作業，請參閱 [工作平行處理原則 \(工作平行程式庫\)](../../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)。  
  
<a name="events_markup_extenions"></a>   
## 事件的標記延伸  
 WPF 4.5 支援事件的標記延伸。  當 WPF 不會定義為事件時所要使用的標記延伸，協力廠商可以建立可搭配事件使用的標記延伸。  
  
## 請參閱  
 [.NET Framework 的新功能](../../../../docs/framework/whats-new/index.md)