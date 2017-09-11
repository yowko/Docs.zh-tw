---
title: "namespace (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- namespace_CSharpKeyword
- namespace
dev_langs:
- CSharp
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: 28
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
ms.openlocfilehash: d2cef3949d9a41db36406db059218f7a204172ea
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="namespace-c-reference"></a><span data-ttu-id="b50f7-102">namespace (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b50f7-102">namespace (C# Reference)</span></span>
<span data-ttu-id="b50f7-103">`namespace` 關鍵字用來宣告包含一組相關物件的範圍。</span><span class="sxs-lookup"><span data-stu-id="b50f7-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="b50f7-104">您可以使用命名空間來組織程式碼項目，並建立全域唯一的型別。</span><span class="sxs-lookup"><span data-stu-id="b50f7-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>  
  
 <span data-ttu-id="b50f7-105">[!code-cs[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b50f7-105">[!code-cs[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b50f7-106">備註</span><span class="sxs-lookup"><span data-stu-id="b50f7-106">Remarks</span></span>  
 <span data-ttu-id="b50f7-107">在命名空間內，您可以宣告下列一或多個型別︰</span><span class="sxs-lookup"><span data-stu-id="b50f7-107">Within a namespace, you can declare one or more of the following types:</span></span>  
  
-   <span data-ttu-id="b50f7-108">另一個命名空間</span><span class="sxs-lookup"><span data-stu-id="b50f7-108">another namespace</span></span>  
  
-   [<span data-ttu-id="b50f7-109">class</span><span class="sxs-lookup"><span data-stu-id="b50f7-109">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="b50f7-110">interface</span><span class="sxs-lookup"><span data-stu-id="b50f7-110">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="b50f7-111">struct</span><span class="sxs-lookup"><span data-stu-id="b50f7-111">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="b50f7-112">enum</span><span class="sxs-lookup"><span data-stu-id="b50f7-112">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
-   [<span data-ttu-id="b50f7-113">delegate</span><span class="sxs-lookup"><span data-stu-id="b50f7-113">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="b50f7-114">無論是否在 C# 來源檔案中明確宣告命名空間，編譯器都會加入預設的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b50f7-114">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="b50f7-115">這個未命名的命名空間，有時候是指全域命名空間，會出現在每個檔案中。</span><span class="sxs-lookup"><span data-stu-id="b50f7-115">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="b50f7-116">全域命名空間中的任何識別項都可用於具名命名空間中。</span><span class="sxs-lookup"><span data-stu-id="b50f7-116">Any identifier in the global namespace is available for use in a named namespace.</span></span>  
  
 <span data-ttu-id="b50f7-117">命名空間以隱含方式具有公用存取，且不可修改。</span><span class="sxs-lookup"><span data-stu-id="b50f7-117">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="b50f7-118">如需可在命名空間中指派給項目之存取修飾詞的討論，請參閱[存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="b50f7-118">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="b50f7-119">您可在兩個或多個宣告中定義命名空間。</span><span class="sxs-lookup"><span data-stu-id="b50f7-119">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="b50f7-120">例如，下例會將兩個類別定義為 `MyCompany` 命名空間的一部分︰</span><span class="sxs-lookup"><span data-stu-id="b50f7-120">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>  
  
 <span data-ttu-id="b50f7-121">[!code-cs[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="b50f7-121">[!code-cs[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="b50f7-122">範例</span><span class="sxs-lookup"><span data-stu-id="b50f7-122">Example</span></span>  
 <span data-ttu-id="b50f7-123">下例顯示如何在巢狀命名空間中呼叫靜態方法。</span><span class="sxs-lookup"><span data-stu-id="b50f7-123">The following example shows how to call a static method in a nested namespace.</span></span>  
  
 <span data-ttu-id="b50f7-124">[!code-cs[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="b50f7-124">[!code-cs[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="b50f7-125">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="b50f7-125">For More Information</span></span>  
 <span data-ttu-id="b50f7-126">如需使用命名空間的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="b50f7-126">For more information about using namespaces, see the following topics:</span></span>  
  
-   [<span data-ttu-id="b50f7-127">命名空間</span><span class="sxs-lookup"><span data-stu-id="b50f7-127">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="b50f7-128">使用命名空間</span><span class="sxs-lookup"><span data-stu-id="b50f7-128">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="b50f7-129">如何：使用全域命名空間別名</span><span class="sxs-lookup"><span data-stu-id="b50f7-129">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="b50f7-130">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b50f7-130">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b50f7-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b50f7-131">See Also</span></span>  
 <span data-ttu-id="b50f7-132">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b50f7-132">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b50f7-133">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b50f7-133">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b50f7-134">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="b50f7-134">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="b50f7-135">[命名空間關鍵字](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="b50f7-135">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
 [<span data-ttu-id="b50f7-136">using</span><span class="sxs-lookup"><span data-stu-id="b50f7-136">using</span></span>](../../../csharp/language-reference/keywords/using.md)

