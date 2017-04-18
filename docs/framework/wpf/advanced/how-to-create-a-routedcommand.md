---
title: "如何：建立 RoutedCommand | Microsoft Docs"
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
  - "類別, RoutedCommand, 建立"
  - "建立, RoutedCommand 類別"
  - "RoutedCommand 類別, 建立"
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：建立 RoutedCommand
本範例示範如何建立自訂 <xref:System.Windows.Input.RoutedCommand>，以及如何透過建立 <xref:System.Windows.Input.ExecutedRoutedEventHandler> 和 <xref:System.Windows.Input.CanExecuteRoutedEventHandler> 並將它們附加到 <xref:System.Windows.Input.CommandBinding> 的方式，實作該自訂命令。  如需使用命令的詳細資訊，請參閱[命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)。  
  
## 範例  
 建立 <xref:System.Windows.Input.RoutedCommand> 的第一個步驟是定義命令並將它具現化。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 您必須建立定義命令功能的事件處理常式 \(Event Handler\)，才能在應用程式中使用該命令。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 接下來建立的 <xref:System.Windows.Input.CommandBinding> 會讓命令與事件處理常式產生關聯。  <xref:System.Windows.Input.CommandBinding> 是在特定物件上建立。  這個物件定義了項目樹狀結構中 <xref:System.Windows.Input.CommandBinding> 的範圍。  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 最後一個步驟是叫用 \(Invoke\) 命令。  叫用命令的其中一種方法是讓命令與 <xref:System.Windows.Input.ICommandSource> \(例如 <xref:System.Windows.Controls.Button>\) 產生關聯。  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 按一下按鈕時，便會呼叫自訂 <xref:System.Windows.Input.RoutedCommand> 上的 <xref:System.Windows.Input.RoutedCommand.Execute%2A> 方法。  <xref:System.Windows.Input.RoutedCommand> 會引發 <xref:System.Windows.Input.CommandManager.PreviewExecuted> 和 <xref:System.Windows.Input.CommandManager.Executed> 路由事件。  這些事件會在項目樹狀結構中周遊，以尋找此特定命令的 <xref:System.Windows.Input.CommandBinding>。  如果找到 <xref:System.Windows.Input.CommandBinding>，便會呼叫與 <xref:System.Windows.Input.CommandBinding> 相關聯的 <xref:System.Windows.Input.ExecutedRoutedEventHandler>。  
  
## 請參閱  
 <xref:System.Windows.Input.RoutedCommand>   
 [命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)