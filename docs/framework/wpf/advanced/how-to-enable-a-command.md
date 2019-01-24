---
title: HOW TO：啟用命令
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
ms.openlocfilehash: 904d5a3404b693c383731eda01e9e43b2d5126fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622061"
---
# <a name="how-to-enable-a-command"></a>HOW TO：啟用命令
下列範例示範如何使用命令執行[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。  此範例示範如何建立關聯<xref:System.Windows.Input.RoutedCommand>要<xref:System.Windows.Controls.Button>，建立<xref:System.Windows.Input.CommandBinding>，並建立事件處理常式實作<xref:System.Windows.Input.RoutedCommand>。  如需有關命令的詳細資訊，請參閱 <<c0> [ 命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)。  
  
## <a name="example"></a>範例  
 程式碼的第一個區段會建立[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]，組成<xref:System.Windows.Controls.Button>並<xref:System.Windows.Controls.StackPanel>，並建立<xref:System.Windows.Input.CommandBinding>命令處理常式建立關聯的<xref:System.Windows.Input.RoutedCommand>。  
  
 <xref:System.Windows.Input.ICommandSource.Command%2A>的屬性<xref:System.Windows.Controls.Button>聯<xref:System.Windows.Input.ApplicationCommands.Close%2A>命令。  
  
 <xref:System.Windows.Input.CommandBinding>新增至<xref:System.Windows.Input.CommandBindingCollection>根目錄的<xref:System.Windows.Window>。 <xref:System.Windows.Input.CommandBinding.Executed>並<xref:System.Windows.Input.CommandBinding.CanExecute>事件處理常式會附加至這個繫結和相關聯<xref:System.Windows.Input.ApplicationCommands.Close%2A>命令。  
  
 不含<xref:System.Windows.Input.CommandBinding>沒有命令邏輯，來叫用命令的機制。  當<xref:System.Windows.Controls.Button>按下時， <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent>後面接著在命令目標上引發<xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>。  這些事件會周遊元素樹狀結構以尋找<xref:System.Windows.Input.CommandBinding>針對該特定命令。  值得注意的是，因為<xref:System.Windows.RoutedEvent>通道和反昇到項目樹狀結構，其中需要小心<xref:System.Windows.Input.CommandBinding>放。   如果<xref:System.Windows.Input.CommandBinding>是命令目標或不在路由的另一個節點的同層級<xref:System.Windows.RoutedEvent>，則<xref:System.Windows.Input.CommandBinding>將無法存取。  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 下一節的程式碼會實作<xref:System.Windows.Input.CommandManager.Executed>和<xref:System.Windows.Input.CommandBinding.CanExecute>事件處理常式。  
  
 <xref:System.Windows.Input.CommandManager.Executed>處理常式呼叫方法，以關閉開啟的檔案。  <xref:System.Windows.Input.CommandBinding.CanExecute>處理常式呼叫方法，以判斷檔案是否為開啟。  如果檔案已開啟，<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A>設定為`true`; 否則它會設定為`false`。  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a>另請參閱
- [命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)
