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
# <a name="how-to-implement-icommandsource"></a>如何：實作 ICommandSource

此示例演示如何通過實現<xref:System.Windows.Input.ICommandSource>創建命令源。 命令源是知道如何調用命令的物件。 該<xref:System.Windows.Input.ICommandSource>介面公開三個成員：

- <xref:System.Windows.Input.ICommandSource.Command%2A>：將調用的命令。
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>：使用者定義的資料類型，從命令源傳遞到處理命令的方法。
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>：正在執行命令的物件。

在此示例中，將創建一個從<xref:System.Windows.Controls.Slider>控制項繼承並實現介面的<xref:System.Windows.Input.ICommandSource>類。
  
## <a name="example"></a>範例

WPF<xref:System.Windows.Input.ICommandSource>提供了許多實現 的類，例如<xref:System.Windows.Controls.Button>，<xref:System.Windows.Controls.MenuItem>和<xref:System.Windows.Documents.Hyperlink>。 命令源定義它如何調用命令。 這些類在按一下時調用命令，並且只有在設置其<xref:System.Windows.Input.ICommandSource.Command%2A>屬性時才會成為命令源。

在此示例中，您將在移動滑塊時調用該命令，或者更準確地在更改<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>屬性時調用該命令。

以下是類定義：

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

下一步是實現<xref:System.Windows.Input.ICommandSource>成員。 在此示例中，屬性作為<xref:System.Windows.DependencyProperty>物件實現。 這使屬性能夠使用資料繫結。 有關類的詳細資訊，<xref:System.Windows.DependencyProperty>請參閱[依賴項屬性概述](dependency-properties-overview.md)。 有關資料繫結的詳細資訊，請參閱[資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)。

此處僅<xref:System.Windows.Input.ICommandSource.Command%2A>顯示該屬性。

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
以下是<xref:System.Windows.DependencyProperty>更改回檔：

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

下一步是添加和刪除與命令源關聯的命令。 在<xref:System.Windows.Input.ICommandSource.Command%2A>添加新命令時，不能簡單地覆蓋該屬性，因為必須先刪除與上一個命令關聯的事件處理常式（如果有）。

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

下一步是為<xref:System.Windows.Input.ICommand.CanExecuteChanged>處理常式創建邏輯。

該<xref:System.Windows.Input.ICommand.CanExecuteChanged>事件通知命令源命令對當前命令目標執行的能力可能已更改。 當命令源收到此事件時，它通常會在 命令<xref:System.Windows.Input.ICommand.CanExecute%2A>上調用 方法。 如果命令無法對當前命令目標執行，則命令源通常會自行禁用。 如果命令可以在當前命令目標上執行，則命令源通常會啟用自身。

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

最後一步是方法<xref:System.Windows.Input.ICommand.Execute%2A>。 如果命令為 ，<xref:System.Windows.Input.RoutedCommand><xref:System.Windows.Input.RoutedCommand><xref:System.Windows.Input.RoutedCommand.Execute%2A>則調用 方法;否則，將<xref:System.Windows.Input.ICommand><xref:System.Windows.Input.ICommand.Execute%2A>調用 該方法。

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [命令概觀](commanding-overview.md)
