---
title: 使用命名空間 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: c5bede7475fdbee3f3524984a9be97b95b44817d
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452678"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="72a6d-102">使用命名空間 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="72a6d-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="72a6d-103">C# 程式內大量使用命名空間的原因有兩個。</span><span class="sxs-lookup"><span data-stu-id="72a6d-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="72a6d-104">首先，.NET Framework 類別會使用命名空間來組織其多種類別。</span><span class="sxs-lookup"><span data-stu-id="72a6d-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="72a6d-105">其次，宣告您自己的命名空間，有助於在較大型的程式設計專案中控制類別和方法名稱的範圍。</span><span class="sxs-lookup"><span data-stu-id="72a6d-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="72a6d-106">存取命名空間</span><span class="sxs-lookup"><span data-stu-id="72a6d-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="72a6d-107">大部分 C# 應用程式的開頭為 `using` 指示詞區段。</span><span class="sxs-lookup"><span data-stu-id="72a6d-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="72a6d-108">本節列出應用程式經常使用的命名空間，並讓程式設計人員每次使用其內包含的方法時不需要指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="72a6d-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="72a6d-109">例如，包含下行：</span><span class="sxs-lookup"><span data-stu-id="72a6d-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="72a6d-110">在程式的開始，程式設計人員可以使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="72a6d-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="72a6d-111">而非：</span><span class="sxs-lookup"><span data-stu-id="72a6d-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="72a6d-112">命名空間別名</span><span class="sxs-lookup"><span data-stu-id="72a6d-112">Namespace Aliases</span></span>  
 <span data-ttu-id="72a6d-113">[using 指示詞](../../../csharp/language-reference/keywords/using-directive.md)也可以用來建立[命名空間](../../../csharp/language-reference/keywords/namespace.md)的別名。</span><span class="sxs-lookup"><span data-stu-id="72a6d-113">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="72a6d-114">例如，如果您要使用先前撰寫的命名空間以包含巢狀命名空間，則可能想要宣告別名，以特別快速參考別名，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="72a6d-114">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#7)]  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="72a6d-115">使用命名空間控制範圍</span><span class="sxs-lookup"><span data-stu-id="72a6d-115">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="72a6d-116">`namespace` 關鍵字用來宣告範圍。</span><span class="sxs-lookup"><span data-stu-id="72a6d-116">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="72a6d-117">在專案內建立範圍的能力有助於組織程式碼，並可讓您建立全域唯一類型。</span><span class="sxs-lookup"><span data-stu-id="72a6d-117">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="72a6d-118">在下列範例中，標題為 `SampleClass` 的類別定義於兩個命名空間中，而其中一個命名空間巢狀於另一個命名空間內。</span><span class="sxs-lookup"><span data-stu-id="72a6d-118">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="72a6d-119">[成員存取運算子 `.`](../../language-reference/operators/member-access-operators.md#member-access-operator-) 用來區分呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="72a6d-119">The [member access `.` operator](../../language-reference/operators/member-access-operators.md#member-access-operator-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="72a6d-120">完整名稱</span><span class="sxs-lookup"><span data-stu-id="72a6d-120">Fully Qualified Names</span></span>  
 <span data-ttu-id="72a6d-121">命名空間和類型具有指出邏輯階層之完整名稱所描述的唯一標題。</span><span class="sxs-lookup"><span data-stu-id="72a6d-121">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="72a6d-122">例如，`A.B` 陳述式表示 `A` 是命名空間或類型的名稱，而 `B` 巢狀於其內。</span><span class="sxs-lookup"><span data-stu-id="72a6d-122">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="72a6d-123">在下列範例中，有巢狀類別和命名空間。</span><span class="sxs-lookup"><span data-stu-id="72a6d-123">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="72a6d-124">完整名稱會表示為每個實體後面的註解。</span><span class="sxs-lookup"><span data-stu-id="72a6d-124">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="72a6d-125">在先前的程式碼區段中：</span><span class="sxs-lookup"><span data-stu-id="72a6d-125">In the previous code segment:</span></span>  
  
