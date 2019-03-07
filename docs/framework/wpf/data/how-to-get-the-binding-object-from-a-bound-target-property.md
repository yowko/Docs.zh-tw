---
title: HOW TO：從繫結的目標屬性取得繫結物件
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: af18cf3fc155148816690bdd16baa3a2a5515eee
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368515"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="ddf33-102">HOW TO：從繫結的目標屬性取得繫結物件</span><span class="sxs-lookup"><span data-stu-id="ddf33-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="ddf33-103">這個範例顯示如何從資料繫結目標屬性取得繫結物件。</span><span class="sxs-lookup"><span data-stu-id="ddf33-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddf33-104">範例</span><span class="sxs-lookup"><span data-stu-id="ddf33-104">Example</span></span>  
 <span data-ttu-id="ddf33-105">您可以執行下列命令，以取得<xref:System.Windows.Data.Binding>物件：</span><span class="sxs-lookup"><span data-stu-id="ddf33-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  <span data-ttu-id="ddf33-106">因為目標物件可能有多個屬性使用資料繫結，所以必須指定所要繫結的相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="ddf33-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>  
  
 <span data-ttu-id="ddf33-107">或者，您可以取得<xref:System.Windows.Data.BindingExpression>，然後取得的值<xref:System.Windows.Data.BindingExpression.ParentBinding%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ddf33-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>  
  
 <span data-ttu-id="ddf33-108">如需完整範例，請參閱[繫結驗證範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=159972)。</span><span class="sxs-lookup"><span data-stu-id="ddf33-108">For the complete example see [Binding Validation Sample](https://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddf33-109">如果您繫結是<xref:System.Windows.Data.MultiBinding>，使用<xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>。</span><span class="sxs-lookup"><span data-stu-id="ddf33-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span></span> <span data-ttu-id="ddf33-110">如果是<xref:System.Windows.Data.PriorityBinding>，使用<xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>。</span><span class="sxs-lookup"><span data-stu-id="ddf33-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span></span> <span data-ttu-id="ddf33-111">如果您不確定是否目標屬性會使用繫結<xref:System.Windows.Data.Binding>、 <xref:System.Windows.Data.MultiBinding>，或<xref:System.Windows.Data.PriorityBinding>，您可以使用<xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>。</span><span class="sxs-lookup"><span data-stu-id="ddf33-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddf33-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddf33-112">See also</span></span>
- [<span data-ttu-id="ddf33-113">使用程式碼建立繫結</span><span class="sxs-lookup"><span data-stu-id="ddf33-113">Create a Binding in Code</span></span>](how-to-create-a-binding-in-code.md)
- [<span data-ttu-id="ddf33-114">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="ddf33-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
