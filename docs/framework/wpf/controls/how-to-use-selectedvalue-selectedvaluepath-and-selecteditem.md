---
title: HOW TO：使用 SelectedValue、SelectedValuePath 和 SelectedItem
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
ms.openlocfilehash: d9f7a8f04f53b7d38a49dfef2c947dfa1c2d263d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169698"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>HOW TO：使用 SelectedValue、SelectedValuePath 和 SelectedItem
此範例示範如何使用<xref:System.Windows.Controls.TreeView.SelectedValue%2A>並<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性，以指定的值<xref:System.Windows.Controls.TreeView.SelectedItem%2A>的<xref:System.Windows.Controls.TreeView>。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性會提供方法來指定<xref:System.Windows.Controls.TreeView.SelectedValue%2A>for<xref:System.Windows.Controls.TreeView.SelectedItem%2A>在<xref:System.Windows.Controls.TreeView>。 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>表示中的物件<xref:System.Windows.Controls.ItemsControl.Items%2A>集合和<xref:System.Windows.Controls.TreeView>顯示選取項目的單一屬性的值。 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性會指定用來判斷的值屬性的路徑<xref:System.Windows.Controls.TreeView.SelectedValue%2A>屬性。 本主題中的範例將說明這個概念。  
  
 下列範例所示<xref:System.Windows.Data.XmlDataProvider>包含員工資訊。  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 下列範例會定義<xref:System.Windows.HierarchicalDataTemplate>會顯示`EmployeeName`並`EmployeeWorkDay`的`Employee`。 請注意，<xref:System.Windows.HierarchicalDataTemplate>未指定`EmployeeNumber`為範本的一部分。  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 下列範例所示<xref:System.Windows.Controls.TreeView>使用先前定義<xref:System.Windows.HierarchicalDataTemplate>，並可設定<xref:System.Windows.Controls.TreeView.SelectedValue%2A>屬性設`EmployeeNumber`。 當您選取`EmployeeName`中<xref:System.Windows.Controls.TreeView>，則<xref:System.Windows.Controls.TreeView.SelectedItem%2A>屬性會傳回`EmployeeInfo`對應至所選的資料項目`EmployeeName`。 不過，因為<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>這個<xref:System.Windows.Controls.TreeView>設為`EmployeeNumber`，則<xref:System.Windows.Controls.TreeView.SelectedValue%2A>設定為`EmployeeNumber`。  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [TreeView 概觀](treeview-overview.md)
- [HOW TO 主題](treeview-how-to-topics.md)
