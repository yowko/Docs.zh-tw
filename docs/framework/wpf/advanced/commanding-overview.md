---
title: "命令概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "類別, CommandBinding"
  - "命令程式庫"
  - "CommandBindings"
  - "命令"
  - "CommandManager"
  - "命令, 定義"
  - "ICommandSource 介面"
  - "介面, ICommandSource"
ms.assetid: bc208dfe-367d-426a-99de-52b7e7511e81
caps.latest.revision: 35
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 34
---
# 命令概觀
<a name="introduction"></a> 命令是 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的輸入機制，比起裝置輸入，可提供語意程度更高的輸入處理。  命令的範例有 \[**複製**\]、\[**剪下**\] 和 \[**貼上**\] 等等，在許多應用程式中都可以找到。  
  
 本概觀會說明 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中有哪些命令、哪些類別屬於命令模型的一部分，以及如何在應用程式中使用和建立命令。  
  
 此主題包括下列章節：  
  
-   [什麼是命令](#commands_at_10000_feet)  
  
-   [WPF 中的簡單命令範例](#simple_command)  
  
-   [WPF 命令中的四個主要概念](#Four_main_Concepts)  
  
-   [命令程式庫](#Command_Library)  
  
-   [建立自訂命令](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## 什麼是命令  
 命令有數種用途。  第一個用途是區隔語意與從執行命令的邏輯叫用該命令的物件。  這可讓多個不同的來源叫用相同的命令邏輯，並可根據不同的目標 \(Target\) 自訂命令邏輯。  例如，\[**複製**\]、\[**剪下**\] 和 \[**貼上**\] 編輯作業都可以在許多應用程式中找到，但如果它們是使用命令進行實作，則會使用不同的使用者介面來叫用。  應用程式可能會讓使用者按一下按鈕、選擇功能表中的項目或使用按鍵組合 \(例如 CTRL\+X\)，來剪下選取的物件或文字。  使用命令，可以將每種使用者動作類型繫結至相同的邏輯。  
  
 命令的另一個用途是指出動作是否可用。  繼續以剪下物件或文字為例，動作只有在選取某個項目時才會有意義。  如果使用者嘗試剪下物件或文字，而未選取任何項目，則不會進行任何處理。  為了向使用者指出發生此狀況，許多應用程式都會停用按鈕和功能表項目，讓使用者知道是否可以執行動作。  實作 <xref:System.Windows.Input.ICommand.CanExecute%2A> 方法，命令可以指出是否可以執行動作。  按鈕可以訂閱 <xref:System.Windows.Input.ICommand.CanExecuteChanged> 事件，並在 <xref:System.Windows.Input.ICommand.CanExecute%2A> 傳回 `false` 時予以停用，而在 <xref:System.Windows.Input.ICommand.CanExecute%2A> 傳回 `true` 時予以啟用。  
  
 命令的語意無論在哪一個應用程式或類別都是一致的，但動作的邏輯則會視其作用的特定物件而定。  組合鍵 CTRL\+X 會在文字類別、影像類別和 Web 瀏覽器中叫用 \[**剪下**\] 命令，但執行 \[**剪下**\] 作業的實際邏輯則是由執行剪下的應用程式所定義。  <xref:System.Windows.Input.RoutedCommand> 可讓用戶端實作邏輯。  文字物件可能會將選取的文字剪下至剪貼簿，影像物件則可能是剪下選取的影像。  應用程式在處理 <xref:System.Windows.Input.CommandManager.Executed> 事件時可以存取命令的目標，而且可以根據目標的類型採取適當的動作。  
  
<a name="simple_command"></a>   
## WPF 中的簡單命令範例  
 要在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中使用命令，最簡單的方式就是從其中一個命令程式庫類別使用預先定義的 <xref:System.Windows.Input.RoutedCommand>，使用有處理命令原生支援的控制項，以及可叫用命令之原生支援的控制項。  <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令是 <xref:System.Windows.Input.ApplicationCommands> 類別中的一個預先定義的命令。  <xref:System.Windows.Controls.TextBox> 控制項具有處理 <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令的內建邏輯。  而 <xref:System.Windows.Controls.MenuItem> 類別則有叫用命令的原生支援。  
  
 下列範例顯示如何設定 <xref:System.Windows.Controls.MenuItem>，這樣在 <xref:System.Windows.Controls.TextBox> 具有鍵盤焦點的情況下，按下該功能表列時會叫用 <xref:System.Windows.Controls.TextBox> 上的 <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令。  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## WPF 命令中的四個主要概念  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的路由命令模型可細分為四個主要概念：命令、命令來源、命令目標和命令繫結：  
  
-   「*命令*」\(Command\) 是要執行的動作。  
  
-   「*命令來源*」\(Command Source\) 是叫用命令的物件。  
  
-   「*命令目標*」\(Command Target\) 是執行命令的目標物件。  
  
-   「*命令繫結*」\(Command Binding\) 是將命令邏輯對應到命令的物件。  
  
 在上一個範例中，<xref:System.Windows.Input.ApplicationCommands.Paste%2A> 是命令，<xref:System.Windows.Controls.MenuItem> 是命令來源，<xref:System.Windows.Controls.TextBox> 是命令目標，而命令繫結則是由 <xref:System.Windows.Controls.TextBox> 控制項所提供。  請注意，<xref:System.Windows.Input.CommandBinding> 不一定都是由命令目標類別的控制項所提供。  <xref:System.Windows.Input.CommandBinding> 常常必須由應用程式開發人員建立，<xref:System.Windows.Input.CommandBinding> 也可能被附加到命令目標的祖系。  
  
<a name="Commands"></a>   
### 命令  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的命令是透過實作 <xref:System.Windows.Input.ICommand> 介面所建立。  <xref:System.Windows.Input.ICommand> 會公開兩種方法 \(<xref:System.Windows.Input.ICommand.Execute%2A> 和 <xref:System.Windows.Input.ICommand.CanExecute%2A>\) 和一個事件 \(<xref:System.Windows.Input.ICommand.CanExecuteChanged>\)。  <xref:System.Windows.Input.ICommand.Execute%2A> 會執行與命令相關聯的動作。<xref:System.Windows.Input.ICommand.CanExecute%2A> 會判斷命令是否能在目前的命令目標上執行。  如果集中管理命令操作的命令管理員偵測到命令來源中發生變更，而且此變更可能會使已引發但命令繫結尚未執行的命令無效，則會引發 <xref:System.Windows.Input.ICommand.CanExecuteChanged>。  <xref:System.Windows.Input.ICommand> 的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作是 <xref:System.Windows.Input.RoutedCommand> 類別，也就是本概觀的重點。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的主要輸入來源為滑鼠、鍵盤、筆跡和路由命令。  裝置導向的輸入會使用 <xref:System.Windows.RoutedEvent>，通知應用程式頁中的物件有輸入事件發生。  <xref:System.Windows.Input.RoutedCommand> 也是如此。  <xref:System.Windows.Input.RoutedCommand> 的 <xref:System.Windows.Input.RoutedCommand.Execute%2A> 和 <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> 方法不含命令的應用程式邏輯，但會引發在項目樹狀結構進行向下 \(Tunnel\) 和反昇 \(Bubble\) 的路由事件，直到遇到具備 <xref:System.Windows.Input.CommandBinding> 的物件。  <xref:System.Windows.Input.CommandBinding> 包含這些事件的處理常式，它也是執行命令的處理常式。  如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中事件路由的詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
 <xref:System.Windows.Input.RoutedCommand> 上的 <xref:System.Windows.Input.RoutedCommand.Execute%2A> 方法會在命令目標上引發 <xref:System.Windows.Input.CommandManager.PreviewExecuted> 和 <xref:System.Windows.Input.CommandManager.Executed> 事件。  <xref:System.Windows.Input.RoutedCommand> 上的 <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> 方法會在命令目標上引發 <xref:System.Windows.Input.CommandManager.CanExecute> 和 <xref:System.Windows.Input.CommandManager.PreviewCanExecute> 事件。  這些事件會在項目樹狀結構進行向下和向下路由，直到遇到有該特定命令之 <xref:System.Windows.Input.CommandBinding> 的物件。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供一組跨數個類別的通用路由命令：<xref:System.Windows.Input.MediaCommands>、<xref:System.Windows.Input.ApplicationCommands>、<xref:System.Windows.Input.NavigationCommands>、<xref:System.Windows.Input.ComponentCommands> 和 <xref:System.Windows.Documents.EditingCommands>。  這些類別只由 <xref:System.Windows.Input.RoutedCommand> 物件組成，沒有命令的實作邏輯。  實作邏輯是由在其中執行命令的物件負責。  
  
<a name="Command_Sources"></a>   
### 命令來源  
 命令來源是叫用命令的物件。  命令來源的範例包括 <xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Input.KeyGesture>。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的命令來源通常會實作 <xref:System.Windows.Input.ICommandSource> 介面。  
  
 <xref:System.Windows.Input.ICommandSource> 會公開三個屬性，也就是 <xref:System.Windows.Input.ICommandSource.Command%2A>、<xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 和 <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>：  
  
-   <xref:System.Windows.Input.ICommandSource.Command%2A> 是叫用命令來源時執行的命令。  
  
-   <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 是在其上執行命令的物件。  請注意，在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，<xref:System.Windows.Input.ICommandSource> 上的 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 屬性只有在 <xref:System.Windows.Input.ICommand> 是 <xref:System.Windows.Input.RoutedCommand> 時才適用。  如果在 <xref:System.Windows.Input.ICommandSource> 上設定 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>，而且對應命令不是 <xref:System.Windows.Input.RoutedCommand>，就會忽略命令目標。  如果沒有設定 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>，有鍵盤焦點的項目將會是命令目標。  
  
-   <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> 是使用者定義資料型別，用來將資訊傳遞給實作命令的處理常式。  
  
 實作 <xref:System.Windows.Input.ICommandSource> 的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別為<xref:System.Windows.Controls.Primitives.ButtonBase>、<xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Documents.Hyperlink> 和 <xref:System.Windows.Input.InputBinding>。  按一下 <xref:System.Windows.Controls.Primitives.ButtonBase>、<xref:System.Windows.Controls.MenuItem> 和 <xref:System.Windows.Documents.Hyperlink> 時，它們會叫用命令，而 <xref:System.Windows.Input.InputBinding> 會在與其關聯的 <xref:System.Windows.Input.InputGesture> 執行時叫用命令。  
  
 下列範例顯示如何使用 <xref:System.Windows.Controls.ContextMenu> 中的 <xref:System.Windows.Controls.MenuItem>，當做 <xref:System.Windows.Input.ApplicationCommands.Properties%2A> 命令的命令來源。  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 通常，命令來源會接聽 <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> 事件。  此事件會通知命令來源，指出命令在目前命令目標上執行的能力可能已經變更。  命令來源可使用 <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> 方法來查詢 <xref:System.Windows.Input.RoutedCommand> 的目前狀態。  如果命令不能執行，命令來源可能會自動停用。  例如，<xref:System.Windows.Controls.MenuItem> 在命令不能執行時，會自動變成灰色。  
  
 <xref:System.Windows.Input.InputGesture> 可當做命令來源使用。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中有兩種輸入筆勢，分別是 <xref:System.Windows.Input.KeyGesture> 和 <xref:System.Windows.Input.MouseGesture>。  您可以將 <xref:System.Windows.Input.KeyGesture> 想成是鍵盤快速鍵，例如 CTRL\+C。  <xref:System.Windows.Input.KeyGesture> 是由一個 <xref:System.Windows.Input.Key> 和一組 <xref:System.Windows.Input.ModifierKeys> 所組成。  <xref:System.Windows.Input.MouseGesture> 是由一個 <xref:System.Windows.Input.MouseAction> 和一組選擇性的 <xref:System.Windows.Input.ModifierKeys> 所組成。  
  
 要將 <xref:System.Windows.Input.InputGesture> 當做命令來源，它必須與命令產生關聯。  有幾種方式可完成這項工作。  其中一種方式是使用 <xref:System.Windows.Input.InputBinding>。  
  
 下列範例顯示如何在 <xref:System.Windows.Input.KeyGesture> 和 <xref:System.Windows.Input.RoutedCommand> 之間建立 <xref:System.Windows.Input.KeyBinding>。  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 另外一種將 <xref:System.Windows.Input.InputGesture> 與 <xref:System.Windows.Input.RoutedCommand> 產生關聯的方式，是將 <xref:System.Windows.Input.InputGesture> 加進 <xref:System.Windows.Input.RoutedCommand> 上的 <xref:System.Windows.Input.InputGestureCollection>。  
  
 下列範例顯示如何將 <xref:System.Windows.Input.KeyGesture> 加入到 <xref:System.Windows.Input.RoutedCommand> 的 <xref:System.Windows.Input.InputGestureCollection>。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### CommandBinding  
 <xref:System.Windows.Input.CommandBinding> 會將命令與實作命令的事件處理常式產生關聯。  
  
 <xref:System.Windows.Input.CommandBinding> 類別包含 <xref:System.Windows.Input.CommandBinding.Command%2A> 屬性，以及 <xref:System.Windows.Input.CommandBinding.PreviewExecuted>、<xref:System.Windows.Input.CommandBinding.Executed>、<xref:System.Windows.Input.CommandBinding.PreviewCanExecute> 和 <xref:System.Windows.Input.CommandBinding.CanExecute> 事件。  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A> 是與 <xref:System.Windows.Input.CommandBinding> 產生關聯的命令。  附加到 <xref:System.Windows.Input.CommandBinding.PreviewExecuted> 和 <xref:System.Windows.Input.CommandBinding.Executed> 事件的事件處理常式會實作命令邏輯。  附加到 <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> 和 <xref:System.Windows.Input.CommandBinding.CanExecute> 事件的事件處理常式會判斷命令是否可在目前的命令目標上執行。  
  
 下列範例顯示如何在應用程式的根 <xref:System.Windows.Window> 建立 <xref:System.Windows.Input.CommandBinding>。  <xref:System.Windows.Input.CommandBinding> 會將 <xref:System.Windows.Input.ApplicationCommands.Open%2A> 命令與 <xref:System.Windows.Input.CommandManager.Executed> 和 <xref:System.Windows.Input.CommandBinding.CanExecute> 處理常式產生關聯。  
  
 [!code-xml[commandwithhandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 接下來，會建立 <xref:System.Windows.Input.ExecutedRoutedEventHandler> 和 <xref:System.Windows.Input.CanExecuteRoutedEventHandler>。  <xref:System.Windows.Input.ExecutedRoutedEventHandler> 會開啟 <xref:System.Windows.MessageBox>，其中顯示指出命令已執行的字串。  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> 會將 <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> 屬性設定為 `true`。  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 <xref:System.Windows.Input.CommandBinding> 會附加到特定物件，例如應用程式的根 <xref:System.Windows.Window> 或控制項。  <xref:System.Windows.Input.CommandBinding> 附加的物件會定義繫結的範圍。  例如，附加到命令目標祖系的 <xref:System.Windows.Input.CommandBinding> 位在 <xref:System.Windows.Input.CommandBinding.Executed> 事件的範圍內，但附加到命令目標子系 \(Descendant\) 的 <xref:System.Windows.Input.CommandBinding> 則不在其範圍內。  這是 <xref:System.Windows.RoutedEvent> 從引發事件的物件以通道的方式向下和反昇向上路由所產生的直接結果。  
  
 在某些情況下，<xref:System.Windows.Input.CommandBinding> 會附加到命令目標本身，例如 <xref:System.Windows.Controls.TextBox> 類別以及 <xref:System.Windows.Input.ApplicationCommands.Cut%2A>、<xref:System.Windows.Input.ApplicationCommands.Copy%2A> 和 <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令。  通常，將 <xref:System.Windows.Input.CommandBinding> 附加到命令目標的祖系會更為方便，例如主要 <xref:System.Windows.Window> 或 Application 物件，尤其是如果相同的 <xref:System.Windows.Input.CommandBinding> 可用於多個命令目標。  這些是在建立命令基礎結構時所要考量的設計決定。  
  
<a name="Commane_Target"></a>   
### 命令目標  
 命令目標是執行命令的項目。  就 <xref:System.Windows.Input.RoutedCommand> 而言，命令目標是開始路由 <xref:System.Windows.Input.CommandManager.Executed> 和 <xref:System.Windows.Input.CommandManager.CanExecute> 的項目。  如前所述，在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，<xref:System.Windows.Input.ICommandSource> 上的 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 屬性只有在 <xref:System.Windows.Input.ICommand> 是 <xref:System.Windows.Input.RoutedCommand> 時才適用。  如果在 <xref:System.Windows.Input.ICommandSource> 上設定 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>，而且對應命令不是 <xref:System.Windows.Input.RoutedCommand>，就會忽略命令目標。  
  
 命令來源可明確設定命令目標。  如果沒有定義命令目標，有鍵盤焦點的項目將當做命令目標使用。  使用有鍵盤焦點的項目當做命令目標的優點之一，就是可讓應用程式開發人員使用相同的命令來源在多個目標上叫用命令，而無須追蹤命令目標。  例如，如果 <xref:System.Windows.Controls.MenuItem> 在有 <xref:System.Windows.Controls.TextBox> 控制項和 <xref:System.Windows.Controls.PasswordBox> 控制項的應用程式中叫用了 \[**貼上**\] 命令，依哪一個控制項有鍵盤焦點而定，目標可能是 <xref:System.Windows.Controls.TextBox> 或 <xref:System.Windows.Controls.PasswordBox>。  
  
 下列範例顯示如何在標記和程式碼後置中明確設定命令目標。  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### CommandManager  
 <xref:System.Windows.Input.CommandManager> 提供數個命令相關功能。  它提供一組靜態方法，可將 <xref:System.Windows.Input.CommandManager.PreviewExecuted>、<xref:System.Windows.Input.CommandManager.Executed>、<xref:System.Windows.Input.CommandManager.PreviewCanExecute> 和 <xref:System.Windows.Input.CommandManager.CanExecute> 事件處理常式加入到特定項目，以及從特定項目移除這些事件處理常式。  它提供了方式，將 <xref:System.Windows.Input.CommandBinding> 和 <xref:System.Windows.Input.InputBinding> 物件註冊到特定類別。  <xref:System.Windows.Input.CommandManager> 也透過 <xref:System.Windows.Input.CommandManager.RequerySuggested> 事件提供方式，來通知命令何時應引發 <xref:System.Windows.Input.ICommand.CanExecuteChanged> 事件。  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> 方法會強制 <xref:System.Windows.Input.CommandManager> 引發 <xref:System.Windows.Input.CommandManager.RequerySuggested> 事件。  這在應該停用\/啟用命令、但 <xref:System.Windows.Input.CommandManager> 無法察覺的情況中很有用。  
  
<a name="Command_Library"></a>   
## 命令程式庫  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供一組預先定義的命令。  命令程式庫由下列類別所組成：<xref:System.Windows.Input.ApplicationCommands>、<xref:System.Windows.Input.NavigationCommands>、<xref:System.Windows.Input.MediaCommands>、<xref:System.Windows.Documents.EditingCommands> 和 <xref:System.Windows.Input.ComponentCommands>。  這些類別提供了如 <xref:System.Windows.Input.ApplicationCommands.Cut%2A>、<xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> 和 <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>、<xref:System.Windows.Input.MediaCommands.Play%2A>、<xref:System.Windows.Input.MediaCommands.Stop%2A> 以及 <xref:System.Windows.Input.MediaCommands.Pause%2A> 命令。  
  
 其中許多命令都包含一組預設的輸入繫結。  例如，如果您指定應用程式處理複製命令，就會自動取得鍵盤繫結 "CTRL\+C"。您也可以取得其他輸入裝置的繫結，例如 [!INCLUDE[TLA2#tla_tpc](../../../../includes/tla2sharptla-tpc-md.md)] 畫筆動作和語音資訊。  
  
 當您使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 參考多個命令程式庫中的命令時，通常可以省略公開靜態命令屬性之程式庫類別的類別名稱。  一般來說，命令名稱是明確的字串，而其型別是要提供命令的邏輯分組，但要清楚指定命令不一定要用到它。  例如，您可以指定 `Command="Cut"`，而非指定一長串的 `Command="ApplicationCommands.Cut"`。  這是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器針對命令內建的便利機制 \(精確地說，這是 <xref:System.Windows.Input.ICommand> 的型別轉換子行為，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器會在載入時間 \(Load Time\) 加以參考\)。  
  
<a name="creating_commands"></a>   
## 建立自訂命令  
 如果命令程式庫中的命令不敷所需，您可以自行建立命令。  有兩種方式可以建立自訂命令。  第一種方式是從頭開始，並實作 <xref:System.Windows.Input.ICommand> 介面。  另一種較常用的方式則是建立 <xref:System.Windows.Input.RoutedCommand> 或 <xref:System.Windows.Input.RoutedUICommand>。  
  
 如需建立自訂 <xref:System.Windows.Input.RoutedCommand> 的範例，請參閱[建立自訂 RoutedCommand 範例](http://go.microsoft.com/fwlink/?LinkID=159980) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Input.RoutedCommand>   
 <xref:System.Windows.Input.CommandBinding>   
 <xref:System.Windows.Input.InputBinding>   
 <xref:System.Windows.Input.CommandManager>   
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [實作 ICommandSource](../../../../docs/framework/wpf/advanced/how-to-implement-icommandsource.md)   
 [How to: Add a Command to a MenuItem](http://msdn.microsoft.com/zh-tw/013d68a0-5373-4a68-bd91-5de574307370)   
 [建立自訂 RoutedCommand 範例](http://go.microsoft.com/fwlink/?LinkID=159980)