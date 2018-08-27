---
title: 執行群組聯結 (C# 中的 LINQ)
description: 了解如何使用 C# 中的 LINQ 執行群組聯結。
ms.date: 12/1/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: f65faabcb039e186a2e0d18dda4373263ffd0b8b
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "42911921"
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="d4389-103">執行群組聯結</span><span class="sxs-lookup"><span data-stu-id="d4389-103">Perform grouped joins</span></span>

<span data-ttu-id="d4389-104">群組聯結適合用來產生階層式資料結構。</span><span class="sxs-lookup"><span data-stu-id="d4389-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="d4389-105">它會配對第一個集合中的項目和第二個集合中一組相互關聯的項目。</span><span class="sxs-lookup"><span data-stu-id="d4389-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>

<span data-ttu-id="d4389-106">例如，名為 `Student` 的類別或關聯式資料庫資料表可能包含兩個欄位︰`Id` 和 `Name`。</span><span class="sxs-lookup"><span data-stu-id="d4389-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="d4389-107">名為 `Course` 的第二個類別或關聯式資料庫資料表可能包含兩個欄位︰`StudentId` 和 `CourseTitle`。</span><span class="sxs-lookup"><span data-stu-id="d4389-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="d4389-108">這兩個資料來源的群組聯結，以相符的 `Student.Id` 和 `Course.StudentId` 為基礎，會將每個 `Student` 分組到 `Course` 物件集合 (可能是空的)。</span><span class="sxs-lookup"><span data-stu-id="d4389-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>

> [!NOTE]
> <span data-ttu-id="d4389-109">無論第二個集合中是否找到相互關聯的項目，第一個集合的每個項目都會出現在群組聯結的結果集中。</span><span class="sxs-lookup"><span data-stu-id="d4389-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="d4389-110">如果找不到任何相互關聯的項目，該項目之相互關聯項目的序列是空的。</span><span class="sxs-lookup"><span data-stu-id="d4389-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="d4389-111">因此，結果選取器可以存取第一個集合的每個項目。</span><span class="sxs-lookup"><span data-stu-id="d4389-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="d4389-112">和非群組聯結中的結果選取器不同，它無法存取和第二個集合沒有相符項目的第一個集合項目。</span><span class="sxs-lookup"><span data-stu-id="d4389-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>

<span data-ttu-id="d4389-113">本文中的第一個範例示範如何執行群組聯結。</span><span class="sxs-lookup"><span data-stu-id="d4389-113">The first example in this article shows you how to perform a group join.</span></span> <span data-ttu-id="d4389-114">第二個範例會示範如何使用群組聯結建立 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="d4389-114">The second example shows you how to use a group join to create XML elements.</span></span>

## <a name="example---group-join"></a><span data-ttu-id="d4389-115">範例 - 群組聯結</span><span class="sxs-lookup"><span data-stu-id="d4389-115">Example - Group join</span></span>

<span data-ttu-id="d4389-116">下例會根據符合 `Pet.Owner` 屬性的 `Person`，執行型別 `Person` 和 `Pet` 的物件群組聯結。</span><span class="sxs-lookup"><span data-stu-id="d4389-116">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="d4389-117">和非群組聯結不同，它會針對每個相符項目產生項目配對，群組聯結只會針對第一個集合的每個項目產生結果物件，在本例中為 `Person` 物件。</span><span class="sxs-lookup"><span data-stu-id="d4389-117">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="d4389-118">第二個集合的對應項目，在本例中為 `Pet` 物件，會群組成集合。</span><span class="sxs-lookup"><span data-stu-id="d4389-118">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="d4389-119">最後，結果選取器函式會為每個符合項目建立匿名型別，包含 `Person.FirstName` 和 `Pet` 物件集合。</span><span class="sxs-lookup"><span data-stu-id="d4389-119">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a><span data-ttu-id="d4389-120">範例 - 群組聯結以建立 XML</span><span class="sxs-lookup"><span data-stu-id="d4389-120">Example - Group join to create XML</span></span>

<span data-ttu-id="d4389-121">群組聯結最適合使用 LINQ to XML 建立 XML。</span><span class="sxs-lookup"><span data-stu-id="d4389-121">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="d4389-122">下例類似上例，只不過它不是建立匿名型別，而是結果選取器函式會建立表示已加入物件的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="d4389-122">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a><span data-ttu-id="d4389-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4389-123">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>  
- <xref:System.Linq.Enumerable.GroupJoin%2A>  
- [<span data-ttu-id="d4389-124">執行內部聯結</span><span class="sxs-lookup"><span data-stu-id="d4389-124">Perform inner joins</span></span>](perform-inner-joins.md)  
- [<span data-ttu-id="d4389-125">執行左方外部聯結</span><span class="sxs-lookup"><span data-stu-id="d4389-125">Perform left outer joins</span></span>](perform-left-outer-joins.md)  
- [<span data-ttu-id="d4389-126">匿名型別</span><span class="sxs-lookup"><span data-stu-id="d4389-126">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  