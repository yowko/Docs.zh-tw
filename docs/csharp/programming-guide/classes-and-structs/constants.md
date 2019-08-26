---
title: 常數 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 7da86a8999f6cc36a7b71f70fd92a363673824b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924537"
---
# <a name="constants-c-programming-guide"></a><span data-ttu-id="38958-102">常數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="38958-102">Constants (C# Programming Guide)</span></span>
<span data-ttu-id="38958-103">常數是在編譯時期已知且不會在程式存留期變更的不可變值。</span><span class="sxs-lookup"><span data-stu-id="38958-103">Constants are immutable values which are known at compile time and do not change for the life of the program.</span></span> <span data-ttu-id="38958-104">常數是使用 [const](../../language-reference/keywords/const.md) 修飾詞所宣告。</span><span class="sxs-lookup"><span data-stu-id="38958-104">Constants are declared with the [const](../../language-reference/keywords/const.md) modifier.</span></span> <span data-ttu-id="38958-105">有 C# 內建型別 (不含 <xref:System.Object?displayProperty=nameWithType>) 才能宣告為 `const`。</span><span class="sxs-lookup"><span data-stu-id="38958-105">Only the C# built-in types (excluding <xref:System.Object?displayProperty=nameWithType>) may be declared as `const`.</span></span> <span data-ttu-id="38958-106">如需內建類型的清單，請參閱[內建類型資料表](../../language-reference/keywords/built-in-types-table.md)。</span><span class="sxs-lookup"><span data-stu-id="38958-106">For a list of the built-in types, see [Built-In Types Table](../../language-reference/keywords/built-in-types-table.md).</span></span> <span data-ttu-id="38958-107">使用者定義型別 (包括類別、結構和陣列) 不能是 `const`。</span><span class="sxs-lookup"><span data-stu-id="38958-107">User-defined types, including classes, structs, and arrays, cannot be `const`.</span></span> <span data-ttu-id="38958-108">使用 [readonly](../../language-reference/keywords/readonly.md) 修飾詞來建立在執行階段一次初始化的類別、結構或陣列 (例如在建構函式中)，因而無法進行變更。</span><span class="sxs-lookup"><span data-stu-id="38958-108">Use the [readonly](../../language-reference/keywords/readonly.md) modifier to create a class, struct, or array that is initialized one time at runtime (for example in a constructor) and thereafter cannot be changed.</span></span>  
  
 <span data-ttu-id="38958-109">C# 不支援 `const` 方法、屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="38958-109">C# does not support `const` methods, properties, or events.</span></span>  
  
 <span data-ttu-id="38958-110">enum 類型可讓您定義整數內建類型的具名常數 (例如 `int`、`uint`、`long` 等等)。</span><span class="sxs-lookup"><span data-stu-id="38958-110">The enum type enables you to define named constants for integral built-in types (for example `int`, `uint`, `long`, and so on).</span></span> <span data-ttu-id="38958-111">如需詳細資訊，請參閱 [enum](../../language-reference/keywords/enum.md)。</span><span class="sxs-lookup"><span data-stu-id="38958-111">For more information, see [enum](../../language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="38958-112">常數必須在宣告時進行初始化。</span><span class="sxs-lookup"><span data-stu-id="38958-112">Constants must be initialized as they are declared.</span></span> <span data-ttu-id="38958-113">例如：</span><span class="sxs-lookup"><span data-stu-id="38958-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 <span data-ttu-id="38958-114">在此範例中，`months` 常數一律為 12，而且甚至類別本身也不能進行變更。</span><span class="sxs-lookup"><span data-stu-id="38958-114">In this example, the constant `months` is always 12, and it cannot be changed even by the class itself.</span></span> <span data-ttu-id="38958-115">事實上，編譯器在 C# 原始程式碼中遇到常數識別碼 (例如　`months`) 時，會直接將常值替代為它所產生的中繼語言 (IL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="38958-115">In fact, when the compiler encounters a constant identifier in C# source code (for example, `months`), it substitutes the literal value directly into the intermediate language (IL) code that it produces.</span></span> <span data-ttu-id="38958-116">因為在執行階段沒有與常數相關聯的變數位址，所以無法以傳址方式傳遞 `const` 欄位，而且無法顯示為運算式中的左值。</span><span class="sxs-lookup"><span data-stu-id="38958-116">Because there is no variable address associated with a constant at run time, `const` fields cannot be passed by reference and cannot appear as an l-value in an expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38958-117">當您參照其他程式碼中所定義的常數值 (例如 DLL) 時，請小心。</span><span class="sxs-lookup"><span data-stu-id="38958-117">Use caution when you refer to constant values defined in other code such as DLLs.</span></span> <span data-ttu-id="38958-118">如果新版本的 DLL 定義常數的新值，則除非對新版本重新編譯新值，否則您的程式仍會保留舊常值。</span><span class="sxs-lookup"><span data-stu-id="38958-118">If a new version of the DLL defines a new value for the constant, your program will still hold the old literal value until it is recompiled against the new version.</span></span>  
  
 <span data-ttu-id="38958-119">可以同時宣告相同類型的多個常數，例如︰</span><span class="sxs-lookup"><span data-stu-id="38958-119">Multiple constants of the same type can be declared at the same time, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 <span data-ttu-id="38958-120">如果用來初始化常數的運算式未建立循環參考，則可以參照另一個常數。</span><span class="sxs-lookup"><span data-stu-id="38958-120">The expression that is used to initialize a constant can refer to another constant if it does not create a circular reference.</span></span> <span data-ttu-id="38958-121">例如：</span><span class="sxs-lookup"><span data-stu-id="38958-121">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 <span data-ttu-id="38958-122">常數可以標記為 [public](../../language-reference/keywords/public.md)、[private](../../language-reference/keywords/private.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md) 或 [private protected](../../language-reference/keywords/private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="38958-122">Constants can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="38958-123">這些存取修飾詞定義類別使用者如何存取常數。</span><span class="sxs-lookup"><span data-stu-id="38958-123">These access modifiers define how users of the class can access the constant.</span></span> <span data-ttu-id="38958-124">如需詳細資訊，請參閱[存取修飾詞](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="38958-124">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="38958-125">因為類型之所有執行個體的常數值都會相同，所以常數的存取方式就像它們是 [static](../../language-reference/keywords/static.md) 欄位一樣。</span><span class="sxs-lookup"><span data-stu-id="38958-125">Constants are accessed as if they were [static](../../language-reference/keywords/static.md) fields because the value of the constant is the same for all instances of the type.</span></span> <span data-ttu-id="38958-126">您未使用 `static` 關鍵字來宣告它們。</span><span class="sxs-lookup"><span data-stu-id="38958-126">You do not use the `static` keyword to declare them.</span></span> <span data-ttu-id="38958-127">不在定義常數之類別中的運算式必須使用類別名稱、句號以及存取常數的常數名稱。</span><span class="sxs-lookup"><span data-stu-id="38958-127">Expressions that are not in the class that defines the constant must use the class name, a period, and the name of the constant to access the constant.</span></span> <span data-ttu-id="38958-128">例如：</span><span class="sxs-lookup"><span data-stu-id="38958-128">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="38958-129">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="38958-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="38958-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38958-130">See also</span></span>

- [<span data-ttu-id="38958-131">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="38958-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="38958-132">類別和結構</span><span class="sxs-lookup"><span data-stu-id="38958-132">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="38958-133">屬性</span><span class="sxs-lookup"><span data-stu-id="38958-133">Properties</span></span>](./properties.md)
- [<span data-ttu-id="38958-134">型別</span><span class="sxs-lookup"><span data-stu-id="38958-134">Types</span></span>](../types/index.md)
- [<span data-ttu-id="38958-135">readonly</span><span class="sxs-lookup"><span data-stu-id="38958-135">readonly</span></span>](../../language-reference/keywords/readonly.md)
- <span data-ttu-id="38958-136">[C# 中的不變性，第一部分：不變性的類型](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="38958-136">[Immutability in C# Part One: Kinds of Immutability](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability)</span></span>
