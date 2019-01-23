---
title: HOW TO：實作 ICommandSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 6d42c3a936114c01eb7b7493a9732597a7d2fab9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593936"
---
# <a name="how-to-implement-icommandsource"></a>HOW TO：實作 ICommandSource
此範例示範如何建立命令來源，藉由實作<xref:System.Windows.Input.ICommandSource>。  命令來源是知道如何叫用命令的物件。  <xref:System.Windows.Input.ICommandSource>介面會公開三個成員： <xref:System.Windows.Input.ICommandSource.Command%2A>， <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>，和<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>。  <xref:System.Windows.Input.ICommandSource.Command%2A> 是將會叫用的命令。 <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>是命令來源的資料傳遞至方法，這個方法會處理命令的使用者定義資料類型。 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>是在執行命令的物件。  
  
 在此範例中，建立類別的子類別<xref:System.Windows.Controls.Slider>控制項，並實作<xref:System.Windows.Input.ICommandSource>。  
  
## <a name="example"></a>範例  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供數個類別實作<xref:System.Windows.Input.ICommandSource>，這類<xref:System.Windows.Controls.Button>， <xref:System.Windows.Controls.MenuItem>，和<xref:System.Windows.Controls.ListBoxItem>。  命令來源可定義如何叫用命令。   <xref:System.Windows.Controls.Button> 和<xref:System.Windows.Controls.MenuItem>叫用命令，在按一下時。  A <xref:System.Windows.Controls.ListBoxItem> double 按一下時叫用命令。 這些類別只會變成命令來源時其<xref:System.Windows.Input.ICommandSource.Command%2A>屬性設定。  
  
 此範例中我們將會叫用命令時移動滑桿時，或更精確地說，當<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>屬性變更。  
  
 以下是在類別定義。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 下一個步驟是實作<xref:System.Windows.Input.ICommandSource>成員。  在此範例中，屬性會實作為<xref:System.Windows.DependencyProperty>物件。  這可讓使用資料繫結的屬性。  如需詳細資訊<xref:System.Windows.DependencyProperty>類別，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  如需有關資料繫結的詳細資訊，請參閱 <<c0> [ 資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
 只有<xref:System.Windows.Input.ICommandSource.Command%2A>屬性如下所示。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 以下是<xref:System.Windows.DependencyProperty>變更回呼。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 下一個步驟是新增和移除的命令來源相關聯的命令。  <xref:System.Windows.Input.ICommandSource.Command%2A>屬性無法只是覆寫時加入新的命令，因為與前一個命令中，相關聯的事件處理常式，所以如果有的話，必須先移除。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 最後一個步驟是建立邏輯<xref:System.Windows.Input.ICommand.CanExecuteChanged>處理常式和<xref:System.Windows.Input.ICommand.Execute%2A>方法。  
  
 <xref:System.Windows.Input.ICommand.CanExecuteChanged>事件會通知命令來源目前命令目標上執行命令的能力可能已變更。  當命令來源收到這個事件時，它通常會呼叫<xref:System.Windows.Input.ICommand.CanExecute%2A>命令的方法。  如果命令無法在目前命令目標上執行，則命令來源會通常停用。  如果命令可以在目前命令目標上執行，則命令來源通常會自動啟用。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 最後一個步驟是<xref:System.Windows.Input.ICommand.Execute%2A>方法。  如果命令<xref:System.Windows.Input.RoutedCommand>，則<xref:System.Windows.Input.RoutedCommand><xref:System.Windows.Input.RoutedCommand.Execute%2A>方法是呼叫，否則<xref:System.Windows.Input.ICommand><xref:System.Windows.Input.ICommand.Execute%2A>呼叫方法。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)
