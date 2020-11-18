---
description: '!  (null 容許) 運算子-c # 參考'
title: '!  (null 容許) 運算子-c # 參考'
ms.date: 10/11/2019
f1_keywords:
- nullForgiving_CSharpKeyword
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: f2eb57bba462d471a041c17024fa7031c2c7f87d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830580"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="f2799-105">!</span><span class="sxs-lookup"><span data-stu-id="f2799-105">!</span></span> <span data-ttu-id="f2799-106"> (null 容許) 運算子 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="f2799-106">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="f2799-107">在 c # 8.0 和更新版本中提供，一元 `!` 後置運算子是 null 容許運算子。</span><span class="sxs-lookup"><span data-stu-id="f2799-107">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="f2799-108">在啟用的 [可為 null 注釋內容](../../nullable-references.md#nullable-annotation-context)中，您可以使用 null 容許運算子來宣告 `x` 參考型別的運算式不是 `null` ： `x!` 。</span><span class="sxs-lookup"><span data-stu-id="f2799-108">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="f2799-109">一元前置 `!` 運算子是 [邏輯負運算子](boolean-logical-operators.md#logical-negation-operator-)。</span><span class="sxs-lookup"><span data-stu-id="f2799-109">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="f2799-110">Null 容許運算子在執行時間不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="f2799-110">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="f2799-111">它只會變更運算式的 null 狀態，以影響編譯器的靜態流程分析。</span><span class="sxs-lookup"><span data-stu-id="f2799-111">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="f2799-112">在執行時間，運算式會 `x!` 評估為基礎運算式的結果 `x` 。</span><span class="sxs-lookup"><span data-stu-id="f2799-112">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

> [!NOTE]
> <span data-ttu-id="f2799-113">在 c # 8 中，null 容許運算子會終止先前的 [null 條件式](member-access-operators.md#null-conditional-operators--and-) 作業清單。</span><span class="sxs-lookup"><span data-stu-id="f2799-113">In C# 8, the null-forgiving operator terminates the list of preceding [null-conditional](member-access-operators.md#null-conditional-operators--and-) operations.</span></span> <span data-ttu-id="f2799-114">例如，運算式會剖析 `x?.y!.z` 為 `(x?.y)!.z` 。</span><span class="sxs-lookup"><span data-stu-id="f2799-114">For example, the expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="f2799-115">由於這種轉譯的緣故， `z` 即使 `x` 為，也會進行評估 `null` ，這樣可能會導致 <xref:System.NullReferenceException> 。</span><span class="sxs-lookup"><span data-stu-id="f2799-115">Due to this interpretation, `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="f2799-116">如需可為 null 的參考型別功能的詳細資訊，請參閱 [可為 null 的參考](../builtin-types/nullable-reference-types.md)型別。</span><span class="sxs-lookup"><span data-stu-id="f2799-116">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="f2799-117">範例</span><span class="sxs-lookup"><span data-stu-id="f2799-117">Examples</span></span>

<span data-ttu-id="f2799-118">Null 容許運算子的其中一個使用案例是測試引數驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="f2799-118">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="f2799-119">例如，請參考下列類別：</span><span class="sxs-lookup"><span data-stu-id="f2799-119">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="f2799-120">您可以使用 [MSTest 測試架構](../../../core/testing/unit-testing-with-mstest.md)，在函式中針對驗證邏輯建立下列測試：</span><span class="sxs-lookup"><span data-stu-id="f2799-120">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="f2799-121">如果沒有容許運算子，編譯器會針對上述程式碼產生下列警告： `Warning CS8625: Cannot convert null literal to non-nullable reference type` 。</span><span class="sxs-lookup"><span data-stu-id="f2799-121">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="f2799-122">藉由使用 null 容許運算子，您會通知編譯器必須傳遞 `null` ，且不應該收到警告。</span><span class="sxs-lookup"><span data-stu-id="f2799-122">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="f2799-123">當您確定運算式不能是， `null` 但編譯器無法管理來辨識該運算式時，您也可以使用 null 容許運算子。</span><span class="sxs-lookup"><span data-stu-id="f2799-123">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="f2799-124">在下列範例中，如果 `IsValid` 方法傳回 `true` ，則其引數不是， `null` 而且您可以安全地取值：</span><span class="sxs-lookup"><span data-stu-id="f2799-124">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="f2799-125">如果沒有容許運算子，編譯器會為程式碼產生下列警告 `p.Name` ： `Warning CS8602: Dereference of a possibly null reference` 。</span><span class="sxs-lookup"><span data-stu-id="f2799-125">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="f2799-126">如果您可以修改 `IsValid` 方法，則可以使用 [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) 屬性來通知編譯器，方法的引數 `IsValid` 不能是方法傳回時的參數 `null` `true` ：</span><span class="sxs-lookup"><span data-stu-id="f2799-126">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="f2799-127">在上述範例中，您不需要使用 null 容許運算子，因為編譯器有足夠的資訊可以找出 `p` 不能在 `null` 語句內的資訊 `if` 。</span><span class="sxs-lookup"><span data-stu-id="f2799-127">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="f2799-128">如需可讓您提供變數 null 狀態之其他相關資訊的屬性詳細資訊，請參閱 [使用屬性升級 api 來定義 null 的預期](../attributes/nullable-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="f2799-128">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f2799-129">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f2799-129">C# language specification</span></span>

<span data-ttu-id="f2799-130">如需詳細資訊，請參閱[可為 null 之參考](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md)型別規格之草稿的[容許運算子](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator)一節。</span><span class="sxs-lookup"><span data-stu-id="f2799-130">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2799-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="f2799-131">See also</span></span>

- [<span data-ttu-id="f2799-132">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="f2799-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f2799-133">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="f2799-133">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="f2799-134">教學課程：使用可為 null 的參考型別設計</span><span class="sxs-lookup"><span data-stu-id="f2799-134">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
