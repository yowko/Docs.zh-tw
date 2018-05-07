---
title: 如何：將命令與沒有命令支援的控制項連結
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
ms.openlocfilehash: 4dd4f4acc3a4a944411c0b39ef91fcd12a4cf5b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>如何：將命令與沒有命令支援的控制項連結
下列範例示範如何連接<xref:System.Windows.Input.RoutedCommand>至<xref:System.Windows.Controls.Control>這不會不具有內建支援命令。  如需將命令連結至多個來源的完整範例，請參閱[建立自訂的 RoutedCommand 範例](http://go.microsoft.com/fwlink/?LinkID=159980)範例。  
  
## <a name="example"></a>範例  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供應用程式設計人員經常遇到之常見命令的程式庫。  構成命令程式庫的類別： <xref:System.Windows.Input.ApplicationCommands>， <xref:System.Windows.Input.ComponentCommands>， <xref:System.Windows.Input.NavigationCommands>， <xref:System.Windows.Input.MediaCommands>，和<xref:System.Windows.Documents.EditingCommands>。  
  
 靜態<xref:System.Windows.Input.RoutedCommand>組成這些類別的物件不提供命令的邏輯。  此命令的邏輯是與命令相關聯<xref:System.Windows.Input.CommandBinding>。  中的許多控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]有內建支援某些命令程式庫中的命令。  <xref:System.Windows.Controls.TextBox>例如，支援的許多應用程式編輯命令，例如<xref:System.Windows.Input.ApplicationCommands.Paste%2A>， <xref:System.Windows.Input.ApplicationCommands.Copy%2A>， <xref:System.Windows.Input.ApplicationCommands.Cut%2A>， <xref:System.Windows.Input.ApplicationCommands.Redo%2A>，和<xref:System.Windows.Input.ApplicationCommands.Undo%2A>。  應用程式開發人員不需要特別執行任何作業，即可取得這些命令來使用這些控制項。  如果<xref:System.Windows.Controls.TextBox>是命令目標執行命令時，它將處理命令使用<xref:System.Windows.Input.CommandBinding>內建控制項。  
  
 下列範例示範如何使用<xref:System.Windows.Controls.Button>做為命令來源<xref:System.Windows.Input.ApplicationCommands.Open%2A>命令。  A<xref:System.Windows.Input.CommandBinding>會建立指定該關聯<xref:System.Windows.Input.CanExecuteRoutedEventHandler>和<xref:System.Windows.Input.CanExecuteRoutedEventHandler>與<xref:System.Windows.Input.RoutedCommand>。  
  
 首先，會建立命令來源。  A<xref:System.Windows.Controls.Button>做為命令來源。  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 下一步<xref:System.Windows.Input.ExecutedRoutedEventHandler>和<xref:System.Windows.Input.CanExecuteRoutedEventHandler>所建立。  <xref:System.Windows.Input.ExecutedRoutedEventHandler>只需開啟<xref:System.Windows.MessageBox>以表示執行的命令。  <xref:System.Windows.Input.CanExecuteRoutedEventHandler>設定<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A>屬性`true`。  一般來說，則可以執行處理常式會執行更穩固的檢查，若要查看是否命令無法在目前命令目標上執行。  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 最後，<xref:System.Windows.Input.CommandBinding>根目錄上建立<xref:System.Windows.Window>應用程式相關聯的路由的事件處理常式的<xref:System.Windows.Input.ApplicationCommands.Open%2A>命令。  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>另請參閱  
 [命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [將命令與含有命令支援的控制項連結](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)
