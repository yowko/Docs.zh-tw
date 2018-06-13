---
title: 。 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 088f1991cafa92a69e11ca14bd2d983b36c0e3ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271025"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8a924-103">。</span><span class="sxs-lookup"><span data-stu-id="8a924-103">.</span></span> <span data-ttu-id="8a924-104">運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8a924-104">Operator (C# Reference)</span></span>
<span data-ttu-id="8a924-105">點運算子 (`.`) 是用於成員存取。</span><span class="sxs-lookup"><span data-stu-id="8a924-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="8a924-106">點運算子可指定型別或命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="8a924-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="8a924-107">例如，點運算子可用來存取 .NET Framework 類別庫中的特定方法：</span><span class="sxs-lookup"><span data-stu-id="8a924-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 <span data-ttu-id="8a924-108">例如，請參考下列類別：</span><span class="sxs-lookup"><span data-stu-id="8a924-108">For example, consider the following class:</span></span>  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 <span data-ttu-id="8a924-109">變數 `s` 擁有 `a` 和 `b` 兩個成員；若要存取它們，請使用點運算子：</span><span class="sxs-lookup"><span data-stu-id="8a924-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 <span data-ttu-id="8a924-110">點也可用來形成限定名稱，例如指定其所屬命名空間或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="8a924-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 <span data-ttu-id="8a924-111">using 指示詞可讓某些名稱限定成為選擇性項目：</span><span class="sxs-lookup"><span data-stu-id="8a924-111">The using directive makes some name qualification optional:</span></span>  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 <span data-ttu-id="8a924-112">但若是模稜兩可的識別項，就必須加以限定：</span><span class="sxs-lookup"><span data-stu-id="8a924-112">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8a924-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="8a924-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8a924-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a924-114">See Also</span></span>  
 [<span data-ttu-id="8a924-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="8a924-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8a924-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8a924-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8a924-117">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="8a924-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
