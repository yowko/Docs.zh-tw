---
title: "執行左方外部聯結"
description: "如何執行左方外部聯結。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d0e4a5840f5a19a42aea477927afb77fee27eaea
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="a959b-104">執行左方外部聯結</span><span class="sxs-lookup"><span data-stu-id="a959b-104">Perform left outer joins</span></span>
<span data-ttu-id="a959b-105">左方外部聯結是第一個集合中的每個項目都會傳回的聯結，不論它在第二個集合中是否有任何相互關聯的項目。</span><span class="sxs-lookup"><span data-stu-id="a959b-105">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="a959b-106">您可以對群組聯結的結果呼叫 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> 方法，使用 LINQ 執行左方外部聯結。</span><span class="sxs-lookup"><span data-stu-id="a959b-106">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a959b-107">範例</span><span class="sxs-lookup"><span data-stu-id="a959b-107">Example</span></span>  
 <span data-ttu-id="a959b-108">下例示範如何對群組聯結的結果使用 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> 方法，來執行左方外部聯結。</span><span class="sxs-lookup"><span data-stu-id="a959b-108">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>  
  
 <span data-ttu-id="a959b-109">產生兩個集合的左方外部聯結的第一個步驟，是使用群組聯結執行內部聯結。</span><span class="sxs-lookup"><span data-stu-id="a959b-109">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="a959b-110">(如需此程序的說明，請參閱[執行內部聯結](perform-inner-joins.md)。)在本例中，`Person` 物件的清單是根據符合 `Pet.Owner` 的 `Person` 物件，內部聯結到 `Pet` 物件的清單。</span><span class="sxs-lookup"><span data-stu-id="a959b-110">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>  
  
 <span data-ttu-id="a959b-111">第二個步驟是在結果集中包含第一個 (左) 集合中的每個項目，即使該元素在右集合中沒有相符的項目。</span><span class="sxs-lookup"><span data-stu-id="a959b-111">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="a959b-112">對來自群組聯結的每個相符項目序列呼叫 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> 即可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="a959b-112">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="a959b-113">本例中，已對每個相符 `Pet` 物件的序列呼叫 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A>。</span><span class="sxs-lookup"><span data-stu-id="a959b-113">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="a959b-114">如果任何 `Person` 物件的相符 `Pet` 物件序列是空的，方法會傳回包含單一預設值的集合，藉此確保結果集合會顯示每個 `Person` 物件。</span><span class="sxs-lookup"><span data-stu-id="a959b-114">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a959b-115">參考型別的預設值是 `null`，因此範例會先檢查 Null 參考，再存取每個 `Pet` 集合的每個項目。</span><span class="sxs-lookup"><span data-stu-id="a959b-115">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>  
  
 <span data-ttu-id="a959b-116">[!code-cs[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a959b-116">[!code-cs[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="a959b-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="a959b-117">See also</span></span>  
 <span data-ttu-id="a959b-118"><xref:System.Linq.Enumerable.Join%2A></span><span class="sxs-lookup"><span data-stu-id="a959b-118"><xref:System.Linq.Enumerable.Join%2A></span></span>   
 <span data-ttu-id="a959b-119"><xref:System.Linq.Enumerable.GroupJoin%2A></span><span class="sxs-lookup"><span data-stu-id="a959b-119"><xref:System.Linq.Enumerable.GroupJoin%2A></span></span>   
<span data-ttu-id="a959b-120"> [執行內部聯結](perform-inner-joins.md) </span><span class="sxs-lookup"><span data-stu-id="a959b-120"> [Perform inner joins](perform-inner-joins.md) </span></span>  
<span data-ttu-id="a959b-121"> [執行群組聯結](perform-grouped-joins.md) </span><span class="sxs-lookup"><span data-stu-id="a959b-121"> [Perform grouped joins](perform-grouped-joins.md) </span></span>  
<span data-ttu-id="a959b-122"> [匿名型別](../programming-guide/classes-and-structs/anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="a959b-122"> [Anonymous types](../programming-guide/classes-and-structs/anonymous-types.md)</span></span>   
 
