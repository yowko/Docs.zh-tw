---
title: C# 6 的新功能 - C# 指南
description: 了解 C# 第 6 版的新功能
ms.date: 12/12/2018
ms.openlocfilehash: 478fd512f6b6facfce6d7f70f9691ce15e418d6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58920671"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="25310-103">C# 6 的新功能</span><span class="sxs-lookup"><span data-stu-id="25310-103">What's New in C# 6</span></span>

<span data-ttu-id="25310-104">C# 6.0 版包含許多功能，能提升開發人員的產能。</span><span class="sxs-lookup"><span data-stu-id="25310-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="25310-105">這些功能的整體影響是您可撰寫更簡潔且更具可讀性的程式碼，。</span><span class="sxs-lookup"><span data-stu-id="25310-105">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="25310-106">語法包含許多常見做法的較少繁瑣細節。</span><span class="sxs-lookup"><span data-stu-id="25310-106">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="25310-107">繁瑣細節較少時比較容易看出設計目的。</span><span class="sxs-lookup"><span data-stu-id="25310-107">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="25310-108">徹底了解這些功能，可讓您提升生產力，並撰寫更容易閱讀的程式碼。</span><span class="sxs-lookup"><span data-stu-id="25310-108">Learn these features well, and you'll be more productive and write more readable code.</span></span> <span data-ttu-id="25310-109">您可以更專注於您的功能，而不是語言的建構。</span><span class="sxs-lookup"><span data-stu-id="25310-109">You can concentrate more on your features than on the constructs of the language.</span></span>

