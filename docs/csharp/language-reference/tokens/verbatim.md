---
title: '@ - C# 參考'
ms.custom: seodec18
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2290c87f7d4d2ba8da122d4f5ddb9ea423852ec
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608729"
---
# <a name="-c-reference"></a><span data-ttu-id="faaa3-102">@ (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="faaa3-102">@ (C# Reference)</span></span>

<span data-ttu-id="faaa3-103">`@` 特殊字元可用為逐字識別項。</span><span class="sxs-lookup"><span data-stu-id="faaa3-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="faaa3-104">使用方式如下：</span><span class="sxs-lookup"><span data-stu-id="faaa3-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="faaa3-105">讓 C# 關鍵字用為識別項。</span><span class="sxs-lookup"><span data-stu-id="faaa3-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="faaa3-106">`@` 字元將程式碼元素當成前置詞，編譯器要將此元素解譯為識別項，不是 C# 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="faaa3-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="faaa3-107">下例會使用 `@` 字元來定義名為 `for` 的識別項，它會用在 `for` 迴圈中。</span><span class="sxs-lookup"><span data-stu-id="faaa3-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="faaa3-108">表示要逐字解譯字串常值。</span><span class="sxs-lookup"><span data-stu-id="faaa3-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="faaa3-109">這個執行個體中的 `@` 字元會定義「逐字字串常值」  。</span><span class="sxs-lookup"><span data-stu-id="faaa3-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="faaa3-110">簡單逸出序列 (例如 `"\\"` 用於反斜線)、十六進位逸出序列 (例如 `"\x0041"` 用於大寫 A)，以及 Unicode 逸出序列 (例如 `"\u0041"` 用於大寫 A) 都是照字面解譯。</span><span class="sxs-lookup"><span data-stu-id="faaa3-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="faaa3-111">只有引號逸出序列 (`""`) 不照字面解譯，它會產生單引號。</span><span class="sxs-lookup"><span data-stu-id="faaa3-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="faaa3-112">此外，如果是逐字[插入字串](interpolated.md)，大括弧逸出序列 (`{{` 和 `}}`) 不會照字面意義解譯，它們會產生一個大括弧字元。</span><span class="sxs-lookup"><span data-stu-id="faaa3-112">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="faaa3-113">下例會定義兩個相同的檔案路徑，一個使用規則字串常值，另一個使用逐字字串常值。</span><span class="sxs-lookup"><span data-stu-id="faaa3-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="faaa3-114">這是逐字字串常值較常見的用法之一。</span><span class="sxs-lookup"><span data-stu-id="faaa3-114">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="faaa3-115">下例示範定義包含相同字元序列的規則字串常值和逐字字串常值的效果。</span><span class="sxs-lookup"><span data-stu-id="faaa3-115">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="faaa3-116">如果發生命名衝突，讓編譯器區別屬性。</span><span class="sxs-lookup"><span data-stu-id="faaa3-116">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="faaa3-117">屬性是衍生自 <xref:System.Attribute> 的類別。</span><span class="sxs-lookup"><span data-stu-id="faaa3-117">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="faaa3-118">其型別名稱通常包含尾碼 **Attribute**，雖然編譯器不會強制執行此慣例。</span><span class="sxs-lookup"><span data-stu-id="faaa3-118">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="faaa3-119">然後，在程式碼中就可以依其完整型別名稱 (例如 `[InfoAttribute]`) 或簡短名稱 (例如 `[Info]`) 參考屬性。</span><span class="sxs-lookup"><span data-stu-id="faaa3-119">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="faaa3-120">不過，如果兩個簡短的屬性型別名稱完全相同，但一個型別名稱有 **Attribute** 尾碼，一個沒有，即會發生命名衝突。</span><span class="sxs-lookup"><span data-stu-id="faaa3-120">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="faaa3-121">例如，下列程式碼無法編譯，因為編譯器無法判斷是否已對 `Example` 類別套用了 `Info` 或 `InfoAttribute` 屬性。</span><span class="sxs-lookup"><span data-stu-id="faaa3-121">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="faaa3-122">請參閱 [CS1614](../compiler-messages/cs1614.md) 以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="faaa3-122">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="faaa3-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="faaa3-123">See also</span></span>

- [<span data-ttu-id="faaa3-124">C# 參考</span><span class="sxs-lookup"><span data-stu-id="faaa3-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="faaa3-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="faaa3-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="faaa3-126">C# 特殊字元</span><span class="sxs-lookup"><span data-stu-id="faaa3-126">C# Special Characters</span></span>](./index.md)
