---
title: 執行內部聯結
description: 如何執行內部聯結。
ms.date: 12/1/2016
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
ms.openlocfilehash: 9d372579e3c32964c588b6387b6d4e97f632a21f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="perform-inner-joins"></a><span data-ttu-id="277f3-103">執行內部聯結</span><span class="sxs-lookup"><span data-stu-id="277f3-103">Perform inner joins</span></span>

<span data-ttu-id="277f3-104">在關聯式資料庫術語中，*內部聯結*產生的結果集中，第一個集合的每個項目都會為第二個集合中的每個相符項目出現一次。</span><span class="sxs-lookup"><span data-stu-id="277f3-104">In relational database terms, an *inner join* produces a result set in which each element of the first collection appears one time for every matching element in the second collection.</span></span> <span data-ttu-id="277f3-105">如果第一個集合中的元素沒有相符的項目，就不會出現在結果集中。</span><span class="sxs-lookup"><span data-stu-id="277f3-105">If an element in the first collection has no matching elements, it does not appear in the result set.</span></span> <span data-ttu-id="277f3-106">C# 中 `join` 子句呼叫的 <xref:System.Linq.Enumerable.Join%2A> 方法會實作內部聯結。</span><span class="sxs-lookup"><span data-stu-id="277f3-106">The <xref:System.Linq.Enumerable.Join%2A> method, which is called by the `join` clause in C#, implements an inner join.</span></span>  
  
 <span data-ttu-id="277f3-107">本主題會示範如何執行內部聯結的四種變化︰</span><span class="sxs-lookup"><span data-stu-id="277f3-107">This topic shows you how to perform four variations of an inner join:</span></span>  
  
-   <span data-ttu-id="277f3-108">簡單內部聯結，根據簡單的索引鍵將兩個資料來源的項目相互關聯。</span><span class="sxs-lookup"><span data-stu-id="277f3-108">A simple inner join that correlates elements from two data sources based on a simple key.</span></span>  
  
-   <span data-ttu-id="277f3-109">內部聯結，根據「複合」的索引鍵將兩個資料來源的項目相互關聯。</span><span class="sxs-lookup"><span data-stu-id="277f3-109">An inner join that correlates elements from two data sources based on a *composite* key.</span></span> <span data-ttu-id="277f3-110">複合索引鍵，也就是由多個值組成的索引鍵，可讓您根據多個屬性將項目相互關聯。</span><span class="sxs-lookup"><span data-stu-id="277f3-110">A composite key, which is a key that consists of more than one value, enables you to correlate elements based on more than one property.</span></span>  
  
-   <span data-ttu-id="277f3-111">「多個聯結」，彼此附加的連續聯結作業。</span><span class="sxs-lookup"><span data-stu-id="277f3-111">A *multiple join* in which successive join operations are appended to each other.</span></span>  
  
-   <span data-ttu-id="277f3-112">使用群組聯結實作的內部聯結。</span><span class="sxs-lookup"><span data-stu-id="277f3-112">An inner join that is implemented by using a group join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="277f3-113">範例</span><span class="sxs-lookup"><span data-stu-id="277f3-113">Example</span></span>  
  
## <a name="simple-key-join-example"></a><span data-ttu-id="277f3-114">簡單索引鍵聯結範例</span><span class="sxs-lookup"><span data-stu-id="277f3-114">Simple key join example</span></span>  
 <span data-ttu-id="277f3-115">下例會建立兩個集合，包含兩個使用者定義型別的物件 `Person` 和 `Pet`。</span><span class="sxs-lookup"><span data-stu-id="277f3-115">The following example creates two collections that contain objects of two user-defined types, `Person` and `Pet`.</span></span> <span data-ttu-id="277f3-116">查詢會使用 C# 的 `join` 子句來比對 `Person` 物件與其 `Owner` 是 `Person` 的 `Pet` 物件。</span><span class="sxs-lookup"><span data-stu-id="277f3-116">The query uses the `join` clause in C# to match `Person` objects with `Pet` objects whose `Owner` is that `Person`.</span></span> <span data-ttu-id="277f3-117">C# 的 `select` 子句會定義產生物件的外觀。</span><span class="sxs-lookup"><span data-stu-id="277f3-117">The `select` clause in C# defines how the resulting objects will look.</span></span> <span data-ttu-id="277f3-118">本例中，產生的物件是由擁有者名字和寵物名字組成的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="277f3-118">In this example the resulting objects are anonymous types that consist of the owner's first name and the pet's name.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#1](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]  
  
 <span data-ttu-id="277f3-119">請注意，其 `LastName` 是 "Huff" 的 `Person` 物件不會出現在結果集中，因為沒有任何 `Pet` 物件的 `Pet.Owner` 等於 `Person`。</span><span class="sxs-lookup"><span data-stu-id="277f3-119">Note that the `Person` object whose `LastName` is "Huff" does not appear in the result set because there is no `Pet` object that has `Pet.Owner` equal to that `Person`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="277f3-120">範例</span><span class="sxs-lookup"><span data-stu-id="277f3-120">Example</span></span>  
  
