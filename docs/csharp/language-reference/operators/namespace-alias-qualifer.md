---
title: ':: 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 077d5835b372897cbe797385271effc5d00bf6e3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43473969"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="96814-102">:: 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="96814-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="96814-103">命名空間別名限定詞 (`::`) 用來查閱識別碼。</span><span class="sxs-lookup"><span data-stu-id="96814-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="96814-104">它一律位在兩個識別碼之間，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="96814-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  

<span data-ttu-id="96814-105">`::` 運算子也可以搭配「using alias 指示詞」使用：</span><span class="sxs-lookup"><span data-stu-id="96814-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="96814-106">備註</span><span class="sxs-lookup"><span data-stu-id="96814-106">Remarks</span></span>  
 <span data-ttu-id="96814-107">命名空間別名限定詞可以是 `global`。</span><span class="sxs-lookup"><span data-stu-id="96814-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="96814-108">這會在全域命名空間中叫用查詢，不是在別名命名空間中。</span><span class="sxs-lookup"><span data-stu-id="96814-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="96814-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="96814-109">For More Information</span></span>  
 <span data-ttu-id="96814-110">如需如何使用 `::` 運算子的範例，請參閱下一節︰</span><span class="sxs-lookup"><span data-stu-id="96814-110">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="96814-111">如何：使用全域命名空間別名</span><span class="sxs-lookup"><span data-stu-id="96814-111">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="96814-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="96814-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="96814-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="96814-113">See Also</span></span>

- [<span data-ttu-id="96814-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="96814-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="96814-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="96814-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="96814-116">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="96814-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="96814-117">命名空間關鍵字</span><span class="sxs-lookup"><span data-stu-id="96814-117">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="96814-118">.運算子</span><span class="sxs-lookup"><span data-stu-id="96814-118">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="96814-119">外部別名</span><span class="sxs-lookup"><span data-stu-id="96814-119">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
