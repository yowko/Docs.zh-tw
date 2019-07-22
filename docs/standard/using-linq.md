---
title: LINQ (Language Integrated Query)
description: 了解 LINQ 如何將語言層級查詢功能和 API 提供給 C# 和 VB，來撰寫易懂的宣告式程式碼。
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: 2e4b23b7bf197c9984c53b2f4cc2acaa61731d38
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238637"
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="dcfac-103">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="dcfac-103">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="dcfac-104">這是什麼？</span><span class="sxs-lookup"><span data-stu-id="dcfac-104">What is it?</span></span>

<span data-ttu-id="dcfac-105">LINQ 將語言層級查詢功能和[較高順序的函式](https://en.wikipedia.org/wiki/Higher-order_function) API 提供給 C# 和 VB，來撰寫易懂的宣告式程式碼。</span><span class="sxs-lookup"><span data-stu-id="dcfac-105">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and VB as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="dcfac-106">語言層級查詢語法︰</span><span class="sxs-lookup"><span data-stu-id="dcfac-106">Language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

```vb
Dim linqExperts = From p in programmers
                  Where p.IsNewToLINQ
                  Select New LINQExpert(p)
```

<span data-ttu-id="dcfac-107">使用 `IEnumerable<T>` API 的相同範例：</span><span class="sxs-lookup"><span data-stu-id="dcfac-107">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a><span data-ttu-id="dcfac-108">LINQ 簡單易懂</span><span class="sxs-lookup"><span data-stu-id="dcfac-108">LINQ is Expressive</span></span>

<span data-ttu-id="dcfac-109">假設您有一份寵物清單，但想要將它轉換成字典，讓您可以藉由其 `RFID` 值直接存取寵物。</span><span class="sxs-lookup"><span data-stu-id="dcfac-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="dcfac-110">傳統的命令式程式碼︰</span><span class="sxs-lookup"><span data-stu-id="dcfac-110">Traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

```vb
Dim petLookup = New Dictionary(Of Integer, Pet)()

For Each pet in pets
    petLookup.Add(pet.RFID, pet)
Next
```

<span data-ttu-id="dcfac-111">程式碼背後的目的不是用來建立新的 `Dictionary<int, Pet>` 並透過迴圈將其加入程式碼中，而是將現有的清單轉換為字典！</span><span class="sxs-lookup"><span data-stu-id="dcfac-111">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="dcfac-112">LINQ 會保留這項目的，而命令式程式碼不會。</span><span class="sxs-lookup"><span data-stu-id="dcfac-112">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="dcfac-113">對等的 LINQ 運算式︰</span><span class="sxs-lookup"><span data-stu-id="dcfac-113">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

<span data-ttu-id="dcfac-114">使用 LINQ 的程式碼之所以重要，是因為它在程式設計師思考時為目的和程式碼之間提供了平衡。</span><span class="sxs-lookup"><span data-stu-id="dcfac-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="dcfac-115">另一個好處是讓程式碼保持簡潔。</span><span class="sxs-lookup"><span data-stu-id="dcfac-115">Another bonus is code brevity.</span></span> <span data-ttu-id="dcfac-116">想像一下減少 1/3 程式碼基底的情況，就如同以上所做一樣。</span><span class="sxs-lookup"><span data-stu-id="dcfac-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="dcfac-117">很不錯，對吧？</span><span class="sxs-lookup"><span data-stu-id="dcfac-117">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="dcfac-118">LINQ 提供者簡化資料存取</span><span class="sxs-lookup"><span data-stu-id="dcfac-118">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="dcfac-119">在現實世界的軟體中，大部分的程序都圍繞在從某個來源處理資料 (資料庫、JSON、XML 等)。</span><span class="sxs-lookup"><span data-stu-id="dcfac-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="dcfac-120">通常這牽涉到針對每個資料來源學習新的 API，這可能很煩人。</span><span class="sxs-lookup"><span data-stu-id="dcfac-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="dcfac-121">LINQ 藉由將常見元素提取至查詢語法內，而該語法在哪一個資料來源中看起來都相同來簡化此工作。</span><span class="sxs-lookup"><span data-stu-id="dcfac-121">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="dcfac-122">請考慮下列項目︰尋找具有特定屬性值的所有 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="dcfac-122">Consider the following: finding all XML elements with a specific attribute value.</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

```vb
Public Shared Function FindAllElementsWithAttribute(documentRoot As XElement, elementName As String,
                                           attributeName As String, value As String) As IEnumerable(Of XElement)
    Return From el In documentRoot.Elements(elementName)
           Where el.Element(attributeName).ToString() = value
           Select el
End Function

```

<span data-ttu-id="dcfac-123">撰寫程式碼以手動周遊 XML 文件來執行此工作會是更大的挑戰。</span><span class="sxs-lookup"><span data-stu-id="dcfac-123">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="dcfac-124">與 XML 互動不是您可以使用 LINQ 提供者來執行的唯一工作。</span><span class="sxs-lookup"><span data-stu-id="dcfac-124">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="dcfac-125">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) 是相當基本的 MSSQL 伺服器資料庫物件關聯式對應程式 (ORM)。</span><span class="sxs-lookup"><span data-stu-id="dcfac-125">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="dcfac-126">[JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) 程式庫提供透過 LINQ 的具效率 JSON 文件周遊。</span><span class="sxs-lookup"><span data-stu-id="dcfac-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="dcfac-127">此外，如果沒有您所需的程式庫，您也可以[撰寫你自己的 LINQ 提供者](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))！</span><span class="sxs-lookup"><span data-stu-id="dcfac-127">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="dcfac-128">為何要使用查詢語法？</span><span class="sxs-lookup"><span data-stu-id="dcfac-128">Why Use the Query Syntax?</span></span>