## <a name="composite-key-join-example"></a><span data-ttu-id="277f3-121">複合索引鍵聯結範例</span><span class="sxs-lookup"><span data-stu-id="277f3-121">Composite key join example</span></span>  
 <span data-ttu-id="277f3-122">非僅根據一個屬性相互關聯的項目，您可以使用複合索引鍵根據多個屬性來比較項目。</span><span class="sxs-lookup"><span data-stu-id="277f3-122">Instead of correlating elements based on just one property, you can use a composite key to compare elements based on multiple properties.</span></span> <span data-ttu-id="277f3-123">若要這樣做，請為每個集合指定索引鍵選取器函式，以傳回包含要比較屬性的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="277f3-123">To do this, specify the key selector function for each collection to return an anonymous type that consists of the properties you want to compare.</span></span> <span data-ttu-id="277f3-124">如果您標示屬性，它們在每個索引鍵的匿名型別中必須有相同的標籤。</span><span class="sxs-lookup"><span data-stu-id="277f3-124">If you label the properties, they must have the same label in each key's anonymous type.</span></span> <span data-ttu-id="277f3-125">屬性也必須以相同的順序出現。</span><span class="sxs-lookup"><span data-stu-id="277f3-125">The properties must also appear in the same order.</span></span>  
  
 <span data-ttu-id="277f3-126">下例會使用 `Employee` 物件清單和 `Student` 物件清單來判斷哪些員工也是學生。</span><span class="sxs-lookup"><span data-stu-id="277f3-126">The following example uses a list of `Employee` objects and a list of `Student` objects to determine which employees are also students.</span></span> <span data-ttu-id="277f3-127">這兩種類型都有 <xref:System.String> 類型的 `FirstName` 和 `LastName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="277f3-127">Both of these types have a `FirstName` and a `LastName` property of type <xref:System.String>.</span></span> <span data-ttu-id="277f3-128">從每個清單的項目建立聯結索引鍵的函式會傳回包含每個項目的 `FirstName` 和 `LastName` 屬性的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="277f3-128">The functions that create the join keys from each list's elements return an anonymous type that consists of the `FirstName` and `LastName` properties of each element.</span></span> <span data-ttu-id="277f3-129">聯結作業會比較這些複合索引鍵是否相等，並傳回每份清單中名字和姓氏相符的物件配對。</span><span class="sxs-lookup"><span data-stu-id="277f3-129">The join operation compares these composite keys for equality and returns pairs of objects from each list where both the first name and the last name match.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#2](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="277f3-130">範例</span><span class="sxs-lookup"><span data-stu-id="277f3-130">Example</span></span>  
  
## <a name="multiple-join-example"></a><span data-ttu-id="277f3-131">多個聯結範例</span><span class="sxs-lookup"><span data-stu-id="277f3-131">Multiple join example</span></span>  
 <span data-ttu-id="277f3-132">彼此可以附加任何數目的聯結作業，以執行多個聯結。</span><span class="sxs-lookup"><span data-stu-id="277f3-132">Any number of join operations can be appended to each other to perform a multiple join.</span></span> <span data-ttu-id="277f3-133">C# 中每個 `join` 子句都會相互關聯指定的資料來源與上一個聯結的結果。</span><span class="sxs-lookup"><span data-stu-id="277f3-133">Each `join` clause in C# correlates a specified data source with the results of the previous join.</span></span>  
  
 <span data-ttu-id="277f3-134">下例會建立三個集合︰`Person` 物件清單、`Cat` 物件清單和 `Dog` 物件清單。</span><span class="sxs-lookup"><span data-stu-id="277f3-134">The following example creates three collections: a list of `Person` objects, a list of `Cat` objects, and a list of `Dog` objects.</span></span>  
  
 <span data-ttu-id="277f3-135">C# 的第一個 `join` 子句會根據符合 `Cat.Owner` 的 `Person` 物件比對人員和貓。</span><span class="sxs-lookup"><span data-stu-id="277f3-135">The first `join` clause in C# matches people and cats based on a `Person` object matching `Cat.Owner`.</span></span> <span data-ttu-id="277f3-136">它會傳回一系列包含 `Person` 物件和 `Cat.Name` 的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="277f3-136">It returns a sequence of anonymous types that contain the `Person` object and `Cat.Name`.</span></span>  
  
 <span data-ttu-id="277f3-137">C# 的第二個 `join` 子句會根據以型別 `Person` 的 `Owner` 屬性組成的複合索引鍵和動物名稱的第一個字母，相互關聯第一個聯結傳回的匿名型別與所提供狗清單的 `Dog` 物件。</span><span class="sxs-lookup"><span data-stu-id="277f3-137">The second `join` clause in C# correlates the anonymous types returned by the first join with `Dog` objects in the supplied list of dogs, based on a composite key that consists of the `Owner` property of type `Person`, and the first letter of the animal's name.</span></span> <span data-ttu-id="277f3-138">它會傳回一系列包含每個相符配對的 `Cat.Name` 和 `Dog.Name` 屬性的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="277f3-138">It returns a sequence of anonymous types that contain the `Cat.Name` and `Dog.Name` properties from each matching pair.</span></span> <span data-ttu-id="277f3-139">因為這是內部聯結，所以只會傳回第一個資料來源中在第二個資料來源中有相符項目的這些物件。</span><span class="sxs-lookup"><span data-stu-id="277f3-139">Because this is an inner join, only those objects from the first data source that have a match in the second data source are returned.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#3](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="277f3-140">範例</span><span class="sxs-lookup"><span data-stu-id="277f3-140">Example</span></span>  
  
## <a name="inner-join-by-using-grouped-join-example"></a><span data-ttu-id="277f3-141">使用群組聯結的內部聯結範例</span><span class="sxs-lookup"><span data-stu-id="277f3-141">Inner join by using grouped join example</span></span>  
 <span data-ttu-id="277f3-142">下例會示範如何使用群組聯結實作內部聯結。</span><span class="sxs-lookup"><span data-stu-id="277f3-142">The following example shows you how to implement an inner join by using a group join.</span></span>  
  
 <span data-ttu-id="277f3-143">在 `query1` 中，`Person` 物件清單是根據符合 `Pet.Owner` 屬性的 `Person` 以群組方式聯結至 `Pet` 物件清單。</span><span class="sxs-lookup"><span data-stu-id="277f3-143">In `query1`, the list of `Person` objects is group-joined to the list of `Pet` objects based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="277f3-144">群組聯結會建立中繼群組的集合，其中每個群組都包含一個 `Person` 物件和一系列的相符 `Pet` 物件。</span><span class="sxs-lookup"><span data-stu-id="277f3-144">The group join creates a collection of intermediate groups, where each group consists of a `Person` object and a sequence of matching `Pet` objects.</span></span>  
  
 <span data-ttu-id="277f3-145">將第二個 `from` 子句加入查詢中，這個系列的序列就會結合 (或扁平化) 成一個較長的序列。</span><span class="sxs-lookup"><span data-stu-id="277f3-145">By adding a second `from` clause to the query, this sequence of sequences is combined (or flattened) into one longer sequence.</span></span> <span data-ttu-id="277f3-146">最終序列的項目型別是由 `select` 子句指定。</span><span class="sxs-lookup"><span data-stu-id="277f3-146">The type of the elements of the final sequence is specified by the `select` clause.</span></span> <span data-ttu-id="277f3-147">本例中的型別是匿名型別，其包含每個相符配對的 `Person.FirstName` 和 `Pet.Name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="277f3-147">In this example, that type is an anonymous type that consists of the `Person.FirstName` and `Pet.Name` properties for each matching pair.</span></span>  
  
 <span data-ttu-id="277f3-148">`query1` 的結果相當於使用不含 `into` 子句的 `join` 子句執行內部聯結所取得的結果集。</span><span class="sxs-lookup"><span data-stu-id="277f3-148">The result of `query1` is equivalent to the result set that would have been obtained by using the `join` clause without the `into` clause to perform an inner join.</span></span> <span data-ttu-id="277f3-149">`query2` 變數會示範此對等查詢。</span><span class="sxs-lookup"><span data-stu-id="277f3-149">The `query2` variable demonstrates this equivalent query.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#4](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="277f3-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="277f3-150">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="277f3-151">執行群組聯結</span><span class="sxs-lookup"><span data-stu-id="277f3-151">Perform grouped joins</span></span>](perform-grouped-joins.md)  
 [<span data-ttu-id="277f3-152">執行左方外部聯結</span><span class="sxs-lookup"><span data-stu-id="277f3-152">Perform left outer joins</span></span>](perform-left-outer-joins.md)  
 [<span data-ttu-id="277f3-153">匿名型別</span><span class="sxs-lookup"><span data-stu-id="277f3-153">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
