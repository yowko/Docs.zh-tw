---
title: "使用命名空間 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f485992f5d4b7bc16aaefeec8c7c76ce39f48ef0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="bd62a-102">使用命名空間 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="bd62a-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="bd62a-103">C# 程式內大量使用命名空間的原因有兩個。</span><span class="sxs-lookup"><span data-stu-id="bd62a-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="bd62a-104">首先，.NET Framework 類別會使用命名空間來組織其多種類別。</span><span class="sxs-lookup"><span data-stu-id="bd62a-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="bd62a-105">其次，宣告您自己的命名空間，有助於在較大型的程式設計專案中控制類別和方法名稱的範圍。</span><span class="sxs-lookup"><span data-stu-id="bd62a-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="bd62a-106">存取命名空間</span><span class="sxs-lookup"><span data-stu-id="bd62a-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="bd62a-107">大部分 C# 應用程式的開頭為 `using` 指示詞區段。</span><span class="sxs-lookup"><span data-stu-id="bd62a-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="bd62a-108">本節列出應用程式經常使用的命名空間，並讓程式設計人員每次使用其內包含的方法時不需要指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="bd62a-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="bd62a-109">例如，包含下行：</span><span class="sxs-lookup"><span data-stu-id="bd62a-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 <span data-ttu-id="bd62a-110">在程式的開始，程式設計人員可以使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="bd62a-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 <span data-ttu-id="bd62a-111">而非：</span><span class="sxs-lookup"><span data-stu-id="bd62a-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="bd62a-112">命名空間別名</span><span class="sxs-lookup"><span data-stu-id="bd62a-112">Namespace Aliases</span></span>  
 <span data-ttu-id="bd62a-113">[using 指示詞](../../../csharp/language-reference/keywords/using-directive.md)也可以用來建立[命名空間](../../../csharp/language-reference/keywords/namespace.md)的別名。</span><span class="sxs-lookup"><span data-stu-id="bd62a-113">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="bd62a-114">例如，如果您要使用先前撰寫的命名空間以包含巢狀命名空間，則可能想要宣告別名，以特別快速參考別名，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bd62a-114">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="bd62a-115">使用命名空間控制範圍</span><span class="sxs-lookup"><span data-stu-id="bd62a-115">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="bd62a-116">`namespace` 關鍵字用來宣告範圍。</span><span class="sxs-lookup"><span data-stu-id="bd62a-116">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="bd62a-117">在專案內建立範圍的能力有助於組織程式碼，並可讓您建立全域唯一類型。</span><span class="sxs-lookup"><span data-stu-id="bd62a-117">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="bd62a-118">在下列範例中，標題為 `SampleClass` 的類別定義於兩個命名空間中，而其中一個命名空間巢狀於另一個命名空間內。</span><span class="sxs-lookup"><span data-stu-id="bd62a-118">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="bd62a-119">[。運算子](../../../csharp/language-reference/operators/member-access-operator.md)用來區分呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="bd62a-119">The [. Operator](../../../csharp/language-reference/operators/member-access-operator.md) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="bd62a-120">完整名稱</span><span class="sxs-lookup"><span data-stu-id="bd62a-120">Fully Qualified Names</span></span>  
 <span data-ttu-id="bd62a-121">命名空間和類型具有指出邏輯階層之完整名稱所描述的唯一標題。</span><span class="sxs-lookup"><span data-stu-id="bd62a-121">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="bd62a-122">例如，`A.B` 陳述式表示 `A` 是命名空間或類型的名稱，而 `B` 巢狀於其內。</span><span class="sxs-lookup"><span data-stu-id="bd62a-122">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="bd62a-123">在下列範例中，有巢狀類別和命名空間。</span><span class="sxs-lookup"><span data-stu-id="bd62a-123">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="bd62a-124">完整名稱會表示為每個實體後面的註解。</span><span class="sxs-lookup"><span data-stu-id="bd62a-124">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 <span data-ttu-id="bd62a-125">在先前的程式碼區段中：</span><span class="sxs-lookup"><span data-stu-id="bd62a-125">In the previous code segment:</span></span>  
  
-   <span data-ttu-id="bd62a-126">`N1` 命名空間是全域命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="bd62a-126">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="bd62a-127">其完整名稱是 `N1`。</span><span class="sxs-lookup"><span data-stu-id="bd62a-127">Its fully qualified name is `N1`.</span></span>  
  
