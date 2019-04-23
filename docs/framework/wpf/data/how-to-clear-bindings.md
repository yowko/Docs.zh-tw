---
title: HOW TO：清除繫結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: 8140928d44555e399ddf4ebd73407a251ad3cffe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101415"
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="b3081-102">HOW TO：清除繫結</span><span class="sxs-lookup"><span data-stu-id="b3081-102">How to: Clear Bindings</span></span>
<span data-ttu-id="b3081-103">這個範例顯示如何清除物件的繫結。</span><span class="sxs-lookup"><span data-stu-id="b3081-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3081-104">範例</span><span class="sxs-lookup"><span data-stu-id="b3081-104">Example</span></span>  
 <span data-ttu-id="b3081-105">若要清除物件個別屬性的繫結，請呼叫<xref:System.Windows.Data.BindingOperations.ClearBinding%2A>如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b3081-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="b3081-106">下列範例會移除從繫結<xref:System.Windows.Controls.TextBlock.TextProperty>的*mytext*、<xref:System.Windows.Controls.TextBlock>物件。</span><span class="sxs-lookup"><span data-stu-id="b3081-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="b3081-107">清除繫結會移除繫結，讓相依性屬性的值還原為沒有繫結時應該有的值。</span><span class="sxs-lookup"><span data-stu-id="b3081-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="b3081-108">這個值可以是預設值、繼承值或是資料範本繫結的值。</span><span class="sxs-lookup"><span data-stu-id="b3081-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="b3081-109">若要清除的物件上的所有可能屬性的繫結，請使用<xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>。</span><span class="sxs-lookup"><span data-stu-id="b3081-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3081-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3081-110">See also</span></span>

- <xref:System.Windows.Data.BindingOperations>
- [<span data-ttu-id="b3081-111">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="b3081-111">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="b3081-112">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="b3081-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
