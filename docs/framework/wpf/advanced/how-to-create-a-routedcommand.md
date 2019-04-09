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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109040"
---
# <a name="how-to-create-a-routedcommand"></a><span data-ttu-id="9183f-102">HOW TO：建立 RoutedCommand</span><span class="sxs-lookup"><span data-stu-id="9183f-102">How to: Create a RoutedCommand</span></span>
<span data-ttu-id="9183f-103">此範例示範如何建立自訂<xref:System.Windows.Input.RoutedCommand>以及如何實作自訂的命令，藉由建立<xref:System.Windows.Input.ExecutedRoutedEventHandler>並<xref:System.Windows.Input.CanExecuteRoutedEventHandler>並將它們以連結<xref:System.Windows.Input.CommandBinding>。</span><span class="sxs-lookup"><span data-stu-id="9183f-103">This example shows how to create a custom <xref:System.Windows.Input.RoutedCommand> and how to implement the custom command by creating a <xref:System.Windows.Input.ExecutedRoutedEventHandler> and a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> and attaching them to a <xref:System.Windows.Input.CommandBinding>.</span></span>  <span data-ttu-id="9183f-104">如需有關命令的詳細資訊，請參閱 <<c0> [ 命令概觀](commanding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9183f-104">For more information on commanding, see the [Commanding Overview](commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9183f-105">範例</span><span class="sxs-lookup"><span data-stu-id="9183f-105">Example</span></span>  
 <span data-ttu-id="9183f-106">建立第一個步驟<xref:System.Windows.Input.RoutedCommand>定義命令，並具現化它。</span><span class="sxs-lookup"><span data-stu-id="9183f-106">The first step in creating a <xref:System.Windows.Input.RoutedCommand> is defining the command and instantiating it.</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 <span data-ttu-id="9183f-107">若要使用的應用程式中的命令，您必須建立事件處理常式，它會定義命令的功用</span><span class="sxs-lookup"><span data-stu-id="9183f-107">In order to use the command in an application, event handlers which define what the command does must be created</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 <span data-ttu-id="9183f-108">接下來，<xref:System.Windows.Input.CommandBinding>建立其關聯的事件處理常式的命令。</span><span class="sxs-lookup"><span data-stu-id="9183f-108">Next, a  <xref:System.Windows.Input.CommandBinding> is created which associates the command with the event handlers.</span></span> <span data-ttu-id="9183f-109"><xref:System.Windows.Input.CommandBinding>建立特定物件上。</span><span class="sxs-lookup"><span data-stu-id="9183f-109">The <xref:System.Windows.Input.CommandBinding> is created on a specific object.</span></span>  <span data-ttu-id="9183f-110">此物件定義的範圍<xref:System.Windows.Input.CommandBinding>項目樹狀結構中</span><span class="sxs-lookup"><span data-stu-id="9183f-110">This object defines the scope of the <xref:System.Windows.Input.CommandBinding> in the element tree</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 <span data-ttu-id="9183f-111">最後一個步驟叫用命令。</span><span class="sxs-lookup"><span data-stu-id="9183f-111">The final step is invoking the command.</span></span>  <span data-ttu-id="9183f-112">若要叫用命令之一是將其關聯<xref:System.Windows.Input.ICommandSource>，例如<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="9183f-112">One way to invoke a command is to associate it with a <xref:System.Windows.Input.ICommandSource>, such as a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 <span data-ttu-id="9183f-113">按一下按鈕時，<xref:System.Windows.Input.RoutedCommand.Execute%2A>上的自訂方法<xref:System.Windows.Input.RoutedCommand>呼叫。</span><span class="sxs-lookup"><span data-stu-id="9183f-113">When the Button is clicked, the <xref:System.Windows.Input.RoutedCommand.Execute%2A> method on the custom <xref:System.Windows.Input.RoutedCommand> is called.</span></span>  <span data-ttu-id="9183f-114"><xref:System.Windows.Input.RoutedCommand>引發<xref:System.Windows.Input.CommandManager.PreviewExecuted>和<xref:System.Windows.Input.CommandManager.Executed>路由事件。</span><span class="sxs-lookup"><span data-stu-id="9183f-114">The <xref:System.Windows.Input.RoutedCommand> raises the <xref:System.Windows.Input.CommandManager.PreviewExecuted> and <xref:System.Windows.Input.CommandManager.Executed> routed events.</span></span>  <span data-ttu-id="9183f-115">這些事件會周遊元素樹狀結構以尋找<xref:System.Windows.Input.CommandBinding>這個特定的命令。</span><span class="sxs-lookup"><span data-stu-id="9183f-115">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for this particular command.</span></span>  <span data-ttu-id="9183f-116">如果<xref:System.Windows.Input.CommandBinding>找到，則<xref:System.Windows.Input.ExecutedRoutedEventHandler>聯<xref:System.Windows.Input.CommandBinding>呼叫。</span><span class="sxs-lookup"><span data-stu-id="9183f-116">If a <xref:System.Windows.Input.CommandBinding> is found, the <xref:System.Windows.Input.ExecutedRoutedEventHandler> associated with <xref:System.Windows.Input.CommandBinding> is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9183f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9183f-117">See also</span></span>

- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="9183f-118">命令概觀</span><span class="sxs-lookup"><span data-stu-id="9183f-118">Commanding Overview</span></span>](commanding-overview.md)
