---
title: 如何：使用 as 和 is 運算子進行安全轉型 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
ms.openlocfilehash: 8e0b17122bd23a7de82ca1c210a559fe09ad7fee
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508114"
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a><span data-ttu-id="2de09-102">如何：使用 as 和 is 運算子進行安全轉型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="2de09-102">How to: Safely Cast by Using as and is Operators (C# Programming Guide)</span></span>
<span data-ttu-id="2de09-103">因為物件都是多型的，所以可能會針對基底類別類型的變數來保存衍生類型。</span><span class="sxs-lookup"><span data-stu-id="2de09-103">Because objects are polymorphic, it is possible for a variable of a base class type to hold a derived type.</span></span> <span data-ttu-id="2de09-104">若要存取衍生類型的執行個體方法，就需要將值轉換回衍生類型。</span><span class="sxs-lookup"><span data-stu-id="2de09-104">To access the derived type's instance methods, it is necessary to cast the value back to the derived type.</span></span> <span data-ttu-id="2de09-105">不過，在這些情況下嘗試簡單轉換，會造成擲回 <xref:System.InvalidCastException> 的風險。</span><span class="sxs-lookup"><span data-stu-id="2de09-105">However, to attempt a simple cast in these cases creates the risk of throwing an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="2de09-106">這也就是為什麼 C# 提供 [is](../../../csharp/language-reference/keywords/is.md) 和 [as](../../../csharp/language-reference/keywords/as.md) 運算子的原因。</span><span class="sxs-lookup"><span data-stu-id="2de09-106">That is why C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators.</span></span> <span data-ttu-id="2de09-107">您可以使用這些運算子，來測試轉換是否成功而不會造成擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2de09-107">You can use these operators to test whether a cast will succeed without causing an exception to be thrown.</span></span> <span data-ttu-id="2de09-108">一般來說，`as` 運算子更有效率，因為如果轉換順利完成，它實際上會傳回轉換值。</span><span class="sxs-lookup"><span data-stu-id="2de09-108">In general, the `as` operator is more efficient because it actually returns the cast value if the cast can be made successfully.</span></span> <span data-ttu-id="2de09-109">`is` 運算子只會傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="2de09-109">The `is` operator returns only a Boolean value.</span></span> <span data-ttu-id="2de09-110">因此，當您只想要判斷物件的類型而不需要實際轉換時，才會使用此運算子。</span><span class="sxs-lookup"><span data-stu-id="2de09-110">It can therefore be used when you just want to determine an object's type but do not have to actually cast it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2de09-111">範例</span><span class="sxs-lookup"><span data-stu-id="2de09-111">Example</span></span>  
 <span data-ttu-id="2de09-112">下列範例示範如何使用 `is` 和 `as` 運算子將某個參考型別轉換成另一個參考型別，而不會造成擲回例外狀況的風險。</span><span class="sxs-lookup"><span data-stu-id="2de09-112">The following examples show how to use the `is` and `as` operators to cast from one reference type to another without the risk of throwing an exception.</span></span> <span data-ttu-id="2de09-113">此範例也示範如何使用 `as` 運算子與可為 Null 的實值型別。</span><span class="sxs-lookup"><span data-stu-id="2de09-113">The example also shows how to use the `as` operator with nullable value types.</span></span>  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2de09-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="2de09-114">See Also</span></span>

- [<span data-ttu-id="2de09-115">型別</span><span class="sxs-lookup"><span data-stu-id="2de09-115">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
- [<span data-ttu-id="2de09-116">轉換和型別轉換</span><span class="sxs-lookup"><span data-stu-id="2de09-116">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
- [<span data-ttu-id="2de09-117">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="2de09-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
