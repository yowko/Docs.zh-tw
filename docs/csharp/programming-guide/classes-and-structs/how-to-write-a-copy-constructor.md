---
title: 如何撰寫複製函式-程式C#設計指南
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: aa6feb1b07f491a90a78684e254910d387b9bccd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714845"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="d1438-102">如何撰寫複製函式（C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="d1438-102">How to write a copy constructor (C# Programming Guide)</span></span>
<span data-ttu-id="d1438-103">C# 未提供物件的複製建構函式，但您可以自行撰寫一個。</span><span class="sxs-lookup"><span data-stu-id="d1438-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1438-104">範例</span><span class="sxs-lookup"><span data-stu-id="d1438-104">Example</span></span>  
 <span data-ttu-id="d1438-105">在下列範例中，`Person`[類別](../../language-reference/keywords/class.md)定義接受 `Person` 執行個體作為其引數的複製建構函式。</span><span class="sxs-lookup"><span data-stu-id="d1438-105">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="d1438-106">引數的屬性值會指派給新 `Person` 執行個體的屬性。</span><span class="sxs-lookup"><span data-stu-id="d1438-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="d1438-107">這個程式碼包含替代的複製建構函式，可將您想要複製之執行個體的 `Name` 和 `Age` 屬性傳送給類別的執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="d1438-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="d1438-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="d1438-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="d1438-109">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d1438-109">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d1438-110">類別和結構</span><span class="sxs-lookup"><span data-stu-id="d1438-110">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="d1438-111">建構函式</span><span class="sxs-lookup"><span data-stu-id="d1438-111">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="d1438-112">完成項</span><span class="sxs-lookup"><span data-stu-id="d1438-112">Finalizers</span></span>](./destructors.md)
