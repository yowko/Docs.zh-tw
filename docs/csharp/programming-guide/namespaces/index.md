---
title: 命名空間 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 893ac7bbfcfe159787789238c3142f34ac7ecf35
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423296"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="b9b2e-102">命名空間 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b9b2e-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="b9b2e-103">C# 程式設計大量使用命名空間的原因有兩個。</span><span class="sxs-lookup"><span data-stu-id="b9b2e-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="b9b2e-104">首先，.NET Framework 會使用命名空間組織其多種類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b9b2e-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
<span data-ttu-id="b9b2e-105">`System` 是命名空間，而 `Console` 是該命名空間中的類別。</span><span class="sxs-lookup"><span data-stu-id="b9b2e-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="b9b2e-106">您可以使用 `using` 關鍵字，如此就不需要完整名稱，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b9b2e-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
<span data-ttu-id="b9b2e-107">如需詳細資訊，請參閱 [using 指示詞](../../language-reference/keywords/using-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="b9b2e-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>  
  
<span data-ttu-id="b9b2e-108">其次，宣告您自己的命名空間，將有助於在較大型的程式設計專案中控制類別和方法名稱的範圍。</span><span class="sxs-lookup"><span data-stu-id="b9b2e-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="b9b2e-109">請使用 [namespace](../../language-reference/keywords/namespace.md) 關鍵字宣告命名空間，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b9b2e-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="b9b2e-110">命名空間的名稱必須是有效的 C# [識別碼名稱](../inside-a-program/identifier-names.md)。</span><span class="sxs-lookup"><span data-stu-id="b9b2e-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="b9b2e-111">命名空間概觀</span><span class="sxs-lookup"><span data-stu-id="b9b2e-111">Namespaces Overview</span></span>  

<span data-ttu-id="b9b2e-112">命名空間具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b9b2e-112">Namespaces have the following properties:</span></span>  
  
- <span data-ttu-id="b9b2e-113">命名空間可組織大型程式碼專案。</span><span class="sxs-lookup"><span data-stu-id="b9b2e-113">They organize large code projects.</span></span>  
- <span data-ttu-id="b9b2e-114">命名空間會使用 `.` 運算子分隔。</span><span class="sxs-lookup"><span data-stu-id="b9b2e-114">They are delimited by using the `.` operator.</span></span>  
- <span data-ttu-id="b9b2e-115">`using` 指示詞讓您不需要指定每個類別的命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="b9b2e-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>  
- <span data-ttu-id="b9b2e-116">`global` 命名空間是「根」命名空間：`global::System` 一律會參考 .NET <xref:System> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="b9b2e-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="b9b2e-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b9b2e-117">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b9b2e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9b2e-118">See also</span></span>

- [<span data-ttu-id="b9b2e-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b9b2e-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b9b2e-120">使用命名空間</span><span class="sxs-lookup"><span data-stu-id="b9b2e-120">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="b9b2e-121">如何：使用全域命名空間別名</span><span class="sxs-lookup"><span data-stu-id="b9b2e-121">How to: Use the Global Namespace Alias</span></span>](how-to-use-the-global-namespace-alias.md)
- [<span data-ttu-id="b9b2e-122">如何：使用 My 命名空間</span><span class="sxs-lookup"><span data-stu-id="b9b2e-122">How to: Use the My Namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="b9b2e-123">識別碼名稱</span><span class="sxs-lookup"><span data-stu-id="b9b2e-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="b9b2e-124">using 指示詞</span><span class="sxs-lookup"><span data-stu-id="b9b2e-124">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="b9b2e-125">::運算子</span><span class="sxs-lookup"><span data-stu-id="b9b2e-125">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifer.md)
