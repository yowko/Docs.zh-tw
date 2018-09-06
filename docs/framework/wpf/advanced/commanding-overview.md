---
title: 命令概觀
ms.date: 03/30/2017
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
ms.openlocfilehash: d41613ce2488fa572fa11def06350ab1e564df6c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749066"
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
  
 命令的另一項用途是指出是否有動作可用。 若要繼續剪下物件或文字的範例，只有選取項目時動作才有意義。 如果使用者嘗試剪下物件或文字，但未選取任何項目，不會有任何事發生。 為向使用者指出這個狀況，許多應用程式會停用按鈕和功能表項目，讓使用者知道是否能執行某動作。 命令可以透過實作 <xref:System.Windows.Input.ICommand.CanExecute%2A> 方法來指出一個動作是否可能執行。 按鈕可以訂閱 <xref:System.Windows.Input.ICommand.CanExecuteChanged> 事件，如果 <xref:System.Windows.Input.ICommand.CanExecute%2A> 傳回 `false` 則會停用，如果 <xref:System.Windows.Input.ICommand.CanExecute%2A> 傳回 `true` 則會啟用。  
  
 命令語意在不同的應用程式和類別中可以一致，但動作邏輯專屬於於其上執行動作的特定物件。 按鍵組合 CTRL+X 在文字類別、映像類別及網頁瀏覽器中叫用 [剪下] 命令，但執行 [剪下] 作業的實際邏輯是由執行剪下動作的應用程式所定義。 <xref:System.Windows.Input.RoutedCommand> 可讓用戶端實作邏輯。 文字物件可能會將選取的文字剪入剪貼簿，而映像物件可能會剪下選取的映像。 當應用程式處理 <xref:System.Windows.Input.CommandManager.Executed> 事件時，可以存取命令目標，並根據目標類型採取適當的動作。  
  
<a name="simple_command"></a>   
## <a name="simple-command-example-in-wpf"></a>WPF 中的簡單命令範例  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中使用命令最簡單的方式，是從命令程式庫類別之一使用預先定義的 <xref:System.Windows.Input.RoutedCommand>、使用有可處理命令之原生支援的控制項，以及使用有可叫用命令之原生支援的控制項。  <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令是在 <xref:System.Windows.Input.ApplicationCommands> 類別中的其中一個預先定義命令。  <xref:System.Windows.Controls.TextBox> 控制項具有內建邏輯來處理 <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令。  <xref:System.Windows.Controls.MenuItem> 類別具有叫用命令的原生支援。  
  
 下列範例示範如何設定 <xref:System.Windows.Controls.MenuItem>，以便其在按一下時叫用 <xref:System.Windows.Controls.TextBox> 上的 <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令，假設 <xref:System.Windows.Controls.TextBox> 具有鍵盤焦點。  
  
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
  
 在上述範例中，<xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令是命令，<xref:System.Windows.Controls.MenuItem> 是命令來源，<xref:System.Windows.Controls.TextBox> 是命令目標，而命令繫結由 <xref:System.Windows.Controls.TextBox> 控制項提供。  值得注意的是，<xref:System.Windows.Input.CommandBinding> 不一定都是由命令目標類別控制項所提供。  通常，<xref:System.Windows.Input.CommandBinding> 必須由應用程式開發人員建立，或 <xref:System.Windows.Input.CommandBinding> 可能會附加至命令目標的上階。  
  
