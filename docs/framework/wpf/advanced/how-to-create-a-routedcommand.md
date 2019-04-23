---
title: HOW TO：建立 RoutedCommand
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
ms.openlocfilehash: d433658a3039c262d2f682eff09df646d978018c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109040"
---
# <a name="how-to-create-a-routedcommand"></a>HOW TO：建立 RoutedCommand
此範例示範如何建立自訂<xref:System.Windows.Input.RoutedCommand>以及如何實作自訂的命令，藉由建立<xref:System.Windows.Input.ExecutedRoutedEventHandler>並<xref:System.Windows.Input.CanExecuteRoutedEventHandler>並將它們以連結<xref:System.Windows.Input.CommandBinding>。  如需有關命令的詳細資訊，請參閱 <<c0> [ 命令概觀](commanding-overview.md)。  
  
## <a name="example"></a>範例  
 建立第一個步驟<xref:System.Windows.Input.RoutedCommand>定義命令，並具現化它。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 若要使用的應用程式中的命令，您必須建立事件處理常式，它會定義命令的功用  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 接下來，<xref:System.Windows.Input.CommandBinding>建立其關聯的事件處理常式的命令。 <xref:System.Windows.Input.CommandBinding>建立特定物件上。  此物件定義的範圍<xref:System.Windows.Input.CommandBinding>項目樹狀結構中  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 最後一個步驟叫用命令。  若要叫用命令之一是將其關聯<xref:System.Windows.Input.ICommandSource>，例如<xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 按一下按鈕時，<xref:System.Windows.Input.RoutedCommand.Execute%2A>上的自訂方法<xref:System.Windows.Input.RoutedCommand>呼叫。  <xref:System.Windows.Input.RoutedCommand>引發<xref:System.Windows.Input.CommandManager.PreviewExecuted>和<xref:System.Windows.Input.CommandManager.Executed>路由事件。  這些事件會周遊元素樹狀結構以尋找<xref:System.Windows.Input.CommandBinding>這個特定的命令。  如果<xref:System.Windows.Input.CommandBinding>找到，則<xref:System.Windows.Input.ExecutedRoutedEventHandler>聯<xref:System.Windows.Input.CommandBinding>呼叫。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Input.RoutedCommand>
- [命令概觀](commanding-overview.md)
