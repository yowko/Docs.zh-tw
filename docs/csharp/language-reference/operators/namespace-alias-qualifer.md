---
title: ::運算子 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 2e456be075f3487676228244e0119ff46ed9a538
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243474"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="90c00-102">::運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="90c00-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="90c00-103">命名空間別名限定詞 (`::`) 用來查閱識別碼。</span><span class="sxs-lookup"><span data-stu-id="90c00-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="90c00-104">它一律位在兩個識別碼之間，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="90c00-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  

<span data-ttu-id="90c00-105">`::` 運算子也可以搭配「using alias 指示詞」使用：</span><span class="sxs-lookup"><span data-stu-id="90c00-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="90c00-106">備註</span><span class="sxs-lookup"><span data-stu-id="90c00-106">Remarks</span></span>  
 <span data-ttu-id="90c00-107">命名空間別名限定詞可以是 `global`。</span><span class="sxs-lookup"><span data-stu-id="90c00-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="90c00-108">這會在全域命名空間中叫用查詢，不是在別名命名空間中。</span><span class="sxs-lookup"><span data-stu-id="90c00-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="90c00-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="90c00-109">For More Information</span></span>  
 <span data-ttu-id="90c00-110">如需如何使用 `::` 運算子的範例，請參閱下一節︰</span><span class="sxs-lookup"><span data-stu-id="90c00-110">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="90c00-111">如何：使用全域命名空間別名</span><span class="sxs-lookup"><span data-stu-id="90c00-111">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="90c00-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="90c00-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="90c00-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="90c00-113">See Also</span></span>

- [<span data-ttu-id="90c00-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="90c00-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="90c00-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="90c00-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="90c00-116">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="90c00-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="90c00-117">命名空間關鍵字</span><span class="sxs-lookup"><span data-stu-id="90c00-117">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="90c00-118">.運算子</span><span class="sxs-lookup"><span data-stu-id="90c00-118">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="90c00-119">外部別名</span><span class="sxs-lookup"><span data-stu-id="90c00-119">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