<a name="Commands"></a>   
### <a name="commands"></a>命令  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的命令是藉由實作 <xref:System.Windows.Input.ICommand> 介面來建立。  <xref:System.Windows.Input.ICommand> 公開兩個方法：<xref:System.Windows.Input.ICommand.Execute%2A> 和 <xref:System.Windows.Input.ICommand.CanExecute%2A>，以及一個事件 <xref:System.Windows.Input.ICommand.CanExecuteChanged>。 <xref:System.Windows.Input.ICommand.Execute%2A> 執行與命令建立關聯的動作。 <xref:System.Windows.Input.ICommand.CanExecute%2A> 判斷命令是否可以在目前命令目標上執行。 如果集中命令作業的命令管理員偵測到命令來源的變更可能會使命令繫結已引發但尚未執行的命令失效，則會引發 <xref:System.Windows.Input.ICommand.CanExecuteChanged>。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的實作 <xref:System.Windows.Input.ICommand> 是 <xref:System.Windows.Input.RoutedCommand> 類別和此概觀焦點所在。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的輸入主要來源是滑鼠、鍵盤、筆跡和路由的命令。  更多裝置導向的輸入使用 <xref:System.Windows.RoutedEvent> 通知應用程式頁面中的物件有輸入事件發生。  <xref:System.Windows.Input.RoutedCommand> 並無不同。  <xref:System.Windows.Input.RoutedCommand> 的 <xref:System.Windows.Input.RoutedCommand.Execute%2A> 和 <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> 方法不包含該命令的應用程式邏輯，而是引發路由事件，該事件會在項目樹狀結構中浮動，直到遇到具有 <xref:System.Windows.Input.CommandBinding> 的物件。  <xref:System.Windows.Input.CommandBinding> 包含這些事件的處理常式，並且是執行命令的處理常式。  如需事件在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中路由的詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
 <xref:System.Windows.Input.RoutedCommand> 上之 <xref:System.Windows.Input.RoutedCommand.Execute%2A> 方法會引發命令目標上的 <xref:System.Windows.Input.CommandManager.PreviewExecuted> 和 <xref:System.Windows.Input.CommandManager.Executed> 事件。  <xref:System.Windows.Input.RoutedCommand> 上之 <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> 方法會引發命令目標上的 <xref:System.Windows.Input.CommandManager.CanExecute> 和 <xref:System.Windows.Input.CommandManager.PreviewCanExecute> 事件。  這些事件會在項目樹狀結構中浮動，直到遇到有該特定命令之 <xref:System.Windows.Input.CommandBinding> 的物件。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供分散到數個類別中的一組常見路由命令：<xref:System.Windows.Input.MediaCommands>、<xref:System.Windows.Input.ApplicationCommands>、<xref:System.Windows.Input.NavigationCommands>、<xref:System.Windows.Input.ComponentCommands> 和 <xref:System.Windows.Documents.EditingCommands>。  這些類別只包含 <xref:System.Windows.Input.RoutedCommand> 物件，不包含命令的實作邏輯。  實作邏輯是於其上執行命令之物件的責任。  
  
<a name="Command_Sources"></a>   
### <a name="command-sources"></a>命令來源  
 命令來源是叫用命令的物件。  命令來源的範例包括 <xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Input.KeyGesture>。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的命令來源通常會實作 <xref:System.Windows.Input.ICommandSource> 介面。  
  
 <xref:System.Windows.Input.ICommandSource> 會公開三個屬性：<xref:System.Windows.Input.ICommandSource.Command%2A>、<xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 和 <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>：  
  
-   <xref:System.Windows.Input.ICommandSource.Command%2A> 是當叫用命令來源時，會執行的命令。  
  
-   <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 是用來執行命令的物件。  值得注意的是，在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，<xref:System.Windows.Input.ICommandSource> 上的 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 屬性僅適用於當 <xref:System.Windows.Input.ICommand> 為 <xref:System.Windows.Input.RoutedCommand> 時。  如果 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 是設定於 <xref:System.Windows.Input.ICommandSource> 上，並且對應的命令不是 <xref:System.Windows.Input.RoutedCommand>，則會忽略命令目標。 如果未設定 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>，則具有鍵盤焦點的項目就是命令目標。  
  
