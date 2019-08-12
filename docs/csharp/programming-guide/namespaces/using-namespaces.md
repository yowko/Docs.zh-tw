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
ms.openlocfilehash: 06ebb9edfaf4753b98c3305a90b52e93ee7b4486
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796631"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="a6b63-102">使用命名空間 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="a6b63-102">Using namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="a6b63-103">C# 程式內大量使用命名空間的原因有兩個。</span><span class="sxs-lookup"><span data-stu-id="a6b63-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="a6b63-104">首先，.NET Framework 類別會使用命名空間來組織其多種類別。</span><span class="sxs-lookup"><span data-stu-id="a6b63-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="a6b63-105">其次，宣告您自己的命名空間，有助於在較大型的程式設計專案中控制類別和方法名稱的範圍。</span><span class="sxs-lookup"><span data-stu-id="a6b63-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="a6b63-106">存取命名空間</span><span class="sxs-lookup"><span data-stu-id="a6b63-106">Accessing namespaces</span></span>

 <span data-ttu-id="a6b63-107">大部分 C# 應用程式的開頭為 `using` 指示詞區段。</span><span class="sxs-lookup"><span data-stu-id="a6b63-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="a6b63-108">本節列出應用程式經常使用的命名空間，並讓程式設計人員每次使用其內包含的方法時不需要指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="a6b63-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="a6b63-109">例如，包含下行：</span><span class="sxs-lookup"><span data-stu-id="a6b63-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="a6b63-110">在程式的開始，程式設計人員可以使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="a6b63-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="a6b63-111">而非：</span><span class="sxs-lookup"><span data-stu-id="a6b63-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="a6b63-112">命名空間別名</span><span class="sxs-lookup"><span data-stu-id="a6b63-112">Namespace aliases</span></span>

 <span data-ttu-id="a6b63-113">您也可以使用 [`using` 指示詞](../../language-reference/keywords/using-directive.md)來建立命名空間的別名。</span><span class="sxs-lookup"><span data-stu-id="a6b63-113">You also can use the [`using` directive](../../language-reference/keywords/using-directive.md) to create an alias for a namespace.</span></span> <span data-ttu-id="a6b63-114">使用[命名空間別名限定詞`::`](../../language-reference/operators/namespace-alias-qualifier.md)來存取別名命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="a6b63-114">Use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to access the members of the aliased namespace.</span></span> <span data-ttu-id="a6b63-115">下列範例示範如何建立及使用命名空間別名：</span><span class="sxs-lookup"><span data-stu-id="a6b63-115">The following example shows how to create and use a namespace alias:</span></span>
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="a6b63-116">使用命名空間來控制範圍</span><span class="sxs-lookup"><span data-stu-id="a6b63-116">Using namespaces to control scope</span></span>

 <span data-ttu-id="a6b63-117">`namespace` 關鍵字用來宣告範圍。</span><span class="sxs-lookup"><span data-stu-id="a6b63-117">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="a6b63-118">在專案內建立範圍的能力有助於組織程式碼，並可讓您建立全域唯一類型。</span><span class="sxs-lookup"><span data-stu-id="a6b63-118">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="a6b63-119">在下列範例中，標題為 `SampleClass` 的類別定義於兩個命名空間中，而其中一個命名空間巢狀於另一個命名空間內。</span><span class="sxs-lookup"><span data-stu-id="a6b63-119">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="a6b63-120">[成員存取運算子 `.`](../../language-reference/operators/member-access-operators.md#member-access-operator-) 用來區分呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="a6b63-120">The [member access `.` operator](../../language-reference/operators/member-access-operators.md#member-access-operator-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="a6b63-121">完整名稱</span><span class="sxs-lookup"><span data-stu-id="a6b63-121">Fully qualified names</span></span>

 <span data-ttu-id="a6b63-122">命名空間和類型具有指出邏輯階層之完整名稱所描述的唯一標題。</span><span class="sxs-lookup"><span data-stu-id="a6b63-122">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="a6b63-123">例如，`A.B` 陳述式表示 `A` 是命名空間或類型的名稱，而 `B` 巢狀於其內。</span><span class="sxs-lookup"><span data-stu-id="a6b63-123">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="a6b63-124">在下列範例中，有巢狀類別和命名空間。</span><span class="sxs-lookup"><span data-stu-id="a6b63-124">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="a6b63-125">完整名稱會表示為每個實體後面的註解。</span><span class="sxs-lookup"><span data-stu-id="a6b63-125">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="a6b63-126">在先前的程式碼區段中：</span><span class="sxs-lookup"><span data-stu-id="a6b63-126">In the previous code segment:</span></span>  
  
- <span data-ttu-id="a6b63-127">`N1` 命名空間是全域命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="a6b63-127">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="a6b63-128">其完整名稱是 `N1`。</span><span class="sxs-lookup"><span data-stu-id="a6b63-128">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="a6b63-129">`N2` 命名空間是 `N1` 的成員。</span><span class="sxs-lookup"><span data-stu-id="a6b63-129">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="a6b63-130">其完整名稱是 `N1.N2`。</span><span class="sxs-lookup"><span data-stu-id="a6b63-130">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="a6b63-131">`C1` 類別是 `N1` 的成員。</span><span class="sxs-lookup"><span data-stu-id="a6b63-131">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="a6b63-132">其完整名稱是 `N1.C1`。</span><span class="sxs-lookup"><span data-stu-id="a6b63-132">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="a6b63-133">這個程式碼使用類別名稱 `C2` 兩次。</span><span class="sxs-lookup"><span data-stu-id="a6b63-133">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="a6b63-134">不過，完整名稱是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a6b63-134">However, the fully qualified names are unique.</span></span> <span data-ttu-id="a6b63-135">第一個 `C2` 執行個體宣告於 `C1` 內；因此，其完整名稱是 `N1.C1.C2`。</span><span class="sxs-lookup"><span data-stu-id="a6b63-135">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="a6b63-136">第二個 `C2` 執行個體宣告於 `N2` 命名空間內；因此，其完整名稱是 `N1.N2.C2`。</span><span class="sxs-lookup"><span data-stu-id="a6b63-136">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="a6b63-137">使用先前的程式碼區段，即可將新的類別成員 `C3` 新增至命名空間 `N1.N2`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a6b63-137">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="a6b63-138">在一般情況下，使用 `::` 來參考命名空間別名，或使用 `global::` 參考全域命名空間，以及使用 `.` 來限定類型或成員。</span><span class="sxs-lookup"><span data-stu-id="a6b63-138">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="a6b63-139">搭配使用 `::` 與參考型別而非命名空間的別名是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="a6b63-139">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="a6b63-140">例如：</span><span class="sxs-lookup"><span data-stu-id="a6b63-140">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="a6b63-141">請記住，`global` 這個單字不是預先定義別名，因此，`global.X` 沒有任何特殊意義。</span><span class="sxs-lookup"><span data-stu-id="a6b63-141">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="a6b63-142">只有在與 `::` 搭配使用時，才會取得特殊意義。</span><span class="sxs-lookup"><span data-stu-id="a6b63-142">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="a6b63-143">因為 `global::` 一律會參考全域命名空間，而不是別名，所以如果您定義名為 global 的別名，就會產生編譯器警告 CS0440。</span><span class="sxs-lookup"><span data-stu-id="a6b63-143">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="a6b63-144">例如，下行會產生警告：</span><span class="sxs-lookup"><span data-stu-id="a6b63-144">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="a6b63-145">搭配使用 `::` 與別名是不錯的想法，並且可避免非預期導入額外的類型。</span><span class="sxs-lookup"><span data-stu-id="a6b63-145">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="a6b63-146">例如，請考慮使用以下範例：</span><span class="sxs-lookup"><span data-stu-id="a6b63-146">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="a6b63-147">這會適用，但是如果後續引進名為 `Alias` 的類型，`Alias.` 會改為繫結至該類型。</span><span class="sxs-lookup"><span data-stu-id="a6b63-147">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="a6b63-148">使用 `Alias::Exception` 來確保將 `Alias` 視為命名空間別名，而非型別。</span><span class="sxs-lookup"><span data-stu-id="a6b63-148">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="a6b63-149">請參閱主題[如何：使用全域命名空間別名](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)，以取得 `global` 別名的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a6b63-149">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b63-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6b63-150">See also</span></span>

- [<span data-ttu-id="a6b63-151">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a6b63-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a6b63-152">命名空間</span><span class="sxs-lookup"><span data-stu-id="a6b63-152">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="a6b63-153">. 運算子</span><span class="sxs-lookup"><span data-stu-id="a6b63-153">. operator</span></span>](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="a6b63-154">:: 運算子</span><span class="sxs-lookup"><span data-stu-id="a6b63-154">:: operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="a6b63-155">外部別名</span><span class="sxs-lookup"><span data-stu-id="a6b63-155">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
