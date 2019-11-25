---
title: 操作說明：從繫結的目標屬性取得繫結物件
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: cf2ddc93a7c46ee6956d2731a786289f64086360
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976426"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="3c272-102">操作說明：從繫結的目標屬性取得繫結物件</span><span class="sxs-lookup"><span data-stu-id="3c272-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="3c272-103">這個範例顯示如何從資料繫結目標屬性取得繫結物件。</span><span class="sxs-lookup"><span data-stu-id="3c272-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>

## <a name="example"></a><span data-ttu-id="3c272-104">範例</span><span class="sxs-lookup"><span data-stu-id="3c272-104">Example</span></span>
 <span data-ttu-id="3c272-105">您可以執行下列動作來取得 <xref:System.Windows.Data.Binding> 物件：</span><span class="sxs-lookup"><span data-stu-id="3c272-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>

 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]

> [!NOTE]
> <span data-ttu-id="3c272-106">因為目標物件可能有多個屬性使用資料繫結，所以必須指定所要繫結的相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="3c272-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>

 <span data-ttu-id="3c272-107">或者，您可以取得 <xref:System.Windows.Data.BindingExpression>，然後取得 <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="3c272-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>

 <span data-ttu-id="3c272-108">如需完整範例，請參閱[繫結驗證範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=159972)。</span><span class="sxs-lookup"><span data-stu-id="3c272-108">For the complete example see [Binding Validation Sample](https://go.microsoft.com/fwlink/?LinkID=159972).</span></span>

> [!NOTE]
> <span data-ttu-id="3c272-109">如果您的系結是 <xref:System.Windows.Data.MultiBinding>，請使用 <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="3c272-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3c272-110">如果是 <xref:System.Windows.Data.PriorityBinding>，請使用 <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="3c272-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3c272-111">如果您不確定目標屬性是使用 <xref:System.Windows.Data.Binding>、<xref:System.Windows.Data.MultiBinding>或 <xref:System.Windows.Data.PriorityBinding>來系結，您可以使用 <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="3c272-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c272-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c272-112">See also</span></span>

- [<span data-ttu-id="3c272-113">使用程式碼建立繫結</span><span class="sxs-lookup"><span data-stu-id="3c272-113">Create a Binding in Code</span></span>](how-to-create-a-binding-in-code.md)
- [<span data-ttu-id="3c272-114">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="3c272-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