- <span data-ttu-id="72a6d-126">`N1` 命名空間是全域命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="72a6d-126">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="72a6d-127">其完整名稱是 `N1`。</span><span class="sxs-lookup"><span data-stu-id="72a6d-127">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="72a6d-128">`N2` 命名空間是 `N1` 的成員。</span><span class="sxs-lookup"><span data-stu-id="72a6d-128">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="72a6d-129">其完整名稱是 `N1.N2`。</span><span class="sxs-lookup"><span data-stu-id="72a6d-129">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="72a6d-130">`C1` 類別是 `N1` 的成員。</span><span class="sxs-lookup"><span data-stu-id="72a6d-130">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="72a6d-131">其完整名稱是 `N1.C1`。</span><span class="sxs-lookup"><span data-stu-id="72a6d-131">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="72a6d-132">這個程式碼使用類別名稱 `C2` 兩次。</span><span class="sxs-lookup"><span data-stu-id="72a6d-132">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="72a6d-133">不過，完整名稱是唯一的。</span><span class="sxs-lookup"><span data-stu-id="72a6d-133">However, the fully qualified names are unique.</span></span> <span data-ttu-id="72a6d-134">第一個 `C2` 執行個體宣告於 `C1` 內；因此，其完整名稱是 `N1.C1.C2`。</span><span class="sxs-lookup"><span data-stu-id="72a6d-134">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="72a6d-135">第二個 `C2` 執行個體宣告於 `N2` 命名空間內；因此，其完整名稱是 `N1.N2.C2`。</span><span class="sxs-lookup"><span data-stu-id="72a6d-135">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="72a6d-136">使用先前的程式碼區段，即可將新的類別成員 `C3` 新增至命名空間 `N1.N2`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="72a6d-136">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="72a6d-137">在一般情況下，使用 `::` 來參考命名空間別名，或使用 `global::` 參考全域命名空間，以及使用 `.` 來限定類型或成員。</span><span class="sxs-lookup"><span data-stu-id="72a6d-137">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="72a6d-138">搭配使用 `::` 與參考型別而非命名空間的別名是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="72a6d-138">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="72a6d-139">例如：</span><span class="sxs-lookup"><span data-stu-id="72a6d-139">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="72a6d-140">請記住，`global` 這個單字不是預先定義別名，因此，`global.X` 沒有任何特殊意義。</span><span class="sxs-lookup"><span data-stu-id="72a6d-140">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="72a6d-141">只有在與 `::` 搭配使用時，才會取得特殊意義。</span><span class="sxs-lookup"><span data-stu-id="72a6d-141">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="72a6d-142">因為 `global::` 一律會參考全域命名空間，而不是別名，所以如果您定義名為 global 的別名，就會產生編譯器警告 CS0440。</span><span class="sxs-lookup"><span data-stu-id="72a6d-142">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="72a6d-143">例如，下行會產生警告：</span><span class="sxs-lookup"><span data-stu-id="72a6d-143">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="72a6d-144">搭配使用 `::` 與別名是不錯的想法，並且可避免非預期導入額外的類型。</span><span class="sxs-lookup"><span data-stu-id="72a6d-144">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="72a6d-145">例如，請考慮使用以下範例：</span><span class="sxs-lookup"><span data-stu-id="72a6d-145">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="72a6d-146">這會適用，但是如果後續引進名為 `Alias` 的類型，`Alias.` 會改為繫結至該類型。</span><span class="sxs-lookup"><span data-stu-id="72a6d-146">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="72a6d-147">使用 `Alias::Exception` 確保 `Alias` 視為命名空間別名，而不要被誤認為類型。</span><span class="sxs-lookup"><span data-stu-id="72a6d-147">Using `Alias::Exception` insures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="72a6d-148">請參閱主題[如何：使用全域命名空間別名](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)，以取得 `global` 別名的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="72a6d-148">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a6d-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72a6d-149">See also</span></span>

- [<span data-ttu-id="72a6d-150">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="72a6d-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="72a6d-151">命名空間</span><span class="sxs-lookup"><span data-stu-id="72a6d-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="72a6d-152">命名空間關鍵字</span><span class="sxs-lookup"><span data-stu-id="72a6d-152">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)
- [<span data-ttu-id="72a6d-153">.運算子</span><span class="sxs-lookup"><span data-stu-id="72a6d-153">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="72a6d-154">::運算子</span><span class="sxs-lookup"><span data-stu-id="72a6d-154">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [<span data-ttu-id="72a6d-155">extern</span><span class="sxs-lookup"><span data-stu-id="72a6d-155">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
