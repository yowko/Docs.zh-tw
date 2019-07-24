---
title: 優化效能:物件行為
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
ms.openlocfilehash: 025c8691eb1aaf9483a222530a5590670ede486b
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400462"
---
# <a name="optimizing-performance-object-behavior"></a>優化效能:物件行為
了解 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件的內建行為有助您做出功能和效能之間的正確取捨。  

<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>不移除物件的事件處理常式可能會保持物件運作  
 物件傳遞給其事件的委派實際上是對該物件的參考。 因此，事件處理常式可以讓物件保持運作時間超出預期。 在對已註冊要接聽物件事件的物件執行清除時，務必要在釋放物件之前先移除該委派。 讓不需要的物件保持運行狀態會增加應用程式的記憶體使用量。 特別是當物件是邏輯樹狀結構或視覺化樹狀結構的根目錄時。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 針對適用於來源與接聽程式之間物件存留期關係難以追蹤的情況的事件，引進了弱式事件接聽程式模式。 某些現有的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件會使用此模式。 如果您正在以自訂事件實作物件，這個模式可能對您有用。 如需詳細資訊，請參閱[弱式事件模式](weak-event-patterns.md)。  
  
 有數個工具，例如 CLR 分析工具和工作集檢視器，可以提供有關指定處理序的記憶體使用量資訊。 CLR 分析工具包含許多配置設定檔的極有用檢視，包括已配置類型長條圖、配置和呼叫圖形、顯示各種層代記憶體回收的時間線和回收之後產生的 managed 堆積狀態，以及顯示每個方法配置和組件載入的呼叫樹狀結構。 如需詳細資訊，請參閱 [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=117435) (.NET Framework 開發人員中心)。  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>相依性屬性與物件  
 一般而言, 存取的相依性屬性<xref:System.Windows.DependencyObject>不會比存取 CLR 屬性慢。 雖然設定屬性值的效能會很小, 但是取得值的速度就和從 CLR 屬性取得值一樣快。 小小效能負荷的補償是相依性屬性可支援強大的功能，例如資料繫結、動畫、繼承和樣式。 如需詳細資訊，請參閱[相依性屬性概觀](dependency-properties-overview.md)。  
  
### <a name="dependencyproperty-optimizations"></a>DependencyProperty 最佳化  
 您應該在應用程式中非常小心地定義相依性屬性。 如果您<xref:System.Windows.DependencyProperty>只影響轉譯類型中繼資料選項, 而不是其他中繼資料<xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>選項 (例如), 您應該將其標示為覆寫其中繼資料。 如需覆寫或取得屬性中繼資料的詳細資訊，請參閱[相依性屬性中繼資料](dependency-property-metadata.md)。  
  
 如果並非所有屬性變更都會實際上影響測量、排列與轉譯，手動讓屬性變更處理常式使測量、排列與轉譯階段失效，可能會更有效率。 比方說，您可能決定只有在值大於設定的限制時，才重新轉譯背景。 在此情況下，您的屬性變更處理常式只會在值超過設定的限制時使轉譯器失效。  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>使 DependencyProperty 成為可繼承不是免費的  
 根據預設，已註冊的相依性屬性是不可繼承的。 不過，您可以明確地使任何屬性成為可繼承。 雖然這是很有用的功能，但將屬性轉換為可繼承會影響效能，因為會增加屬性失效的時間長度。  
  
### <a name="use-registerclasshandler-carefully"></a>小心使用 RegisterClassHandler  
 雖然呼叫<xref:System.Windows.EventManager.RegisterClassHandler%2A>可讓您儲存實例狀態, 但請務必注意, 處理常式是在每個實例上呼叫, 這可能會造成效能問題。 只有在<xref:System.Windows.EventManager.RegisterClassHandler%2A>您的應用程式需要您儲存實例狀態時, 才使用。  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>在註冊期間設定 DependencyProperty 的預設值  
 建立<xref:System.Windows.DependencyProperty>需要預設值的時, 請使用傳遞做為參數的預設中繼資料, 將值設定<xref:System.Windows.DependencyProperty.Register%2A>為的方法<xref:System.Windows.DependencyProperty>。 使用這項技術，而不是在建構函式或項目的每個執行個體上設定屬性值。  
  
