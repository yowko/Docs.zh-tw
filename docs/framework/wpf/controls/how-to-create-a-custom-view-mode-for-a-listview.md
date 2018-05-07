---
title: 如何：建立 ListView 的自訂檢視模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: b8600a2e201fdbcb566e6a322e3ecdabbe1641ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>如何：建立 ListView 的自訂檢視模式
這個範例示範如何建立自訂<xref:System.Windows.Controls.ListView.View%2A>模式<xref:System.Windows.Controls.ListView>控制項。  
  
## <a name="example"></a>範例  
 您必須使用<xref:System.Windows.Controls.ViewBase>類別時會建立的自訂檢視<xref:System.Windows.Controls.ListView>控制項。 下列範例示範呼叫的檢視模式`PlainView`，其衍生自<xref:System.Windows.Controls.ViewBase>類別。  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 若要將樣式套用至自訂的檢視，使用<xref:System.Windows.Style>類別。 下列範例會定義<xref:System.Windows.Style>如`PlainView`檢視模式。 在上一個範例中，設定此樣式的值為<xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A>屬性定義的`PlainView`。  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 若要在自訂檢視模式中定義的資料版面配置，定義<xref:System.Windows.DataTemplate>物件。 下列範例會定義<xref:System.Windows.DataTemplate>，可以用來顯示資料在`PlainView`檢視模式。  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 下列範例示範如何定義<xref:System.Windows.ResourceKey>如`PlainView`檢視模式中使用<xref:System.Windows.DataTemplate>前一個範例中定義的。  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 A<xref:System.Windows.Controls.ListView>控制項可以使用自訂的檢視，如果您設定<xref:System.Windows.Controls.ListView.View%2A>資源索引鍵的屬性。 下列範例示範如何指定`PlainView`作為檢視模式<xref:System.Windows.Controls.ListView>。  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 如需完整範例，請參閱[ListView 與多個檢視範例](http://go.microsoft.com/fwlink/?LinkID=160013)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)
