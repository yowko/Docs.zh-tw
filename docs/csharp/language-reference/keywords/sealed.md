---
title: sealed 修飾詞 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 7b9551fe892b0335fb445ab9edce4facca0badbe
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833340"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="6eee0-102">sealed (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6eee0-102">sealed (C# Reference)</span></span>

<span data-ttu-id="6eee0-103">套用至類別時，`sealed` 修飾詞可防止其他類別繼承自它。</span><span class="sxs-lookup"><span data-stu-id="6eee0-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="6eee0-104">在下列範例中，`B` 類別繼承自 `A`類別，但類別無法繼承自 `B` 類別。</span><span class="sxs-lookup"><span data-stu-id="6eee0-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>

```csharp
class A {}
sealed class B : A {}
```

<span data-ttu-id="6eee0-105">您也可以在方法或屬性上使用可覆寫基底類別中虛擬方法或屬性的 `sealed` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="6eee0-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="6eee0-106">這可讓您允許類別衍生自您的類別，並防止它們覆寫特定虛擬方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="6eee0-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>

## <a name="example"></a><span data-ttu-id="6eee0-107">範例</span><span class="sxs-lookup"><span data-stu-id="6eee0-107">Example</span></span>

<span data-ttu-id="6eee0-108">在下列範例中，`Z` 繼承自 `Y`，但 `Z` 無法覆寫宣告於 `X` 並密封於 `Y` 的虛擬函式 `F`。</span><span class="sxs-lookup"><span data-stu-id="6eee0-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

<span data-ttu-id="6eee0-109">當您在類別中定義新方法或屬性時，可以不將這些方法或屬性宣告為 [virtual](virtual.md)，以防止衍生類別覆寫它們。</span><span class="sxs-lookup"><span data-stu-id="6eee0-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](virtual.md).</span></span>

<span data-ttu-id="6eee0-110">搭配使用 [abstract](abstract.md) 修飾詞與 sealed 類別會產生錯誤，因為提供 abstract 方法或屬性實作的類別必須繼承 abstract 類別。</span><span class="sxs-lookup"><span data-stu-id="6eee0-110">It is an error to use the [abstract](abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>

<span data-ttu-id="6eee0-111">套用至方法或屬性時，`sealed` 修飾詞必須一律與 [override](override.md) 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="6eee0-111">When applied to a method or property, the `sealed` modifier must always be used with [override](override.md).</span></span>

<span data-ttu-id="6eee0-112">結構會隱含地進行密封，因此無法進行繼承。</span><span class="sxs-lookup"><span data-stu-id="6eee0-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>

<span data-ttu-id="6eee0-113">如需詳細資訊，請參閱[繼承](../../programming-guide/classes-and-structs/inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="6eee0-113">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="6eee0-114">如需更多範例，請參閱[抽象和密封類別以及類別成員](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="6eee0-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="6eee0-115">範例</span><span class="sxs-lookup"><span data-stu-id="6eee0-115">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

<span data-ttu-id="6eee0-116">在上述範例中，您可以嘗試使用下列陳述式從 sealed 類別繼承︰</span><span class="sxs-lookup"><span data-stu-id="6eee0-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>

`class MyDerivedC: SealedClass {}   // Error`

<span data-ttu-id="6eee0-117">結果是錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="6eee0-117">The result is an error message:</span></span>

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a><span data-ttu-id="6eee0-118">備註</span><span class="sxs-lookup"><span data-stu-id="6eee0-118">Remarks</span></span>

<span data-ttu-id="6eee0-119">若要判斷是否密封類別、方法或屬性，您通常應該考慮下列兩點︰</span><span class="sxs-lookup"><span data-stu-id="6eee0-119">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>

- <span data-ttu-id="6eee0-120">衍生類別的潛在優點可能是透過類別自訂功能所取得。</span><span class="sxs-lookup"><span data-stu-id="6eee0-120">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>

- <span data-ttu-id="6eee0-121">衍生類別可能會修改您的類別，因此它們無法再正確運作或如預期運作。</span><span class="sxs-lookup"><span data-stu-id="6eee0-121">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6eee0-122">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="6eee0-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6eee0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6eee0-123">See also</span></span>

- [<span data-ttu-id="6eee0-124">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6eee0-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6eee0-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6eee0-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6eee0-126">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="6eee0-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6eee0-127">靜態類別和靜態類別成員</span><span class="sxs-lookup"><span data-stu-id="6eee0-127">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="6eee0-128">抽象和密封類別以及類別成員</span><span class="sxs-lookup"><span data-stu-id="6eee0-128">Abstract and Sealed Classes and Class Members</span></span>](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="6eee0-129">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="6eee0-129">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="6eee0-130">修飾詞</span><span class="sxs-lookup"><span data-stu-id="6eee0-130">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="6eee0-131">override</span><span class="sxs-lookup"><span data-stu-id="6eee0-131">override</span></span>](override.md)
- [<span data-ttu-id="6eee0-132">virtual</span><span class="sxs-lookup"><span data-stu-id="6eee0-132">virtual</span></span>](virtual.md)
