---
title: "?? 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ??_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 86e50b97d7ded8adc74f031faf026b69ccdd0c87
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="aeba0-103">??</span><span class="sxs-lookup"><span data-stu-id="aeba0-103">??</span></span> <span data-ttu-id="aeba0-104">運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="aeba0-104">Operator (C# Reference)</span></span>
<span data-ttu-id="aeba0-105">`??` 運算子稱為 null 聯合運算子。</span><span class="sxs-lookup"><span data-stu-id="aeba0-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="aeba0-106">如果運算元不是 null，則會傳回左方運算元，否則傳回右方運算元。</span><span class="sxs-lookup"><span data-stu-id="aeba0-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aeba0-107">備註</span><span class="sxs-lookup"><span data-stu-id="aeba0-107">Remarks</span></span>  
 <span data-ttu-id="aeba0-108">可為 Null 的類型可以表示來自類型網域的值，或值可以是未定義 (這種情況下，值為 null)。</span><span class="sxs-lookup"><span data-stu-id="aeba0-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="aeba0-109">當左方運算元是可為 null 類型且其值為 null 時，您可以使用 `??` 運算子的語法表達能力傳回適當的值 (右方運算元)。</span><span class="sxs-lookup"><span data-stu-id="aeba0-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullible type whose value is null.</span></span> <span data-ttu-id="aeba0-110">如果您嘗試在不使用 `??` 運算子的情況下，將可為 null 的實值類型指派給不可為 null 的實值類型，則會產生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="aeba0-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="aeba0-111">如果您使用轉型，而可為 null 的實值類型目前為未定義，則會擲回 `InvalidOperationException` 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="aeba0-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>  
  
 <span data-ttu-id="aeba0-112">如需詳細資訊，請參閱[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="aeba0-112">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="aeba0-113">?? 運算子的結果</span><span class="sxs-lookup"><span data-stu-id="aeba0-113">The result of a ??</span></span> <span data-ttu-id="aeba0-114">不視為常數，即使它的兩個引數都是常數。</span><span class="sxs-lookup"><span data-stu-id="aeba0-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeba0-115">範例</span><span class="sxs-lookup"><span data-stu-id="aeba0-115">Example</span></span>  
 <span data-ttu-id="aeba0-116">[!code-cs[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="aeba0-116">[!code-cs[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeba0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aeba0-117">See Also</span></span>  
 <span data-ttu-id="aeba0-118">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="aeba0-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="aeba0-119">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="aeba0-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="aeba0-120">[C# 運算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="aeba0-120">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="aeba0-121">[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="aeba0-121">[Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) </span></span>  
 [<span data-ttu-id="aeba0-122">「增益」(Lift) 的真正意義是什麼？</span><span class="sxs-lookup"><span data-stu-id="aeba0-122">What Exactly Does 'Lifted' mean?</span></span>](http://go.microsoft.com/fwlink/?LinkID=112382)

