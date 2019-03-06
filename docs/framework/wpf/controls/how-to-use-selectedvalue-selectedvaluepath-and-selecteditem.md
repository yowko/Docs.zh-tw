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
ms.openlocfilehash: e3f4e5e6a51426581082ab24a1c3a962e38846bd
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373825"
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
- [HOW-TO 主題](treeview-how-to-topics.md)
