---
title: 如何：使用含階層式資料的主從式模式
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 2e7d9ceed3ab8385f07d87ecdb92c0a99d410b40
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459089"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>如何：使用含階層式資料的主從式模式
這個範例示範如何執行主要-詳細資料案例。  
  
## <a name="example"></a>範例  
 在此範例中，`LeagueList` 是 `Leagues`的集合。 每個 `League` 都有一個 `Name` 和一個 `Divisions`的集合，而且每個 `Division` 都有一個名稱和一個 `Teams`的集合。 每個 `Team` 都有一個小組名稱。  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 以下是範例的螢幕擷取畫面。 `Divisions` <xref:System.Windows.Controls.ListBox> 會自動追蹤 `Leagues` <xref:System.Windows.Controls.ListBox> 中的選取專案，並顯示對應的資料。 `Teams` <xref:System.Windows.Controls.ListBox> 會追蹤其他兩個 <xref:System.Windows.Controls.ListBox> 控制項中的選取專案。  
  
 ![顯示主要&#45;詳細資料案例範例的螢幕擷取畫面。](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 在此範例中要注意的兩件事包括：  
  
1. 三個 <xref:System.Windows.Controls.ListBox> 控制項系結至相同的來源。 您可以設定系結的 <xref:System.Windows.Data.Binding.Path%2A> 屬性，以指定要讓 <xref:System.Windows.Controls.ListBox> 顯示的資料層級。  
  
2. 您必須將 [<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>] 屬性設定為您要追蹤其選取範圍之 <xref:System.Windows.Controls.ListBox> 控制項上的 `true`。 設定這個屬性可確保選取的專案一律設定為 <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>。 或者，如果 <xref:System.Windows.Controls.ListBox> 從 <xref:System.Windows.Data.CollectionViewSource>取得資料，則會自動同步處理選取範圍和貨幣。  
  
 當您使用 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料時，這項技術會稍有不同。 如需範例，請參閱搭配[階層式 XML 資料使用主版-詳細模式](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.HierarchicalDataTemplate>
- [繫結至集合並根據選取項目顯示資訊](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [資料範本化概觀](data-templating-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
