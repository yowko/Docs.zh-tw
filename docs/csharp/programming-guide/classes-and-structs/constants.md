---
title: 常數 - C# 程式設計手冊
description: 'C # 中的常數是編譯時間常值，在程式編譯後不會變更。 只有 c # 內建類型可以是常數。'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: dd42dcd62bb46898c20f14cdc893b8f5801894f2
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474978"
---
# <a name="constants-c-programming-guide"></a><span data-ttu-id="9e131-104">常數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="9e131-104">Constants (C# Programming Guide)</span></span>
<span data-ttu-id="9e131-105">常數是在編譯時期已知且不會在程式存留期變更的不可變值。</span><span class="sxs-lookup"><span data-stu-id="9e131-105">Constants are immutable values which are known at compile time and do not change for the life of the program.</span></span> <span data-ttu-id="9e131-106">常數是使用 [const](../../language-reference/keywords/const.md) 修飾詞所宣告。</span><span class="sxs-lookup"><span data-stu-id="9e131-106">Constants are declared with the [const](../../language-reference/keywords/const.md) modifier.</span></span> <span data-ttu-id="9e131-107">只有 c #[內建類型](../../language-reference/builtin-types/built-in-types.md)（不包括 <xref:System.Object?displayProperty=nameWithType> ）可以宣告為 `const` 。</span><span class="sxs-lookup"><span data-stu-id="9e131-107">Only the C# [built-in types](../../language-reference/builtin-types/built-in-types.md) (excluding <xref:System.Object?displayProperty=nameWithType>) may be declared as `const`.</span></span> <span data-ttu-id="9e131-108">使用者定義型別 (包括類別、結構和陣列) 不能是 `const`。</span><span class="sxs-lookup"><span data-stu-id="9e131-108">User-defined types, including classes, structs, and arrays, cannot be `const`.</span></span> <span data-ttu-id="9e131-109">使用 [readonly](../../language-reference/keywords/readonly.md) 修飾詞來建立在執行階段一次初始化的類別、結構或陣列 (例如在建構函式中)，因而無法進行變更。</span><span class="sxs-lookup"><span data-stu-id="9e131-109">Use the [readonly](../../language-reference/keywords/readonly.md) modifier to create a class, struct, or array that is initialized one time at runtime (for example in a constructor) and thereafter cannot be changed.</span></span>  
  
 <span data-ttu-id="9e131-110">C# 不支援 `const` 方法、屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="9e131-110">C# does not support `const` methods, properties, or events.</span></span>  
  
 <span data-ttu-id="9e131-111">enum 類型可讓您定義整數內建類型的具名常數 (例如 `int`、`uint`、`long` 等等)。</span><span class="sxs-lookup"><span data-stu-id="9e131-111">The enum type enables you to define named constants for integral built-in types (for example `int`, `uint`, `long`, and so on).</span></span> <span data-ttu-id="9e131-112">如需詳細資訊，請參閱 [enum](../../language-reference/builtin-types/enum.md)。</span><span class="sxs-lookup"><span data-stu-id="9e131-112">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="9e131-113">常數必須在宣告時進行初始化。</span><span class="sxs-lookup"><span data-stu-id="9e131-113">Constants must be initialized as they are declared.</span></span> <span data-ttu-id="9e131-114">例如：</span><span class="sxs-lookup"><span data-stu-id="9e131-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 <span data-ttu-id="9e131-115">在此範例中，`months` 常數一律為 12，而且甚至類別本身也不能進行變更。</span><span class="sxs-lookup"><span data-stu-id="9e131-115">In this example, the constant `months` is always 12, and it cannot be changed even by the class itself.</span></span> <span data-ttu-id="9e131-116">事實上，編譯器在 C# 原始程式碼中遇到常數識別碼 (例如　`months`) 時，會直接將常值替代為它所產生的中繼語言 (IL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="9e131-116">In fact, when the compiler encounters a constant identifier in C# source code (for example, `months`), it substitutes the literal value directly into the intermediate language (IL) code that it produces.</span></span> <span data-ttu-id="9e131-117">因為在執行階段沒有與常數相關聯的變數位址，所以無法以傳址方式傳遞 `const` 欄位，而且無法顯示為運算式中的左值。</span><span class="sxs-lookup"><span data-stu-id="9e131-117">Because there is no variable address associated with a constant at run time, `const` fields cannot be passed by reference and cannot appear as an l-value in an expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e131-118">當您參照其他程式碼中所定義的常數值 (例如 DLL) 時，請小心。</span><span class="sxs-lookup"><span data-stu-id="9e131-118">Use caution when you refer to constant values defined in other code such as DLLs.</span></span> <span data-ttu-id="9e131-119">如果新版本的 DLL 定義常數的新值，則除非對新版本重新編譯新值，否則您的程式仍會保留舊常值。</span><span class="sxs-lookup"><span data-stu-id="9e131-119">If a new version of the DLL defines a new value for the constant, your program will still hold the old literal value until it is recompiled against the new version.</span></span>  
  
 <span data-ttu-id="9e131-120">可以同時宣告相同類型的多個常數，例如︰</span><span class="sxs-lookup"><span data-stu-id="9e131-120">Multiple constants of the same type can be declared at the same time, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 <span data-ttu-id="9e131-121">如果用來初始化常數的運算式未建立循環參考，則可以參照另一個常數。</span><span class="sxs-lookup"><span data-stu-id="9e131-121">The expression that is used to initialize a constant can refer to another constant if it does not create a circular reference.</span></span> <span data-ttu-id="9e131-122">例如：</span><span class="sxs-lookup"><span data-stu-id="9e131-122">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 <span data-ttu-id="9e131-123">常數可以標記為 [public](../../language-reference/keywords/public.md)、[private](../../language-reference/keywords/private.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md) 或 [private protected](../../language-reference/keywords/private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="9e131-123">Constants can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="9e131-124">這些存取修飾詞定義類別使用者如何存取常數。</span><span class="sxs-lookup"><span data-stu-id="9e131-124">These access modifiers define how users of the class can access the constant.</span></span> <span data-ttu-id="9e131-125">如需詳細資訊，請參閱[存取修飾詞](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="9e131-125">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="9e131-126">因為類型之所有執行個體的常數值都會相同，所以常數的存取方式就像它們是 [static](../../language-reference/keywords/static.md) 欄位一樣。</span><span class="sxs-lookup"><span data-stu-id="9e131-126">Constants are accessed as if they were [static](../../language-reference/keywords/static.md) fields because the value of the constant is the same for all instances of the type.</span></span> <span data-ttu-id="9e131-127">您未使用 `static` 關鍵字來宣告它們。</span><span class="sxs-lookup"><span data-stu-id="9e131-127">You do not use the `static` keyword to declare them.</span></span> <span data-ttu-id="9e131-128">不在定義常數之類別中的運算式必須使用類別名稱、句號以及存取常數的常數名稱。</span><span class="sxs-lookup"><span data-stu-id="9e131-128">Expressions that are not in the class that defines the constant must use the class name, a period, and the name of the constant to access the constant.</span></span> <span data-ttu-id="9e131-129">例如：</span><span class="sxs-lookup"><span data-stu-id="9e131-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="9e131-130">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9e131-130">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9e131-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e131-131">See also</span></span>

- [<span data-ttu-id="9e131-132">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9e131-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9e131-133">類別和結構</span><span class="sxs-lookup"><span data-stu-id="9e131-133">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="9e131-134">屬性</span><span class="sxs-lookup"><span data-stu-id="9e131-134">Properties</span></span>](./properties.md)
- [<span data-ttu-id="9e131-135">類型</span><span class="sxs-lookup"><span data-stu-id="9e131-135">Types</span></span>](../types/index.md)
- [<span data-ttu-id="9e131-136">唯讀</span><span class="sxs-lookup"><span data-stu-id="9e131-136">readonly</span></span>](../../language-reference/keywords/readonly.md)
- <span data-ttu-id="9e131-137">[Immutability in C# Part One: Kinds of Immutability](https://docs.microsoft.com/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability) (C# 中不變性第一部分：不變性類型)</span><span class="sxs-lookup"><span data-stu-id="9e131-137">[Immutability in C# Part One: Kinds of Immutability](https://docs.microsoft.com/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability)</span></span>
