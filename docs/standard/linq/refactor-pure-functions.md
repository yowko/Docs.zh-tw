---
title: 重構為純虛擬函式-LINQ to XML
description: 瞭解純虛擬函式，以及如何使用它們來重構程式碼。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 18418a1fc39bee9f08cbe92d42c842e3fc9e148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552784"
---
# <a name="refactor-into-pure-functions-linq-to-xml"></a><span data-ttu-id="26076-103">重構為純虛擬函式 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="26076-103">Refactor into pure functions (LINQ to XML)</span></span>

<span data-ttu-id="26076-104">純功能性轉換的重要觀點為學習如何使用純虛擬函式重構程式碼。</span><span class="sxs-lookup"><span data-stu-id="26076-104">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>

> [!NOTE]
> <span data-ttu-id="26076-105">功能性程式設計的常見命名法為使用純虛擬函式重構程式。</span><span class="sxs-lookup"><span data-stu-id="26076-105">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="26076-106">在 Visual Basic 和 C++ 中，這可以利用個別的語言，調整函式的用法。</span><span class="sxs-lookup"><span data-stu-id="26076-106">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="26076-107">不過，在 C# 中，函式稱為方法。</span><span class="sxs-lookup"><span data-stu-id="26076-107">However, in C#, functions are called methods.</span></span> <span data-ttu-id="26076-108">就這個討論而言，純虛擬函式會當成 C# 中的方法實作。</span><span class="sxs-lookup"><span data-stu-id="26076-108">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>

<span data-ttu-id="26076-109">如同本節先前所述，純虛擬函式擁有兩個實用的特性：</span><span class="sxs-lookup"><span data-stu-id="26076-109">As noted previously in this section, a pure function has two useful characteristics:</span></span>

- <span data-ttu-id="26076-110">它有沒有副作用。</span><span class="sxs-lookup"><span data-stu-id="26076-110">It has no side effects.</span></span> <span data-ttu-id="26076-111">函式不會變更函數以外任何類型的任何變數或資料。</span><span class="sxs-lookup"><span data-stu-id="26076-111">The function doesn't change any variables or the data of any type outside of the function.</span></span>
- <span data-ttu-id="26076-112">它是一致的。</span><span class="sxs-lookup"><span data-stu-id="26076-112">It's consistent.</span></span> <span data-ttu-id="26076-113">假設是相同的輸入資料集合，就永遠會傳回相同的輸出值。</span><span class="sxs-lookup"><span data-stu-id="26076-113">Given the same set of input data, it will always return the same output value.</span></span>

<span data-ttu-id="26076-114">轉換為功能性程式設計的其中一種方式為重構現有的程式碼以排除不必要的副作用與外部相依性。</span><span class="sxs-lookup"><span data-stu-id="26076-114">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="26076-115">以此種方式，您可以建立現有程式碼的純虛擬函式版本。</span><span class="sxs-lookup"><span data-stu-id="26076-115">In this way, you can create pure function versions of existing code.</span></span>

<span data-ttu-id="26076-116">本文討論什麼是純虛擬函式，以及它不是什麼。</span><span class="sxs-lookup"><span data-stu-id="26076-116">This article discusses what a pure function is and what it's not.</span></span> <span data-ttu-id="26076-117">[教學課程：操作 WordprocessingML 檔中的內容](xml-shape-wordprocessingml-documents.md)教學課程示範如何操作 WordprocessingML 檔，並包含兩個如何使用純虛擬函式重構的範例。</span><span class="sxs-lookup"><span data-stu-id="26076-117">The [Tutorial: Manipulate content in a WordprocessingML document](xml-shape-wordprocessingml-documents.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>

<span data-ttu-id="26076-118">下列範例對照兩個非純虛擬函式與一個純虛擬函式。</span><span class="sxs-lookup"><span data-stu-id="26076-118">The following examples contrast two non-pure functions and a pure function.</span></span>

## <a name="example-implement-a-non-pure-function-that-changes-a-static-class-member"></a><span data-ttu-id="26076-119">範例：執行變更靜態類別成員的非純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="26076-119">Example: Implement a non-pure function that changes a static class member</span></span>

<span data-ttu-id="26076-120">在下列程式碼中， `HyphenatedConcat` 函數不是純虛擬函式，因為它會修改 `aMember` 靜態類別成員：</span><span class="sxs-lookup"><span data-stu-id="26076-120">In the following code, the `HyphenatedConcat` function isn't a pure function, because it modifies the `aMember` static class member:</span></span>

```csharp
public class Program
{
    private static string aMember = "StringOne";

    public static void HyphenatedConcat(string appendStr)
    {
        aMember += '-' + appendStr;
    }

    public static void Main()
    {
        HyphenatedConcat("StringTwo");
        Console.WriteLine(aMember);
    }
}
```

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

<span data-ttu-id="26076-121">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="26076-121">This example produces the following output:</span></span>

```output
StringOne-StringTwo
```

<span data-ttu-id="26076-122">請注意，要修改的資料具有 `public` 或 `private` 存取，或者是 `static` 成員、 `shared` 成員或實例成員，都不會有任何差異。</span><span class="sxs-lookup"><span data-stu-id="26076-122">Note that it's irrelevant whether the data being modified has `public` or `private` access, or is a `static` member, `shared` member, or instance member.</span></span> <span data-ttu-id="26076-123">純虛擬函式不會變更函數以外的任何資料。</span><span class="sxs-lookup"><span data-stu-id="26076-123">A pure function doesn't change any data outside of the function.</span></span>