<span data-ttu-id="dcfac-129">這是常常被人提起的問題。</span><span class="sxs-lookup"><span data-stu-id="dcfac-129">This is a question which often comes up.</span></span> <span data-ttu-id="dcfac-130">畢竟，這方法，</span><span class="sxs-lookup"><span data-stu-id="dcfac-130">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

<span data-ttu-id="dcfac-131">是比下列問題更簡潔︰</span><span class="sxs-lookup"><span data-stu-id="dcfac-131">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

```vb
Dim filteredItems = From item In myItems
                    Where item.Foo
                    Select item
```

<span data-ttu-id="dcfac-132">API 語法只是一個使用查詢語法的更簡潔方法嗎？</span><span class="sxs-lookup"><span data-stu-id="dcfac-132">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="dcfac-133">否。</span><span class="sxs-lookup"><span data-stu-id="dcfac-133">No.</span></span> <span data-ttu-id="dcfac-134">查詢語法可讓您使用 **let** 子句，允許您在運算式的範圍內導入及繫結變數，並在運算式的後續片段中使用它。</span><span class="sxs-lookup"><span data-stu-id="dcfac-134">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="dcfac-135">可以僅使用 API 語法來重新產生相同的程式碼，但很可能會產生難以閱讀的程式碼。</span><span class="sxs-lookup"><span data-stu-id="dcfac-135">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="dcfac-136">而這就帶出了一個問題，**您應該只使用查詢語法嗎？**</span><span class="sxs-lookup"><span data-stu-id="dcfac-136">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="dcfac-137">如果你符合下列條件，則此問題的答案為**是**...</span><span class="sxs-lookup"><span data-stu-id="dcfac-137">The answer to this question is **yes** if...</span></span>

* <span data-ttu-id="dcfac-138">現有的程式碼基底已經使用查詢語法</span><span class="sxs-lookup"><span data-stu-id="dcfac-138">Your existing codebase already uses the query syntax</span></span>
* <span data-ttu-id="dcfac-139">為了避免過於複雜，您需要在查詢內指定變數的範圍</span><span class="sxs-lookup"><span data-stu-id="dcfac-139">You need to scope variables within your queries due to complexity</span></span>
* <span data-ttu-id="dcfac-140">您偏好查詢語法，且它不會偏離程式碼基底</span><span class="sxs-lookup"><span data-stu-id="dcfac-140">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="dcfac-141">如果你符合下列條件，則此問題的答案為**否**...</span><span class="sxs-lookup"><span data-stu-id="dcfac-141">The answer to this question is **no** if...</span></span>

* <span data-ttu-id="dcfac-142">現有的程式碼基底已經使用 API 語法</span><span class="sxs-lookup"><span data-stu-id="dcfac-142">Your existing codebase already uses the API syntax</span></span>
* <span data-ttu-id="dcfac-143">您不需要在查詢內指定變數的範圍</span><span class="sxs-lookup"><span data-stu-id="dcfac-143">You have no need to scope variables within your queries</span></span>
* <span data-ttu-id="dcfac-144">您偏好 API 語法，且它不會影響程式碼基底</span><span class="sxs-lookup"><span data-stu-id="dcfac-144">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="dcfac-145">基本範例</span><span class="sxs-lookup"><span data-stu-id="dcfac-145">Essential Samples</span></span>

