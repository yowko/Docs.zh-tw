---
title: for (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
caps.latest.revision: 39
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb7e83733fe026658f502b430975a0f8a27e9df3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="for-c-reference"></a><span data-ttu-id="056a4-102">for (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="056a4-102">for (C# Reference)</span></span>
<span data-ttu-id="056a4-103">透過 `for` 迴圈，您可以重複執行陳述式或陳述式區塊，直到指定的運算式評估為 `false` 為止。</span><span class="sxs-lookup"><span data-stu-id="056a4-103">By using a `for` loop, you can run a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="056a4-104">這種迴圈對於逐一查看陣列很有用，也適用於您事先知道迴圈要反覆運算幾次的其他應用。</span><span class="sxs-lookup"><span data-stu-id="056a4-104">This kind of loop is useful for iterating over arrays and for other applications in which you know in advance how many times you want the loop to iterate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="056a4-105">範例</span><span class="sxs-lookup"><span data-stu-id="056a4-105">Example</span></span>  
 <span data-ttu-id="056a4-106">在下列範例中，`i` 值會寫入至主控台，並在迴圈每次反覆運算就加 1。</span><span class="sxs-lookup"><span data-stu-id="056a4-106">In the following example, the value of `i` is written to the console and incremented by 1 during each iteration of the loop.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 <span data-ttu-id="056a4-107">上述範例中的 `for` 陳述式會執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="056a4-107">The `for` statement in the previous example performs the following actions.</span></span>  
  
1.  <span data-ttu-id="056a4-108">首先，請建立變數 `i` 的初始值。</span><span class="sxs-lookup"><span data-stu-id="056a4-108">First, the initial value of variable `i` is established.</span></span> <span data-ttu-id="056a4-109">不論迴圈重複幾次，此步驟只會發生一次。</span><span class="sxs-lookup"><span data-stu-id="056a4-109">This step happens only once, regardless of how many times the loop repeats.</span></span> <span data-ttu-id="056a4-110">您可以將此初始化視為在迴圈程序之外進行。</span><span class="sxs-lookup"><span data-stu-id="056a4-110">You can think of this initialization as happening outside the looping process.</span></span>  
  
2.  <span data-ttu-id="056a4-111">為了評估條件 (`i <= 5`)，`i` 值會與 5 進行比較。</span><span class="sxs-lookup"><span data-stu-id="056a4-111">To evaluate the condition (`i <= 5`), the value of `i` is compared to 5.</span></span>  
  
    -   <span data-ttu-id="056a4-112">如果 `i` 小於或等於 5，則條件會評估為 `true`，而且會執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="056a4-112">If `i` is less than or equal to 5, the condition evaluates to `true`, and the following actions occur.</span></span>  
  
        1.  <span data-ttu-id="056a4-113">迴圈主體中的 `Console.WriteLine` 陳述式會顯示 `i` 值。</span><span class="sxs-lookup"><span data-stu-id="056a4-113">The `Console.WriteLine` statement in the body of the loop displays the value of `i`.</span></span>  
  
        2.  <span data-ttu-id="056a4-114">此 `i` 值會加 1。</span><span class="sxs-lookup"><span data-stu-id="056a4-114">The value of `i` is incremented by 1.</span></span>  
  
        3.  <span data-ttu-id="056a4-115">迴圈會回到步驟 2 的開頭，以重新評估條件。</span><span class="sxs-lookup"><span data-stu-id="056a4-115">The loop returns to the start of step 2 to evaluate the condition again.</span></span>  
  
    -   <span data-ttu-id="056a4-116">如果 `i` 大於 5，則條件會評估為`false`，而且您會結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="056a4-116">If `i` is greater than 5, the condition evaluates to `false`, and you exit the loop.</span></span>  
  
 <span data-ttu-id="056a4-117">請注意，如果 `i` 的初始值大於 5，則迴圈主體一次也不會執行。</span><span class="sxs-lookup"><span data-stu-id="056a4-117">Note that, if the initial value of `i` is greater than 5, the body of the loop doesn't run even once.</span></span>  
  
 <span data-ttu-id="056a4-118">每個 `for` 陳述式都會定義初始設定式、條件和迭代器區段。</span><span class="sxs-lookup"><span data-stu-id="056a4-118">Every `for` statement defines initializer, condition, and iterator sections.</span></span> <span data-ttu-id="056a4-119">這些區段通常會決定迴圈的反覆運算次數。</span><span class="sxs-lookup"><span data-stu-id="056a4-119">These sections usually determine how many times the loop iterates.</span></span>  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
 <span data-ttu-id="056a4-120">這些區段有下列用途。</span><span class="sxs-lookup"><span data-stu-id="056a4-120">The sections serve the following purposes.</span></span>  
  
-   <span data-ttu-id="056a4-121">初始設定式區段會設定初始條件。</span><span class="sxs-lookup"><span data-stu-id="056a4-121">The initializer section sets the initial conditions.</span></span> <span data-ttu-id="056a4-122">此區段中的陳述式只會執行一次，之後就會進入迴圈。</span><span class="sxs-lookup"><span data-stu-id="056a4-122">The statements in this section run only once, before you enter the loop.</span></span> <span data-ttu-id="056a4-123">此區段只能包含下列兩個選項的其中之一。</span><span class="sxs-lookup"><span data-stu-id="056a4-123">The section can contain only one of the following two options.</span></span>  
  
    -   <span data-ttu-id="056a4-124">區域迴圈變數的宣告和初始化，如第一個範例所示 (`int i = 1`)。</span><span class="sxs-lookup"><span data-stu-id="056a4-124">The declaration and initialization of a local loop variable, as the first example shows (`int i = 1`).</span></span> <span data-ttu-id="056a4-125">這是迴圈的區域變數，無法從迴圈外部存取。</span><span class="sxs-lookup"><span data-stu-id="056a4-125">The variable is local to the loop and can't be accessed from outside the loop.</span></span>  
  
    -   <span data-ttu-id="056a4-126">下列清單中的零個或多個陳述式運算式，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="056a4-126">Zero or more statement expressons from the following list, separated by commas.</span></span>  
  
        -   <span data-ttu-id="056a4-127">[指派](../../../csharp/language-reference/operators/assignment-operator.md)陳述式</span><span class="sxs-lookup"><span data-stu-id="056a4-127">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
        -   <span data-ttu-id="056a4-128">方法的引動過程</span><span class="sxs-lookup"><span data-stu-id="056a4-128">invocation of a method</span></span>  
  
        -   <span data-ttu-id="056a4-129">前置或後置[遞增](../../../csharp/language-reference/operators/increment-operator.md)運算式，例如 `++i` 或 `i++`</span><span class="sxs-lookup"><span data-stu-id="056a4-129">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
        -   <span data-ttu-id="056a4-130">前置或後置[遞減](../../../csharp/language-reference/operators/decrement-operator.md)運算式，例如 `--i` 或 `i--`</span><span class="sxs-lookup"><span data-stu-id="056a4-130">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
        -   <span data-ttu-id="056a4-131">使用 [new](../../../csharp/language-reference/keywords/new-operator.md) 建立物件</span><span class="sxs-lookup"><span data-stu-id="056a4-131">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
        -   <span data-ttu-id="056a4-132">[await](../../../csharp/language-reference/keywords/await.md) 運算式</span><span class="sxs-lookup"><span data-stu-id="056a4-132">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="056a4-133">條件區段包含布林運算式，以評估判斷迴圈應該結束或重新執行。</span><span class="sxs-lookup"><span data-stu-id="056a4-133">The condition section contains a boolean expression that’s evaluated to determine whether the loop should exit or should run again.</span></span>  
  
-   <span data-ttu-id="056a4-134">迭代器區段會定義迴圈主體每次反覆運算之後的狀況。</span><span class="sxs-lookup"><span data-stu-id="056a4-134">The iterator section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="056a4-135">迭代器區段包含下列零個或多個陳述式運算式，並以逗號分隔：</span><span class="sxs-lookup"><span data-stu-id="056a4-135">The iterator section contains zero or more of the following statement expressions, separated by commas:</span></span>  
  
    -   <span data-ttu-id="056a4-136">[指派](../../../csharp/language-reference/operators/assignment-operator.md)陳述式</span><span class="sxs-lookup"><span data-stu-id="056a4-136">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
    -   <span data-ttu-id="056a4-137">方法的引動過程</span><span class="sxs-lookup"><span data-stu-id="056a4-137">invocation of a method</span></span>  
  
    -   <span data-ttu-id="056a4-138">前置或後置[遞增](../../../csharp/language-reference/operators/increment-operator.md)運算式，例如 `++i` 或 `i++`</span><span class="sxs-lookup"><span data-stu-id="056a4-138">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
    -   <span data-ttu-id="056a4-139">前置或後置[遞減](../../../csharp/language-reference/operators/decrement-operator.md)運算式，例如 `--i` 或 `i--`</span><span class="sxs-lookup"><span data-stu-id="056a4-139">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
    -   <span data-ttu-id="056a4-140">使用 [new](../../../csharp/language-reference/keywords/new-operator.md) 建立物件</span><span class="sxs-lookup"><span data-stu-id="056a4-140">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
    -   <span data-ttu-id="056a4-141">[await](../../../csharp/language-reference/keywords/await.md) 運算式</span><span class="sxs-lookup"><span data-stu-id="056a4-141">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="056a4-142">迴圈主體包含陳述式、空白陳述式或陳述式區塊，您可以用括號括住零個或多個陳述式來建立。</span><span class="sxs-lookup"><span data-stu-id="056a4-142">The body of the loop consists of a statement, an empty statement, or a block of statements, which you create by enclosing zero or more statements in braces.</span></span>  
  
     <span data-ttu-id="056a4-143">您可以使用 [break](../../../csharp/language-reference/keywords/break.md) 關鍵字跳出 `for` 迴圈，或使用 [continue](../../../csharp/language-reference/keywords/continue.md) 關鍵字逐步執行到下一個反覆運算。</span><span class="sxs-lookup"><span data-stu-id="056a4-143">You can break out of a `for` loop by using the [break](../../../csharp/language-reference/keywords/break.md) keyword, or you can step to the next iteration by using the [continue](../../../csharp/language-reference/keywords/continue.md) keyword.</span></span> <span data-ttu-id="056a4-144">您也可以使用 [goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式結束任何迴圈。</span><span class="sxs-lookup"><span data-stu-id="056a4-144">You also can exit any loop by using a [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement.</span></span>  
  
 <span data-ttu-id="056a4-145">本主題中的第一個範例示範最典型的 `for` 迴圈，並在各區段中進行下列選擇。</span><span class="sxs-lookup"><span data-stu-id="056a4-145">The first example in this topic shows the most typical kind of `for` loop, which makes the following choices for the sections.</span></span>  
  
-   <span data-ttu-id="056a4-146">初始設定式會宣告並初始化區域迴圈變數 `i`，以維護迴圈的反覆運算計數。</span><span class="sxs-lookup"><span data-stu-id="056a4-146">The initializer declares and initializes a local loop variable, `i`, that maintains a count of the iterations of the loop.</span></span>  
  
-   <span data-ttu-id="056a4-147">條件會根據已知的最後一個值 5 來檢查迴圈變數的值。</span><span class="sxs-lookup"><span data-stu-id="056a4-147">The condition checks the value of the loop variable against a known final value, 5.</span></span>  
  
-   <span data-ttu-id="056a4-148">迭代器區段使用後置遞增陳述式 `i++`，來合計迴圈的每個反覆運算。</span><span class="sxs-lookup"><span data-stu-id="056a4-148">The iterator section uses a postfix increment statement, `i++`, to tally each iteration of the loop.</span></span>  
  
 <span data-ttu-id="056a4-149">下列範例描述幾個較少見的選項︰將值指派給初始設定式區段中的外部迴圈變數、在初始設定式和迭代器區段中叫用 `Console.WriteLine` 方法，以及在迭代器區段中變更兩個變數的值。</span><span class="sxs-lookup"><span data-stu-id="056a4-149">The following example illustrates several less common choices: assigning a value to an external loop variable in the initializer section,  invoking the `Console.WriteLine` method in both the initializer and the iterator sections, and changing the values of two variables in the iterator section.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 <span data-ttu-id="056a4-150">所有定義 `for` 陳述式的運算式都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="056a4-150">All of the expressions that define a `for` statement are optional.</span></span> <span data-ttu-id="056a4-151">例如，下列陳述式會建立一個無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="056a4-151">For example, the following statement creates an infinite loop.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="056a4-152">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="056a4-152">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="056a4-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="056a4-153">See Also</span></span>  
 [<span data-ttu-id="056a4-154">C# 參考</span><span class="sxs-lookup"><span data-stu-id="056a4-154">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="056a4-155">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="056a4-155">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="056a4-156">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="056a4-156">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="056a4-157">foreach、in</span><span class="sxs-lookup"><span data-stu-id="056a4-157">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="056a4-158">for 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="056a4-158">for Statement (C++)</span></span>](/cpp/cpp/for-statement-cpp)  
 [<span data-ttu-id="056a4-159">反覆運算陳述式</span><span class="sxs-lookup"><span data-stu-id="056a4-159">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
