---
title: static 修飾詞 - C# 參考
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744657"
---
# <a name="static-c-reference"></a><span data-ttu-id="59e6b-102">static (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="59e6b-102">static (C# Reference)</span></span>

<span data-ttu-id="59e6b-103">使用 `static` 修飾詞來宣告靜態成員，而靜態成員屬於類型本身，而不是特定物件。</span><span class="sxs-lookup"><span data-stu-id="59e6b-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="59e6b-104">`static` 修飾詞可以用來宣告 `static` 類別。</span><span class="sxs-lookup"><span data-stu-id="59e6b-104">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="59e6b-105">在類別、介面和結構中，您可以將 `static` 修飾詞加入至欄位、方法、屬性、運算子、事件和函數。</span><span class="sxs-lookup"><span data-stu-id="59e6b-105">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="59e6b-106">`static` 修飾詞不能與索引子或完成項搭配使用。</span><span class="sxs-lookup"><span data-stu-id="59e6b-106">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="59e6b-107">如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="59e6b-107">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="59e6b-108">範例</span><span class="sxs-lookup"><span data-stu-id="59e6b-108">Example</span></span>

<span data-ttu-id="59e6b-109">下列類別宣告為 `static`，並且只包含 `static` 方法：</span><span class="sxs-lookup"><span data-stu-id="59e6b-109">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="59e6b-110">常數或類型宣告隱含為 `static` 成員。</span><span class="sxs-lookup"><span data-stu-id="59e6b-110">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="59e6b-111">無法透過實例參考 `static` 成員。</span><span class="sxs-lookup"><span data-stu-id="59e6b-111">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="59e6b-112">相反地，它是透過型別名稱來參考。</span><span class="sxs-lookup"><span data-stu-id="59e6b-112">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="59e6b-113">例如，請參考下列類別：</span><span class="sxs-lookup"><span data-stu-id="59e6b-113">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="59e6b-114">若要參考 `static` 成員 `x`，請使用完整名稱 `MyBaseC.MyStruct.x`，除非可以從相同的範圍存取該成員：</span><span class="sxs-lookup"><span data-stu-id="59e6b-114">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="59e6b-115">雖然類別的實例包含類別的所有實例欄位的個別複本，但每個 `static` 欄位只有一個複本。</span><span class="sxs-lookup"><span data-stu-id="59e6b-115">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="59e6b-116">您無法使用[`this`](this.md)來參考 `static` 方法或屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="59e6b-116">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="59e6b-117">如果 `static` 關鍵字套用至類別，則類別的所有成員都必須 `static`。</span><span class="sxs-lookup"><span data-stu-id="59e6b-117">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="59e6b-118">類別、介面和 `static` 類別可能會有 `static` 的構造函式。</span><span class="sxs-lookup"><span data-stu-id="59e6b-118">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="59e6b-119">在程式啟動和類別具現化的某個時間點，會呼叫 `static` 的函式。</span><span class="sxs-lookup"><span data-stu-id="59e6b-119">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="59e6b-120">`static` 關鍵字的使用方式比在 C++ 中受到更多限制。</span><span class="sxs-lookup"><span data-stu-id="59e6b-120">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="59e6b-121">若要與 C++ 關鍵字進行比較，請參閱[儲存類別 (C++)](/cpp/cpp/storage-classes-cpp#static)。</span><span class="sxs-lookup"><span data-stu-id="59e6b-121">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="59e6b-122">若要示範 `static` 成員，請考慮代表公司員工的類別。</span><span class="sxs-lookup"><span data-stu-id="59e6b-122">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="59e6b-123">假設此類別包含可計算員工人數的方法以及可儲存員工人數的欄位。</span><span class="sxs-lookup"><span data-stu-id="59e6b-123">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="59e6b-124">方法和欄位都不屬於任何一個員工實例。</span><span class="sxs-lookup"><span data-stu-id="59e6b-124">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="59e6b-125">相反地，它們屬於整個員工的類別。</span><span class="sxs-lookup"><span data-stu-id="59e6b-125">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="59e6b-126">它們應該宣告為類別的 `static` 成員。</span><span class="sxs-lookup"><span data-stu-id="59e6b-126">They should be declared as `static` members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="59e6b-127">範例</span><span class="sxs-lookup"><span data-stu-id="59e6b-127">Example</span></span>

<span data-ttu-id="59e6b-128">這個範例會讀取新員工的名稱和識別碼，並將員工計數器遞加一，然後顯示新員工和新員工人數的資訊。</span><span class="sxs-lookup"><span data-stu-id="59e6b-128">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="59e6b-129">此程式會從鍵盤讀取目前的員工人數。</span><span class="sxs-lookup"><span data-stu-id="59e6b-129">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="59e6b-130">範例</span><span class="sxs-lookup"><span data-stu-id="59e6b-130">Example</span></span>

<span data-ttu-id="59e6b-131">這個範例顯示您可以使用尚未宣告的另一個 `static` 欄位來初始化 `static` 欄位。</span><span class="sxs-lookup"><span data-stu-id="59e6b-131">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="59e6b-132">除非您明確地將值指派給 `static` 欄位，否則結果會是未定義的。</span><span class="sxs-lookup"><span data-stu-id="59e6b-132">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="59e6b-133">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="59e6b-133">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="59e6b-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="59e6b-134">See also</span></span>

- [<span data-ttu-id="59e6b-135">C# 參考</span><span class="sxs-lookup"><span data-stu-id="59e6b-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="59e6b-136">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="59e6b-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="59e6b-137">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="59e6b-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="59e6b-138">修飾詞</span><span class="sxs-lookup"><span data-stu-id="59e6b-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="59e6b-139">靜態類別和靜態類別成員</span><span class="sxs-lookup"><span data-stu-id="59e6b-139">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
