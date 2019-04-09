---
title: GridView 概觀
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: d2f55db90fb130416ee4dcb15d440b6d367c0b06
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201295"
---
# <a name="gridview-overview"></a>GridView 概觀
<xref:System.Windows.Controls.GridView> 檢視模式是一種檢視模式的<xref:System.Windows.Controls.ListView>控制項。 <xref:System.Windows.Controls.GridView>類別和其支援的類別讓您和您的使用者可以檢視通常使用按鈕作為互動式資料行標頭的資料表中的集合項目。 本主題將介紹<xref:System.Windows.Controls.GridView>類別並概述其用法。  

<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>什麼是 GridView 檢視？  
 <xref:System.Windows.Controls.GridView>模式會顯示一份資料的項目所繫結至資料行的資料欄位，並顯示資料行標頭來識別欄位的檢視。 預設值<xref:System.Windows.Controls.GridView>樣式會將作為資料行標頭按鈕。 藉由使用資料行標頭按鈕，您可以實作重要的使用者互動功能;例如，使用者可以按一下資料行標頭來排序<xref:System.Windows.Controls.GridView>根據特定的資料行的內容資料。  
  
> [!NOTE]
>  按鈕控制項<xref:System.Windows.Controls.GridView>資料行標頭的用途衍生自<xref:System.Windows.Controls.Primitives.ButtonBase>。  
  
 如下圖所示<xref:System.Windows.Controls.GridView>檢視的<xref:System.Windows.Controls.ListView>內容。  
    
 ![如果螢幕擷取畫面顯示 ListView 內容的 GridView 檢視。](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView> 資料行都由<xref:System.Windows.Controls.GridViewColumn>其內容可以自動調整大小的物件。 （選擇性） 您可以明確設定<xref:System.Windows.Controls.GridViewColumn>為特定寬度。 您可以藉由拖曳資料行標頭間的移駐夾來調整資料行大小。 您可以也會動態地新增、 移除、 取代和重新排列資料行，因為這項功能內建在<xref:System.Windows.Controls.GridView>。 不過，<xref:System.Windows.Controls.GridView>無法直接更新它所顯示的資料。  
  
 下列範例示範如何定義<xref:System.Windows.Controls.GridView>顯示員工資料。 在此範例中，<xref:System.Windows.Controls.ListView>定義`EmployeeInfoDataSource`做為<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。 屬性定義<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>繫結<xref:System.Windows.Controls.GridViewColumn>內容`EmployeeInfoDataSource`資料類別。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 下圖顯示上一個範例所建立的表格。 GridView 控制項中，會顯示來自 ItemsSource 物件的資料：
    
 ![螢幕擷取畫面，顯示 ListView 與 GridView 輸出。](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>GridView 版面配置和樣式  
 資料行儲存格和資料行標頭<xref:System.Windows.Controls.GridViewColumn>具有相同寬度。 根據預設，每個資料行會依據其內容來調整其寬度。 您也可以選擇將資料行設定成固定寬度。  
  
 相關資料內容會顯示在水平資料列中。 例如，在上圖中，是將每個員工的姓氏、名字及識別碼都顯示成一組，因為它們是出現在水平資料列中。  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>定義及設定 GridView 中的資料行樣式  
 定義要顯示的資料欄位時<xref:System.Windows.Controls.GridViewColumn>，使用<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>， <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>，或<xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A>屬性。 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性會優先於其中一個範本內容。  
  
 若要指定的資料行中的內容的對齊<xref:System.Windows.Controls.GridView>，定義<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>。 請勿使用<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>並<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>屬性<xref:System.Windows.Controls.ListView>會顯示所使用的內容<xref:System.Windows.Controls.GridView>。  
  
 若要指定資料行行首的範本和樣式屬性，請使用<xref:System.Windows.Controls.GridView>， <xref:System.Windows.Controls.GridViewColumn>，和<xref:System.Windows.Controls.GridViewColumnHeader>類別。 如需詳細資訊，請參閱 [GridView 資料行標頭樣式和範本概觀](gridview-column-header-styles-and-templates-overview.md)。  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>將視覺元素新增到 GridView  
 若要將視覺元素，例如<xref:System.Windows.Controls.CheckBox>並<xref:System.Windows.Controls.Button>控制項，為<xref:System.Windows.Controls.GridView>檢視模式中，使用範本或樣式。  
  
 如果您明確定義視覺項目，做為資料的項目，它可以出現一次只能在<xref:System.Windows.Controls.GridView>。 之所以會有這項限制，是因為一個元素只能有一個父代，因此在視覺化樹狀結構中只能出現一次。  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>設定 GridView 中資料列的樣式  
 使用<xref:System.Windows.Controls.GridViewRowPresenter>並<xref:System.Windows.Controls.GridViewHeaderRowPresenter>類別來格式化和顯示的資料列<xref:System.Windows.Controls.GridView>。 如需如何的樣式中的資料列的範例<xref:System.Windows.Controls.GridView>檢視模式，請參閱[資料列的樣式的 ListView，實作 GridView](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md)。  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>使用 ItemContainerStyle 時的對齊問題  
 若要防止資料行標頭之間的資料格的對齊問題，請勿設定屬性或指定會影響該寬度的中的項目範本<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>。 例如，未設定<xref:System.Windows.FrameworkElement.Margin%2A>屬性，或指定<xref:System.Windows.Controls.ControlTemplate>，將加上<xref:System.Windows.Controls.CheckBox>來<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>上所定義之<xref:System.Windows.Controls.ListView>控制項。 相反地，指定的屬性和會影響直接在定義的類別上的資料行寬度的範本<xref:System.Windows.Controls.GridView>檢視模式。  
  
 例如，若要新增<xref:System.Windows.Controls.CheckBox>中的資料列<xref:System.Windows.Controls.GridView>檢視模式中，新增<xref:System.Windows.Controls.CheckBox>來<xref:System.Windows.DataTemplate>，然後將<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>屬性所<xref:System.Windows.DataTemplate>。  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>使用者與 GridView 的互動  
 當您使用<xref:System.Windows.Controls.GridView>在您的應用程式，使用者可以互動，並修改其格式設定<xref:System.Windows.Controls.GridView>。 例如，使用者可以重新排列資料行、調整資料行大小、選取表格中的項目，以及捲動內容。 您也可以定義會在使用者按一下資料行標頭按鈕時回應的事件處理常式。 事件處理常式可以執行作業，例如排序的資料，會顯示在<xref:System.Windows.Controls.GridView>根據資料行的內容。  
  
 下列清單的討論將更詳細的功能使用<xref:System.Windows.Controls.GridView>與使用者互動：  
  
-   **使用拖放方法，重新排列資料行。**  
  
     使用者可以重新排列資料行中的<xref:System.Windows.Controls.GridView>資料行標頭上方時，請按下滑鼠左的按鈕，然後再將該資料行拖曳到新位置。 當使用者拖曳資料行標頭時，除了會顯示一條指出資料行插入位置的實心黑線之外，也會顯示該標頭的浮動版本。  
  
     如果您想要修改標頭的浮動版本的預設樣式，指定<xref:System.Windows.Controls.ControlTemplate>for<xref:System.Windows.Controls.GridViewColumnHeader>類型，它是時觸發<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>屬性設定為<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>。 如需詳細資訊，請參閱[為已拖曳的 GridView 資料行標頭建立樣式](how-to-create-a-style-for-a-dragged-gridview-column-header.md)。  
  
-   **調整大小的資料行，其內容。**  
  
     使用者可以按兩下資料行標頭右邊的移駐夾，來依資料行內容調整資料行大小。  
  
    > [!NOTE]
    >  您可以設定<xref:System.Windows.Controls.GridViewColumn.Width%2A>屬性設`Double.NaN`產生相同的效果。  
  
-   **選取的資料列的項目。**  
  
     使用者可以選取一或多個項目中的<xref:System.Windows.Controls.GridView>。  
  
     如果您想要變更<xref:System.Windows.Style>的 選取的項目，請參閱[樣式的 ListView 中的選取項目使用之觸發程序](how-to-use-triggers-to-style-selected-items-in-a-listview.md)。  
  
-   **捲動到檢視一開始在螢幕上看不到的內容。**  
  
     如果大小<xref:System.Windows.Controls.GridView>不是大到足以顯示所有項目，使用者可以捲動水平或垂直藉由使用捲軸，這由提供<xref:System.Windows.Controls.ScrollViewer>控制項。 A<xref:System.Windows.Controls.Primitives.ScrollBar>會隱藏如果所有內容都會顯示在特定的方向。 資料行標頭不會以垂直捲軸捲動，但是會以水平方式捲動。  
  
-   **按一下資料行標頭按鈕互動的資料行。**  
  
     如果您已提供排序演算法，則當使用者按一下資料行標頭按鈕時，將可排序該資料行中顯示的資料。  
  
     您可以處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件資料行標頭按鈕，以提供排序演算法之類的功能。 若要處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>的單一資料行標頭中，事件上設定的事件處理常式<xref:System.Windows.Controls.GridViewColumnHeader>。 若要設定處理的事件處理常式<xref:System.Windows.Controls.Primitives.ButtonBase.Click>用於所有的資料行標頭，事件上設定的處理常式<xref:System.Windows.Controls.ListView>控制項。  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>取得其他自訂檢視  
 <xref:System.Windows.Controls.GridView>類別，衍生自<xref:System.Windows.Controls.ViewBase>抽象類別，只是其中一個可能檢視模式的<xref:System.Windows.Controls.ListView>類別。 您可以建立其他自訂檢視<xref:System.Windows.Controls.ListView>藉由衍生自<xref:System.Windows.Controls.ViewBase>類別。 如需自訂檢視模式的範例，請參閱[建立 ListView 的自訂檢視模式](how-to-create-a-custom-view-mode-for-a-listview.md)。  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>支援 GridView 的類別  
 下列類別會支援<xref:System.Windows.Controls.GridView>檢視模式。  
  
-   <xref:System.Windows.Controls.GridViewColumn>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GridViewRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewColumnCollection>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
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
- [HOW TO 主題](listview-how-to-topics.md)
