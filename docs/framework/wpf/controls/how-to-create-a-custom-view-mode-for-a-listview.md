---
title: 如何：建立 ListView 的自訂檢視模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 239fb2e9a364bd0265ff7cf644ee296878280cf3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389089"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>如何：建立 ListView 的自訂檢視模式
此範例示範如何建立自訂<xref:System.Windows.Controls.ListView.View%2A>模式<xref:System.Windows.Controls.ListView>控制項。  
  
## <a name="example"></a>範例  
 您必須使用<xref:System.Windows.Controls.ViewBase>類別，在您建立的自訂檢視<xref:System.Windows.Controls.ListView>控制項。 下列範例示範呼叫的檢視模式`PlainView`，其係衍生自<xref:System.Windows.Controls.ViewBase>類別。  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 若要將樣式套用至自訂的檢視，使用<xref:System.Windows.Style>類別。 下列範例會定義<xref:System.Windows.Style>針對`PlainView`檢視模式。 在上述範例中，這個樣式設定的值<xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A>屬性所定義`PlainView`。  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 若要定義的資料配置的自訂檢視模式中，定義<xref:System.Windows.DataTemplate>物件。 下列範例會定義<xref:System.Windows.DataTemplate>，可以用來顯示資料在`PlainView`檢視模式。  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 下列範例示範如何定義<xref:System.Windows.ResourceKey>for`PlainView`使用的檢視模式<xref:System.Windows.DataTemplate>在上述範例中定義。  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 A<xref:System.Windows.Controls.ListView>控制項可以使用自訂的檢視，如果您將設定<xref:System.Windows.Controls.ListView.View%2A>資源索引鍵的屬性。 下列範例示範如何指定`PlainView`做為檢視模式的<xref:System.Windows.Controls.ListView>。  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 如需完整的範例，請參閱[具有多個檢視範例的 ListView](https://go.microsoft.com/fwlink/?LinkID=160013)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)
