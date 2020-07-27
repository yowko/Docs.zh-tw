---
title: 如何：使用 SelectedValue、SelectedValuePath 和 SelectedItem
description: 瞭解如何使用 SelectedValue 和 SelectedValuePath 屬性，為 Windows Presentation Foundation TreeView 的 SelectedItem 指定值。
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
ms.openlocfilehash: ddac2455dee0bf69d25307340eddd5364e43e823
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166276"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>如何：使用 SelectedValue、SelectedValuePath 和 SelectedItem
這個範例會示範如何使用 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 和 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 屬性來指定 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 的值 <xref:System.Windows.Controls.TreeView> 。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性提供一種方法，可為 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 中的指定 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> 。 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>表示集合中的物件 <xref:System.Windows.Controls.ItemsControl.Items%2A> ，而則會 <xref:System.Windows.Controls.TreeView> 顯示所選取專案的單一屬性值。 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性會指定用來判斷屬性值的屬性路徑 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 。 本主題中的範例將說明此概念。  
  
 下列範例 <xref:System.Windows.Data.XmlDataProvider> 會顯示包含員工資訊的。  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 下列範例 <xref:System.Windows.HierarchicalDataTemplate> 會定義，其會顯示的 `EmployeeName` 和 `EmployeeWorkDay` `Employee` 。 請注意， <xref:System.Windows.HierarchicalDataTemplate> 不會將指定 `EmployeeNumber` 為範本的一部分。  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 下列範例 <xref:System.Windows.Controls.TreeView> 會顯示，其使用先前定義的 <xref:System.Windows.HierarchicalDataTemplate> ，並將 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 屬性設定為 `EmployeeNumber` 。 當您選取 `EmployeeName` 中的時 <xref:System.Windows.Controls.TreeView> ， <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 屬性會傳回對應于 `EmployeeInfo` 所選取的資料項目 `EmployeeName` 。 不過，由於 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 這個的 <xref:System.Windows.Controls.TreeView> 是設定為 `EmployeeNumber` ，因此 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 會設定為 `EmployeeNumber` 。  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [TreeView 概觀](treeview-overview.md)
- [操作說明主題](treeview-how-to-topics.md)
