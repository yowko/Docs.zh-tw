---
title: 如何：撰寫複製建構函式 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: d6ecfc3659dcf533db0f4e7b67fdffd620a584fd
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47232699"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="e14a5-102">如何：撰寫複製建構函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e14a5-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="e14a5-103">C# 未提供物件的複製建構函式，但您可以自行撰寫一個。</span><span class="sxs-lookup"><span data-stu-id="e14a5-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e14a5-104">範例</span><span class="sxs-lookup"><span data-stu-id="e14a5-104">Example</span></span>  
 <span data-ttu-id="e14a5-105">在下列範例中，`Person`[類別](../../../csharp/language-reference/keywords/class.md)定義接受 `Person` 執行個體作為其引數的複製建構函式。</span><span class="sxs-lookup"><span data-stu-id="e14a5-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="e14a5-106">引數的屬性值會指派給新 `Person` 執行個體的屬性。</span><span class="sxs-lookup"><span data-stu-id="e14a5-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="e14a5-107">這個程式碼包含替代的複製建構函式，可將您想要複製之執行個體的 `Name` 和 `Age` 屬性傳送給類別的執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="e14a5-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e14a5-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="e14a5-108">See Also</span></span>

- <xref:System.ICloneable>  
- [<span data-ttu-id="e14a5-109">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e14a5-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e14a5-110">類別和結構</span><span class="sxs-lookup"><span data-stu-id="e14a5-110">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="e14a5-111">建構函式</span><span class="sxs-lookup"><span data-stu-id="e14a5-111">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [<span data-ttu-id="e14a5-112">完成項</span><span class="sxs-lookup"><span data-stu-id="e14a5-112">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
