---
title: LINQ (Language Integrated Query)
description: "了解 LINQ 如何將語言層級查詢功能和 API 提供給 C# 和 VB，來撰寫易懂的宣告式程式碼。"
keywords: .NET, .NET Core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.translationtype: HT
ms.sourcegitcommit: ef6d1bf9a7153f7adf635d13b4dcfb7647ed2e33
ms.openlocfilehash: 1478b5dc5844cef0abfea44eba88a12801d32bd4
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---

# <a name="linq-language-integrated-query"></a><span data-ttu-id="38116-104">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="38116-104">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="38116-105">這是什麼？</span><span class="sxs-lookup"><span data-stu-id="38116-105">What is it?</span></span>

<span data-ttu-id="38116-106">LINQ 將語言層級查詢功能和[較高順序的函式](https://en.wikipedia.org/wiki/Higher-order_function) API 提供給 C# 和 VB，來撰寫易懂的宣告式程式碼。</span><span class="sxs-lookup"><span data-stu-id="38116-106">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and VB as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="38116-107">語言層級查詢語法︰</span><span class="sxs-lookup"><span data-stu-id="38116-107">Language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

<span data-ttu-id="38116-108">使用 `IEnumerable<T>` API 的相同範例：</span><span class="sxs-lookup"><span data-stu-id="38116-108">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a><span data-ttu-id="38116-109">LINQ 簡單易懂</span><span class="sxs-lookup"><span data-stu-id="38116-109">LINQ is Expressive</span></span>

<span data-ttu-id="38116-110">假設您有一份寵物清單，但想要將它轉換成字典，讓您可以藉由其 `RFID` 值直接存取寵物。</span><span class="sxs-lookup"><span data-stu-id="38116-110">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="38116-111">傳統的命令式程式碼︰</span><span class="sxs-lookup"><span data-stu-id="38116-111">Traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

<span data-ttu-id="38116-112">程式碼背後的目的不是用來建立新的 `Dictionary<int, Pet>` 並透過迴圈將其加入程式碼中，而是將現有的清單轉換為字典！</span><span class="sxs-lookup"><span data-stu-id="38116-112">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="38116-113">LINQ 會保留這項目的，而命令式程式碼不會。</span><span class="sxs-lookup"><span data-stu-id="38116-113">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="38116-114">對等的 LINQ 運算式︰</span><span class="sxs-lookup"><span data-stu-id="38116-114">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

<span data-ttu-id="38116-115">使用 LINQ 的程式碼之所以重要，是因為它在程式設計師思考時為目的和程式碼之間提供了平衡。</span><span class="sxs-lookup"><span data-stu-id="38116-115">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="38116-116">另一個好處是讓程式碼保持簡潔。</span><span class="sxs-lookup"><span data-stu-id="38116-116">Another bonus is code brevity.</span></span> <span data-ttu-id="38116-117">想像一下減少 1/3 程式碼基底的情況，就如同以上所做一樣。</span><span class="sxs-lookup"><span data-stu-id="38116-117">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="38116-118">很不錯，對吧？</span><span class="sxs-lookup"><span data-stu-id="38116-118">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="38116-119">LINQ 提供者簡化資料存取</span><span class="sxs-lookup"><span data-stu-id="38116-119">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="38116-120">在現實世界的軟體中，大部分的程序都圍繞在從某個來源處理資料 (資料庫、JSON、XML 等)。</span><span class="sxs-lookup"><span data-stu-id="38116-120">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="38116-121">通常這牽涉到針對每個資料來源學習新的 API，這可能很煩人。</span><span class="sxs-lookup"><span data-stu-id="38116-121">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="38116-122">LINQ 藉由將常見元素提取至查詢語法內，而該語法在哪一個資料來源中看起來都相同來簡化此工作。</span><span class="sxs-lookup"><span data-stu-id="38116-122">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="38116-123">請考慮下列項目︰尋找具有特定屬性值的所有 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="38116-123">Consider the following: finding all XML elements with a specific attribute value.</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

<span data-ttu-id="38116-124">撰寫程式碼以手動周遊 XML 文件來執行此工作會是更大的挑戰。</span><span class="sxs-lookup"><span data-stu-id="38116-124">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="38116-125">與 XML 互動不是您可以使用 LINQ 提供者來執行的唯一工作。</span><span class="sxs-lookup"><span data-stu-id="38116-125">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="38116-126">[Linq to SQL](https://msdn.microsoft.com/library/bb386976.aspx) 是相當基本的 MSSQL 伺服器資料庫物件關聯式對應程式 (ORM)。</span><span class="sxs-lookup"><span data-stu-id="38116-126">[Linq to SQL](https://msdn.microsoft.com/library/bb386976.aspx) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="38116-127">[JSON.NET](http://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) 程式庫提供透過 LINQ 的具效率 JSON 文件周遊。</span><span class="sxs-lookup"><span data-stu-id="38116-127">The [JSON.NET](http://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="38116-128">此外，如果沒有您所需的程式庫，您也可以[撰寫你自己的 LINQ 提供者](https://msdn.microsoft.com/library/Bb546158.aspx)！</span><span class="sxs-lookup"><span data-stu-id="38116-128">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://msdn.microsoft.com/library/Bb546158.aspx)!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="38116-129">為何要使用查詢語法？</span><span class="sxs-lookup"><span data-stu-id="38116-129">Why Use the Query Syntax?</span></span>

<span data-ttu-id="38116-130">這是常常被人提起的問題。</span><span class="sxs-lookup"><span data-stu-id="38116-130">This is a question which often comes up.</span></span> <span data-ttu-id="38116-131">畢竟，這方法，</span><span class="sxs-lookup"><span data-stu-id="38116-131">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

<span data-ttu-id="38116-132">是比下列問題更簡潔︰</span><span class="sxs-lookup"><span data-stu-id="38116-132">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

<span data-ttu-id="38116-133">API 語法只是一個使用查詢語法的更簡潔方法嗎？</span><span class="sxs-lookup"><span data-stu-id="38116-133">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="38116-134">否。</span><span class="sxs-lookup"><span data-stu-id="38116-134">No.</span></span> <span data-ttu-id="38116-135">查詢語法可讓您使用 **let** 子句，可使用運算式的後續部分，讓您將變數導入並將其繫結至運算式的範圍中。</span><span class="sxs-lookup"><span data-stu-id="38116-135">The query syntax allows for the use the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="38116-136">可以僅使用 API 語法來重新產生相同的程式碼，但很可能會產生難以閱讀的程式碼。</span><span class="sxs-lookup"><span data-stu-id="38116-136">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="38116-137">而這就帶出了一個問題，**您應該只使用查詢語法嗎？**</span><span class="sxs-lookup"><span data-stu-id="38116-137">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="38116-138">如果你符合下列條件，則此問題的答案為**是**...</span><span class="sxs-lookup"><span data-stu-id="38116-138">The answer to this question is **yes** if...</span></span>

*   <span data-ttu-id="38116-139">現有的程式碼基底已經使用查詢語法</span><span class="sxs-lookup"><span data-stu-id="38116-139">Your existing codebase already uses the query syntax</span></span>
*   <span data-ttu-id="38116-140">為了避免過於複雜，您需要在查詢內指定變數的範圍</span><span class="sxs-lookup"><span data-stu-id="38116-140">You need to scope variables within your queries due to complexity</span></span>
*   <span data-ttu-id="38116-141">您偏好查詢語法，且它不會偏離程式碼基底</span><span class="sxs-lookup"><span data-stu-id="38116-141">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="38116-142">如果你符合下列條件，則此問題的答案為**否**...</span><span class="sxs-lookup"><span data-stu-id="38116-142">The answer to this question is **no** if...</span></span>

*   <span data-ttu-id="38116-143">現有的程式碼基底已經使用 API 語法</span><span class="sxs-lookup"><span data-stu-id="38116-143">Your existing codebase already uses the API syntax</span></span>
*   <span data-ttu-id="38116-144">您不需要在查詢內指定變數的範圍</span><span class="sxs-lookup"><span data-stu-id="38116-144">You have no need to scope variables within your queries</span></span>
*   <span data-ttu-id="38116-145">您偏好 API 語法，且它不會影響程式碼基底</span><span class="sxs-lookup"><span data-stu-id="38116-145">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="38116-146">基本範例</span><span class="sxs-lookup"><span data-stu-id="38116-146">Essential Samples</span></span>

<span data-ttu-id="38116-147">如需 LINQ 範例的真正完整清單，請瀏覽 [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b) (LINQ 範例入門)。</span><span class="sxs-lookup"><span data-stu-id="38116-147">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span></span>

<span data-ttu-id="38116-148">以下是一些 LINQ 基本部分的簡單示範。</span><span class="sxs-lookup"><span data-stu-id="38116-148">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="38116-149">這些示範並不完整，因為 LINQ 提供的功能遠比此處說明的功能還多。</span><span class="sxs-lookup"><span data-stu-id="38116-149">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

*   <span data-ttu-id="38116-150">基本要素 - `Where``Select`和 `Aggregate`：</span><span class="sxs-lookup"><span data-stu-id="38116-150">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

```csharp
// Filtering a list
var germanShepards = dogs.Where(dog => dog.Breed == DogBreed.GermanShepard);

// Using the query syntax
var queryGermanShepards = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepard
                          select dog;

// Mapping a list from type A to type B
var cats = dogs.Select(dog => dog.TurnIntoACat());

// Using the query syntax
var queryCats = from dog in dogs
                select dog.TurnIntoACat();

// Summing then lengths of a set of strings
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

*   <span data-ttu-id="38116-151">簡維清單的清單︰</span><span class="sxs-lookup"><span data-stu-id="38116-151">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

*   <span data-ttu-id="38116-152">兩組集合之間的聯集 (使用自訂比較子)︰</span><span class="sxs-lookup"><span data-stu-id="38116-152">Union between two sets (with custom comparator):</span></span>

```csharp
public class DogHairLengthComparer : IEqualityComparer<Dog>
{
    public bool Equals(Dog a, Dog b)
    {
        if (a == null && b == null)
        {
            return true;
        }
        else if ((a == null && b != null) ||
                 (a != null && b == null))
        {
            return false;
        }
        else
        {
            return a.HairLengthType == b.HairLengthType;
        }
    }

    public int GetHashCode(Dog d)
    {
        // default hashcode is enough here, as these are simple objects.
        return b.GetHashCode();
    }
}

...

// Gets all the short-haired dogs between two different kennels
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());
```

*   <span data-ttu-id="38116-153">兩組集合之間的交集︰</span><span class="sxs-lookup"><span data-stu-id="38116-153">Intersection between two sets:</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

*   <span data-ttu-id="38116-154">排序︰</span><span class="sxs-lookup"><span data-stu-id="38116-154">Ordering:</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

*   <span data-ttu-id="38116-155">最後是一項更進階的範例︰判斷兩個相同類型執行個體的屬性值是否相等 (從 [此 StackOverflow 文章](http://stackoverflow.com/a/844855)中借用並經過修改)：</span><span class="sxs-lookup"><span data-stu-id="38116-155">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](http://stackoverflow.com/a/844855)):</span></span>

```csharp
public static bool PublicInstancePropertiesEqual<T>(this T self, T to, params string[] ignore) where T : class
{
    if (self != null && to != null)
    {
        var type = typeof(T);
        var ignoreList = new List<string>(ignore);

        // Selects the properties which have unequal values into a sequence of those properties.
        var unequalProperties = from pi in type.GetProperties(BindingFlags.Public | BindingFlags.Instance)
                                where !ignoreList.Contains(pi.Name)
                                let selfValue = type.GetProperty(pi.Name).GetValue(self, null)
                                let toValue = type.GetProperty(pi.Name).GetValue(to, null)
                                where selfValue != toValue && (selfValue == null || !selfValue.Equals(toValue))
                                select new { Prop = pi.Name, selfValue, toValue };
        return !unequalProperties.Any();
    }

    return self == to;
}
```

## <a name="plinq"></a><span data-ttu-id="38116-156">PLINQ</span><span class="sxs-lookup"><span data-stu-id="38116-156">PLINQ</span></span>

<span data-ttu-id="38116-157">PLINQ 或 Parallel LINQ，都是 LINQ 運算式的平行執行引擎。</span><span class="sxs-lookup"><span data-stu-id="38116-157">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="38116-158">換句話說，普通的 LINQ 運算式可以在任意數目的執行緒之間進行完整的平行處理。</span><span class="sxs-lookup"><span data-stu-id="38116-158">In other words, a regular LINQ expressions can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="38116-159">這是透過在執行運算式之前呼叫 `AsParallel()` 所完成的。</span><span class="sxs-lookup"><span data-stu-id="38116-159">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="38116-160">請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="38116-160">Consider the following:</span></span>

```csharp
public static string GetAllFacebookUserLikesMessage(IEnumerable<FacebookUser> facebookUsers)
{
    var seed = default(UInt64);

    Func<UInt64, UInt64, UInt64> threadAccumulator = (t1, t2) => t1 + t2;
    Func<UInt64, UInt64, UInt64> threadResultAccumulator = (t1, t2) => t1 + t2;
    Func<Uint64, string> resultSelector = total => $"Facebook has {total} likes!";

    return facebookUsers.AsParallel()
                        .Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector);
}
```

<span data-ttu-id="38116-161">此程式碼會視需要來跨系統執行緒進行 `facebookUsers` 分割、平行加總每個執行緒上的總相似項目、加總每個執行緒所計算的結果，並將結果投射至良好的字串。</span><span class="sxs-lookup"><span data-stu-id="38116-161">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="38116-162">以圖表形式︰</span><span class="sxs-lookup"><span data-stu-id="38116-162">In diagram form:</span></span>

![PLINQ 圖表](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="38116-164">可以輕鬆地透過 LINQ 表示可平行的 CPU-bound 工作 (亦即，純虛擬函式，而且沒有任何副作用)，是 PLINQ 的絕佳候選項目。</span><span class="sxs-lookup"><span data-stu-id="38116-164">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="38116-165">針對 _do_ 會產生副作用的工作，請考慮使用 [Task Parallel Library (TPL)](https://msdn.microsoft.com/library/dd460717.aspx) (工作平行程式庫)。</span><span class="sxs-lookup"><span data-stu-id="38116-165">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](https://msdn.microsoft.com/library/dd460717.aspx).</span></span>

## <a name="further-resources"></a><span data-ttu-id="38116-166">其他資源︰</span><span class="sxs-lookup"><span data-stu-id="38116-166">Further Resources:</span></span>

*   [<span data-ttu-id="38116-167">101 LINQ 範例</span><span class="sxs-lookup"><span data-stu-id="38116-167">101 LINQ Samples</span></span>](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
*   <span data-ttu-id="38116-168">[Linqpad](https://www.linqpad.net/)為 C#/F#/VB 的遊樂場環境和資料庫查詢引擎</span><span class="sxs-lookup"><span data-stu-id="38116-168">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/VB</span></span>
*   <span data-ttu-id="38116-169">[EduLinq](http://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/)，為學習 LINQ-to-object 如何實作的電子書</span><span class="sxs-lookup"><span data-stu-id="38116-169">[EduLinq](http://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>

