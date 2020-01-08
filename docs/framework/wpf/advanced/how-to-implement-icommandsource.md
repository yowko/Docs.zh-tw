---
title: 如何：實作 ICommandSource
ms.date: 12/05/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 755377d25a2deb48aa9da86d4182075e30763530
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345088"
---
# <a name="how-to-implement-icommandsource"></a><span data-ttu-id="38292-102">如何：實作 ICommandSource</span><span class="sxs-lookup"><span data-stu-id="38292-102">How to: Implement ICommandSource</span></span>

<span data-ttu-id="38292-103">這個範例會示範如何透過執行 <xref:System.Windows.Input.ICommandSource>來建立命令來源。</span><span class="sxs-lookup"><span data-stu-id="38292-103">This example shows how to create a command source by implementing <xref:System.Windows.Input.ICommandSource>.</span></span> <span data-ttu-id="38292-104">命令來源是知道如何叫用命令的物件。</span><span class="sxs-lookup"><span data-stu-id="38292-104">A command source is an object that knows how to invoke a command.</span></span> <span data-ttu-id="38292-105"><xref:System.Windows.Input.ICommandSource> 介面會公開三個成員：</span><span class="sxs-lookup"><span data-stu-id="38292-105">The <xref:System.Windows.Input.ICommandSource> interface exposes three members:</span></span>

- <span data-ttu-id="38292-106"><xref:System.Windows.Input.ICommandSource.Command%2A>：將叫用的命令。</span><span class="sxs-lookup"><span data-stu-id="38292-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: the command that will be invoked.</span></span>
- <span data-ttu-id="38292-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>：使用者定義的資料類型，會從命令來源傳遞至處理命令的方法。</span><span class="sxs-lookup"><span data-stu-id="38292-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: a user-defined data type which is passed from the command source to the method that handles the command.</span></span>
- <span data-ttu-id="38292-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>：正在其上執行命令的物件。</span><span class="sxs-lookup"><span data-stu-id="38292-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: the object that the command is being executed on.</span></span>

<span data-ttu-id="38292-109">在此範例中，會建立繼承自 <xref:System.Windows.Controls.Slider> 控制項並執行 <xref:System.Windows.Input.ICommandSource> 介面的類別。</span><span class="sxs-lookup"><span data-stu-id="38292-109">In this example, a class is created that inherits from the <xref:System.Windows.Controls.Slider> control and implements the  <xref:System.Windows.Input.ICommandSource> interface.</span></span>
  
## <a name="example"></a><span data-ttu-id="38292-110">範例</span><span class="sxs-lookup"><span data-stu-id="38292-110">Example</span></span>

<span data-ttu-id="38292-111">WPF 提供一些可執行 <xref:System.Windows.Input.ICommandSource>的類別，例如 <xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.MenuItem>和 <xref:System.Windows.Documents.Hyperlink>。</span><span class="sxs-lookup"><span data-stu-id="38292-111">WPF provides a number of classes which implement <xref:System.Windows.Input.ICommandSource>, such as <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, and <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="38292-112">命令來源會定義它叫用命令的方式。</span><span class="sxs-lookup"><span data-stu-id="38292-112">A command source defines how it invokes a command.</span></span> <span data-ttu-id="38292-113">這些類別會在按下按鈕時叫用命令，而當設定 <xref:System.Windows.Input.ICommandSource.Command%2A> 屬性時，它們只會變成命令來源。</span><span class="sxs-lookup"><span data-stu-id="38292-113">These classes invoke a command when they're clicked and they only become a command source when their <xref:System.Windows.Input.ICommandSource.Command%2A> property is set.</span></span>

<span data-ttu-id="38292-114">在此範例中，當 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> 屬性變更時，您將會叫用命令，或更精確地移動滑杆。</span><span class="sxs-lookup"><span data-stu-id="38292-114">In this example, you'll invoke the command when the slider is moved, or more accurately, when the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property is changed.</span></span>

<span data-ttu-id="38292-115">以下是類別定義：</span><span class="sxs-lookup"><span data-stu-id="38292-115">The following is the class definition:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

