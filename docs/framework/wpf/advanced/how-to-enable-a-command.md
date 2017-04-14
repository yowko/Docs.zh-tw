---
title: "如何：啟用命令 | Microsoft Docs"
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
  - "CommandBindings"
  - "命令"
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：啟用命令
下列範例示範如何在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中使用命令。  範例顯示如何建立 <xref:System.Windows.Input.RoutedCommand> 和 <xref:System.Windows.Controls.Button> 的關聯、建立 <xref:System.Windows.Input.CommandBinding>，以及建立實作 <xref:System.Windows.Input.RoutedCommand> 的事件處理常式。  如需使用命令的詳細資訊，請參閱[命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)。  
  
## 範例  
 程式碼的第一個區段會建立由 <xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Controls.StackPanel> 組成的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]，並建立會將命令處理常式與 <xref:System.Windows.Input.RoutedCommand> 相關聯的 <xref:System.Windows.Input.CommandBinding>。  
  
 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Input.ICommandSource.Command%2A> 屬性與 <xref:System.Windows.Input.ApplicationCommands.Close%2A> 命令相關聯。  
  
 <xref:System.Windows.Input.CommandBinding> 是加入到根 <xref:System.Windows.Window> 的 <xref:System.Windows.Input.CommandBindingCollection>。  <xref:System.Windows.Input.CommandBinding.Executed> 和 <xref:System.Windows.Input.CommandBinding.CanExecute> 事件處理常式會附加到這個繫結，並與 <xref:System.Windows.Input.ApplicationCommands.Close%2A> 命令相關聯。  
  
 沒有 <xref:System.Windows.Input.CommandBinding>，就沒有命令邏輯，只有用於叫用命令的機制。  當按一下 <xref:System.Windows.Controls.Button> 時，會在命令目標上隨著 <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent> 後引發 <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent>。  這些事件會在項目樹狀結構中周遊，以查看該特定命令的 <xref:System.Windows.Input.CommandBinding>。  值得注意的是，因為 <xref:System.Windows.RoutedEvent> 會在項目樹狀結構中進行通道和反昇，必須在放置 <xref:System.Windows.Input.CommandBinding> 的地方特別留意。  如果 <xref:System.Windows.Input.CommandBinding> 位於命令目標的同層級 \(Sibling\) 中，或是位於不在 <xref:System.Windows.RoutedEvent> 的路由的其他節點中，就不會存取 <xref:System.Windows.Input.CommandBinding>。  
  
 [!code-xml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 下一個程式碼區段會實作 <xref:System.Windows.Input.CommandManager.Executed> 和 <xref:System.Windows.Input.CommandBinding.CanExecute> 事件處理常式。  
  
 <xref:System.Windows.Input.CommandManager.Executed> 處理常式會呼叫方法關閉開啟的檔案。  <xref:System.Windows.Input.CommandBinding.CanExecute> 處理常式會呼叫方法判斷檔案是否開啟。  如果檔案是開啟的，<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> 會設定為 `true`，否則就設定為 `false`。  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## 請參閱  
 [命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)