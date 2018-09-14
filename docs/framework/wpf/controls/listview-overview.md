---
title: ListView 概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: a3b5805808ce2e84e7713f07694464b75d83a391
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521618"
---
# <a name="listview-overview"></a>ListView 概觀
<xref:System.Windows.Controls.ListView>控制項提供的基礎結構，以顯示不同的版面配置或檢視表中的一組資料的項目。 例如，使用者可能會想要以表格顯示資料項目，還要排序其資料行。  
  
  
<a name="WhatisaListView"></a>   
## <a name="what-is-a-listview"></a>什麼是 ListView？  
 <xref:System.Windows.Controls.ListView>控制項是<xref:System.Windows.Controls.ItemsControl>衍生自<xref:System.Windows.Controls.ListBox>。 一般而言，其項目是資料集合的成員，並會表示為<xref:System.Windows.Controls.ListViewItem>物件。 A<xref:System.Windows.Controls.ListViewItem>是<xref:System.Windows.Controls.ContentControl>，而且可以包含單一子項目。 不過，該子元素可以是任何視覺元素。  
  
<a name="DefiningaListViewView"></a>   
## <a name="defining-a-view-mode-for-a-listview"></a>定義 ListView 的檢視模式  
 若要指定內容的檢視模式<xref:System.Windows.Controls.ListView>控制項，您設定<xref:System.Windows.Controls.ListView.View%2A>屬性。 一個檢視模式中，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供是<xref:System.Windows.Controls.GridView>，其中具有可自訂的資料行的資料表中顯示資料的項目集合。  
  
 下列範例示範如何定義<xref:System.Windows.Controls.GridView>針對<xref:System.Windows.Controls.ListView>顯示員工資訊的控制項。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 下圖顯示上一個範例的資料顯示方式。  
  
 ![含有 GridView 輸出的 ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
 您可以建立自訂檢視模式定義類別繼承自<xref:System.Windows.Controls.ViewBase>類別。 <xref:System.Windows.Controls.ViewBase>類別會提供您需要建立自訂檢視的基礎結構。 如需有關如何建立自訂檢視的詳細資訊，請參閱[建立 ListView 的自訂檢視模式](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md)。  
  
<a name="BindingDatatoaListView"></a>   
## <a name="binding-data-to-a-listview"></a>將資料繫結至 ListView  
 使用<xref:System.Windows.Controls.ItemsControl.Items%2A>並<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性，以指定的項目<xref:System.Windows.Controls.ListView>控制項。 下列範例會設定<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性到資料集合，稱為`EmployeeInfoDataSource`。  
  
 [!code-xaml[ListViewCode#ItemsSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 在  <xref:System.Windows.Controls.GridView>，<xref:System.Windows.Controls.GridViewColumn>物件繫結至指定的資料欄位。 下列範例會繫結<xref:System.Windows.Controls.GridViewColumn>藉由指定資料欄位的物件<xref:System.Windows.Data.Binding>如<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性。  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 您也可以指定<xref:System.Windows.Data.Binding>一部分<xref:System.Windows.DataTemplate>定義您用來設定資料行中的資料格的樣式。 在下列範例中， <xref:System.Windows.DataTemplate> ，會用來識別<xref:System.Windows.ResourceKey>設定<xref:System.Windows.Data.Binding>如<xref:System.Windows.Controls.GridViewColumn>。 請注意，此範例並未定義<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>因為如此一來，會覆寫所指定的繫結<xref:System.Windows.DataTemplate>。  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>   
## <a name="styling-a-listview-that-implements-a-gridview"></a>為實作 GridView 的 ListView 設定樣式  
 <xref:System.Windows.Controls.ListView>控制項包含<xref:System.Windows.Controls.ListViewItem>物件，代表顯示資料項目。 您可以使用下列屬性來定義資料項目的內容和樣式：  
  
-   在 <xref:System.Windows.Controls.ListView>控制，請使用<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>， <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>，和<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>屬性。  
  
-   在 <xref:System.Windows.Controls.ListViewItem>控制，請使用<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>和<xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>屬性。  
  
 若要避免發生對齊問題中儲存格之間<xref:System.Windows.Controls.GridView>，請勿使用<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>來設定屬性，或將影響該寬度的項目中的內容新增<xref:System.Windows.Controls.ListView>。 比方說，當您設定時可能會發生對齊問題<xref:System.Windows.FrameworkElement.Margin%2A>屬性中的<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>。 若要指定屬性或定義會影響該寬度的項目中的內容<xref:System.Windows.Controls.GridView>，使用的屬性<xref:System.Windows.Controls.GridView>類別和其相關的類別，例如<xref:System.Windows.Controls.GridViewColumn>。  
  
 如需有關如何使用<xref:System.Windows.Controls.GridView>和其支援的類別，請參閱[GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)。  
  
 如果您定義<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>for<xref:System.Windows.Controls.ListView>控制，而且也定義<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>，您必須包含<xref:System.Windows.Controls.ContentPresenter>為了讓樣式<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>才能正常運作。  
  
 請勿使用<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>並<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>屬性<xref:System.Windows.Controls.ListView>會顯示所使用的內容<xref:System.Windows.Controls.GridView>。 若要指定的資料行中的內容的對齊<xref:System.Windows.Controls.GridView>，定義<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>。  
  
<a name="UsingtheSameViewMoreThanOnce"></a>   
## <a name="sharing-the-same-view-mode"></a>共用相同的檢視模式  
 兩個<xref:System.Windows.Controls.ListView>控制項不能共用相同的檢視模式，在相同的時間。 如果您嘗試使用相同的檢視模式與多個<xref:System.Windows.Controls.ListView>控制項時，發生例外狀況。  
  
 若要指定可以同時使用多個檢視模式<xref:System.Windows.Controls.ListView>，使用範本或樣式。 如需如何定義為檢視的範例<xref:System.Windows.FrameworkElement.Resources%2A>，請參閱 < [ListView 與多個檢視範例](https://go.microsoft.com/fwlink/?LinkID=160013)。  
  
<a name="CreatingaCustomView"></a>   
## <a name="creating-a-custom-view-mode"></a>建立自訂檢視模式  
 自訂檢視<xref:System.Windows.Controls.GridView>衍生自<xref:System.Windows.Controls.ViewBase>抽象類別，可提供工具，可顯示資料的項目，即表示<xref:System.Windows.Controls.ListViewItem>物件。  
  
 如需自訂檢視模式的範例，請參閱[具有多個檢視的 ListView 範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=160013)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.GridView>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Data.Binding>  
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [控制項](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
