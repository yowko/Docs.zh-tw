---
title: 如何：將樹狀檢視繫結至未知深度的資料
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
ms.openlocfilehash: cd9a1ee015ebb707a7a06d1c062a1bb3003c96e8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458610"
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>如何：將樹狀檢視繫結至未知深度的資料
有時候，您可能會想要將 <xref:System.Windows.Controls.TreeView> 系結至深度未知的資料來源。  這種情況可能發生在資料本質上是遞迴的情況下（例如檔案系統），其中資料夾可以包含資料夾，或公司的組織結構，其中員工會將其他員工當做直接報表。  
  
 資料來源必須有階層式物件模型。 例如，`Employee` 的類別可能包含 employee 物件的集合，這些物件是員工的直屬員工。 如果資料是以不是階層式的方式來表示，您就必須建立資料的階層式標記法。  
  
 當您設定 [<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType>] 屬性，而且 <xref:System.Windows.Controls.ItemsControl> 為每個子專案產生 <xref:System.Windows.Controls.ItemsControl> 時，子 <xref:System.Windows.Controls.ItemsControl> 會使用與父系相同的 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>。 例如，如果您在資料系結 <xref:System.Windows.Controls.TreeView>上設定 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 屬性，則每個產生的 <xref:System.Windows.Controls.TreeViewItem> 都會使用指派給 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 之 <xref:System.Windows.Controls.TreeView>屬性的 <xref:System.Windows.DataTemplate>。  
  
 <xref:System.Windows.HierarchicalDataTemplate> 可讓您在資料範本上指定 <xref:System.Windows.Controls.TreeViewItem>或任何 <xref:System.Windows.Controls.HeaderedItemsControl>的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。 當您設定 <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType> 屬性時，會在套用 <xref:System.Windows.HierarchicalDataTemplate> 時使用該值。 藉由使用 <xref:System.Windows.HierarchicalDataTemplate>，您可以在 <xref:System.Windows.Controls.TreeView>中，以遞迴方式設定每個 <xref:System.Windows.Controls.TreeViewItem> 的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。  
  
## <a name="example"></a>範例  
 下列範例示範如何將 <xref:System.Windows.Controls.TreeView> 系結至階層式資料，並使用 <xref:System.Windows.HierarchicalDataTemplate> 來指定每個 <xref:System.Windows.Controls.TreeViewItem>的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。  <xref:System.Windows.Controls.TreeView> 系結至代表公司員工的 XML 資料。  每個 `Employee` 元素都可以包含其他 `Employee` 元素，以指出誰向誰報告。 因為資料是遞迴的，所以 <xref:System.Windows.HierarchicalDataTemplate> 可以套用至每個層級。  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>請參閱

- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [資料範本化概觀](../data/data-templating-overview.md)
