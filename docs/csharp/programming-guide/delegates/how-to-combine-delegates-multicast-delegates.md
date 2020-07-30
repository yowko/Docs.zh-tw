---
title: '如何合併委派（多播委派）-c # 程式設計指南'
description: 瞭解如何結合委派來建立多播委派。 查看程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d23ea758c9da2c3399f5d98e81360cc250b428a1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302733"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="0b4bc-104">如何合併委派 (多點傳送委派) (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="0b4bc-104">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="0b4bc-105">本例示範如何建立多點傳送委派。</span><span class="sxs-lookup"><span data-stu-id="0b4bc-105">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="0b4bc-106">[delegate](../../language-reference/builtin-types/reference-types.md) 物件有一個有用的屬性，是可以使用 `+` 運算子將多個物件指派給一個委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="0b4bc-106">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="0b4bc-107">多點傳送委派包含指派委派的清單。</span><span class="sxs-lookup"><span data-stu-id="0b4bc-107">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="0b4bc-108">呼叫多點傳送委派時，會依序叫用清單中的委派。</span><span class="sxs-lookup"><span data-stu-id="0b4bc-108">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="0b4bc-109">只有相同類型的委派可以合併。</span><span class="sxs-lookup"><span data-stu-id="0b4bc-109">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="0b4bc-110">您可使用 `-` 運算子從多點傳送委派移除元件委派。</span><span class="sxs-lookup"><span data-stu-id="0b4bc-110">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b4bc-111">範例</span><span class="sxs-lookup"><span data-stu-id="0b4bc-111">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="0b4bc-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b4bc-112">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="0b4bc-113">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0b4bc-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0b4bc-114">事件</span><span class="sxs-lookup"><span data-stu-id="0b4bc-114">Events</span></span>](../events/index.md)
