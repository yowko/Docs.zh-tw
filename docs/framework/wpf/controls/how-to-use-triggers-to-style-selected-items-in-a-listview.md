---
title: 操作說明：使用觸發程序來設定 ListView 中所選項目的樣式
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
ms.openlocfilehash: 1741ce84fab1639409a7c834845573239c51cc35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a>操作說明：使用觸發程序來設定 ListView 中所選項目的樣式
這個範例示範如何定義<xref:System.Windows.Style.Triggers%2A>如<xref:System.Windows.Controls.ListViewItem>控制項，讓屬性值時<xref:System.Windows.Controls.ListViewItem>變更，<xref:System.Windows.Style>的<xref:System.Windows.Controls.ListViewItem>回應中的變更。  
  
## <a name="example"></a>範例  
 如果您想<xref:System.Windows.Style>的<xref:System.Windows.Controls.ListViewItem>若要變更以回應變更屬性，定義<xref:System.Windows.Style.Triggers%2A>如<xref:System.Windows.Style>變更。  
  
 下列範例會定義<xref:System.Windows.Trigger>設定<xref:System.Windows.Controls.Control.Foreground%2A>屬性<xref:System.Windows.Media.Brushes.Blue%2A>並變更<xref:System.Windows.FrameworkElement.Cursor%2A>顯示<xref:System.Windows.Input.CursorType.Hand>時<xref:System.Windows.UIElement.IsMouseOver%2A>屬性變更為`true`。  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 下列範例會定義<xref:System.Windows.MultiTrigger>設定<xref:System.Windows.Controls.Control.Foreground%2A>屬性<xref:System.Windows.Controls.ListViewItem>至<xref:System.Windows.Media.Brushes.Yellow%2A>時<xref:System.Windows.Controls.ListViewItem>是選取的項目，並具有鍵盤焦點。  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)
