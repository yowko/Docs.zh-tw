---
title: 重構為純虛擬函式 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 0a37b30278c850256355612cec09a4c017c7adc2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787162"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="141b2-102">重構為純虛擬函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="141b2-102">Refactoring Into Pure Functions (Visual Basic)</span></span>

<span data-ttu-id="141b2-103">純功能性轉換的重要觀點為學習如何使用純虛擬函式重構程式碼。</span><span class="sxs-lookup"><span data-stu-id="141b2-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>

<span data-ttu-id="141b2-104">如同本節先前所述，純虛擬函式擁有兩個實用的特性：</span><span class="sxs-lookup"><span data-stu-id="141b2-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>

- <span data-ttu-id="141b2-105">它有沒有副作用。</span><span class="sxs-lookup"><span data-stu-id="141b2-105">It has no side effects.</span></span> <span data-ttu-id="141b2-106">函式不會變更函式以外任何類型的任何變數或資料。</span><span class="sxs-lookup"><span data-stu-id="141b2-106">The function does not change any variables or the data of any type outside of the function.</span></span>

- <span data-ttu-id="141b2-107">它是一致的。</span><span class="sxs-lookup"><span data-stu-id="141b2-107">It is consistent.</span></span> <span data-ttu-id="141b2-108">假設是相同的輸入資料集合，就永遠會傳回相同的輸出值。</span><span class="sxs-lookup"><span data-stu-id="141b2-108">Given the same set of input data, it will always return the same output value.</span></span>

 <span data-ttu-id="141b2-109">轉換為功能性程式設計的其中一種方式為重構現有的程式碼以排除不必要的副作用與外部相依性。</span><span class="sxs-lookup"><span data-stu-id="141b2-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="141b2-110">以此種方式，您可以建立現有程式碼的純虛擬函式版本。</span><span class="sxs-lookup"><span data-stu-id="141b2-110">In this way, you can create pure function versions of existing code.</span></span>

<span data-ttu-id="141b2-111">這個主題討論什麼是純虛擬函式以及什麼不是純虛擬函式。</span><span class="sxs-lookup"><span data-stu-id="141b2-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="141b2-112">[教學課程：管理 WordprocessingML 文件 (Visual Basic) 中的內容](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)教學課程示範如何管理 WordprocessingML 文件，並包含兩個範例使用純虛擬函式重構。</span><span class="sxs-lookup"><span data-stu-id="141b2-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>

## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="141b2-113">排除副作用與外部相依性</span><span class="sxs-lookup"><span data-stu-id="141b2-113">Eliminating Side Effects and External Dependencies</span></span>

<span data-ttu-id="141b2-114">下列範例對照兩個非純虛擬函式與一個純虛擬函式。</span><span class="sxs-lookup"><span data-stu-id="141b2-114">The following examples contrast two non-pure functions and a pure function.</span></span>

### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="141b2-115">變更類別成員的非純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="141b2-115">Non-Pure Function that Changes a Class Member</span></span>

<span data-ttu-id="141b2-116">在下列程式碼中，`HyphenatedConcat` 函式不是純虛擬函式，因為它會修改類別中的 `aMember` 資料成員：</span><span class="sxs-lookup"><span data-stu-id="141b2-116">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>

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

<span data-ttu-id="141b2-117">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="141b2-117">This code produces the following output:</span></span>

```
StringOne-StringTwo
```

<span data-ttu-id="141b2-118">請注意，它是不相關要修改的資料是否有`public`或是`private`存取權，或者是`shared`成員或執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="141b2-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="141b2-119">純虛擬函式不會變更函式以外的任何資料。</span><span class="sxs-lookup"><span data-stu-id="141b2-119">A pure function does not change any data outside of the function.</span></span>

### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="141b2-120">變更引數的非純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="141b2-120">Non-Pure Function that Changes an Argument</span></span>

<span data-ttu-id="141b2-121">此外，這個相同函式的下列版本不是純虛擬函式，因為它會修改其參數 `sb` 的內容。</span><span class="sxs-lookup"><span data-stu-id="141b2-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>

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

<span data-ttu-id="141b2-122">這個版本的程式會產生與第一版相同的輸出，因為 `HyphenatedConcat` 函式已經叫用 <xref:System.Text.StringBuilder.Append%2A> 成員函式來變更其第一個參數的值 (狀態)。</span><span class="sxs-lookup"><span data-stu-id="141b2-122">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="141b2-123">請注意，雖然 `HyphenatedConcat` 使用 call-by-value 參數傳遞 (Parameter Passing)，還是會發生這個改變。</span><span class="sxs-lookup"><span data-stu-id="141b2-123">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="141b2-124">若是參考型別 (Reference Type)，如果您依據值傳遞參數，會使參考的副本傳遞到物件。</span><span class="sxs-lookup"><span data-stu-id="141b2-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="141b2-125">這個副本仍然跟原始參考一樣，與相同的執行個體資料相關聯 (直到將參考變數指派給新的物件)。</span><span class="sxs-lookup"><span data-stu-id="141b2-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="141b2-126">對於要修改參數的函式，則不一定需要 Call-by-reference。</span><span class="sxs-lookup"><span data-stu-id="141b2-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>

### <a name="pure-function"></a><span data-ttu-id="141b2-127">純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="141b2-127">Pure Function</span></span>

<span data-ttu-id="141b2-128">這個下一個版本的程式顯示如何實作 `HyphenatedConcat` 函式做為純虛擬函式。</span><span class="sxs-lookup"><span data-stu-id="141b2-128">This next version of the program hows how to implement the `HyphenatedConcat` function as a pure function.</span></span>

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

<span data-ttu-id="141b2-129">再次聲明，這個版本會產生相同的輸出行：`StringOne-StringTwo`。</span><span class="sxs-lookup"><span data-stu-id="141b2-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="141b2-130">請注意，若要保留串連值，它會儲存在中繼變數 `s2` 中。</span><span class="sxs-lookup"><span data-stu-id="141b2-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>

<span data-ttu-id="141b2-131">其中一個可能非常實用的方法是，撰寫在本機非純虛擬但全域為純虛擬的函式 (亦即，它們可以宣告並修改本機變數)。</span><span class="sxs-lookup"><span data-stu-id="141b2-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="141b2-132">這類函式擁有許多值得撰寫的特性，但是會避免某些更錯綜複雜的功能性程式設計慣用句，例如，當簡易迴圈可以完成相同的事情時，必須使用遞迴。</span><span class="sxs-lookup"><span data-stu-id="141b2-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>

## <a name="standard-query-operators"></a><span data-ttu-id="141b2-133">標準查詢運算子</span><span class="sxs-lookup"><span data-stu-id="141b2-133">Standard Query Operators</span></span>

<span data-ttu-id="141b2-134">標準查詢運算子的重要特性為它們會被當做純虛擬函式實作。</span><span class="sxs-lookup"><span data-stu-id="141b2-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>

<span data-ttu-id="141b2-135">如需詳細資訊，請參閱 <<c0> [ 標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="141b2-135">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="141b2-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="141b2-136">See also</span></span>

- [<span data-ttu-id="141b2-137">純函數式轉換 (Visual Basic) 簡介</span><span class="sxs-lookup"><span data-stu-id="141b2-137">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="141b2-138">函數式程式設計與命令式程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="141b2-138">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
