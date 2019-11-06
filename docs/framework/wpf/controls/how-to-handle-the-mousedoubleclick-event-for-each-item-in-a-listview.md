---
title: 如何：處理 ListView 中每個項目的 MouseDoubleClick 事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 25308ee87fb387787e20c8a8887ae8e4e60742b9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460226"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>如何：處理 ListView 中每個項目的 MouseDoubleClick 事件
若要處理 <xref:System.Windows.Controls.ListView>中專案的事件，您需要將事件處理常式新增至每個 <xref:System.Windows.Controls.ListViewItem>。 當 <xref:System.Windows.Controls.ListView> 系結至資料來源時，您不會明確建立 <xref:System.Windows.Controls.ListViewItem>，但是您可以藉由將 <xref:System.Windows.EventSetter> 新增至 <xref:System.Windows.Controls.ListViewItem>的樣式，來處理每個專案的事件。  
  
## <a name="example"></a>範例  
 下列範例會建立資料系結 <xref:System.Windows.Controls.ListView>，並建立 <xref:System.Windows.Style>，將事件處理常式加入至每個 <xref:System.Windows.Controls.ListViewItem>。  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 下列範例會處理 <xref:System.Windows.Controls.Control.MouseDoubleClick> 事件。  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> 雖然將 <xref:System.Windows.Controls.ListView> 系結至資料來源是最常見的，但您可以使用樣式，將事件處理常式新增至非資料系結 <xref:System.Windows.Controls.ListView> 中的每個 <xref:System.Windows.Controls.ListViewItem>，不論您是否明確建立 <xref:System.Windows.Controls.ListViewItem>。  如需明確和隱含建立之 <xref:System.Windows.Controls.ListViewItem> 控制項的詳細資訊，請參閱 <xref:System.Windows.Controls.ItemsControl>。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Xml.XmlElement>
- [資料繫結概觀](../data/data-binding-overview.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView 概觀](listview-overview.md)
