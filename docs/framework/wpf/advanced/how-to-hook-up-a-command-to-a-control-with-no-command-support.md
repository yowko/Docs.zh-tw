---
title: "如何：將命令與沒有命令支援的控制項連結"
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
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 804c4ffd54a0f8cc94e8849a223b1af8b27a58b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a><span data-ttu-id="42c97-102">如何：將命令與沒有命令支援的控制項連結</span><span class="sxs-lookup"><span data-stu-id="42c97-102">How to: Hook Up a Command to a Control with No Command Support</span></span>
<span data-ttu-id="42c97-103">下列範例示範如何連接<xref:System.Windows.Input.RoutedCommand>至<xref:System.Windows.Controls.Control>這不會不具有內建支援命令。</span><span class="sxs-lookup"><span data-stu-id="42c97-103">The following example shows how to hook up a <xref:System.Windows.Input.RoutedCommand> to a <xref:System.Windows.Controls.Control> which does not have built in support for the command.</span></span>  <span data-ttu-id="42c97-104">如需將命令連結至多個來源的完整範例，請參閱[建立自訂的 RoutedCommand 範例](http://go.microsoft.com/fwlink/?LinkID=159980)範例。</span><span class="sxs-lookup"><span data-stu-id="42c97-104">For a complete sample which hooks up commands to multiple sources, see the [Create a Custom RoutedCommand Sample](http://go.microsoft.com/fwlink/?LinkID=159980) sample.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42c97-105">範例</span><span class="sxs-lookup"><span data-stu-id="42c97-105">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="42c97-106"> 提供應用程式設計人員經常遇到之常見命令的程式庫。</span><span class="sxs-lookup"><span data-stu-id="42c97-106"> provides a library of common commands which application programmers encounter regularly.</span></span>  <span data-ttu-id="42c97-107">構成命令程式庫的類別： <xref:System.Windows.Input.ApplicationCommands>， <xref:System.Windows.Input.ComponentCommands>， <xref:System.Windows.Input.NavigationCommands>， <xref:System.Windows.Input.MediaCommands>，和<xref:System.Windows.Documents.EditingCommands>。</span><span class="sxs-lookup"><span data-stu-id="42c97-107">The classes which comprise the command library are: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, and <xref:System.Windows.Documents.EditingCommands>.</span></span>  
  
 <span data-ttu-id="42c97-108">靜態<xref:System.Windows.Input.RoutedCommand>組成這些類別的物件不提供命令的邏輯。</span><span class="sxs-lookup"><span data-stu-id="42c97-108">The static <xref:System.Windows.Input.RoutedCommand> objects which make up these classes do not supply command logic.</span></span>  <span data-ttu-id="42c97-109">此命令的邏輯是與命令相關聯<xref:System.Windows.Input.CommandBinding>。</span><span class="sxs-lookup"><span data-stu-id="42c97-109">The logic for the command is associated with the command with a <xref:System.Windows.Input.CommandBinding>.</span></span>  <span data-ttu-id="42c97-110">中的許多控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]有內建支援某些命令程式庫中的命令。</span><span class="sxs-lookup"><span data-stu-id="42c97-110">Many controls in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] have built in support for some of the commands in the command library.</span></span>  <span data-ttu-id="42c97-111"><xref:System.Windows.Controls.TextBox>例如，支援的許多應用程式編輯命令，例如<xref:System.Windows.Input.ApplicationCommands.Paste%2A>， <xref:System.Windows.Input.ApplicationCommands.Copy%2A>， <xref:System.Windows.Input.ApplicationCommands.Cut%2A>， <xref:System.Windows.Input.ApplicationCommands.Redo%2A>，和<xref:System.Windows.Input.ApplicationCommands.Undo%2A>。</span><span class="sxs-lookup"><span data-stu-id="42c97-111"><xref:System.Windows.Controls.TextBox>, for example, supports many of the application edit commands such as <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, and <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.</span></span>  <span data-ttu-id="42c97-112">應用程式開發人員不需要特別執行任何作業，即可取得這些命令來使用這些控制項。</span><span class="sxs-lookup"><span data-stu-id="42c97-112">The application developer does not have to do anything special to get these commands to work with these controls.</span></span>  <span data-ttu-id="42c97-113">如果<xref:System.Windows.Controls.TextBox>是命令目標執行命令時，它將處理命令使用<xref:System.Windows.Input.CommandBinding>內建控制項。</span><span class="sxs-lookup"><span data-stu-id="42c97-113">If the <xref:System.Windows.Controls.TextBox> is the command target when the command is executed, it will handle the command using the <xref:System.Windows.Input.CommandBinding> that is built into the control.</span></span>  
  
 <span data-ttu-id="42c97-114">下列範例示範如何使用<xref:System.Windows.Controls.Button>做為命令來源<xref:System.Windows.Input.ApplicationCommands.Open%2A>命令。</span><span class="sxs-lookup"><span data-stu-id="42c97-114">The following shows how to use a <xref:System.Windows.Controls.Button> as the command source for the <xref:System.Windows.Input.ApplicationCommands.Open%2A> command.</span></span>  <span data-ttu-id="42c97-115">A<xref:System.Windows.Input.CommandBinding>會建立指定該關聯<xref:System.Windows.Input.CanExecuteRoutedEventHandler>和<xref:System.Windows.Input.CanExecuteRoutedEventHandler>與<xref:System.Windows.Input.RoutedCommand>。</span><span class="sxs-lookup"><span data-stu-id="42c97-115">A <xref:System.Windows.Input.CommandBinding> is created that associates the specified <xref:System.Windows.Input.CanExecuteRoutedEventHandler> and the <xref:System.Windows.Input.CanExecuteRoutedEventHandler> with the <xref:System.Windows.Input.RoutedCommand>.</span></span>  
  
 <span data-ttu-id="42c97-116">首先，會建立命令來源。</span><span class="sxs-lookup"><span data-stu-id="42c97-116">First, the command source is created.</span></span>  <span data-ttu-id="42c97-117">A<xref:System.Windows.Controls.Button>做為命令來源。</span><span class="sxs-lookup"><span data-stu-id="42c97-117">A <xref:System.Windows.Controls.Button> is used as the command source.</span></span>  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 <span data-ttu-id="42c97-118">下一步<xref:System.Windows.Input.ExecutedRoutedEventHandler>和<xref:System.Windows.Input.CanExecuteRoutedEventHandler>所建立。</span><span class="sxs-lookup"><span data-stu-id="42c97-118">Next, the <xref:System.Windows.Input.ExecutedRoutedEventHandler> and the <xref:System.Windows.Input.CanExecuteRoutedEventHandler> are created.</span></span>  <span data-ttu-id="42c97-119"><xref:System.Windows.Input.ExecutedRoutedEventHandler>只需開啟<xref:System.Windows.MessageBox>以表示執行的命令。</span><span class="sxs-lookup"><span data-stu-id="42c97-119">The <xref:System.Windows.Input.ExecutedRoutedEventHandler> simply opens a <xref:System.Windows.MessageBox> to signify that the command executed.</span></span>  <span data-ttu-id="42c97-120"><xref:System.Windows.Input.CanExecuteRoutedEventHandler>設定<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="42c97-120">The <xref:System.Windows.Input.CanExecuteRoutedEventHandler> sets the <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> property to `true`.</span></span>  <span data-ttu-id="42c97-121">一般來說，則可以執行處理常式會執行更穩固的檢查，若要查看是否命令無法在目前命令目標上執行。</span><span class="sxs-lookup"><span data-stu-id="42c97-121">Normally, the can execute handler would perform more robust checks to see if the command could execute on the current command target.</span></span>  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 <span data-ttu-id="42c97-122">最後，<xref:System.Windows.Input.CommandBinding>根目錄上建立<xref:System.Windows.Window>應用程式相關聯的路由的事件處理常式的<xref:System.Windows.Input.ApplicationCommands.Open%2A>命令。</span><span class="sxs-lookup"><span data-stu-id="42c97-122">Finally, a <xref:System.Windows.Input.CommandBinding> is created on the root <xref:System.Windows.Window> of the application that associates the routed events handlers to the <xref:System.Windows.Input.ApplicationCommands.Open%2A> command.</span></span>  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a><span data-ttu-id="42c97-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="42c97-123">See Also</span></span>  
 [<span data-ttu-id="42c97-124">命令概觀</span><span class="sxs-lookup"><span data-stu-id="42c97-124">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [<span data-ttu-id="42c97-125">將命令與含有命令支援的控制項連結</span><span class="sxs-lookup"><span data-stu-id="42c97-125">Hook Up a Command to a Control with Command Support</span></span>](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)
