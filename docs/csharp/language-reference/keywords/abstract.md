---
title: abstract - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 3a4d29ae4814ccceb7b405d9c1749150059a24a0
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859583"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="fb934-102">abstract (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="fb934-102">abstract (C# Reference)</span></span>
<span data-ttu-id="fb934-103">`abstract` 修飾詞表示要修改的項目具有遺失或不完整的實作。</span><span class="sxs-lookup"><span data-stu-id="fb934-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="fb934-104">抽象修飾詞可以與類別、方法、屬性、索引子和事件搭配使用。</span><span class="sxs-lookup"><span data-stu-id="fb934-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="fb934-105">在類別宣告中使用 `abstract` 修飾詞，來表示某一類別只是要作為其他類別的基底類別，不是自行具現化。</span><span class="sxs-lookup"><span data-stu-id="fb934-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes, not instantiated on its own.</span></span> <span data-ttu-id="fb934-106">標記為抽象的成員，必須由衍生自抽象類別的非抽象類別實作。</span><span class="sxs-lookup"><span data-stu-id="fb934-106">Members marked as abstract must be implemented by non-abstract classes that derive from the abstract class.</span></span>
  
## <a name="example"></a><span data-ttu-id="fb934-107">範例</span><span class="sxs-lookup"><span data-stu-id="fb934-107">Example</span></span>  
 <span data-ttu-id="fb934-108">在此範例中，`Square` 類別必須提供 `GetArea` 的實作，因為它繼承自 `Shape`：</span><span class="sxs-lookup"><span data-stu-id="fb934-108">In this example, the class `Square` must provide an implementation of `GetArea` because it derives from `Shape`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="fb934-109">抽象類別具有下列功能：</span><span class="sxs-lookup"><span data-stu-id="fb934-109">Abstract classes have the following features:</span></span>  
  
- <span data-ttu-id="fb934-110">抽象類別無法具現化。</span><span class="sxs-lookup"><span data-stu-id="fb934-110">An abstract class cannot be instantiated.</span></span>  
  
- <span data-ttu-id="fb934-111">抽象類別可能包含抽象方法和存取子。</span><span class="sxs-lookup"><span data-stu-id="fb934-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
- <span data-ttu-id="fb934-112">因為兩個修飾詞的意義相反，所以無法使用 [sealed](../../../csharp/language-reference/keywords/sealed.md) 修飾詞來修改抽象類別。</span><span class="sxs-lookup"><span data-stu-id="fb934-112">It is not possible to modify an abstract class with the [sealed](../../../csharp/language-reference/keywords/sealed.md) modifier because the two modifiers have opposite meanings.</span></span> <span data-ttu-id="fb934-113">`sealed` 修飾詞可防止繼承類別，而 `abstract` 修飾詞需要繼承類別。</span><span class="sxs-lookup"><span data-stu-id="fb934-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
- <span data-ttu-id="fb934-114">衍生自抽象類別的非抽象類別必須包括所有繼承抽象方法和存取子的實際實作。</span><span class="sxs-lookup"><span data-stu-id="fb934-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="fb934-115">在方法或屬性宣告中使用 `abstract` 修飾詞，表示方法或屬性未包含實作。</span><span class="sxs-lookup"><span data-stu-id="fb934-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="fb934-116">抽象方法具有下列功能：</span><span class="sxs-lookup"><span data-stu-id="fb934-116">Abstract methods have the following features:</span></span>  
  
- <span data-ttu-id="fb934-117">抽象方法隱含為虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="fb934-117">An abstract method is implicitly a virtual method.</span></span>  
  
- <span data-ttu-id="fb934-118">只有在抽象類別中才允許抽象方法宣告。</span><span class="sxs-lookup"><span data-stu-id="fb934-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
- <span data-ttu-id="fb934-119">因為抽象方法宣告未提供實際實作，所以沒有方法主體；方法宣告的結尾就是分號，而且簽章後面沒有大括號 ({ })。</span><span class="sxs-lookup"><span data-stu-id="fb934-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="fb934-120">例如：</span><span class="sxs-lookup"><span data-stu-id="fb934-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="fb934-121">方法 [override](../../../csharp/language-reference/keywords/override.md) 提供了實作，而這個方法是非抽象類別的成員。</span><span class="sxs-lookup"><span data-stu-id="fb934-121">The implementation is provided by a method [override](../../../csharp/language-reference/keywords/override.md), which is a member of a non-abstract class.</span></span>  
  
- <span data-ttu-id="fb934-122">在抽象方法宣告中使用 [static](../../../csharp/language-reference/keywords/static.md) 或 [virtual](../../../csharp/language-reference/keywords/virtual.md) 修飾詞是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="fb934-122">It is an error to use the [static](../../../csharp/language-reference/keywords/static.md) or [virtual](../../../csharp/language-reference/keywords/virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="fb934-123">抽象屬性的行為類似抽象方法，但宣告和引動過程語法的差異除外。</span><span class="sxs-lookup"><span data-stu-id="fb934-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
- <span data-ttu-id="fb934-124">在靜態屬性上使用 `abstract` 修飾詞是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="fb934-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
- <span data-ttu-id="fb934-125">包括使用 [override](../../../csharp/language-reference/keywords/override.md) 修飾詞的屬性宣告，即可覆寫衍生類別中的抽象繼承屬性。</span><span class="sxs-lookup"><span data-stu-id="fb934-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](../../../csharp/language-reference/keywords/override.md) modifier.</span></span>  
  
 <span data-ttu-id="fb934-126">如需抽象類別的詳細資訊，請參閱[抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="fb934-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="fb934-127">抽象類別必須提供所有介面成員的實作。</span><span class="sxs-lookup"><span data-stu-id="fb934-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="fb934-128">實作介面的抽象類別可能會將介面方法對應至抽象方法。</span><span class="sxs-lookup"><span data-stu-id="fb934-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="fb934-129">例如：</span><span class="sxs-lookup"><span data-stu-id="fb934-129">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="fb934-130">範例</span><span class="sxs-lookup"><span data-stu-id="fb934-130">Example</span></span>  
 <span data-ttu-id="fb934-131">在此範例中，`DerivedClass` 類別衍生自抽象類別 `BaseClass`。</span><span class="sxs-lookup"><span data-stu-id="fb934-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="fb934-132">抽象類別包含抽象方法 `AbstractMethod` 和兩個抽象屬性：`X` 和 `Y`。</span><span class="sxs-lookup"><span data-stu-id="fb934-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="fb934-133">在上述範例中，如果您嘗試使用如下的陳述式來具現化抽象類別︰</span><span class="sxs-lookup"><span data-stu-id="fb934-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="fb934-134">您會收到錯誤，指出編譯器無法建立抽象類別 'BaseClass' 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fb934-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="fb934-135">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="fb934-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fb934-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb934-136">See also</span></span>

- [<span data-ttu-id="fb934-137">C# 參考</span><span class="sxs-lookup"><span data-stu-id="fb934-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="fb934-138">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="fb934-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="fb934-139">修飾詞</span><span class="sxs-lookup"><span data-stu-id="fb934-139">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
- [<span data-ttu-id="fb934-140">virtual</span><span class="sxs-lookup"><span data-stu-id="fb934-140">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)
- [<span data-ttu-id="fb934-141">override</span><span class="sxs-lookup"><span data-stu-id="fb934-141">override</span></span>](../../../csharp/language-reference/keywords/override.md)
- [<span data-ttu-id="fb934-142">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="fb934-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