<span data-ttu-id="dcfac-146">如需 LINQ 範例的真正完整清單，請瀏覽 [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b) (LINQ 範例入門)。</span><span class="sxs-lookup"><span data-stu-id="dcfac-146">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span></span>

<span data-ttu-id="dcfac-147">以下是一些 LINQ 基本部分的簡單示範。</span><span class="sxs-lookup"><span data-stu-id="dcfac-147">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="dcfac-148">這些示範並不完整，因為 LINQ 提供的功能遠比此處說明的功能還多。</span><span class="sxs-lookup"><span data-stu-id="dcfac-148">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

* <span data-ttu-id="dcfac-149">基本要素 - `Where``Select`和 `Aggregate`：</span><span class="sxs-lookup"><span data-stu-id="dcfac-149">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

```csharp
// Filtering a list.
var germanShepards = dogs.Where(dog => dog.Breed == DogBreed.GermanShepard);

// Using the query syntax.
var queryGermanShepards = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepard
                          select dog;

// Mapping a list from type A to type B.
var cats = dogs.Select(dog => dog.TurnIntoACat());

// Using the query syntax.
var queryCats = from dog in dogs
                select dog.TurnIntoACat();

// Summing the lengths of a set of strings.
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

```vb
' Filtering a list.
Dim germanShepards = dogs.Where(Function(dog) dog.Breed = DogBreed.GermanShepard)

' Using the query syntax.
Dim queryGermanShepards = From dog In dogs
                          Where dog.Breed = DogBreed.GermanShepard
                          Select dog

' Mapping a list from type A to type B.
Dim cats = dogs.Select(Function(dog) dog.TurnIntoACat())

' Using the query syntax.
Dim queryCats = From dog In dogs
                Select dog.TurnIntoACat()

' Summing the lengths of a set of strings.
Dim seed As Integer = 0
Dim sumOfStrings As Integer = strings.Aggregate(seed, Function(s1, s2) s1.Length + s2.Length)
```

* <span data-ttu-id="dcfac-150">簡維清單的清單︰</span><span class="sxs-lookup"><span data-stu-id="dcfac-150">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

* <span data-ttu-id="dcfac-151">兩組集合之間的聯集 (使用自訂比較子)︰</span><span class="sxs-lookup"><span data-stu-id="dcfac-151">Union between two sets (with custom comparator):</span></span>

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
        // Default hashcode is enough here, as these are simple objects.
        return d.GetHashCode();
    }
}

...

// Gets all the short-haired dogs between two different kennels.
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());
```

```vb
Public Class DogHairLengthComparer 
  Inherits IEqualityComparer(Of Dog)

  Public Function Equals(a As Dog,b As Dog) As Boolean
      If a Is Nothing AndAlso b Is Nothing Then
          Return True
      ElseIf (a Is Nothing AndAlso b IsNot Nothing) OrElse (a IsNot Nothing AndAlso b Is Nothing) Then
          Return False
      Else
          Return a.HairLengthType = b.HairLengthType
      End If
  End Function

  Public Function GetHashCode(d As Dog) As Integer
      ' Default hashcode is enough here, as these are simple objects.
      Return d.GetHashCode()
  End Function
End Class

...

' Gets all the short-haired dogs between two different kennels.
Dim allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, New DogHairLengthComparer())
```

* <span data-ttu-id="dcfac-152">兩組集合之間的交集︰</span><span class="sxs-lookup"><span data-stu-id="dcfac-152">Intersection between two sets:</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

```vb
' Gets the volunteers who spend share time with two humane societies.
Dim volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     New VolunteerTimeComparer())
```

* <span data-ttu-id="dcfac-153">排序︰</span><span class="sxs-lookup"><span data-stu-id="dcfac-153">Ordering:</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

```vb
' Get driving directions, ordering by if it's toll-free before estimated driving time.
Dim results = DirectionsProcessor.GetDirections(start, end).
                OrderBy(Function(direction) direction.HasNoTolls).
                ThenBy(Function(direction) direction.EstimatedTime)
```

