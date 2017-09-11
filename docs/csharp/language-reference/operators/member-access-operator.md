---
title: ". 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ._CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
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
ms.openlocfilehash: fdc7c1821548509f3a3750aef2836c034f7aa53b
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="ca32c-103">。</span><span class="sxs-lookup"><span data-stu-id="ca32c-103">.</span></span> <span data-ttu-id="ca32c-104">運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ca32c-104">Operator (C# Reference)</span></span>
<span data-ttu-id="ca32c-105">點運算子 (`.`) 是用於成員存取。</span><span class="sxs-lookup"><span data-stu-id="ca32c-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="ca32c-106">點運算子可指定型別或命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="ca32c-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="ca32c-107">例如，點運算子可用來存取 .NET Framework 類別庫中的特定方法：</span><span class="sxs-lookup"><span data-stu-id="ca32c-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 <span data-ttu-id="ca32c-108">[!code-cs[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ca32c-108">[!code-cs[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="ca32c-109">例如，請參考下列類別：</span><span class="sxs-lookup"><span data-stu-id="ca32c-109">For example, consider the following class:</span></span>  
  
 <span data-ttu-id="ca32c-110">[!code-cs[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ca32c-110">[!code-cs[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]</span></span>  
  
 <span data-ttu-id="ca32c-111">[!code-cs[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="ca32c-111">[!code-cs[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]</span></span>  
  
 <span data-ttu-id="ca32c-112">變數 `s` 擁有 `a` 和 `b` 兩個成員；若要存取它們，請使用點運算子：</span><span class="sxs-lookup"><span data-stu-id="ca32c-112">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 <span data-ttu-id="ca32c-113">[!code-cs[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="ca32c-113">[!code-cs[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]</span></span>  
  
 <span data-ttu-id="ca32c-114">點也可用來形成限定名稱，例如指定其所屬命名空間或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="ca32c-114">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 <span data-ttu-id="ca32c-115">[!code-cs[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="ca32c-115">[!code-cs[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]</span></span>  
  
 <span data-ttu-id="ca32c-116">using 指示詞可讓某些名稱限定成為選擇性項目：</span><span class="sxs-lookup"><span data-stu-id="ca32c-116">The using directive makes some name qualification optional:</span></span>  
  
 <span data-ttu-id="ca32c-117">[!code-cs[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="ca32c-117">[!code-cs[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]</span></span>  
  
 <span data-ttu-id="ca32c-118">但若是模稜兩可的識別項，就必須加以限定：</span><span class="sxs-lookup"><span data-stu-id="ca32c-118">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 <span data-ttu-id="ca32c-119">[!code-cs[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="ca32c-119">[!code-cs[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ca32c-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ca32c-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ca32c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca32c-121">See Also</span></span>  
 <span data-ttu-id="ca32c-122">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ca32c-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ca32c-123">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ca32c-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="ca32c-124">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="ca32c-124">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

