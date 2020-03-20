---
title: 如何：實作 ICommandSource
ms.date: 12/05/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 6c18e0b77ec53d9bd3e7ce610f2940effe603c88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174689"
---
# <a name="how-to-implement-icommandsource"></a><span data-ttu-id="111ca-102">如何：實作 ICommandSource</span><span class="sxs-lookup"><span data-stu-id="111ca-102">How to: Implement ICommandSource</span></span>

<span data-ttu-id="111ca-103">此示例演示如何通過實現<xref:System.Windows.Input.ICommandSource>創建命令源。</span><span class="sxs-lookup"><span data-stu-id="111ca-103">This example shows how to create a command source by implementing <xref:System.Windows.Input.ICommandSource>.</span></span> <span data-ttu-id="111ca-104">命令源是知道如何調用命令的物件。</span><span class="sxs-lookup"><span data-stu-id="111ca-104">A command source is an object that knows how to invoke a command.</span></span> <span data-ttu-id="111ca-105">該<xref:System.Windows.Input.ICommandSource>介面公開三個成員：</span><span class="sxs-lookup"><span data-stu-id="111ca-105">The <xref:System.Windows.Input.ICommandSource> interface exposes three members:</span></span>

- <span data-ttu-id="111ca-106"><xref:System.Windows.Input.ICommandSource.Command%2A>：將調用的命令。</span><span class="sxs-lookup"><span data-stu-id="111ca-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: the command that will be invoked.</span></span>
- <span data-ttu-id="111ca-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>：使用者定義的資料類型，從命令源傳遞到處理命令的方法。</span><span class="sxs-lookup"><span data-stu-id="111ca-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: a user-defined data type which is passed from the command source to the method that handles the command.</span></span>
- <span data-ttu-id="111ca-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>：正在執行命令的物件。</span><span class="sxs-lookup"><span data-stu-id="111ca-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: the object that the command is being executed on.</span></span>

<span data-ttu-id="111ca-109">在此示例中，將創建一個從<xref:System.Windows.Controls.Slider>控制項繼承並實現介面的<xref:System.Windows.Input.ICommandSource>類。</span><span class="sxs-lookup"><span data-stu-id="111ca-109">In this example, a class is created that inherits from the <xref:System.Windows.Controls.Slider> control and implements the  <xref:System.Windows.Input.ICommandSource> interface.</span></span>
  
## <a name="example"></a><span data-ttu-id="111ca-110">範例</span><span class="sxs-lookup"><span data-stu-id="111ca-110">Example</span></span>

<span data-ttu-id="111ca-111">WPF<xref:System.Windows.Input.ICommandSource>提供了許多實現 的類，例如<xref:System.Windows.Controls.Button>，<xref:System.Windows.Controls.MenuItem>和<xref:System.Windows.Documents.Hyperlink>。</span><span class="sxs-lookup"><span data-stu-id="111ca-111">WPF provides a number of classes which implement <xref:System.Windows.Input.ICommandSource>, such as <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, and <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="111ca-112">命令源定義它如何調用命令。</span><span class="sxs-lookup"><span data-stu-id="111ca-112">A command source defines how it invokes a command.</span></span> <span data-ttu-id="111ca-113">這些類在按一下時調用命令，並且只有在設置其<xref:System.Windows.Input.ICommandSource.Command%2A>屬性時才會成為命令源。</span><span class="sxs-lookup"><span data-stu-id="111ca-113">These classes invoke a command when they're clicked and they only become a command source when their <xref:System.Windows.Input.ICommandSource.Command%2A> property is set.</span></span>

<span data-ttu-id="111ca-114">在此示例中，您將在移動滑塊時調用該命令，或者更準確地在更改<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>屬性時調用該命令。</span><span class="sxs-lookup"><span data-stu-id="111ca-114">In this example, you'll invoke the command when the slider is moved, or more accurately, when the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property is changed.</span></span>

<span data-ttu-id="111ca-115">以下是類定義：</span><span class="sxs-lookup"><span data-stu-id="111ca-115">The following is the class definition:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

