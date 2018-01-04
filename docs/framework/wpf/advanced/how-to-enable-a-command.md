---
title: "如何：啟用命令"
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
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b27f8544a44a252eb1a1afd6e096f303360c14e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-a-command"></a>如何：啟用命令
下列範例示範如何使用命令中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。  此範例示範如何將<xref:System.Windows.Input.RoutedCommand>至<xref:System.Windows.Controls.Button>，建立<xref:System.Windows.Input.CommandBinding>，並建立事件處理常式實作<xref:System.Windows.Input.RoutedCommand>。  如需命令的詳細資訊，請參閱[指揮概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)。  
  
## <a name="example"></a>範例  
 程式碼的第一個區段會建立[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]，其中包含的<xref:System.Windows.Controls.Button>和<xref:System.Windows.Controls.StackPanel>，並建立<xref:System.Windows.Input.CommandBinding>將命令處理常式取代<xref:System.Windows.Input.RoutedCommand>。  
  
 <xref:System.Windows.Input.ICommandSource.Command%2A>屬性<xref:System.Windows.Controls.Button>聯<xref:System.Windows.Input.ApplicationCommands.Close%2A>命令。  
  
 <xref:System.Windows.Input.CommandBinding>加入至<xref:System.Windows.Input.CommandBindingCollection>根的<xref:System.Windows.Window>。 <xref:System.Windows.Input.CommandBinding.Executed>和<xref:System.Windows.Input.CommandBinding.CanExecute>事件處理常式會附加至這個繫結和相關聯<xref:System.Windows.Input.ApplicationCommands.Close%2A>命令。  
  
 不含<xref:System.Windows.Input.CommandBinding>沒有命令邏輯，來叫用命令的機制。  當<xref:System.Windows.Controls.Button>按一下時， <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent>後面接著命令目標上引發<xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>。  這些事件尋找項目樹狀目錄中周遊<xref:System.Windows.Input.CommandBinding>針對該特定命令。  它是值得一提，因為<xref:System.Windows.RoutedEvent>通道和透過項目樹狀結構的泡泡，必須特別小心 where<xref:System.Windows.Input.CommandBinding>放。   如果<xref:System.Windows.Input.CommandBinding>命令目標或不在的路由的另一個節點的同層級上<xref:System.Windows.RoutedEvent>、<xref:System.Windows.Input.CommandBinding>將無法存取。  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 下一節的程式碼實作<xref:System.Windows.Input.CommandManager.Executed>和<xref:System.Windows.Input.CommandBinding.CanExecute>事件處理常式。  
  
 <xref:System.Windows.Input.CommandManager.Executed>處理常式呼叫方法來關閉開啟的檔案。  <xref:System.Windows.Input.CommandBinding.CanExecute>處理常式會呼叫方法來判斷檔案是否為開啟。  如果檔案為開啟，<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A>設`true`，否則會設為`false`。  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a>請參閱  
 [命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)
