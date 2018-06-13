---
title: =&gt; 運算子 (C# 參考)
ms.date: 10/02/2017
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: d1565e262fbd3ebcee2d1576a2a0c8ed3ba8ce38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288222"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="66300-102">=&gt; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="66300-102">=&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="66300-103">`=>` 運算子在 C# 中有兩種用法：</span><span class="sxs-lookup"><span data-stu-id="66300-103">The `=>` operator can be used in two ways in C#:</span></span>

- <span data-ttu-id="66300-104">作為 [Lambda 運算式](../../lambda-expressions.md)中的 [Lambda 運算子](#lamba-operator)，它會分開輸入變數與 Lambda 主體。</span><span class="sxs-lookup"><span data-stu-id="66300-104">As the [lambda operator](#lamba-operator) in a [lambda expression](../../lambda-expressions.md), it separates the input variables from the lambda body.</span></span>
 
- <span data-ttu-id="66300-105">在[運算式主體定義](#expression-body-definition)中，它會分開成員名稱與成員實作。</span><span class="sxs-lookup"><span data-stu-id="66300-105">In an [expression body definition](#expression-body-definition), it separates a member name from the member implementation.</span></span> 

## <a name="lambda-operator"></a><span data-ttu-id="66300-106">Lambda 運算子</span><span class="sxs-lookup"><span data-stu-id="66300-106">Lambda operator</span></span>

<span data-ttu-id="66300-107">`=>` 語彙基元又稱為 Lambda 運算子。</span><span class="sxs-lookup"><span data-stu-id="66300-107">The `=>` token is called the lambda operator.</span></span> <span data-ttu-id="66300-108">它會在「Lambda 運算式」中使用，以分開右邊的 Lambda 主體和左邊的輸入變數。</span><span class="sxs-lookup"><span data-stu-id="66300-108">It is used in *lambda expressions* to separate the input variables on the left side from the lambda body on the right side.</span></span> <span data-ttu-id="66300-109">Lambda 運算式是類似匿名方法的內嵌運算式，但更有彈性；它會在以方法語法所表示的 LINQ 查詢中大量使用。</span><span class="sxs-lookup"><span data-stu-id="66300-109">Lambda expressions are inline expressions similar to anonymous methods but more flexible; they are used extensively in LINQ queries that are expressed in method syntax.</span></span> <span data-ttu-id="66300-110">如需詳細資訊，請參閱 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="66300-110">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="66300-111">下列範例顯示兩種方法來尋找及顯示字串陣列中最短字串的長度。</span><span class="sxs-lookup"><span data-stu-id="66300-111">The following example shows two ways to find and display the length of the shortest string in an array of strings.</span></span> <span data-ttu-id="66300-112">此範例的第一個部分會將 Lambda 運算式 (`w => w.Length`) 套用至 `words` 陣列的每個項目，然後使用 <xref:System.Linq.Enumerable.Min%2A> 方法來尋找最小長度。</span><span class="sxs-lookup"><span data-stu-id="66300-112">The first part of the example applies a lambda expression (`w => w.Length`) to each element of the `words` array and then uses the <xref:System.Linq.Enumerable.Min%2A> method to find the smallest length.</span></span> <span data-ttu-id="66300-113">相較之下，此範例的第二個部分會顯示使用查詢語法執行相同動作的較長方案。</span><span class="sxs-lookup"><span data-stu-id="66300-113">For comparison, the second part of the example shows a longer solution that uses query syntax to do the same thing.</span></span>  
  
```csharp  
string[] words = { "cherry", "apple", "blueberry" };  
  
// Use method syntax to apply a lambda expression to each element  
// of the words array.   
int shortestWordLength = words.Min(w => w.Length);  
Console.WriteLine(shortestWordLength);  
  
// Compare the following code that uses query syntax.  
// Get the lengths of each word in the words array.  
var query = from w in words  
            select w.Length;  
// Apply the Min method to execute the query and get the shortest length.  
int shortestWordLength2 = query.Min();  
Console.WriteLine(shortestWordLength2);  
  
// Output:   
// 5  
// 5  
```  
  
### <a name="remarks"></a><span data-ttu-id="66300-114">備註</span><span class="sxs-lookup"><span data-stu-id="66300-114">Remarks</span></span>  
 <span data-ttu-id="66300-115">`=>` 運算子與指派運算子 (`=`) 具有相同的優先順序，而且為右向關聯。</span><span class="sxs-lookup"><span data-stu-id="66300-115">The `=>` operator has the same precedence as the assignment operator (`=`) and is right-associative.</span></span>  
  
 <span data-ttu-id="66300-116">您可以明確指定輸入變數的類型，或讓編譯器推斷類型；不論是哪種情況，此變數在編譯時都屬於強型別。</span><span class="sxs-lookup"><span data-stu-id="66300-116">You can specify the type of the input variable explicitly or let the compiler infer it; in either case, the variable is strongly typed at compile time.</span></span> <span data-ttu-id="66300-117">當您指定類型時，您必須以括號括住類型名稱和變數名稱，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="66300-117">When you specify a type, you must enclose the type name and the variable name in parentheses, as the following example shows.</span></span>  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a><span data-ttu-id="66300-118">範例</span><span class="sxs-lookup"><span data-stu-id="66300-118">Example</span></span>  
 <span data-ttu-id="66300-119">下列範例示範如何為接受兩個引數之標準查詢運算子 <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> 的多載，撰寫 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="66300-119">The following example shows how to write a lambda expression for the overload of the standard query operator <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> that takes two arguments.</span></span> <span data-ttu-id="66300-120">因為 Lambda 運算式有多個參數，所以必須以括號括住這些參數。</span><span class="sxs-lookup"><span data-stu-id="66300-120">Because the lambda expression has more than one parameter, the parameters must be enclosed in parentheses.</span></span> <span data-ttu-id="66300-121">第二個參數 `index` 表示集合中目前項目的索引。</span><span class="sxs-lookup"><span data-stu-id="66300-121">The second parameter, `index`, represents the index of the current element in the collection.</span></span> <span data-ttu-id="66300-122">`Where` 運算式會傳回長度小於其陣列索引位置的所有字串。</span><span class="sxs-lookup"><span data-stu-id="66300-122">The `Where` expression returns all the strings whose lengths are less than their index positions in the array.</span></span>  
  
```csharp  
static void Main(string[] args)  
{  
    string[] digits = { "zero", "one", "two", "three", "four", "five",   
            "six", "seven", "eight", "nine" };  
  
    Console.WriteLine("Example that uses a lambda expression:");  
    var shortDigits = digits.Where((digit, index) => digit.Length < index);  
    foreach (var sD in shortDigits)  
    {  
        Console.WriteLine(sD);  
    }  
  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
## <a name="expression-body-definition"></a><span data-ttu-id="66300-123">運算式主體定義</span><span class="sxs-lookup"><span data-stu-id="66300-123">Expression body definition</span></span>

<span data-ttu-id="66300-124">運算式主體定義以極為簡潔且可讀的形式提供成員的實作。</span><span class="sxs-lookup"><span data-stu-id="66300-124">An expression body definition provides a member's implementation in a highly condensed, readable form.</span></span> <span data-ttu-id="66300-125">它有下列一般語法：</span><span class="sxs-lookup"><span data-stu-id="66300-125">It has the following general syntax:</span></span>

```csharp
member => expression;
```
<span data-ttu-id="66300-126">其中 *expression* 是有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="66300-126">where *expression* is a valid expression.</span></span> <span data-ttu-id="66300-127">請注意，只有在成員的傳回型別為 `void` 時，或成員為建構函式或完成項時，*expression* 才可以是「陳述式運算式」。</span><span class="sxs-lookup"><span data-stu-id="66300-127">Note that *expression* can be a *statement expression* only if the member's return type is `void`, or if the member is a constructor or a finalizer.</span></span>

<span data-ttu-id="66300-128">從 C# 6 開始支援方法和 property get 陳述式的運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="66300-128">Expression body definitions for methods and property get statements are supported starting with C# 6.</span></span> <span data-ttu-id="66300-129">從 C# 7 開始支援建構函式、完成項、property set 陳述式和索引子的運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="66300-129">Expression body definitions for constructors, finalizers, property set statements, and indexers are supported starting with C# 7.</span></span>

<span data-ttu-id="66300-130">`Person.ToString` 方法的運算式主體定義如下︰</span><span class="sxs-lookup"><span data-stu-id="66300-130">The following is an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="66300-131">它是下列方法定義的簡短版：</span><span class="sxs-lookup"><span data-stu-id="66300-131">It is a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
<span data-ttu-id="66300-132">如需運算式主體定義的詳細資訊，請參閱[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)。</span><span class="sxs-lookup"><span data-stu-id="66300-132">For more detailed information on expression body definitions, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="66300-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="66300-133">See Also</span></span>  
<span data-ttu-id="66300-134">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="66300-134">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="66300-135">[C# 程式設計指南](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="66300-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="66300-136">[Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="66300-136">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span></span>  
<span data-ttu-id="66300-137">[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)。</span><span class="sxs-lookup"><span data-stu-id="66300-137">[Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>