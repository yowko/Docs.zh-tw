---
title: 如何：將命令與含有命令支援的控制項連結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: 8d8592ae-0c91-469e-a1cd-d179c4544548
ms.openlocfilehash: 47abd36558864116e5f5ed921419c374c064e2cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hook-up-a-command-to-a-control-with-command-support"></a>如何：將命令與含有命令支援的控制項連結
下列範例示範如何連接<xref:System.Windows.Input.RoutedCommand>至<xref:System.Windows.Controls.Control>其中具有內建命令的支援。  如需將命令連結至多個來源的完整範例，請參閱[建立自訂的 RoutedCommand 範例](http://go.microsoft.com/fwlink/?LinkID=159980)範例。  
  
## <a name="example"></a>範例  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供應用程式設計人員經常遇到之常見命令的程式庫。  構成命令程式庫的類別： <xref:System.Windows.Input.ApplicationCommands>， <xref:System.Windows.Input.ComponentCommands>， <xref:System.Windows.Input.NavigationCommands>， <xref:System.Windows.Input.MediaCommands>，和<xref:System.Windows.Documents.EditingCommands>。  
  
 靜態<xref:System.Windows.Input.RoutedCommand>組成這些類別的物件不提供命令的邏輯。  此命令的邏輯是與命令相關聯<xref:System.Windows.Input.CommandBinding>。  有些控制項具有某些命令的內建 CommandBindings。  此機制允許命令的語意保持不變，但實際實作可以變更。  A <xref:System.Windows.Controls.TextBox>，例如，處理<xref:System.Windows.Input.ApplicationCommands.Paste%2A>命令以不同的方式，控制項用來支援映像，但是它所代表的項目貼上的基本概念都保持不變。  命令無法提供命令邏輯，而是必須由控制項或應用程式提供。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的許多控制項都有命令程式庫中一些命令的內建支援。  <xref:System.Windows.Controls.TextBox>例如，支援的許多應用程式編輯命令，例如<xref:System.Windows.Input.ApplicationCommands.Paste%2A>， <xref:System.Windows.Input.ApplicationCommands.Copy%2A>， <xref:System.Windows.Input.ApplicationCommands.Cut%2A>， <xref:System.Windows.Input.ApplicationCommands.Redo%2A>，和<xref:System.Windows.Input.ApplicationCommands.Undo%2A>。  應用程式開發人員不需要特別執行任何作業，即可取得這些命令來使用這些控制項。  如果<xref:System.Windows.Controls.TextBox>是命令目標執行命令時，它將處理命令使用<xref:System.Windows.Input.CommandBinding>內建控制項。  
  
 下列範例示範如何使用<xref:System.Windows.Controls.MenuItem>做為命令來源<xref:System.Windows.Input.ApplicationCommands.Paste%2A>命令，其中<xref:System.Windows.Controls.TextBox>做為目標的命令。  定義的所有邏輯如何<xref:System.Windows.Controls.TextBox>執行貼上內建<xref:System.Windows.Controls.TextBox>控制項。  
  
 A<xref:System.Windows.Controls.MenuItem>建立，而且<xref:System.Windows.Controls.MenuItem.Command%2A>屬性設定為<xref:System.Windows.Input.ApplicationCommands.Paste%2A>命令。  <xref:System.Windows.Controls.MenuItem.CommandTarget%2A>未明確設定為<xref:System.Windows.Controls.TextBox>物件。  當<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>未設定時，目標的命令具有鍵盤焦點的項目。  如果具有鍵盤焦點的元素不支援<xref:System.Windows.Input.ApplicationCommands.Paste%2A>命令，或目前無法執行貼上 命令 （剪貼簿是空的比方說） 則<xref:System.Windows.Controls.MenuItem>就會變成灰色。  
  
 [!code-xaml[MenuItemCommandTask_XAML#MenuItemCommanding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask_XAML/CS/Window1.xaml#menuitemcommanding)]  
  
 [!code-csharp[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask/CSharp/Window1.xaml.cs#menuitemcommandingcodebehind)]
 [!code-vb[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandTask/VisualBasic/Window1.xaml.vb#menuitemcommandingcodebehind)]  
  
## <a name="see-also"></a>另請參閱  
 [命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [將命令與沒有命令支援的控制項連結](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-no-command-support.md)
