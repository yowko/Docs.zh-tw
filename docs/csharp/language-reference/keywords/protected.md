---
title: protected 關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: f25e692430f876ec384971079d6d0aa2c97e967b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577434"
---
# <a name="protected-c-reference"></a><span data-ttu-id="dafe1-102">protected (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="dafe1-102">protected (C# Reference)</span></span>

<span data-ttu-id="dafe1-103">`protected` 關鍵字是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="dafe1-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="dafe1-104">此頁面涵蓋 `protected` 存取。</span><span class="sxs-lookup"><span data-stu-id="dafe1-104">This page covers `protected` access.</span></span> <span data-ttu-id="dafe1-105">`protected` 關鍵字也是屬於 [`protected internal`](protected-internal.md) 和 [`private protected`](private-protected.md) 存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="dafe1-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="dafe1-106">受保護的成員可在其類別內由衍生類別執行個體存取。</span><span class="sxs-lookup"><span data-stu-id="dafe1-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="dafe1-107">如需 `protected` 和其他存取修飾詞的比較，請參閱[存取範圍層級](accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="dafe1-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="dafe1-108">範例</span><span class="sxs-lookup"><span data-stu-id="dafe1-108">Example</span></span>

<span data-ttu-id="dafe1-109">只有在存取是透過衍生類別類型進行時，才可以存取衍生類別中屬於基底類別的受保護成員。</span><span class="sxs-lookup"><span data-stu-id="dafe1-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="dafe1-110">例如，請考慮下列程式碼區段：</span><span class="sxs-lookup"><span data-stu-id="dafe1-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="dafe1-111">陳述式 `a.x = 10` 會產生錯誤，因為它是在靜態方法 Main 中發出，而不是在類別 B 的執行個體中發出。</span><span class="sxs-lookup"><span data-stu-id="dafe1-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="dafe1-112">結構成員不可以是受保護的成員，因為無法繼承結構。</span><span class="sxs-lookup"><span data-stu-id="dafe1-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="dafe1-113">範例</span><span class="sxs-lookup"><span data-stu-id="dafe1-113">Example</span></span>

<span data-ttu-id="dafe1-114">在此範例中，`DerivedPoint` 類別衍生自 `Point`。</span><span class="sxs-lookup"><span data-stu-id="dafe1-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="dafe1-115">因此，您可以直接從衍生類別存取基底類別的受保護成員。</span><span class="sxs-lookup"><span data-stu-id="dafe1-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="dafe1-116">如果您將 `x` 和 `y` 的存取層級變更為 [private](private.md)，編譯器會發出錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="dafe1-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="dafe1-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="dafe1-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="dafe1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dafe1-118">See also</span></span>

- [<span data-ttu-id="dafe1-119">C# 參考</span><span class="sxs-lookup"><span data-stu-id="dafe1-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="dafe1-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="dafe1-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="dafe1-121">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="dafe1-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="dafe1-122">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="dafe1-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="dafe1-123">存取範圍層級</span><span class="sxs-lookup"><span data-stu-id="dafe1-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="dafe1-124">修飾詞</span><span class="sxs-lookup"><span data-stu-id="dafe1-124">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="dafe1-125">public</span><span class="sxs-lookup"><span data-stu-id="dafe1-125">public</span></span>](public.md)
- [<span data-ttu-id="dafe1-126">private</span><span class="sxs-lookup"><span data-stu-id="dafe1-126">private</span></span>](private.md)
- [<span data-ttu-id="dafe1-127">internal</span><span class="sxs-lookup"><span data-stu-id="dafe1-127">internal</span></span>](internal.md)
- <span data-ttu-id="dafe1-128">[internal virtual 關鍵字的安全性考量](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dafe1-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>