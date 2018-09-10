---
title: using static 指示詞 (C# 參考)
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04e7368a6b6a4453f2dd07c7afdc0bffa7473ed1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506668"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="56083-102">using static 指示詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="56083-102">using static Directive (C# Reference)</span></span>

<span data-ttu-id="56083-103">`using static` 指示詞指定一種類型，讓您不需要指定類型名稱，即可存取其靜態成員和巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="56083-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="56083-104">它的語法為：</span><span class="sxs-lookup"><span data-stu-id="56083-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="56083-105">其中 *fully-qualified-type-name* 是不需要指定類型名稱，即可參考其靜態成員和巢狀型別類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="56083-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="56083-106">如果您未提供完整類型名稱 (完整命名空間名稱及類型名稱)，C# 會產生編譯器錯誤 [CS0246](../compiler-messages/cs0246.md)：「找不到類型或命名空間名稱 'type/namespace' (您是否遺漏 using 指示詞或組件參考?)」。</span><span class="sxs-lookup"><span data-stu-id="56083-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="56083-107">`using static` 指示詞會套用至任何具有靜態成員 (或巢狀型別) 的類型，即使該類型同時具有執行個體成員也一樣。</span><span class="sxs-lookup"><span data-stu-id="56083-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="56083-108">不過，執行個體成員只能透過類型執行個體叫用。</span><span class="sxs-lookup"><span data-stu-id="56083-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="56083-109">`using static` 指示詞是在 C# 6 中引進。</span><span class="sxs-lookup"><span data-stu-id="56083-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="56083-110">備註</span><span class="sxs-lookup"><span data-stu-id="56083-110">Remarks</span></span>
 
<span data-ttu-id="56083-111">一般而言，當您呼叫靜態成員時，您會提供類型名稱及成員名稱。</span><span class="sxs-lookup"><span data-stu-id="56083-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="56083-112">重複輸入相同的類型名稱來叫用類型的成員，可能會導致冗長且難以理解的程式碼。</span><span class="sxs-lookup"><span data-stu-id="56083-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="56083-113">例如，`Circle` 類別的下列定義參考了 <xref:System.Math> 類別的一些成員。</span><span class="sxs-lookup"><span data-stu-id="56083-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="56083-114">`using static` 指示詞可避免每次參考成員時都必須明確參考 <xref:System.Math> 類別，因此所產生的程式碼會更簡潔：</span><span class="sxs-lookup"><span data-stu-id="56083-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="56083-115">`using static` 只會匯入指定的類型中宣告的可存取靜態成員和巢狀類型。</span><span class="sxs-lookup"><span data-stu-id="56083-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="56083-116">不會匯入繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="56083-116">Inherited members are not imported.</span></span>  <span data-ttu-id="56083-117">您可以使用 using 靜態指示詞從任何具名類型匯入，包括 Visual Basic 模組。</span><span class="sxs-lookup"><span data-stu-id="56083-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="56083-118">如果 F# 最上層函式出現在中繼資料中，作為具名類型的靜態成員，其名稱是有效的 C# 識別項，則可以匯入 F# 函式。</span><span class="sxs-lookup"><span data-stu-id="56083-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>  
  
 <span data-ttu-id="56083-119">`using static` 讓您在可供擴充方法查閱使用的指定類型中宣告擴充方法。</span><span class="sxs-lookup"><span data-stu-id="56083-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="56083-120">不過，擴充方法的名稱不會匯入程式碼中未限定參考的範圍。</span><span class="sxs-lookup"><span data-stu-id="56083-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>  
  
 <span data-ttu-id="56083-121">在相同編譯單位或命名空間中透過不同 `using static` 指示詞從不同的類型匯入、具有相同名稱的方法會形成方法群組。</span><span class="sxs-lookup"><span data-stu-id="56083-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="56083-122">這些方法群組內的多載解析會遵循一般的 C# 規則。</span><span class="sxs-lookup"><span data-stu-id="56083-122">Overload resolution within these method groups follows normal C# rules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56083-123">範例</span><span class="sxs-lookup"><span data-stu-id="56083-123">Example</span></span>

<span data-ttu-id="56083-124">下列範例使用 `using static` 指示詞來提供 <xref:System.Console>、<xref:System.Math> 和 <xref:System.String> 類別的靜態成員，而不需要指定其類型名稱。</span><span class="sxs-lookup"><span data-stu-id="56083-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="56083-125">在此範例中，`using static` 指示詞也可能已套用至 <xref:System.Double> 類型。</span><span class="sxs-lookup"><span data-stu-id="56083-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="56083-126">因此不需要指定類型名稱，即可呼叫 <xref:System.Double.TryParse(System.String,System.Double@)> 方法。</span><span class="sxs-lookup"><span data-stu-id="56083-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="56083-127">不過，這會建立難以閱讀的程式碼，因為您必須檢查 `using static` 陳述式，以判斷呼叫了哪一個數字類型的 `TryParse` 方法。</span><span class="sxs-lookup"><span data-stu-id="56083-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="56083-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56083-128">See also</span></span>

- [<span data-ttu-id="56083-129">using 指示詞</span><span class="sxs-lookup"><span data-stu-id="56083-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="56083-130">C# 參考</span><span class="sxs-lookup"><span data-stu-id="56083-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="56083-131">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="56083-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="56083-132">使用命名空間</span><span class="sxs-lookup"><span data-stu-id="56083-132">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="56083-133">命名空間關鍵字</span><span class="sxs-lookup"><span data-stu-id="56083-133">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)
- [<span data-ttu-id="56083-134">命名空間</span><span class="sxs-lookup"><span data-stu-id="56083-134">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
