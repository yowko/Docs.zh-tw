---
title: base 關鍵字 (C# 參考)
description: 了解 base 關鍵字，該關鍵字可用來存取 C# 衍生類別中基底類別的成員。
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 8719ab79273701173530760ad1bec837c4f4302d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45648417"
---
# <a name="base-c-reference"></a><span data-ttu-id="910d7-103">base (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="910d7-103">base (C# Reference)</span></span>

<span data-ttu-id="910d7-104">`base` 關鍵字是用來存取衍生類別中基底類別的成員︰</span><span class="sxs-lookup"><span data-stu-id="910d7-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="910d7-105">對已由另一個方法覆寫的基底類別來呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="910d7-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="910d7-106">指定應該在建立衍生類別的執行個體時呼叫的基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="910d7-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="910d7-107">僅允許在建構函式、執行個體方法或執行個體屬性存取子中進行基底類別存取。</span><span class="sxs-lookup"><span data-stu-id="910d7-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="910d7-108">從靜態方法使用 `base` 關鍵字是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="910d7-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="910d7-109">所存取的基底類別是類別宣告中所指定的基底類別。</span><span class="sxs-lookup"><span data-stu-id="910d7-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="910d7-110">例如，如果您指定 `class ClassB : ClassA`，則不論 ClassA 的基底類別為何，都會從 ClassB 存取 ClassA 成員。</span><span class="sxs-lookup"><span data-stu-id="910d7-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="910d7-111">範例</span><span class="sxs-lookup"><span data-stu-id="910d7-111">Example</span></span>

<span data-ttu-id="910d7-112">在此範例中，基底類別 `Person` 和衍生類別 `Employee` 都會有名為 `Getinfo` 的方法。</span><span class="sxs-lookup"><span data-stu-id="910d7-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="910d7-113">使用 `base` 關鍵字，即可從衍生類別對基底類別呼叫 `Getinfo` 方法。</span><span class="sxs-lookup"><span data-stu-id="910d7-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="910d7-114">如需其他範例，請參閱 [new](../../../csharp/language-reference/keywords/new.md)、[virtual](../../../csharp/language-reference/keywords/virtual.md) 和 [override](../../../csharp/language-reference/keywords/override.md)。</span><span class="sxs-lookup"><span data-stu-id="910d7-114">For additional examples, see [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md), and [override](../../../csharp/language-reference/keywords/override.md).</span></span>

## <a name="example"></a><span data-ttu-id="910d7-115">範例</span><span class="sxs-lookup"><span data-stu-id="910d7-115">Example</span></span>

<span data-ttu-id="910d7-116">這個範例示範如何指定在建立衍生類別的執行個體時呼叫的基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="910d7-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="910d7-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="910d7-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="910d7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="910d7-118">See also</span></span>

- [<span data-ttu-id="910d7-119">C# 參考</span><span class="sxs-lookup"><span data-stu-id="910d7-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="910d7-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="910d7-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="910d7-121">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="910d7-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="910d7-122">this</span><span class="sxs-lookup"><span data-stu-id="910d7-122">this</span></span>](../../../csharp/language-reference/keywords/this.md)