-   <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> 是使用者定義資料類型，用來將資訊傳遞至實作命令的處理常式。  
  
 實作 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的 <xref:System.Windows.Input.ICommandSource> 類別是 <xref:System.Windows.Controls.Primitives.ButtonBase>、<xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Documents.Hyperlink> 和 <xref:System.Windows.Input.InputBinding>。  按一下 <xref:System.Windows.Controls.Primitives.ButtonBase>、<xref:System.Windows.Controls.MenuItem> 和 <xref:System.Windows.Documents.Hyperlink> 時會叫用一個命令，並且在與其建立關聯的 <xref:System.Windows.Input.InputGesture> 執行時，<xref:System.Windows.Input.InputBinding> 會叫用一個命令。  
  
 下列範例示範如何將 <xref:System.Windows.Controls.ContextMenu> 中的 <xref:System.Windows.Controls.MenuItem> 用作 <xref:System.Windows.Input.ApplicationCommands.Properties%2A> 命令的命令來源。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 一般而言，命令來源會接聽 <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> 事件。  此事件會通知命令來源，命令在目前的命令目標上執行的能力可能已變更。  命令來源可以使用 <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> 方法來查詢 <xref:System.Windows.Input.RoutedCommand> 的目前狀態。  如果命令無法執行，則命令來源可以自行停用。  此情況範例就是 <xref:System.Windows.Controls.MenuItem> 在命令無法執行時把自己變成灰色。  
  
 <xref:System.Windows.Input.InputGesture> 可用作命令來源。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中兩種類型的輸入筆勢為 <xref:System.Windows.Input.KeyGesture> 和 <xref:System.Windows.Input.MouseGesture>。  您可以將 <xref:System.Windows.Input.KeyGesture> 視為鍵盤快速鍵，例如 CTRL+C。  <xref:System.Windows.Input.KeyGesture> 由 <xref:System.Windows.Input.Key> 和一組 <xref:System.Windows.Input.ModifierKeys> 組成。  <xref:System.Windows.Input.MouseGesture> 由 <xref:System.Windows.Input.MouseAction> 和選擇性的一組 <xref:System.Windows.Input.ModifierKeys> 組成。  
  
 為了讓 <xref:System.Windows.Input.InputGesture> 表現如同命令來源，必須將其與命令建立關聯。 有幾種方法可達成這個目標。  其中一種方式是使用 <xref:System.Windows.Input.InputBinding>。  
  
 下列範例會示範如何在 <xref:System.Windows.Input.KeyGesture> 和 <xref:System.Windows.Input.RoutedCommand> 之間建立 <xref:System.Windows.Input.KeyBinding>。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 將 <xref:System.Windows.Input.InputGesture> 與 <xref:System.Windows.Input.RoutedCommand> 建立關聯的另一種方法是將 <xref:System.Windows.Input.InputGesture> 新增至 <xref:System.Windows.Input.RoutedCommand> 上的 <xref:System.Windows.Input.InputGestureCollection>。  
  
 下列範例示範如何將 <xref:System.Windows.Input.KeyGesture> 新增至 <xref:System.Windows.Input.RoutedCommand> 的 <xref:System.Windows.Input.InputGestureCollection>。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### <a name="commandbinding"></a>CommandBinding  
 <xref:System.Windows.Input.CommandBinding> 會將命令與實作此命令的事件處理常式建立關聯。  
  
 <xref:System.Windows.Input.CommandBinding> 類別包含 <xref:System.Windows.Input.CommandBinding.Command%2A> 屬性，以及 <xref:System.Windows.Input.CommandBinding.PreviewExecuted>、<xref:System.Windows.Input.CommandBinding.Executed>、<xref:System.Windows.Input.CommandBinding.PreviewCanExecute> 和 <xref:System.Windows.Input.CommandBinding.CanExecute> 事件。  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A> 是與 <xref:System.Windows.Input.CommandBinding> 建立關聯的命令。  附加到 <xref:System.Windows.Input.CommandBinding.PreviewExecuted> 和 <xref:System.Windows.Input.CommandBinding.Executed> 事件的事件處理常式會實作命令邏輯。  附加到 <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> 和 <xref:System.Windows.Input.CommandBinding.CanExecute> 事件的事件處理常式會判斷命令是否可以在目前命令目標上執行。  
  
 下列範例將示範如何在應用程式的根目錄 <xref:System.Windows.Window> 上建立 <xref:System.Windows.Input.CommandBinding>。  <xref:System.Windows.Input.CommandBinding> 會將 <xref:System.Windows.Input.ApplicationCommands.Open%2A> 命令與 <xref:System.Windows.Input.CommandManager.Executed> 和 <xref:System.Windows.Input.CommandBinding.CanExecute> 處理常式建立關聯。  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 接下來，會建立 <xref:System.Windows.Input.ExecutedRoutedEventHandler> 和 <xref:System.Windows.Input.CanExecuteRoutedEventHandler>。  <xref:System.Windows.Input.ExecutedRoutedEventHandler> 會開啟 <xref:System.Windows.MessageBox>，會顯示一個字串，指出該命令已執行。  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> 會將 <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> 屬性設定為 `true`。  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 <xref:System.Windows.Input.CommandBinding> 會附加至特定的物件，例如應用程式或控制項的根目錄 <xref:System.Windows.Window>。  <xref:System.Windows.Input.CommandBinding> 所附加至的物件會定義繫結範圍。  例如，附加至命令目標上階的 <xref:System.Windows.Input.CommandBinding> 可以透過 <xref:System.Windows.Input.CommandBinding.Executed> 事件到達，但無法到達附加至命令目標子系的 <xref:System.Windows.Input.CommandBinding>。  這是 <xref:System.Windows.RoutedEvent> 在引發事件之物件中浮動的直接結果。  
  
 在某些情況下，<xref:System.Windows.Input.CommandBinding> 會附加至命令目標本身，例如 <xref:System.Windows.Controls.TextBox> 類別與 <xref:System.Windows.Input.ApplicationCommands.Cut%2A>、<xref:System.Windows.Input.ApplicationCommands.Copy%2A> 和 <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令。 但通常將 <xref:System.Windows.Input.CommandBinding> 附加至命令目標的上階會更方便，例如主要的 <xref:System.Windows.Window> 或應用程式物件，特別是當相同的 <xref:System.Windows.Input.CommandBinding> 可用於多個命令目標時。  這些都是當您要建立命令基礎結構時會想要考慮的設計決策。  
  
