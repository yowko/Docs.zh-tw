---
title: 如何：取得指標變數值 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 66f341e193a0f018adb76a40617f85266519e602
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "45746584"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="82d24-102">如何：取得指標變數值 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="82d24-102">How to: Obtain the Value of a Pointer Variable (C# Programming Guide)</span></span>
<span data-ttu-id="82d24-103">您可以使用指標間接運算子來取得指標所指向位置的變數。</span><span class="sxs-lookup"><span data-stu-id="82d24-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="82d24-104">運算式會採用下列格式，其中 `p` 是指標類型：</span><span class="sxs-lookup"><span data-stu-id="82d24-104">The expression takes the following form, where `p` is a pointer type:</span></span>  
  
```  
*p;  
```  
  
 <span data-ttu-id="82d24-105">您無法在非指標類型之任何類型的運算式上使用一元間接運算子。</span><span class="sxs-lookup"><span data-stu-id="82d24-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="82d24-106">此外，也無法將它套用至 [void](../../../csharp/language-reference/keywords/void.md) 指標。</span><span class="sxs-lookup"><span data-stu-id="82d24-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  
  
 <span data-ttu-id="82d24-107">當您將間接運算子套用至 [null](../../../csharp/language-reference/keywords/null.md) 指標時，結果會取決於實作。</span><span class="sxs-lookup"><span data-stu-id="82d24-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82d24-108">範例</span><span class="sxs-lookup"><span data-stu-id="82d24-108">Example</span></span>  
 <span data-ttu-id="82d24-109">在下列範例中，`char` 類型的變數會使用不同類型的指標來存取。</span><span class="sxs-lookup"><span data-stu-id="82d24-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="82d24-110">請注意，`theChar` 的位址會因執行而異，原因是配置給變數的實體位址可能會變更。</span><span class="sxs-lookup"><span data-stu-id="82d24-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
<span data-ttu-id="82d24-111">**theChar 的值 = Z**
**theChar 的位址 = 12F718**
**pChar 的值 = Z**
**pInt 的值 = 90**</span><span class="sxs-lookup"><span data-stu-id="82d24-111">**Value of theChar = Z**
**Address of theChar = 12F718**
**Value of pChar = Z**
**Value of pInt = 90**</span></span>

## <a name="see-also"></a><span data-ttu-id="82d24-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="82d24-112">See Also</span></span>

- [<span data-ttu-id="82d24-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="82d24-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="82d24-114">指標運算式</span><span class="sxs-lookup"><span data-stu-id="82d24-114">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="82d24-115">指標型別</span><span class="sxs-lookup"><span data-stu-id="82d24-115">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="82d24-116">型別</span><span class="sxs-lookup"><span data-stu-id="82d24-116">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="82d24-117">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="82d24-117">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="82d24-118">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="82d24-118">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="82d24-119">stackalloc</span><span class="sxs-lookup"><span data-stu-id="82d24-119">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
