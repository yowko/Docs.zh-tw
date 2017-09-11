---
title: "如何：使用 foreach 存取集合類別 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 841132b5181c5e17d1eabae11d3550811aa959ec
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a><span data-ttu-id="f8974-102">如何：使用 foreach 存取集合類別 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f8974-102">How to: Access a Collection Class with foreach (C# Programming Guide)</span></span>
<span data-ttu-id="f8974-103">下列程式碼範例說明如何撰寫可與 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 搭配使用的非泛型集合類別。</span><span class="sxs-lookup"><span data-stu-id="f8974-103">The following code example illustrates how to write a non-generic collection class that can be used with [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span></span> <span data-ttu-id="f8974-104">這個範例定義字串權杖化工具類別。</span><span class="sxs-lookup"><span data-stu-id="f8974-104">The example defines a string tokenizer class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8974-105">這個範例只有在無法使用泛型集合類別時才會呈現建議做法。</span><span class="sxs-lookup"><span data-stu-id="f8974-105">This example represents recommended practice only when you cannot use a generic collection class.</span></span> <span data-ttu-id="f8974-106">如需如何實作支援 <xref:System.Collections.Generic.IEnumerable%601> 之類型安全泛型集合類別的範例，請參閱[迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)。</span><span class="sxs-lookup"><span data-stu-id="f8974-106">For an example of how to implement a type-safe generic collection class that supports <xref:System.Collections.Generic.IEnumerable%601>, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="f8974-107">在範例中，下列程式碼區段使用 `Tokens` 類別，將句子 "This is a sample sentence."</span><span class="sxs-lookup"><span data-stu-id="f8974-107">In the example, the following code segment uses the `Tokens` class to break the sentence "This is a sample sentence."</span></span> <span data-ttu-id="f8974-108">分為權杖，方法是使用 ' ' 和 '-' 作為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="f8974-108">into tokens by using ' ' and '-' as separators.</span></span> <span data-ttu-id="f8974-109">程式碼接著使用 `foreach` 陳述式來顯示那些權杖。</span><span class="sxs-lookup"><span data-stu-id="f8974-109">The code then displays those tokens by using a `foreach` statement.</span></span>  
  
 <span data-ttu-id="f8974-110">[!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f8974-110">[!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8974-111">範例</span><span class="sxs-lookup"><span data-stu-id="f8974-111">Example</span></span>  
 <span data-ttu-id="f8974-112">就內部而言，`Tokens` 類別會使用陣列來儲存權杖。</span><span class="sxs-lookup"><span data-stu-id="f8974-112">Internally, the `Tokens` class uses an array to store the tokens.</span></span> <span data-ttu-id="f8974-113">因為陣列實作 <xref:System.Collections.IEnumerator> 和 <xref:System.Collections.IEnumerable>，所以程式碼範例可能已使用陣列的列舉方法 (<xref:System.Collections.IEnumerable.GetEnumerator%2A>、<xref:System.Collections.IEnumerator.MoveNext%2A>、<xref:System.Collections.IEnumerator.Reset%2A> 和 <xref:System.Collections.IEnumerator.Current%2A>)，而不是將它們定義在 `Tokens` 類別中。</span><span class="sxs-lookup"><span data-stu-id="f8974-113">Because arrays implement <xref:System.Collections.IEnumerator> and <xref:System.Collections.IEnumerable>, the code example could have used the array's enumeration methods (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A>) instead of defining them in the `Tokens` class.</span></span> <span data-ttu-id="f8974-114">範例中所包含的方法定義是要釐清其定義方式和其用途。</span><span class="sxs-lookup"><span data-stu-id="f8974-114">The method definitions are included in the example to clarify how they are defined and what each does.</span></span>  
  
 <span data-ttu-id="f8974-115">[!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f8974-115">[!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]</span></span>  
  
 <span data-ttu-id="f8974-116">在 C# 中，集合類別不需要實作 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.IEnumerator> 以與 `foreach` 相容。</span><span class="sxs-lookup"><span data-stu-id="f8974-116">In C#, it is not necessary for a collection class to implement <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> to be compatible with `foreach`.</span></span> <span data-ttu-id="f8974-117">如果類別具有必要的 <xref:System.Collections.IEnumerable.GetEnumerator%2A>、<xref:System.Collections.IEnumerator.MoveNext%2A>、<xref:System.Collections.IEnumerator.Reset%2A> 和 <xref:System.Collections.IEnumerator.Current%2A> 成員，則會使用 `foreach`。</span><span class="sxs-lookup"><span data-stu-id="f8974-117">If the class has the required <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A> members, it will work with `foreach`.</span></span> <span data-ttu-id="f8974-118">省略介面的優點是讓您定義 `Current` 的傳回型別，而這比 <xref:System.Object> 更為具體。</span><span class="sxs-lookup"><span data-stu-id="f8974-118">Omitting the interfaces has the advantage of enabling you to define a return type for `Current` that is more specific than <xref:System.Object>.</span></span> <span data-ttu-id="f8974-119">這提供類型安全。</span><span class="sxs-lookup"><span data-stu-id="f8974-119">This provides type safety.</span></span>  
  
 <span data-ttu-id="f8974-120">例如，變更上述範例中的下列各行。</span><span class="sxs-lookup"><span data-stu-id="f8974-120">For example, change the following lines in the previous example.</span></span>  
  
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
  
 <span data-ttu-id="f8974-121">因為 `Current` 會傳回字串，所以編譯器可以偵測到在 `foreach` 陳述式中使用不相容的類型，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="f8974-121">Because `Current` returns a string, the compiler can detect when an incompatible type is used in a `foreach` statement, as shown in the following code.</span></span>  
  
```csharp  
  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 <span data-ttu-id="f8974-122">省略 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.IEnumerator> 的缺點是集合類別無法再與其他通用語言執行階段語言的 `foreach` 陳述式或對等陳述式互通。</span><span class="sxs-lookup"><span data-stu-id="f8974-122">The disadvantage of omitting <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> is that the collection class is no longer interoperable with the `foreach` statements, or equivalent statements, of other common language runtime languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8974-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8974-123">See Also</span></span>  
 <span data-ttu-id="f8974-124"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="f8974-124"><xref:System.Collections.Generic></span></span>   
<span data-ttu-id="f8974-125"> [C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f8974-125"> [C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="f8974-126"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f8974-126"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="f8974-127"> [陣列](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="f8974-127"> [Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
<span data-ttu-id="f8974-128"> [集合](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)</span><span class="sxs-lookup"><span data-stu-id="f8974-128"> [Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)</span></span>
