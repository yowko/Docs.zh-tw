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
ms.openlocfilehash: 67184db7fc1459e83ac7b1e6ff09ef56e43f0ca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187081"
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
 通常，訪問 的依賴<xref:System.Windows.DependencyObject>項屬性不會比訪問 CLR 屬性慢。 雖然設置屬性值的性能開銷很小，但獲取值的速度與從 CLR 屬性獲取值的速度一樣快。 小小效能負荷的補償是相依性屬性可支援強大的功能，例如資料繫結、動畫、繼承和樣式。 如需詳細資訊，請參閱[相依性屬性概觀](dependency-properties-overview.md)。  
  
### <a name="dependencyproperty-optimizations"></a>DependencyProperty 最佳化  
 您應該在應用程式中非常小心地定義相依性屬性。 如果<xref:System.Windows.DependencyProperty>影響僅影響呈現類型中繼資料選項，而不是其他中繼資料選項（如<xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>），則應通過重寫其中繼資料來標記它。 如需覆寫或取得屬性中繼資料的詳細資訊，請參閱[相依性屬性中繼資料](dependency-property-metadata.md)。  
  
 如果並非所有屬性變更都會實際上影響測量、排列與轉譯，手動讓屬性變更處理常式使測量、排列與轉譯階段失效，可能會更有效率。 比方說，您可能決定只有在值大於設定的限制時，才重新轉譯背景。 在此情況下，您的屬性變更處理常式只會在值超過設定的限制時使轉譯器失效。  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>使 DependencyProperty 成為可繼承不是免費的  
 根據預設，已註冊的相依性屬性是不可繼承的。 不過，您可以明確地使任何屬性成為可繼承。 雖然這是很有用的功能，但將屬性轉換為可繼承會影響效能，因為會增加屬性失效的時間長度。  
  
### <a name="use-registerclasshandler-carefully"></a>小心使用 RegisterClassHandler  
 雖然調用<xref:System.Windows.EventManager.RegisterClassHandler%2A>允許您保存實例狀態，但請務必注意每個實例上都調用處理程式，這可能會導致性能問題。 僅當應用程式<xref:System.Windows.EventManager.RegisterClassHandler%2A>要求您保存實例狀態時才使用。  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>在註冊期間設定 DependencyProperty 的預設值  
 創建需要預設值<xref:System.Windows.DependencyProperty>的 創建 時，請使用作為參數<xref:System.Windows.DependencyProperty.Register%2A>傳遞給 的<xref:System.Windows.DependencyProperty>預設中繼資料設置值。 使用這項技術，而不是在建構函式或項目的每個執行個體上設定屬性值。  
  
### <a name="set-the-propertymetadata-value-using-register"></a>使用 Register 設定 PropertyMetadata 值  
 創建 時<xref:System.Windows.DependencyProperty>，可以選擇<xref:System.Windows.PropertyMetadata>使用<xref:System.Windows.DependencyProperty.Register%2A>或<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>方法設置 。 儘管物件可能有一個靜態建構函式要調用<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>，但這不是最佳解決方案，會影響性能。 為獲得最佳性能，請在<xref:System.Windows.PropertyMetadata>調用 期間設置為<xref:System.Windows.DependencyProperty.Register%2A>。  
  
<a name="Freezable_Objects"></a>
## <a name="freezable-objects"></a>Freezable 物件  
 A<xref:System.Windows.Freezable>是具有特殊類型的物件，具有兩種狀態：解凍和凍結。 盡可能凍結物件可以提升應用程式的效能，並縮減其工作集。 如需詳細資訊，請參閱 [Freezable 物件概觀](freezable-objects-overview.md)。  
  
 每個<xref:System.Windows.Freezable>都有一<xref:System.Windows.Freezable.Changed>個事件，每當它發生更改時都會引發該事件。 不過，變更通知會嚴重降低應用程式效能。  
  
 請考慮以下示例，其中每個物件<xref:System.Windows.Shapes.Rectangle>使用相同的<xref:System.Windows.Media.Brush>物件：  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]預設情況下，為<xref:System.Windows.Media.SolidColorBrush>物件<xref:System.Windows.Freezable.Changed>的事件提供事件處理常式，以使<xref:System.Windows.Shapes.Rectangle>物件<xref:System.Windows.Shapes.Shape.Fill%2A>的屬性無效。 在這種情況下，每次<xref:System.Windows.Media.SolidColorBrush>必須觸發其<xref:System.Windows.Freezable.Changed>事件時，都需要為每個事件<xref:System.Windows.Shapes.Rectangle>調用回呼函數 — 這些回呼函數調用的累積會帶來巨大的性能損失。 此外，在此時新增和移除處理常式會相當耗損效能，因為應用程式必須周遊整個清單才能執行這項操作。 如果應用程式方案從未更改 ，<xref:System.Windows.Media.SolidColorBrush>則不必要地需要支付維護<xref:System.Windows.Freezable.Changed>事件處理常式的成本。  
  
 凍結可以<xref:System.Windows.Freezable>提高其性能，因為它不再需要將資源用於維護更改通知。 下表顯示了簡單<xref:System.Windows.Media.SolidColorBrush><xref:System.Windows.Freezable.IsFrozen%2A>屬性設置為`true`時的大小，而不是設置為 時的大小。 這假定將一個畫筆應用於<xref:System.Windows.Shapes.Shape.Fill%2A>十<xref:System.Windows.Shapes.Rectangle>個物件的屬性。  
  
