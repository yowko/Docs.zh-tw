---
title: 如何：使用 foreach 存取集合類別 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
ms.openlocfilehash: b02b9f4508984e3248cfd8e0cde0c994e1b871ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a><span data-ttu-id="ee295-102">如何：使用 foreach 存取集合類別 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="ee295-102">How to: Access a Collection Class with foreach (C# Programming Guide)</span></span>
<span data-ttu-id="ee295-103">下列程式碼範例說明如何撰寫可與 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 搭配使用的非泛型集合類別。</span><span class="sxs-lookup"><span data-stu-id="ee295-103">The following code example illustrates how to write a non-generic collection class that can be used with [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span></span> <span data-ttu-id="ee295-104">這個範例定義字串權杖化工具類別。</span><span class="sxs-lookup"><span data-stu-id="ee295-104">The example defines a string tokenizer class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee295-105">這個範例只有在無法使用泛型集合類別時才會呈現建議做法。</span><span class="sxs-lookup"><span data-stu-id="ee295-105">This example represents recommended practice only when you cannot use a generic collection class.</span></span> <span data-ttu-id="ee295-106">如需如何實作支援 <xref:System.Collections.Generic.IEnumerable%601> 之類型安全泛型集合類別的範例，請參閱[迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)。</span><span class="sxs-lookup"><span data-stu-id="ee295-106">For an example of how to implement a type-safe generic collection class that supports <xref:System.Collections.Generic.IEnumerable%601>, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="ee295-107">在範例中，下列程式碼區段使用 `Tokens` 類別，將句子 "This is a sample sentence."</span><span class="sxs-lookup"><span data-stu-id="ee295-107">In the example, the following code segment uses the `Tokens` class to break the sentence "This is a sample sentence."</span></span> <span data-ttu-id="ee295-108">分為權杖，方法是使用 ' ' 和 '-' 作為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="ee295-108">into tokens by using ' ' and '-' as separators.</span></span> <span data-ttu-id="ee295-109">程式碼接著使用 `foreach` 陳述式來顯示那些權杖。</span><span class="sxs-lookup"><span data-stu-id="ee295-109">The code then displays those tokens by using a `foreach` statement.</span></span>  
  
 [!code-csharp[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="ee295-110">範例</span><span class="sxs-lookup"><span data-stu-id="ee295-110">Example</span></span>  
 <span data-ttu-id="ee295-111">就內部而言，`Tokens` 類別會使用陣列來儲存權杖。</span><span class="sxs-lookup"><span data-stu-id="ee295-111">Internally, the `Tokens` class uses an array to store the tokens.</span></span> <span data-ttu-id="ee295-112">因為陣列實作 <xref:System.Collections.IEnumerator> 和 <xref:System.Collections.IEnumerable>，所以程式碼範例可能已用過陣列的列舉方法 (<xref:System.Collections.IEnumerable.GetEnumerator%2A>、<xref:System.Collections.IEnumerator.MoveNext%2A>、<xref:System.Collections.IEnumerator.Reset%2A> 和 <xref:System.Collections.IEnumerator.Current%2A>)，而不是在 `Tokens` 類別中定義它們。</span><span class="sxs-lookup"><span data-stu-id="ee295-112">Because arrays implement <xref:System.Collections.IEnumerator> and <xref:System.Collections.IEnumerable>, the code example could have used the array's enumeration methods (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A>) instead of defining them in the `Tokens` class.</span></span> <span data-ttu-id="ee295-113">範例中所包含的方法定義是要釐清其定義方式和其用途。</span><span class="sxs-lookup"><span data-stu-id="ee295-113">The method definitions are included in the example to clarify how they are defined and what each does.</span></span>  
  
 [!code-csharp[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 <span data-ttu-id="ee295-114">在 C# 中，集合類別沒必要實作 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.IEnumerator>，以與 `foreach` 相容。</span><span class="sxs-lookup"><span data-stu-id="ee295-114">In C#, it is not necessary for a collection class to implement <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> to be compatible with `foreach`.</span></span> <span data-ttu-id="ee295-115">如果類別有所需的 <xref:System.Collections.IEnumerable.GetEnumerator%2A>、<xref:System.Collections.IEnumerator.MoveNext%2A>、<xref:System.Collections.IEnumerator.Reset%2A> 和 <xref:System.Collections.IEnumerator.Current%2A> 成員，就能搭配 `foreach` 使用。</span><span class="sxs-lookup"><span data-stu-id="ee295-115">If the class has the required <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A> members, it will work with `foreach`.</span></span> <span data-ttu-id="ee295-116">省略介面的優點是讓您定義 `Current` 的傳回型別，而這比 <xref:System.Object> 更為具體。</span><span class="sxs-lookup"><span data-stu-id="ee295-116">Omitting the interfaces has the advantage of enabling you to define a return type for `Current` that is more specific than <xref:System.Object>.</span></span> <span data-ttu-id="ee295-117">這提供類型安全。</span><span class="sxs-lookup"><span data-stu-id="ee295-117">This provides type safety.</span></span>  
  
 <span data-ttu-id="ee295-118">例如，變更上述範例中的下列各行。</span><span class="sxs-lookup"><span data-stu-id="ee295-118">For example, change the following lines in the previous example.</span></span>  
  
```csharp  
// Change the Tokens class so that it no longer implements IEnumerable.  
public class Tokens  
{  
    // . . .  
  
    // Change the return type for the GetEnumerator method.  
    public TokenEnumerator GetEnumerator()  
    {   }  
  
    // Change TokenEnumerator so that it no longer implements IEnumerator.  
    public class TokenEnumerator  
    {  
        // . . .  
  
        // Change the return type of method Current to string.  
        public string Current  
        {   }  
    }  
 }  
```  
  
 <span data-ttu-id="ee295-119">因為 `Current` 會傳回字串，所以編譯器可以偵測到在 `foreach` 陳述式中使用不相容的類型，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ee295-119">Because `Current` returns a string, the compiler can detect when an incompatible type is used in a `foreach` statement, as shown in the following code.</span></span>  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 <span data-ttu-id="ee295-120">省略 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.IEnumerator> 的缺點是集合類別無法再與其他 Common Language Runtime 語言的 `foreach` 陳述式或對等陳述式互通。</span><span class="sxs-lookup"><span data-stu-id="ee295-120">The disadvantage of omitting <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> is that the collection class is no longer interoperable with the `foreach` statements, or equivalent statements, of other common language runtime languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee295-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="ee295-121">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="ee295-122">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ee295-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ee295-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ee295-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ee295-124">陣列</span><span class="sxs-lookup"><span data-stu-id="ee295-124">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="ee295-125">集合</span><span class="sxs-lookup"><span data-stu-id="ee295-125">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
