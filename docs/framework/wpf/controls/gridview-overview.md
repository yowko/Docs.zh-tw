---
title: GridView 概觀
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 6da556296679de1161f609a7731c6fbf14e94730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966475"
---
# <a name="gridview-overview"></a>GridView 概觀
<xref:System.Windows.Controls.GridView>view 模式是<xref:System.Windows.Controls.ListView>控制項的其中一個視圖模式。 <xref:System.Windows.Controls.GridView>類別及其支援的類別可讓您和您的使用者在通常使用按鈕做為互動式資料行標頭的資料表中, 查看專案集合。 本主題介紹<xref:System.Windows.Controls.GridView>類別並概述其用法。  

<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>什麼是 GridView 檢視？  
 <xref:System.Windows.Controls.GridView> View 模式會藉由將資料欄位系結至資料行, 以及藉由顯示欄標題來識別欄位, 來顯示資料項目清單。 預設<xref:System.Windows.Controls.GridView>樣式會將按鈕實作為資料行標題。 藉由使用資料行標頭的按鈕, 您可以執行重要的使用者互動功能;例如, 使用者可以按一下資料行標頭, 根據特定<xref:System.Windows.Controls.GridView>資料行的內容來排序資料。  
  
> [!NOTE]
> 資料行標頭所<xref:System.Windows.Controls.GridView>使用的按鈕控制項衍生自。 <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
 下圖顯示<xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView>內容的觀點。  
    
 ![顯示 ListView 內容之 GridView 視圖的螢幕擷取畫面。](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>資料行是以<xref:System.Windows.Controls.GridViewColumn>物件表示, 可以自動調整為其內容。 (選擇性) 您可以明確地<xref:System.Windows.Controls.GridViewColumn>將設為特定寬度。 您可以藉由拖曳資料行標頭間的移駐夾來調整資料行大小。 您也可以動態加入、移除、取代和重新排列資料行, 因為這是內<xref:System.Windows.Controls.GridView>建的功能。 不過, <xref:System.Windows.Controls.GridView>無法直接更新它所顯示的資料。  
  
 下列範例示範如何定義<xref:System.Windows.Controls.GridView>會顯示員工資料的。 在此範例中<xref:System.Windows.Controls.ListView> , 會`EmployeeInfoDataSource`將定義<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>為。 將<xref:System.Windows.Controls.GridViewColumn>內容系結<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>至`EmployeeInfoDataSource`資料類別目錄的屬性定義。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 下圖顯示上一個範例所建立的表格。 GridView 控制項會顯示來自 ItemsSource 物件的資料:
    
 ![顯示具有 GridView 輸出之 ListView 的螢幕擷取畫面。](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>GridView 版面配置和樣式  
 資料行儲存格和的欄標題<xref:System.Windows.Controls.GridViewColumn>具有相同的寬度。 根據預設，每個資料行會依據其內容來調整其寬度。 您也可以選擇將資料行設定成固定寬度。  
  
 相關資料內容會顯示在水平資料列中。 例如，在上圖中，是將每個員工的姓氏、名字及識別碼都顯示成一組，因為它們是出現在水平資料列中。  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>定義及設定 GridView 中的資料行樣式  
 定義<xref:System.Windows.Controls.GridViewColumn>要顯示在中的資料欄位時, 請<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>使用、 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>或<xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A>屬性。 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性優先于範本屬性的其中一個。  
  
 若要指定資料行<xref:System.Windows.Controls.GridView>中內容的對齊方式, 請<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>定義。 請<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>不要針對<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> 使用<xref:System.Windows.Controls.ListView> 所顯示的內容<xref:System.Windows.Controls.GridView>使用和屬性。  
  
 若要指定資料行標頭的範本和樣式屬性, <xref:System.Windows.Controls.GridView>請<xref:System.Windows.Controls.GridViewColumn>使用、 <xref:System.Windows.Controls.GridViewColumnHeader>和類別。 如需詳細資訊，請參閱 [GridView 資料行標頭樣式和範本概觀](gridview-column-header-styles-and-templates-overview.md)。  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>將視覺元素新增到 GridView  
 若要將視覺元素 (例如<xref:System.Windows.Controls.CheckBox>和<xref:System.Windows.Controls.Button>控制項) 加入至<xref:System.Windows.Controls.GridView>視圖模式, 請使用範本或樣式。  
  
 如果您將視覺專案明確定義為數據項, 則在中<xref:System.Windows.Controls.GridView>只能出現一次。 之所以會有這項限制，是因為一個元素只能有一個父代，因此在視覺化樹狀結構中只能出現一次。  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>設定 GridView 中資料列的樣式  
 <xref:System.Windows.Controls.GridViewRowPresenter>使用和<xref:System.Windows.Controls.GridViewHeaderRowPresenter>類別來格式化和<xref:System.Windows.Controls.GridView>顯示的資料列。 如需如何在<xref:System.Windows.Controls.GridView>視圖模式中建立資料列樣式的範例, 請參閱[在執行 GridView 的 ListView 中建立資料列的樣式](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md)。  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>使用 ItemContainerStyle 時的對齊問題  
 若要防止資料行標頭和資料格之間的對齊問題, 請勿設定屬性或指定會影響中<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>專案寬度的範本。 例如, <xref:System.Windows.FrameworkElement.Margin%2A>請勿設定屬性, 或<xref:System.Windows.Controls.ControlTemplate>指定將加入<xref:System.Windows.Controls.CheckBox>至<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListView>控制項定義之的。 相反地, 請在定義<xref:System.Windows.Controls.GridView>視圖模式的類別上, 直接指定會影響資料行寬度的屬性和範本。  
  
 例如, 若要將加入<xref:System.Windows.Controls.CheckBox>至<xref:System.Windows.Controls.CheckBox> view 模式中<xref:System.Windows.Controls.GridView>的資料列<xref:System.Windows.DataTemplate>, 請將新增至, 然後將<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>屬性設定為該<xref:System.Windows.DataTemplate>。  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>使用者與 GridView 的互動  
 當您<xref:System.Windows.Controls.GridView>在應用程式中使用時, 使用者可以與進行互動及修改的格式<xref:System.Windows.Controls.GridView>。 例如，使用者可以重新排列資料行、調整資料行大小、選取表格中的項目，以及捲動內容。 您也可以定義會在使用者按一下資料行標頭按鈕時回應的事件處理常式。 事件處理常式可以執行作業, 例如<xref:System.Windows.Controls.GridView>根據資料行的內容來排序顯示在中的資料。  
  
 下列清單更詳細地討論使用<xref:System.Windows.Controls.GridView>進行使用者互動的功能:  
  
- **使用拖放方法來重新排列資料行。**  
  
     當使用者在資料行標頭<xref:System.Windows.Controls.GridView>上按下滑鼠左鍵, 然後將資料行拖曳至新位置時, 可以在中重新排列資料行。 當使用者拖曳資料行標頭時，除了會顯示一條指出資料行插入位置的實心黑線之外，也會顯示該標頭的浮動版本。  
  
     如果您想要修改標頭浮動版本的<xref:System.Windows.Controls.ControlTemplate>預設樣式, 請<xref:System.Windows.Controls.GridViewColumnHeader>針對當<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>屬性設定為<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>時所觸發的類型, 指定。 如需詳細資訊，請參閱[為已拖曳的 GridView 資料行標頭建立樣式](how-to-create-a-style-for-a-dragged-gridview-column-header.md)。  
  
- **依資料行內容調整資料行大小。**  
  
     使用者可以按兩下資料行標頭右邊的移駐夾，來依資料行內容調整資料行大小。  
  
    > [!NOTE]
    > 您可以將<xref:System.Windows.Controls.GridViewColumn.Width%2A>屬性設定為`Double.NaN` , 以產生相同的效果。  
  
- **選取資料列項目。**  
  
     使用者可以在中<xref:System.Windows.Controls.GridView>選取一個或多個專案。  
  
     如果您想要變更<xref:System.Windows.Style>所選項目的, 請參閱[使用觸發程式來為 ListView 中選取的專案建立樣式](how-to-use-triggers-to-style-selected-items-in-a-listview.md)。  
  
- **捲動以檢視一開始在畫面上看不到的內容。**  
  
     如果的大小<xref:System.Windows.Controls.GridView>不夠大而無法顯示所有專案, 使用者可以使用<xref:System.Windows.Controls.ScrollViewer>控制項提供的捲軸, 以水準或垂直方式滾動。 如果所有內容都是以特定方向顯示,則會隱藏。<xref:System.Windows.Controls.Primitives.ScrollBar> 資料行標頭不會以垂直捲軸捲動，但是會以水平方式捲動。  
  
- **按一下資料行標頭按鈕來與資料行進行互動。**  
  
     如果您已提供排序演算法，則當使用者按一下資料行標頭按鈕時，將可排序該資料行中顯示的資料。  
  
     您可以處理資料<xref:System.Windows.Controls.Primitives.ButtonBase.Click>行標頭按鈕的事件, 以便提供排序演算法之類的功能。 若要處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>單一資料行標頭的事件, 請<xref:System.Windows.Controls.GridViewColumnHeader>在上設定事件處理常式。 若要設定處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>所有資料行標頭之事件的事件處理常式, 請<xref:System.Windows.Controls.ListView>在控制項上設定處理常式。  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>取得其他自訂檢視  
 衍生自抽象類別的<xref:System.Windows.Controls.ListView> 類別,只是類別的其中一個可能的視圖模式。<xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ViewBase> 您可以<xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ViewBase>從類別衍生, 以建立的其他自訂視圖。 如需自訂檢視模式的範例，請參閱[建立 ListView 的自訂檢視模式](how-to-create-a-custom-view-mode-for-a-listview.md)。  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>支援 GridView 的類別  
 下列類別支援<xref:System.Windows.Controls.GridView> view 模式。  
  
- <xref:System.Windows.Controls.GridViewColumn>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GridViewRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewColumnCollection>  
  
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Controls.GridViewColumn>
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.ViewBase>
- [ListView 概觀](listview-overview.md)
- [在按一下標頭時排序 GridView 資料行](how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [HOW-TO 主題](listview-how-to-topics.md)
