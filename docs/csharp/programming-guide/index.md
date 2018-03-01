---
title: "C# 程式設計手冊"
ms.date: 05/02/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.langref
helpviewer_keywords:
- reference tables [C#]
- C# language, programming guide
- Visual C#, programming concepts
- C# language, concepts
ms.assetid: ac0f23a2-6bf3-4077-be99-538ae5fd3bc5
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bd22abedc8fc43fd2bd0ea77e1506394400fbfbb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="c-programming-guide"></a><span data-ttu-id="ecfba-102">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="ecfba-102">C# programming guide</span></span>
<span data-ttu-id="ecfba-103">本節提供可透過 .NET Framework 存取 C# 的重要 C# 語言特性與功能的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ecfba-103">This section provides detailed information on key C# language features and features accessible to C# through the .NET Framework.</span></span>  
  
 <span data-ttu-id="ecfba-104">本節內容中大部分會假設您已經了解一些 C# 和一般程式設計概念。</span><span class="sxs-lookup"><span data-stu-id="ecfba-104">Most of this section assumes that you already know something about C# and general programming concepts.</span></span> <span data-ttu-id="ecfba-105">如果您是 C# 程式設計或 C# 的新手，您可能想要瀏覽 [C# 使用者入門](https://www.microsoft.com/net/tutorials/csharp/getting-started)互動式教學課程，而不需要事先具備程式設計知識。</span><span class="sxs-lookup"><span data-stu-id="ecfba-105">If you are a complete beginner with programming or with C#, you might want to visit the [Getting Started with C#](https://www.microsoft.com/net/tutorials/csharp/getting-started) interactive tutorial, where no prior programming knowledge is required.</span></span>  
  
 <span data-ttu-id="ecfba-106">如需特定關鍵字、運算子和前置處理器指示詞的相關資訊，請參閱 [C# 參考](../../csharp/language-reference/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ecfba-106">For information about specific keywords, operators and preprocessor directives, see [C# Reference](../../csharp/language-reference/index.md).</span></span> <span data-ttu-id="ecfba-107">如需 C# 語言規格的相關資訊，請參閱 [C# 語言規格](../../csharp/language-reference/language-specification/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ecfba-107">For information about the C# Language Specification, see [C# Language Specification](../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="program-sections"></a><span data-ttu-id="ecfba-108">程式區段</span><span class="sxs-lookup"><span data-stu-id="ecfba-108">Program sections</span></span>

[<span data-ttu-id="ecfba-109">C# 程式內部</span><span class="sxs-lookup"><span data-stu-id="ecfba-109">Inside a C# Program</span></span>](../../csharp/programming-guide/inside-a-program/index.md)  
  
[<span data-ttu-id="ecfba-110">Main() 和命令列引數</span><span class="sxs-lookup"><span data-stu-id="ecfba-110">Main() and Command-Line Arguments</span></span>](../../csharp/programming-guide/main-and-command-args/index.md)  
 
## <a name="language-sections"></a><span data-ttu-id="ecfba-111">語言章節</span><span class="sxs-lookup"><span data-stu-id="ecfba-111">Language Sections</span></span>  
[<span data-ttu-id="ecfba-112">陳述式、運算式和運算子</span><span class="sxs-lookup"><span data-stu-id="ecfba-112">Statements, Expressions, and Operators</span></span>](../../csharp/programming-guide/statements-expressions-operators/index.md)  

 [<span data-ttu-id="ecfba-113">型別</span><span class="sxs-lookup"><span data-stu-id="ecfba-113">Types</span></span>](../../csharp/programming-guide/types/index.md)  

 [<span data-ttu-id="ecfba-114">類別和結構</span><span class="sxs-lookup"><span data-stu-id="ecfba-114">Classes and Structs</span></span>](../../csharp/programming-guide/classes-and-structs/index.md)  
  
 [<span data-ttu-id="ecfba-115">介面</span><span class="sxs-lookup"><span data-stu-id="ecfba-115">Interfaces</span></span>](../../csharp/programming-guide/interfaces/index.md)  

 [<span data-ttu-id="ecfba-116">列舉型別</span><span class="sxs-lookup"><span data-stu-id="ecfba-116">Enumeration Types</span></span>](../../csharp/programming-guide/enumeration-types.md)  
  
 [<span data-ttu-id="ecfba-117">委派</span><span class="sxs-lookup"><span data-stu-id="ecfba-117">Delegates</span></span>](../../csharp/programming-guide/delegates/index.md)  
 
 [<span data-ttu-id="ecfba-118">陣列</span><span class="sxs-lookup"><span data-stu-id="ecfba-118">Arrays</span></span>](../../csharp/programming-guide/arrays/index.md)  
  
 [<span data-ttu-id="ecfba-119">字串</span><span class="sxs-lookup"><span data-stu-id="ecfba-119">Strings</span></span>](../../csharp/programming-guide/strings/index.md)  
  
 [<span data-ttu-id="ecfba-120">屬性</span><span class="sxs-lookup"><span data-stu-id="ecfba-120">Properties</span></span>](../../csharp/programming-guide/classes-and-structs/properties.md)  
  
 [<span data-ttu-id="ecfba-121">索引子</span><span class="sxs-lookup"><span data-stu-id="ecfba-121">Indexers</span></span>](../../csharp/programming-guide/indexers/index.md)  
  
 [<span data-ttu-id="ecfba-122">事件</span><span class="sxs-lookup"><span data-stu-id="ecfba-122">Events</span></span>](../../csharp/programming-guide/events/index.md)  
  
 [<span data-ttu-id="ecfba-123">泛型</span><span class="sxs-lookup"><span data-stu-id="ecfba-123">Generics</span></span>](../../csharp/programming-guide/generics/index.md)  
  
 [<span data-ttu-id="ecfba-124">迭代器</span><span class="sxs-lookup"><span data-stu-id="ecfba-124">Iterators</span></span>](../../csharp/programming-guide/concepts/iterators.md)
  
 [<span data-ttu-id="ecfba-125">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="ecfba-125">LINQ Query Expressions</span></span>](../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [<span data-ttu-id="ecfba-126">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="ecfba-126">Lambda Expressions</span></span>](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
 [<span data-ttu-id="ecfba-127">命名空間</span><span class="sxs-lookup"><span data-stu-id="ecfba-127">Namespaces</span></span>](../../csharp/programming-guide/namespaces/index.md)  
  
 [<span data-ttu-id="ecfba-128">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="ecfba-128">Nullable Types</span></span>](../../csharp/programming-guide/nullable-types/index.md)  
  
 [<span data-ttu-id="ecfba-129">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="ecfba-129">Unsafe Code and Pointers</span></span>](../../csharp/programming-guide/unsafe-code-pointers/index.md)  
  
 [<span data-ttu-id="ecfba-130">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="ecfba-130">XML Documentation Comments</span></span>](../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
  
## <a name="platform-sections"></a><span data-ttu-id="ecfba-131">平台章節</span><span class="sxs-lookup"><span data-stu-id="ecfba-131">Platform Sections</span></span>  
 [<span data-ttu-id="ecfba-132">應用程式定義域 (C# 和 Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ecfba-132">Application Domains (C# and Visual Basic)</span></span>](http://msdn.microsoft.com/library/1bc2939a-79db-4a4a-a677-4a2ce6de2b1e)  
  
 [<span data-ttu-id="ecfba-133">組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="ecfba-133">Assemblies and the Global Assembly Cache</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
  
 [<span data-ttu-id="ecfba-134">屬性</span><span class="sxs-lookup"><span data-stu-id="ecfba-134">Attributes</span></span>](../../csharp/programming-guide/concepts/attributes/index.md)  
  
 [<span data-ttu-id="ecfba-135">集合</span><span class="sxs-lookup"><span data-stu-id="ecfba-135">Collections</span></span>](../../csharp/programming-guide/concepts/collections.md)  
  
 [<span data-ttu-id="ecfba-136">例外狀況和例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="ecfba-136">Exceptions and Exception Handling</span></span>](../../csharp/programming-guide/exceptions/index.md)  
  
 [<span data-ttu-id="ecfba-137">檔案系統和登錄 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="ecfba-137">File System and the Registry (C# Programming Guide)</span></span>](../../csharp/programming-guide/file-system/index.md)  
  
 [<span data-ttu-id="ecfba-138">互通性</span><span class="sxs-lookup"><span data-stu-id="ecfba-138">Interoperability</span></span>](../../csharp/programming-guide/interop/index.md)  
  
 [<span data-ttu-id="ecfba-139">反映</span><span class="sxs-lookup"><span data-stu-id="ecfba-139">Reflection</span></span>](../../csharp/programming-guide/concepts/reflection.md)  
  
## <a name="see-also"></a><span data-ttu-id="ecfba-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="ecfba-140">See Also</span></span>  
 [<span data-ttu-id="ecfba-141">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ecfba-141">C# Reference</span></span>](../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ecfba-142">C#</span><span class="sxs-lookup"><span data-stu-id="ecfba-142">C#</span></span>](../../csharp/index.md)
