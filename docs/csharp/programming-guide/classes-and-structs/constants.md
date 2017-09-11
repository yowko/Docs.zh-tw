---
title: "常數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
caps.latest.revision: 24
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 34d31860afdb83c0ae0ca00b4d523b00b920c680
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="constants-c-programming-guide"></a><span data-ttu-id="c27c0-102">常數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="c27c0-102">Constants (C# Programming Guide)</span></span>
<span data-ttu-id="c27c0-103">常數是在編譯時期已知且不會在程式存留期變更的不可變值。</span><span class="sxs-lookup"><span data-stu-id="c27c0-103">Constants are immutable values which are known at compile time and do not change for the life of the program.</span></span> <span data-ttu-id="c27c0-104">常數是使用 [const](../../../csharp/language-reference/keywords/const.md) 修飾詞所宣告。</span><span class="sxs-lookup"><span data-stu-id="c27c0-104">Constants are declared with the [const](../../../csharp/language-reference/keywords/const.md) modifier.</span></span> <span data-ttu-id="c27c0-105">只有 C# 內建類型 (不含 <xref:System.Object?displayProperty=fullName>) 才能宣告為 `const`。</span><span class="sxs-lookup"><span data-stu-id="c27c0-105">Only the C# built-in types (excluding <xref:System.Object?displayProperty=fullName>) may be declared as `const`.</span></span> <span data-ttu-id="c27c0-106">如需內建類型的清單，請參閱[內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)。</span><span class="sxs-lookup"><span data-stu-id="c27c0-106">For a list of the built-in types, see [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md).</span></span> <span data-ttu-id="c27c0-107">使用者定義型別 (包括類別、結構和陣列) 不能是 `const`。</span><span class="sxs-lookup"><span data-stu-id="c27c0-107">User-defined types, including classes, structs, and arrays, cannot be `const`.</span></span> <span data-ttu-id="c27c0-108">使用 [readonly](../../../csharp/language-reference/keywords/readonly.md) 修飾詞來建立在執行階段一次初始化的類別、結構或陣列 (例如在建構函式中)，因而無法進行變更。</span><span class="sxs-lookup"><span data-stu-id="c27c0-108">Use the [readonly](../../../csharp/language-reference/keywords/readonly.md) modifier to create a class, struct, or array that is initialized one time at runtime (for example in a constructor) and thereafter cannot be changed.</span></span>  
  
 <span data-ttu-id="c27c0-109">C# 不支援 `const` 方法、屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="c27c0-109">C# does not support `const` methods, properties, or events.</span></span>  
  
 <span data-ttu-id="c27c0-110">enum 類型可讓您定義整數內建類型的具名常數 (例如 `int`、`uint`、`long` 等等)。</span><span class="sxs-lookup"><span data-stu-id="c27c0-110">The enum type enables you to define named constants for integral built-in types (for example `int`, `uint`, `long`, and so on).</span></span> <span data-ttu-id="c27c0-111">如需詳細資訊，請參閱 [enum](../../../csharp/language-reference/keywords/enum.md)。</span><span class="sxs-lookup"><span data-stu-id="c27c0-111">For more information, see [enum](../../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="c27c0-112">常數必須在宣告時進行初始化。</span><span class="sxs-lookup"><span data-stu-id="c27c0-112">Constants must be initialized as they are declared.</span></span> <span data-ttu-id="c27c0-113">例如: </span><span class="sxs-lookup"><span data-stu-id="c27c0-113">For example:</span></span>  
  
 <span data-ttu-id="c27c0-114">[!code-cs[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c27c0-114">[!code-cs[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]</span></span>  
  
 <span data-ttu-id="c27c0-115">在此範例中，`months` 常數一律為 12，而且甚至類別本身也不能進行變更。</span><span class="sxs-lookup"><span data-stu-id="c27c0-115">In this example, the constant `months` is always 12, and it cannot be changed even by the class itself.</span></span> <span data-ttu-id="c27c0-116">事實上，編譯器在 C# 原始程式碼中遇到常數識別碼 (例如　`months`) 時，會直接將常值替代為它所產生的中繼語言 (IL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="c27c0-116">In fact, when the compiler encounters a constant identifier in C# source code (for example, `months`), it substitutes the literal value directly into the intermediate language (IL) code that it produces.</span></span> <span data-ttu-id="c27c0-117">因為在執行階段沒有與常數相關聯的變數位址，所以無法以傳址方式傳遞 `const` 欄位，而且無法顯示為運算式中的左值。</span><span class="sxs-lookup"><span data-stu-id="c27c0-117">Because there is no variable address associated with a constant at run time, `const` fields cannot be passed by reference and cannot appear as an l-value in an expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c27c0-118">當您參照其他程式碼中所定義的常數值 (例如 DLL) 時，請小心。</span><span class="sxs-lookup"><span data-stu-id="c27c0-118">Use caution when you refer to constant values defined in other code such as DLLs.</span></span> <span data-ttu-id="c27c0-119">如果新版本的 DLL 定義常數的新值，則除非對新版本重新編譯新值，否則您的程式仍會保留舊常值。</span><span class="sxs-lookup"><span data-stu-id="c27c0-119">If a new version of the DLL defines a new value for the constant, your program will still hold the old literal value until it is recompiled against the new version.</span></span>  
  
 <span data-ttu-id="c27c0-120">可以同時宣告相同類型的多個常數，例如︰</span><span class="sxs-lookup"><span data-stu-id="c27c0-120">Multiple constants of the same type can be declared at the same time, for example:</span></span>  
  
 <span data-ttu-id="c27c0-121">[!code-cs[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c27c0-121">[!code-cs[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]</span></span>  
  
 <span data-ttu-id="c27c0-122">如果用來初始化常數的運算式未建立循環參考，則可以參照另一個常數。</span><span class="sxs-lookup"><span data-stu-id="c27c0-122">The expression that is used to initialize a constant can refer to another constant if it does not create a circular reference.</span></span> <span data-ttu-id="c27c0-123">例如: </span><span class="sxs-lookup"><span data-stu-id="c27c0-123">For example:</span></span>  
  
 <span data-ttu-id="c27c0-124">[!code-cs[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c27c0-124">[!code-cs[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]</span></span>  
  
 <span data-ttu-id="c27c0-125">常數可以標記為 [public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md) 或 `protected``internal`。</span><span class="sxs-lookup"><span data-stu-id="c27c0-125">Constants can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or `protected``internal`.</span></span> <span data-ttu-id="c27c0-126">這些存取修飾詞定義類別使用者如何存取常數。</span><span class="sxs-lookup"><span data-stu-id="c27c0-126">These access modifiers define how users of the class can access the constant.</span></span> <span data-ttu-id="c27c0-127">如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="c27c0-127">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="c27c0-128">因為類型之所有執行個體的常數值都會相同，所以常數的存取方式就像它們是 [static](../../../csharp/language-reference/keywords/static.md) 欄位一樣。</span><span class="sxs-lookup"><span data-stu-id="c27c0-128">Constants are accessed as if they were [static](../../../csharp/language-reference/keywords/static.md) fields because the value of the constant is the same for all instances of the type.</span></span> <span data-ttu-id="c27c0-129">您未使用 `static` 關鍵字來宣告它們。</span><span class="sxs-lookup"><span data-stu-id="c27c0-129">You do not use the `static` keyword to declare them.</span></span> <span data-ttu-id="c27c0-130">不在定義常數之類別中的運算式必須使用類別名稱、句號以及存取常數的常數名稱。</span><span class="sxs-lookup"><span data-stu-id="c27c0-130">Expressions that are not in the class that defines the constant must use the class name, a period, and the name of the constant to access the constant.</span></span> <span data-ttu-id="c27c0-131">例如: </span><span class="sxs-lookup"><span data-stu-id="c27c0-131">For example:</span></span>  
  
 <span data-ttu-id="c27c0-132">[!code-cs[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="c27c0-132">[!code-cs[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c27c0-133">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c27c0-133">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c27c0-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c27c0-134">See Also</span></span>  
 <span data-ttu-id="c27c0-135">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c27c0-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="c27c0-136"> [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="c27c0-136"> [Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
<span data-ttu-id="c27c0-137"> [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md) </span><span class="sxs-lookup"><span data-stu-id="c27c0-137"> [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) </span></span>  
<span data-ttu-id="c27c0-138"> [類型](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="c27c0-138"> [Types](../../../csharp/programming-guide/types/index.md) </span></span>  
<span data-ttu-id="c27c0-139"> [readonly](../../../csharp/language-reference/keywords/readonly.md) </span><span class="sxs-lookup"><span data-stu-id="c27c0-139"> [readonly](../../../csharp/language-reference/keywords/readonly.md) </span></span>  
<span data-ttu-id="c27c0-140"> [Immutability in C# Part One: Kinds of Immutability](http://go.microsoft.com/fwlink/?LinkId=112379) (C# 中不變性第一部分：不變性類型)</span><span class="sxs-lookup"><span data-stu-id="c27c0-140"> [Immutability in C# Part One: Kinds of Immutability](http://go.microsoft.com/fwlink/?LinkId=112379)</span></span>
