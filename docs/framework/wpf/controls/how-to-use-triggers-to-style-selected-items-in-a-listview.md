---
title: "操作說明：使用觸發程序來設定 ListView 中所選項目的樣式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e86c7f875376a4ab28eec7cd032a165745445441
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
 [操作說明主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)
