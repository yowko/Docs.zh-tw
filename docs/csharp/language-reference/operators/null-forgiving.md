---
title: '! （null-容許）運算子- C# reference'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: cf941e5e3fa3fc6313ef8b2ff5c176aec68c1e6b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291722"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="9e3e0-103">!</span><span class="sxs-lookup"><span data-stu-id="9e3e0-103">!</span></span> <span data-ttu-id="9e3e0-104">（null-容許）運算子（C#參考）</span><span class="sxs-lookup"><span data-stu-id="9e3e0-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="9e3e0-105">可在C# 8.0 和更新版本中使用，一元後置 `!` 運算子是 null 容許運算子。</span><span class="sxs-lookup"><span data-stu-id="9e3e0-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="9e3e0-106">在啟用的[可為 null 注釋內容](../../nullable-references.md#nullable-annotation-context)中，您可以使用 null 容許運算子來宣告參考型別的運算式 `x` 不是 null： `x!`。</span><span class="sxs-lookup"><span data-stu-id="9e3e0-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't null: `x!`.</span></span> <span data-ttu-id="9e3e0-107">一元前置字元 `!` 運算子是[邏輯負運算子](boolean-logical-operators.md#logical-negation-operator-)。</span><span class="sxs-lookup"><span data-stu-id="9e3e0-107">The unary prefix `!` operator is a [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="9e3e0-108">Null 容許運算子在執行時間沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="9e3e0-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="9e3e0-109">它只會影響編譯器的靜態流程分析，方法是變更運算式的 null 狀態。</span><span class="sxs-lookup"><span data-stu-id="9e3e0-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="9e3e0-110">在執行時間，expression `x!` 會評估為基礎運算式 `x` 的結果。</span><span class="sxs-lookup"><span data-stu-id="9e3e0-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="9e3e0-111">如需可為 null 的參考型別功能的詳細資訊，請參閱[可為 null 的參考型別](../../nullable-references.md)。</span><span class="sxs-lookup"><span data-stu-id="9e3e0-111">For more information about the nullable reference types feature, see [Nullable reference types](../../nullable-references.md).</span></span>

## <a name="examples"></a><span data-ttu-id="9e3e0-112">範例</span><span class="sxs-lookup"><span data-stu-id="9e3e0-112">Examples</span></span>

<span data-ttu-id="9e3e0-113">Null 容許運算子的其中一個使用案例是測試引數驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="9e3e0-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="9e3e0-114">例如，請參考下列類別：</span><span class="sxs-lookup"><span data-stu-id="9e3e0-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="9e3e0-115">使用[MSTest 測試架構](../../../core/testing/unit-testing-with-mstest.md)，您可以在函式中針對驗證邏輯建立下列測試：</span><span class="sxs-lookup"><span data-stu-id="9e3e0-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="9e3e0-116">如果沒有 null 容許運算子，編譯器會針對上述程式碼產生下列警告： `Warning CS8625: Cannot convert null literal to non-nullable reference type`。</span><span class="sxs-lookup"><span data-stu-id="9e3e0-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="9e3e0-117">使用 null 容許運算子時，您可以讓編譯器知道預期傳遞 `null`，而不應該收到關於的警告。</span><span class="sxs-lookup"><span data-stu-id="9e3e0-117">With the use of the null-forgiving operator, you let the compiler know that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="9e3e0-118">當您肯定知道運算式不能 `null`，但編譯器不會管理來辨識這一點時，您也可以使用 null 容許運算子。</span><span class="sxs-lookup"><span data-stu-id="9e3e0-118">You also can use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="9e3e0-119">在下列範例中，如果 `IsValid` 方法傳回 `true`，其引數不會 `null`，而您可以安全地進行取值：</span><span class="sxs-lookup"><span data-stu-id="9e3e0-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="9e3e0-120">如果沒有 null 容許運算子，編譯器會為 `p.Name` 程式碼產生下列警告： `Warning CS8602: Dereference of a possibly null reference.`。</span><span class="sxs-lookup"><span data-stu-id="9e3e0-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference.`.</span></span>

<span data-ttu-id="9e3e0-121">如果您可以修改 `IsValid` 方法，您可以使用[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)屬性，讓編譯器知道當方法傳回 `true` 時，@no__t 2 方法的引數不能 `null`：</span><span class="sxs-lookup"><span data-stu-id="9e3e0-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to let the compiler know that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="9e3e0-122">在上述範例中，您不需要使用 null-容許運算子，因為編譯器有足夠的資訊可發現 `p` 不能在 `if` 語句內 `null`。</span><span class="sxs-lookup"><span data-stu-id="9e3e0-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="9e3e0-123">如需可讓您指定變數之 null 狀態的其他資訊之屬性的詳細資訊，請參閱[使用屬性升級 api 以定義 null 預期](../../nullable-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="9e3e0-123">For more information about the attributes that allow you to specify additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9e3e0-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e3e0-124">See also</span></span>

- [<span data-ttu-id="9e3e0-125">C# 參考</span><span class="sxs-lookup"><span data-stu-id="9e3e0-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9e3e0-126">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="9e3e0-126">C# operators</span></span>](index.md)
- <span data-ttu-id="9e3e0-127">[教學課程：以可為 null 的參考型別設計 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="9e3e0-127">[Tutorial: Design with nullable reference types](../../tutorials/nullable-reference-types.md)</span></span>
