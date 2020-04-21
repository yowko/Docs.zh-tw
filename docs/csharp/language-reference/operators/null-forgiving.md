---
title: '! (空寬恕) 運算子 - C# 參考'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: a8b47e83ce9e999ea2afe94db0a21725abc2d327
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738579"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="6fef5-103">!</span><span class="sxs-lookup"><span data-stu-id="6fef5-103">!</span></span> <span data-ttu-id="6fef5-104">(空寬恕) 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6fef5-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="6fef5-105">在 C# 8.0 及更高版本中`!`提供,未修復後運算符是空寬恕運算符。</span><span class="sxs-lookup"><span data-stu-id="6fef5-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="6fef5-106">開啟[的空註解中](../../nullable-references.md#nullable-annotation-context), 使用 null 寬容運算符宣告的表示式`x`不是`null`: `x!`。</span><span class="sxs-lookup"><span data-stu-id="6fef5-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="6fef5-107">一元前置字`!`元是[邏輯否定運算子](boolean-logical-operators.md#logical-negation-operator-)。</span><span class="sxs-lookup"><span data-stu-id="6fef5-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="6fef5-108">放棄運算符在運行時不起作用。</span><span class="sxs-lookup"><span data-stu-id="6fef5-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="6fef5-109">它僅透過更改表達式的 null 狀態來影響編譯器的靜態流分析。</span><span class="sxs-lookup"><span data-stu-id="6fef5-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="6fef5-110">在運行時,表達式`x!`計算到基礎表達`x`式 的結果。</span><span class="sxs-lookup"><span data-stu-id="6fef5-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="6fef5-111">有關可空引用類型功能的詳細資訊,請參考[空參考類型](../builtin-types/nullable-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="6fef5-111">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="6fef5-112">範例</span><span class="sxs-lookup"><span data-stu-id="6fef5-112">Examples</span></span>

<span data-ttu-id="6fef5-113">null 寬容運算子的一個用例是測試參數驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="6fef5-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="6fef5-114">例如，請參考下列類別：</span><span class="sxs-lookup"><span data-stu-id="6fef5-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="6fef5-115">使用[MSTest 測試框架](../../../core/testing/unit-testing-with-mstest.md),可以為建構函式中的驗證邏輯建立以下測試:</span><span class="sxs-lookup"><span data-stu-id="6fef5-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="6fef5-116">如果沒有 null 寬容運算子,編譯器將產生上述代碼的以下警告: `Warning CS8625: Cannot convert null literal to non-nullable reference type`。</span><span class="sxs-lookup"><span data-stu-id="6fef5-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="6fef5-117">通過使用 null 寬容運算符,您可以通知編譯器傳遞`null`是預期的,不應被警告。</span><span class="sxs-lookup"><span data-stu-id="6fef5-117">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="6fef5-118">當您肯定知道表示式不能,`null`但編譯器無法識別這一點時,也可以使用 null 寬容運算符。</span><span class="sxs-lookup"><span data-stu-id="6fef5-118">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="6fef5-119">在下面的範例中,如果`IsValid`方法傳`true`回 ,則其`null`參數不是 ,您可以安全地取消引用它:</span><span class="sxs-lookup"><span data-stu-id="6fef5-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="6fef5-120">如果沒有允許的 null 運算子,編譯器將產生`p.Name`以下 代碼`Warning CS8602: Dereference of a possibly null reference`警告: 。</span><span class="sxs-lookup"><span data-stu-id="6fef5-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="6fef5-121">如果可以修改方法,`IsValid`則可以使用[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)屬性通知編譯`IsValid`器,`null``true`當方法傳回 時,該方法的參數不能是 :</span><span class="sxs-lookup"><span data-stu-id="6fef5-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="6fef5-122">在前面的範例中,不需要使用 null 寬容運算符,因為編譯器有足夠的資訊來找出`p`語句`null``if`中 不能包含的資訊。</span><span class="sxs-lookup"><span data-stu-id="6fef5-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="6fef5-123">有關允許您提供有關變數的 null 狀態的其他資訊的屬性的詳細資訊,請參閱[使用屬性升級 API 以定義 null 期望值](../../nullable-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="6fef5-123">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6fef5-124">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="6fef5-124">C# language specification</span></span>

<span data-ttu-id="6fef5-125">有關詳細資訊,請參閱[空引用類型規範草案](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)的[null 寬容運算元](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator)部分。</span><span class="sxs-lookup"><span data-stu-id="6fef5-125">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6fef5-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fef5-126">See also</span></span>

- [<span data-ttu-id="6fef5-127">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6fef5-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6fef5-128">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="6fef5-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="6fef5-129">教學:具有空引言類型的設計</span><span class="sxs-lookup"><span data-stu-id="6fef5-129">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
