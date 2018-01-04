---
title: "如何：實作 ICommandSource"
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
helpviewer_keywords: ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d82a211f59fbdecdc932b7e57b242274e91cd5b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-icommandsource"></a><span data-ttu-id="c2789-102">如何：實作 ICommandSource</span><span class="sxs-lookup"><span data-stu-id="c2789-102">How to: Implement ICommandSource</span></span>
<span data-ttu-id="c2789-103">這個範例示範如何建立命令來源藉由實作<xref:System.Windows.Input.ICommandSource>。</span><span class="sxs-lookup"><span data-stu-id="c2789-103">This example shows how to create a command source by implementing <xref:System.Windows.Input.ICommandSource>.</span></span>  <span data-ttu-id="c2789-104">命令來源是知道如何叫用命令的物件。</span><span class="sxs-lookup"><span data-stu-id="c2789-104">A command source is an object that knows how to invoke a command.</span></span>  <span data-ttu-id="c2789-105"><xref:System.Windows.Input.ICommandSource>介面會公開三個成員： <xref:System.Windows.Input.ICommandSource.Command%2A>， <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>，和<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>。</span><span class="sxs-lookup"><span data-stu-id="c2789-105">The <xref:System.Windows.Input.ICommandSource> interface exposes three members: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>, and <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.</span></span>  <span data-ttu-id="c2789-106"><xref:System.Windows.Input.ICommandSource.Command%2A>是將會叫用的命令。</span><span class="sxs-lookup"><span data-stu-id="c2789-106"><xref:System.Windows.Input.ICommandSource.Command%2A> is the command which will be invoked.</span></span> <span data-ttu-id="c2789-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>是從命令來源傳遞至方法，這個方法會處理命令的使用者定義資料類型。</span><span class="sxs-lookup"><span data-stu-id="c2789-107">The <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> is a user-defined data type which is passed from the command source to the method which handles the command.</span></span> <span data-ttu-id="c2789-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>是正在其執行命令的物件。</span><span class="sxs-lookup"><span data-stu-id="c2789-108">The <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> is the object that the command is being executed on.</span></span>  
  
 <span data-ttu-id="c2789-109">在此範例中，建立類別的子類別<xref:System.Windows.Controls.Slider>控制項，而且會實作<xref:System.Windows.Input.ICommandSource>。</span><span class="sxs-lookup"><span data-stu-id="c2789-109">In this example, a class is created which subclasses the <xref:System.Windows.Controls.Slider> control and implements <xref:System.Windows.Input.ICommandSource>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2789-110">範例</span><span class="sxs-lookup"><span data-stu-id="c2789-110">Example</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="c2789-111">提供數個類別會實作<xref:System.Windows.Input.ICommandSource>，例如<xref:System.Windows.Controls.Button>， <xref:System.Windows.Controls.MenuItem>，和<xref:System.Windows.Controls.ListBoxItem>。</span><span class="sxs-lookup"><span data-stu-id="c2789-111"> provides a number of classes which implement <xref:System.Windows.Input.ICommandSource>, such as <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, and <xref:System.Windows.Controls.ListBoxItem>.</span></span>  <span data-ttu-id="c2789-112">命令來源會定義如何叫用命令。</span><span class="sxs-lookup"><span data-stu-id="c2789-112">A command source defines how it invokes a command.</span></span>   <span data-ttu-id="c2789-113"><xref:System.Windows.Controls.Button>和<xref:System.Windows.Controls.MenuItem>在按一下時叫用命令。</span><span class="sxs-lookup"><span data-stu-id="c2789-113"><xref:System.Windows.Controls.Button> and <xref:System.Windows.Controls.MenuItem> invoke a command when they are clicked.</span></span>  <span data-ttu-id="c2789-114">A <xref:System.Windows.Controls.ListBoxItem> double 按下時，會叫用命令。</span><span class="sxs-lookup"><span data-stu-id="c2789-114">A <xref:System.Windows.Controls.ListBoxItem> invokes a command when it is double clicked.</span></span> <span data-ttu-id="c2789-115">這些類別才會變成命令來源時其<xref:System.Windows.Input.ICommandSource.Command%2A>屬性設定。</span><span class="sxs-lookup"><span data-stu-id="c2789-115">These classes only become a command source when their <xref:System.Windows.Input.ICommandSource.Command%2A> property is set.</span></span>  
  
 <span data-ttu-id="c2789-116">此範例中我們將會叫用命令時移動滑桿時，或更精確地說，當<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>屬性變更。</span><span class="sxs-lookup"><span data-stu-id="c2789-116">For this example we will invoke the command when the slider is moved, or more accurately, when the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property is changed.</span></span>  
  
 <span data-ttu-id="c2789-117">以下是在類別定義。</span><span class="sxs-lookup"><span data-stu-id="c2789-117">The following is the class definition.</span></span>  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 <span data-ttu-id="c2789-118">下一個步驟是實作<xref:System.Windows.Input.ICommandSource>成員。</span><span class="sxs-lookup"><span data-stu-id="c2789-118">The next step is to implement the <xref:System.Windows.Input.ICommandSource> members.</span></span>  <span data-ttu-id="c2789-119">在此範例中，內容會實作為<xref:System.Windows.DependencyProperty>物件。</span><span class="sxs-lookup"><span data-stu-id="c2789-119">In this example, the properties are implemented as <xref:System.Windows.DependencyProperty> objects.</span></span>  <span data-ttu-id="c2789-120">這可讓使用資料繫結的屬性。</span><span class="sxs-lookup"><span data-stu-id="c2789-120">This enables the properties to use data binding.</span></span>  <span data-ttu-id="c2789-121">如需有關<xref:System.Windows.DependencyProperty>類別，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c2789-121">For more information about the <xref:System.Windows.DependencyProperty> class, see the [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  <span data-ttu-id="c2789-122">如需資料繫結的詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c2789-122">For more information about data binding, see the [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="c2789-123">只有<xref:System.Windows.Input.ICommandSource.Command%2A>屬性如下所示。</span><span class="sxs-lookup"><span data-stu-id="c2789-123">Only the <xref:System.Windows.Input.ICommandSource.Command%2A> property is shown here.</span></span>  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 <span data-ttu-id="c2789-124">以下是<xref:System.Windows.DependencyProperty>變更回撥。</span><span class="sxs-lookup"><span data-stu-id="c2789-124">The following is the <xref:System.Windows.DependencyProperty> change callback.</span></span>  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 <span data-ttu-id="c2789-125">下一個步驟是加入和移除命令來源相關聯的命令。</span><span class="sxs-lookup"><span data-stu-id="c2789-125">The next step is to add and remove the command which is associated with the command source.</span></span>  <span data-ttu-id="c2789-126"><xref:System.Windows.Input.ICommandSource.Command%2A>屬性無法只覆寫時加入新的命令，因為事件處理常式相關聯前一個命令中，如果有的話，必須先移除。</span><span class="sxs-lookup"><span data-stu-id="c2789-126">The <xref:System.Windows.Input.ICommandSource.Command%2A> property cannot simply be overwritten when a new command is added, because the event handlers associated with the previous command, if there was one, must be removed first.</span></span>  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 <span data-ttu-id="c2789-127">最後一個步驟是建立邏輯<xref:System.Windows.Input.ICommand.CanExecuteChanged>處理常式和<xref:System.Windows.Input.ICommand.Execute%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c2789-127">The last step is to create logic for the <xref:System.Windows.Input.ICommand.CanExecuteChanged> handler and the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span>  
  
 <span data-ttu-id="c2789-128"><xref:System.Windows.Input.ICommand.CanExecuteChanged>事件通知的命令來源可能已變更的目前命令目標上執行命令的能力。</span><span class="sxs-lookup"><span data-stu-id="c2789-128">The <xref:System.Windows.Input.ICommand.CanExecuteChanged> event notifies the command source that the ability of the command to execute on the current command target may have changed.</span></span>  <span data-ttu-id="c2789-129">當命令來源收到此事件時，它通常會呼叫<xref:System.Windows.Input.ICommand.CanExecute%2A>命令上的方法。</span><span class="sxs-lookup"><span data-stu-id="c2789-129">When a command source receives this event, it typically calls the <xref:System.Windows.Input.ICommand.CanExecute%2A> method on the command.</span></span>  <span data-ttu-id="c2789-130">如果命令無法在目前命令目標上執行，命令來源會通常停用。</span><span class="sxs-lookup"><span data-stu-id="c2789-130">If the command cannot execute on the current command target, the command source will typically disable itself.</span></span>  <span data-ttu-id="c2789-131">如果命令可以在目前命令目標上執行，則命令來源通常會自動啟用。</span><span class="sxs-lookup"><span data-stu-id="c2789-131">If the command can execute on the current command target, the command source will typically enable itself.</span></span>  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 <span data-ttu-id="c2789-132">最後一個步驟是<xref:System.Windows.Input.ICommand.Execute%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c2789-132">The last step is the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span>  <span data-ttu-id="c2789-133">如果命令是<xref:System.Windows.Input.RoutedCommand>、 <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A>方法是呼叫，否則<xref:System.Windows.Input.ICommand><xref:System.Windows.Input.ICommand.Execute%2A>方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="c2789-133">If the command is a <xref:System.Windows.Input.RoutedCommand>, the <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> method is called; otherwise, the <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> method is called.</span></span>  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a><span data-ttu-id="c2789-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="c2789-134">See Also</span></span>  
 <xref:System.Windows.Input.ICommandSource>  
 <xref:System.Windows.Input.ICommand>  
 <xref:System.Windows.Input.RoutedCommand>  
 [<span data-ttu-id="c2789-135">命令概觀</span><span class="sxs-lookup"><span data-stu-id="c2789-135">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)