<span data-ttu-id="38292-116">下一個步驟是執行 <xref:System.Windows.Input.ICommandSource> 成員。</span><span class="sxs-lookup"><span data-stu-id="38292-116">The next step is to implement the <xref:System.Windows.Input.ICommandSource> members.</span></span> <span data-ttu-id="38292-117">在此範例中，屬性會實作為 <xref:System.Windows.DependencyProperty> 物件。</span><span class="sxs-lookup"><span data-stu-id="38292-117">In this example, the properties are implemented as <xref:System.Windows.DependencyProperty> objects.</span></span> <span data-ttu-id="38292-118">這可讓屬性使用資料系結。</span><span class="sxs-lookup"><span data-stu-id="38292-118">This enables the properties to use data binding.</span></span> <span data-ttu-id="38292-119">如需有關 <xref:System.Windows.DependencyProperty> 類別的詳細資訊，請參閱相依性[屬性總覽](dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="38292-119">For more information about the <xref:System.Windows.DependencyProperty> class, see the [Dependency Properties Overview](dependency-properties-overview.md).</span></span> <span data-ttu-id="38292-120">如需資料系結的詳細資訊，請參閱資料系結[總覽](../../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="38292-120">For more information about data binding, see the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="38292-121">這裡只會顯示 <xref:System.Windows.Input.ICommandSource.Command%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="38292-121">Only the <xref:System.Windows.Input.ICommandSource.Command%2A> property is shown here.</span></span>
 
[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
<span data-ttu-id="38292-122">以下是 <xref:System.Windows.DependencyProperty> 變更回呼：</span><span class="sxs-lookup"><span data-stu-id="38292-122">The following is the <xref:System.Windows.DependencyProperty> change callback:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

<span data-ttu-id="38292-123">下一個步驟是新增和移除與命令來源相關聯的命令。</span><span class="sxs-lookup"><span data-stu-id="38292-123">The next step is to add and remove the command which is associated with the command source.</span></span> <span data-ttu-id="38292-124">新增新的命令時，不能直接覆寫 <xref:System.Windows.Input.ICommandSource.Command%2A> 屬性，因為與前一個命令相關聯的事件處理常式（如果有的話）必須先移除。</span><span class="sxs-lookup"><span data-stu-id="38292-124">The <xref:System.Windows.Input.ICommandSource.Command%2A> property cannot simply be overwritten when a new command is added, because the event handlers associated with the previous command, if there was one, must be removed first.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

<span data-ttu-id="38292-125">下一個步驟是建立 <xref:System.Windows.Input.ICommand.CanExecuteChanged> 處理常式的邏輯。</span><span class="sxs-lookup"><span data-stu-id="38292-125">The next step is to create logic for the <xref:System.Windows.Input.ICommand.CanExecuteChanged> handler.</span></span>

<span data-ttu-id="38292-126"><xref:System.Windows.Input.ICommand.CanExecuteChanged> 事件會通知命令來源，命令在目前命令目標上執行的能力可能已變更。</span><span class="sxs-lookup"><span data-stu-id="38292-126">The <xref:System.Windows.Input.ICommand.CanExecuteChanged> event notifies the command source that the ability of the command to execute on the current command target may have changed.</span></span> <span data-ttu-id="38292-127">當命令來源收到此事件時，通常會在命令上呼叫 <xref:System.Windows.Input.ICommand.CanExecute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="38292-127">When a command source receives this event, it typically calls the <xref:System.Windows.Input.ICommand.CanExecute%2A> method on the command.</span></span> <span data-ttu-id="38292-128">如果命令無法在目前的命令目標上執行，命令來源通常會自行停用。</span><span class="sxs-lookup"><span data-stu-id="38292-128">If the command cannot execute on the current command target, the command source will typically disable itself.</span></span> <span data-ttu-id="38292-129">如果命令可在目前的命令目標上執行，命令來源通常會自行啟用。</span><span class="sxs-lookup"><span data-stu-id="38292-129">If the command can execute on the current command target, the command source will typically enable itself.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

<span data-ttu-id="38292-130">最後一個步驟是 <xref:System.Windows.Input.ICommand.Execute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="38292-130">The last step is the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span> <span data-ttu-id="38292-131">如果命令是 <xref:System.Windows.Input.RoutedCommand>，就會呼叫 <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> 方法;否則，會呼叫 <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="38292-131">If the command is a <xref:System.Windows.Input.RoutedCommand>, the <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> method is called; otherwise, the <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> method is called.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a><span data-ttu-id="38292-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="38292-132">See also</span></span>

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="38292-133">命令概觀</span><span class="sxs-lookup"><span data-stu-id="38292-133">Commanding Overview</span></span>](commanding-overview.md)
