---
title: HOW TO：組合委派 (多點傳送委派) - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: ebfcba4d2ebebe2697aa01b7109bbf50b8f144e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631551"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="582e3-102">HOW TO：組合委派 (多點傳送委派) (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="582e3-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="582e3-103">本例示範如何建立多點傳送委派。</span><span class="sxs-lookup"><span data-stu-id="582e3-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="582e3-104">[delegate](../../../csharp/language-reference/keywords/delegate.md) 物件有一個有用的屬性，是可以使用 `+` 運算子將多個物件指派給一個委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="582e3-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="582e3-105">多點傳送委派包含指派委派的清單。</span><span class="sxs-lookup"><span data-stu-id="582e3-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="582e3-106">呼叫多點傳送委派時，會依序叫用清單中的委派。</span><span class="sxs-lookup"><span data-stu-id="582e3-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="582e3-107">只有相同類型的委派可以合併。</span><span class="sxs-lookup"><span data-stu-id="582e3-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="582e3-108">您可使用 `-` 運算子從多點傳送委派移除元件委派。</span><span class="sxs-lookup"><span data-stu-id="582e3-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="582e3-109">範例</span><span class="sxs-lookup"><span data-stu-id="582e3-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="582e3-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="582e3-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="582e3-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="582e3-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="582e3-112">事件</span><span class="sxs-lookup"><span data-stu-id="582e3-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