-   <span data-ttu-id="bd62a-128">`N2` 命名空間是 `N1` 的成員。</span><span class="sxs-lookup"><span data-stu-id="bd62a-128">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="bd62a-129">其完整名稱是 `N1.N2`。</span><span class="sxs-lookup"><span data-stu-id="bd62a-129">Its fully qualified name is `N1.N2`.</span></span>  
  
-   <span data-ttu-id="bd62a-130">`C1` 類別是 `N1` 的成員。</span><span class="sxs-lookup"><span data-stu-id="bd62a-130">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="bd62a-131">其完整名稱是 `N1.C1`。</span><span class="sxs-lookup"><span data-stu-id="bd62a-131">Its fully qualified name is `N1.C1`.</span></span>  
  
-   <span data-ttu-id="bd62a-132">這個程式碼使用類別名稱 `C2` 兩次。</span><span class="sxs-lookup"><span data-stu-id="bd62a-132">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="bd62a-133">不過，完整名稱是唯一的。</span><span class="sxs-lookup"><span data-stu-id="bd62a-133">However, the fully qualified names are unique.</span></span> <span data-ttu-id="bd62a-134">第一個 `C2` 執行個體宣告於 `C1` 內；因此，其完整名稱是 `N1.C1.C2`。</span><span class="sxs-lookup"><span data-stu-id="bd62a-134">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="bd62a-135">第二個 `C2` 執行個體宣告於 `N2` 命名空間內；因此，其完整名稱是 `N1.N2.C2`。</span><span class="sxs-lookup"><span data-stu-id="bd62a-135">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="bd62a-136">使用先前的程式碼區段，即可將新的類別成員 `C3` 新增至命名空間 `N1.N2`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bd62a-136">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 <span data-ttu-id="bd62a-137">在一般情況下，使用 `::` 來參考命名空間別名，或使用 `global::` 參考全域命名空間，以及使用 `.` 來限定類型或成員。</span><span class="sxs-lookup"><span data-stu-id="bd62a-137">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="bd62a-138">搭配使用 `::` 與參考型別而非命名空間的別名是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="bd62a-138">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="bd62a-139">例如: </span><span class="sxs-lookup"><span data-stu-id="bd62a-139">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 <span data-ttu-id="bd62a-140">請記住，`global` 這個單字不是預先定義別名，因此，`global.X` 沒有任何特殊意義。</span><span class="sxs-lookup"><span data-stu-id="bd62a-140">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="bd62a-141">只有在與 `::` 搭配使用時，才會取得特殊意義。</span><span class="sxs-lookup"><span data-stu-id="bd62a-141">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="bd62a-142">因為 `global::` 一律會參考全域命名空間，而不是別名，所以如果您定義名為 global 的別名，就會產生編譯器警告 CS0440。</span><span class="sxs-lookup"><span data-stu-id="bd62a-142">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="bd62a-143">例如，下行會產生警告：</span><span class="sxs-lookup"><span data-stu-id="bd62a-143">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 <span data-ttu-id="bd62a-144">搭配使用 `::` 與別名是不錯的想法，並且可避免非預期導入額外的類型。</span><span class="sxs-lookup"><span data-stu-id="bd62a-144">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="bd62a-145">例如，請考慮使用以下範例：</span><span class="sxs-lookup"><span data-stu-id="bd62a-145">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 <span data-ttu-id="bd62a-146">這會適用，但是如果後續引進名為 `Alias` 的類型，`Alias.` 會改為繫結至該類型。</span><span class="sxs-lookup"><span data-stu-id="bd62a-146">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="bd62a-147">使用 `Alias::Exception` 確保 `Alias` 視為命名空間別名，而不要被誤認為類型。</span><span class="sxs-lookup"><span data-stu-id="bd62a-147">Using `Alias::Exception` insures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="bd62a-148">如需 `global` 別名的詳細資訊，請參閱[如何：使用全域命名空間別名](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)主題。</span><span class="sxs-lookup"><span data-stu-id="bd62a-148">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd62a-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd62a-149">See Also</span></span>  
 [<span data-ttu-id="bd62a-150">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bd62a-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bd62a-151">命名空間</span><span class="sxs-lookup"><span data-stu-id="bd62a-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="bd62a-152">命名空間關鍵字</span><span class="sxs-lookup"><span data-stu-id="bd62a-152">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="bd62a-153">.運算子</span><span class="sxs-lookup"><span data-stu-id="bd62a-153">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="bd62a-154">:: 運算子</span><span class="sxs-lookup"><span data-stu-id="bd62a-154">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="bd62a-155">extern</span><span class="sxs-lookup"><span data-stu-id="bd62a-155">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
