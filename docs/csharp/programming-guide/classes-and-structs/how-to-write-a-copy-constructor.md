---
title: '如何撰寫複製方法-c # 程式設計手冊'
description: '瞭解如何在 c # 中撰寫使用類別實例的複製程式，並傳回具有輸入值的新實例。'
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: beb2fcfaa36303eeaabd5278cf5e7a128282270e
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864224"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="e4704-103">如何撰寫複製函式（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="e4704-103">How to write a copy constructor (C# Programming Guide)</span></span>
<span data-ttu-id="e4704-104">C# 未提供物件的複製建構函式，但您可以自行撰寫一個。</span><span class="sxs-lookup"><span data-stu-id="e4704-104">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4704-105">範例</span><span class="sxs-lookup"><span data-stu-id="e4704-105">Example</span></span>  
 <span data-ttu-id="e4704-106">在下列範例中，`Person`[類別](../../language-reference/keywords/class.md)定義接受 `Person` 執行個體作為其引數的複製建構函式。</span><span class="sxs-lookup"><span data-stu-id="e4704-106">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="e4704-107">引數的屬性值會指派給新 `Person` 執行個體的屬性。</span><span class="sxs-lookup"><span data-stu-id="e4704-107">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="e4704-108">這個程式碼包含替代的複製建構函式，可將您想要複製之執行個體的 `Name` 和 `Age` 屬性傳送給類別的執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="e4704-108">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="e4704-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4704-109">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="e4704-110">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e4704-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e4704-111">類別和結構</span><span class="sxs-lookup"><span data-stu-id="e4704-111">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="e4704-112">建構函式</span><span class="sxs-lookup"><span data-stu-id="e4704-112">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="e4704-113">完成項</span><span class="sxs-lookup"><span data-stu-id="e4704-113">Finalizers</span></span>](./destructors.md)
