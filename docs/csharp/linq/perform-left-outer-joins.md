---
title: 執行左方外部聯結 (C# 中的 LINQ)
description: 了解如何使用 C# 中的 LINQ 執行左方外部聯結。
ms.date: 12/1/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: 329fe9e17640931c5eb39b33b791a7a77a6f7b89
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506592"
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="1017f-103">執行左方外部聯結</span><span class="sxs-lookup"><span data-stu-id="1017f-103">Perform left outer joins</span></span>

<span data-ttu-id="1017f-104">左方外部聯結是第一個集合中的每個項目都會傳回的聯結，不論它在第二個集合中是否有任何相互關聯的項目。</span><span class="sxs-lookup"><span data-stu-id="1017f-104">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="1017f-105">您可以對群組聯結的結果呼叫 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> 方法，使用 LINQ 執行左方外部聯結。</span><span class="sxs-lookup"><span data-stu-id="1017f-105">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>

## <a name="example"></a><span data-ttu-id="1017f-106">範例</span><span class="sxs-lookup"><span data-stu-id="1017f-106">Example</span></span>

<span data-ttu-id="1017f-107">下列範例示範如何對群組聯結的結果使用 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> 方法，來執行左方外部聯結。</span><span class="sxs-lookup"><span data-stu-id="1017f-107">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>

<span data-ttu-id="1017f-108">產生兩個集合的左方外部聯結的第一個步驟，是使用群組聯結執行內部聯結。</span><span class="sxs-lookup"><span data-stu-id="1017f-108">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="1017f-109">(如需此程序的說明，請參閱[執行內部聯結](perform-inner-joins.md)。)在本例中，`Person` 物件的清單是根據符合 `Pet.Owner` 的 `Person` 物件，內部聯結到 `Pet` 物件的清單。</span><span class="sxs-lookup"><span data-stu-id="1017f-109">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>

<span data-ttu-id="1017f-110">第二個步驟是在結果集中包含第一個 (左) 集合中的每個項目，即使該元素在右集合中沒有相符的項目。</span><span class="sxs-lookup"><span data-stu-id="1017f-110">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="1017f-111">對來自群組聯結的每個相符項目序列呼叫 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> 即可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="1017f-111">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="1017f-112">在此範例中，會在每個相符 `Pet` 物件的序列上呼叫 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A>。</span><span class="sxs-lookup"><span data-stu-id="1017f-112">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="1017f-113">如果任何 `Person` 物件的相符 `Pet` 物件序列是空的，方法會傳回包含單一預設值的集合，藉此確保結果集合會顯示每個 `Person` 物件。</span><span class="sxs-lookup"><span data-stu-id="1017f-113">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>

> [!NOTE]
> <span data-ttu-id="1017f-114">參考型別的預設值是 `null`，因此範例會先檢查 Null 參考，再存取每個 `Pet` 集合的每個項目。</span><span class="sxs-lookup"><span data-stu-id="1017f-114">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>

[!code-csharp[CsLINQProgJoining#7](~/samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]

## <a name="see-also"></a><span data-ttu-id="1017f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1017f-115">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>  
- <xref:System.Linq.Enumerable.GroupJoin%2A>  
- [<span data-ttu-id="1017f-116">執行內部聯結</span><span class="sxs-lookup"><span data-stu-id="1017f-116">Perform inner joins</span></span>](perform-inner-joins.md)  
- [<span data-ttu-id="1017f-117">執行群組聯結</span><span class="sxs-lookup"><span data-stu-id="1017f-117">Perform grouped joins</span></span>](perform-grouped-joins.md)  
- [<span data-ttu-id="1017f-118">匿名型別</span><span class="sxs-lookup"><span data-stu-id="1017f-118">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  