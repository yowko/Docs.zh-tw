---
title: 如何：將樹狀檢視繫結至未知深度的資料
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
ms.openlocfilehash: 30e328c94e1e1da4641e93dd5f5730eab2d8af1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554371"
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>如何：將樹狀檢視繫結至未知深度的資料
有時當您想要繫結<xref:System.Windows.Controls.TreeView>深度不知道資料來源。  發生這個問題的資料是遞迴的本質，例如檔案系統，其中的資料夾可以包含資料夾或公司的組織結構，其中員工的直屬員工的其他員工。  
  
 資料來源必須具有階層式物件模型。 例如，`Employee`類別可能包含員工的直屬員工的員工物件的集合。 如果資料以不是階層式的方式表示，您必須建置資料的階層式表示法。  
  
 當您將<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType>屬性，而且當<xref:System.Windows.Controls.ItemsControl>產生<xref:System.Windows.Controls.ItemsControl>每個子項目，則子系<xref:System.Windows.Controls.ItemsControl>會使用相同<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>做為父系。 例如，如果您設定<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>資料繫結上的屬性<xref:System.Windows.Controls.TreeView>，每個<xref:System.Windows.Controls.TreeViewItem>也就是產生的使用<xref:System.Windows.DataTemplate>，已指派給<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>屬性<xref:System.Windows.Controls.TreeView>。  
  
 <xref:System.Windows.HierarchicalDataTemplate>可讓您指定<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>如<xref:System.Windows.Controls.TreeViewItem>，或任何<xref:System.Windows.Controls.HeaderedItemsControl>，資料範本。 當您將<xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType>屬性的值時使用<xref:System.Windows.HierarchicalDataTemplate>套用。 使用<xref:System.Windows.HierarchicalDataTemplate>，您可以以遞迴方式組<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>每個<xref:System.Windows.Controls.TreeViewItem>中<xref:System.Windows.Controls.TreeView>。  
  
## <a name="example"></a>範例  
 下列範例示範如何將繫結<xref:System.Windows.Controls.TreeView>階層式資料和使用<xref:System.Windows.HierarchicalDataTemplate>指定<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>每個<xref:System.Windows.Controls.TreeViewItem>。  <xref:System.Windows.Controls.TreeView>繫結至 XML 資料表示公司的員工。  每個`Employee`元素可包含其他`Employee`表示人員報告對項目。 因為資料是遞迴，<xref:System.Windows.HierarchicalDataTemplate>可以套用至每個層級。  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>另請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)
