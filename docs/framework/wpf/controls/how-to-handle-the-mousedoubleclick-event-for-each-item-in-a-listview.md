---
title: HOW TO：處理 ListView 中每個項目的 MouseDoubleClick 事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 2a201eefba6e2623cfd7f733b85e271ce1c4e177
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576049"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>HOW TO：處理 ListView 中每個項目的 MouseDoubleClick 事件
若要處理的事件中的項目<xref:System.Windows.Controls.ListView>，您需要將事件處理常式新增至每個<xref:System.Windows.Controls.ListViewItem>。 當<xref:System.Windows.Controls.ListView>繫結至資料來源，您無法明確建立<xref:System.Windows.Controls.ListViewItem>，但您可以藉由新增來處理每個項目的事件<xref:System.Windows.EventSetter>風格的<xref:System.Windows.Controls.ListViewItem>。  
  
## <a name="example"></a>範例  
 下列範例會建立資料繫結<xref:System.Windows.Controls.ListView>，並建立<xref:System.Windows.Style>將事件處理常式新增至每個<xref:System.Windows.Controls.ListViewItem>。  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 下列範例會處理<xref:System.Windows.Controls.Control.MouseDoubleClick>事件。  
  
 [!code-csharp[ListViewHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  雖然它是最常用來繫結<xref:System.Windows.Controls.ListView>到資料來源，您可以將事件處理常式新增至每個使用樣式<xref:System.Windows.Controls.ListViewItem>在非資料-繫結<xref:System.Windows.Controls.ListView>不論您是否明確建立<xref:System.Windows.Controls.ListViewItem>。  如需有關明確和隱含方式建立<xref:System.Windows.Controls.ListViewItem>控制項，請參閱<xref:System.Windows.Controls.ItemsControl>。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Xml.XmlElement>
- [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)
