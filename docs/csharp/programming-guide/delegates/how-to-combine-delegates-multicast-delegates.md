---
title: 如何組合委託（多播代表） - C# 程式設計指南
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705375"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="0a395-102">如何合併委派 (多點傳送委派) (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="0a395-102">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="0a395-103">本例示範如何建立多點傳送委派。</span><span class="sxs-lookup"><span data-stu-id="0a395-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="0a395-104">[delegate](../../language-reference/builtin-types/reference-types.md) 物件有一個有用的屬性，是可以使用 `+` 運算子將多個物件指派給一個委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a395-104">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="0a395-105">多點傳送委派包含指派委派的清單。</span><span class="sxs-lookup"><span data-stu-id="0a395-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="0a395-106">呼叫多點傳送委派時，會依序叫用清單中的委派。</span><span class="sxs-lookup"><span data-stu-id="0a395-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="0a395-107">只有相同類型的委派可以合併。</span><span class="sxs-lookup"><span data-stu-id="0a395-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="0a395-108">您可使用 `-` 運算子從多點傳送委派移除元件委派。</span><span class="sxs-lookup"><span data-stu-id="0a395-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a395-109">範例</span><span class="sxs-lookup"><span data-stu-id="0a395-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="0a395-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a395-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="0a395-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0a395-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0a395-112">事件</span><span class="sxs-lookup"><span data-stu-id="0a395-112">Events</span></span>](../events/index.md)
