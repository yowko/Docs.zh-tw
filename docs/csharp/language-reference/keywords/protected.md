---
description: protected 關鍵字 - C# 參考
title: protected 關鍵字 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: d8d9a75bb5e07816adaa8d09c96cee8a240130fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688909"
---
# <a name="protected-c-reference"></a><span data-ttu-id="2dd6c-103">protected (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2dd6c-103">protected (C# Reference)</span></span>

<span data-ttu-id="2dd6c-104">`protected` 關鍵字是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="2dd6c-104">The `protected` keyword is a member access modifier.</span></span>

> [!NOTE]
> <span data-ttu-id="2dd6c-105">此頁面涵蓋 `protected` 存取。</span><span class="sxs-lookup"><span data-stu-id="2dd6c-105">This page covers `protected` access.</span></span> <span data-ttu-id="2dd6c-106">`protected`關鍵字也是和存取修飾詞的一部分 [`protected internal`](protected-internal.md) [`private protected`](private-protected.md) 。</span><span class="sxs-lookup"><span data-stu-id="2dd6c-106">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="2dd6c-107">受保護的成員可在其類別內由衍生類別執行個體存取。</span><span class="sxs-lookup"><span data-stu-id="2dd6c-107">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="2dd6c-108">如需 `protected` 和其他存取修飾詞的比較，請參閱[存取範圍層級](accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="2dd6c-108">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="2dd6c-109">範例</span><span class="sxs-lookup"><span data-stu-id="2dd6c-109">Example</span></span>

<span data-ttu-id="2dd6c-110">只有在存取是透過衍生類別類型進行時，才可以存取衍生類別中屬於基底類別的受保護成員。</span><span class="sxs-lookup"><span data-stu-id="2dd6c-110">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="2dd6c-111">例如，請考慮下列程式碼區段：</span><span class="sxs-lookup"><span data-stu-id="2dd6c-111">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="2dd6c-112">陳述式 `a.x = 10` 會產生錯誤，因為它是在靜態方法 Main 中發出，而不是在類別 B 的執行個體中發出。</span><span class="sxs-lookup"><span data-stu-id="2dd6c-112">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="2dd6c-113">結構成員不可以是受保護的成員，因為無法繼承結構。</span><span class="sxs-lookup"><span data-stu-id="2dd6c-113">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="2dd6c-114">範例</span><span class="sxs-lookup"><span data-stu-id="2dd6c-114">Example</span></span>

<span data-ttu-id="2dd6c-115">在此範例中，`DerivedPoint` 類別衍生自 `Point`。</span><span class="sxs-lookup"><span data-stu-id="2dd6c-115">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="2dd6c-116">因此，您可以直接從衍生類別存取基底類別的受保護成員。</span><span class="sxs-lookup"><span data-stu-id="2dd6c-116">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="2dd6c-117">如果您將 `x` 和 `y` 的存取層級變更為 [private](private.md)，編譯器會發出錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="2dd6c-117">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="2dd6c-118">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="2dd6c-118">C# language specification</span></span>  

<span data-ttu-id="2dd6c-119">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的[已宣告存取範圍](~/_csharplang/spec/basic-concepts.md#declared-accessibility)。</span><span class="sxs-lookup"><span data-stu-id="2dd6c-119">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="2dd6c-120">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="2dd6c-120">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="2dd6c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dd6c-121">See also</span></span>

- [<span data-ttu-id="2dd6c-122">C # 參考</span><span class="sxs-lookup"><span data-stu-id="2dd6c-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2dd6c-123">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2dd6c-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2dd6c-124">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="2dd6c-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2dd6c-125">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="2dd6c-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="2dd6c-126">協助工具層級</span><span class="sxs-lookup"><span data-stu-id="2dd6c-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="2dd6c-127">修飾詞</span><span class="sxs-lookup"><span data-stu-id="2dd6c-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="2dd6c-128">public</span><span class="sxs-lookup"><span data-stu-id="2dd6c-128">public</span></span>](public.md)
- [<span data-ttu-id="2dd6c-129">private</span><span class="sxs-lookup"><span data-stu-id="2dd6c-129">private</span></span>](private.md)
- [<span data-ttu-id="2dd6c-130">internal</span><span class="sxs-lookup"><span data-stu-id="2dd6c-130">internal</span></span>](internal.md)
- <span data-ttu-id="2dd6c-131">[internal virtual 關鍵字的安全性考量](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2dd6c-131">[Security concerns for internal virtual keywords](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
