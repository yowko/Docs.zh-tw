---
title: C# 6 的新功能 - C# 指南
description: 了解 C# 第 6 版的新功能
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: f6f953eacc935d38cc7d45173109c96c52a5e2f3
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2018
ms.locfileid: "47208181"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="1854f-103">C# 6 的新功能</span><span class="sxs-lookup"><span data-stu-id="1854f-103">What's New in C# 6</span></span>

<span data-ttu-id="1854f-104">C# 6.0 版包含許多功能，能提升開發人員的產能。</span><span class="sxs-lookup"><span data-stu-id="1854f-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="1854f-105">本版的功能包括︰</span><span class="sxs-lookup"><span data-stu-id="1854f-105">Features in this release include:</span></span>

* <span data-ttu-id="1854f-106">[唯讀 Auto 屬性](#read-only-auto-properties)：</span><span class="sxs-lookup"><span data-stu-id="1854f-106">[Read-only Auto-properties](#read-only-auto-properties):</span></span>
    - <span data-ttu-id="1854f-107">您可以建立只能在建構函式中設定的唯讀 Auto 屬性。</span><span class="sxs-lookup"><span data-stu-id="1854f-107">You can create read-only auto-properties that can be set only in constructors.</span></span>
* <span data-ttu-id="1854f-108">[Auto 屬性初始設定式](#auto-property-initializers)：</span><span class="sxs-lookup"><span data-stu-id="1854f-108">[Auto-Property Initializers](#auto-property-initializers):</span></span>
    - <span data-ttu-id="1854f-109">您可以撰寫初始化運算式，以設定 Auto 屬性的初始值。</span><span class="sxs-lookup"><span data-stu-id="1854f-109">You can write initialization expressions to set the initial value of an auto-property.</span></span>
* <span data-ttu-id="1854f-110">[具有運算式主體的函式成員](#expression-bodied-function-members)：</span><span class="sxs-lookup"><span data-stu-id="1854f-110">[Expression-bodied function members](#expression-bodied-function-members):</span></span>
    - <span data-ttu-id="1854f-111">您可以使用 Lambda 運算式撰寫單行方法。</span><span class="sxs-lookup"><span data-stu-id="1854f-111">You can author one-line methods using lambda expressions.</span></span>
* <span data-ttu-id="1854f-112">[使用靜態](#using-static)：</span><span class="sxs-lookup"><span data-stu-id="1854f-112">[using static](#using-static):</span></span>
    - <span data-ttu-id="1854f-113">您可以將單一類別的所有方法都匯入目前的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1854f-113">You can import all the methods of a single class into the current namespace.</span></span>
* <span data-ttu-id="1854f-114">[Null - 條件運算子](#null-conditional-operators)：</span><span class="sxs-lookup"><span data-stu-id="1854f-114">[Null - conditional operators](#null-conditional-operators):</span></span>
    - <span data-ttu-id="1854f-115">您可以精確且安全地存取物件的成員，同時仍然以 null 條件運算子檢查 null。</span><span class="sxs-lookup"><span data-stu-id="1854f-115">You can concisely and safely access members of an object while still checking for null with the null conditional operator.</span></span>
* <span data-ttu-id="1854f-116">[字串插值](#string-interpolation)：</span><span class="sxs-lookup"><span data-stu-id="1854f-116">[String Interpolation](#string-interpolation):</span></span>
    - <span data-ttu-id="1854f-117">您可以使用內嵌運算式而非位置引數來撰寫字串格式化運算式。</span><span class="sxs-lookup"><span data-stu-id="1854f-117">You can write string formatting expressions using inline expressions instead of positional arguments.</span></span>
* <span data-ttu-id="1854f-118">[例外狀況篩選條件](#exception-filters)：</span><span class="sxs-lookup"><span data-stu-id="1854f-118">[Exception filters](#exception-filters):</span></span>
    - <span data-ttu-id="1854f-119">您可以根據例外狀況的屬性或其他程式狀態攔截運算式。</span><span class="sxs-lookup"><span data-stu-id="1854f-119">You can catch expressions based on properties of the exception or other program state.</span></span> 
* <span data-ttu-id="1854f-120">[nameof 運算式](#nameof-expressions)：</span><span class="sxs-lookup"><span data-stu-id="1854f-120">[nameof Expressions](#nameof-expressions):</span></span>
    - <span data-ttu-id="1854f-121">您可以讓編譯器產生符號的字串表示。</span><span class="sxs-lookup"><span data-stu-id="1854f-121">You can let the compiler generate string representations of symbols.</span></span>
* <span data-ttu-id="1854f-122">[Catch 和 Finally 區塊中的 Await](#await-in-catch-and-finally-blocks)：</span><span class="sxs-lookup"><span data-stu-id="1854f-122">[await in catch and finally blocks](#await-in-catch-and-finally-blocks):</span></span>
    - <span data-ttu-id="1854f-123">您可以在先前不允許 `await` 運算式的位置中使用它們。</span><span class="sxs-lookup"><span data-stu-id="1854f-123">You can use `await` expressions in locations that previously disallowed them.</span></span>
* <span data-ttu-id="1854f-124">[索引初始設定式](#index-initializers)：</span><span class="sxs-lookup"><span data-stu-id="1854f-124">[index initializers](#index-initializers):</span></span>
    - <span data-ttu-id="1854f-125">您可以撰寫關聯容器和序列容器的初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="1854f-125">You can author initialization expressions for associative containers as well as sequence containers.</span></span>
* <span data-ttu-id="1854f-126">[集合初始設定式的擴充方法](#extension-add-methods-in-collection-initializers)：</span><span class="sxs-lookup"><span data-stu-id="1854f-126">[Extension methods for collection initializers](#extension-add-methods-in-collection-initializers):</span></span>
    - <span data-ttu-id="1854f-127">集合初始設定式可以依賴可存取的擴充方法，以及成員方法。</span><span class="sxs-lookup"><span data-stu-id="1854f-127">Collection initializers can rely on accessible extension methods, in addition to member methods.</span></span>
* <span data-ttu-id="1854f-128">[改進的多載解析](#improved-overload-resolution)：</span><span class="sxs-lookup"><span data-stu-id="1854f-128">[Improved overload resolution](#improved-overload-resolution):</span></span>
    - <span data-ttu-id="1854f-129">有些建構先前會產生模稜兩可的方法呼叫，現在已可以正確解析。</span><span class="sxs-lookup"><span data-stu-id="1854f-129">Some constructs that previously generated ambiguous method calls now resolve correctly.</span></span>
* <span data-ttu-id="1854f-130">[`deterministic` 編譯器選項](#deterministic-compiler-output)：</span><span class="sxs-lookup"><span data-stu-id="1854f-130">[`deterministic` compiler option](#deterministic-compiler-output):</span></span>
    - <span data-ttu-id="1854f-131">deterministic 編譯器選項可確保相同來源的後續編譯會產生相同的二進位輸出。</span><span class="sxs-lookup"><span data-stu-id="1854f-131">The deterministic compiler option ensures that subsequent compilations of the same source generate the same binary output.</span></span>

<span data-ttu-id="1854f-132">這些功能的整體影響是您可撰寫更簡潔且更具可讀性的程式碼，。</span><span class="sxs-lookup"><span data-stu-id="1854f-132">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="1854f-133">語法包含許多常見做法的較少繁瑣細節。</span><span class="sxs-lookup"><span data-stu-id="1854f-133">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="1854f-134">繁瑣細節較少時比較容易看出設計目的。</span><span class="sxs-lookup"><span data-stu-id="1854f-134">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="1854f-135">充分了解這些功能，您將更具生產力、撰寫更具可讀性的程式碼，並且更專注於您的核心功能，而不是語言的建構。</span><span class="sxs-lookup"><span data-stu-id="1854f-135">Learn these features well, and you'll be more productive, write more readable code, and concentrate more on your core features than on the constructs of the language.</span></span>

<span data-ttu-id="1854f-136">本主題的其餘部分提供這些功能每一項的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1854f-136">The remainder of this topic provides details on each of these features.</span></span>

## <a name="auto-property-enhancements"></a><span data-ttu-id="1854f-137">Auto 屬性增強功能</span><span class="sxs-lookup"><span data-stu-id="1854f-137">Auto-Property enhancements</span></span>

<span data-ttu-id="1854f-138">自動實作屬性 (通常稱為 Auto 屬性) 的語法讓建立具有簡單 get 和 set 存取子的屬性變得相當容易︰</span><span class="sxs-lookup"><span data-stu-id="1854f-138">The syntax for automatically implemented properties (usually referred to as 'auto-properties') made it very easy to create properties that had simple get and set accessors:</span></span>

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

<span data-ttu-id="1854f-139">不過，這個簡單的語法限制了您可以使用 Auto 屬性支援的設計類型。</span><span class="sxs-lookup"><span data-stu-id="1854f-139">However, this simple syntax limited the kinds of designs you could support using auto-properties.</span></span> <span data-ttu-id="1854f-140">C# 6 改善 Auto 屬性功能，讓您可以在更多案例中使用它們。</span><span class="sxs-lookup"><span data-stu-id="1854f-140">C# 6 improves the auto-properties capabilities so that you can use them in more scenarios.</span></span> <span data-ttu-id="1854f-141">您不需要最後求助於更詳細的宣告語法，並且經常以手動方式操作支援欄位。</span><span class="sxs-lookup"><span data-stu-id="1854f-141">You won't need to fall back on the more verbose syntax of declaring and manipulating the backing field by hand so often.</span></span>

<span data-ttu-id="1854f-142">新的語法可解決唯讀屬性的案例，以及初始化 Auto 屬性背後的變數儲存體。</span><span class="sxs-lookup"><span data-stu-id="1854f-142">The new syntax addresses scenarios for read-only properties, and for initializing the variable storage behind an auto-property.</span></span>

### <a name="read-only-auto-properties"></a><span data-ttu-id="1854f-143">唯讀 Auto 屬性</span><span class="sxs-lookup"><span data-stu-id="1854f-143">Read-only auto-properties</span></span>

<span data-ttu-id="1854f-144">「唯讀 Auto 屬性」提供更簡潔的語法，來建立不可變的類型。</span><span class="sxs-lookup"><span data-stu-id="1854f-144">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="1854f-145">在舊版 C# ，您最接近不可變類型的程度是宣告私用 setter：</span><span class="sxs-lookup"><span data-stu-id="1854f-145">The closest you could get to immutable types in earlier versions of C# was to declare private setters:</span></span>

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
<span data-ttu-id="1854f-146">使用這個語法時，編譯器不會確定類型是否確實不可變。</span><span class="sxs-lookup"><span data-stu-id="1854f-146">Using this syntax, the compiler doesn't ensure that the type really is immutable.</span></span> <span data-ttu-id="1854f-147">它只會強制使 `FirstName` 和 `LastName` 屬性不會被類別之外的任何程式碼修改。</span><span class="sxs-lookup"><span data-stu-id="1854f-147">It only enforces that the `FirstName` and `LastName` properties are not modified from any code outside the class.</span></span>

<span data-ttu-id="1854f-148">唯讀 Auto 屬性會啟用真正的唯讀行為。</span><span class="sxs-lookup"><span data-stu-id="1854f-148">Read-only auto-properties enable true read-only behavior.</span></span> <span data-ttu-id="1854f-149">您只需要用 get 存取子宣告 Auto 屬性︰</span><span class="sxs-lookup"><span data-stu-id="1854f-149">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="1854f-150">`FirstName` 和 `LastName` 屬性只能在建構函式主體中設定︰</span><span class="sxs-lookup"><span data-stu-id="1854f-150">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="1854f-151">嘗試在另一個方法設定 `LastName` 會產生 `CS0200` 編譯錯誤︰</span><span class="sxs-lookup"><span data-stu-id="1854f-151">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

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

<span data-ttu-id="1854f-152">這項功能可真正達到建立不可變類型的語言支援，並使用更精簡且方便的 Auto 屬性語法。</span><span class="sxs-lookup"><span data-stu-id="1854f-152">This feature enables true language support for creating immutable types and using the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="1854f-153">如果新增這個語法不會移除可存取的方法，那麼這就是[二進位相容變更](version-update-considerations.md#binary-compatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="1854f-153">If adding this syntax does not not remove an accessible method, it is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

### <a name="auto-property-initializers"></a><span data-ttu-id="1854f-154">Auto 屬性初始設定式</span><span class="sxs-lookup"><span data-stu-id="1854f-154">Auto-Property Initializers</span></span>

<span data-ttu-id="1854f-155">「Auto 屬性初始設定式」可以讓您宣告 Auto 屬性的初始值作為屬性宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="1854f-155">*Auto-Property Initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>  <span data-ttu-id="1854f-156">在舊版中，這些屬性必須有 setter，且您必須使用該 setter 來初始化支援欄位所使用的資料存放區。</span><span class="sxs-lookup"><span data-stu-id="1854f-156">In earlier versions, these properties would need to have setters and you would need to use that setter to initialize the data storage used by the backing field.</span></span> <span data-ttu-id="1854f-157">請針對學生考慮此類別，其中包含學生的姓名和成績清單︰</span><span class="sxs-lookup"><span data-stu-id="1854f-157">Consider this class for a student that contains the name and a list of the student's grades:</span></span>

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
<span data-ttu-id="1854f-158">隨著這個類別成長，您可以包括其他建構函式。</span><span class="sxs-lookup"><span data-stu-id="1854f-158">As this class grows, you may include other constructors.</span></span> <span data-ttu-id="1854f-159">每個建構函式必須初始化這個欄位，否則您將會導致發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1854f-159">Each constructor needs to initialize this field, or you'll introduce errors.</span></span>

<span data-ttu-id="1854f-160">C# 6 可讓您在 Auto 屬性宣告中指派 Auto 屬性所使用的儲存體初始值︰</span><span class="sxs-lookup"><span data-stu-id="1854f-160">C# 6 enables you to assign an initial value for the storage used by an auto-property in the auto-property declaration:</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="1854f-161">`Grades` 成員會在宣告的位置初始化。</span><span class="sxs-lookup"><span data-stu-id="1854f-161">The `Grades` member is initialized where it is declared.</span></span> <span data-ttu-id="1854f-162">這可讓您更輕鬆地只執行初始化一次。</span><span class="sxs-lookup"><span data-stu-id="1854f-162">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="1854f-163">初始化是屬性宣告的一部分，如此能更容易讓儲存區配置與 `Student` 物件的公用介面相等。</span><span class="sxs-lookup"><span data-stu-id="1854f-163">The initialization is part of the property declaration, making it easier to equate the storage allocation with public interface for `Student` objects.</span></span>

<span data-ttu-id="1854f-164">屬性初始設定式可以與讀取/寫入屬性一起使用，也可以與唯讀屬性一起使用，如下所示。</span><span class="sxs-lookup"><span data-stu-id="1854f-164">Property Initializers can be used with read/write properties as well as read-only properties, as shown here.</span></span>

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a><span data-ttu-id="1854f-165">具有運算式主體的函式成員</span><span class="sxs-lookup"><span data-stu-id="1854f-165">Expression-bodied function members</span></span>

<span data-ttu-id="1854f-166">我們撰寫的很多成員主體只包含一個陳述式，它可以表示為運算式。</span><span class="sxs-lookup"><span data-stu-id="1854f-166">The body of a lot of members that we write consist of only one statement that can be represented as an expression.</span></span> <span data-ttu-id="1854f-167">您可以藉由改為撰寫運算式主體的成員，而減少該語法。</span><span class="sxs-lookup"><span data-stu-id="1854f-167">You can reduce that syntax by writing an expression-bodied member instead.</span></span> <span data-ttu-id="1854f-168">其適用於方法和唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="1854f-168">It works for methods and read-only properties.</span></span> <span data-ttu-id="1854f-169">例如，`ToString()` 覆寫通常是絕佳的候選︰</span><span class="sxs-lookup"><span data-stu-id="1854f-169">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="1854f-170">您也可以在唯讀屬性中使用運算式主體的成員︰</span><span class="sxs-lookup"><span data-stu-id="1854f-170">You can also use expression-bodied members in read-only properties as well:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="1854f-171">將現有成員變更為運算式主體成員是[二進位相容變更](version-update-considerations.md#binary-compatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="1854f-171">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>


## <a name="using-static"></a><span data-ttu-id="1854f-172">使用靜態</span><span class="sxs-lookup"><span data-stu-id="1854f-172">using static</span></span>

<span data-ttu-id="1854f-173">「使用靜態」增強功能可讓您匯入單一類別的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="1854f-173">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="1854f-174">先前，`using` 陳述式會匯入命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="1854f-174">Previously, the `using` statement imported all types in a namespace.</span></span> 

<span data-ttu-id="1854f-175">通常我們會在程式碼中到處使用類別的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="1854f-175">Often we use a class' static methods throughout our code.</span></span> <span data-ttu-id="1854f-176">重複輸入類別名稱，可能會混淆您的程式碼意義。</span><span class="sxs-lookup"><span data-stu-id="1854f-176">Repeatedly typing the class name can obscure the meaning of your code.</span></span> <span data-ttu-id="1854f-177">常見的範例是當您撰寫類別來執行許多數值計算時。</span><span class="sxs-lookup"><span data-stu-id="1854f-177">A common example is when you write classes that perform many numeric calculations.</span></span>
<span data-ttu-id="1854f-178">您的程式碼會散布著 <xref:System.Math.Sin%2A>、<xref:System.Math.Sqrt%2A> 和其他對 <xref:System.Math> 類別中不同方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="1854f-178">Your code will be littered with <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> and other calls to different methods in the <xref:System.Math> class.</span></span> <span data-ttu-id="1854f-179">新的 `using static` 語法可以讓這些類別容易讀取許多。</span><span class="sxs-lookup"><span data-stu-id="1854f-179">The new `using static` syntax can make these classes much cleaner to read.</span></span> <span data-ttu-id="1854f-180">您指定正在使用的類別︰</span><span class="sxs-lookup"><span data-stu-id="1854f-180">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="1854f-181">現在，您可以使用 <xref:System.Math> 類別中的任何靜態方法，而不需限定 <xref:System.Math> 類別。</span><span class="sxs-lookup"><span data-stu-id="1854f-181">And now, you can use any static method in the <xref:System.Math> class without qualifying the <xref:System.Math> class.</span></span> <span data-ttu-id="1854f-182"><xref:System.Math> 類別是這項功能很棒的使用案例，因為它不包含任何執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="1854f-182">The <xref:System.Math> class is a great use case for this feature because it does not contain any instance methods.</span></span> <span data-ttu-id="1854f-183">您也可以使用 `using static` 為同時具有靜態和執行個體方法的類別匯入類別的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="1854f-183">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="1854f-184">其中一個最有用的範例是 <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="1854f-184">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="1854f-185">您必須在靜態 using 陳述式中使用完整的類別名稱 `System.String`。</span><span class="sxs-lookup"><span data-stu-id="1854f-185">You must use the fully qualified class name, `System.String` in a static using statement.</span></span> <span data-ttu-id="1854f-186">不能改用 `string` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1854f-186">You cannot use the `string` keyword instead.</span></span> 

<span data-ttu-id="1854f-187">您現在可以呼叫 <xref:System.String> 類別中定義的靜態方法，而不需要將那些方法限定為該類別的成員︰</span><span class="sxs-lookup"><span data-stu-id="1854f-187">You can now call static methods defined in the <xref:System.String> class without qualifying those methods as members of that class:</span></span>

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

<span data-ttu-id="1854f-188">`static using` 功能和擴充方法會以有趣的方式互動，且語言設計包含了明確提供這些互動的一些規則。</span><span class="sxs-lookup"><span data-stu-id="1854f-188">The `static using` feature and extension methods interact in interesting ways, and the language design included some rules that specifically address those interactions.</span></span> <span data-ttu-id="1854f-189">目標是在包括您的現有程式碼基底中，將任何可能的重大變更減到最少。</span><span class="sxs-lookup"><span data-stu-id="1854f-189">The goal is to minimize any chances of breaking changes in existing codebases, including yours.</span></span>

<span data-ttu-id="1854f-190">擴充方法只有在使用擴充方法引動語法來呼叫時才會在範圍中，作為靜態方法來呼叫時則否。</span><span class="sxs-lookup"><span data-stu-id="1854f-190">Extension methods are only in scope when called using the extension method invocation syntax, not when called as a static method.</span></span>
<span data-ttu-id="1854f-191">您會經常在 LINQ 查詢中看到此情況。</span><span class="sxs-lookup"><span data-stu-id="1854f-191">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="1854f-192">您可以藉由匯入 <xref:System.Linq.Enumerable> 來匯入 LINQ 模式。</span><span class="sxs-lookup"><span data-stu-id="1854f-192">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="1854f-193">這樣會匯入 <xref:System.Linq.Enumerable> 類別中的所有方法。</span><span class="sxs-lookup"><span data-stu-id="1854f-193">This imports all the methods in the <xref:System.Linq.Enumerable> class.</span></span>
<span data-ttu-id="1854f-194">不過，擴充方法只有在呼叫為擴充方法時才會在範圍中。</span><span class="sxs-lookup"><span data-stu-id="1854f-194">However, the extension methods are only in scope when called as extension methods.</span></span> <span data-ttu-id="1854f-195">如果使用靜態方法語法呼叫則不在範圍內︰</span><span class="sxs-lookup"><span data-stu-id="1854f-195">They are not in scope if they are called using the static method syntax:</span></span>

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

<span data-ttu-id="1854f-196">這項決策是因為擴充方法通常使用擴充方法引動運算式來呼叫。</span><span class="sxs-lookup"><span data-stu-id="1854f-196">This decision is because extension methods are typically called using extension method invocation expressions.</span></span> <span data-ttu-id="1854f-197">在少數情況下，它們是使用靜態方法呼叫語法來呼叫時，用於解決模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="1854f-197">In the rare case where they are called using the static method call syntax it is to resolve ambiguity.</span></span>
<span data-ttu-id="1854f-198">要求在引動過程中使用類別名稱，似乎是明智的做法。</span><span class="sxs-lookup"><span data-stu-id="1854f-198">Requiring the class name as part of the invocation seems wise.</span></span>

<span data-ttu-id="1854f-199">`static using` 有最後一項功能。</span><span class="sxs-lookup"><span data-stu-id="1854f-199">There's one last feature of `static using`.</span></span> <span data-ttu-id="1854f-200">`static using` 指示詞也會匯入任何巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="1854f-200">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="1854f-201">那讓您能參照任何巢狀型別而無限定性條件。</span><span class="sxs-lookup"><span data-stu-id="1854f-201">That enables you to reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="1854f-202">Null 條件運算子</span><span class="sxs-lookup"><span data-stu-id="1854f-202">Null-conditional operators</span></span>

<span data-ttu-id="1854f-203">Null 值會使程式碼變得複雜。</span><span class="sxs-lookup"><span data-stu-id="1854f-203">Null values complicate code.</span></span> <span data-ttu-id="1854f-204">您需要檢查變數的每次存取，以確保您不會為 `null` 取值。</span><span class="sxs-lookup"><span data-stu-id="1854f-204">You need to check every access of variables to ensure you are not dereferencing `null`.</span></span> <span data-ttu-id="1854f-205">「Null 條件運算子」讓這些檢查更容易且流暢。</span><span class="sxs-lookup"><span data-stu-id="1854f-205">The *null conditional operator* makes those checks much easier and fluid.</span></span>

<span data-ttu-id="1854f-206">只要將成員存取 `.` 取代為 `?.`：</span><span class="sxs-lookup"><span data-stu-id="1854f-206">Simply replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="1854f-207">在上述範例中，如果 person 物件為 `null`，變數 `first` 便會被指派 `null`。</span><span class="sxs-lookup"><span data-stu-id="1854f-207">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="1854f-208">否則，它會被指派 `FirstName` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1854f-208">Otherwise, it gets assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="1854f-209">最重要的是，`?.` 表示當 `person` 變數是 `null` 時，這行程式碼不會產生 `NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="1854f-209">Most importantly, the `?.` means that this line of code does not generate a `NullReferenceException` when the `person` variable is `null`.</span></span> <span data-ttu-id="1854f-210">相反地，它會進行最少運算並產生 `null`。</span><span class="sxs-lookup"><span data-stu-id="1854f-210">Instead, it short-circuits and produces `null`.</span></span>

<span data-ttu-id="1854f-211">另外，請注意，這個運算式會傳回 `string`，不論 `person` 的值為何。</span><span class="sxs-lookup"><span data-stu-id="1854f-211">Also, note that this expression returns a `string`, regardless of the value of `person`.</span></span>
<span data-ttu-id="1854f-212">在最少運算的情況下，傳回的 `null` 值型別會改變以符合完整的運算式。</span><span class="sxs-lookup"><span data-stu-id="1854f-212">In the case of short circuiting, the `null` value returned is typed to match the full expression.</span></span>

<span data-ttu-id="1854f-213">您可以經常將這個建構與「null 聯合」運算子一起使用，以在其中一個屬性為 `null` 時指派預設值：</span><span class="sxs-lookup"><span data-stu-id="1854f-213">You can often use this construct with the *null coalescing* operator to assign default values when one of the properties are `null`:</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="1854f-214">`?.` 運算子右側的運算元不限於屬性或欄位。</span><span class="sxs-lookup"><span data-stu-id="1854f-214">The right hand side operand of the `?.` operator is not limited to properties or fields.</span></span>
<span data-ttu-id="1854f-215">您也可以使用它來條件式地叫用方法。</span><span class="sxs-lookup"><span data-stu-id="1854f-215">You can also use it to conditionally invoke methods.</span></span> <span data-ttu-id="1854f-216">最常見的成員函數與 Null 條件運算子使用，是安全地叫用可能為 `null` 的委派 (或事件處理常式)。</span><span class="sxs-lookup"><span data-stu-id="1854f-216">The most common use of member functions with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="1854f-217">做法是藉由呼叫委派的 `Invoke` 方法，並使用 `?.` 運算子來存取成員。</span><span class="sxs-lookup"><span data-stu-id="1854f-217">You'll do this by calling the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="1854f-218">如需範例，可參閱</span><span class="sxs-lookup"><span data-stu-id="1854f-218">You can see an example in the</span></span>  
<span data-ttu-id="1854f-219">[委派模式](../delegates-patterns.md#handling-null-delegates)主題。</span><span class="sxs-lookup"><span data-stu-id="1854f-219">[delegate patterns](../delegates-patterns.md#handling-null-delegates) topic.</span></span>

<span data-ttu-id="1854f-220">`?.` 運算子的規則確保運算子的左邊只會評估一次。</span><span class="sxs-lookup"><span data-stu-id="1854f-220">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="1854f-221">這很重要，並且可以啟用許多慣用句，包括使用事件處理常式的範例。</span><span class="sxs-lookup"><span data-stu-id="1854f-221">This is important and enables many idioms, including the example using event handlers.</span></span> <span data-ttu-id="1854f-222">讓我們從事件處理常式用法開始。</span><span class="sxs-lookup"><span data-stu-id="1854f-222">Let's start with the event handler usage.</span></span> <span data-ttu-id="1854f-223">在舊版的 C# 中，我們鼓勵您撰寫如下的程式碼︰</span><span class="sxs-lookup"><span data-stu-id="1854f-223">In previous versions of C#, you were encouraged to write code like this:</span></span>

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

<span data-ttu-id="1854f-224">這比起較簡單的語法而言更為慣用︰</span><span class="sxs-lookup"><span data-stu-id="1854f-224">This was preferred over a simpler syntax:</span></span>

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> <span data-ttu-id="1854f-225">上述範例中介紹競爭條件。</span><span class="sxs-lookup"><span data-stu-id="1854f-225">The preceding example introduces a race condition.</span></span> <span data-ttu-id="1854f-226">`SomethingHappened` 事件可能在核對 `null` 時有訂閱者，而且這些訂閱者可能在引發事件之前便已被移除。</span><span class="sxs-lookup"><span data-stu-id="1854f-226">The `SomethingHappened` event may have subscribers when checked against `null`, and those subscribers may have been removed before the event is raised.</span></span> <span data-ttu-id="1854f-227">那會導致擲回 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="1854f-227">That would cause a <xref:System.NullReferenceException> to be thrown.</span></span>

<span data-ttu-id="1854f-228">在第二個版本中，`SomethingHappened` 事件處理常式可能在測試時為非 Null，但如果其他程式碼移除處理常式，它仍可能在呼叫事件處理常式時為 Null。</span><span class="sxs-lookup"><span data-stu-id="1854f-228">In this second version, the `SomethingHappened` event handler might be non-null when tested, but if other code removes a handler, it could still be null when the event handler was called.</span></span>

<span data-ttu-id="1854f-229">編譯器會為 `?.` 運算子產生程式碼，確保 `?.` 運算式的左邊 (`this.SomethingHappened`) 只會評估一次，而且結果會加以快取︰</span><span class="sxs-lookup"><span data-stu-id="1854f-229">The compiler generates code for the `?.` operator that ensures the left side (`this.SomethingHappened`) of the `?.` expression is evaluated once, and the result is cached:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="1854f-230">確保左邊只評估一次也可讓您對 `?.` 的左邊使用任何運算式，包括方法呼叫。即使有副作用，它們只會評估一次，因此副作用只會發生一次。</span><span class="sxs-lookup"><span data-stu-id="1854f-230">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.` Even if these have side-effects, they are evaluated once, so the side effects occur only once.</span></span> <span data-ttu-id="1854f-231">您可以在我們的內容看到關於[事件](../events-overview.md#language-support-for-events)的範例。</span><span class="sxs-lookup"><span data-stu-id="1854f-231">You can see an example in our content on [events](../events-overview.md#language-support-for-events).</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="1854f-232">字串插值</span><span class="sxs-lookup"><span data-stu-id="1854f-232">String Interpolation</span></span>

<span data-ttu-id="1854f-233">C# 6 包含新的語法，其可從格式字串和可評估的運算式撰寫字串，以產生其他字串值。</span><span class="sxs-lookup"><span data-stu-id="1854f-233">C# 6 contains new syntax for composing strings from a format string and expressions that are evaluated to produce other string values.</span></span>

<span data-ttu-id="1854f-234">傳統上，您需要在像是 `string.Format` 的方法中使用位置參數：</span><span class="sxs-lookup"><span data-stu-id="1854f-234">Traditionally, you needed to use positional parameters in a method like `string.Format`:</span></span>

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

<span data-ttu-id="1854f-235">使用 C# 6，新的[字串內插補點](../language-reference/tokens/interpolated.md)功能可讓您將運算式內嵌在格式字串中。</span><span class="sxs-lookup"><span data-stu-id="1854f-235">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed the expressions in the format string.</span></span> <span data-ttu-id="1854f-236">只要在字串開頭加上 `$`：</span><span class="sxs-lookup"><span data-stu-id="1854f-236">Simply preface the string with `$`:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="1854f-237">這個最初範例將屬性運算式用於替代的運算式。</span><span class="sxs-lookup"><span data-stu-id="1854f-237">This initial example uses property expressions for the substituted expressions.</span></span> <span data-ttu-id="1854f-238">您可以展開此語法，即能使用任何運算式。</span><span class="sxs-lookup"><span data-stu-id="1854f-238">You can expand on this syntax to use any expression.</span></span> <span data-ttu-id="1854f-239">比方說，您可能在內插補點的過程中計算某學生的平均成積點︰</span><span class="sxs-lookup"><span data-stu-id="1854f-239">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

<span data-ttu-id="1854f-240">執行上述範例時，您會發現，`Grades.Average()` 的輸出小數位數可能會超出您想要的位數。</span><span class="sxs-lookup"><span data-stu-id="1854f-240">Running the preceding example, you would find that the output for `Grades.Average()` might have more decimal places than you would like.</span></span> <span data-ttu-id="1854f-241">字串內插補點語法支援使用稍早格式化方法時可用的所有格式字串。</span><span class="sxs-lookup"><span data-stu-id="1854f-241">The string interpolation syntax supports all the format strings available using earlier formatting methods.</span></span> <span data-ttu-id="1854f-242">您在大括弧內新增了格式字串。</span><span class="sxs-lookup"><span data-stu-id="1854f-242">You add the format strings inside the braces.</span></span> <span data-ttu-id="1854f-243">在運算式之後新增 `:` 以格式化︰</span><span class="sxs-lookup"><span data-stu-id="1854f-243">Add a `:` following the expression to format:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="1854f-244">前一行程式碼會將 `Grades.Average()` 的值格式化為具有兩個小數位數的浮點數。</span><span class="sxs-lookup"><span data-stu-id="1854f-244">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="1854f-245">`:` 一律會解譯為格式化運算式與格式字串之間的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="1854f-245">The `:` is always interpreted as the separator between the expression being formatted and the format string.</span></span> <span data-ttu-id="1854f-246">當您的運算式以另一種方式使用 `:` 時，例如條件運算子，這會導致問題︰</span><span class="sxs-lookup"><span data-stu-id="1854f-246">This can introduce problems when your expression uses a `:` in another way, such as a conditional operator:</span></span>

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

<span data-ttu-id="1854f-247">在上述範例中，`:` 剖析為格式字串的開頭，而不是條件運算子的一部分。</span><span class="sxs-lookup"><span data-stu-id="1854f-247">In the preceding example, the `:` is parsed as the beginning of the format string, not part of the conditional operator.</span></span> <span data-ttu-id="1854f-248">在發生這種情況的所有情況下，您可以將運算式圍上括弧，強制編譯器將運算式解譯如您的預期︰</span><span class="sxs-lookup"><span data-stu-id="1854f-248">In all cases where this happens, you can surround the expression with parentheses to force the compiler to interpret the expression as you intend:</span></span>

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

<span data-ttu-id="1854f-249">對於您可以放在大括弧之間的運算式沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="1854f-249">There aren't any limitations on the expressions you can place between the braces.</span></span> <span data-ttu-id="1854f-250">您可以在插入字串內執行複雜的 LINQ 查詢，來執行計算並顯示結果︰</span><span class="sxs-lookup"><span data-stu-id="1854f-250">You can execute a complex LINQ query inside an interpolated string to perform computations and display the result:</span></span>

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

<span data-ttu-id="1854f-251">您可以從此範例看到，您甚至可以將字串內插補點運算式巢狀放入另一個字串內插補點運算式內。</span><span class="sxs-lookup"><span data-stu-id="1854f-251">You can see from this sample that you can even nest a string interpolation expression inside another string interpolation expression.</span></span> <span data-ttu-id="1854f-252">這個範例很有可能比您想要用在實際執行程式碼的更複雜。</span><span class="sxs-lookup"><span data-stu-id="1854f-252">This example is very likely more complex than you would want in production code.</span></span>
<span data-ttu-id="1854f-253">但是，它能夠描述功能的廣度。</span><span class="sxs-lookup"><span data-stu-id="1854f-253">Rather, it is illustrative of the breadth of the feature.</span></span> <span data-ttu-id="1854f-254">任何 C# 運算式都可以放在插入字串的大括號之間。</span><span class="sxs-lookup"><span data-stu-id="1854f-254">Any C# expression can be placed between the curly braces of an interpolated string.</span></span>

### <a name="string-interpolation-and-specific-cultures"></a><span data-ttu-id="1854f-255">字串內插補點和特定文化特性</span><span class="sxs-lookup"><span data-stu-id="1854f-255">String interpolation and specific cultures</span></span>

<span data-ttu-id="1854f-256">所有在上一節中顯示的範例將會使用程式碼執行所在電腦上的目前文化特性和語言來格式化字串。</span><span class="sxs-lookup"><span data-stu-id="1854f-256">All the examples shown in the preceding section format the strings using the current culture and language on the machine where the code executes.</span></span> <span data-ttu-id="1854f-257">通常，您可能需要格式化使用特定文化特性產生的字串。</span><span class="sxs-lookup"><span data-stu-id="1854f-257">Often you may need to format the string produced using a specific culture.</span></span>
<span data-ttu-id="1854f-258">若要那麼做，請使用物件依可隱含轉換至 <xref:System.FormattableString> 之字串內插補點所產生的事實。</span><span class="sxs-lookup"><span data-stu-id="1854f-258">To do that use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString>.</span></span>

<span data-ttu-id="1854f-259"><xref:System.FormattableString> 執行個體包含格式字串，以及在將其轉換為字串之前，評估運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="1854f-259">The <xref:System.FormattableString> instance contains the format string, and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="1854f-260">您可以使用 <xref:System.FormattableString> 的公用方法指定格式化字串時的文化特性。</span><span class="sxs-lookup"><span data-stu-id="1854f-260">You can use public methods of <xref:System.FormattableString> to specify the culture when formatting a string.</span></span> <span data-ttu-id="1854f-261">例如，下列範例會使用德國文化特性產生字串。</span><span class="sxs-lookup"><span data-stu-id="1854f-261">For example, the following example produces a string using German culture.</span></span> <span data-ttu-id="1854f-262">(其會使用 ',' 字元作為十進位分隔符號，並使用 '. ' 字元作為千位分隔符號。)</span><span class="sxs-lookup"><span data-stu-id="1854f-262">(It uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="1854f-263">如需詳細資訊，請參閱[字串內插補點](../language-reference/tokens/interpolated.md)主題。</span><span class="sxs-lookup"><span data-stu-id="1854f-263">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="1854f-264">例外狀況篩選條件</span><span class="sxs-lookup"><span data-stu-id="1854f-264">Exception Filters</span></span>

<span data-ttu-id="1854f-265">C# 6 的另一個新功能是「例外狀況篩選條件」。</span><span class="sxs-lookup"><span data-stu-id="1854f-265">Another new feature in C# 6 is *exception filters*.</span></span> <span data-ttu-id="1854f-266">例外狀況篩選條件是判斷指定 catch 子句何時應該套用的子句。</span><span class="sxs-lookup"><span data-stu-id="1854f-266">Exception Filters are clauses that determine when a given catch clause should be applied.</span></span>
<span data-ttu-id="1854f-267">如果例外狀況篩選條件所用的運算式評估為 `true`，catch 子句便會對例外狀況執行其一般處理。</span><span class="sxs-lookup"><span data-stu-id="1854f-267">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="1854f-268">如果運算式評估為 `false`，則會略過 `catch` 子句。</span><span class="sxs-lookup"><span data-stu-id="1854f-268">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span>

<span data-ttu-id="1854f-269">用法之一是檢查例外狀況的相關資訊，以判斷 `catch` 子句是否可以處理例外狀況︰</span><span class="sxs-lookup"><span data-stu-id="1854f-269">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

<span data-ttu-id="1854f-270">例外狀況篩選條件產生的程式碼會提供關於擲回且未處理之例外狀況的更詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1854f-270">The code generated by exception filters provides better information about an exception that is thrown and not processed.</span></span> <span data-ttu-id="1854f-271">在例外狀況篩選條件新增至語言之前，您需要建立程式碼，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="1854f-271">Before exception filters were added to the language, you would need to create code like the following:</span></span>

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

<span data-ttu-id="1854f-272">在這兩個範例之間，例外狀況擲回點會變更。</span><span class="sxs-lookup"><span data-stu-id="1854f-272">The point where the exception is thrown changes between these two examples.</span></span>
<span data-ttu-id="1854f-273">在先前的程式碼，使用了 `throw` 子句，任何堆疊追蹤分析或損毀傾印的檢查將會顯示已從 catch 子句中的 `throw` 陳述式擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1854f-273">In the previous code, where a `throw` clause is used, any stack trace analysis or examination of crash dumps will show that the exception was thrown from the `throw` statement in your catch clause.</span></span> <span data-ttu-id="1854f-274">實際的例外狀況物件會包含原始呼叫堆疊，但在此擲回點與原始擲回點位置之間的呼叫堆疊中的任何變數所有其他相關資訊都已遺失。</span><span class="sxs-lookup"><span data-stu-id="1854f-274">The actual exception object will contain the original call stack, but all other information about any variables in the call stack between this throw point and the location of the original throw point has been lost.</span></span> 

<span data-ttu-id="1854f-275">與使用例外狀況篩選條件之程式碼的處理方式相反︰例外狀況篩選條件運算式會評估為 `false`。</span><span class="sxs-lookup"><span data-stu-id="1854f-275">Contrast that with how the code using an exception filter is processed: the exception filter expression evaluates to `false`.</span></span> <span data-ttu-id="1854f-276">因此，執行永遠不會進入 `catch` 子句。</span><span class="sxs-lookup"><span data-stu-id="1854f-276">Therefore, execution never enters the `catch` clause.</span></span> <span data-ttu-id="1854f-277">因為 `catch` 子句不會執行，所以不會發生堆疊回溯的情形。</span><span class="sxs-lookup"><span data-stu-id="1854f-277">Because the `catch` clause does not execute, no stack unwinding takes place.</span></span> <span data-ttu-id="1854f-278">那表示原始擲回位置會被保留給之後發生的任何偵錯活動。</span><span class="sxs-lookup"><span data-stu-id="1854f-278">That means the original throw location is preserved for any debugging activities that would take place later.</span></span>

<span data-ttu-id="1854f-279">每當您需要評估例外狀況的欄位或屬性時，請不要只依賴例外狀況類型，而是使用例外狀況篩選條件來保留偵錯的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1854f-279">Whenever you need to evaluate fields or properties of an exception, instead of relying solely on the exception type, use an exception filter to preserve more debugging information.</span></span>

<span data-ttu-id="1854f-280">例外狀況篩選條件的另一個建議模式是用於記錄的常式。</span><span class="sxs-lookup"><span data-stu-id="1854f-280">Another recommended pattern with exception filters is to use them for logging routines.</span></span> <span data-ttu-id="1854f-281">這種使用方式也會充分利用在例外狀況篩選條件評估為 `false` 時，例外狀況擲回點的保留方式。</span><span class="sxs-lookup"><span data-stu-id="1854f-281">This usage also leverages the manner in which the exception throw point is preserved when an exception filter evaluates to `false`.</span></span>

<span data-ttu-id="1854f-282">記錄方法的引數為無條件地傳回 `false` 的例外狀況：</span><span class="sxs-lookup"><span data-stu-id="1854f-282">A logging method would be a method whose argument is the exception that unconditionally returns `false`:</span></span>

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

<span data-ttu-id="1854f-283">每當您想要記錄例外狀況時，可以新增 catch 子句，並使用這個方法作為例外狀況篩選條件︰</span><span class="sxs-lookup"><span data-stu-id="1854f-283">Whenever you want to log an exception, you can add a catch clause, and use this method as the exception filter:</span></span>

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

<span data-ttu-id="1854f-284">例外狀況永遠不會被攔截，因為 `LogException` 方法一律會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="1854f-284">The exceptions are never caught, because the `LogException` method always returns `false`.</span></span> <span data-ttu-id="1854f-285">永遠為 false 的例外狀況篩選條件，表示您可以將此記錄處理常式放在任何其他例外狀況處理常式之前︰</span><span class="sxs-lookup"><span data-stu-id="1854f-285">That always false exception filter means that you can place this logging handler before any other exception handlers:</span></span>

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

<span data-ttu-id="1854f-286">上述範例中強調例外狀況篩選條件的一個非常重要的層面。</span><span class="sxs-lookup"><span data-stu-id="1854f-286">The preceding example highlights a very important facet of exception filters.</span></span>
<span data-ttu-id="1854f-287">例外狀況篩選條件讓較一般的例外狀況 catch 子句能夠出現在較特定的例外狀況 catch 子句之前。</span><span class="sxs-lookup"><span data-stu-id="1854f-287">The exception filters enable scenarios where a more general exception catch clause may appear before a more specific one.</span></span> <span data-ttu-id="1854f-288">此外，也可以讓相同的例外狀況類型出現在多個 catch 子句︰</span><span class="sxs-lookup"><span data-stu-id="1854f-288">It's also possible to have the same exception type appear in multiple catch clauses:</span></span>

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

<span data-ttu-id="1854f-289">另一種建議的模式有助於避免 catch 子句在附加偵錯工具時，處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1854f-289">Another recommended pattern helps prevent catch clauses from processing exceptions when a debugger is attached.</span></span> <span data-ttu-id="1854f-290">這項技術可讓您執行應用程式及偵錯工具，並在擲回例外狀況時停止執行。</span><span class="sxs-lookup"><span data-stu-id="1854f-290">This technique enables you to run an application with the debugger, and stop execution when an exception is thrown.</span></span>

<span data-ttu-id="1854f-291">在您的程式碼中，新增例外狀況篩選條件，使得只有在未附加偵錯工具時，才會執行任何復原程式碼︰</span><span class="sxs-lookup"><span data-stu-id="1854f-291">In your code, add an exception filter so that any recovery code executes only when a debugger is not attached:</span></span>

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

<span data-ttu-id="1854f-292">在程式碼中新增這項之後，您可以設定偵錯工具以在所有未處理的例外狀況處中斷。</span><span class="sxs-lookup"><span data-stu-id="1854f-292">After adding this in code, you set your debugger to break on all unhandled exceptions.</span></span> <span data-ttu-id="1854f-293">在偵錯工具中執行程式，偵錯工具會在 `PerformFailingOperation()` 擲回 `RecoverableException` 時便中斷。</span><span class="sxs-lookup"><span data-stu-id="1854f-293">Run the program under the debugger, and the debugger breaks whenever `PerformFailingOperation()` throws a `RecoverableException`.</span></span>
<span data-ttu-id="1854f-294">偵錯工具會中斷您的程式，因為 catch 子句不會執行，因為例外狀況篩選條件傳回 false。</span><span class="sxs-lookup"><span data-stu-id="1854f-294">The debugger breaks your program, because the catch clause won't be executed due to the false-returning exception filter.</span></span>

## <a name="nameof-expressions"></a><span data-ttu-id="1854f-295">`nameof` 運算式</span><span class="sxs-lookup"><span data-stu-id="1854f-295">`nameof` Expressions</span></span>

<span data-ttu-id="1854f-296">`nameof` 運算式評估為符號的名稱。</span><span class="sxs-lookup"><span data-stu-id="1854f-296">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="1854f-297">每當您需要變數、屬性或成員欄位的名稱時，這是讓工具能運作的好方法。</span><span class="sxs-lookup"><span data-stu-id="1854f-297">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span>

<span data-ttu-id="1854f-298">`nameof` 最常見的其中一個用途是提供造成例外狀況的符號名稱︰</span><span class="sxs-lookup"><span data-stu-id="1854f-298">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="1854f-299">另一個用途是實作 `INotifyPropertyChanged` 介面的 XAML 應用程式︰</span><span class="sxs-lookup"><span data-stu-id="1854f-299">Another use is with XAML based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

<span data-ttu-id="1854f-300">使用 `nameof` 運算子相較於常數字串而言的優點，是工具可以了解符號。</span><span class="sxs-lookup"><span data-stu-id="1854f-300">The advantage of using the `nameof` operator over a constant string is that tools can understand the symbol.</span></span> <span data-ttu-id="1854f-301">如果您使用重整工具來重新命名符號，它會在 `nameof` 運算式中將它重新命名。</span><span class="sxs-lookup"><span data-stu-id="1854f-301">If you use refactoring tools to rename the symbol, it will rename it in the `nameof` expression.</span></span> <span data-ttu-id="1854f-302">常數字串沒有這項優點。</span><span class="sxs-lookup"><span data-stu-id="1854f-302">Constant strings don't have that advantage.</span></span> <span data-ttu-id="1854f-303">您可以在喜好的編輯器中自行嘗試︰重新命名變數，任何 `nameof` 運算式將會一併更新。</span><span class="sxs-lookup"><span data-stu-id="1854f-303">Try it yourself in your favorite editor: rename a variable, and any `nameof` expressions will update as well.</span></span>

<span data-ttu-id="1854f-304">`nameof` 運算式會產生其引數的非限定名稱 (上述範例中的 `LastName`)，即使您使用引數的完整格式名稱︰</span><span class="sxs-lookup"><span data-stu-id="1854f-304">The `nameof` expression produces the unqualified name of its argument (`LastName` in the previous examples) even if you use the fully qualified name for the argument:</span></span>

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

<span data-ttu-id="1854f-305">這個 `nameof` 運算式會產生 `FirstName`，而非 `UXComponents.ViewModel.FirstName`。</span><span class="sxs-lookup"><span data-stu-id="1854f-305">This `nameof` expression produces `FirstName`, not `UXComponents.ViewModel.FirstName`.</span></span>

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="1854f-306">Catch 和 Finally 區塊中的 Await</span><span class="sxs-lookup"><span data-stu-id="1854f-306">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="1854f-307">C# 5 對於您可以放置 `await` 運算式的位置有數個限制。</span><span class="sxs-lookup"><span data-stu-id="1854f-307">C# 5 had several limitations around where you could place `await` expressions.</span></span>
<span data-ttu-id="1854f-308">其中一個在 C# 6 中已移除。</span><span class="sxs-lookup"><span data-stu-id="1854f-308">One of those has been removed in C# 6.</span></span> <span data-ttu-id="1854f-309">您現在可以在 `catch` 或 `finally` 運算式中使用 `await`。</span><span class="sxs-lookup"><span data-stu-id="1854f-309">You can now use `await` in `catch` or `finally` expressions.</span></span> 

<span data-ttu-id="1854f-310">在 catch 和 finally 區塊中新增 await 運算式可能會讓這些的處理方式變複雜。</span><span class="sxs-lookup"><span data-stu-id="1854f-310">The addition of await expressions in catch and finally blocks may appear to complicate how those are processed.</span></span> <span data-ttu-id="1854f-311">讓我們新增一個範例討論這會如何。</span><span class="sxs-lookup"><span data-stu-id="1854f-311">Let's add an example to discuss how this appears.</span></span> <span data-ttu-id="1854f-312">在任何非同步方法中，您可以在 finally 子句使用 await 運算式。</span><span class="sxs-lookup"><span data-stu-id="1854f-312">In any async method, you can use an await expression in a finally clause.</span></span>

<span data-ttu-id="1854f-313">使用 C# 6，您也可以在 catch 運算式中使用 await。</span><span class="sxs-lookup"><span data-stu-id="1854f-313">With C# 6, you can also await in catch expressions.</span></span> <span data-ttu-id="1854f-314">這最常用於記錄情節︰</span><span class="sxs-lookup"><span data-stu-id="1854f-314">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="1854f-315">在 `catch` 和 `finally` 子句內新增 `await` 支援的實作詳細資料，可確保行為與同步程式碼的行為一致。</span><span class="sxs-lookup"><span data-stu-id="1854f-315">The implementation details for adding `await` support inside `catch` and `finally` clauses ensures that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="1854f-316">當 `catch` 或 `finally` 子句中執行的程式碼擲回時，執行會在下個周圍區塊中尋找適合的 `catch` 子句。</span><span class="sxs-lookup"><span data-stu-id="1854f-316">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="1854f-317">如果有目前的例外狀況，該例外狀況將會遺失。</span><span class="sxs-lookup"><span data-stu-id="1854f-317">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="1854f-318">`catch` 和 `finally` 子 句中等候的運算式也會發生相同的情況︰搜尋適合的 `catch`，目前的例外狀況 (如果有的話) 將會遺失。</span><span class="sxs-lookup"><span data-stu-id="1854f-318">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="1854f-319">此行為是建議您小心撰寫 `catch` 和 `finally` 子句的原因，以避免產生新的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1854f-319">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="index-initializers"></a><span data-ttu-id="1854f-320">索引初始設定式</span><span class="sxs-lookup"><span data-stu-id="1854f-320">Index Initializers</span></span>

<span data-ttu-id="1854f-321">「索引初始設定式」是讓集合初始設定式與索引使用方式更一致的兩個功能之一。</span><span class="sxs-lookup"><span data-stu-id="1854f-321">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="1854f-322">在舊版的 C# 中，您可以只搭配序列樣式集合來使用「集合初始設定式」，包括在索引鍵值/組前後加上大括號的 <xref:System.Collections.Generic.Dictionary%602>：</span><span class="sxs-lookup"><span data-stu-id="1854f-322">In earlier releases of C#, you could use *collection initializers* only with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602> by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

<span data-ttu-id="1854f-323">現在，您可以使用它們來搭配 <xref:System.Collections.Generic.Dictionary%602> 集合與類似的型別。</span><span class="sxs-lookup"><span data-stu-id="1854f-323">Now, you can use them with <xref:System.Collections.Generic.Dictionary%602> collections and similar types.</span></span> <span data-ttu-id="1854f-324">新的語法支援使用集合中的索引進行指派：</span><span class="sxs-lookup"><span data-stu-id="1854f-324">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="1854f-325">這項功能表示可以使用類似於已可供數個版本的序列容器使用的語法，將關聯容器初始化。</span><span class="sxs-lookup"><span data-stu-id="1854f-325">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="1854f-326">集合初始設定式中的擴充 `Add` 方法</span><span class="sxs-lookup"><span data-stu-id="1854f-326">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="1854f-327">能夠輕鬆進行集合初始設定的另一個功能，是可以針對 `Add` 方法使用「擴充方法」。</span><span class="sxs-lookup"><span data-stu-id="1854f-327">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="1854f-328">新增這項功能是為了與 Visual Basic 相當。</span><span class="sxs-lookup"><span data-stu-id="1854f-328">This feature was added for parity with Visual Basic.</span></span> 

<span data-ttu-id="1854f-329">當您的自訂集合類別具有不同名稱的方法，可以在語意上新增項目時，此功能最實用。</span><span class="sxs-lookup"><span data-stu-id="1854f-329">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

<span data-ttu-id="1854f-330">比方說，請考慮如下的學生集合︰</span><span class="sxs-lookup"><span data-stu-id="1854f-330">For example, consider a collection of students like this:</span></span>

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

<span data-ttu-id="1854f-331">`Enroll` 方法會新增學生。</span><span class="sxs-lookup"><span data-stu-id="1854f-331">The `Enroll` method adds a student.</span></span> <span data-ttu-id="1854f-332">但它不是採用 `Add` 模式。</span><span class="sxs-lookup"><span data-stu-id="1854f-332">But it doesn't follow the `Add` pattern.</span></span>
<span data-ttu-id="1854f-333">在舊版的 C# 中，您無法使用集合初始設定式搭配 `Enrollment` 物件︰</span><span class="sxs-lookup"><span data-stu-id="1854f-333">In previous versions of C#, you could not use collection initializers with an `Enrollment` object:</span></span>

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

<span data-ttu-id="1854f-334">現在您可以，但是只有當您建立將 `Add` 對應至 `Enroll` 的擴充方法時：</span><span class="sxs-lookup"><span data-stu-id="1854f-334">Now you can, but only if you create an extension method that maps `Add` to `Enroll`:</span></span>

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

<span data-ttu-id="1854f-335">您使用這項功能做的事，是藉由建立擴充方法，將任何新增項目到集合的方法對應至名為 `Add` 的方法。</span><span class="sxs-lookup"><span data-stu-id="1854f-335">What you are doing with this feature is to map whatever method adds items to a collection to a method named `Add` by creating an extension method.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="1854f-336">改進的多載解析</span><span class="sxs-lookup"><span data-stu-id="1854f-336">Improved overload resolution</span></span>

<span data-ttu-id="1854f-337">您可能不會發現最後這項功能。</span><span class="sxs-lookup"><span data-stu-id="1854f-337">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="1854f-338">在有些建構中，舊版 C# 編譯器可能會發現一些涉及 Lambda 運算式的方法呼叫為模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="1854f-338">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="1854f-339">請參考下列方法：</span><span class="sxs-lookup"><span data-stu-id="1854f-339">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="1854f-340">在舊版的 C# 中，使用方法群組語法呼叫該方法會失敗︰</span><span class="sxs-lookup"><span data-stu-id="1854f-340">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
<span data-ttu-id="1854f-341">舊版的編譯器無法正確分辨 `Task.Run(Action)` 和 `Task.Run(Func<Task>())`。</span><span class="sxs-lookup"><span data-stu-id="1854f-341">The earlier compiler could not distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="1854f-342">在舊版中，您必須使用 Lambda 運算式作為引數︰</span><span class="sxs-lookup"><span data-stu-id="1854f-342">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="1854f-343">C# 6 編譯器可正確判斷 `Task.Run(Func<Task>())` 是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="1854f-343">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="1854f-344">deterministic 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="1854f-344">Deterministic compiler output</span></span>

<span data-ttu-id="1854f-345">`-deterministic` 選項會指示編譯器針對相同原始程式檔 的後續編譯產生位元組對位元組的相同輸出組件。</span><span class="sxs-lookup"><span data-stu-id="1854f-345">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="1854f-346">根據預設，每次編譯會針對每次編譯產生唯一的輸出。</span><span class="sxs-lookup"><span data-stu-id="1854f-346">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="1854f-347">編譯器會新增時間戳記，以及從亂數產生的 GUID。</span><span class="sxs-lookup"><span data-stu-id="1854f-347">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="1854f-348">如果您想要比較位元組對位元組的輸出，以確保組建的一致性，您可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="1854f-348">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="1854f-349">如需詳細資訊，請參閱 [-deterministic 編譯器選項](../language-reference/compiler-options/deterministic-compiler-option.md)文章。</span><span class="sxs-lookup"><span data-stu-id="1854f-349">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
