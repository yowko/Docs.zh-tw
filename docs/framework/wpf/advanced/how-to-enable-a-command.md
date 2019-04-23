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
ms.openlocfilehash: bf01066a35672e1996f193abc6d76153e5e9dd46
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181697"
---
# <a name="how-to-enable-a-command"></a><span data-ttu-id="e1718-102">HOW TO：啟用命令</span><span class="sxs-lookup"><span data-stu-id="e1718-102">How to: Enable a Command</span></span>
<span data-ttu-id="e1718-103">下列範例示範如何使用命令執行[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e1718-103">The following example demonstrates how to use commanding in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  <span data-ttu-id="e1718-104">此範例示範如何建立關聯<xref:System.Windows.Input.RoutedCommand>要<xref:System.Windows.Controls.Button>，建立<xref:System.Windows.Input.CommandBinding>，並建立事件處理常式實作<xref:System.Windows.Input.RoutedCommand>。</span><span class="sxs-lookup"><span data-stu-id="e1718-104">The example shows how to associate a <xref:System.Windows.Input.RoutedCommand> to a <xref:System.Windows.Controls.Button>, create a <xref:System.Windows.Input.CommandBinding>, and create the event handlers which implement the <xref:System.Windows.Input.RoutedCommand>.</span></span>  <span data-ttu-id="e1718-105">如需有關命令的詳細資訊，請參閱 <<c0> [ 命令概觀](commanding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e1718-105">For more information on commanding, see the [Commanding Overview](commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1718-106">範例</span><span class="sxs-lookup"><span data-stu-id="e1718-106">Example</span></span>  
 <span data-ttu-id="e1718-107">程式碼的第一個區段會建立[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]，組成<xref:System.Windows.Controls.Button>並<xref:System.Windows.Controls.StackPanel>，並建立<xref:System.Windows.Input.CommandBinding>命令處理常式建立關聯的<xref:System.Windows.Input.RoutedCommand>。</span><span class="sxs-lookup"><span data-stu-id="e1718-107">The first section of code creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], which consists of a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.StackPanel>, and creates a <xref:System.Windows.Input.CommandBinding> that associates the command handlers with the <xref:System.Windows.Input.RoutedCommand>.</span></span>  
  
 <span data-ttu-id="e1718-108"><xref:System.Windows.Input.ICommandSource.Command%2A>的屬性<xref:System.Windows.Controls.Button>聯<xref:System.Windows.Input.ApplicationCommands.Close%2A>命令。</span><span class="sxs-lookup"><span data-stu-id="e1718-108">The <xref:System.Windows.Input.ICommandSource.Command%2A> property of the <xref:System.Windows.Controls.Button> is associated with the <xref:System.Windows.Input.ApplicationCommands.Close%2A> command.</span></span>  
  
 <span data-ttu-id="e1718-109"><xref:System.Windows.Input.CommandBinding>新增至<xref:System.Windows.Input.CommandBindingCollection>根目錄的<xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="e1718-109">The <xref:System.Windows.Input.CommandBinding> is added to the <xref:System.Windows.Input.CommandBindingCollection> of the root <xref:System.Windows.Window>.</span></span> <span data-ttu-id="e1718-110"><xref:System.Windows.Input.CommandBinding.Executed>並<xref:System.Windows.Input.CommandBinding.CanExecute>事件處理常式會附加至這個繫結和相關聯<xref:System.Windows.Input.ApplicationCommands.Close%2A>命令。</span><span class="sxs-lookup"><span data-stu-id="e1718-110">The <xref:System.Windows.Input.CommandBinding.Executed> and <xref:System.Windows.Input.CommandBinding.CanExecute> event handlers are attached to this binding and associated with the <xref:System.Windows.Input.ApplicationCommands.Close%2A> command.</span></span>  
  
 <span data-ttu-id="e1718-111">不含<xref:System.Windows.Input.CommandBinding>沒有命令邏輯，來叫用命令的機制。</span><span class="sxs-lookup"><span data-stu-id="e1718-111">Without the <xref:System.Windows.Input.CommandBinding> there is no command logic, only a mechanism to invoke the command.</span></span>  <span data-ttu-id="e1718-112">當<xref:System.Windows.Controls.Button>按下時， <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent>後面接著在命令目標上引發<xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>。</span><span class="sxs-lookup"><span data-stu-id="e1718-112">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> is raised on the command target followed by the <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.</span></span>  <span data-ttu-id="e1718-113">這些事件會周遊元素樹狀結構以尋找<xref:System.Windows.Input.CommandBinding>針對該特定命令。</span><span class="sxs-lookup"><span data-stu-id="e1718-113">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for that particular command.</span></span>  <span data-ttu-id="e1718-114">值得注意的是，因為<xref:System.Windows.RoutedEvent>通道和反昇到項目樹狀結構，其中需要小心<xref:System.Windows.Input.CommandBinding>放。</span><span class="sxs-lookup"><span data-stu-id="e1718-114">It is worth noting that because <xref:System.Windows.RoutedEvent> tunnel and bubble through the element tree, care must be taken in where the <xref:System.Windows.Input.CommandBinding> is put.</span></span>   <span data-ttu-id="e1718-115">如果<xref:System.Windows.Input.CommandBinding>是命令目標或不在路由的另一個節點的同層級<xref:System.Windows.RoutedEvent>，則<xref:System.Windows.Input.CommandBinding>將無法存取。</span><span class="sxs-lookup"><span data-stu-id="e1718-115">If the <xref:System.Windows.Input.CommandBinding> is on a sibling of the command target or another node that is not on the route of the <xref:System.Windows.RoutedEvent>, the <xref:System.Windows.Input.CommandBinding> will not be accessed.</span></span>  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 <span data-ttu-id="e1718-116">下一節的程式碼會實作<xref:System.Windows.Input.CommandManager.Executed>和<xref:System.Windows.Input.CommandBinding.CanExecute>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="e1718-116">The next section of code implements the <xref:System.Windows.Input.CommandManager.Executed> and <xref:System.Windows.Input.CommandBinding.CanExecute> event handlers.</span></span>  
  
 <span data-ttu-id="e1718-117"><xref:System.Windows.Input.CommandManager.Executed>處理常式呼叫方法，以關閉開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="e1718-117">The <xref:System.Windows.Input.CommandManager.Executed> handler calls a method to close the open file.</span></span>  <span data-ttu-id="e1718-118"><xref:System.Windows.Input.CommandBinding.CanExecute>處理常式呼叫方法，以判斷檔案是否為開啟。</span><span class="sxs-lookup"><span data-stu-id="e1718-118">The <xref:System.Windows.Input.CommandBinding.CanExecute> handler calls a method to determine whether a file is open.</span></span>  <span data-ttu-id="e1718-119">如果檔案已開啟，<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A>設定為`true`; 否則它會設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="e1718-119">If a file is open, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> is set to `true`; otherwise, it is set to `false`.</span></span>  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a><span data-ttu-id="e1718-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1718-120">See also</span></span>

- [<span data-ttu-id="e1718-121">命令概觀</span><span class="sxs-lookup"><span data-stu-id="e1718-121">Commanding Overview</span></span>](commanding-overview.md)
