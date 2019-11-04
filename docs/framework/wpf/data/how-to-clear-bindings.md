---
title: 操作說明：清除繫結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: 66f7eb0209d23660b9c7351ca793f509b2f4bb8d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458872"
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="c092b-102">操作說明：清除繫結</span><span class="sxs-lookup"><span data-stu-id="c092b-102">How to: Clear Bindings</span></span>
<span data-ttu-id="c092b-103">這個範例顯示如何清除物件的繫結。</span><span class="sxs-lookup"><span data-stu-id="c092b-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c092b-104">範例</span><span class="sxs-lookup"><span data-stu-id="c092b-104">Example</span></span>  
 <span data-ttu-id="c092b-105">若要清除物件上個別屬性的系結，請呼叫 <xref:System.Windows.Data.BindingOperations.ClearBinding%2A>，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c092b-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="c092b-106">下列範例會從*mytext*的 <xref:System.Windows.Controls.TextBlock.TextProperty> 中移除系結，<xref:System.Windows.Controls.TextBlock> 物件。</span><span class="sxs-lookup"><span data-stu-id="c092b-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="c092b-107">清除繫結會移除繫結，讓相依性屬性的值還原為沒有繫結時應該有的值。</span><span class="sxs-lookup"><span data-stu-id="c092b-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="c092b-108">這個值可以是預設值、繼承值或是資料範本繫結的值。</span><span class="sxs-lookup"><span data-stu-id="c092b-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="c092b-109">若要清除物件上所有可能屬性的系結，請使用 <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>。</span><span class="sxs-lookup"><span data-stu-id="c092b-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c092b-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="c092b-110">See also</span></span>

- <xref:System.Windows.Data.BindingOperations>
- [<span data-ttu-id="c092b-111">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="c092b-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c092b-112">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="c092b-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
