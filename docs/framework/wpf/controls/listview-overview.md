---
title: "ListView 概觀 | Microsoft Docs"
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
  - "ListView 控制項 [WPF], 關於 ListView 控制項"
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# ListView 概觀
<xref:System.Windows.Controls.ListView> 控制項可提供基礎結構，以在不同的版面配置或檢視顯示一組資料項目。  例如，使用者可能會想在資料表中顯示資料項目，並以資料行排序。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="WhatisaListView"></a>   
## 什麼是 ListView  
 <xref:System.Windows.Controls.ListView> 控制項是衍生自 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.Controls.ItemsControl>。  這種控制項的項目通常是資料集合的成員，而且會以 <xref:System.Windows.Controls.ListViewItem> 物件表示。  <xref:System.Windows.Controls.ListViewItem> 是一種 <xref:System.Windows.Controls.ContentControl>，只能包含單一子項目。  不過，這個子項目可以是任何視覺化項目。  
  
<a name="DefiningaListViewView"></a>   
## 定義 ListView 的檢視模式  
 若要指定 <xref:System.Windows.Controls.ListView> 控制項內容的檢視模式，請設定 <xref:System.Windows.Controls.ListView.View%2A> 屬性。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供的一種檢視模式是 <xref:System.Windows.Controls.GridView>，會在可以自訂資料行的資料表中顯示一組資料項目。  
  
 下列範例顯示如何定義 <xref:System.Windows.Controls.ListView> 控制項的 <xref:System.Windows.Controls.GridView>，以顯示員工資訊。  
  
 [!code-xml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 下圖顯示上述範例的資料顯示出來的樣子。  
  
 ![ListView 與 GridView 輸出](../../../../docs/framework/wpf/controls/media/listviewgridview.png "ListViewGridView")  
  
 您可以定義繼承自 <xref:System.Windows.Controls.ViewBase> 類別的類別，以建立自訂檢視模式。  <xref:System.Windows.Controls.ViewBase> 類別可提供建立自訂檢視所需的基礎結構。  如需如何建立自訂檢視的詳細資訊，請參閱 [建立 ListView 的自訂檢視模式](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md)。  
  
<a name="BindingDatatoaListView"></a>   
## 將資料繫結至 ListView  
 請使用 <xref:System.Windows.Controls.ItemsControl.Items%2A> 和 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性指定 <xref:System.Windows.Controls.ListView> 控制項的項目。  下列範例會將 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性設為名為 `EmployeeInfoDataSource` 的資料集合。  
  
 [!code-xml[ListViewCode#ItemsSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 在 <xref:System.Windows.Controls.GridView> 中，<xref:System.Windows.Controls.GridViewColumn> 物件會繫結至指定的資料欄位。  下列範例會指定 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 屬性的 <xref:System.Windows.Data.Binding>，以將 <xref:System.Windows.Controls.GridViewColumn> 物件繫結至資料欄位。  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xml[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 您也可以指定 <xref:System.Windows.Data.Binding> 做為 <xref:System.Windows.DataTemplate> 定義的一部分，再使用定義設定資料行儲存格的樣式。  下列範例中，以 <xref:System.Windows.ResourceKey> 識別的 <xref:System.Windows.DataTemplate> 會設定 <xref:System.Windows.Controls.GridViewColumn> 的 <xref:System.Windows.Data.Binding>。  請注意，這個範例不會定義 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>，因為這麼做會覆寫 <xref:System.Windows.DataTemplate> 指定的繫結。  
  
 [!code-xml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>   
## 設定實作 GridView 之 ListView 的樣式  
 <xref:System.Windows.Controls.ListView> 控制項包含 <xref:System.Windows.Controls.ListViewItem> 物件，這些物件代表顯示的資料項目。  您可以使用下列屬性定義資料項目的內容和樣式：  
  
-   在 <xref:System.Windows.Controls.ListView> 控制項上，使用 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>、<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> 和 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 屬性。  
  
-   在 <xref:System.Windows.Controls.ListViewItem> 控制項上，使用 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 和 <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> 屬性。  
  
 為避免 <xref:System.Windows.Controls.GridView> 儲存格之間的對齊問題，請不要使用 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 設定屬性或加入會影響 <xref:System.Windows.Controls.ListView> 中項目寬度的內容。  例如，當您在 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 中設定 <xref:System.Windows.FrameworkElement.Margin%2A> 屬性時，就可能會發生對齊問題。  若要指定屬性或定義會影響 <xref:System.Windows.Controls.GridView> 中項目寬度的內容，請使用 <xref:System.Windows.Controls.GridView> 類別及其相關類別的屬性，例如 <xref:System.Windows.Controls.GridViewColumn>。  
  
 如需如何使用 <xref:System.Windows.Controls.GridView> 及其支援類別的詳細資訊，請參閱 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)。  
  
 如果您定義了 <xref:System.Windows.Controls.ListView> 控制項的 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>，而且也定義了 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>，就必須將 <xref:System.Windows.Controls.ContentPresenter> 加入樣式中，<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 才能正常運作。  
  
 使用 <xref:System.Windows.Controls.GridView> 顯示的 <xref:System.Windows.Controls.ListView> 內容請不要使用 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> 和 <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> 屬性。  若要指定 <xref:System.Windows.Controls.GridView> 資料行的內容對齊方式，請定義 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>。  
  
<a name="UsingtheSameViewMoreThanOnce"></a>   
## 共用相同檢視模式  
 兩個 <xref:System.Windows.Controls.ListView> 控制項無法同時共用相同的檢視模式。  如果有一個以上的 <xref:System.Windows.Controls.ListView> 控制項嘗試使用相同的檢視模式，會發生例外狀況。  
  
 若要指定多個 <xref:System.Windows.Controls.ListView> 可以同時使用的檢視模式，請使用樣板或樣式。  如需如何將檢視定義為 <xref:System.Windows.FrameworkElement.Resources%2A> 的範例，請參閱[具有多個檢視的 ListView 範例](http://go.microsoft.com/fwlink/?LinkID=160013) \(英文\)。  
  
<a name="CreatingaCustomView"></a>   
## 建立自訂檢視模式  
 自訂檢視 \(如 <xref:System.Windows.Controls.GridView>\) 是衍生自 <xref:System.Windows.Controls.ViewBase> 抽象類別，能提供工具來顯示 <xref:System.Windows.Controls.ListViewItem> 物件所代表的資料項目。  
  
 如需自訂檢視模式的範例，請參閱[具有多個檢視的 ListView 範例](http://go.microsoft.com/fwlink/?LinkID=160013) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Controls.GridView>   
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.ListViewItem>   
 <xref:System.Windows.Data.Binding>   
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [控制項](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)