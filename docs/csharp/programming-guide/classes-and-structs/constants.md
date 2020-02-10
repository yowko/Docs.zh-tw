---
title: 常數 - C# 程式設計手冊
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 85f6684617b893bdd85eb5b530aa2481941fbc5d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093548"
---
# <a name="constants-c-programming-guide"></a><span data-ttu-id="9dbcd-102">常數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="9dbcd-102">Constants (C# Programming Guide)</span></span>
<span data-ttu-id="9dbcd-103">常數是在編譯時期已知且不會在程式存留期變更的不可變值。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-103">Constants are immutable values which are known at compile time and do not change for the life of the program.</span></span> <span data-ttu-id="9dbcd-104">常數是使用 [const](../../language-reference/keywords/const.md) 修飾詞所宣告。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-104">Constants are declared with the [const](../../language-reference/keywords/const.md) modifier.</span></span> <span data-ttu-id="9dbcd-105">C#只有[內建類型](../../language-reference/builtin-types/built-in-types.md)（<xref:System.Object?displayProperty=nameWithType>除外）可以宣告為 `const`。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-105">Only the C# [built-in types](../../language-reference/builtin-types/built-in-types.md) (excluding <xref:System.Object?displayProperty=nameWithType>) may be declared as `const`.</span></span> <span data-ttu-id="9dbcd-106">使用者定義型別 (包括類別、結構和陣列) 不能是 `const`。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-106">User-defined types, including classes, structs, and arrays, cannot be `const`.</span></span> <span data-ttu-id="9dbcd-107">使用 [readonly](../../language-reference/keywords/readonly.md) 修飾詞來建立在執行階段一次初始化的類別、結構或陣列 (例如在建構函式中)，因而無法進行變更。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-107">Use the [readonly](../../language-reference/keywords/readonly.md) modifier to create a class, struct, or array that is initialized one time at runtime (for example in a constructor) and thereafter cannot be changed.</span></span>  
  
 <span data-ttu-id="9dbcd-108">C# 不支援 `const` 方法、屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-108">C# does not support `const` methods, properties, or events.</span></span>  
  
 <span data-ttu-id="9dbcd-109">enum 類型可讓您定義整數內建類型的具名常數 (例如 `int`、`uint`、`long` 等等)。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-109">The enum type enables you to define named constants for integral built-in types (for example `int`, `uint`, `long`, and so on).</span></span> <span data-ttu-id="9dbcd-110">如需詳細資訊，請參閱 [enum](../../language-reference/builtin-types/enum.md)。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-110">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="9dbcd-111">常數必須在宣告時進行初始化。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-111">Constants must be initialized as they are declared.</span></span> <span data-ttu-id="9dbcd-112">例如：</span><span class="sxs-lookup"><span data-stu-id="9dbcd-112">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 <span data-ttu-id="9dbcd-113">在此範例中，`months` 常數一律為 12，而且甚至類別本身也不能進行變更。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-113">In this example, the constant `months` is always 12, and it cannot be changed even by the class itself.</span></span> <span data-ttu-id="9dbcd-114">事實上，編譯器在 C# 原始程式碼中遇到常數識別碼 (例如　`months`) 時，會直接將常值替代為它所產生的中繼語言 (IL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-114">In fact, when the compiler encounters a constant identifier in C# source code (for example, `months`), it substitutes the literal value directly into the intermediate language (IL) code that it produces.</span></span> <span data-ttu-id="9dbcd-115">因為在執行階段沒有與常數相關聯的變數位址，所以無法以傳址方式傳遞 `const` 欄位，而且無法顯示為運算式中的左值。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-115">Because there is no variable address associated with a constant at run time, `const` fields cannot be passed by reference and cannot appear as an l-value in an expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9dbcd-116">當您參照其他程式碼中所定義的常數值 (例如 DLL) 時，請小心。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-116">Use caution when you refer to constant values defined in other code such as DLLs.</span></span> <span data-ttu-id="9dbcd-117">如果新版本的 DLL 定義常數的新值，則除非對新版本重新編譯新值，否則您的程式仍會保留舊常值。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-117">If a new version of the DLL defines a new value for the constant, your program will still hold the old literal value until it is recompiled against the new version.</span></span>  
  
 <span data-ttu-id="9dbcd-118">可以同時宣告相同類型的多個常數，例如︰</span><span class="sxs-lookup"><span data-stu-id="9dbcd-118">Multiple constants of the same type can be declared at the same time, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 <span data-ttu-id="9dbcd-119">如果用來初始化常數的運算式未建立循環參考，則可以參照另一個常數。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-119">The expression that is used to initialize a constant can refer to another constant if it does not create a circular reference.</span></span> <span data-ttu-id="9dbcd-120">例如：</span><span class="sxs-lookup"><span data-stu-id="9dbcd-120">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 <span data-ttu-id="9dbcd-121">常數可以標記為 [public](../../language-reference/keywords/public.md)、[private](../../language-reference/keywords/private.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md) 或 [private protected](../../language-reference/keywords/private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-121">Constants can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="9dbcd-122">這些存取修飾詞定義類別使用者如何存取常數。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-122">These access modifiers define how users of the class can access the constant.</span></span> <span data-ttu-id="9dbcd-123">如需詳細資訊，請參閱[存取修飾詞](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-123">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="9dbcd-124">因為類型之所有執行個體的常數值都會相同，所以常數的存取方式就像它們是 [static](../../language-reference/keywords/static.md) 欄位一樣。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-124">Constants are accessed as if they were [static](../../language-reference/keywords/static.md) fields because the value of the constant is the same for all instances of the type.</span></span> <span data-ttu-id="9dbcd-125">您未使用 `static` 關鍵字來宣告它們。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-125">You do not use the `static` keyword to declare them.</span></span> <span data-ttu-id="9dbcd-126">不在定義常數之類別中的運算式必須使用類別名稱、句號以及存取常數的常數名稱。</span><span class="sxs-lookup"><span data-stu-id="9dbcd-126">Expressions that are not in the class that defines the constant must use the class name, a period, and the name of the constant to access the constant.</span></span> <span data-ttu-id="9dbcd-127">例如：</span><span class="sxs-lookup"><span data-stu-id="9dbcd-127">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="9dbcd-128">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9dbcd-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9dbcd-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dbcd-129">See also</span></span>

- [<span data-ttu-id="9dbcd-130">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9dbcd-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9dbcd-131">類別和結構</span><span class="sxs-lookup"><span data-stu-id="9dbcd-131">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="9dbcd-132">屬性</span><span class="sxs-lookup"><span data-stu-id="9dbcd-132">Properties</span></span>](./properties.md)
- [<span data-ttu-id="9dbcd-133">類型</span><span class="sxs-lookup"><span data-stu-id="9dbcd-133">Types</span></span>](../types/index.md)
- [<span data-ttu-id="9dbcd-134">readonly</span><span class="sxs-lookup"><span data-stu-id="9dbcd-134">readonly</span></span>](../../language-reference/keywords/readonly.md)
- <span data-ttu-id="9dbcd-135">[Immutability in C# Part One: Kinds of Immutability](https://docs.microsoft.com/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability) (C# 中不變性第一部分：不變性類型)</span><span class="sxs-lookup"><span data-stu-id="9dbcd-135">[Immutability in C# Part One: Kinds of Immutability](https://docs.microsoft.com/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability)</span></span>
