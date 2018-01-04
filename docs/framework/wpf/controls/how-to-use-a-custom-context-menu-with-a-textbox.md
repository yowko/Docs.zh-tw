---
title: "如何：在文字方塊使用自訂內容功能表"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4552031a08680af2f4d41702d2f76ed0c44af21b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a>如何：在文字方塊使用自訂內容功能表
這個範例示範如何定義及實作簡單的自訂內容功能表<xref:System.Windows.Controls.TextBox>。  
  
## <a name="example"></a>範例  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例會定義<xref:System.Windows.Controls.TextBox>包含自訂內容功能表控制項。  
  
 使用定義的內容功能表<xref:System.Windows.Controls.ContextMenu>項目。  內容功能表本身包含的一系列<xref:System.Windows.Controls.MenuItem>項目和<xref:System.Windows.Controls.Separator>項目。  每個<xref:System.Windows.Controls.MenuItem>項目定義命令的內容功能表;<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>屬性會定義功能表命令的顯示文字和<xref:System.Windows.Controls.MenuItem.Click>屬性會指定每個功能表項目的處理常式方法。  <xref:System.Windows.Controls.Separator>項目只會導致要呈現的上一個與後續的功能表項目之間的分隔列。  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a>範例  
 下列範例會示範實作程式碼，如前述內容功能表的定義，以及啟用和停用操作功能表的程式碼。  <xref:System.Windows.Controls.ContextMenu.Opened>事件用來動態啟用或停用特定命令，根據目前的狀態<xref:System.Windows.Controls.TextBox>。  
  
 若要還原預設的內容功能表，請使用<xref:System.Windows.DependencyObject.ClearValue%2A>方法，以清除的值<xref:System.Windows.FrameworkElement.ContextMenu%2A>屬性。  若要完全停用操作功能表，請設定<xref:System.Windows.FrameworkElement.ContextMenu%2A>屬性為 null 參考 (`Nothing`在 Visual Basic 中)。  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a>請參閱  
 [使用內容功能表的拼字檢查](../../../../docs/framework/wpf/controls/how-to-use-spell-checking-with-a-context-menu.md)  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