### <a name="set-the-propertymetadata-value-using-register"></a>使用 Register 設定 PropertyMetadata 值  
 建立<xref:System.Windows.DependencyProperty>時, 您可以選擇<xref:System.Windows.PropertyMetadata>使用<xref:System.Windows.DependencyProperty.Register%2A>或<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>方法來設定。 雖然您的物件可以呼叫<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>靜態的函式, 但這不是最佳的解決方案, 而且會影響效能。 為了達到最佳效能, 請<xref:System.Windows.PropertyMetadata>在<xref:System.Windows.DependencyProperty.Register%2A>呼叫期間設定。  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Freezable 物件  
 <xref:System.Windows.Freezable>是特殊類型的物件, 有兩種狀態: [未凍結] 和 [已凍結]。 盡可能凍結物件可以提升應用程式的效能，並縮減其工作集。 如需詳細資訊，請參閱 [Freezable 物件概觀](freezable-objects-overview.md)。  
  
 每<xref:System.Windows.Freezable>個都<xref:System.Windows.Freezable.Changed>有每次變更時所引發的事件。 不過，變更通知會嚴重降低應用程式效能。  
  
 請考慮下列範例, 其中每<xref:System.Windows.Shapes.Rectangle>個都會使用<xref:System.Windows.Media.Brush>相同的物件:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 根據預設, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]會提供<xref:System.Windows.Media.SolidColorBrush>物件<xref:System.Windows.Freezable.Changed>之事件的事件處理常式, 以便使<xref:System.Windows.Shapes.Rectangle>物件的<xref:System.Windows.Shapes.Shape.Fill%2A>屬性失效。 在這種情況下, 每<xref:System.Windows.Media.SolidColorBrush>次必須引發其<xref:System.Windows.Freezable.Changed>事件時, 都必須叫用每個<xref:System.Windows.Shapes.Rectangle>的回呼函式, 而這些回呼函數調用的累積會造成顯著的效能負面影響。 此外，在此時新增和移除處理常式會相當耗損效能，因為應用程式必須周遊整個清單才能執行這項操作。 如果您的<xref:System.Windows.Media.SolidColorBrush>應用程式案例永遠不會變更, 您將需要支付維護<xref:System.Windows.Freezable.Changed>事件處理常式不必要的成本。  
  
 <xref:System.Windows.Freezable>凍結可以改善其效能, 因為它不再需要耗費資源來維護變更通知。 下表顯示其<xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Freezable.IsFrozen%2A>屬性設定為`true`時的簡單大小, 相較于不是時。 這會假設將一個筆刷<xref:System.Windows.Shapes.Shape.Fill%2A>套用至十<xref:System.Windows.Shapes.Rectangle>個物件的屬性。  
  
|**狀態**|**Size**|  
|---------------|--------------|  
|凍結<xref:System.Windows.Media.SolidColorBrush>|212 個位元組|  
|未凍結<xref:System.Windows.Media.SolidColorBrush>|972 個位元組|  
  
 下列程式碼範例說明此概念：  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>未凍結的 Freezable 上的已變更處理常式可能會保持物件運作  
 物件傳遞至<xref:System.Windows.Freezable> <xref:System.Windows.Freezable.Changed>物件事件的委派實際上是該物件的參考。 因此, <xref:System.Windows.Freezable.Changed>事件處理常式可以讓物件的運作時間超過預期。 執行已註冊要接聽<xref:System.Windows.Freezable> <xref:System.Windows.Freezable.Changed>物件事件之物件的清除時, 必須先移除該委派, 然後再釋放物件。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]也會在內部連結事件。<xref:System.Windows.Freezable.Changed> 例如, 做<xref:System.Windows.Freezable>為值的所有相依性屬性都會自動<xref:System.Windows.Freezable.Changed>接聽事件。 接受的<xref:System.Windows.Shapes.Shape.Fill%2A>屬性會<xref:System.Windows.Media.Brush>說明此概念。  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 `myBrush`在指派<xref:System.Windows.Freezable.Changed>給`myRectangle.Fill`時, 指向<xref:System.Windows.Shapes.Rectangle>物件的委派會加入至<xref:System.Windows.Media.SolidColorBrush>物件的事件。 這表示下列程式碼實際上不會讓 `myRect` 符合記憶體回收資格︰  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 在此情況`myBrush`下, 仍`myRectangle`會保持運作狀態, 並在引發<xref:System.Windows.Freezable.Changed>事件時回呼。 請注意, `myBrush`指派<xref:System.Windows.Shapes.Shape.Fill%2A>給新<xref:System.Windows.Shapes.Rectangle>的屬性只會將另一個事件處理常式`myBrush`加入至。  
  
 清除這些物件類型的建議方式是<xref:System.Windows.Media.Brush> <xref:System.Windows.Shapes.Shape.Fill%2A>從屬性中移除, 這<xref:System.Windows.Freezable.Changed>會接著移除事件處理常式。  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>使用者介面虛擬化  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]也提供可自動「虛擬<xref:System.Windows.Controls.StackPanel>化」資料系結子內容的元素變化。 在此內容中，「虛擬化」一字係指一種技術，藉由這種技術，將可從較大量的資料項目，根據畫面上可見的項目來產生物件子集。 當在指定的時間內畫面上只能有幾個 UI 項目時，不論是就記憶體還是處理器而言，產生大量 UI 項目都會相當耗費資源。 <xref:System.Windows.Controls.VirtualizingStackPanel>(透過提供<xref:System.Windows.Controls.VirtualizingPanel>的功能) 會計算可見專案, 並使用<xref:System.Windows.Controls.ItemContainerGenerator> <xref:System.Windows.Controls.ListBox>從<xref:System.Windows.Controls.ItemsControl> (例如或<xref:System.Windows.Controls.ListView>) 的來建立可見專案的元素。  
  
 作為效能最佳化，只有在這些項目的視覺物件顯示在螢幕上時才會產生或保持這些項目的視覺物件運作。 如果視覺物件不再位於控制項的可檢視區域中，可能會移除視覺物件。 這並不會與資料虛擬化混淆，在資料虛擬化中，資料物件不會全都在本機集合，而是視需要進行資料流處理。  
  
 下表顯示在<xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.StackPanel>和<xref:System.Windows.Controls.VirtualizingStackPanel>中加入和呈現5000元素的經過時間。 在此案例中, 測量代表將文字字串附加至<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ItemsControl>物件的屬性到面板元素顯示文字字串的時間之間的時間。  
  
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
