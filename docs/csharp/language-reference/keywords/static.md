---
title: "static (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- static
- static_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
caps.latest.revision: 26
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
ms.openlocfilehash: 8e46dc2f00d1c185379dba1017ca445b9ae5ae72
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="static-c-reference"></a><span data-ttu-id="8dd9a-102">static (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8dd9a-102">static (C# Reference)</span></span>
<span data-ttu-id="8dd9a-103">使用 `static` 修飾詞來宣告靜態成員，而靜態成員屬於類型本身，而不是特定物件。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="8dd9a-104">`static` 修飾詞可以與類別、欄位、方法、屬性、運算子、事件和建構函式搭配使用，但不能與索引子、完成項或類別以外的類型搭配使用。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="8dd9a-105">如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-105">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dd9a-106">範例</span><span class="sxs-lookup"><span data-stu-id="8dd9a-106">Example</span></span>  
 <span data-ttu-id="8dd9a-107">下列類別宣告為 `static`，並且只包含 `static` 方法：</span><span class="sxs-lookup"><span data-stu-id="8dd9a-107">The following class is declared as `static` and contains only `static` methods:</span></span>  
  
 <span data-ttu-id="8dd9a-108">[!code-cs[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8dd9a-108">[!code-cs[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]</span></span>  
  
 <span data-ttu-id="8dd9a-109">常數或型別宣告隱含為靜態成員。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-109">A constant or type declaration is implicitly a static member.</span></span>  
  
 <span data-ttu-id="8dd9a-110">靜態成員無法透過執行個體進行參考。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-110">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="8dd9a-111">而是透過類型名稱進行參考。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-111">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="8dd9a-112">例如，請參考下列類別：</span><span class="sxs-lookup"><span data-stu-id="8dd9a-112">For example, consider the following class:</span></span>  
  
 <span data-ttu-id="8dd9a-113">[!code-cs[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="8dd9a-113">[!code-cs[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]</span></span>  
  
 <span data-ttu-id="8dd9a-114">若要參照靜態成員 `x`，除非可以從相同的範圍存取該成員，否則請使用完整名稱 `MyBaseC.MyStruct.x`︰</span><span class="sxs-lookup"><span data-stu-id="8dd9a-114">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 <span data-ttu-id="8dd9a-115">雖然類別的執行個體包含類別的所有執行個體欄位的個別複本，但是每個靜態欄位都只會有一個複本。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-115">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>  
  
 <span data-ttu-id="8dd9a-116">無法使用 [this](../../../csharp/language-reference/keywords/this.md) 來參考靜態方法或屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-116">It is not possible to use [this](../../../csharp/language-reference/keywords/this.md) to reference static methods or property accessors.</span></span>  
  
 <span data-ttu-id="8dd9a-117">如果將 `static` 關鍵字套用至類別，則類別的所有成員都必須是靜態。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-117">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>  
  
 <span data-ttu-id="8dd9a-118">類別和靜態類別可能會有靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-118">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="8dd9a-119">在啟動程式時與具現化類別時之間的某個點，會呼叫靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-119">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8dd9a-120">`static` 關鍵字的使用方式比在 C++ 中受到更多限制。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-120">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="8dd9a-121">若要與 C++ 關鍵字進行比較，請參閱[儲存類別 (C++)](/cpp/cpp/storage-classes-cpp#static)。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-121">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>
  
 <span data-ttu-id="8dd9a-122">若要示範靜態成員，請考慮使用代表公司員工的類別。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-122">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="8dd9a-123">假設此類別包含可計算員工人數的方法以及可儲存員工人數的欄位。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-123">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="8dd9a-124">方法和欄位都不屬於任何執行個體員工。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-124">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="8dd9a-125">相反地，它們屬於公司類別。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-125">Instead they belong to the company class.</span></span> <span data-ttu-id="8dd9a-126">因此，它們應該宣告為類別的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-126">Therefore, they should be declared as static members of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dd9a-127">範例</span><span class="sxs-lookup"><span data-stu-id="8dd9a-127">Example</span></span>  
 <span data-ttu-id="8dd9a-128">這個範例會讀取新員工的名稱和識別碼，並將員工計數器遞加一，然後顯示新員工和新員工人數的資訊。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-128">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="8dd9a-129">為求簡單，此程式會從鍵盤讀取目前的員工人數。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-129">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="8dd9a-130">在實際的應用程式中，應該從檔案讀取這項資訊。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-130">In a real application, this information should be read from a file.</span></span>  
  
 <span data-ttu-id="8dd9a-131">[!code-cs[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="8dd9a-131">[!code-cs[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dd9a-132">範例</span><span class="sxs-lookup"><span data-stu-id="8dd9a-132">Example</span></span>  
 <span data-ttu-id="8dd9a-133">這個範例示範，雖然您可以使用另一個尚未宣告的靜態欄位來初始化靜態欄位，但是除非將值明確指派給靜態欄位，否則不會定義結果。</span><span class="sxs-lookup"><span data-stu-id="8dd9a-133">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>  
  
 <span data-ttu-id="8dd9a-134">[!code-cs[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="8dd9a-134">[!code-cs[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="8dd9a-135">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="8dd9a-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8dd9a-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dd9a-136">See Also</span></span>  
 <span data-ttu-id="8dd9a-137">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="8dd9a-137">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="8dd9a-138">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8dd9a-138">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8dd9a-139">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="8dd9a-139">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="8dd9a-140">[修飾詞](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="8dd9a-140">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 [<span data-ttu-id="8dd9a-141">靜態類別和靜態類別成員</span><span class="sxs-lookup"><span data-stu-id="8dd9a-141">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)

