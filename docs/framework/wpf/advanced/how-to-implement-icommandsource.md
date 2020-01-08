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
# <a name="how-to-implement-icommandsource"></a>如何：實作 ICommandSource

這個範例會示範如何透過執行 <xref:System.Windows.Input.ICommandSource>來建立命令來源。 命令來源是知道如何叫用命令的物件。 <xref:System.Windows.Input.ICommandSource> 介面會公開三個成員：

- <xref:System.Windows.Input.ICommandSource.Command%2A>：將叫用的命令。
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>：使用者定義的資料類型，會從命令來源傳遞至處理命令的方法。
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>：正在其上執行命令的物件。

在此範例中，會建立繼承自 <xref:System.Windows.Controls.Slider> 控制項並執行 <xref:System.Windows.Input.ICommandSource> 介面的類別。
  
## <a name="example"></a>範例

WPF 提供一些可執行 <xref:System.Windows.Input.ICommandSource>的類別，例如 <xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.MenuItem>和 <xref:System.Windows.Documents.Hyperlink>。 命令來源會定義它叫用命令的方式。 這些類別會在按下按鈕時叫用命令，而當設定 <xref:System.Windows.Input.ICommandSource.Command%2A> 屬性時，它們只會變成命令來源。

在此範例中，當 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> 屬性變更時，您將會叫用命令，或更精確地移動滑杆。

以下是類別定義：

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

下一個步驟是執行 <xref:System.Windows.Input.ICommandSource> 成員。 在此範例中，屬性會實作為 <xref:System.Windows.DependencyProperty> 物件。 這可讓屬性使用資料系結。 如需有關 <xref:System.Windows.DependencyProperty> 類別的詳細資訊，請參閱相依性[屬性總覽](dependency-properties-overview.md)。 如需資料系結的詳細資訊，請參閱資料系結[總覽](../../../desktop-wpf/data/data-binding-overview.md)。

這裡只會顯示 <xref:System.Windows.Input.ICommandSource.Command%2A> 屬性。
 
[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
以下是 <xref:System.Windows.DependencyProperty> 變更回呼：

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

下一個步驟是新增和移除與命令來源相關聯的命令。 新增新的命令時，不能直接覆寫 <xref:System.Windows.Input.ICommandSource.Command%2A> 屬性，因為與前一個命令相關聯的事件處理常式（如果有的話）必須先移除。

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

下一個步驟是建立 <xref:System.Windows.Input.ICommand.CanExecuteChanged> 處理常式的邏輯。

<xref:System.Windows.Input.ICommand.CanExecuteChanged> 事件會通知命令來源，命令在目前命令目標上執行的能力可能已變更。 當命令來源收到此事件時，通常會在命令上呼叫 <xref:System.Windows.Input.ICommand.CanExecute%2A> 方法。 如果命令無法在目前的命令目標上執行，命令來源通常會自行停用。 如果命令可在目前的命令目標上執行，命令來源通常會自行啟用。

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

最後一個步驟是 <xref:System.Windows.Input.ICommand.Execute%2A> 方法。 如果命令是 <xref:System.Windows.Input.RoutedCommand>，就會呼叫 <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> 方法;否則，會呼叫 <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> 方法。

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [命令概觀](commanding-overview.md)
