---
title: 隱含類型陣列 - C# 程式設計手冊
description: 'C # 中的隱含型別陣列型別是從陣列初始化運算式中的元素推斷而來。 在查詢運算式中使用隱含類型陣列。'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 1f14f68207dfb79c92eaa01ac2a8ffaa08facc03
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474705"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="3a811-104">隱含類型陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="3a811-104">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="3a811-105">您可以建立隱含型別陣列，其中陣列執行個體的類型是從陣列初始設定式中所指定的項目推斷而來。</span><span class="sxs-lookup"><span data-stu-id="3a811-105">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="3a811-106">任何隱含型別變數的規則也適用於隱含型別陣列。</span><span class="sxs-lookup"><span data-stu-id="3a811-106">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="3a811-107">如需詳細資訊，請參閱[隱含型別區域變數](../classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="3a811-107">For more information, see [Implicitly Typed Local Variables](../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="3a811-108">隱含型別的陣列以及匿名型別與物件和集合初始設定式通常用於查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="3a811-108">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="3a811-109">下列範例示範如何建立隱含型別陣列：</span><span class="sxs-lookup"><span data-stu-id="3a811-109">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="3a811-110">在上述範例中，請注意，使用隱含型別陣列時，在初始化陳述式左邊未使用方括弧。</span><span class="sxs-lookup"><span data-stu-id="3a811-110">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="3a811-111">也請注意不規則陣列是使用 `new []` 進行初始化，就像一維陣列一樣。</span><span class="sxs-lookup"><span data-stu-id="3a811-111">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="3a811-112">物件初始設定式中的隱含型別陣列</span><span class="sxs-lookup"><span data-stu-id="3a811-112">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="3a811-113">當您建立包含陣列的匿名型別時，在類型的物件初始設定式中，陣列必須是隱含型別。</span><span class="sxs-lookup"><span data-stu-id="3a811-113">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="3a811-114">在下列範例中，`contacts` 是隱含型別的匿名型別陣列，且每個都會包含名為 `PhoneNumbers` 的陣列。</span><span class="sxs-lookup"><span data-stu-id="3a811-114">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="3a811-115">請注意，`var` 關鍵字未用於物件初始設定式內。</span><span class="sxs-lookup"><span data-stu-id="3a811-115">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="3a811-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a811-116">See also</span></span>

- [<span data-ttu-id="3a811-117">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3a811-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3a811-118">隱含類型區域變數</span><span class="sxs-lookup"><span data-stu-id="3a811-118">Implicitly Typed Local Variables</span></span>](../classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="3a811-119">陣列</span><span class="sxs-lookup"><span data-stu-id="3a811-119">Arrays</span></span>](./index.md)
- [<span data-ttu-id="3a811-120">匿名類型</span><span class="sxs-lookup"><span data-stu-id="3a811-120">Anonymous Types</span></span>](../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="3a811-121">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="3a811-121">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="3a811-122">var</span><span class="sxs-lookup"><span data-stu-id="3a811-122">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="3a811-123">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="3a811-123">LINQ in C#</span></span>](../../linq/index.md)
