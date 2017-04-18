---
title: "如何：將命令與沒有命令支援的控制項連結 | Microsoft Docs"
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
  - "類別, 控制項, 附加 RoutedCommand"
  - "類別, RoutedCommand, 附加至控制項"
  - "Control 類別, 附加 RoutedCommand"
  - "RoutedCommand 類別, 附加至控制項"
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：將命令與沒有命令支援的控制項連結
下列範例顯示如何將 <xref:System.Windows.Input.RoutedCommand> 與沒有命令內建支援的 <xref:System.Windows.Controls.Control> 連結。  如需將命令連結至多個來源的完整範例，請參閱[建立自訂 RoutedCommand 範例](http://go.microsoft.com/fwlink/?LinkID=159980) 範例 \(英文\)。  
  
## 範例  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供應用程式開發人員經常會遇到的通用命令程式庫。  組成命令程式庫的類別有：<xref:System.Windows.Input.ApplicationCommands>、<xref:System.Windows.Input.ComponentCommands>、<xref:System.Windows.Input.NavigationCommands>、<xref:System.Windows.Input.MediaCommands> 和 <xref:System.Windows.Documents.EditingCommands>。  
  
 構成這些類別的靜態 <xref:System.Windows.Input.RoutedCommand> 物件不提供命令邏輯。  命令的邏輯是與具有 <xref:System.Windows.Input.CommandBinding> 的命令相關聯。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中有許多控制項會對命令程式庫中的某些命令提供內建支援。  舉例來說，<xref:System.Windows.Controls.TextBox> 支援許多應用程式編輯命令，例如 <xref:System.Windows.Input.ApplicationCommands.Paste%2A>、<xref:System.Windows.Input.ApplicationCommands.Copy%2A>、<xref:System.Windows.Input.ApplicationCommands.Cut%2A>、<xref:System.Windows.Input.ApplicationCommands.Redo%2A> 和 <xref:System.Windows.Input.ApplicationCommands.Undo%2A>。  應用程式開發人員不需要特別做什麼，就可以讓這些命令與這些控制項一起運作。  如果執行命令時 <xref:System.Windows.Controls.TextBox> 是命令目標，就會使用內建在控制項內的 <xref:System.Windows.Input.CommandBinding> 處理命令。  
  
 下列範例顯示如何使用 <xref:System.Windows.Controls.Button> 做為 <xref:System.Windows.Input.ApplicationCommands.Open%2A> 命令的命令來源。  <xref:System.Windows.Input.CommandBinding> 的建立，會將指定的 <xref:System.Windows.Input.CanExecuteRoutedEventHandler> 和 <xref:System.Windows.Input.CanExecuteRoutedEventHandler> 與 <xref:System.Windows.Input.RoutedCommand> 建立關聯。  
  
 首先會建立命令來源。  <xref:System.Windows.Controls.Button> 是用來做為命令來源。  
  
 [!code-xml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 接著會建立 <xref:System.Windows.Input.ExecutedRoutedEventHandler> 和 <xref:System.Windows.Input.CanExecuteRoutedEventHandler>。  <xref:System.Windows.Input.ExecutedRoutedEventHandler> 會直接開啟 <xref:System.Windows.MessageBox> 以表示命令已執行。  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> 會將 <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> 屬性設定為 `true`。  通常，CanExecute 處理常式會執行更健全的檢查，以查看命令是否可以在目前命令目標上執行。  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 最後會在應用程式的根 <xref:System.Windows.Window> 上，建立會將路由事件處理常式與 <xref:System.Windows.Input.ApplicationCommands.Open%2A> 命令建立關聯的 <xref:System.Windows.Input.CommandBinding>。  
  
 [!code-xml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## 請參閱  
 [命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)   
 [將命令與含有命令支援的控制項連結](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)