---
title: if-else - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- if_CSharpKeyword
- else
- else_CSharpKeyword
- if
helpviewer_keywords:
- else keyword [C#]
- if keyword [C#]
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
ms.openlocfilehash: ef25b3fb5657d833bbccf5bace71e049623476c9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59294415"
---
# <a name="if-else-c-reference"></a><span data-ttu-id="3742e-102">if-else (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3742e-102">if-else (C# Reference)</span></span>

<span data-ttu-id="3742e-103">`if` 陳述式會根據布林運算式的值識別要執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="3742e-103">An `if` statement identifies which statement to run based on the value of a Boolean expression.</span></span> <span data-ttu-id="3742e-104">在下列範例中， `bool` 變數 `condition` 設為 `true` ，然後以 `if` 陳述式進行檢查。</span><span class="sxs-lookup"><span data-stu-id="3742e-104">In the following example, the `bool` variable `condition` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="3742e-105">輸出為 `The variable is set to true.`。</span><span class="sxs-lookup"><span data-stu-id="3742e-105">The output is `The variable is set to true.`.</span></span>

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

<span data-ttu-id="3742e-106">您也可以將本主題中的範例放在主控台 App 的 `Main` 方法執行。</span><span class="sxs-lookup"><span data-stu-id="3742e-106">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>

<span data-ttu-id="3742e-107">如下列範例所示， `if` 陳述式在 C# 中可能有兩種形式。</span><span class="sxs-lookup"><span data-stu-id="3742e-107">An `if` statement in C# can take two forms, as the following example shows.</span></span>

```csharp
// if-else statement
if (condition)
{
    then-statement;
}
else
{
    else-statement;
}
// Next statement in the program.

// if statement without an else
if (condition)
{
    then-statement;
}
// Next statement in the program.
```

<span data-ttu-id="3742e-108">在 `if-else` 陳述式中，如果 `condition` 評估為 true，則執行 `then-statement` 。</span><span class="sxs-lookup"><span data-stu-id="3742e-108">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="3742e-109">如果 `condition` 為 false，則執行 `else-statement` 。</span><span class="sxs-lookup"><span data-stu-id="3742e-109">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="3742e-110">由於 `condition` 無法同時為 true 和 false，所以 `then-statement` 陳述式的 `else-statement` 和 `if-else` 永遠無法同時執行。</span><span class="sxs-lookup"><span data-stu-id="3742e-110">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="3742e-111">在執行 `then-statement` 或 `else-statement` 後，控制權會轉移到在 `if` 陳述式之後的下一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="3742e-111">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="3742e-112">在不包含 `if` 陳述式的 `else` 陳述式，如果 `condition` 為 true，則執行 `then-statement` 。</span><span class="sxs-lookup"><span data-stu-id="3742e-112">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="3742e-113">如果 `condition` 為 false，控制權會轉移到在 `if` 陳述式之後的下一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="3742e-113">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="3742e-114">`then-statement` 和 `else-statement` 皆可包含以大括弧括住 (`{}`) 的單一陳述式或多個陳述式。</span><span class="sxs-lookup"><span data-stu-id="3742e-114">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="3742e-115">對於單一陳述式，大括弧是選擇項，但建議使用。</span><span class="sxs-lookup"><span data-stu-id="3742e-115">For a single statement, the braces are optional but recommended.</span></span>

<span data-ttu-id="3742e-116">在 `then-statement` 和 `else-statement` 的陳述式可以是任何類型，包括其他在原始 `if` 陳述式內巢狀的 `if` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3742e-116">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="3742e-117">在巢狀 `if` 陳述式，每個 `else` 子句都隸屬於最後一個沒有相對應 `if` 的 `else`。</span><span class="sxs-lookup"><span data-stu-id="3742e-117">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="3742e-118">在下列範例中，如果 `Result1` 和 `m > 10` 都評估為 true，則會顯示 `n > 20` 。</span><span class="sxs-lookup"><span data-stu-id="3742e-118">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="3742e-119">如果 `m > 10` 為 true，但 `n > 20` 是 false，則會顯示 `Result2` 。</span><span class="sxs-lookup"><span data-stu-id="3742e-119">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

<span data-ttu-id="3742e-120">如果相反地，您希望 `Result2` 在 `(m > 10)` 為 false 時顯示，則可以使用大括弧指定關聯，以建立巢狀 `if` 陳述式的開頭和結尾，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="3742e-120">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

`Result2` <span data-ttu-id="3742e-121">評估為 false，就會顯示 `(m > 10)` 。</span><span class="sxs-lookup"><span data-stu-id="3742e-121">appears if the condition `(m > 10)` evaluates to false.</span></span>

## <a name="example"></a><span data-ttu-id="3742e-122">範例</span><span class="sxs-lookup"><span data-stu-id="3742e-122">Example</span></span>

<span data-ttu-id="3742e-123">在下列範例中，將由鍵盤輸入字元，而程式會使用巢狀 `if` 陳述式判斷輸入字元是否為字母字元。</span><span class="sxs-lookup"><span data-stu-id="3742e-123">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="3742e-124">如果輸入字元是字母字元，程式就會檢查輸入的字元是大寫或小寫，</span><span class="sxs-lookup"><span data-stu-id="3742e-124">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="3742e-125">並顯示每一種情況的訊息。</span><span class="sxs-lookup"><span data-stu-id="3742e-125">A message appears for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a><span data-ttu-id="3742e-126">範例</span><span class="sxs-lookup"><span data-stu-id="3742e-126">Example</span></span>

<span data-ttu-id="3742e-127">如下列程式碼片段所示，您也可以巢狀方式將 `if` 陳述式置於其他區塊內。</span><span class="sxs-lookup"><span data-stu-id="3742e-127">You also can nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="3742e-128">此範例將 `if` 以巢狀方式置於兩個 else 區塊和一個 then 區塊內部。</span><span class="sxs-lookup"><span data-stu-id="3742e-128">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="3742e-129">在每個區塊中，註解指定哪些條件為 true 或 false。</span><span class="sxs-lookup"><span data-stu-id="3742e-129">The comments specify which conditions are true or false in each block.</span></span>

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a><span data-ttu-id="3742e-130">範例</span><span class="sxs-lookup"><span data-stu-id="3742e-130">Example</span></span>

<span data-ttu-id="3742e-131">下列範例會判斷輸入字元是否為小寫字母、大寫字母或數字。</span><span class="sxs-lookup"><span data-stu-id="3742e-131">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="3742e-132">如果這三個條件為 false，字元不是英數字元。</span><span class="sxs-lookup"><span data-stu-id="3742e-132">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="3742e-133">這個範例會顯示每一種情況的訊息。</span><span class="sxs-lookup"><span data-stu-id="3742e-133">The example displays a message for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

<span data-ttu-id="3742e-134">就像在 else 區塊或 then 區塊中的陳述式可以是任何有效的陳述式一樣，您可以為這個條件使用任何有效的布林運算式。</span><span class="sxs-lookup"><span data-stu-id="3742e-134">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="3742e-135">您可以使用[邏輯運算子](../operators/boolean-logical-operators.md) (例如 `!`、`&&`、`||`、`&`、`|` 和 `^`) 來撰寫複合條件。</span><span class="sxs-lookup"><span data-stu-id="3742e-135">You can use [logical operators](../operators/boolean-logical-operators.md) such as `!`, `&&`, `||`, `&`, `|`, and `^` to make compound conditions.</span></span> <span data-ttu-id="3742e-136">下列程式碼顯示範例。</span><span class="sxs-lookup"><span data-stu-id="3742e-136">The following code shows examples.</span></span>

```csharp
// NOT
bool result = true;
if (!result)
{
    Console.WriteLine("The condition is true (result is false).");
}
else
{
    Console.WriteLine("The condition is false (result is true).");
}

// Short-circuit AND
int m = 9;
int n = 7;
int p = 5;
if (m >= n && m >= p)
{
    Console.WriteLine("Nothing is larger than m.");
}

// AND and NOT
if (m >= n && !(p > m))
{
    Console.WriteLine("Nothing is larger than m.");
}

// Short-circuit OR
if (m > n || m > p)
{
    Console.WriteLine("m isn't the smallest.");
}

// NOT and OR
m = 4;
if (!(m >= n || m >= p))
{
    Console.WriteLine("Now m is the smallest.");
}
// Output:
// The condition is false (result is true).
// Nothing is larger than m.
// Nothing is larger than m.
// m isn't the smallest.
// Now m is the smallest.
```

## <a name="c-language-specification"></a><span data-ttu-id="3742e-137">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3742e-137">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3742e-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3742e-138">See also</span></span>

- [<span data-ttu-id="3742e-139">C# 參考</span><span class="sxs-lookup"><span data-stu-id="3742e-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3742e-140">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="3742e-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3742e-141">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="3742e-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3742e-142">?:運算子</span><span class="sxs-lookup"><span data-stu-id="3742e-142">?: Operator</span></span>](../operators/conditional-operator.md)
- [<span data-ttu-id="3742e-143">if-else 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="3742e-143">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)
- [<span data-ttu-id="3742e-144">switch</span><span class="sxs-lookup"><span data-stu-id="3742e-144">switch</span></span>](switch.md)