|**狀態**|**大小**|  
|---------------|--------------|  
|冷凍<xref:System.Windows.Media.SolidColorBrush>|212 個位元組|  
|非凍結<xref:System.Windows.Media.SolidColorBrush>|972 個位元組|  
  
 下列程式碼範例說明此概念：  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>未凍結的 Freezable 上的已變更處理常式可能會保持物件運作  
 物件傳遞給<xref:System.Windows.Freezable>物件<xref:System.Windows.Freezable.Changed>事件的委託實際上是對該物件的引用。 因此，<xref:System.Windows.Freezable.Changed>事件處理常式可以使物件保持比預期的時間更長。 執行已註冊以偵聽<xref:System.Windows.Freezable>物件<xref:System.Windows.Freezable.Changed>事件的物件的清理時，在釋放該物件之前必須刪除該委託。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]也連接<xref:System.Windows.Freezable.Changed>內部的事件。 例如，所有作為<xref:System.Windows.Freezable>值的依賴項屬性將自動偵聽<xref:System.Windows.Freezable.Changed>事件。 屬性<xref:System.Windows.Shapes.Shape.Fill%2A>（採用 ）<xref:System.Windows.Media.Brush>說明了這個概念。  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 在`myBrush`分配`myRectangle.Fill`時，<xref:System.Windows.Shapes.Rectangle>指向物件的委託將添加到<xref:System.Windows.Media.SolidColorBrush>物件的<xref:System.Windows.Freezable.Changed>事件。 這表示下列程式碼實際上不會讓 `myRect` 符合記憶體回收資格︰  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 在這種情況下`myBrush`，仍然保持`myRectangle`活動狀態，並在觸發事件<xref:System.Windows.Freezable.Changed>時將其回電。 `myBrush`請注意，<xref:System.Windows.Shapes.Shape.Fill%2A>分配給 new<xref:System.Windows.Shapes.Rectangle>的屬性只會向`myBrush`添加另一個事件處理常式。  
  
 清除這些類型的物件的推薦方法是從<xref:System.Windows.Media.Brush><xref:System.Windows.Shapes.Shape.Fill%2A>屬性中刪除 ，這反過來將刪除<xref:System.Windows.Freezable.Changed>事件處理常式。  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>
## <a name="user-interface-virtualization"></a>使用者介面虛擬化  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]還提供了自動"虛擬化"<xref:System.Windows.Controls.StackPanel>資料繫結子內容的元素的變體。 在此內容中，「虛擬化」一字係指一種技術，藉由這種技術，將可從較大量的資料項目，根據畫面上可見的項目來產生物件子集。 當在指定的時間內畫面上只能有幾個 UI 項目時，不論是就記憶體還是處理器而言，產生大量 UI 項目都會相當耗費資源。 <xref:System.Windows.Controls.VirtualizingStackPanel>（通過<xref:System.Windows.Controls.VirtualizingPanel>提供的功能計算可見項，並與<xref:System.Windows.Controls.ItemContainerGenerator>從<xref:System.Windows.Controls.ItemsControl>（如<xref:System.Windows.Controls.ListBox>）<xref:System.Windows.Controls.ListView>到僅為可見項創建元素。  
  
 作為效能最佳化，只有在這些項目的視覺物件顯示在螢幕上時才會產生或保持這些項目的視覺物件運作。 如果視覺物件不再位於控制項的可檢視區域中，可能會移除視覺物件。 這並不會與資料虛擬化混淆，在資料虛擬化中，資料物件不會全都在本機集合，而是視需要進行資料流處理。  
  
 下表顯示了向 和<xref:System.Windows.Controls.TextBlock><xref:System.Windows.Controls.StackPanel>添加和渲染 5000 個元素的<xref:System.Windows.Controls.VirtualizingStackPanel>經過時間。 在這種情況下，度量值表示將文本字串附加到<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A><xref:System.Windows.Controls.ItemsControl>物件屬性到面板元素顯示文本字串的時間之間的時間。  
  
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
- [文本](optimizing-performance-text.md)
- [資料繫結](optimizing-performance-data-binding.md)
- [其他效能建議](optimizing-performance-other-recommendations.md)
