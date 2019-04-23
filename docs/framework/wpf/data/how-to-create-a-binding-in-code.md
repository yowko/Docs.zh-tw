---
title: HOW TO：使用程式碼建立繫結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 57ec845c5c9a5bddb801428b9ecde035a97cf447
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089259"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="71e3a-102">HOW TO：使用程式碼建立繫結</span><span class="sxs-lookup"><span data-stu-id="71e3a-102">How to: Create a Binding in Code</span></span>
<span data-ttu-id="71e3a-103">此範例示範如何建立並設定<xref:System.Windows.Data.Binding>在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="71e3a-103">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71e3a-104">範例</span><span class="sxs-lookup"><span data-stu-id="71e3a-104">Example</span></span>  
 <span data-ttu-id="71e3a-105"><xref:System.Windows.FrameworkElement>類別和<xref:System.Windows.FrameworkContentElement>類別兩者公開`SetBinding`方法。</span><span class="sxs-lookup"><span data-stu-id="71e3a-105">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="71e3a-106">如果您要繫結項目繼承這些類別其中一種方法，您可以呼叫<xref:System.Windows.FrameworkElement.SetBinding%2A>直接方法。</span><span class="sxs-lookup"><span data-stu-id="71e3a-106">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="71e3a-107">下列範例會建立名為類別`MyData`，其中包含一個名為屬性`MyDataProperty`。</span><span class="sxs-lookup"><span data-stu-id="71e3a-107">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="71e3a-108">下列範例示範如何建立繫結物件，以設定繫結的來源。</span><span class="sxs-lookup"><span data-stu-id="71e3a-108">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="71e3a-109">此範例會使用<xref:System.Windows.FrameworkElement.SetBinding%2A>繫結<xref:System.Windows.Controls.TextBlock.Text%2A>屬性`myText`，即<xref:System.Windows.Controls.TextBlock>控制項，為`MyDataProperty`。</span><span class="sxs-lookup"><span data-stu-id="71e3a-109">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="71e3a-110">如需完整的程式碼範例，請參閱[僅適用程式碼的繫結範例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="71e3a-110">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="71e3a-111">而不是呼叫<xref:System.Windows.FrameworkElement.SetBinding%2A>，您可以使用<xref:System.Windows.Data.BindingOperations.SetBinding%2A>靜態方法<xref:System.Windows.Data.BindingOperations>類別。</span><span class="sxs-lookup"><span data-stu-id="71e3a-111">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="71e3a-112">下列範例中，會呼叫<xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>而非<xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType>繫結`myText`至`myDataProperty`。</span><span class="sxs-lookup"><span data-stu-id="71e3a-112">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="71e3a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71e3a-113">See also</span></span>

- [<span data-ttu-id="71e3a-114">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="71e3a-114">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="71e3a-115">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="71e3a-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
