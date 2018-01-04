---
title: "如何：使用 SelectedValue、SelectedValuePath 和 SelectedItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6355ed45d7422735d1dac1e1419990e1c5bd120
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>如何：使用 SelectedValue、SelectedValuePath 和 SelectedItem
這個範例示範如何使用<xref:System.Windows.Controls.TreeView.SelectedValue%2A>和<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性，以指定的值<xref:System.Windows.Controls.TreeView.SelectedItem%2A>的<xref:System.Windows.Controls.TreeView>。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性會提供方法來指定<xref:System.Windows.Controls.TreeView.SelectedValue%2A>如<xref:System.Windows.Controls.TreeView.SelectedItem%2A>中<xref:System.Windows.Controls.TreeView>。 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>代表中的物件<xref:System.Windows.Controls.ItemsControl.Items%2A>集合和<xref:System.Windows.Controls.TreeView>顯示選取之項目的單一屬性的值。 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性會指定用來判斷值的屬性路徑<xref:System.Windows.Controls.TreeView.SelectedValue%2A>屬性。 本主題中的範例說明此概念。  
  
 下列範例所示<xref:System.Windows.Data.XmlDataProvider>包含員工資訊。  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 下列範例會定義<xref:System.Windows.HierarchicalDataTemplate>顯示`EmployeeName`和`EmployeeWorkDay`的`Employee`。 請注意，<xref:System.Windows.HierarchicalDataTemplate>未指定`EmployeeNumber`做為範本的一部分。  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 下列範例所示<xref:System.Windows.Controls.TreeView>使用先前定義<xref:System.Windows.HierarchicalDataTemplate>和設定<xref:System.Windows.Controls.TreeView.SelectedValue%2A>屬性`EmployeeNumber`。 當您選取`EmployeeName`中<xref:System.Windows.Controls.TreeView>、<xref:System.Windows.Controls.TreeView.SelectedItem%2A>屬性會傳回`EmployeeInfo`對應於所選的資料項目`EmployeeName`。 不過，因為<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>這個<xref:System.Windows.Controls.TreeView>設`EmployeeNumber`、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>設`EmployeeNumber`。  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [TreeView 概觀](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
