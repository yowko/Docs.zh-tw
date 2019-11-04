---
title: 如何：使用程式碼建立繫結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 616487a16ebbe6e23fe067fb7ce72644aa3f919f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458855"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="8d2f4-102">如何：使用程式碼建立繫結</span><span class="sxs-lookup"><span data-stu-id="8d2f4-102">How to: Create a Binding in Code</span></span>
<span data-ttu-id="8d2f4-103">這個範例示範如何在程式碼中建立和設定 <xref:System.Windows.Data.Binding>。</span><span class="sxs-lookup"><span data-stu-id="8d2f4-103">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d2f4-104">範例</span><span class="sxs-lookup"><span data-stu-id="8d2f4-104">Example</span></span>  
 <span data-ttu-id="8d2f4-105"><xref:System.Windows.FrameworkElement> 類別和 <xref:System.Windows.FrameworkContentElement> 類別都會公開 `SetBinding` 方法。</span><span class="sxs-lookup"><span data-stu-id="8d2f4-105">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="8d2f4-106">如果您要系結的元素會繼承其中任一類別，您可以直接呼叫 <xref:System.Windows.FrameworkElement.SetBinding%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8d2f4-106">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="8d2f4-107">下列範例會建立名為的類別，`MyData`，其中包含名為 `MyDataProperty`的屬性。</span><span class="sxs-lookup"><span data-stu-id="8d2f4-107">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="8d2f4-108">下列範例顯示如何建立系結物件，以設定系結的來源。</span><span class="sxs-lookup"><span data-stu-id="8d2f4-108">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="8d2f4-109">此範例會使用 <xref:System.Windows.FrameworkElement.SetBinding%2A>，將 `myText`的 <xref:System.Windows.Controls.TextBlock.Text%2A> 屬性（也就是 <xref:System.Windows.Controls.TextBlock> 控制項）系結至 `MyDataProperty`。</span><span class="sxs-lookup"><span data-stu-id="8d2f4-109">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="8d2f4-110">如需完整的程式碼範例，請參閱[僅限程式碼](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90))系結範例。</span><span class="sxs-lookup"><span data-stu-id="8d2f4-110">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="8d2f4-111">您可以使用 <xref:System.Windows.Data.BindingOperations> 類別的 <xref:System.Windows.Data.BindingOperations.SetBinding%2A> 靜態方法，而不是呼叫 <xref:System.Windows.FrameworkElement.SetBinding%2A>。</span><span class="sxs-lookup"><span data-stu-id="8d2f4-111">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="8d2f4-112">下列範例會呼叫 <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>，而不是將 `myText` 系結至 `myDataProperty`的 <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8d2f4-112">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="8d2f4-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d2f4-113">See also</span></span>

- [<span data-ttu-id="8d2f4-114">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="8d2f4-114">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="8d2f4-115">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="8d2f4-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
