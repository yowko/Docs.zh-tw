---
title: "預設值運算式 (C# 程式設計指南)"
description: "預設值運算式會為任何參考型別或實值型別產生預設值"
ms.date: 2017-08-23
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 1e548df4de2c07934313311a7ffcfae82be76000
ms.openlocfilehash: 7b5b53d7ed92c6f6377a3e494daf1d02a4cf0934
ms.contentlocale: zh-tw
ms.lasthandoff: 08/29/2017

---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="fa8ab-103">預設值運算式 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="fa8ab-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="fa8ab-104">預設值運算式會為型別產生預設值。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-104">A default value expression produces the default value for a type.</span></span> <span data-ttu-id="fa8ab-105">預設值運算式對泛型類別和方法特別有用。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-105">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="fa8ab-106">使用泛型時會發生一個問題，也就是當您無法預先知道下列資訊時，如何將預設值指派給參數化型別 `T`：</span><span class="sxs-lookup"><span data-stu-id="fa8ab-106">One issue that arises using generics is how to assign a default value to a parameterized type `T` when you do not know the following in advance:</span></span>

- <span data-ttu-id="fa8ab-107">`T` 是參考型別或實值型別。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-107">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="fa8ab-108">如果 `T` 是實值型別，則會是數值或使用者定義結構。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-108">If `T` is a value type, whether is a numeric value or a user-defined struct.</span></span>

 <span data-ttu-id="fa8ab-109">假設有參數化型別 `T` 的變數 `t`，陳述式 `t = null` 就只在 `T` 為參考型別時有效。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-109">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="fa8ab-110">指派 `t = 0` 僅適用於數值型別，而不適用於結構。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-110">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="fa8ab-111">解決方案是使用預設值運算式，若為參考型別 (類別類型及介面類型)，其傳回 `null`；若為數值型別，其傳回零。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-111">The solution is to use a default value expression, which returns `null` for reference types (class types and interface types) and zero for numeric value types.</span></span> <span data-ttu-id="fa8ab-112">若是使用者定義結構，其傳回已初始化為零位元模式的結構，而依據成員為數值或參考型別，來為各成員產生 0 或 `null`。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-112">For user-defined structs, it returns the struct initialized to the zero bit pattern, which produces 0 or `null` for each member depending on whether that member is a value or reference type.</span></span> <span data-ttu-id="fa8ab-113">若是可為 Null 的實值型別，`default` 會傳回 <xref:System.Nullable%601?displayProperty=fullName>，該值會與任何結構一樣經過初始化。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-113">For nullable value types, `default` returns a <xref:System.Nullable%601?displayProperty=fullName>, which is initialized like any struct.</span></span>

<span data-ttu-id="fa8ab-114">`default(T)` 運算式不限於泛型類別及方法。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-114">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="fa8ab-115">預設值運算式可搭配任何 managed 型別使用。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-115">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="fa8ab-116">以下任一運算式均有效：</span><span class="sxs-lookup"><span data-stu-id="fa8ab-116">Any of these expressions are valid:</span></span>

 <span data-ttu-id="fa8ab-117">[!code-cs[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]</span><span class="sxs-lookup"><span data-stu-id="fa8ab-117">[!code-cs[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]</span></span>

 <span data-ttu-id="fa8ab-118">下列 `GenericList<T>` 類別的範例示範如何在泛型類別中使用 `default(T)` 運算子。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-118">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="fa8ab-119">如需詳細資訊，請參閱[泛型概觀](../generics/introduction-to-generics.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-119">For more information, see [Generics Overview](../generics/introduction-to-generics.md).</span></span>

 <span data-ttu-id="fa8ab-120">[!code-cs[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]</span><span class="sxs-lookup"><span data-stu-id="fa8ab-120">[!code-cs[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]</span></span>

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="fa8ab-121">預設常值和型別推斷</span><span class="sxs-lookup"><span data-stu-id="fa8ab-121">default literal and type inference</span></span>

<span data-ttu-id="fa8ab-122">從 C# 7.1 開始，可以在編譯器能推斷運算式型別時，將 `default` 用於預設值運算式。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-122">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="fa8ab-123">`default` 常值會產生與對等 `default(T)` 相同的值，其中 `T` 是推斷出來的型別。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-123">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="fa8ab-124">這樣能夠減少宣告型別一次以上所產生的冗餘，讓程式碼更精簡。</span><span class="sxs-lookup"><span data-stu-id="fa8ab-124">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="fa8ab-125">`default` 常值可以用在下列任一位置：</span><span class="sxs-lookup"><span data-stu-id="fa8ab-125">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="fa8ab-126">變數初始設定式</span><span class="sxs-lookup"><span data-stu-id="fa8ab-126">variable initializer</span></span>
- <span data-ttu-id="fa8ab-127">變數設定</span><span class="sxs-lookup"><span data-stu-id="fa8ab-127">variable assignment</span></span>
- <span data-ttu-id="fa8ab-128">宣告選用參數的預設值</span><span class="sxs-lookup"><span data-stu-id="fa8ab-128">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="fa8ab-129">提供方法呼叫引數的值</span><span class="sxs-lookup"><span data-stu-id="fa8ab-129">providing the value for a method call argument</span></span>
- <span data-ttu-id="fa8ab-130">傳回陳述式 (或運算式主體成員中的運算式)</span><span class="sxs-lookup"><span data-stu-id="fa8ab-130">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="fa8ab-131">下列範例示範 `default` 常值在預設值運算式中的多種使用方式：</span><span class="sxs-lookup"><span data-stu-id="fa8ab-131">The following example shows many usages of the `default` literal in a default value expression:</span></span>

<span data-ttu-id="fa8ab-132">[!code-cs[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]</span><span class="sxs-lookup"><span data-stu-id="fa8ab-132">[!code-cs[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fa8ab-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="fa8ab-133">See also</span></span>

 <span data-ttu-id="fa8ab-134"><xref:System.Collections.Generic> [C# 程式設計指南](../index.md) </span><span class="sxs-lookup"><span data-stu-id="fa8ab-134"><xref:System.Collections.Generic> [C# Programming Guide](../index.md) </span></span>  
 <span data-ttu-id="fa8ab-135">[泛型](../generics/index.md) </span><span class="sxs-lookup"><span data-stu-id="fa8ab-135">[Generics](../generics/index.md) </span></span>  
 <span data-ttu-id="fa8ab-136">[泛型方法](../generics/generic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="fa8ab-136">[Generic Methods](../generics/generic-methods.md) </span></span>  
 [<span data-ttu-id="fa8ab-137">泛型</span><span class="sxs-lookup"><span data-stu-id="fa8ab-137">Generics</span></span>](~/docs/standard/generics/index.md)   