* <span data-ttu-id="dcfac-154">最後是一項更進階的範例︰判斷兩個相同類型執行個體的屬性值是否相等 (從 [此 StackOverflow 文章](https://stackoverflow.com/a/844855)中借用並經過修改)：</span><span class="sxs-lookup"><span data-stu-id="dcfac-154">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

```csharp
public static bool PublicInstancePropertiesEqual<T>(this T self, T to, params string[] ignore) where T : class
{
    if (self == null || to == null)
    {
        return self == to;
    }
    
    // Selects the properties which have unequal values into a sequence of those properties.
    var unequalProperties = from property in typeof(T).GetProperties(BindingFlags.Public | BindingFlags.Instance)
                            where !ignore.Contains(property.Name)
                            let selfValue = property.GetValue(self, null)
                            let toValue = property.GetValue(to, null)
                            where !Equals(selfValue, toValue)
                            select property;
    return !unequalProperties.Any();
}
```

```vb
<System.Runtime.CompilerServices.Extension()> 
Public Function PublicInstancePropertiesEqual(Of T As Class)(self As T, [to] As T, ParamArray ignore As String()) As Boolean
    If self Is Nothing OrElse [to] Is Nothing Then
        Return self Is [to]
    End If

    ' Selects the properties which have unequal values into a sequence of those properties.
    Dim unequalProperties = From [property] In GetType(T).GetProperties(BindingFlags.Public Or BindingFlags.Instance) 
                            Where Not ignore.Contains([property].Name)
                            Let selfValue = [property].GetValue(self, Nothing)
                            Let toValue = [property].GetValue([to], Nothing)
                            Where Not Equals(selfValue, toValue) Select [property]
    Return Not unequalProperties.Any()
End Function
```

## <a name="plinq"></a><span data-ttu-id="dcfac-155">PLINQ</span><span class="sxs-lookup"><span data-stu-id="dcfac-155">PLINQ</span></span>

<span data-ttu-id="dcfac-156">PLINQ 或 Parallel LINQ，都是 LINQ 運算式的平行執行引擎。</span><span class="sxs-lookup"><span data-stu-id="dcfac-156">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="dcfac-157">換句話說，標準 LINQ 運算式可以在任意數目的執行緒上進行完整的平行處理。</span><span class="sxs-lookup"><span data-stu-id="dcfac-157">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="dcfac-158">這是透過在執行運算式之前呼叫 `AsParallel()` 所完成的。</span><span class="sxs-lookup"><span data-stu-id="dcfac-158">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="dcfac-159">請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="dcfac-159">Consider the following:</span></span>

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

```vb
Public Shared GetAllFacebookUserLikesMessage(facebookUsers As IEnumerable(Of FacebookUser)) As String
{
    Dim seed As UInt64 = 0

    Dim threadAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim threadResultAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim resultSelector As Func(Of Uint64, string) = Function(total) $"Facebook has {total} likes!"

    Return facebookUsers.AsParallel().
                        Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector)
}
```

<span data-ttu-id="dcfac-160">此程式碼會視需要來跨系統執行緒進行 `facebookUsers` 分割、平行加總每個執行緒上的總相似項目、加總每個執行緒所計算的結果，並將結果投射至良好的字串。</span><span class="sxs-lookup"><span data-stu-id="dcfac-160">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="dcfac-161">以圖表形式︰</span><span class="sxs-lookup"><span data-stu-id="dcfac-161">In diagram form:</span></span>

![PLINQ 圖表](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="dcfac-163">可以輕鬆地透過 LINQ 表示可平行的 CPU-bound 工作 (亦即，純虛擬函式，而且沒有任何副作用)，是 PLINQ 的絕佳候選項目。</span><span class="sxs-lookup"><span data-stu-id="dcfac-163">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="dcfac-164">針對 _do_ 會產生副作用的工作，請考慮使用 [Task Parallel Library (TPL)](./parallel-programming/task-parallel-library-tpl.md) (工作平行程式庫)。</span><span class="sxs-lookup"><span data-stu-id="dcfac-164">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="dcfac-165">其他資源︰</span><span class="sxs-lookup"><span data-stu-id="dcfac-165">Further Resources:</span></span>

* [<span data-ttu-id="dcfac-166">101 LINQ 範例</span><span class="sxs-lookup"><span data-stu-id="dcfac-166">101 LINQ Samples</span></span>](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
* <span data-ttu-id="dcfac-167">[Linqpad](https://www.linqpad.net/)為 C#/F#/VB 的遊樂場環境和資料庫查詢引擎</span><span class="sxs-lookup"><span data-stu-id="dcfac-167">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/VB</span></span>
* <span data-ttu-id="dcfac-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/)，為學習 LINQ-to-object 如何實作的電子書</span><span class="sxs-lookup"><span data-stu-id="dcfac-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
