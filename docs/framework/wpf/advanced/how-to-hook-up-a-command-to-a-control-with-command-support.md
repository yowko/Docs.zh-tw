---
title: HOW TO：將命令連結到有命令支援的控制項
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
ms.openlocfilehash: 981fecf33b60c76ecab760185db7dab4bbb254d7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165200"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-command-support"></a>HOW TO：將命令連結到有命令支援的控制項
下列範例示範如何將 <xref:System.Windows.Input.RoutedCommand> 與含有命令內建支援的 <xref:System.Windows.Controls.Control> 連結。  如需將命令連結至多個來源的完整範例，請參閱[建立自訂的 RoutedCommand 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)範例。  
  
## <a name="example"></a>範例  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供應用程式的程式設計人員經常遇到的常見命令程式的庫。  命令程式庫包含的類別如下：<xref:System.Windows.Input.ApplicationCommands>、<xref:System.Windows.Input.ComponentCommands>、<xref:System.Windows.Input.NavigationCommands>、<xref:System.Windows.Input.MediaCommands> 和 <xref:System.Windows.Documents.EditingCommands>。  
  
 構成這些類別的靜態 <xref:System.Windows.Input.RoutedCommand> 物件不提供命令邏輯。  此命令的邏輯會與具有 <xref:System.Windows.Input.CommandBinding> 的命令建立關聯。  有些控制項具有某些命令的內建 CommandBindings。  此機制允許命令的語意保持不變，但實際實作可以變更。  例如，<xref:System.Windows.Controls.TextBox> 處理 <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令的方式與設計成支援映像的控制項不同，但貼上某個項目所代表之意義的基本概念維持不變。  命令無法提供命令邏輯，而是必須由控制項或應用程式提供。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的許多控制項都有命令程式庫中一些命令的內建支援。  <xref:System.Windows.Controls.TextBox>例如，支援許多應用程式編輯命令，例如<xref:System.Windows.Input.ApplicationCommands.Paste%2A>， <xref:System.Windows.Input.ApplicationCommands.Copy%2A>， <xref:System.Windows.Input.ApplicationCommands.Cut%2A>， <xref:System.Windows.Input.ApplicationCommands.Redo%2A>，和<xref:System.Windows.Input.ApplicationCommands.Undo%2A>。  應用程式開發人員不需要特別執行任何作業，即可取得這些命令來使用這些控制項。  如果 <xref:System.Windows.Controls.TextBox> 在執行命令時是命令目標，它將使用控制項內建的 <xref:System.Windows.Input.CommandBinding> 來處理命令。  
  
 下列範例示範如何使用 <xref:System.Windows.Controls.MenuItem> 作為 <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令的命令來源，其中 <xref:System.Windows.Controls.TextBox> 是命令的目標。  <xref:System.Windows.Controls.TextBox> 控制項中內建定義 <xref:System.Windows.Controls.TextBox> 如何執行貼上的所有邏輯。  
  
 將會建立 <xref:System.Windows.Controls.MenuItem>，且其 <xref:System.Windows.Controls.MenuItem.Command%2A> 屬性會設定為 <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令。  <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> 不會明確地設定為 <xref:System.Windows.Controls.TextBox> 物件。  未設定 <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> 時，命令的目標是具有鍵盤焦點的元素。  如果具有鍵盤焦點的元素不支援 <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令，或目前無法執行貼上命令 (例如，剪貼簿是空的)，<xref:System.Windows.Controls.MenuItem> 就會變成灰色。  
  
 [!code-xaml[MenuItemCommandTask_XAML#MenuItemCommanding](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask_XAML/CS/Window1.xaml#menuitemcommanding)]  
  
 [!code-csharp[MenuItemCommandTask#MenuItemCommandingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask/CSharp/Window1.xaml.cs#menuitemcommandingcodebehind)]
 [!code-vb[MenuItemCommandTask#MenuItemCommandingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandTask/VisualBasic/Window1.xaml.vb#menuitemcommandingcodebehind)]  
  
## <a name="see-also"></a>另請參閱

- [命令概觀](commanding-overview.md)
- [將命令連結到沒有命令支援的控制項](how-to-hook-up-a-command-to-a-control-with-no-command-support.md)