<a name="Commane_Target"></a>   
### <a name="command-target"></a>命令目標  
 命令目標是於其上執行命令的項目。  關於 <xref:System.Windows.Input.RoutedCommand>，命令目標是 <xref:System.Windows.Input.CommandManager.Executed> 和 <xref:System.Windows.Input.CommandManager.CanExecute> 之路由啟動的項目。  如前所述，在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，<xref:System.Windows.Input.ICommandSource> 上的 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 屬性僅適用於當 <xref:System.Windows.Input.ICommand> 為 <xref:System.Windows.Input.RoutedCommand> 時。  如果 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 是設定於 <xref:System.Windows.Input.ICommandSource> 上，並且對應的命令不是 <xref:System.Windows.Input.RoutedCommand>，則會忽略命令目標。  
  
 命令來源可以明確設定命令目標。  如未定義命令目標，則具有鍵盤焦點的項目會作為命令目標。  將具有鍵盤焦點的項目作為命令目標的優點之一是，它讓應用程式開發人員使用相同的命令來源對多個目標叫用命令，但不必追蹤命令目標。  例如，如果 <xref:System.Windows.Controls.MenuItem> 在具有 <xref:System.Windows.Controls.TextBox> 控制項和 <xref:System.Windows.Controls.PasswordBox> 控制項的應用程式中叫用**貼上**命令，則目標可以是 <xref:System.Windows.Controls.TextBox> 或 <xref:System.Windows.Controls.PasswordBox>，取決於哪個控制項具有鍵盤焦點。  
  
 下例示範如何在標記和程式碼後置中明確設定命令目標。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### <a name="the-commandmanager"></a>The CommandManager  
 <xref:System.Windows.Input.CommandManager> 提供許多與命令相關的功能。  會提供一組靜態方法，用於向特定項目新增和移除 <xref:System.Windows.Input.CommandManager.PreviewExecuted>、<xref:System.Windows.Input.CommandManager.Executed>、<xref:System.Windows.Input.CommandManager.PreviewCanExecute> 和 <xref:System.Windows.Input.CommandManager.CanExecute> 事件處理常式。  會提供將 <xref:System.Windows.Input.CommandBinding> 和 <xref:System.Windows.Input.InputBinding> 物件註冊到特定類別的方法。  <xref:System.Windows.Input.CommandManager> 也會透過 <xref:System.Windows.Input.CommandManager.RequerySuggested> 事件提供一種方法，用於在引發 <xref:System.Windows.Input.ICommand.CanExecuteChanged> 事件時通知命令。  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> 方法會強制 <xref:System.Windows.Input.CommandManager> 引發 <xref:System.Windows.Input.CommandManager.RequerySuggested> 事件。  出現應該停用/啟用命令的條件，卻非 <xref:System.Windows.Input.CommandManager> 所知的條件時，這很有用。  
  
