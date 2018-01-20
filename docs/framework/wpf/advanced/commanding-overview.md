---
title: "命令概觀"
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
- interfaces [WPF], ICommandSource
- command library [WPF]
- commands [WPF], definition of
- CommandBindings [WPF]
- ICommandSource interfaces [WPF]
- commanding [WPF]
- CommandManager [WPF]
ms.assetid: bc208dfe-367d-426a-99de-52b7e7511e81
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3eb7d05cdf5f6a80a0a247a5f429052cc9a8368b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="commanding-overview"></a>命令概觀
<a name="introduction"></a> 命令是處理比裝置輸入更接近語意層級的 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的輸入機制。 命令範例包含許多應用程式中都有的 [複製]、[剪下] 和 [貼上] 作業。  
  
 本概觀會定義 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中有哪些命令、哪些類別屬於命令模型，以及如何在應用程式中使用及建立命令。  
  
 此主題包括下列章節：  
  
-   [命令是什麼？](#commands_at_10000_feet)  
  
-   [WPF 中的簡單命令範例](#simple_command)  
  
-   [WPF 命令的四個主要概念](#Four_main_Concepts)  
  
-   [命令程式庫](#Command_Library)  
  
-   [建立自訂命令](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## <a name="what-are-commands"></a>命令是什麼？  
 命令有多種用途。 第一個用途是要分隔語意和從執行命令的邏輯叫用命令的物件。 這可讓多個不同的來源叫用相同的命令邏輯，並可針對不同的目標自訂命令邏輯。 例如，許多應用程式中都有的 [複製]、[剪下] 和 [貼上] 等編輯作業；如果使用命令實作，即可使用不同的使用者動作叫用。 應用程式可能會讓使用者按一下按鈕、選擇功能表中的項目，或使用 CTRL+X 等按鍵組合，剪下選取的物件或文字。 您可以使用命令將每一種使用者動作類型繫結至相同的邏輯。  
  
 命令的另一項用途是指出是否有動作可用。 若要繼續剪下物件或文字的範例，只有選取項目時動作才有意義。 如果使用者嘗試剪下物件或文字，但未選取任何項目，不會有任何事發生。 為向使用者指出這個狀況，許多應用程式會停用按鈕和功能表項目，讓使用者知道是否能執行某動作。 命令可以指出動作是否可以藉由實作<xref:System.Windows.Input.ICommand.CanExecute%2A>方法。 按鈕可以訂閱<xref:System.Windows.Input.ICommand.CanExecuteChanged>事件，而且如果停用<xref:System.Windows.Input.ICommand.CanExecute%2A>傳回`false`或如果啟用<xref:System.Windows.Input.ICommand.CanExecute%2A>傳回`true`。  
  
 命令語意在不同的應用程式和類別中可以一致，但動作邏輯專屬於於其上執行動作的特定物件。 按鍵組合 CTRL+X 在文字類別、映像類別及網頁瀏覽器中叫用 [剪下] 命令，但執行 [剪下] 作業的實際邏輯是由執行剪下動作的應用程式所定義。 A<xref:System.Windows.Input.RoutedCommand>可讓用戶端實作的邏輯。 文字物件可能會將選取的文字剪入剪貼簿，而映像物件可能會剪下選取的映像。 當應用程式處理<xref:System.Windows.Input.CommandManager.Executed>事件，它可以存取的命令目標，而且可以採取適當的動作，取決於目標的類型。  
  
<a name="simple_command"></a>   
## <a name="simple-command-example-in-wpf"></a>WPF 中的簡單命令範例  
 最簡單的方式使用中的命令[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是使用預先定義<xref:System.Windows.Input.RoutedCommand>從其中一個命令程式庫類別; 使用處理命令; 原生支援的控制項，並使用叫用命令的原生支援的控制項。  <xref:System.Windows.Input.ApplicationCommands.Paste%2A>命令是其中一個預先定義的命令在<xref:System.Windows.Input.ApplicationCommands>類別。  <xref:System.Windows.Controls.TextBox>控制項具有內建邏輯來處理<xref:System.Windows.Input.ApplicationCommands.Paste%2A>命令。  和<xref:System.Windows.Controls.MenuItem>類別具有叫用命令的原生支援。  
  
 下列範例示範如何設定<xref:System.Windows.Controls.MenuItem>以便按一下時它將會叫用<xref:System.Windows.Input.ApplicationCommands.Paste%2A>命令<xref:System.Windows.Controls.TextBox>，此時是假設<xref:System.Windows.Controls.TextBox>具有鍵盤焦點。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## <a name="four-main-concepts-in-wpf-commanding"></a>WPF 命令的四個主要概念  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的路由命令模型可以分成四個主要概念︰命令、命令來源、命令目標和命令繫結︰  
  
-   「命令」是要執行的動作。  
  
-   「命令來源」是叫用命令的物件。  
  
-   「命令目標」是在其上執行命令的物件。  
  
-   「命令繫結」是對應命令邏輯和命令的物件。  
  
 在上述範例中，<xref:System.Windows.Input.ApplicationCommands.Paste%2A>命令是命令<xref:System.Windows.Controls.MenuItem>命令來源，<xref:System.Windows.Controls.TextBox>命令目標，而命令繫結由提供<xref:System.Windows.Controls.TextBox>控制項。  值得注意的是，它不一定愈，<xref:System.Windows.Input.CommandBinding>命令目標類別的控制項所提供。  經常<xref:System.Windows.Input.CommandBinding>必須由應用程式開發人員建立或<xref:System.Windows.Input.CommandBinding>可能會附加至命令目標的上階。  
  
<a name="Commands"></a>   
### <a name="commands"></a>命令  
 中的命令[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]由實作<xref:System.Windows.Input.ICommand>介面。  <xref:System.Windows.Input.ICommand>公開兩個方法， <xref:System.Windows.Input.ICommand.Execute%2A>，和<xref:System.Windows.Input.ICommand.CanExecute%2A>，和事件， <xref:System.Windows.Input.ICommand.CanExecuteChanged>。 <xref:System.Windows.Input.ICommand.Execute%2A>執行與命令相關聯的動作。 <xref:System.Windows.Input.ICommand.CanExecute%2A>判斷命令是否可以在目前命令目標上執行。 <xref:System.Windows.Input.ICommand.CanExecuteChanged>如果命令來源可能會使引發但尚未執行的命令繫結的命令中集中管理命令的作業的命令管理員偵測到的變更會引發。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]實作<xref:System.Windows.Input.ICommand>是<xref:System.Windows.Input.RoutedCommand>類別和此概觀單元焦點所在。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的輸入主要來源是滑鼠、鍵盤、筆跡和路由的命令。  使用更多裝置導向輸入<xref:System.Windows.RoutedEvent>通知已發生輸入的事件的應用程式頁面中的物件。  A<xref:System.Windows.Input.RoutedCommand>並無不同。  <xref:System.Windows.Input.RoutedCommand.Execute%2A>和<xref:System.Windows.Input.RoutedCommand.CanExecute%2A>方法<xref:System.Windows.Input.RoutedCommand>不包含命令中，應用程式邏輯，但而引發該通道的路由的事件並且傳遞項目樹狀結構，直到遇到具有<xref:System.Windows.Input.CommandBinding>。  <xref:System.Windows.Input.CommandBinding>包含這些事件處理常式，而且執行此命令的處理常式。  如需事件在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中路由的詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
 <xref:System.Windows.Input.RoutedCommand.Execute%2A>方法<xref:System.Windows.Input.RoutedCommand>引發<xref:System.Windows.Input.CommandManager.PreviewExecuted>和<xref:System.Windows.Input.CommandManager.Executed>命令目標上的事件。  <xref:System.Windows.Input.RoutedCommand.CanExecute%2A>方法<xref:System.Windows.Input.RoutedCommand>引發<xref:System.Windows.Input.CommandManager.CanExecute>和<xref:System.Windows.Input.CommandManager.PreviewCanExecute>命令目標上的事件。  這些事件通道和透過項目樹狀結構，直到遇到含有物件的泡泡<xref:System.Windows.Input.CommandBinding>針對該特定命令。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供一組常見的路由命令分散到數個類別： <xref:System.Windows.Input.MediaCommands>， <xref:System.Windows.Input.ApplicationCommands>， <xref:System.Windows.Input.NavigationCommands>， <xref:System.Windows.Input.ComponentCommands>，和<xref:System.Windows.Documents.EditingCommands>。  這些類別只包含<xref:System.Windows.Input.RoutedCommand>物件與未命令的實作邏輯。  實作邏輯是於其上執行命令之物件的責任。  
  
<a name="Command_Sources"></a>   
### <a name="command-sources"></a>命令來源  
 命令來源是叫用命令的物件。  命令來源的範例包括<xref:System.Windows.Controls.MenuItem>， <xref:System.Windows.Controls.Button>，和<xref:System.Windows.Input.KeyGesture>。  
  
 命令中的來源[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]通常實作<xref:System.Windows.Input.ICommandSource>介面。  
  
 <xref:System.Windows.Input.ICommandSource>會公開三個屬性： <xref:System.Windows.Input.ICommandSource.Command%2A>， <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>，和<xref:System.Windows.Input.ICommandSource.CommandParameter%2A>:  
  
-   <xref:System.Windows.Input.ICommandSource.Command%2A>是叫用命令來源時要執行的命令。  
  
-   <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>是用來執行命令的物件。  值得注意的是，在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>屬性<xref:System.Windows.Input.ICommandSource>時，才適用<xref:System.Windows.Input.ICommand>是<xref:System.Windows.Input.RoutedCommand>。  如果<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>上設定<xref:System.Windows.Input.ICommandSource>和對應的命令不是<xref:System.Windows.Input.RoutedCommand>，則會忽略命令目標。 如果<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>未設定，具有鍵盤焦點的項目將會在命令目標。  
  
-   <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>用來將資訊傳遞給處理常式的使用者定義資料類型實作命令。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類別可實作<xref:System.Windows.Input.ICommandSource>是<xref:System.Windows.Controls.Primitives.ButtonBase>， <xref:System.Windows.Controls.MenuItem>， <xref:System.Windows.Documents.Hyperlink>，和<xref:System.Windows.Input.InputBinding>。  <xref:System.Windows.Controls.Primitives.ButtonBase><xref:System.Windows.Controls.MenuItem>，和<xref:System.Windows.Documents.Hyperlink>時按一下，而叫用命令<xref:System.Windows.Input.InputBinding>叫用命令時<xref:System.Windows.Input.InputGesture>相關聯的方式執行。  
  
 下列範例示範如何使用<xref:System.Windows.Controls.MenuItem>中<xref:System.Windows.Controls.ContextMenu>做為命令來源<xref:System.Windows.Input.ApplicationCommands.Properties%2A>命令。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 一般而言，將接聽命令來源<xref:System.Windows.Input.RoutedCommand.CanExecuteChanged>事件。  此事件會通知命令來源，命令在目前的命令目標上執行的能力可能已變更。  命令來源可以查詢的目前狀態<xref:System.Windows.Input.RoutedCommand>使用<xref:System.Windows.Input.RoutedCommand.CanExecute%2A>方法。  如果命令無法執行，則命令來源可以自行停用。  舉例來說，這是<xref:System.Windows.Controls.MenuItem>對於本身 out 時，無法執行指令。  
  
 <xref:System.Windows.Input.InputGesture>可用來當作命令來源。  兩種類型的輸入中的筆勢[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是<xref:System.Windows.Input.KeyGesture>和<xref:System.Windows.Input.MouseGesture>。  您可以將<xref:System.Windows.Input.KeyGesture>做為鍵盤快速鍵，例如 CTRL + C。  A<xref:System.Windows.Input.KeyGesture>組成<xref:System.Windows.Input.Key>和一組<xref:System.Windows.Input.ModifierKeys>。  A<xref:System.Windows.Input.MouseGesture>組成<xref:System.Windows.Input.MouseAction>和一組選擇性的<xref:System.Windows.Input.ModifierKeys>。  
  
 為了讓<xref:System.Windows.Input.InputGesture>做為命令來源，必須是與命令相關聯。 有幾種方法可達成這個目標。  一種方式是使用<xref:System.Windows.Input.InputBinding>。  
  
 下列範例示範如何建立<xref:System.Windows.Input.KeyBinding>之間<xref:System.Windows.Input.KeyGesture>和<xref:System.Windows.Input.RoutedCommand>。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 建立關聯的另一種方式<xref:System.Windows.Input.InputGesture>至<xref:System.Windows.Input.RoutedCommand>是加入<xref:System.Windows.Input.InputGesture>至<xref:System.Windows.Input.InputGestureCollection>上<xref:System.Windows.Input.RoutedCommand>。  
  
 下列範例示範如何將加入<xref:System.Windows.Input.KeyGesture>至<xref:System.Windows.Input.InputGestureCollection>的<xref:System.Windows.Input.RoutedCommand>。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### <a name="commandbinding"></a>CommandBinding  
 A<xref:System.Windows.Input.CommandBinding>將命令與實作命令的事件處理常式產生關聯。  
  
 <xref:System.Windows.Input.CommandBinding>類別包含<xref:System.Windows.Input.CommandBinding.Command%2A>屬性，以及<xref:System.Windows.Input.CommandBinding.PreviewExecuted>， <xref:System.Windows.Input.CommandBinding.Executed>， <xref:System.Windows.Input.CommandBinding.PreviewCanExecute>，和<xref:System.Windows.Input.CommandBinding.CanExecute>事件。  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A>是的命令，<xref:System.Windows.Input.CommandBinding>相關聯。  事件處理常式附加到<xref:System.Windows.Input.CommandBinding.PreviewExecuted>和<xref:System.Windows.Input.CommandBinding.Executed>事件實作命令邏輯。  事件處理常式附加至<xref:System.Windows.Input.CommandBinding.PreviewCanExecute>和<xref:System.Windows.Input.CommandBinding.CanExecute>事件判斷是否命令可以在目前命令目標上執行。  
  
 下列範例示範如何建立<xref:System.Windows.Input.CommandBinding>根目錄上<xref:System.Windows.Window>應用程式。  <xref:System.Windows.Input.CommandBinding>關聯<xref:System.Windows.Input.ApplicationCommands.Open%2A>命令搭配<xref:System.Windows.Input.CommandManager.Executed>和<xref:System.Windows.Input.CommandBinding.CanExecute>處理常式。  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 下一步<xref:System.Windows.Input.ExecutedRoutedEventHandler>和<xref:System.Windows.Input.CanExecuteRoutedEventHandler>所建立。  <xref:System.Windows.Input.ExecutedRoutedEventHandler>開啟<xref:System.Windows.MessageBox>，顯示指出在執行命令的字串。  <xref:System.Windows.Input.CanExecuteRoutedEventHandler>設定<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A>屬性`true`。  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 A<xref:System.Windows.Input.CommandBinding>會附加至特定的物件，例如根目錄<xref:System.Windows.Window>的應用程式或控制項。  物件，<xref:System.Windows.Input.CommandBinding>附加至定義繫結的範圍。  例如，<xref:System.Windows.Input.CommandBinding>附加可以達到目標的命令的上階<xref:System.Windows.Input.CommandBinding.Executed>事件，但<xref:System.Windows.Input.CommandBinding>附加至命令的子系無法到達目標。  這是方法的直接影響<xref:System.Windows.RoutedEvent>通道以及泡泡會引發事件的物件。  
  
 在某些情況下<xref:System.Windows.Input.CommandBinding>附加至命令目標本身，例如與<xref:System.Windows.Controls.TextBox>類別和<xref:System.Windows.Input.ApplicationCommands.Cut%2A>， <xref:System.Windows.Input.ApplicationCommands.Copy%2A>，和<xref:System.Windows.Input.ApplicationCommands.Paste%2A>命令。 通常它是，更方便地附加<xref:System.Windows.Input.CommandBinding>命令目標，例如主要的祖系<xref:System.Windows.Window>或應用程式物件，特別是當相同<xref:System.Windows.Input.CommandBinding>可以用於多個命令目標。  這些都是當您要建立命令基礎結構時會想要考慮的設計決策。  
  
<a name="Commane_Target"></a>   
### <a name="command-target"></a>命令目標  
 命令目標是於其上執行命令的項目。  與 regards <xref:System.Windows.Input.RoutedCommand>，命令目標是在路由傳送的項目<xref:System.Windows.Input.CommandManager.Executed>和<xref:System.Windows.Input.CommandManager.CanExecute>啟動。  如先前在標註[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>屬性<xref:System.Windows.Input.ICommandSource>時，才適用<xref:System.Windows.Input.ICommand>是<xref:System.Windows.Input.RoutedCommand>。  如果<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>上設定<xref:System.Windows.Input.ICommandSource>和對應的命令不是<xref:System.Windows.Input.RoutedCommand>，則會忽略命令目標。  
  
 命令來源可以明確設定命令目標。  如未定義命令目標，則具有鍵盤焦點的項目會作為命令目標。  將具有鍵盤焦點的項目作為命令目標的優點之一是，它讓應用程式開發人員使用相同的命令來源對多個目標叫用命令，但不必追蹤命令目標。  例如，如果<xref:System.Windows.Controls.MenuItem>叫用**貼上**命令中的應用程式<xref:System.Windows.Controls.TextBox>控制項和<xref:System.Windows.Controls.PasswordBox>控制項，目標可以是<xref:System.Windows.Controls.TextBox>或<xref:System.Windows.Controls.PasswordBox>依據控制項具有鍵盤焦點。  
  
 下例示範如何在標記和程式碼後置中明確設定命令目標。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### <a name="the-commandmanager"></a>The CommandManager  
 <xref:System.Windows.Input.CommandManager>做一個數字命令的相關函式。  它提供一組靜態方法加入和移除<xref:System.Windows.Input.CommandManager.PreviewExecuted>， <xref:System.Windows.Input.CommandManager.Executed>， <xref:System.Windows.Input.CommandManager.PreviewCanExecute>，和<xref:System.Windows.Input.CommandManager.CanExecute>事件處理常式從特定的項目。  它提供方法來註冊<xref:System.Windows.Input.CommandBinding>和<xref:System.Windows.Input.InputBinding>放入特定類別的物件。  <xref:System.Windows.Input.CommandManager>也會提供方法，透過<xref:System.Windows.Input.CommandManager.RequerySuggested>時要通知的命令應該引發事件，<xref:System.Windows.Input.ICommand.CanExecuteChanged>事件。  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A>方法強制<xref:System.Windows.Input.CommandManager>引發<xref:System.Windows.Input.CommandManager.RequerySuggested>事件。  這非常有用的狀況，應該停用/啟用命令，卻不屬於條件<xref:System.Windows.Input.CommandManager>感知。  
  
<a name="Command_Library"></a>   
## <a name="command-library"></a>命令程式庫  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供一組預先定義的命令。  指令程式庫包含下列類別： <xref:System.Windows.Input.ApplicationCommands>， <xref:System.Windows.Input.NavigationCommands>， <xref:System.Windows.Input.MediaCommands>， <xref:System.Windows.Documents.EditingCommands>，而<xref:System.Windows.Input.ComponentCommands>。  這些類別提供的命令，例如<xref:System.Windows.Input.ApplicationCommands.Cut%2A>，<xref:System.Windows.Input.NavigationCommands.BrowseBack%2A>和<xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>， <xref:System.Windows.Input.MediaCommands.Play%2A>， <xref:System.Windows.Input.MediaCommands.Stop%2A>，和<xref:System.Windows.Input.MediaCommands.Pause%2A>。  
  
 這些命令許多都包含一組預設的輸入繫結。  例如，如果指定應用程式處理複製命令，您會自動取得鍵盤繫結 "CTRL+C"。您也會取得其他輸入裝置的繫結，例如 [!INCLUDE[TLA2#tla_tpc](../../../../includes/tla2sharptla-tpc-md.md)] 筆勢和語音資訊。  
  
 當您參考使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的各種命令程式庫中的命令時，通常會省略公開靜態命令屬性的文件庫類別的類別名稱。 命令名稱通常像字串一樣明確，且擁有提供命令邏輯群組的類型，但不一定用於去除混淆。 例如，您可以指定 `Command="Cut"` 而不是更詳細的 `Command="ApplicationCommands.Cut"`。 這是內建的便利性機制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]命令處理器 (更明確地說，它是型別轉換器行為的<xref:System.Windows.Input.ICommand>、 哪些[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器的參考，在載入時間)。  
  
<a name="creating_commands"></a>   
## <a name="creating-custom-commands"></a>建立自訂命令  
 如果命令程式庫類別中的命令不符合您的需求，您可以建立自己的命令。  有兩種方式可以建立自訂的命令。  第一個是從頭開始並實作<xref:System.Windows.Input.ICommand>介面。  其他的方式，更常見的方法，是建立<xref:System.Windows.Input.RoutedCommand>或<xref:System.Windows.Input.RoutedUICommand>。  
  
 如需建立自訂的範例<xref:System.Windows.Input.RoutedCommand>，請參閱[建立自訂的 RoutedCommand 範例](http://go.microsoft.com/fwlink/?LinkID=159980)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Input.RoutedCommand>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Input.InputBinding>  
 <xref:System.Windows.Input.CommandManager>  
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [實作 ICommandSource](../../../../docs/framework/wpf/advanced/how-to-implement-icommandsource.md)  
 [如何：將命令新增至 MenuItem](http://msdn.microsoft.com/library/013d68a0-5373-4a68-bd91-5de574307370)  
 [建立自訂的 RoutedCommand 範例](http://go.microsoft.com/fwlink/?LinkID=159980)
