---
title: HOW TO：使用 Windows Forms BindingSource 自訂新增項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 0a2f8491d0f027ca834257e2ec3a08d0b8bdb7ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129542"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="ca526-102">HOW TO：使用 Windows Forms BindingSource 自訂新增項目</span><span class="sxs-lookup"><span data-stu-id="ca526-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="ca526-103">當您使用 <xref:System.Windows.Forms.BindingSource> 元件將 Windows Form 控制項繫結至資料來源時，您可能會發現有必要自訂新項目的建立。</span><span class="sxs-lookup"><span data-stu-id="ca526-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="ca526-104"><xref:System.Windows.Forms.BindingSource> 元件提供了通常會在繫結控制項需要建立新項目時引發的 <xref:System.Windows.Forms.BindingSource.AddingNew> 事件，使這項作業毫不費力。</span><span class="sxs-lookup"><span data-stu-id="ca526-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="ca526-105">您的事件處理常式能夠提供任何要求的自訂行為，例如在 Web 服務上呼叫方法或者從 Class Factory 取得新物件。</span><span class="sxs-lookup"><span data-stu-id="ca526-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca526-106">當您利用處理 <xref:System.Windows.Forms.BindingSource.AddingNew> 事件來加入項目時，這項加入作業將無法取消。</span><span class="sxs-lookup"><span data-stu-id="ca526-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca526-107">範例</span><span class="sxs-lookup"><span data-stu-id="ca526-107">Example</span></span>  
 <span data-ttu-id="ca526-108">下列範例示範如何使用 <xref:System.Windows.Forms.DataGridView> 元件將 <xref:System.Windows.Forms.BindingSource> 控制項繫結至 Class Factory。</span><span class="sxs-lookup"><span data-stu-id="ca526-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="ca526-109">當使用者按一下 <xref:System.Windows.Forms.DataGridView> 控制項的新資料列時，就會引發 <xref:System.Windows.Forms.BindingSource.AddingNew> 事件。</span><span class="sxs-lookup"><span data-stu-id="ca526-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="ca526-110">事件處理常式將會建立新的 `DemoCustomer` 物件，以指派給 <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="ca526-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ca526-111">這將使得新的 `DemoCustomer` 物件加入 <xref:System.Windows.Forms.BindingSource> 元件的清單，並於 <xref:System.Windows.Forms.DataGridView> 控制項的新資料列中顯示。</span><span class="sxs-lookup"><span data-stu-id="ca526-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ca526-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ca526-112">Compiling the Code</span></span>  
 <span data-ttu-id="ca526-113">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="ca526-113">This example requires:</span></span>  
  
-   <span data-ttu-id="ca526-114">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="ca526-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="ca526-115">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="ca526-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="ca526-116">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="ca526-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca526-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca526-117">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="ca526-118">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="ca526-118">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="ca526-119">HOW TO：將 Windows Forms 控制項繫結至類型</span><span class="sxs-lookup"><span data-stu-id="ca526-119">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
