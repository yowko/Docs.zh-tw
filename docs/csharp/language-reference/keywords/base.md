---
title: base 關鍵字 - C# 參考
description: 了解 base 關鍵字，該關鍵字可用來存取 C# 衍生類別中基底類別的成員。
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: a4686fc5d4245a50de5d77dc0e71c231772f40ef
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713774"
---
# <a name="base-c-reference"></a><span data-ttu-id="7e107-103">base (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="7e107-103">base (C# Reference)</span></span>

<span data-ttu-id="7e107-104">`base` 關鍵字是用來存取衍生類別中基底類別的成員︰</span><span class="sxs-lookup"><span data-stu-id="7e107-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="7e107-105">對已由另一個方法覆寫的基底類別來呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="7e107-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="7e107-106">指定應該在建立衍生類別的執行個體時呼叫的基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="7e107-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="7e107-107">僅允許在建構函式、執行個體方法或執行個體屬性存取子中進行基底類別存取。</span><span class="sxs-lookup"><span data-stu-id="7e107-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="7e107-108">從靜態方法使用 `base` 關鍵字是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="7e107-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="7e107-109">所存取的基底類別是類別宣告中所指定的基底類別。</span><span class="sxs-lookup"><span data-stu-id="7e107-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="7e107-110">例如，如果您指定 `class ClassB : ClassA`，則不論 ClassA 的基底類別為何，都會從 ClassB 存取 ClassA 成員。</span><span class="sxs-lookup"><span data-stu-id="7e107-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="7e107-111">範例</span><span class="sxs-lookup"><span data-stu-id="7e107-111">Example</span></span>

<span data-ttu-id="7e107-112">在此範例中，基底類別 `Person` 和衍生類別 `Employee` 都會有名為 `Getinfo` 的方法。</span><span class="sxs-lookup"><span data-stu-id="7e107-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="7e107-113">使用 `base` 關鍵字，即可從衍生類別對基底類別呼叫 `Getinfo` 方法。</span><span class="sxs-lookup"><span data-stu-id="7e107-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="7e107-114">如需其他範例，請參閱 [new](new-modifier.md)、[virtual](virtual.md) 和 [override](override.md)。</span><span class="sxs-lookup"><span data-stu-id="7e107-114">For additional examples, see [new](new-modifier.md), [virtual](virtual.md), and [override](override.md).</span></span>

## <a name="example"></a><span data-ttu-id="7e107-115">範例</span><span class="sxs-lookup"><span data-stu-id="7e107-115">Example</span></span>

<span data-ttu-id="7e107-116">這個範例示範如何指定在建立衍生類別的執行個體時呼叫的基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="7e107-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="7e107-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="7e107-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7e107-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="7e107-118">See also</span></span>

- [<span data-ttu-id="7e107-119">C# 參考</span><span class="sxs-lookup"><span data-stu-id="7e107-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7e107-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7e107-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7e107-121">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="7e107-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="7e107-122">this</span><span class="sxs-lookup"><span data-stu-id="7e107-122">this</span></span>](./this.md)
