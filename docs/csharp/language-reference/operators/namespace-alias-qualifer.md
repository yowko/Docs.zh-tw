---
title: ":: 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6b4f1683e1250ed745e15ced88203ca942c75ff8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="68014-102">:: 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="68014-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="68014-103">命名空間別名限定詞 (`::`) 用來查閱識別碼。</span><span class="sxs-lookup"><span data-stu-id="68014-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="68014-104">它一律位在兩個識別碼之間，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="68014-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="68014-105">備註</span><span class="sxs-lookup"><span data-stu-id="68014-105">Remarks</span></span>  
 <span data-ttu-id="68014-106">命名空間別名限定詞可以是 `global`。</span><span class="sxs-lookup"><span data-stu-id="68014-106">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="68014-107">這會在全域命名空間中叫用查詢，不是在別名命名空間中。</span><span class="sxs-lookup"><span data-stu-id="68014-107">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="68014-108">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="68014-108">For More Information</span></span>  
 <span data-ttu-id="68014-109">如需如何使用 `::` 運算子的範例，請參閱下一節︰</span><span class="sxs-lookup"><span data-stu-id="68014-109">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="68014-110">如何：使用全域命名空間別名</span><span class="sxs-lookup"><span data-stu-id="68014-110">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="68014-111">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="68014-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="68014-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68014-112">See Also</span></span>  
 [<span data-ttu-id="68014-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="68014-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="68014-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="68014-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="68014-115">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="68014-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="68014-116">命名空間關鍵字</span><span class="sxs-lookup"><span data-stu-id="68014-116">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="68014-117">.運算子</span><span class="sxs-lookup"><span data-stu-id="68014-117">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="68014-118">外部別名</span><span class="sxs-lookup"><span data-stu-id="68014-118">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
