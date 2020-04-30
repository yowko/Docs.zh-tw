---
title: '! （null-容許）運算子-c # 參考'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 772f37f1fc7446eae66f0cd0f12adb5e2e41997d
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595945"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="c261b-103">!</span><span class="sxs-lookup"><span data-stu-id="c261b-103">!</span></span> <span data-ttu-id="c261b-104">（null-容許）運算子（c # 參考）</span><span class="sxs-lookup"><span data-stu-id="c261b-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="c261b-105">適用于 c # 8.0 和更新版本，一元`!`後置運算子是 null 容許運算子。</span><span class="sxs-lookup"><span data-stu-id="c261b-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="c261b-106">在啟用的[可為 null 注釋內容](../../nullable-references.md#nullable-annotation-context)中，您可以使用 null 容許運算子來宣告`x`參考型別的運算式不`null`是`x!`：。</span><span class="sxs-lookup"><span data-stu-id="c261b-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="c261b-107">一元前置`!`運算子是[邏輯負運算子](boolean-logical-operators.md#logical-negation-operator-)。</span><span class="sxs-lookup"><span data-stu-id="c261b-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="c261b-108">Null 容許運算子在執行時間沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="c261b-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="c261b-109">它只會影響編譯器的靜態流程分析，方法是變更運算式的 null 狀態。</span><span class="sxs-lookup"><span data-stu-id="c261b-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="c261b-110">在執行時間，expression `x!`會評估為基礎運算式`x`的結果。</span><span class="sxs-lookup"><span data-stu-id="c261b-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

> [!NOTE]
> <span data-ttu-id="c261b-111">在 c # 8 中，null 容許運算子會以非預期的方式與[null 條件運算子](member-access-operators.md#null-conditional-operators--and-)互動。</span><span class="sxs-lookup"><span data-stu-id="c261b-111">In C# 8 the null-forgiving operator interacts with the [null-conditional operators](member-access-operators.md#null-conditional-operators--and-) in an unexpected way.</span></span> <span data-ttu-id="c261b-112">運算式`x?.y!.z`會剖析為`(x?.y)!.z`。</span><span class="sxs-lookup"><span data-stu-id="c261b-112">The expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="c261b-113">由於這項轉譯`z`會進行評估， `x`即使`null`為，這可能會導致<xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="c261b-113">Due to this interpretation `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="c261b-114">如需可為 null 的參考型別功能的詳細資訊，請參閱[可為 null 的參考型別](../builtin-types/nullable-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c261b-114">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="c261b-115">範例</span><span class="sxs-lookup"><span data-stu-id="c261b-115">Examples</span></span>

<span data-ttu-id="c261b-116">Null 容許運算子的其中一個使用案例是測試引數驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="c261b-116">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="c261b-117">例如，請參考下列類別：</span><span class="sxs-lookup"><span data-stu-id="c261b-117">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="c261b-118">使用[MSTest 測試架構](../../../core/testing/unit-testing-with-mstest.md)，您可以在函式中針對驗證邏輯建立下列測試：</span><span class="sxs-lookup"><span data-stu-id="c261b-118">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="c261b-119">如果沒有 null 容許運算子，編譯器會針對上述程式碼產生下列警告： `Warning CS8625: Cannot convert null literal to non-nullable reference type`。</span><span class="sxs-lookup"><span data-stu-id="c261b-119">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="c261b-120">藉由使用 null 容許運算子，您可以通知編譯器預期傳遞`null` ，而不應該收到關於的警告。</span><span class="sxs-lookup"><span data-stu-id="c261b-120">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="c261b-121">當您肯定知道運算式不能是`null` ，但編譯器不會管理來辨識這種情況時，也可以使用 null 容許運算子。</span><span class="sxs-lookup"><span data-stu-id="c261b-121">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="c261b-122">在下列範例中，如果`IsValid`方法傳回`true`，則其引數不`null`是，而且您可以安全地進行取值：</span><span class="sxs-lookup"><span data-stu-id="c261b-122">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="c261b-123">如果沒有 null 容許運算子，編譯器會為程式`p.Name`代碼產生下列警告：。 `Warning CS8602: Dereference of a possibly null reference`</span><span class="sxs-lookup"><span data-stu-id="c261b-123">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="c261b-124">如果您可以`IsValid`修改方法，您可以使用[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)屬性來通知編譯器，當方法傳回時， `IsValid`方法的引數不`null`能是`true`：</span><span class="sxs-lookup"><span data-stu-id="c261b-124">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="c261b-125">在上述範例中，您不需要使用 null 容許運算子，因為編譯器有足夠的資訊可以找出不在`p` `null` `if`語句內的。</span><span class="sxs-lookup"><span data-stu-id="c261b-125">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="c261b-126">如需可讓您提供變數 null 狀態之其他相關資訊的屬性詳細資訊，請參閱[使用屬性升級 api 以定義 null 預期](../attributes/nullable-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="c261b-126">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c261b-127">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c261b-127">C# language specification</span></span>

<span data-ttu-id="c261b-128">如需詳細資訊，請參閱[可為 null 的參考型別規格之草稿](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)的[null-容許運算子](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator)一節。</span><span class="sxs-lookup"><span data-stu-id="c261b-128">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c261b-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c261b-129">See also</span></span>

- [<span data-ttu-id="c261b-130">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c261b-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c261b-131">C # 運算子</span><span class="sxs-lookup"><span data-stu-id="c261b-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="c261b-132">教學課程：使用可為 null 的參考型別進行設計</span><span class="sxs-lookup"><span data-stu-id="c261b-132">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
