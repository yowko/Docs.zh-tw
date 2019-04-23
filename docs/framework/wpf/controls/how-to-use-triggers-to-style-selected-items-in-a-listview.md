---
title: HOW TO：使用觸發程序為 ListView 中的選取項目設定樣式
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
ms.openlocfilehash: ad64382b871bae9114a1e63257de3f8595376923
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145401"
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a>HOW TO：使用觸發程序為 ListView 中的選取項目設定樣式
此範例示範如何定義<xref:System.Windows.Style.Triggers%2A>for<xref:System.Windows.Controls.ListViewItem>控制項，讓屬性值時<xref:System.Windows.Controls.ListViewItem>變更，<xref:System.Windows.Style>的<xref:System.Windows.Controls.ListViewItem>回應中的變更。  
  
## <a name="example"></a>範例  
 如果您想<xref:System.Windows.Style>的<xref:System.Windows.Controls.ListViewItem>若要變更以回應變更屬性，定義<xref:System.Windows.Style.Triggers%2A>如<xref:System.Windows.Style>變更。  
  
 下列範例會定義<xref:System.Windows.Trigger>，設定<xref:System.Windows.Controls.Control.Foreground%2A>屬性設<xref:System.Windows.Media.Brushes.Blue%2A>，並變更<xref:System.Windows.FrameworkElement.Cursor%2A>以顯示<xref:System.Windows.Input.CursorType.Hand>當<xref:System.Windows.UIElement.IsMouseOver%2A>屬性變更為`true`。  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 下列範例會定義<xref:System.Windows.MultiTrigger>，設定<xref:System.Windows.Controls.Control.Foreground%2A>屬性<xref:System.Windows.Controls.ListViewItem>要<xref:System.Windows.Media.Brushes.Yellow%2A>當<xref:System.Windows.Controls.ListViewItem>是選取的項目，並具有鍵盤焦點。  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [HOW-TO 主題](listview-how-to-topics.md)
- [ListView 概觀](listview-overview.md)
- [GridView 概觀](gridview-overview.md)
