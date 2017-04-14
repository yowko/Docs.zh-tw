---
title: "最佳化效能：物件行為 | Microsoft Docs"
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
  - "相依性屬性, 效能"
  - "事件處理常式 [WPF]"
  - "Freezable 物件, 效能"
  - "物件效能考量"
  - "使用者介面虛擬化"
ms.assetid: 73aa2f47-1d73-439a-be1f-78dc4ba2b5bd
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 最佳化效能：物件行為
了解 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件的內建行為可以協助您在功能與效能之間做正確的取捨。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Not_Removing_Event_Handlers"></a>   
## 不移除物件的事件處理常式可以保持物件持續運作  
 物件傳給事件的委派其實是該物件的參考。  因此，事件處理常式可能會讓物件持續運作得比預期更久。  對已註冊接聽物件事件的物件執行清除時，最重要的動作是在釋放物件之前移除該委派。  讓不需要的物件持續運作會增加應用程式的記憶體使用量。  特別是在物件為[輯樹狀結構](GTMT)或[視覺化樹狀結構](GTMT)的根項目時更是如此。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用弱式事件接聽程式模式，以在物件存留期間難以判斷來源與接聽程式關係的情況下，追蹤有助於判斷的事件。  部分現有的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件會使用這個模式。  如果您以自訂事件實作物件，這個模式對您可能有用。  如需詳細資訊，請參閱[弱式事件模式](../../../../docs/framework/wpf/advanced/weak-event-patterns.md)。  
  
 有數個工具 \(例如 CLR 分析工具和工作集檢視器\) 可以提供所指定處理程序的記憶體使用量相關資訊。  CLR 分析工具包含一些相當有用的配置分析檢視，其中包括配置類型長條圖、配置和呼叫圖形、時間表 \(顯示各代記憶體回收以及回收之後 Managed 堆積 \(Heap\) 的狀態\)，以及呼叫樹狀結構 \(顯示每個方法的配置和組件負載\)。  如需詳細資訊，請參閱 [.NET Framework 開發人員中心](http://msdn.microsoft.com/zh-tw/netframework/aa497289.aspx) \(英文\)。  
  
<a name="DPs_and_Objects"></a>   
## 相依性屬性和物件  
 一般來說，存取 <xref:System.Windows.DependencyObject> 的[相依性屬性](GTMT)不會比存取 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性慢。  姑且不論設定屬性值會帶來少許效能負荷，取得值與從 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性取得值的速度一樣快。  [相依性屬性](GTMT)得以省去這少許效能負荷的關鍵在於，其能夠支援強大的功能，例如資料繫結、動畫、繼承和樣式。  如需詳細資訊，請參閱 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  
  
### DependencyProperty 最佳化  
 您應謹慎定義應用程式中的[相依性屬性](GTMT)。  如果 <xref:System.Windows.DependencyProperty> 只會影響呈現型別中繼資料 \(Metadata\) 選項，而不會影響 <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> 等其他中繼資料選項，您應該覆寫中繼資料來進行相關標示。  如需覆寫或取得屬性中繼資料的詳細資訊，請參閱[相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)。  
  
 如果不是所有屬性變更都會實際影響測量、排列和呈現，手動用屬性變更處理常式使測量、排列和呈現活動失效會更有效率。  例如，您可能決定只有在值大於設定的限制時重新呈現背景。  在此情況下，屬性變更常式只會在值超過設定的限制時使呈現失效。  
  
### 無法自由將 DependencyProperty 變成可繼承的屬性  
 根據預設，已註冊的[相依性屬性](GTMT)是不可繼承的。  不過，您可以明確讓任何屬性變成可繼承的。  雖然這是很有用的功能，但是將屬性轉換為可繼承的會增加讓屬性失效所需的時間長度，進而影響效能。  
  
### 小心使用 RegisterClassHandler  
 呼叫 <xref:System.Windows.EventManager.RegisterClassHandler%2A> 可以讓您儲存執行個體狀態，但是請務必注意，由於每個執行個體上都會呼叫這個處理常式，因此可能會造成效能問題。  只有在應用程式需要您儲存執行個體狀態時才使用 <xref:System.Windows.EventManager.RegisterClassHandler%2A>。  
  
### 註冊時設定 DependencyProperty 的預設值  
 建立需要預設值的 <xref:System.Windows.DependencyProperty> 時，請在預設中繼資料中加入預設值，然後做為參數傳遞至 <xref:System.Windows.DependencyProperty> 的 <xref:System.Windows.DependencyProperty.Register%2A> 方法。  請使用這個方式，而不是在建構函式 \(Constructor\) 中或項目的每個執行個體上設定屬性值。  
  
### 使用登錄來設定 PropertyMetadata 值  
 建立 <xref:System.Windows.DependencyProperty> 時，可以選擇使用 <xref:System.Windows.DependencyProperty.Register%2A> 或 <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> 方法來設定 <xref:System.Windows.PropertyMetadata>。  雖然您的物件可能已有靜態建構函式可以呼叫 <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>，但是這不是最佳的解決方案而且會影響效能。  如需最佳的效能，請在呼叫 <xref:System.Windows.DependencyProperty.Register%2A> 時設定 <xref:System.Windows.PropertyMetadata>。  
  
<a name="Freezable_Objects"></a>   
## Freezable 物件  
 <xref:System.Windows.Freezable> 是具有下列兩種狀態的特殊物件型別：未凍結和凍結。  只要一有可能就凍結物件，將能改善應用程式的效能並且減少其工作集。  如需詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
 每個 <xref:System.Windows.Freezable> 變更時，都會引發 <xref:System.Windows.Freezable.Changed> 事件。  不過，就應用程式效能的角度來說變更告知所費不眥。  
  
 請考量下列範例，範例中每個 <xref:System.Windows.Shapes.Rectangle> 都使用相同的 <xref:System.Windows.Media.Brush> 物件：  
  
 [!code-csharp[Performance#PerformanceSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 根據預設，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會針對 <xref:System.Windows.Media.SolidColorBrush> 物件的 <xref:System.Windows.Freezable.Changed> 事件提供事件處理常式，以使 <xref:System.Windows.Shapes.Rectangle> 物件的 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性失效。  在此情況下，每次 <xref:System.Windows.Media.SolidColorBrush> 需要引發其 <xref:System.Windows.Freezable.Changed> 事件時，都需要針對每個 <xref:System.Windows.Shapes.Rectangle> 叫用 \(Invoke\) 回呼函式 \(Callback Function\)。這些回呼函式叫用累積的越多，效能降得越多。  此外，在這個時候加入或移除處理常式會導致效能耗損，因為應用程式需要周遊整個清單以執行動作。  如果您的應用案例絕對不會變更 <xref:System.Windows.Media.SolidColorBrush>，您還是得付出維護不需要的 <xref:System.Windows.Freezable.Changed> 事件處理常式的成本。  
  
 凍結 <xref:System.Windows.Freezable> 可以改善效能，因為不再需要耗用資源來維護變更告知。  下表顯示一個簡單的 <xref:System.Windows.Media.SolidColorBrush> 在它的 <xref:System.Windows.Freezable.IsFrozen%2A> 屬性是設定為和不是設定為 `true` 時的大小。  其中假設將一個筆刷套用至十個 <xref:System.Windows.Shapes.Rectangle> 物件的 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性。  
  
|**狀態**|**Size**|  
|------------|--------------|  
|凍結的 <xref:System.Windows.Media.SolidColorBrush>|212 個位元組|  
|未凍結的 <xref:System.Windows.Media.SolidColorBrush>|972 個位元組|  
  
 下列程式碼範例示範這個概念：  
  
 [!code-csharp[Performance#PerformanceSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### 變更未凍結 Freezable 上的處理常式可能會讓物件持續運作  
 物件傳給 <xref:System.Windows.Freezable> 物件之 <xref:System.Windows.Freezable.Changed> 事件的委派，其實是該物件的參考。  因此，<xref:System.Windows.Freezable.Changed> 事件處理常式可以讓物件持續運作得比預期更久。  對已註冊接聽 <xref:System.Windows.Freezable> 物件之 <xref:System.Windows.Freezable.Changed> 事件的物件執行清除時，最重要的動作是在釋放物件之前移除該委派。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也會攔截內部的 <xref:System.Windows.Freezable.Changed> 事件。  例如，所有以 <xref:System.Windows.Freezable> 做為值的[相依性屬性](GTMT)都會自動接聽 <xref:System.Windows.Freezable.Changed> 事件。  以 <xref:System.Windows.Media.Brush> 為值的 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性會說明這個概念。  
  
 [!code-csharp[Performance#PerformanceSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 將 `myBrush` 指派給 `myRectangle.Fill` 時，<xref:System.Windows.Media.SolidColorBrush> 物件的 <xref:System.Windows.Freezable.Changed> 事件中會加入指回 <xref:System.Windows.Shapes.Rectangle> 物件的委派。  這表示下列程式碼不會實際將 `myRect` 納入記憶體回收作業：  
  
 [!code-csharp[Performance#PerformanceSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 在這個案例中，`myBrush` 仍然會使 `myRectangle` 持續運作，並且在這個物件引發 <xref:System.Windows.Freezable.Changed> 事件時回頭呼叫這個物件。  請注意，將 `myBrush` 指派給新 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性，不過是將另一個事件處理常式加入至 `myBrush`。  
  
 清除這類物件的建議方式是從 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性移除 <xref:System.Windows.Media.Brush>，這樣就會移除 <xref:System.Windows.Freezable.Changed> 事件處理常式。  
  
 [!code-csharp[Performance#PerformanceSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## 使用者介面虛擬化  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也提供另一種 <xref:System.Windows.Controls.StackPanel> 項目，這種項目會自動「虛擬化」資料繫結子內容。  在此情況下，「虛擬化」一詞是指一種技術，這種技術可以依據畫面上所顯示的項目，從眾多資料項目當中產生物件的子集。  在指定時間畫面上只會出現少數項目時，產生大量 UI 項目會耗用許多記憶體和處理器資源。  <xref:System.Windows.Controls.VirtualizingStackPanel> 會 \(透過 <xref:System.Windows.Controls.VirtualizingPanel> 所提供的功能\) 計算可見項目 \(Item\)，並從 <xref:System.Windows.Controls.ItemsControl> \(例如 <xref:System.Windows.Controls.ListBox> 或 <xref:System.Windows.Controls.ListView>\) 搭配 <xref:System.Windows.Controls.ItemContainerGenerator> 使用，只為可見項目 \(Item\) 建立項目 \(Element\)。  
  
 做為效能最佳化的方法，這些項目的視覺物件只會在可於螢幕上看見時產生或持續運作。  當不再位於控制項的可見區域中時，視覺物件會遭到移除。  這項功能不能與資料虛擬化混淆，在資料虛擬化中資料物件不存在於本機集合中，而是視需要透過資料流傳入。  
  
 下表顯示將 5000 個 <xref:System.Windows.Controls.TextBlock> 項目加入及呈現至 <xref:System.Windows.Controls.StackPanel> 和 <xref:System.Windows.Controls.VirtualizingStackPanel> 的耗用時間。  這個案例中的度量單位，代表從將文字字串附加至 <xref:System.Windows.Controls.ItemsControl> 物件的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性，至面板項目顯示文字字串的時間。  
  
|**主面板**|**轉譯時間 \(毫秒\)**|  
|-------------|---------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## 請參閱  
 [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [應用程式效能規劃](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [運用硬體](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [2D 圖形和影像](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [應用程式資源](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [文字](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [其他效能建議](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)