<span data-ttu-id="25310-110">本文的其餘部分將概述每項功能，並提供連結以探索每項功能。</span><span class="sxs-lookup"><span data-stu-id="25310-110">The rest of this article provides an overview of each of these features, with a link to explore each feature.</span></span> <span data-ttu-id="25310-111">您也可以在＜教學課程＞一節的 [C# 6 互動式探索](../tutorials/exploration/csharp-6.yml)中探索這些功能。</span><span class="sxs-lookup"><span data-stu-id="25310-111">You can also explore the features in an [interactive exploration on C# 6](../tutorials/exploration/csharp-6.yml) in the tutorials section.</span></span>

## <a name="read-only-auto-properties"></a><span data-ttu-id="25310-112">唯讀 Auto 屬性</span><span class="sxs-lookup"><span data-stu-id="25310-112">Read-only auto-properties</span></span>

<span data-ttu-id="25310-113">「唯讀 Auto 屬性」提供更簡潔的語法，來建立不可變的類型。</span><span class="sxs-lookup"><span data-stu-id="25310-113">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="25310-114">您只需要用 get 存取子宣告 Auto 屬性︰</span><span class="sxs-lookup"><span data-stu-id="25310-114">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="25310-115">`FirstName` 和 `LastName` 屬性只能在建構函式主體中設定︰</span><span class="sxs-lookup"><span data-stu-id="25310-115">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="25310-116">嘗試在另一個方法設定 `LastName` 會產生 `CS0200` 編譯錯誤︰</span><span class="sxs-lookup"><span data-stu-id="25310-116">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

<span data-ttu-id="25310-117">這項功能可真正達到建立不可變類型的語言支援，並使用更精簡且方便的 Auto 屬性語法。</span><span class="sxs-lookup"><span data-stu-id="25310-117">This feature enables true language support for creating immutable types and uses the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="25310-118">如果新增這個語法不會移除可存取的方法，那麼這就是[二進位相容變更](version-update-considerations.md#binary-compatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="25310-118">If adding this syntax doesn't remove an accessible method, it's a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="auto-property-initializers"></a><span data-ttu-id="25310-119">Auto 屬性初始設定式</span><span class="sxs-lookup"><span data-stu-id="25310-119">Auto-property initializers</span></span>

<span data-ttu-id="25310-120">「Auto 屬性初始設定式」可以讓您宣告 Auto 屬性的初始值作為屬性宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="25310-120">*Auto-property initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="25310-121">`Grades` 成員會在宣告的位置初始化。</span><span class="sxs-lookup"><span data-stu-id="25310-121">The `Grades` member is initialized where it's declared.</span></span> <span data-ttu-id="25310-122">這可讓您更輕鬆地只執行初始化一次。</span><span class="sxs-lookup"><span data-stu-id="25310-122">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="25310-123">初始化是屬性宣告的一部分，如此能更容易讓儲存區配置與 `Student` 物件的公用介面相等。</span><span class="sxs-lookup"><span data-stu-id="25310-123">The initialization is part of the property declaration, making it easier to equate the storage allocation with the public interface for `Student` objects.</span></span>

## <a name="expression-bodied-function-members"></a><span data-ttu-id="25310-124">具有運算式主體的函式成員</span><span class="sxs-lookup"><span data-stu-id="25310-124">Expression-bodied function members</span></span>

<span data-ttu-id="25310-125">您撰寫的許多成員都是單一陳述式，而這些陳述式可能是單一運算式。</span><span class="sxs-lookup"><span data-stu-id="25310-125">Many members that you write are single statements that could be single expressions.</span></span> <span data-ttu-id="25310-126">請改為撰寫運算式主體成員。</span><span class="sxs-lookup"><span data-stu-id="25310-126">Write an expression-bodied member instead.</span></span> <span data-ttu-id="25310-127">其適用於方法和唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="25310-127">It works for methods and read-only properties.</span></span> <span data-ttu-id="25310-128">例如，`ToString()` 覆寫通常是絕佳的候選︰</span><span class="sxs-lookup"><span data-stu-id="25310-128">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="25310-129">您也可以將此語法用於唯讀屬性：</span><span class="sxs-lookup"><span data-stu-id="25310-129">You can also use this syntax for read-only properties:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="25310-130">將現有成員變更為運算式主體成員是[二進位相容變更](version-update-considerations.md#binary-compatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="25310-130">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="using-static"></a><span data-ttu-id="25310-131">使用靜態</span><span class="sxs-lookup"><span data-stu-id="25310-131">using static</span></span>

<span data-ttu-id="25310-132">「使用靜態」增強功能可讓您匯入單一類別的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="25310-132">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="25310-133">您指定正在使用的類別︰</span><span class="sxs-lookup"><span data-stu-id="25310-133">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="25310-134"><xref:System.Math> 不包含任何執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="25310-134">The <xref:System.Math> does not contain any instance methods.</span></span> <span data-ttu-id="25310-135">您也可以使用 `using static` 為同時具有靜態和執行個體方法的類別匯入類別的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="25310-135">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="25310-136">其中一個最有用的範例是 <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="25310-136">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="25310-137">您必須在靜態 using 陳述式中使用完整的類別名稱 `System.String`。</span><span class="sxs-lookup"><span data-stu-id="25310-137">You must use the fully qualified class name, `System.String`  in a static using statement.</span></span>  <span data-ttu-id="25310-138">不能改用 `string` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="25310-138">You cannot use the `string` keyword instead.</span></span>

<span data-ttu-id="25310-139">如果從 `static using` 陳述式匯入，延伸方法只有在使用延伸方法引動語法來呼叫時才會在範圍中。</span><span class="sxs-lookup"><span data-stu-id="25310-139">When imported from a `static using` statement, extension methods are only in scope when called using the extension method invocation syntax.</span></span> <span data-ttu-id="25310-140">它們在作為靜態方法呼叫時，則不在範圍中。</span><span class="sxs-lookup"><span data-stu-id="25310-140">They aren't in scope when called as a static method.</span></span> <span data-ttu-id="25310-141">您會經常在 LINQ 查詢中看到此情況。</span><span class="sxs-lookup"><span data-stu-id="25310-141">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="25310-142">您可以藉由匯入 <xref:System.Linq.Enumerable> 或 <xref:System.Linq.Queryable> 來匯入 LINQ 模式。</span><span class="sxs-lookup"><span data-stu-id="25310-142">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>, or <xref:System.Linq.Queryable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="25310-143">您通常會使用延伸方法引動運算式來呼叫延伸方法。</span><span class="sxs-lookup"><span data-stu-id="25310-143">You typically call extension methods using extension method invocation expressions.</span></span> <span data-ttu-id="25310-144">在您使用靜態方法呼叫語法來呼叫它們的少數情況下，新增類別名稱可解決語意模糊問題。</span><span class="sxs-lookup"><span data-stu-id="25310-144">Adding the class name in the rare case where you call them using static method call syntax resolves ambiguity.</span></span>

<span data-ttu-id="25310-145">`static using` 指示詞也會匯入任何巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="25310-145">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="25310-146">您可以參照任何巢狀型別而無限定性條件。</span><span class="sxs-lookup"><span data-stu-id="25310-146">You can reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="25310-147">Null 條件運算子</span><span class="sxs-lookup"><span data-stu-id="25310-147">Null-conditional operators</span></span>

<span data-ttu-id="25310-148">「Null 條件運算子」讓 Null 檢查更容易且流暢。</span><span class="sxs-lookup"><span data-stu-id="25310-148">The *null conditional operator* makes null checks much easier and fluid.</span></span> <span data-ttu-id="25310-149">請將成員存取 `.` 取代為 `?.`：</span><span class="sxs-lookup"><span data-stu-id="25310-149">Replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="25310-150">在上述範例中，如果 person 物件為 `null`，變數 `first` 便會被指派 `null`。</span><span class="sxs-lookup"><span data-stu-id="25310-150">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="25310-151">否則，會為其指派 `FirstName` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="25310-151">Otherwise, it is assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="25310-152">最重要的是，`?.` 表示當 `person` 變數是 `null` 時，這行程式碼不會產生 `NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="25310-152">Most importantly, the `?.` means that this line of code doesn't generate a `NullReferenceException` if the `person` variable is `null`.</span></span> <span data-ttu-id="25310-153">相反地，它會進行最少運算並傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="25310-153">Instead, it short-circuits and returns `null`.</span></span> <span data-ttu-id="25310-154">您也可以使用 Null 條件運算子來進行陣列或索引子存取。</span><span class="sxs-lookup"><span data-stu-id="25310-154">You can also use a null conditional operator for array or indexer access.</span></span> <span data-ttu-id="25310-155">請在索引運算式中將 `[]` 取代為 `?[]`。</span><span class="sxs-lookup"><span data-stu-id="25310-155">Replace `[]` with `?[]` in the index expression.</span></span>

<span data-ttu-id="25310-156">不論 `person` 的值為何，下列運算式都會傳回 `string`。</span><span class="sxs-lookup"><span data-stu-id="25310-156">The following expression returns a `string`, regardless of the value of `person`.</span></span> <span data-ttu-id="25310-157">您經常將這個建構與「Null 聯合」運算子一起使用，以便在其中一個屬性為 `null` 時指派預設值。</span><span class="sxs-lookup"><span data-stu-id="25310-157">You often use this construct with the *null coalescing* operator to assign default values when one of the properties is `null`.</span></span> <span data-ttu-id="25310-158">當運算式進行最少運算時，傳回的 `null` 值型別會改變以符合完整的運算式。</span><span class="sxs-lookup"><span data-stu-id="25310-158">When the expression short-circuits, the `null` value returned is typed to match the full expression.</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="25310-159">您也可以使用 `?.` 來進行方法的條件式叫用。</span><span class="sxs-lookup"><span data-stu-id="25310-159">You can also use `?.` to conditionally invoke methods.</span></span> <span data-ttu-id="25310-160">成員函式搭配 Null 條件運算子的最常見用法，是安全地叫用可能為 `null` 的委派 (或事件處理常式)。</span><span class="sxs-lookup"><span data-stu-id="25310-160">The most common use of member functions  with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="25310-161">您將使用 `?.` 運算子呼叫委派的 `Invoke` 方法來存取成員。</span><span class="sxs-lookup"><span data-stu-id="25310-161">You'll call the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="25310-162">如需範例，請參閱[委派模式](../delegates-patterns.md#handling-null-delegates)一文。</span><span class="sxs-lookup"><span data-stu-id="25310-162">You can see an example in the [delegate patterns](../delegates-patterns.md#handling-null-delegates) article.</span></span>

<span data-ttu-id="25310-163">`?.` 運算子的規則確保運算子的左邊只會評估一次。</span><span class="sxs-lookup"><span data-stu-id="25310-163">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="25310-164">它可啟用許多慣用句，包括使用事件處理常式的下列範例：</span><span class="sxs-lookup"><span data-stu-id="25310-164">It enables many idioms, including the following example using event handlers:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="25310-165">確保左側只評估一次也可讓您在 `?.` 的左側使用任何運算式，包括方法呼叫</span><span class="sxs-lookup"><span data-stu-id="25310-165">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.`</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="25310-166">字串插補</span><span class="sxs-lookup"><span data-stu-id="25310-166">String interpolation</span></span>

<span data-ttu-id="25310-167">使用 C# 6，新的[字串插補](../language-reference/tokens/interpolated.md)功能可讓您將運算式內嵌在字串中。</span><span class="sxs-lookup"><span data-stu-id="25310-167">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed expressions in a string.</span></span> <span data-ttu-id="25310-168">只需要在字串前面加上 `$`，並在 `{` 與 `}` 之間使用運算式而不是序數：</span><span class="sxs-lookup"><span data-stu-id="25310-168">Simply preface the string with `$`and use expressions between `{` and `}` instead of ordinals:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="25310-169">這個範例將屬性用於替代的運算式。</span><span class="sxs-lookup"><span data-stu-id="25310-169">This example uses properties for the substituted expressions.</span></span> <span data-ttu-id="25310-170">您可以使用任何運算式。</span><span class="sxs-lookup"><span data-stu-id="25310-170">You can use any expression.</span></span> <span data-ttu-id="25310-171">比方說，您可能在內插補點的過程中計算某學生的平均成積點︰</span><span class="sxs-lookup"><span data-stu-id="25310-171">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="25310-172">前一行程式碼會將 `Grades.Average()` 的值格式化為具有兩個小數位數的浮點數。</span><span class="sxs-lookup"><span data-stu-id="25310-172">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="25310-173">通常，您可能需要格式化使用特定文化特性產生的字串。</span><span class="sxs-lookup"><span data-stu-id="25310-173">Often, you may need to format the string produced using a specific culture.</span></span> <span data-ttu-id="25310-174">您會利用字串插補所產生的物件可隱含轉換為 <xref:System.FormattableString?displayProperty=nameWithType> 的事實。</span><span class="sxs-lookup"><span data-stu-id="25310-174">You use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="25310-175"><xref:System.FormattableString> 執行個體包含複合格式字串，以及在將其轉換為字串之前，評估運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="25310-175">The <xref:System.FormattableString> instance contains the composite format string and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="25310-176">使用 <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> 方法以指定設定字串格式時的文化特性。</span><span class="sxs-lookup"><span data-stu-id="25310-176">Use the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method to specify the culture when formatting a string.</span></span> <span data-ttu-id="25310-177">下列範例會使用德國 (de-DE) 文化特性產生字串。</span><span class="sxs-lookup"><span data-stu-id="25310-177">The following example produces a string using the German (de-DE) culture.</span></span> <span data-ttu-id="25310-178">(根據預設，德國文化特性會使用 ',' 字元作為十進位分隔符號，並使用 '. ' 字元作為千位分隔符號。)</span><span class="sxs-lookup"><span data-stu-id="25310-178">(By default, the German culture uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="25310-179">若要開始使用字串插補，請參閱 [C# 中的字串插補](../tutorials/exploration/interpolated-strings.yml)互動式教學課程、[字串插補](../language-reference/tokens/interpolated.md)一文，以及 [C# 中的字串插補](../tutorials/string-interpolation.md)教學課程。</span><span class="sxs-lookup"><span data-stu-id="25310-179">To get started with string interpolation, see the [String interpolation in C#](../tutorials/exploration/interpolated-strings.yml) interactive tutorial, the [String interpolation](../language-reference/tokens/interpolated.md) article, and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="25310-180">例外狀況篩選條件</span><span class="sxs-lookup"><span data-stu-id="25310-180">Exception filters</span></span>

<span data-ttu-id="25310-181">*例外狀況篩選條件*是判斷指定 catch 子句何時應該套用的子句。</span><span class="sxs-lookup"><span data-stu-id="25310-181">*Exception Filters* are clauses that determine when a given catch clause should be applied.</span></span> <span data-ttu-id="25310-182">如果例外狀況篩選條件所用的運算式評估為 `true`，catch 子句便會對例外狀況執行其一般處理。</span><span class="sxs-lookup"><span data-stu-id="25310-182">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="25310-183">如果運算式評估為 `false`，則會略過 `catch` 子句。</span><span class="sxs-lookup"><span data-stu-id="25310-183">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span> <span data-ttu-id="25310-184">用法之一是檢查例外狀況的相關資訊，以判斷 `catch` 子句是否可以處理例外狀況︰</span><span class="sxs-lookup"><span data-stu-id="25310-184">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a><span data-ttu-id="25310-185">`nameof` 運算式</span><span class="sxs-lookup"><span data-stu-id="25310-185">The `nameof` expression</span></span>

<span data-ttu-id="25310-186">`nameof` 運算式評估為符號的名稱。</span><span class="sxs-lookup"><span data-stu-id="25310-186">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="25310-187">每當您需要變數、屬性或成員欄位的名稱時，這是讓工具能運作的好方法。</span><span class="sxs-lookup"><span data-stu-id="25310-187">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span> <span data-ttu-id="25310-188">`nameof` 最常見的其中一個用途是提供造成例外狀況的符號名稱︰</span><span class="sxs-lookup"><span data-stu-id="25310-188">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="25310-189">另一個用途是實作 `INotifyPropertyChanged` 介面的 XAML 型應用程式：</span><span class="sxs-lookup"><span data-stu-id="25310-189">Another use is with XAML-based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="25310-190">Catch 和 Finally 區塊中的 Await</span><span class="sxs-lookup"><span data-stu-id="25310-190">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="25310-191">C# 5 對於您可以放置 `await` 運算式的位置有數個限制。</span><span class="sxs-lookup"><span data-stu-id="25310-191">C# 5 had several limitations around where you could place `await` expressions.</span></span> <span data-ttu-id="25310-192">透過 C# 6，您現在可以在 `catch` 或 `finally` 運算式中使用 `await`。</span><span class="sxs-lookup"><span data-stu-id="25310-192">With C# 6, you can now use `await` in `catch` or `finally` expressions.</span></span> <span data-ttu-id="25310-193">這最常用於記錄情節︰</span><span class="sxs-lookup"><span data-stu-id="25310-193">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="25310-194">在 `catch` 和 `finally` 子句內新增 `await` 支援的實作詳細資料，可確保行為與同步程式碼的行為一致。</span><span class="sxs-lookup"><span data-stu-id="25310-194">The implementation details for adding `await` support inside `catch` and `finally` clauses ensure that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="25310-195">當 `catch` 或 `finally` 子句中執行的程式碼擲回時，執行會在下個周圍區塊中尋找適合的 `catch` 子句。</span><span class="sxs-lookup"><span data-stu-id="25310-195">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="25310-196">如果有目前的例外狀況，該例外狀況將會遺失。</span><span class="sxs-lookup"><span data-stu-id="25310-196">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="25310-197">`catch` 和 `finally` 子 句中等候的運算式也會發生相同的情況︰搜尋適合的 `catch`，目前的例外狀況 (如果有的話) 將會遺失。</span><span class="sxs-lookup"><span data-stu-id="25310-197">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="25310-198">此行為是建議您小心撰寫 `catch` 和 `finally` 子句的原因，以避免產生新的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="25310-198">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="initialize-associative-collections-using-indexers"></a><span data-ttu-id="25310-199">使用索引子初始化關聯集合</span><span class="sxs-lookup"><span data-stu-id="25310-199">Initialize associative collections using indexers</span></span>

<span data-ttu-id="25310-200">「索引初始設定式」是讓集合初始設定式與索引使用方式更一致的兩個功能之一。</span><span class="sxs-lookup"><span data-stu-id="25310-200">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="25310-201">在舊版的 C# 中，您可以在索引鍵值/組前後新增大括弧，藉以搭配序列樣式集合 (包括 <xref:System.Collections.Generic.Dictionary%602>) 來使用「集合初始設定式」：</span><span class="sxs-lookup"><span data-stu-id="25310-201">In earlier releases of C#, you could use *collection initializers* with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602>, by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

<span data-ttu-id="25310-202">您可將它們與 <xref:System.Collections.Generic.Dictionary%602> 集合和其他類型一起使用，其中可存取的 `Add` 方法接受一個以上的引數。</span><span class="sxs-lookup"><span data-stu-id="25310-202">You can use them with <xref:System.Collections.Generic.Dictionary%602> collections and other types where the accessible `Add` method accepts more than one argument.</span></span> <span data-ttu-id="25310-203">新的語法支援使用集合中的索引進行指派：</span><span class="sxs-lookup"><span data-stu-id="25310-203">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="25310-204">這項功能表示可以使用類似於已可供數個版本的序列容器使用的語法，將關聯容器初始化。</span><span class="sxs-lookup"><span data-stu-id="25310-204">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="25310-205">集合初始設定式中的擴充 `Add` 方法</span><span class="sxs-lookup"><span data-stu-id="25310-205">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="25310-206">能夠輕鬆進行集合初始設定的另一個功能，是可以針對 `Add` 方法使用「擴充方法」。</span><span class="sxs-lookup"><span data-stu-id="25310-206">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="25310-207">新增這項功能是為了與 Visual Basic 相當。</span><span class="sxs-lookup"><span data-stu-id="25310-207">This feature was added for parity with Visual Basic.</span></span> <span data-ttu-id="25310-208">當您的自訂集合類別具有不同名稱的方法，可以在語意上新增項目時，此功能最實用。</span><span class="sxs-lookup"><span data-stu-id="25310-208">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="25310-209">改進的多載解析</span><span class="sxs-lookup"><span data-stu-id="25310-209">Improved overload resolution</span></span>

<span data-ttu-id="25310-210">您可能不會發現最後這項功能。</span><span class="sxs-lookup"><span data-stu-id="25310-210">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="25310-211">在有些建構中，舊版 C# 編譯器可能會發現一些涉及 Lambda 運算式的方法呼叫為模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="25310-211">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="25310-212">請參考下列方法：</span><span class="sxs-lookup"><span data-stu-id="25310-212">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="25310-213">在舊版的 C# 中，使用方法群組語法呼叫該方法會失敗︰</span><span class="sxs-lookup"><span data-stu-id="25310-213">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

<span data-ttu-id="25310-214">舊版的編譯器無法正確分辨 `Task.Run(Action)` 與 `Task.Run(Func<Task>())`。</span><span class="sxs-lookup"><span data-stu-id="25310-214">The earlier compiler couldn't distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="25310-215">在舊版中，您必須使用 Lambda 運算式作為引數︰</span><span class="sxs-lookup"><span data-stu-id="25310-215">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="25310-216">C# 6 編譯器可正確判斷 `Task.Run(Func<Task>())` 是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="25310-216">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="25310-217">deterministic 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="25310-217">Deterministic compiler output</span></span>

<span data-ttu-id="25310-218">`-deterministic` 選項會指示編譯器針對相同原始程式檔 的後續編譯產生位元組對位元組的相同輸出組件。</span><span class="sxs-lookup"><span data-stu-id="25310-218">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="25310-219">根據預設，每次編譯會針對每次編譯產生唯一的輸出。</span><span class="sxs-lookup"><span data-stu-id="25310-219">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="25310-220">編譯器會新增時間戳記，以及從亂數產生的 GUID。</span><span class="sxs-lookup"><span data-stu-id="25310-220">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="25310-221">如果您想要比較位元組對位元組的輸出，以確保組建的一致性，您可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="25310-221">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="25310-222">如需詳細資訊，請參閱 [-deterministic 編譯器選項](../language-reference/compiler-options/deterministic-compiler-option.md)文章。</span><span class="sxs-lookup"><span data-stu-id="25310-222">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
