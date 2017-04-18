---
title: "如何：實作 ICommandSource | Microsoft Docs"
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
  - "ICommandSource 介面, 實作"
  - "介面, ICommandSource, 實作"
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：實作 ICommandSource
本範例示範如何透過實作 <xref:System.Windows.Input.ICommandSource> 建立命令來源。  命令來源是知道如何叫用 \(Invoke\) 命令的物件。  <xref:System.Windows.Input.ICommandSource> 介面會公開三個成員：<xref:System.Windows.Input.ICommandSource.Command%2A>、<xref:System.Windows.Input.ICommandSource.CommandParameter%2A> 和 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>。  <xref:System.Windows.Input.ICommandSource.Command%2A> 是要叫用的命令。  <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> 是從命令來源傳遞至處理命令之方法的使用者定義資料型別。  <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 則是在其上執行命令的物件。  
  
 這個範中建立的類別會子類別化 \(Subclass\) <xref:System.Windows.Controls.Slider> 控制項並實作 <xref:System.Windows.Input.ICommandSource>。  
  
## 範例  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供多個實作 <xref:System.Windows.Input.ICommandSource> 的類別，例如 <xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.MenuItem> 和 <xref:System.Windows.Controls.ListBoxItem>。  命令來源會定義叫用命令的方式。  <xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Controls.MenuItem> 會在按下時叫用命令。  按兩下 <xref:System.Windows.Controls.ListBoxItem> 也會叫用命令。  您必須設定這些類別的 <xref:System.Windows.Input.ICommandSource.Command%2A> 屬性，它們才會變成命令來源。  
  
 針對這個範例，我們將在移動滑桿時 \(正確來說就是 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> 變更\) 時叫用命令。  
  
 以下為類別定義。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 下一個步驟是實作 <xref:System.Windows.Input.ICommandSource> 成員。  在這個範例中，屬性會實作成 <xref:System.Windows.DependencyProperty> 物件。  這可以讓屬性使用資料繫結 \(Data Binding\)。  如需 <xref:System.Windows.DependencyProperty> 類別的詳細資訊，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  如需資料繫結的詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
 此處只顯示 <xref:System.Windows.Input.ICommandSource.Command%2A> 屬性。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 以下為 <xref:System.Windows.DependencyProperty> 變更回呼 \(Callback\)。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 下一個步驟是加入及移除與命令來源相關聯的命令。  <xref:System.Windows.Input.ICommandSource.Command%2A> 屬性不能在加入新命令時直接加以覆寫，因為您必須先移除與先前命令相關聯的事件處理常式 \(Event Handler\) \(如果有的話\)。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 最後一個步驟是建立 <xref:System.Windows.Input.ICommand.CanExecuteChanged> 處理常式和 <xref:System.Windows.Input.ICommand.Execute%2A> 方法的邏輯。  
  
 <xref:System.Windows.Input.ICommand.CanExecuteChanged> 事件會通知命令來源，指出命令在目前命令目標上執行的能力可能已經變更。  當命令來源收到這個事件時，它通常會在該命令上呼叫 <xref:System.Windows.Input.ICommand.CanExecute%2A> 方法。  如果命令無法在目前的命令目標上執行，命令來源一般都會自動停用。  如果命令可以在目前的命令目標上執行，則命令來源通常會自動啟用。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 最後一個步驟是 <xref:System.Windows.Input.ICommand.Execute%2A> 方法。  如果命令是 <xref:System.Windows.Input.RoutedCommand>，則會呼叫 <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> 方法，否則便會呼叫 <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> 方法。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## 請參閱  
 <xref:System.Windows.Input.ICommandSource>   
 <xref:System.Windows.Input.ICommand>   
 <xref:System.Windows.Input.RoutedCommand>   
 [命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)