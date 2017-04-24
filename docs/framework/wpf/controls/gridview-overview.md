---
title: "GridView 概觀 | Microsoft Docs"
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
  - "控制項, ListView"
  - "GridView 檢視模式"
  - "ListView 控制項, GridView 檢視模式"
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# GridView 概觀
<xref:System.Windows.Controls.GridView> 檢視模式是 <xref:System.Windows.Controls.ListView> 控制項的其中一種檢視模式。  <xref:System.Windows.Controls.GridView> 類別及其支援類別可以讓您和使用者在資料表中檢視項目集合；資料表會通常使用按鈕做為互動資料行行首。  本主題簡介 <xref:System.Windows.Controls.GridView> 類別並概述其用法。  
  
   
  
<a name="DefiningaListViewthatusesGridViewView"></a>   
## 什麼是 GridView 檢視  
 <xref:System.Windows.Controls.GridView> 檢視模式會顯示一份資料項目清單，方法是將資料欄位繫結至資料行，並顯示資料行行首來識別該欄位。  預設的 <xref:System.Windows.Controls.GridView> 樣式會將按鈕實作為資料行行首。  藉由將按鈕當做資料行行首，您可以實作重要的使用者互動功能；例如，使用者可以按一下資料行行首，根據特定資料行的內容來排序 <xref:System.Windows.Controls.GridView> 資料。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.GridView> 用來當做資料行行首的按鈕控制項是從 <xref:System.Windows.Controls.Primitives.ButtonBase> 衍生而來。  
  
 下圖顯示 <xref:System.Windows.Controls.ListView> 內容的 <xref:System.Windows.Controls.GridView> 檢視。  
  
 **ListView 內容的 GridView 檢視**  
  
 ![已設定樣式的 ListView](../../../../docs/framework/wpf/controls/media/styledlistview.png "StyledListView")  
  
 <xref:System.Windows.Controls.GridView> 資料行由 <xref:System.Windows.Controls.GridViewColumn> 物件表示，這些資料行的大小可以依照內容自動調整。  您也可以選擇將 <xref:System.Windows.Controls.GridViewColumn> 明確設定為特定寬度。  您可以透過拖曳資料行行首間的移駐夾 \(Gripper\)，調整資料行的大小。  您也可以動態加入、移除、取代和重新排序資料行，因為這是 <xref:System.Windows.Controls.GridView> 的內建功能。  不過，<xref:System.Windows.Controls.GridView> 不能直接更新其所顯示的資料。  
  
 下列範例示範如何定義顯示員工資料的 <xref:System.Windows.Controls.GridView>。  在這個範例中，<xref:System.Windows.Controls.ListView> 將 `EmployeeInfoDataSource` 定義為 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。  <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 的屬性定義則將 <xref:System.Windows.Controls.GridViewColumn> 內容繫結至 `EmployeeInfoDataSource` 資料分類。  
  
 [!code-xml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 下圖顯示上述範例所建立的資料表。  
  
 **顯示來自 ItemsSource 之資料的 GridView**  
  
 ![ListView 與 GridView 輸出](../../../../docs/framework/wpf/controls/media/listviewgridview.png "ListViewGridView")  
  
<a name="GridViewLayoutandStyle"></a>   
## GridView 配置和樣式  
 <xref:System.Windows.Controls.GridViewColumn> 的資料行儲存格和資料行行首寬度相同。  根據預設，每個資料行都會配合其內容來調整寬度。  您也可以選擇將資料行設定為固定寬度。  
  
 相關資料內容會顯示在水平資料列中。  例如在上圖中，每個員工的姓氏、名字和 ID 編號顯示成一個集合，因為它們會出現在一個水平資料列中。  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### 定義 GridView 中的資料行並設定樣式  
 定義要顯示在 <xref:System.Windows.Controls.GridViewColumn> 中的資料欄位時，請使用 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> 或 <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> 等屬性。  <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 屬性的優先順序高於任何一個範本屬性。  
  
 若要指定 <xref:System.Windows.Controls.GridView> 資料行的內容對齊方式，請定義 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>。  使用 <xref:System.Windows.Controls.GridView> 顯示的 <xref:System.Windows.Controls.ListView> 內容請不要使用 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> 和 <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> 屬性。  
  
 若要指定資料行行首的範本和樣式屬性，請使用 <xref:System.Windows.Controls.GridView>、<xref:System.Windows.Controls.GridViewColumn> 和 <xref:System.Windows.Controls.GridViewColumnHeader> 等類別。  如需詳細資訊，請參閱 [GridView 資料行行首樣式和範本概觀](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)。  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### 將視覺化項目加入至 GridView  
 若要將視覺化項目 \(例如 <xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.Button> 控制項\) 加入至 <xref:System.Windows.Controls.GridView> 檢視模式，請使用範本或樣式。  
  
 如果您將視覺化項目明確定為資料項目，該項目就只能在 <xref:System.Windows.Controls.GridView> 中出現一次。  這項限制存在的原因是項目只能有一個父代 \(Parent\)，因此只能在[視覺化樹狀結構](GTMT)中出現一次。  
  
<a name="StylingRowsinaGridViewView"></a>   
### 設定 GridView 中的資料列樣式  
 請使用 <xref:System.Windows.Controls.GridViewRowPresenter> 和 <xref:System.Windows.Controls.GridViewHeaderRowPresenter> 類別格式化及顯示 <xref:System.Windows.Controls.GridView> 的資料列。  如需如何在 <xref:System.Windows.Controls.GridView> 檢視模式中設定資料列樣式的範例，請參閱 [在實作 GridView 的 ListView 中設定資料列的樣式](../../../../docs/framework/wpf/controls/how-to-style-a-row-in-a-listview-that-implements-a-gridview.md)。  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### 使用 ItemContainerStyle 時的對齊問題  
 為避免資料行行首和儲存格之間的對齊問題，請勿設定屬性或指定會影響 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 中項目寬度的範本。  例如，請勿設定 <xref:System.Windows.FrameworkElement.Margin%2A> 屬性，或是指定會將 <xref:System.Windows.Controls.CheckBox> 加入至 <xref:System.Windows.Controls.ListView> 控制項上定義之 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 的 <xref:System.Windows.Controls.ControlTemplate>。  請改為在定義 <xref:System.Windows.Controls.GridView> 檢視模式的類別上，指定直接影響資料行寬度的屬性和範本。  
  
 例如，若要將 <xref:System.Windows.Controls.CheckBox> 加入至 <xref:System.Windows.Controls.GridView> 檢視模式中的資料列，請將 <xref:System.Windows.Controls.CheckBox> 加入至 <xref:System.Windows.DataTemplate>，然後將 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> 屬性設定為該 <xref:System.Windows.DataTemplate>。  
  
<a name="InteractingwithaGridViewControl"></a>   
## 使用者與 GridView 的互動  
 當您在應用程式中使用 <xref:System.Windows.Controls.GridView> 時，使用者可以與 <xref:System.Windows.Controls.GridView> 互動並修改其格式設定。  例如，使用者可以重新排序資料行、調整資料行大小、選取資料表中的項目，以及捲動內容。  您也可以定義事件處理常式 \(Event Handler\)，在使用者按一下資料行行首按鈕時做出回應。  這個事件處理常式可以執行諸如根據資料行內容排序 <xref:System.Windows.Controls.GridView> 中顯示之資料等作業。  
  
 下列清單將進一步探討使用 <xref:System.Windows.Controls.GridView> 與使用者互動的功能：  
  
-   **使用拖放方法重新排序資料行。**  
  
     使用者可以重新排序 <xref:System.Windows.Controls.GridView> 中的資料行，方法是在資料行行首上按下滑鼠左鍵，然後將該資料行拖曳到新的位置。  當使用者拖曳資料行行首時，將會顯示行首的浮動版本，以及指出資料行插入位置的實心黑線。  
  
     如果您想修改行首浮動版本的預設樣式，請指定 <xref:System.Windows.Controls.GridViewColumnHeader> 型別的 <xref:System.Windows.Controls.ControlTemplate>，其觸發 \(Trigger\) 時機是在 <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> 屬性設定為 <xref:System.Windows.Controls.GridViewColumnHeaderRole> 時。  如需詳細資訊，請參閱 [為已拖曳的 GridView 資料行行首建立樣式](../../../../docs/framework/wpf/controls/how-to-create-a-style-for-a-dragged-gridview-column-header.md)。  
  
-   **配合內容調整資料行大小。**  
  
     使用者可以按兩下資料行行首右邊的移駐夾，以配合內容調整資料行的大小。  
  
    > [!NOTE]
    >  您可以將 <xref:System.Windows.Controls.GridViewColumn.Width%2A> 屬性設定為 `Double.NaN` 來產生相同的效果。  
  
-   **選取資料列項目。**  
  
     使用者可以在 <xref:System.Windows.Controls.GridView> 中選取一個或多個項目。  
  
     如果您想變更選定項目的 <xref:System.Windows.Style>，請參閱 [使用觸發程式設定 ListView 中的選取項目樣式](../../../../docs/framework/wpf/controls/how-to-use-triggers-to-style-selected-items-in-a-listview.md)。  
  
-   **捲動以檢視一開始未顯示在螢幕上的內容。**  
  
     如果 <xref:System.Windows.Controls.GridView> 的大小不足以顯示所有的項目，使用者可以使用捲軸進行水平或垂直捲動；捲軸是由 <xref:System.Windows.Controls.ScrollViewer> 控制項提供。  如果可以在特定方向看到所有的內容，<xref:System.Windows.Controls.Primitives.ScrollBar> 就會隱藏起來。  資料行行首不能以垂直捲軸捲動，但可以水平捲動。  
  
-   **按一下資料行行首按鈕與資料行互動。**  
  
     當使用者按一下資料行行首按鈕時，如果您已提供排序演算法，使用者就可以排序顯示在資料行中的資料。  
  
     您可以處理資料行行首按鈕的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件，以提供與排序演算法類似的功能。  若要處理單一資料行行首的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件，請在 <xref:System.Windows.Controls.GridViewColumnHeader> 上設定事件處理常式。  若要設定處理所有資料行行首之 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的事件處理常式，請在 <xref:System.Windows.Controls.ListView> 控制項上設定該處理常式。  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## 取得其他自訂檢視  
 衍生自 <xref:System.Windows.Controls.ViewBase> 抽象類別 \(Abstract Class\) 的 <xref:System.Windows.Controls.GridView> 類別只是 <xref:System.Windows.Controls.ListView> 類別多種可能的檢視模式其中一種。  您可以透過從 <xref:System.Windows.Controls.ViewBase> 類別衍生，建立 <xref:System.Windows.Controls.ListView> 的其他自訂檢視。  如需自訂檢視模式的範例，請參閱 [建立 ListView 的自訂檢視模式](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md)。  
  
<a name="GridViewSupportingClasses"></a>   
## GridView 支援類別  
 下列類別可支援 <xref:System.Windows.Controls.GridView> 檢視模式。  
  
-   <xref:System.Windows.Controls.GridViewColumn>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GridViewRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewColumnCollection>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## 請參閱  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.ListViewItem>   
 <xref:System.Windows.Controls.GridViewColumn>   
 <xref:System.Windows.Controls.GridViewColumnHeader>   
 <xref:System.Windows.Controls.GridViewRowPresenter>   
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>   
 <xref:System.Windows.Controls.ViewBase>   
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [在按一下行首時排序 GridView 資料行](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)