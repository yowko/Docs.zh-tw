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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744657"
---
# <a name="static-c-reference"></a><span data-ttu-id="2499e-102">static (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2499e-102">static (C# Reference)</span></span>

<span data-ttu-id="2499e-103">使用 `static` 修飾詞來宣告靜態成員，而靜態成員屬於類型本身，而不是特定物件。</span><span class="sxs-lookup"><span data-stu-id="2499e-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="2499e-104">修改`static`器可用於聲明`static`類。</span><span class="sxs-lookup"><span data-stu-id="2499e-104">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="2499e-105">在類、介面和結構中，您可以將`static`修改器添加到欄位、方法、屬性、運算子、事件和建構函式。</span><span class="sxs-lookup"><span data-stu-id="2499e-105">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="2499e-106">修改`static`器不能與索引子或終端子一起使用。</span><span class="sxs-lookup"><span data-stu-id="2499e-106">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="2499e-107">有關詳細資訊，請參閱[靜態類和靜態類成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="2499e-107">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="2499e-108">範例</span><span class="sxs-lookup"><span data-stu-id="2499e-108">Example</span></span>

<span data-ttu-id="2499e-109">下列類別宣告為 `static`，並且只包含 `static` 方法：</span><span class="sxs-lookup"><span data-stu-id="2499e-109">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="2499e-110">常量或型別宣告是隱式`static`成員。</span><span class="sxs-lookup"><span data-stu-id="2499e-110">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="2499e-111">無法通過`static`實例引用成員。</span><span class="sxs-lookup"><span data-stu-id="2499e-111">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="2499e-112">相反，它是通過類型名稱引用的。</span><span class="sxs-lookup"><span data-stu-id="2499e-112">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="2499e-113">例如，請參考下列類別：</span><span class="sxs-lookup"><span data-stu-id="2499e-113">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="2499e-114">要引用`static`成員`x`，請使用完全限定的名稱 ，`MyBaseC.MyStruct.x`除非成員可以從同一作用域訪問：</span><span class="sxs-lookup"><span data-stu-id="2499e-114">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="2499e-115">雖然類的實例包含類所有實例欄位的單獨副本，但每個`static`欄位只有一個副本。</span><span class="sxs-lookup"><span data-stu-id="2499e-115">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="2499e-116">不能用於[`this`](this.md)引用`static`方法或屬性訪問器。</span><span class="sxs-lookup"><span data-stu-id="2499e-116">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="2499e-117">如果關鍵字`static`應用於類，則類的所有成員必須為`static`。</span><span class="sxs-lookup"><span data-stu-id="2499e-117">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="2499e-118">類、介面和`static`類可能具有`static`建構函式。</span><span class="sxs-lookup"><span data-stu-id="2499e-118">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="2499e-119">在`static`程式啟動和類具現化之間的某個點調用建構函式。</span><span class="sxs-lookup"><span data-stu-id="2499e-119">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="2499e-120">`static` 關鍵字的使用方式比在 C++ 中受到更多限制。</span><span class="sxs-lookup"><span data-stu-id="2499e-120">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="2499e-121">若要與 C++ 關鍵字進行比較，請參閱[儲存類別 (C++)](/cpp/cpp/storage-classes-cpp#static)。</span><span class="sxs-lookup"><span data-stu-id="2499e-121">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="2499e-122">要演示`static`成員，請考慮代表公司員工的類。</span><span class="sxs-lookup"><span data-stu-id="2499e-122">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="2499e-123">假設此類別包含可計算員工人數的方法以及可儲存員工人數的欄位。</span><span class="sxs-lookup"><span data-stu-id="2499e-123">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="2499e-124">方法和欄位都不屬於任何一個員工實例。</span><span class="sxs-lookup"><span data-stu-id="2499e-124">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="2499e-125">相反，它們屬於整個員工階層。</span><span class="sxs-lookup"><span data-stu-id="2499e-125">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="2499e-126">應聲明它們為`static`類的成員。</span><span class="sxs-lookup"><span data-stu-id="2499e-126">They should be declared as `static` members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="2499e-127">範例</span><span class="sxs-lookup"><span data-stu-id="2499e-127">Example</span></span>

<span data-ttu-id="2499e-128">這個範例會讀取新員工的名稱和識別碼，並將員工計數器遞加一，然後顯示新員工和新員工人數的資訊。</span><span class="sxs-lookup"><span data-stu-id="2499e-128">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="2499e-129">此程式從鍵盤讀取當前員工人數。</span><span class="sxs-lookup"><span data-stu-id="2499e-129">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="2499e-130">範例</span><span class="sxs-lookup"><span data-stu-id="2499e-130">Example</span></span>

<span data-ttu-id="2499e-131">此示例顯示可以使用尚未聲明的另一`static`個`static`欄位初始化欄位。</span><span class="sxs-lookup"><span data-stu-id="2499e-131">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="2499e-132">在顯式為欄位分配值之前，`static`結果將未定義。</span><span class="sxs-lookup"><span data-stu-id="2499e-132">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="2499e-133">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="2499e-133">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2499e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2499e-134">See also</span></span>

- [<span data-ttu-id="2499e-135">C# 參考</span><span class="sxs-lookup"><span data-stu-id="2499e-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2499e-136">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2499e-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2499e-137">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="2499e-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2499e-138">修飾詞</span><span class="sxs-lookup"><span data-stu-id="2499e-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="2499e-139">靜態類別和靜態類別成員</span><span class="sxs-lookup"><span data-stu-id="2499e-139">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
