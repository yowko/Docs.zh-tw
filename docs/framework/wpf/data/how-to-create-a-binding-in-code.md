---
title: 如何：使用程式碼建立繫結
description: 瞭解如何藉由直接呼叫 SetBinding 方法，在 Windows Presentation Foundation 應用程式的程式碼中建立系結。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: aa2a29f4c1262d8ac54641b856c297b284b23a38
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165813"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="9d5d2-103">如何：使用程式碼建立繫結</span><span class="sxs-lookup"><span data-stu-id="9d5d2-103">How to: Create a Binding in Code</span></span>
<span data-ttu-id="9d5d2-104">這個範例示範如何在程式碼中建立和設定 <xref:System.Windows.Data.Binding> 。</span><span class="sxs-lookup"><span data-stu-id="9d5d2-104">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d5d2-105">範例</span><span class="sxs-lookup"><span data-stu-id="9d5d2-105">Example</span></span>  
 <span data-ttu-id="9d5d2-106"><xref:System.Windows.FrameworkElement>類別和 <xref:System.Windows.FrameworkContentElement> 類別都公開 `SetBinding` 方法。</span><span class="sxs-lookup"><span data-stu-id="9d5d2-106">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="9d5d2-107">如果您要系結的元素會繼承其中任一類別，您可以直接呼叫 <xref:System.Windows.FrameworkElement.SetBinding%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9d5d2-107">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="9d5d2-108">下列範例會建立名為的類別， `MyData` 其中包含名為的屬性 `MyDataProperty` 。</span><span class="sxs-lookup"><span data-stu-id="9d5d2-108">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="9d5d2-109">下列範例顯示如何建立系結物件，以設定系結的來源。</span><span class="sxs-lookup"><span data-stu-id="9d5d2-109">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="9d5d2-110">此範例會使用，將的 <xref:System.Windows.FrameworkElement.SetBinding%2A> <xref:System.Windows.Controls.TextBlock.Text%2A> 屬性 `myText` （即 <xref:System.Windows.Controls.TextBlock> 控制項）系結至 `MyDataProperty` 。</span><span class="sxs-lookup"><span data-stu-id="9d5d2-110">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="9d5d2-111">如需完整的程式碼範例，請參閱[僅限程式碼](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90))系結範例。</span><span class="sxs-lookup"><span data-stu-id="9d5d2-111">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="9d5d2-112"><xref:System.Windows.FrameworkElement.SetBinding%2A>您可以使用類別的靜態方法，而不是呼叫 <xref:System.Windows.Data.BindingOperations.SetBinding%2A> <xref:System.Windows.Data.BindingOperations> 。</span><span class="sxs-lookup"><span data-stu-id="9d5d2-112">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="9d5d2-113">下列範例會呼叫， <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> 而不是系結 <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> `myText` 至 `myDataProperty` 。</span><span class="sxs-lookup"><span data-stu-id="9d5d2-113">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="9d5d2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d5d2-114">See also</span></span>

- [<span data-ttu-id="9d5d2-115">資料系結總覽</span><span class="sxs-lookup"><span data-stu-id="9d5d2-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="9d5d2-116">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="9d5d2-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