## <a name="example-implement-a-non-pure-function-that-changes-a-parameter"></a><span data-ttu-id="26076-124">範例：執行變更參數的非純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="26076-124">Example: Implement a non-pure function that changes a parameter</span></span>

<span data-ttu-id="26076-125">此外，這個相同函式的下列版本不是純粹的，因為它會修改其參數的內容 `sb` 。</span><span class="sxs-lookup"><span data-stu-id="26076-125">Furthermore, the following version of this same function isn't pure because it modifies the contents of its parameter, `sb`.</span></span>

```csharp
public class Program
{
    public static void HyphenatedConcat(StringBuilder sb, String appendStr)
    {
        sb.Append('-' + appendStr);
    }

    public static void Main()
    {
        StringBuilder sb1 = new StringBuilder("StringOne");
        HyphenatedConcat(sb1, "StringTwo");
        Console.WriteLine(sb1);
    }
}
```

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

<span data-ttu-id="26076-126">這個版本的程式會產生與第一版相同的輸出，因為 `HyphenatedConcat` 函式已經叫用 <xref:System.Text.StringBuilder.Append%2A> 成員函式來變更其第一個參數的值 (狀態)。</span><span class="sxs-lookup"><span data-stu-id="26076-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="26076-127">請注意，即使 `HyphenatedConcat` 使用傳值參數傳遞的事實，還是會發生這種改變。</span><span class="sxs-lookup"><span data-stu-id="26076-127">Note that this alteration occurs despite the fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26076-128">若是參考型別 (Reference Type)，如果您依據值傳遞參數，會使參考的副本傳遞到物件。</span><span class="sxs-lookup"><span data-stu-id="26076-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="26076-129">這個副本仍然跟原始參考一樣，與相同的執行個體資料相關聯 (直到將參考變數指派給新的物件)。</span><span class="sxs-lookup"><span data-stu-id="26076-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="26076-130">修改參數的函式不一定需要呼叫傳址。</span><span class="sxs-lookup"><span data-stu-id="26076-130">Call-by-reference isn't necessarily required for a function to modify a parameter.</span></span>

## <a name="example-implement-a-pure-function"></a><span data-ttu-id="26076-131">範例：實作為純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="26076-131">Example: Implement a pure function</span></span>

<span data-ttu-id="26076-132">這個下一版的程式會顯示如何將 `HyphenatedConcat` 函式實作為純虛擬函式。</span><span class="sxs-lookup"><span data-stu-id="26076-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>

```csharp
class Program
{
    public static string HyphenatedConcat(string s, string appendStr)
    {
        return (s + '-' + appendStr);
    }

    public static void Main(string[] args)
    {
        string s1 = "StringOne";
        string s2 = HyphenatedConcat(s1, "StringTwo");
        Console.WriteLine(s2);
    }
}
```

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

<span data-ttu-id="26076-133">再次聲明，這個版本會產生相同的輸出行：`StringOne-StringTwo`。</span><span class="sxs-lookup"><span data-stu-id="26076-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="26076-134">請注意，若要保留串連值，它會儲存在中繼變數中 `s2` 。</span><span class="sxs-lookup"><span data-stu-id="26076-134">Note that to retain the concatenated value, it's stored in the intermediate variable `s2`.</span></span>

<span data-ttu-id="26076-135">其中一個可能非常實用的方法是，撰寫在本機非純虛擬但全域為純虛擬的函式 (亦即，它們可以宣告並修改本機變數)。</span><span class="sxs-lookup"><span data-stu-id="26076-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="26076-136">這類函式擁有許多值得撰寫的特性，但是會避免某些更錯綜複雜的功能性程式設計慣用句，例如，當簡易迴圈可以完成相同的事情時，必須使用遞迴。</span><span class="sxs-lookup"><span data-stu-id="26076-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>

## <a name="standard-query-operators"></a><span data-ttu-id="26076-137">標準查詢運算子</span><span class="sxs-lookup"><span data-stu-id="26076-137">Standard query operators</span></span>

<span data-ttu-id="26076-138">標準查詢運算子的重要特性是它們會實作為純量函數。</span><span class="sxs-lookup"><span data-stu-id="26076-138">An important characteristic of the standard query operators is that they're implemented as pure functions.</span></span>

<span data-ttu-id="26076-139">如需詳細資訊，請參閱 [標準查詢運算子總覽 (c # ) ](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) 和 [標準查詢運算子總覽 (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="26076-139">For more information, see [Standard Query Operators Overview (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) and [Standard Query Operators Overview (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26076-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26076-140">See also</span></span>

- [<span data-ttu-id="26076-141">純功能性轉換簡介</span><span class="sxs-lookup"><span data-stu-id="26076-141">Introduction to pure functional transformations</span></span>](introduction-pure-functional-transformations.md)
- [<span data-ttu-id="26076-142">功能性程式設計與命令式程式設計</span><span class="sxs-lookup"><span data-stu-id="26076-142">Functional programming vs. imperative programming</span></span>](functional-vs-imperative-programming.md)
