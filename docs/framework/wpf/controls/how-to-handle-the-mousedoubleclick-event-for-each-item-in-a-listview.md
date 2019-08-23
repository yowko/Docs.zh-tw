---
title: 作法：處理 ListView 中每個項目的 MouseDoubleClick 事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7e51c810a2e1e4bf4157aa1311255c5547021b60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962068"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>作法：處理 ListView 中每個項目的 MouseDoubleClick 事件
若要處理中<xref:System.Windows.Controls.ListView>某個專案的事件, 您必須將事件處理常式加入至每個。 <xref:System.Windows.Controls.ListViewItem> 當系結至資料來源時, 您不會明確<xref:System.Windows.Controls.ListViewItem>建立, 但是您可以藉由將加入<xref:System.Windows.EventSetter>至的樣式<xref:System.Windows.Controls.ListViewItem>, 來處理每個專案的事件。 <xref:System.Windows.Controls.ListView>  
  
## <a name="example"></a>範例  
 下列範例會建立資料<xref:System.Windows.Controls.ListView>系結並<xref:System.Windows.Style>建立, 以便將事件處理常式加入至每<xref:System.Windows.Controls.ListViewItem>個。  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 下列範例會處理<xref:System.Windows.Controls.Control.MouseDoubleClick>事件。  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> 雖然將<xref:System.Windows.Controls.ListView>系結至資料來源是最常見的, 但您可以使用樣式, 將事件處理常式新增至<xref:System.Windows.Controls.ListView>非<xref:System.Windows.Controls.ListViewItem>資料系結中的每個, 而不論您是否明確建立<xref:System.Windows.Controls.ListViewItem>。  如需明確和隱含建立<xref:System.Windows.Controls.ListViewItem>之控制項的詳細資訊, 請參閱。 <xref:System.Windows.Controls.ItemsControl>  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.XmlElement>
- [資料繫結概觀](../data/data-binding-overview.md)
- [樣式設定和範本化](styling-and-templating.md)
- [使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView 概觀](listview-overview.md)