<a name="Command_Library"></a>   
## <a name="command-library"></a>命令程式庫  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供一組預先定義的命令。  命令程式庫包含下列類別：<xref:System.Windows.Input.ApplicationCommands>、<xref:System.Windows.Input.NavigationCommands>、<xref:System.Windows.Input.MediaCommands>、<xref:System.Windows.Documents.EditingCommands> 和 <xref:System.Windows.Input.ComponentCommands>。  這些類別提供的命令，例如 <xref:System.Windows.Input.ApplicationCommands.Cut%2A>、<xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> 以及 <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>、<xref:System.Windows.Input.MediaCommands.Play%2A>、<xref:System.Windows.Input.MediaCommands.Stop%2A> 和 <xref:System.Windows.Input.MediaCommands.Pause%2A>。  
  
 這些命令許多都包含一組預設的輸入繫結。  例如，如果指定應用程式處理複製命令，您會自動取得鍵盤繫結 "CTRL+C"。您也會取得其他輸入裝置的繫結，例如 [!INCLUDE[TLA2#tla_tpc](../../../../includes/tla2sharptla-tpc-md.md)] 筆勢和語音資訊。  
  
 當您參考使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的各種命令程式庫中的命令時，通常會省略公開靜態命令屬性的文件庫類別的類別名稱。 命令名稱通常像字串一樣明確，且擁有提供命令邏輯群組的類型，但不一定用於去除混淆。 例如，您可以指定 `Command="Cut"` 而不是更詳細的 `Command="ApplicationCommands.Cut"`。 這是內建在命令 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的方便機制 (更精確地說，這是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器在載入階段參考的 <xref:System.Windows.Input.ICommand> 類型轉換器行為)。  
  
<a name="creating_commands"></a>   
## <a name="creating-custom-commands"></a>建立自訂命令  
 如果命令程式庫類別中的命令不符合您的需求，您可以建立自己的命令。  有兩種方式可以建立自訂的命令。  第一種是從頭開始實作 <xref:System.Windows.Input.ICommand> 介面。  另一種為更常見的方式，即建立 <xref:System.Windows.Input.RoutedCommand> 或 <xref:System.Windows.Input.RoutedUICommand>。  
  
 如需建立自訂 <xref:System.Windows.Input.RoutedCommand> 的範例，請參閱[建立自訂的 RoutedCommand 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Input.RoutedCommand>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Input.InputBinding>  
 <xref:System.Windows.Input.CommandManager>  
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [實作 ICommandSource](../../../../docs/framework/wpf/advanced/how-to-implement-icommandsource.md)  
 [如何：將命令新增至 MenuItem](https://msdn.microsoft.com/library/013d68a0-5373-4a68-bd91-5de574307370)  
 [建立自訂的 RoutedCommand 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
