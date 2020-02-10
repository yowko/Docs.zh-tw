---
title: 最佳化效能：物件行為
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interface virtualization [WPF]
- dependency properties [WPF], performance
- event handlers [WPF]
- object performance considerations [WPF]
- Freezable objects [WPF], performance
ms.assetid: 73aa2f47-1d73-439a-be1f-78dc4ba2b5bd
ms.openlocfilehash: 64e567cd28e9458b483b0963e0dedd924ad23bab
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094484"
---
# <a name="optimizing-performance-object-behavior"></a>最佳化效能：物件行為
了解 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件的內建行為有助您做出功能和效能之間的正確取捨。  

<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>不移除物件的事件處理常式可能會保持物件運作  
 物件傳遞給其事件的委派實際上是對該物件的參考。 因此，事件處理常式可以讓物件保持運作時間超出預期。 在對已註冊要接聽物件事件的物件執行清除時，務必要在釋放物件之前先移除該委派。 讓不需要的物件保持運行狀態會增加應用程式的記憶體使用量。 特別是當物件是邏輯樹狀結構或視覺化樹狀結構的根目錄時。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 針對適用於來源與接聽程式之間物件存留期關係難以追蹤的情況的事件，引進了弱式事件接聽程式模式。 某些現有的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件會使用此模式。 如果您正在以自訂事件實作物件，這個模式可能對您有用。 如需詳細資訊，請參閱[弱式事件模式](weak-event-patterns.md)。  
  
 有數個工具，例如 CLR 分析工具和工作集檢視器，可以提供有關指定處理序的記憶體使用量資訊。 CLR 分析工具包含許多配置設定檔的極有用檢視，包括已配置類型長條圖、配置和呼叫圖形、顯示各種層代記憶體回收的時間線和回收之後產生的 managed 堆積狀態，以及顯示每個方法配置和組件載入的呼叫樹狀結構。 如需詳細資訊，請參閱[效能](https://docs.microsoft.com/previous-versions/aa497289(v=msdn.10))。  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>相依性屬性與物件  
 一般來說，存取 <xref:System.Windows.DependencyObject> 的相依性屬性，並不會比存取 CLR 屬性慢。 雖然設定屬性值的效能會很小，但是取得值的速度就和從 CLR 屬性取得值一樣快。 小小效能負荷的補償是相依性屬性可支援強大的功能，例如資料繫結、動畫、繼承和樣式。 如需詳細資訊，請參閱[相依性屬性概觀](dependency-properties-overview.md)。  
  
### <a name="dependencyproperty-optimizations"></a>DependencyProperty 最佳化  
 您應該在應用程式中非常小心地定義相依性屬性。 如果您的 <xref:System.Windows.DependencyProperty> 只會影響轉譯類型中繼資料選項，而不是其他中繼資料選項（例如 <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>），您應該將其標示為覆寫它的中繼資料。 如需覆寫或取得屬性中繼資料的詳細資訊，請參閱[相依性屬性中繼資料](dependency-property-metadata.md)。  
  
 如果並非所有屬性變更都會實際上影響測量、排列與轉譯，手動讓屬性變更處理常式使測量、排列與轉譯階段失效，可能會更有效率。 比方說，您可能決定只有在值大於設定的限制時，才重新轉譯背景。 在此情況下，您的屬性變更處理常式只會在值超過設定的限制時使轉譯器失效。  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>使 DependencyProperty 成為可繼承不是免費的  
 根據預設，已註冊的相依性屬性是不可繼承的。 不過，您可以明確地使任何屬性成為可繼承。 雖然這是很有用的功能，但將屬性轉換為可繼承會影響效能，因為會增加屬性失效的時間長度。  
  
### <a name="use-registerclasshandler-carefully"></a>小心使用 RegisterClassHandler  
 當您呼叫 <xref:System.Windows.EventManager.RegisterClassHandler%2A> 可讓您儲存實例狀態時，請務必注意，在每個實例上呼叫處理常式會造成效能問題。 當您的應用程式需要您儲存實例狀態時，才使用 <xref:System.Windows.EventManager.RegisterClassHandler%2A>。  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>在註冊期間設定 DependencyProperty 的預設值  
 建立需要預設值的 <xref:System.Windows.DependencyProperty> 時，請使用傳遞做為參數的預設中繼資料，將此值設定為 <xref:System.Windows.DependencyProperty>的 <xref:System.Windows.DependencyProperty.Register%2A> 方法。 使用這項技術，而不是在建構函式或項目的每個執行個體上設定屬性值。  
  
### <a name="set-the-propertymetadata-value-using-register"></a>使用 Register 設定 PropertyMetadata 值  
 建立 <xref:System.Windows.DependencyProperty>時，您可以選擇使用 <xref:System.Windows.DependencyProperty.Register%2A> 或 <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> 方法來設定 <xref:System.Windows.PropertyMetadata>。 雖然您的物件可以有靜態的函式來呼叫 <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>，但這不是最佳的解決方案，而且會影響效能。 為了達到最佳效能，請在呼叫 <xref:System.Windows.DependencyProperty.Register%2A>期間設定 <xref:System.Windows.PropertyMetadata>。  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Freezable 物件  
 <xref:System.Windows.Freezable> 是特殊類型的物件，有兩種狀態： [未凍結] 和 [已凍結]。 盡可能凍結物件可以提升應用程式的效能，並縮減其工作集。 如需詳細資訊，請參閱 [Freezable 物件概觀](freezable-objects-overview.md)。  
  
 每個 <xref:System.Windows.Freezable> 都會有每次變更時所引發的 <xref:System.Windows.Freezable.Changed> 事件。 不過，變更通知會嚴重降低應用程式效能。  
  
 請考慮下列範例，其中每個 <xref:System.Windows.Shapes.Rectangle> 都會使用相同的 <xref:System.Windows.Media.Brush> 物件：  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 根據預設，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會提供 <xref:System.Windows.Media.SolidColorBrush> 物件 <xref:System.Windows.Freezable.Changed> 事件的事件處理常式，以便使 <xref:System.Windows.Shapes.Rectangle> 物件的 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性失效。 在此情況下，每次 <xref:System.Windows.Media.SolidColorBrush> 都必須引發其 <xref:System.Windows.Freezable.Changed> 事件時，就必須為每個 <xref:System.Windows.Shapes.Rectangle>叫用回呼函式，而這些回呼函數調用的累積會造成顯著的效能影響。 此外，在此時新增和移除處理常式會相當耗損效能，因為應用程式必須周遊整個清單才能執行這項操作。 如果您的應用程式案例永遠不會改變 <xref:System.Windows.Media.SolidColorBrush>，您將需要支付維護 <xref:System.Windows.Freezable.Changed> 事件處理常式不必要的成本。  
  
 凍結 <xref:System.Windows.Freezable> 可以改善其效能，因為它不再需要耗費資源來維護變更通知。 下表顯示當簡單 <xref:System.Windows.Media.SolidColorBrush> 的 <xref:System.Windows.Freezable.IsFrozen%2A> 屬性設定為 `true`時，其大小（相較于非）。 這會假設將一個筆刷套用至十個 <xref:System.Windows.Shapes.Rectangle> 物件的 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性。  
  
|**State**|**大小**|  
|---------------|--------------|  
|凍結的 <xref:System.Windows.Media.SolidColorBrush>|212 個位元組|  
|未凍結的 <xref:System.Windows.Media.SolidColorBrush>|972 個位元組|  
  
 下列程式碼範例說明此概念：  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>未凍結的 Freezable 上的已變更處理常式可能會保持物件運作  
 物件傳遞給 <xref:System.Windows.Freezable> 物件之 <xref:System.Windows.Freezable.Changed> 事件的委派實際上是該物件的參考。 因此，<xref:System.Windows.Freezable.Changed> 事件處理常式可以讓物件的運作時間超過預期。 在執行已註冊要接聽 <xref:System.Windows.Freezable> 物件之 <xref:System.Windows.Freezable.Changed> 事件的物件清除時，必須先移除該委派，然後再釋放物件。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也會在內部連結 <xref:System.Windows.Freezable.Changed> 事件。 例如，以 <xref:System.Windows.Freezable> 做為值的所有相依性屬性都會自動接聽 <xref:System.Windows.Freezable.Changed> 事件。 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性（採用 <xref:System.Windows.Media.Brush>）會說明此概念。  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 在 `myBrush` 指派 `myRectangle.Fill`時，指向 <xref:System.Windows.Shapes.Rectangle> 物件的委派會加入 <xref:System.Windows.Media.SolidColorBrush> 物件的 <xref:System.Windows.Freezable.Changed> 事件中。 這表示下列程式碼實際上不會讓 `myRect` 符合記憶體回收資格︰  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 在此情況下，`myBrush` 仍會保持 `myRectangle` 運作，並在引發其 <xref:System.Windows.Freezable.Changed> 事件時回呼。 請注意，將 `myBrush` 指派給新 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性，只會將另一個事件處理常式新增至 `myBrush`。  
  
 清除這些物件類型的建議方式是從 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性移除 <xref:System.Windows.Media.Brush>，然後再移除 <xref:System.Windows.Freezable.Changed> 事件處理常式。  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>使用者介面虛擬化  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也會提供 <xref:System.Windows.Controls.StackPanel> 元素的變化，自動「虛擬化」資料系結的子內容。 在此內容中，「虛擬化」一字係指一種技術，藉由這種技術，將可從較大量的資料項目，根據畫面上可見的項目來產生物件子集。 當在指定的時間內畫面上只能有幾個 UI 元素時，不論是就記憶體還是處理器而言，產生大量 UI 元素都會相當耗費資源。 <xref:System.Windows.Controls.VirtualizingStackPanel> （透過 <xref:System.Windows.Controls.VirtualizingPanel>提供的功能）會計算可見專案，並使用 <xref:System.Windows.Controls.ItemsControl> （例如 <xref:System.Windows.Controls.ListBox> 或 <xref:System.Windows.Controls.ListView>）中的 <xref:System.Windows.Controls.ItemContainerGenerator>，來建立可見專案的元素。  
  
 作為效能最佳化，只有在這些項目的視覺物件顯示在螢幕上時才會產生或保持這些項目的視覺物件運作。 如果視覺物件不再位於控制項的可檢視區域中，可能會移除視覺物件。 這並不會與資料虛擬化混淆，在資料虛擬化中，資料物件不會全都在本機集合，而是視需要進行資料流處理。  
  
 下表顯示在 <xref:System.Windows.Controls.StackPanel> 和 <xref:System.Windows.Controls.VirtualizingStackPanel>中，將 5000 <xref:System.Windows.Controls.TextBlock> 專案加入和轉譯的經過時間。 在此案例中，測量代表將文字字串附加至 <xref:System.Windows.Controls.ItemsControl> 物件的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性到面板元素顯示文字字串之間的時間。  
  
|**主面板**|**轉譯時間 (毫秒)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>另請參閱

- [最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)
- [應用程式效能規劃](planning-for-application-performance.md)
- [運用硬體](optimizing-performance-taking-advantage-of-hardware.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [2D 圖形和影像處理](optimizing-performance-2d-graphics-and-imaging.md)
- [應用程式資源](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [資料繫結](optimizing-performance-data-binding.md)
- [其他效能建議](optimizing-performance-other-recommendations.md)