<span data-ttu-id="111ca-116">下一步是實現<xref:System.Windows.Input.ICommandSource>成員。</span><span class="sxs-lookup"><span data-stu-id="111ca-116">The next step is to implement the <xref:System.Windows.Input.ICommandSource> members.</span></span> <span data-ttu-id="111ca-117">在此示例中，屬性作為<xref:System.Windows.DependencyProperty>物件實現。</span><span class="sxs-lookup"><span data-stu-id="111ca-117">In this example, the properties are implemented as <xref:System.Windows.DependencyProperty> objects.</span></span> <span data-ttu-id="111ca-118">這使屬性能夠使用資料繫結。</span><span class="sxs-lookup"><span data-stu-id="111ca-118">This enables the properties to use data binding.</span></span> <span data-ttu-id="111ca-119">有關類的詳細資訊，<xref:System.Windows.DependencyProperty>請參閱[依賴項屬性概述](dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="111ca-119">For more information about the <xref:System.Windows.DependencyProperty> class, see the [Dependency Properties Overview](dependency-properties-overview.md).</span></span> <span data-ttu-id="111ca-120">有關資料繫結的詳細資訊，請參閱[資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="111ca-120">For more information about data binding, see the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="111ca-121">此處僅<xref:System.Windows.Input.ICommandSource.Command%2A>顯示該屬性。</span><span class="sxs-lookup"><span data-stu-id="111ca-121">Only the <xref:System.Windows.Input.ICommandSource.Command%2A> property is shown here.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
<span data-ttu-id="111ca-122">以下是<xref:System.Windows.DependencyProperty>更改回檔：</span><span class="sxs-lookup"><span data-stu-id="111ca-122">The following is the <xref:System.Windows.DependencyProperty> change callback:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

<span data-ttu-id="111ca-123">下一步是添加和刪除與命令源關聯的命令。</span><span class="sxs-lookup"><span data-stu-id="111ca-123">The next step is to add and remove the command which is associated with the command source.</span></span> <span data-ttu-id="111ca-124">在<xref:System.Windows.Input.ICommandSource.Command%2A>添加新命令時，不能簡單地覆蓋該屬性，因為必須先刪除與上一個命令關聯的事件處理常式（如果有）。</span><span class="sxs-lookup"><span data-stu-id="111ca-124">The <xref:System.Windows.Input.ICommandSource.Command%2A> property cannot simply be overwritten when a new command is added, because the event handlers associated with the previous command, if there was one, must be removed first.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

<span data-ttu-id="111ca-125">下一步是為<xref:System.Windows.Input.ICommand.CanExecuteChanged>處理常式創建邏輯。</span><span class="sxs-lookup"><span data-stu-id="111ca-125">The next step is to create logic for the <xref:System.Windows.Input.ICommand.CanExecuteChanged> handler.</span></span>

<span data-ttu-id="111ca-126">該<xref:System.Windows.Input.ICommand.CanExecuteChanged>事件通知命令源命令對當前命令目標執行的能力可能已更改。</span><span class="sxs-lookup"><span data-stu-id="111ca-126">The <xref:System.Windows.Input.ICommand.CanExecuteChanged> event notifies the command source that the ability of the command to execute on the current command target may have changed.</span></span> <span data-ttu-id="111ca-127">當命令源收到此事件時，它通常會在 命令<xref:System.Windows.Input.ICommand.CanExecute%2A>上調用 方法。</span><span class="sxs-lookup"><span data-stu-id="111ca-127">When a command source receives this event, it typically calls the <xref:System.Windows.Input.ICommand.CanExecute%2A> method on the command.</span></span> <span data-ttu-id="111ca-128">如果命令無法對當前命令目標執行，則命令源通常會自行禁用。</span><span class="sxs-lookup"><span data-stu-id="111ca-128">If the command cannot execute on the current command target, the command source will typically disable itself.</span></span> <span data-ttu-id="111ca-129">如果命令可以在當前命令目標上執行，則命令源通常會啟用自身。</span><span class="sxs-lookup"><span data-stu-id="111ca-129">If the command can execute on the current command target, the command source will typically enable itself.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

<span data-ttu-id="111ca-130">最後一步是方法<xref:System.Windows.Input.ICommand.Execute%2A>。</span><span class="sxs-lookup"><span data-stu-id="111ca-130">The last step is the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span> <span data-ttu-id="111ca-131">如果命令為 ，<xref:System.Windows.Input.RoutedCommand><xref:System.Windows.Input.RoutedCommand><xref:System.Windows.Input.RoutedCommand.Execute%2A>則調用 方法;否則，將<xref:System.Windows.Input.ICommand><xref:System.Windows.Input.ICommand.Execute%2A>調用 該方法。</span><span class="sxs-lookup"><span data-stu-id="111ca-131">If the command is a <xref:System.Windows.Input.RoutedCommand>, the <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> method is called; otherwise, the <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> method is called.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a><span data-ttu-id="111ca-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="111ca-132">See also</span></span>

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="111ca-133">命令概觀</span><span class="sxs-lookup"><span data-stu-id="111ca-133">Commanding Overview</span></span>](commanding-overview.md)
