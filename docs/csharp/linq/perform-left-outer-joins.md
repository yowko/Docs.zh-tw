---
title: "執行左方外部聯結"
description: "如何執行左方外部聯結。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: 0c28c85bf933a411403aefcb91801d28fe1c268e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="bba87-104">執行左方外部聯結</span><span class="sxs-lookup"><span data-stu-id="bba87-104">Perform left outer joins</span></span>
<span data-ttu-id="bba87-105">左方外部聯結是第一個集合中的每個項目都會傳回的聯結，不論它在第二個集合中是否有任何相互關聯的項目。</span><span class="sxs-lookup"><span data-stu-id="bba87-105">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="bba87-106">您可以對群組聯結的結果呼叫 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> 方法，使用 LINQ 執行左方外部聯結。</span><span class="sxs-lookup"><span data-stu-id="bba87-106">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bba87-107">範例</span><span class="sxs-lookup"><span data-stu-id="bba87-107">Example</span></span>  
 <span data-ttu-id="bba87-108">下列範例示範如何對群組聯結的結果使用 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> 方法，來執行左方外部聯結。</span><span class="sxs-lookup"><span data-stu-id="bba87-108">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>  
  
 <span data-ttu-id="bba87-109">產生兩個集合的左方外部聯結的第一個步驟，是使用群組聯結執行內部聯結。</span><span class="sxs-lookup"><span data-stu-id="bba87-109">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="bba87-110">(如需此程序的說明，請參閱[執行內部聯結](perform-inner-joins.md)。)在本例中，`Person` 物件的清單是根據符合 `Pet.Owner` 的 `Person` 物件，內部聯結到 `Pet` 物件的清單。</span><span class="sxs-lookup"><span data-stu-id="bba87-110">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>  
  
 <span data-ttu-id="bba87-111">第二個步驟是在結果集中包含第一個 (左) 集合中的每個項目，即使該元素在右集合中沒有相符的項目。</span><span class="sxs-lookup"><span data-stu-id="bba87-111">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="bba87-112">對來自群組聯結的每個相符項目序列呼叫 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> 即可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="bba87-112">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="bba87-113">在此範例中，會在每個相符 `Pet` 物件的序列上呼叫 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A>。</span><span class="sxs-lookup"><span data-stu-id="bba87-113">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="bba87-114">如果任何 `Person` 物件的相符 `Pet` 物件序列是空的，方法會傳回包含單一預設值的集合，藉此確保結果集合會顯示每個 `Person` 物件。</span><span class="sxs-lookup"><span data-stu-id="bba87-114">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bba87-115">參考型別的預設值是 `null`，因此範例會先檢查 Null 參考，再存取每個 `Pet` 集合的每個項目。</span><span class="sxs-lookup"><span data-stu-id="bba87-115">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="bba87-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="bba87-116">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="bba87-117">執行內部聯結</span><span class="sxs-lookup"><span data-stu-id="bba87-117">Perform inner joins</span></span>](perform-inner-joins.md)  
 [<span data-ttu-id="bba87-118">執行群組聯結</span><span class="sxs-lookup"><span data-stu-id="bba87-118">Perform grouped joins</span></span>](perform-grouped-joins.md)  
 [<span data-ttu-id="bba87-119">匿名型別</span><span class="sxs-lookup"><span data-stu-id="bba87-119">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
