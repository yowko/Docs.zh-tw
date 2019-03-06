---
title: HOW TO：將命令與沒有命令支援的控制項連結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
ms.openlocfilehash: 66b371f4d67c1102ddf341dd4b70aac66aa41605
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352668"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>HOW TO：將命令與沒有命令支援的控制項連結
下列範例示範如何將 <xref:System.Windows.Input.RoutedCommand> 與沒有命令內建支援的 <xref:System.Windows.Controls.Control> 連結。  如需將命令連結至多個來源的完整範例，請參閱[建立自訂的 RoutedCommand 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)範例。  
  
## <a name="example"></a>範例  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供應用程式設計人員經常遇到之常見命令的程式庫。  命令程式庫包含的類別如下：<xref:System.Windows.Input.ApplicationCommands>、<xref:System.Windows.Input.ComponentCommands>、<xref:System.Windows.Input.NavigationCommands>、<xref:System.Windows.Input.MediaCommands> 和 <xref:System.Windows.Documents.EditingCommands>。  
  
 構成這些類別的靜態 <xref:System.Windows.Input.RoutedCommand> 物件不提供命令邏輯。  此命令的邏輯會與具有 <xref:System.Windows.Input.CommandBinding> 的命令建立關聯。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的許多控制項都有命令程式庫中一些命令的內建支援。  比方說，<xref:System.Windows.Controls.TextBox> 支援許多應用程式編輯命令，例如<xref:System.Windows.Input.ApplicationCommands.Paste%2A>、<xref:System.Windows.Input.ApplicationCommands.Copy%2A>、<xref:System.Windows.Input.ApplicationCommands.Cut%2A>、<xref:System.Windows.Input.ApplicationCommands.Redo%2A> 和 <xref:System.Windows.Input.ApplicationCommands.Undo%2A>。  應用程式開發人員不需要特別執行任何作業，即可取得這些命令來使用這些控制項。  如果 <xref:System.Windows.Controls.TextBox> 在執行命令時是命令目標，它將使用控制項內建的 <xref:System.Windows.Input.CommandBinding> 來處理命令。  
  
 下列範例示範如何使用 <xref:System.Windows.Controls.Button> 作為 <xref:System.Windows.Input.ApplicationCommands.Open%2A> 命令的命令來源。  會建立一個 <xref:System.Windows.Input.CommandBinding>，將指定的 <xref:System.Windows.Input.CanExecuteRoutedEventHandler> 和 <xref:System.Windows.Input.CanExecuteRoutedEventHandler> 與 <xref:System.Windows.Input.RoutedCommand> 建立關聯。  
  
 首先，會建立命令來源。  將使用 <xref:System.Windows.Controls.Button> 作為命令來源。  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 接下來，會建立 <xref:System.Windows.Input.ExecutedRoutedEventHandler> 和 <xref:System.Windows.Input.CanExecuteRoutedEventHandler>。  <xref:System.Windows.Input.ExecutedRoutedEventHandler> 只會開啟 <xref:System.Windows.MessageBox> 來表示已執行命令。  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> 會將 <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> 屬性設定為 `true`。  一般來說，可以執行處理常式會執行更穩固的檢查，以查看命令是否無法在目前命令目標上執行。  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 最後，會在應用程式的根 <xref:System.Windows.Window> 上建立 <xref:System.Windows.Input.CommandBinding>，將路由的事件處理常式與 <xref:System.Windows.Input.ApplicationCommands.Open%2A> 命令建立關聯。  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>另請參閱
- [命令概觀](commanding-overview.md)
- [將命令與含有命令支援的控制項連結](how-to-hook-up-a-command-to-a-control-with-command-support.md)
