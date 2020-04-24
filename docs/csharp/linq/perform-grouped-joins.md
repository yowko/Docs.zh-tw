---
title: 執行群組聯結 (C# 中的 LINQ)
description: 了解如何使用 C# 中的 LINQ 執行群組聯結。
ms.date: 04/22/2020
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: 740a861da7dfb9653a874d5baf67eeb2030555b4
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135746"
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="27b8f-103">執行群組聯結</span><span class="sxs-lookup"><span data-stu-id="27b8f-103">Perform grouped joins</span></span>

<span data-ttu-id="27b8f-104">群組聯結適合用來產生階層式資料結構。</span><span class="sxs-lookup"><span data-stu-id="27b8f-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="27b8f-105">它會配對第一個集合中的項目和第二個集合中一組相互關聯的項目。</span><span class="sxs-lookup"><span data-stu-id="27b8f-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>

<span data-ttu-id="27b8f-106">例如，名為 `Student` 的類別或關聯式資料庫資料表可能包含兩個欄位︰`Id` 和 `Name`。</span><span class="sxs-lookup"><span data-stu-id="27b8f-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="27b8f-107">名為 `Course` 的第二個類別或關聯式資料庫資料表可能包含兩個欄位︰`StudentId` 和 `CourseTitle`。</span><span class="sxs-lookup"><span data-stu-id="27b8f-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="27b8f-108">這兩個資料來源的群組聯結，以相符的 `Student.Id` 和 `Course.StudentId` 為基礎，會將每個 `Student` 分組到 `Course` 物件集合 (可能是空的)。</span><span class="sxs-lookup"><span data-stu-id="27b8f-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>

> [!NOTE]
> <span data-ttu-id="27b8f-109">無論第二個集合中是否找到相互關聯的項目，第一個集合的每個項目都會出現在群組聯結的結果集中。</span><span class="sxs-lookup"><span data-stu-id="27b8f-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="27b8f-110">如果找不到任何相互關聯的項目，該項目之相互關聯項目的序列是空的。</span><span class="sxs-lookup"><span data-stu-id="27b8f-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="27b8f-111">因此，結果選取器可以存取第一個集合的每個項目。</span><span class="sxs-lookup"><span data-stu-id="27b8f-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="27b8f-112">和非群組聯結中的結果選取器不同，它無法存取和第二個集合沒有相符項目的第一個集合項目。</span><span class="sxs-lookup"><span data-stu-id="27b8f-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>

> [!WARNING]
> <span data-ttu-id="27b8f-113"><xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType>在傳統關係資料庫詞彙中沒有直接的對等用法。</span><span class="sxs-lookup"><span data-stu-id="27b8f-113"><xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType> has no direct equivalent in traditional relational database terms.</span></span> <span data-ttu-id="27b8f-114">不過，這個方法會執行內部聯結和左方外部聯結的超集合。</span><span class="sxs-lookup"><span data-stu-id="27b8f-114">However, this method does implement a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="27b8f-115">這兩種作業都可以根據群組聯結來撰寫。</span><span class="sxs-lookup"><span data-stu-id="27b8f-115">Both of these operations can be written in terms of a grouped join.</span></span> <span data-ttu-id="27b8f-116">如需詳細資訊，請參閱[Join 作業](../programming-guide/concepts/linq/join-operations.md)和[Entity Framework Core，GroupJoin](https://docs.microsoft.com/ef/core/querying/complex-query-operators#groupjoin)。</span><span class="sxs-lookup"><span data-stu-id="27b8f-116">For more information, see [Join Operations](../programming-guide/concepts/linq/join-operations.md) and [Entity Framework Core, GroupJoin](https://docs.microsoft.com/ef/core/querying/complex-query-operators#groupjoin).</span></span>

<span data-ttu-id="27b8f-117">本文中的第一個範例示範如何執行群組聯結。</span><span class="sxs-lookup"><span data-stu-id="27b8f-117">The first example in this article shows you how to perform a group join.</span></span> <span data-ttu-id="27b8f-118">第二個範例會示範如何使用群組聯結建立 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="27b8f-118">The second example shows you how to use a group join to create XML elements.</span></span>

## <a name="example---group-join"></a><span data-ttu-id="27b8f-119">範例 - 群組聯結</span><span class="sxs-lookup"><span data-stu-id="27b8f-119">Example - Group join</span></span>

<span data-ttu-id="27b8f-120">下例會根據符合 `Pet.Owner` 屬性的 `Person`，執行型別 `Person` 和 `Pet` 的物件群組聯結。</span><span class="sxs-lookup"><span data-stu-id="27b8f-120">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="27b8f-121">和非群組聯結不同，它會針對每個相符項目產生項目配對，群組聯結只會針對第一個集合的每個項目產生結果物件，在本例中為 `Person` 物件。</span><span class="sxs-lookup"><span data-stu-id="27b8f-121">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="27b8f-122">第二個集合的對應項目，在本例中為 `Pet` 物件，會群組成集合。</span><span class="sxs-lookup"><span data-stu-id="27b8f-122">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="27b8f-123">最後，結果選取器函式會為每個符合項目建立匿名型別，包含 `Person.FirstName` 和 `Pet` 物件集合。</span><span class="sxs-lookup"><span data-stu-id="27b8f-123">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a><span data-ttu-id="27b8f-124">範例 - 群組聯結以建立 XML</span><span class="sxs-lookup"><span data-stu-id="27b8f-124">Example - Group join to create XML</span></span>

<span data-ttu-id="27b8f-125">群組聯結最適合使用 LINQ to XML 建立 XML。</span><span class="sxs-lookup"><span data-stu-id="27b8f-125">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="27b8f-126">下例類似上例，只不過它不是建立匿名型別，而是結果選取器函式會建立表示已加入物件的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="27b8f-126">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a><span data-ttu-id="27b8f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27b8f-127">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="27b8f-128">執行內部聯結</span><span class="sxs-lookup"><span data-stu-id="27b8f-128">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="27b8f-129">執行左方外部聯結</span><span class="sxs-lookup"><span data-stu-id="27b8f-129">Perform left outer joins</span></span>](perform-left-outer-joins.md)
- [<span data-ttu-id="27b8f-130">匿名型別</span><span class="sxs-lookup"><span data-stu-id="27b8f-130">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
