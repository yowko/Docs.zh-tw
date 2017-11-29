---
title: "GridView 概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 44574b5737873371f9a7bc9be2d851a8ae1e101b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="gridview-overview"></a>GridView 概觀
<xref:System.Windows.Controls.GridView>檢視模式是一種檢視模式的<xref:System.Windows.Controls.ListView>控制項。 <xref:System.Windows.Controls.GridView>類別和其支援的類別可讓您和您的使用者通常使用按鈕為互動式的資料行標頭的資料表中檢視項目集合。 本主題將介紹<xref:System.Windows.Controls.GridView>類別，並且摘要說明其用途。  
  
  
  
<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>什麼是 GridView 檢視？  
 <xref:System.Windows.Controls.GridView>檢視模式顯示項目清單，由繫結至資料行的資料欄位和顯示資料行標頭，識別欄位。 預設值<xref:System.Windows.Controls.GridView>樣式實作作為資料行標頭的按鈕。 藉由使用資料行標頭的按鈕，您可以實作重要的使用者互動功能。例如，使用者可以按一下資料行標頭來排序<xref:System.Windows.Controls.GridView>根據特定資料行的內容資料。  
  
> [!NOTE]
>  按鈕控制項<xref:System.Windows.Controls.GridView>資料行標頭的用法衍生自<xref:System.Windows.Controls.Primitives.ButtonBase>。  
  
 下圖顯示<xref:System.Windows.Controls.GridView>檢視<xref:System.Windows.Controls.ListView>內容。  
  
 **ListView 內容的 GridView 檢視**  
  
 ![已設定樣式的 ListView](../../../../docs/framework/wpf/controls/media/styledlistview.PNG "StyledListView")  
  
 <xref:System.Windows.Controls.GridView>資料行都由<xref:System.Windows.Controls.GridViewColumn>物件，其內容可以自動調整大小。 （選擇性） 您可以明確設定<xref:System.Windows.Controls.GridViewColumn>寬度。 您可以藉由拖曳資料行標頭間的移駐夾來調整資料行大小。 您可以也會動態地新增、 移除、 取代和重新排列資料行，因為這項功能已內建在<xref:System.Windows.Controls.GridView>。 不過，<xref:System.Windows.Controls.GridView>無法直接更新它所顯示的資料。  
  
 下列範例示範如何定義<xref:System.Windows.Controls.GridView>，會顯示員工資料。 在此範例中，<xref:System.Windows.Controls.ListView>定義`EmployeeInfoDataSource`為<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。 屬性定義的<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>繫結<xref:System.Windows.Controls.GridViewColumn>內容`EmployeeInfoDataSource`資料類別。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 下圖顯示上一個範例所建立的表格。  
  
 **顯示來自 ItemsSource 之資料的 GridView**  
  
 ![含有 GridView 輸出的 ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>GridView 版面配置和樣式  
 資料行儲存格和資料行標頭的<xref:System.Windows.Controls.GridViewColumn>具有相同寬度。 根據預設，每個資料行會依據其內容來調整其寬度。 您也可以選擇將資料行設定成固定寬度。  
  
 相關資料內容會顯示在水平資料列中。 例如，在上圖中，是將每個員工的姓氏、名字及識別碼都顯示成一組，因為它們是出現在水平資料列中。  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>定義及設定 GridView 中的資料行樣式  
 定義要顯示的資料欄位時<xref:System.Windows.Controls.GridViewColumn>，使用<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>， <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>，或<xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A>屬性。 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性會優先於其中一個範本內容。  
  
 若要指定內容的對齊方式的資料行中<xref:System.Windows.Controls.GridView>，定義<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>。 請勿使用<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>和<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>屬性<xref:System.Windows.Controls.ListView>使用所顯示的內容<xref:System.Windows.Controls.GridView>。  
  
 若要指定資料行標頭的範本和樣式屬性，請使用<xref:System.Windows.Controls.GridView>， <xref:System.Windows.Controls.GridViewColumn>，和<xref:System.Windows.Controls.GridViewColumnHeader>類別。 如需詳細資訊，請參閱 [GridView 資料行標頭樣式和範本概觀](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)。  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>將視覺元素新增到 GridView  
 若要加入視覺項目，例如<xref:System.Windows.Controls.CheckBox>和<xref:System.Windows.Controls.Button>控制項，為<xref:System.Windows.Controls.GridView>檢視模式，請使用範本或樣式。  
  
 如果您明確地定義視覺項目，做為資料項目，它可以出現一次只能在<xref:System.Windows.Controls.GridView>。 之所以會有這項限制，是因為一個元素只能有一個父代，因此在視覺化樹狀結構中只能出現一次。  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>設定 GridView 中資料列的樣式  
 使用<xref:System.Windows.Controls.GridViewRowPresenter>和<xref:System.Windows.Controls.GridViewHeaderRowPresenter>格式化及顯示的資料列類別<xref:System.Windows.Controls.GridView>。 如需如何樣式中的資料列<xref:System.Windows.Controls.GridView>檢視模式，請參閱[GridView 樣式 ListView 的實作中的資料列](../../../../docs/framework/wpf/controls/how-to-style-a-row-in-a-listview-that-implements-a-gridview.md)。  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>使用 ItemContainerStyle 時的對齊問題  
 若要避免資料行標頭之間的資料格的對齊問題，請勿設定屬性，或指定的範本，會影響中項目的寬度<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>。 例如，請勿設定<xref:System.Windows.FrameworkElement.Margin%2A>屬性，或指定<xref:System.Windows.Controls.ControlTemplate>，將加上<xref:System.Windows.Controls.CheckBox>至<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>上定義的<xref:System.Windows.Controls.ListView>控制項。 請改為指定的屬性和會影響直接上定義的類別資料行寬度的範本<xref:System.Windows.Controls.GridView>檢視模式。  
  
 例如，若要新增<xref:System.Windows.Controls.CheckBox>中的資料列<xref:System.Windows.Controls.GridView>檢視模式中，加入<xref:System.Windows.Controls.CheckBox>至<xref:System.Windows.DataTemplate>，然後設定<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>屬性的<xref:System.Windows.DataTemplate>。  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>使用者與 GridView 的互動  
 當您使用<xref:System.Windows.Controls.GridView>應用程式中，使用者可以互動和修改的格式設定<xref:System.Windows.Controls.GridView>。 例如，使用者可以重新排列資料行、調整資料行大小、選取表格中的項目，以及捲動內容。 您也可以定義會在使用者按一下資料行標頭按鈕時回應的事件處理常式。 此事件處理常式可以執行作業，例如排序的資料，會顯示在<xref:System.Windows.Controls.GridView>根據資料行的內容。  
  
 下列清單詳細的功能使用討論<xref:System.Windows.Controls.GridView>與使用者互動：  
  
-   **使用拖放方法來重新排列資料行。**  
  
     使用者可以重新排列中的資料行<xref:System.Windows.Controls.GridView>資料行標頭上方時，按滑鼠左鍵，然後將該資料行拖曳至新位置。 當使用者拖曳資料行標頭時，除了會顯示一條指出資料行插入位置的實心黑線之外，也會顯示該標頭的浮動版本。  
  
     如果您想要修改預設樣式浮點版本的標頭，指定<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.GridViewColumnHeader>類型，它是觸發時<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>屬性設定為<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>。 如需詳細資訊，請參閱[為已拖曳的 GridView 資料行標頭建立樣式](../../../../docs/framework/wpf/controls/how-to-create-a-style-for-a-dragged-gridview-column-header.md)。  
  
-   **依資料行內容調整資料行大小。**  
  
     使用者可以按兩下資料行標頭右邊的移駐夾，來依資料行內容調整資料行大小。  
  
    > [!NOTE]
    >  您可以設定<xref:System.Windows.Controls.GridViewColumn.Width%2A>屬性`Double.NaN`產生相同的效果。  
  
-   **選取資料列項目。**  
  
     使用者可以選取一個或多個項目中的<xref:System.Windows.Controls.GridView>。  
  
     如果您想要變更<xref:System.Windows.Style>的選取項目，請參閱[使用觸發程序至樣式 ListView 中選取項目的](../../../../docs/framework/wpf/controls/how-to-use-triggers-to-style-selected-items-in-a-listview.md)。  
  
-   **捲動以檢視一開始在畫面上看不到的內容。**  
  
     如果大小<xref:System.Windows.Controls.GridView>不是大到足以顯示所有項目，使用者可以捲動水平或垂直藉由使用捲軸，這由提供<xref:System.Windows.Controls.ScrollViewer>控制項。 A<xref:System.Windows.Controls.Primitives.ScrollBar>如果特定方向中顯示所有內容，都則都會隱藏。 資料行標頭不會以垂直捲軸捲動，但是會以水平方式捲動。  
  
-   **按一下資料行標頭按鈕來與資料行進行互動。**  
  
     如果您已提供排序演算法，則當使用者按一下資料行標頭按鈕時，將可排序該資料行中顯示的資料。  
  
     您可以處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>資料行行首按鈕，以提供排序演算法等功能的事件。 若要處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>單一的資料行標頭，事件上設定的事件處理常式<xref:System.Windows.Controls.GridViewColumnHeader>。 若要設定事件處理常式處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件的所有資料行標頭，在設定處理常式<xref:System.Windows.Controls.ListView>控制項。  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>取得其他自訂檢視  
 <xref:System.Windows.Controls.GridView>類別，衍生自<xref:System.Windows.Controls.ViewBase>抽象類別，只是其中一個可能的檢視模式的<xref:System.Windows.Controls.ListView>類別。 您可以建立其他自訂檢視<xref:System.Windows.Controls.ListView>由衍生自<xref:System.Windows.Controls.ViewBase>類別。 如需自訂檢視模式的範例，請參閱[建立 ListView 的自訂檢視模式](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md)。  
  
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
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Controls.GridViewColumn>  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.ViewBase>  
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [在按一下標頭時排序 GridView 資料行](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [操作說明主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
