---
description: static 修飾詞 - C# 參考
title: static 修飾詞 - C# 參考
ms.date: 09/25/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 239163fc2f91ccbfe8b1c111a358db87d36a8308
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654635"
---
# <a name="static-c-reference"></a><span data-ttu-id="1bcc7-103">static (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1bcc7-103">static (C# Reference)</span></span>

<span data-ttu-id="1bcc7-104">此頁面涵蓋 `static` 修飾詞關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-104">This page covers the `static` modifier keyword.</span></span> <span data-ttu-id="1bcc7-105">`static`關鍵字也是指示詞的一部分 [`using static`](using-static.md) 。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-105">The `static` keyword is also part of the [`using static`](using-static.md) directive.</span></span>

<span data-ttu-id="1bcc7-106">使用 `static` 修飾詞來宣告靜態成員，而靜態成員屬於類型本身，而不是特定物件。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-106">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="1bcc7-107">`static`修飾詞可以用來宣告 `static` 類別。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-107">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="1bcc7-108">在類別、介面和結構中，您可以將修飾詞加入 `static` 至欄位、方法、屬性、運算子、事件和函式。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-108">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="1bcc7-109">`static`修飾元無法與索引子或完成項一起使用。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-109">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="1bcc7-110">如需詳細資訊，請參閱 [靜態類別和靜態類別成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-110">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

<span data-ttu-id="1bcc7-111">從 c # 8.0 開始，您可以將 `static` 修飾詞加入至 [區域函數](../../programming-guide/classes-and-structs/local-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-111">Beginning with C# 8.0, you can add the `static` modifier to a [local function](../../programming-guide/classes-and-structs/local-functions.md).</span></span> <span data-ttu-id="1bcc7-112">靜態區域函式無法捕捉本機變數或實例狀態。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-112">A static local function can't capture local variables or instance state.</span></span>

<span data-ttu-id="1bcc7-113">從 c # 9.0 開始，您可以將 `static` 修飾詞加入至 [lambda 運算式](../operators/lambda-expressions.md) 或 [匿名方法](../operators/delegate-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-113">Beginning with C# 9.0, you can add the `static` modifier to a [lambda expression](../operators/lambda-expressions.md) or [anonymous method](../operators/delegate-operator.md).</span></span> <span data-ttu-id="1bcc7-114">靜態 lambda 或匿名方法無法捕捉本機變數或實例狀態。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-114">A static lambda or anonymous method can't capture local variables or instance state.</span></span>

## <a name="example---static-class"></a><span data-ttu-id="1bcc7-115">範例-靜態類別</span><span class="sxs-lookup"><span data-stu-id="1bcc7-115">Example - static class</span></span>

<span data-ttu-id="1bcc7-116">下列類別宣告為 `static`，並且只包含 `static` 方法：</span><span class="sxs-lookup"><span data-stu-id="1bcc7-116">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="1bcc7-117">常數或型別宣告是隱含的 `static` 成員。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-117">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="1bcc7-118">`static`無法透過實例參考成員。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-118">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="1bcc7-119">相反地，它是透過型別名稱來參考。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-119">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="1bcc7-120">例如，請參考下列類別：</span><span class="sxs-lookup"><span data-stu-id="1bcc7-120">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="1bcc7-121">若要參考該 `static` 成員 `x` ，請使用完整名稱， `MyBaseC.MyStruct.x` 除非該成員可以從相同範圍存取：</span><span class="sxs-lookup"><span data-stu-id="1bcc7-121">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="1bcc7-122">雖然類別的實例包含類別的所有實例欄位的個別複本，但每個欄位只有一個複本 `static` 。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-122">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="1bcc7-123">您無法使用 [`this`](this.md) 參考 `static` 方法或屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-123">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="1bcc7-124">如果 `static` 關鍵字套用至類別，則類別的所有成員都必須是 `static` 。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-124">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="1bcc7-125">類別、介面和 `static` 類別可能具有函式 `static` 。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-125">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="1bcc7-126">在 `static` 程式啟動和具現化類別之間的某個時間點，會呼叫一個函數。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-126">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="1bcc7-127">`static` 關鍵字的使用方式比在 C++ 中受到更多限制。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-127">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="1bcc7-128">若要與 C++ 關鍵字進行比較，請參閱[儲存類別 (C++)](/cpp/cpp/storage-classes-cpp#static)。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-128">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="1bcc7-129">若要示範 `static` 成員，請考慮代表公司員工的類別。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-129">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="1bcc7-130">假設此類別包含可計算員工人數的方法以及可儲存員工人數的欄位。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-130">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="1bcc7-131">方法和欄位都不屬於任何一個員工實例。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-131">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="1bcc7-132">相反地，它們屬於整個員工的類別。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-132">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="1bcc7-133">它們應該宣告為 `static` 類別的成員。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-133">They should be declared as `static` members of the class.</span></span>

## <a name="example---static-field-and-method"></a><span data-ttu-id="1bcc7-134">範例-靜態欄位和方法</span><span class="sxs-lookup"><span data-stu-id="1bcc7-134">Example - static field and method</span></span>

<span data-ttu-id="1bcc7-135">這個範例會讀取新員工的名稱和識別碼，並將員工計數器遞加一，然後顯示新員工和新員工人數的資訊。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-135">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="1bcc7-136">此程式會從鍵盤讀取目前的員工數目。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-136">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a><span data-ttu-id="1bcc7-137">範例-靜態初始化</span><span class="sxs-lookup"><span data-stu-id="1bcc7-137">Example - static initialization</span></span>

<span data-ttu-id="1bcc7-138">此範例顯示您可以使用尚未宣告的 `static` 其他欄位來初始化欄位 `static` 。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-138">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="1bcc7-139">在您明確指派值給欄位之前，將不會定義結果 `static` 。</span><span class="sxs-lookup"><span data-stu-id="1bcc7-139">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="1bcc7-140">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1bcc7-140">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1bcc7-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bcc7-141">See also</span></span>

- [<span data-ttu-id="1bcc7-142">C # 參考</span><span class="sxs-lookup"><span data-stu-id="1bcc7-142">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1bcc7-143">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1bcc7-143">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1bcc7-144">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1bcc7-144">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1bcc7-145">修飾詞</span><span class="sxs-lookup"><span data-stu-id="1bcc7-145">Modifiers</span></span>](index.md)
- [<span data-ttu-id="1bcc7-146">using static 指示詞</span><span class="sxs-lookup"><span data-stu-id="1bcc7-146">using static directive</span></span>](using-static.md)
- [<span data-ttu-id="1bcc7-147">靜態類別和靜態類別成員</span><span class="sxs-lookup"><span data-stu-id="1bcc7-147">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
