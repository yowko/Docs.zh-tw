---
title: ":: 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ::_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
caps.latest.revision: 21
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
ms.openlocfilehash: 97b9fa706669244ac579602a107c092e8593567d
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="00c8f-102">:: 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="00c8f-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="00c8f-103">命名空間別名限定詞 (`::`) 用來查閱識別碼。</span><span class="sxs-lookup"><span data-stu-id="00c8f-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="00c8f-104">它一律位在兩個識別碼之間，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="00c8f-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 <span data-ttu-id="00c8f-105">[!code-cs[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="00c8f-105">[!code-cs[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00c8f-106">備註</span><span class="sxs-lookup"><span data-stu-id="00c8f-106">Remarks</span></span>  
 <span data-ttu-id="00c8f-107">命名空間別名限定詞可以是 `global`。</span><span class="sxs-lookup"><span data-stu-id="00c8f-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="00c8f-108">這會在全域命名空間中叫用查詢，不是在別名命名空間中。</span><span class="sxs-lookup"><span data-stu-id="00c8f-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="00c8f-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="00c8f-109">For More Information</span></span>  
 <span data-ttu-id="00c8f-110">如需如何使用 `::` 運算子的範例，請參閱下一節︰</span><span class="sxs-lookup"><span data-stu-id="00c8f-110">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="00c8f-111">如何：使用全域命名空間別名</span><span class="sxs-lookup"><span data-stu-id="00c8f-111">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="00c8f-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="00c8f-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="00c8f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00c8f-113">See Also</span></span>  
 <span data-ttu-id="00c8f-114">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="00c8f-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="00c8f-115">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="00c8f-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="00c8f-116">[C# 運算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="00c8f-116">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="00c8f-117">[命名空間關鍵字](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="00c8f-117">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
 <span data-ttu-id="00c8f-118">[.運算子](../../../csharp/language-reference/operators/member-access-operator.md) </span><span class="sxs-lookup"><span data-stu-id="00c8f-118">[. Operator](../../../csharp/language-reference/operators/member-access-operator.md) </span></span>  
 [<span data-ttu-id="00c8f-119">外部別名</span><span class="sxs-lookup"><span data-stu-id="00c8f-119">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)

