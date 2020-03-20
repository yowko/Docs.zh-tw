---
title: GridView 概觀
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 98bc7985172cabeab19469af4b4c21e13a6bce73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181893"
---
# <a name="gridview-overview"></a>GridView 概觀
<xref:System.Windows.Controls.GridView>視圖模式是控制項的視圖模式之一<xref:System.Windows.Controls.ListView>。 類<xref:System.Windows.Controls.GridView>及其支援類使您和您的使用者能夠在通常使用按鈕作為互動式列標題的表中查看項集合。 本主題介紹該<xref:System.Windows.Controls.GridView>類並概述其用途。  

<a name="DefiningaListViewthatusesGridViewView"></a>
## <a name="what-is-a-gridview-view"></a>什麼是 GridView 檢視？  
 視圖<xref:System.Windows.Controls.GridView>模式通過將資料欄位綁定到列以及顯示列標題來標識該欄位來顯示資料項目的清單。 預設<xref:System.Windows.Controls.GridView>樣式將按鈕作為列標題實現。 通過使用按鈕進行列標題，可以實現重要的使用者交互功能;例如，使用者可以按一下列標題根據特定列的內容對<xref:System.Windows.Controls.GridView>資料進行排序。  
  
> [!NOTE]
> <xref:System.Windows.Controls.GridView>用於列標題的按鈕控制項派生自<xref:System.Windows.Controls.Primitives.ButtonBase>。  
  
 下圖顯示了<xref:System.Windows.Controls.GridView>內容視圖<xref:System.Windows.Controls.ListView>。  

 ![顯示清單視圖內容的 GridView 視圖的螢幕截圖。](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>列由<xref:System.Windows.Controls.GridViewColumn>物件表示，物件可以自動調整其內容的大小。 或者，您可以顯式將 設置為<xref:System.Windows.Controls.GridViewColumn>特定寬度。 您可以藉由拖曳資料行標頭間的移駐夾來調整資料行大小。 您還可以動態添加、刪除、替換和重新排序列，因為此功能內置於<xref:System.Windows.Controls.GridView>中。 但是，<xref:System.Windows.Controls.GridView>無法直接更新它顯示的資料。  
  
 下面的示例演示如何定義顯示員工資料的<xref:System.Windows.Controls.GridView>。 在此示例中，<xref:System.Windows.Controls.ListView>將`EmployeeInfoDataSource`定義為 。 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>將內容綁定<xref:System.Windows.Controls.GridViewColumn>到`EmployeeInfoDataSource`資料類別的屬性定義。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 下圖顯示上一個範例所建立的表格。 GridView 控制項顯示來自專案源物件的資料：

 ![顯示帶有 GridView 輸出的 ListView 的螢幕截圖。](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>
## <a name="gridview-layout-and-style"></a>GridView 版面配置和樣式  
 的列儲存格和的列標題<xref:System.Windows.Controls.GridViewColumn>具有相同的寬度。 根據預設，每個資料行會依據其內容來調整其寬度。 您也可以選擇將資料行設定成固定寬度。  
  
 相關資料內容會顯示在水平資料列中。 例如，在上圖中，是將每個員工的姓氏、名字及識別碼都顯示成一組，因為它們是出現在水平資料列中。  
  
<a name="DefiningandStylingColumnsinaGridView"></a>
### <a name="defining-and-styling-columns-in-a-gridview"></a>定義及設定 GridView 中的資料行樣式  
 <xref:System.Windows.Controls.GridViewColumn>定義要在 中顯示的資料欄位時，請使用<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>。 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> 屬性<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>優先于任一範本屬性。  
  
 要指定 內容在 的列中的對齊方式<xref:System.Windows.Controls.GridView>，請定義<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>。 不要對使用<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>顯示<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A><xref:System.Windows.Controls.ListView>的內容使用 和 屬性<xref:System.Windows.Controls.GridView>。  
  
 要為列標題指定範本和樣式屬性，請使用<xref:System.Windows.Controls.GridView>和<xref:System.Windows.Controls.GridViewColumn><xref:System.Windows.Controls.GridViewColumnHeader>類。 如需詳細資訊，請參閱 [GridView 資料行標頭樣式和範本概觀](gridview-column-header-styles-and-templates-overview.md)。  
  
<a name="AddingVisualElementstoaGridViewView"></a>
### <a name="adding-visual-elements-to-a-gridview"></a>將視覺元素新增到 GridView  
 要將可視元素（如<xref:System.Windows.Controls.CheckBox>和<xref:System.Windows.Controls.Button>控制項）添加到<xref:System.Windows.Controls.GridView>視圖模式，請使用範本或樣式。  
  
 如果顯式將可視元素定義為數據項，則它只能在 中<xref:System.Windows.Controls.GridView>出現一次。 之所以會有這項限制，是因為一個元素只能有一個父代，因此在視覺化樹狀結構中只能出現一次。  
  
<a name="StylingRowsinaGridViewView"></a>
### <a name="styling-rows-in-a-gridview"></a>設定 GridView 中資料列的樣式  
 使用<xref:System.Windows.Controls.GridViewRowPresenter>和<xref:System.Windows.Controls.GridViewHeaderRowPresenter>類格式化和顯示 行<xref:System.Windows.Controls.GridView>。 有關如何在<xref:System.Windows.Controls.GridView>視圖模式下設置行樣式的示例，請參閱[實現 GridView 的 ListView 中對行的樣式](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md)。  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>使用 ItemContainerStyle 時的對齊問題  
 為了防止列標題和儲存格之間的對齊問題，請不要設置屬性或指定影響 中項寬度的範本<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>。 例如，不要設置<xref:System.Windows.FrameworkElement.Margin%2A>屬性或指定<xref:System.Windows.Controls.ControlTemplate>將 添加到<xref:System.Windows.Controls.CheckBox>控制項上<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A><xref:System.Windows.Controls.ListView>定義的 的 。 相反，請指定直接影響列寬度的屬性和範本，這些屬性和範本直接影響定義視圖<xref:System.Windows.Controls.GridView>模式的類。  
  
 例如，要<xref:System.Windows.Controls.CheckBox>向<xref:System.Windows.Controls.GridView>視圖模式下的行添加 ， 將 添加到<xref:System.Windows.Controls.CheckBox>，<xref:System.Windows.DataTemplate>然後將<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>屬性設置為 該<xref:System.Windows.DataTemplate>。  
  
<a name="InteractingwithaGridViewControl"></a>
## <a name="user-interactions-with-a-gridview"></a>使用者與 GridView 的互動  
 在應用程式中使用<xref:System.Windows.Controls.GridView>時，使用者可以與 進行交互並修改 的<xref:System.Windows.Controls.GridView>格式。 例如，使用者可以重新排列資料行、調整資料行大小、選取表格中的項目，以及捲動內容。 您也可以定義會在使用者按一下資料行標頭按鈕時回應的事件處理常式。 事件處理常式可以執行操作，例如<xref:System.Windows.Controls.GridView>根據列的內容對 中顯示的資料進行排序。  
  
 下面的清單更詳細地討論了用於<xref:System.Windows.Controls.GridView>使用者交互的功能：  
  
- **使用拖放方法來重新排列資料行。**  
  
     使用者可以在列標題上按滑鼠<xref:System.Windows.Controls.GridView>左鍵重新排序，然後將該列拖動到新位置。 當使用者拖曳資料行標頭時，除了會顯示一條指出資料行插入位置的實心黑線之外，也會顯示該標頭的浮動版本。  
  
     如果要修改標頭的浮動版本的預設樣式，<xref:System.Windows.Controls.ControlTemplate>請為在<xref:System.Windows.Controls.GridViewColumnHeader><xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>屬性設置為<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>時觸發的類型指定 。 如需詳細資訊，請參閱[為已拖曳的 GridView 資料行標頭建立樣式](how-to-create-a-style-for-a-dragged-gridview-column-header.md)。  
  
- **依資料行內容調整資料行大小。**  
  
     使用者可以按兩下資料行標頭右邊的移駐夾，來依資料行內容調整資料行大小。  
  
    > [!NOTE]
    > 您可以將 該<xref:System.Windows.Controls.GridViewColumn.Width%2A>屬性設置為`Double.NaN`以生成相同的效果。  
  
- **選取資料列項目。**  
  
     使用者可以在 中選擇 一<xref:System.Windows.Controls.GridView>個或多個專案。  
  
     如果要更改<xref:System.Windows.Style>所選項目的 ，請參閱[在 ListView 中使用觸發器來設置所選項目。](how-to-use-triggers-to-style-selected-items-in-a-listview.md)  
  
- **捲動以檢視一開始在畫面上看不到的內容。**  
  
     如果 的大小<xref:System.Windows.Controls.GridView>不足以顯示所有專案，則使用者可以使用<xref:System.Windows.Controls.ScrollViewer>控制項提供的捲軸水準或垂直捲動。 如果<xref:System.Windows.Controls.Primitives.ScrollBar>所有內容在特定方向上可見，則隱藏 。 資料行標頭不會以垂直捲軸捲動，但是會以水平方式捲動。  
  
- **按一下資料行標頭按鈕來與資料行進行互動。**  
  
     如果您已提供排序演算法，則當使用者按一下資料行標頭按鈕時，將可排序該資料行中顯示的資料。  
  
     您可以處理列標題<xref:System.Windows.Controls.Primitives.ButtonBase.Click>按鈕的事件，以便提供排序演算法等功能。 要處理單個<xref:System.Windows.Controls.Primitives.ButtonBase.Click>列標頭的事件，在 上設置事件處理常式<xref:System.Windows.Controls.GridViewColumnHeader>。 要設置處理所有列標題<xref:System.Windows.Controls.Primitives.ButtonBase.Click>的事件處理常式，在<xref:System.Windows.Controls.ListView>控制項上設置處理常式。  
  
<a name="Obtaining_Other_Custom_Views"></a>
## <a name="obtaining-other-custom-views"></a>取得其他自訂檢視  
 從<xref:System.Windows.Controls.GridView>抽象類別派生的<xref:System.Windows.Controls.ViewBase>類只是<xref:System.Windows.Controls.ListView>類的可能視圖模式之一。 可以通過從<xref:System.Windows.Controls.ListView><xref:System.Windows.Controls.ViewBase>類派生來創建其他自訂視圖。 如需自訂檢視模式的範例，請參閱[建立 ListView 的自訂檢視模式](how-to-create-a-custom-view-mode-for-a-listview.md)。  
  
<a name="GridViewSupportingClasses"></a>
## <a name="gridview-supporting-classes"></a>支援 GridView 的類別  
 以下類支援<xref:System.Windows.Controls.GridView>視圖模式。  
  
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
- [如何使用主題](listview-how-to-topics.md)
