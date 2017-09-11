---
title: "命名空間 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
caps.latest.revision: 27
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
ms.openlocfilehash: a45339a4c3320a92c0339b1cad6345a2555ed920
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="940cd-102">命名空間 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="940cd-102">Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="940cd-103">C# 程式設計大量使用命名空間的原因有兩個。</span><span class="sxs-lookup"><span data-stu-id="940cd-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="940cd-104">首先，.NET Framework 會使用命名空間組織其多種類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="940cd-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 <span data-ttu-id="940cd-105">[!code-cs[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="940cd-105">[!code-cs[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]</span></span>  
  
 <span data-ttu-id="940cd-106">`System` 是命名空間，而 `Console` 是該命名空間中的類別。</span><span class="sxs-lookup"><span data-stu-id="940cd-106">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="940cd-107">您可以使用 `using` 關鍵字，如此就不需要完整名稱，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="940cd-107">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 <span data-ttu-id="940cd-108">[!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="940cd-108">[!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]</span></span>  
  
 <span data-ttu-id="940cd-109">[!code-cs[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="940cd-109">[!code-cs[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]</span></span>  
  
 <span data-ttu-id="940cd-110">如需詳細資訊，請參閱 [using 陳述式](../../../csharp/language-reference/keywords/using-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="940cd-110">For more information, see [using Directive](../../../csharp/language-reference/keywords/using-directive.md).</span></span>  
  
 <span data-ttu-id="940cd-111">其次，宣告您自己的命名空間，將有助於在較大型的程式設計專案中控制類別和方法名稱的範圍。</span><span class="sxs-lookup"><span data-stu-id="940cd-111">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="940cd-112">請使用 [namespace](../../../csharp/language-reference/keywords/namespace.md) 關鍵字宣告命名空間，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="940cd-112">Use the [namespace](../../../csharp/language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 <span data-ttu-id="940cd-113">[!code-cs[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="940cd-113">[!code-cs[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]</span></span>  
  
## <a name="namespaces-overview"></a><span data-ttu-id="940cd-114">命名空間概觀</span><span class="sxs-lookup"><span data-stu-id="940cd-114">Namespaces Overview</span></span>  
 <span data-ttu-id="940cd-115">命名空間具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="940cd-115">Namespaces have the following properties:</span></span>  
  
-   <span data-ttu-id="940cd-116">命名空間可組織大型程式碼專案。</span><span class="sxs-lookup"><span data-stu-id="940cd-116">They organize large code projects.</span></span>  
  
-   <span data-ttu-id="940cd-117">命名空間會使用 `.` 運算子分隔。</span><span class="sxs-lookup"><span data-stu-id="940cd-117">They are delimited by using the `.` operator.</span></span>  
  
-   <span data-ttu-id="940cd-118">`using directive` 讓您不需要指定每個類別的命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="940cd-118">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
  
-   <span data-ttu-id="940cd-119">`global` 命名空間是「根」命名空間：`global::System` 一律會參考 .NET Framework 命名空間 `System`。</span><span class="sxs-lookup"><span data-stu-id="940cd-119">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="940cd-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="940cd-120">Related Sections</span></span>  
 <span data-ttu-id="940cd-121">如需命名空間的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="940cd-121">See the following topics for more information about namespaces:</span></span>  
  
-   [<span data-ttu-id="940cd-122">使用命名空間</span><span class="sxs-lookup"><span data-stu-id="940cd-122">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="940cd-123">如何：使用全域命名空間別名</span><span class="sxs-lookup"><span data-stu-id="940cd-123">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [<span data-ttu-id="940cd-124">如何：使用 My 命名空間</span><span class="sxs-lookup"><span data-stu-id="940cd-124">How to: Use the My Namespace</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="940cd-125">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="940cd-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="940cd-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="940cd-126">See Also</span></span>  
 <span data-ttu-id="940cd-127">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="940cd-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="940cd-128">[命名空間關鍵字](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="940cd-128">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
 <span data-ttu-id="940cd-129">[using 指示詞](../../../csharp/language-reference/keywords/using-directive.md) </span><span class="sxs-lookup"><span data-stu-id="940cd-129">[using Directive](../../../csharp/language-reference/keywords/using-directive.md) </span></span>  
 <span data-ttu-id="940cd-130">[:: 運算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md) </span><span class="sxs-lookup"><span data-stu-id="940cd-130">[:: Operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md) </span></span>  
 [<span data-ttu-id="940cd-131">.運算子</span><span class="sxs-lookup"><span data-stu-id="940cd-131">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)

