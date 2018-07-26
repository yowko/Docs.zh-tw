---
title: namespace (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 343cce85dd235532fbe3fc90af0a785f48518db7
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245607"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="82465-102">namespace (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="82465-102">namespace (C# Reference)</span></span>
<span data-ttu-id="82465-103">`namespace` 關鍵字用來宣告包含一組相關物件的範圍。</span><span class="sxs-lookup"><span data-stu-id="82465-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="82465-104">您可以使用命名空間來組織程式碼項目，並建立全域唯一的型別。</span><span class="sxs-lookup"><span data-stu-id="82465-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="82465-105">備註</span><span class="sxs-lookup"><span data-stu-id="82465-105">Remarks</span></span>  
 <span data-ttu-id="82465-106">在命名空間內，您可以宣告下列一或多個型別︰</span><span class="sxs-lookup"><span data-stu-id="82465-106">Within a namespace, you can declare one or more of the following types:</span></span>  
  
-   <span data-ttu-id="82465-107">另一個命名空間</span><span class="sxs-lookup"><span data-stu-id="82465-107">another namespace</span></span>  
  
-   [<span data-ttu-id="82465-108">class</span><span class="sxs-lookup"><span data-stu-id="82465-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="82465-109">interface</span><span class="sxs-lookup"><span data-stu-id="82465-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="82465-110">struct</span><span class="sxs-lookup"><span data-stu-id="82465-110">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="82465-111">enum</span><span class="sxs-lookup"><span data-stu-id="82465-111">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
-   [<span data-ttu-id="82465-112">delegate</span><span class="sxs-lookup"><span data-stu-id="82465-112">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="82465-113">無論是否在 C# 來源檔案中明確宣告命名空間，編譯器都會加入預設的命名空間。</span><span class="sxs-lookup"><span data-stu-id="82465-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="82465-114">這個未命名的命名空間，有時候是指全域命名空間，會出現在每個檔案中。</span><span class="sxs-lookup"><span data-stu-id="82465-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="82465-115">全域命名空間中的任何識別項都可用於具名命名空間中。</span><span class="sxs-lookup"><span data-stu-id="82465-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>  
  
 <span data-ttu-id="82465-116">命名空間以隱含方式具有公用存取，且不可修改。</span><span class="sxs-lookup"><span data-stu-id="82465-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="82465-117">如需可在命名空間中指派給項目之存取修飾詞的討論，請參閱[存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="82465-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="82465-118">您可在兩個或多個宣告中定義命名空間。</span><span class="sxs-lookup"><span data-stu-id="82465-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="82465-119">例如，下例會將兩個類別定義為 `MyCompany` 命名空間的一部分︰</span><span class="sxs-lookup"><span data-stu-id="82465-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="82465-120">範例</span><span class="sxs-lookup"><span data-stu-id="82465-120">Example</span></span>  
 <span data-ttu-id="82465-121">下例顯示如何在巢狀命名空間中呼叫靜態方法。</span><span class="sxs-lookup"><span data-stu-id="82465-121">The following example shows how to call a static method in a nested namespace.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a><span data-ttu-id="82465-122">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="82465-122">For More Information</span></span>  
 <span data-ttu-id="82465-123">如需使用命名空間的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="82465-123">For more information about using namespaces, see the following topics:</span></span>  
  
-   [<span data-ttu-id="82465-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="82465-124">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="82465-125">使用命名空間</span><span class="sxs-lookup"><span data-stu-id="82465-125">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="82465-126">如何：使用全域命名空間別名</span><span class="sxs-lookup"><span data-stu-id="82465-126">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="82465-127">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="82465-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="82465-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="82465-128">See Also</span></span>  
 [<span data-ttu-id="82465-129">C# 參考</span><span class="sxs-lookup"><span data-stu-id="82465-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="82465-130">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="82465-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="82465-131">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="82465-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="82465-132">命名空間關鍵字</span><span class="sxs-lookup"><span data-stu-id="82465-132">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="82465-133">using</span><span class="sxs-lookup"><span data-stu-id="82465-133">using</span></span>](../../../csharp/language-reference/keywords/using.md)
