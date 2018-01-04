---
title: "如何：排序檢視中的資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7467913f867ea0990ae85b0ad933c11f2fd271b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-sort-data-in-a-view"></a>如何：排序檢視中的資料
這個範例說明如何在檢視中排序資料。  
  
## <a name="example"></a>範例  
 下列範例會建立簡單<xref:System.Windows.Controls.ListBox>和<xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <xref:System.Windows.Controls.Primitives.ButtonBase.Click>按鈕的事件處理常式包含邏輯，可排序的項目<xref:System.Windows.Controls.ListBox>遞減的順序。 您可以新增項目到因為<xref:System.Windows.Controls.ListBox>這種方式將它們加入至<xref:System.Windows.Controls.ItemCollection>的<xref:System.Windows.Controls.ListBox>，和<xref:System.Windows.Controls.ItemCollection>衍生自<xref:System.Windows.Data.CollectionView>類別。 如果您要繫結您<xref:System.Windows.Controls.ListBox>集合使用<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性，您可以使用相同的技巧來排序。  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 只要您有檢視物件的參考，您可以使用相同的技巧來排序其他集合檢視的內容。 如需如何取得檢視的範例，請參閱[取得預設的檢視資料收集](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)。 如需其他範例，請參閱[排序 GridView 資料行時標頭按一下](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)。 如需檢視的詳細資訊，請參閱 < 繫結至集合中[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
 如需如何套用排序的邏輯中的範例[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，請參閱[排序與群組資料使用 XAML 中的檢視](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>  
 [在按一下標頭時排序 GridView 資料行](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [篩選檢視中的資料](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
