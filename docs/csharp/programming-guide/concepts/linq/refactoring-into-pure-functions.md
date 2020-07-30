---
title: 重構為純虛擬函式 (C#)
description: 瞭解如何使用純虛擬函式重構程式碼。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: cc5dd26923e2edaed34c8f1b742b3dfa1e935e68
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300224"
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="18312-104">重構為純虛擬函式 (C#)</span><span class="sxs-lookup"><span data-stu-id="18312-104">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="18312-105">純功能性轉換的重要觀點為學習如何使用純虛擬函式重構程式碼。</span><span class="sxs-lookup"><span data-stu-id="18312-105">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18312-106">功能性程式設計的常見命名法為使用純虛擬函式重構程式。</span><span class="sxs-lookup"><span data-stu-id="18312-106">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="18312-107">在 Visual Basic 和 C++ 中，這可以利用個別的語言，調整函式的用法。</span><span class="sxs-lookup"><span data-stu-id="18312-107">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="18312-108">不過，在 C# 中，函式稱為方法。</span><span class="sxs-lookup"><span data-stu-id="18312-108">However, in C#, functions are called methods.</span></span> <span data-ttu-id="18312-109">就這個討論而言，純虛擬函式會當成 C# 中的方法實作。</span><span class="sxs-lookup"><span data-stu-id="18312-109">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="18312-110">如同本節先前所述，純虛擬函式擁有兩個實用的特性：</span><span class="sxs-lookup"><span data-stu-id="18312-110">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
- <span data-ttu-id="18312-111">它有沒有副作用。</span><span class="sxs-lookup"><span data-stu-id="18312-111">It has no side effects.</span></span> <span data-ttu-id="18312-112">函式不會變更函式以外任何類型的任何變數或資料。</span><span class="sxs-lookup"><span data-stu-id="18312-112">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
- <span data-ttu-id="18312-113">它是一致的。</span><span class="sxs-lookup"><span data-stu-id="18312-113">It is consistent.</span></span> <span data-ttu-id="18312-114">假設是相同的輸入資料集合，就永遠會傳回相同的輸出值。</span><span class="sxs-lookup"><span data-stu-id="18312-114">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="18312-115">轉換為功能性程式設計的其中一種方式為重構現有的程式碼以排除不必要的副作用與外部相依性。</span><span class="sxs-lookup"><span data-stu-id="18312-115">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="18312-116">以此種方式，您可以建立現有程式碼的純虛擬函式版本。</span><span class="sxs-lookup"><span data-stu-id="18312-116">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="18312-117">這個主題討論什麼是純虛擬函式以及什麼不是純虛擬函式。</span><span class="sxs-lookup"><span data-stu-id="18312-117">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="18312-118">[教學課程：管理 WordprocessingML 文件中的內容 (C#)](./shape-of-wordprocessingml-documents.md) 教學課程顯示如何管理 WordprocessingML 文件，並包含兩個如何使用純虛擬函式重構的範例。</span><span class="sxs-lookup"><span data-stu-id="18312-118">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](./shape-of-wordprocessingml-documents.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="18312-119">排除副作用與外部相依性</span><span class="sxs-lookup"><span data-stu-id="18312-119">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="18312-120">下列範例對照兩個非純虛擬函式與一個純虛擬函式。</span><span class="sxs-lookup"><span data-stu-id="18312-120">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="18312-121">變更類別成員的非純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="18312-121">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="18312-122">在下列程式碼中，`HyphenatedConcat` 函式不是純虛擬函式，因為它會修改類別中的 `aMember` 資料成員：</span><span class="sxs-lookup"><span data-stu-id="18312-122">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
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
  
 <span data-ttu-id="18312-123">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="18312-123">This code produces the following output:</span></span>  
  
```output  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="18312-124">請注意，要修改的資料具有 `public` 或 `private` 存取權，或者是 `static` 成員或執行個體成員，都沒有關係。</span><span class="sxs-lookup"><span data-stu-id="18312-124">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="18312-125">純虛擬函式不會變更函式以外的任何資料。</span><span class="sxs-lookup"><span data-stu-id="18312-125">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="18312-126">變更引數的非純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="18312-126">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="18312-127">此外，這個相同函式的下列版本不是純虛擬函式，因為它會修改其參數 `sb` 的內容。</span><span class="sxs-lookup"><span data-stu-id="18312-127">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
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
  
 <span data-ttu-id="18312-128">這個版本的程式會產生與第一版相同的輸出，因為 `HyphenatedConcat` 函式已經叫用 <xref:System.Text.StringBuilder.Append%2A> 成員函式來變更其第一個參數的值 (狀態)。</span><span class="sxs-lookup"><span data-stu-id="18312-128">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="18312-129">請注意，雖然 `HyphenatedConcat` 使用 call-by-value 參數傳遞 (Parameter Passing)，還是會發生這個改變。</span><span class="sxs-lookup"><span data-stu-id="18312-129">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="18312-130">若是參考型別 (Reference Type)，如果您依據值傳遞參數，會使參考的副本傳遞到物件。</span><span class="sxs-lookup"><span data-stu-id="18312-130">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="18312-131">這個副本仍然跟原始參考一樣，與相同的執行個體資料相關聯 (直到將參考變數指派給新的物件)。</span><span class="sxs-lookup"><span data-stu-id="18312-131">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="18312-132">對於要修改參數的函式，則不一定需要 Call-by-reference。</span><span class="sxs-lookup"><span data-stu-id="18312-132">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="18312-133">純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="18312-133">Pure Function</span></span>  
<span data-ttu-id="18312-134">這個下一版的程式會顯示如何將 `HyphenatedConcat` 函式實作為純虛擬函式。</span><span class="sxs-lookup"><span data-stu-id="18312-134">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="18312-135">再次聲明，這個版本會產生相同的輸出行：`StringOne-StringTwo`。</span><span class="sxs-lookup"><span data-stu-id="18312-135">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="18312-136">請注意，若要保留串連值，它會儲存在中繼變數 `s2` 中。</span><span class="sxs-lookup"><span data-stu-id="18312-136">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="18312-137">其中一個可能非常實用的方法是，撰寫在本機非純虛擬但全域為純虛擬的函式 (亦即，它們可以宣告並修改本機變數)。</span><span class="sxs-lookup"><span data-stu-id="18312-137">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="18312-138">這類函式擁有許多值得撰寫的特性，但是會避免某些更錯綜複雜的功能性程式設計慣用句，例如，當簡易迴圈可以完成相同的事情時，必須使用遞迴。</span><span class="sxs-lookup"><span data-stu-id="18312-138">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="18312-139">標準查詢運算子</span><span class="sxs-lookup"><span data-stu-id="18312-139">Standard Query Operators</span></span>  
 <span data-ttu-id="18312-140">標準查詢運算子的重要特性為它們會被當做純虛擬函式實作。</span><span class="sxs-lookup"><span data-stu-id="18312-140">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="18312-141">如需詳細資訊，請參閱[標準查詢運算子概觀 (C#)](./standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="18312-141">For more information, see [Standard Query Operators Overview (C#)](./standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18312-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18312-142">See also</span></span>

- [<span data-ttu-id="18312-143">純函數式轉換簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="18312-143">Introduction to Pure Functional Transformations (C#)</span></span>](./introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="18312-144">功能程式設計與命令式程式設計的比較（c #）</span><span class="sxs-lookup"><span data-stu-id="18312-144">Functional Programming vs. Imperative Programming (C#)</span></span>](./functional-programming-vs-imperative-programming.md)
