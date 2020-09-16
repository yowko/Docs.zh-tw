---
title: LINQ 總覽-.NET
description: " (LINQ) 的語言整合式查詢提供語言層級的查詢功能，以及可讓您撰寫明確宣告式程式碼的高序位函式 API （c # 和 Visual Basic）。"
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.openlocfilehash: 65370a2bd21e2474af4cb070bb8d82a167f10070
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554992"
---
# <a name="linq-overview"></a><span data-ttu-id="fe3eb-103">LINQ 概觀</span><span class="sxs-lookup"><span data-stu-id="fe3eb-103">LINQ overview</span></span>

<span data-ttu-id="fe3eb-104"> (LINQ) 的語言整合式查詢提供語言層級的查詢功能，以及可讓您撰寫明確宣告式程式碼的 [高序位函式](https://en.wikipedia.org/wiki/Higher-order_function) API （c # 和 Visual Basic）。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-104">Language-Integrated Query (LINQ) provides language-level querying capabilities, and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and Visual Basic, that enable you to write expressive declarative code.</span></span>

## <a name="language-level-query-syntax"></a><span data-ttu-id="fe3eb-105">語言層級查詢語法</span><span class="sxs-lookup"><span data-stu-id="fe3eb-105">Language-level query syntax</span></span>

<span data-ttu-id="fe3eb-106">這是語言層級的查詢語法：</span><span class="sxs-lookup"><span data-stu-id="fe3eb-106">This is the language-level query syntax:</span></span>

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

<span data-ttu-id="fe3eb-107">這是使用 API 的相同範例 `IEnumerable<T>` ：</span><span class="sxs-lookup"><span data-stu-id="fe3eb-107">This is the same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a><span data-ttu-id="fe3eb-108">LINQ 為表達</span><span class="sxs-lookup"><span data-stu-id="fe3eb-108">LINQ is expressive</span></span>

<span data-ttu-id="fe3eb-109">假設您有一份寵物清單，但想要將它轉換成字典，讓您可以藉由其 `RFID` 值直接存取寵物。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="fe3eb-110">這是傳統的命令式程式碼：</span><span class="sxs-lookup"><span data-stu-id="fe3eb-110">This is traditional imperative code:</span></span>

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

<span data-ttu-id="fe3eb-111">程式碼背後的目的並不是透過迴圈來建立新的 `Dictionary<int, Pet>` 並新增至該程式碼，而是將現有的清單轉換成字典！</span><span class="sxs-lookup"><span data-stu-id="fe3eb-111">The intention behind the code isn't to create a new `Dictionary<int, Pet>` and add to it via a loop, it's to convert an existing list into a dictionary!</span></span> <span data-ttu-id="fe3eb-112">LINQ 會保留意圖，而命令式程式碼則不會。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-112">LINQ preserves the intention whereas the imperative code doesn't.</span></span>

<span data-ttu-id="fe3eb-113">這是對等的 LINQ 運算式：</span><span class="sxs-lookup"><span data-stu-id="fe3eb-113">This is the equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

<span data-ttu-id="fe3eb-114">使用 LINQ 的程式碼之所以重要，是因為它在程式設計師思考時為目的和程式碼之間提供了平衡。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="fe3eb-115">另一個好處是讓程式碼保持簡潔。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-115">Another bonus is code brevity.</span></span> <span data-ttu-id="fe3eb-116">想像一下減少 1/3 程式碼基底的情況，就如同以上所做一樣。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="fe3eb-117">太棒了，對吧？</span><span class="sxs-lookup"><span data-stu-id="fe3eb-117">Sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="fe3eb-118">LINQ 提供者簡化資料存取</span><span class="sxs-lookup"><span data-stu-id="fe3eb-118">LINQ providers simplify data access</span></span>

<span data-ttu-id="fe3eb-119">針對大量的軟體，大部分的工作都是處理來自某些來源 (資料庫、JSON、) XML 等等的資料。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, and so on).</span></span> <span data-ttu-id="fe3eb-120">通常這牽涉到針對每個資料來源學習新的 API，這可能很煩人。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="fe3eb-121">LINQ 簡化了這項工作，方法是將資料存取的通用元素抽象化成查詢語法，不論您選擇哪一種資料來源都一樣。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-121">LINQ simplifies this by abstracting common elements of data access into a query syntax that looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="fe3eb-122">這會尋找具有特定屬性值的所有 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="fe3eb-122">This finds all XML elements with a specific attribute value:</span></span>

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

<span data-ttu-id="fe3eb-123">撰寫程式碼以手動方式流覽 XML 檔以進行這項工作，是更具挑戰性的。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-123">Writing code to manually traverse the XML document to do this task would be far more challenging.</span></span>

<span data-ttu-id="fe3eb-124">與 XML 互動不是您唯一可以使用 LINQ 提供者進行的作業。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-124">Interacting with XML isn't the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="fe3eb-125">[Linq to SQL](../../framework/data/adonet/sql/linq/index.md) 是相當基本的 MSSQL 伺服器資料庫物件關聯式對應程式 (ORM)。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-125">[Linq to SQL](../../framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="fe3eb-126">[JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) 程式庫提供透過 LINQ 的具效率 JSON 文件周遊。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="fe3eb-127">此外，如果沒有可執行所需功能的程式庫，您也可以 [撰寫自己的 LINQ 提供者](/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))！</span><span class="sxs-lookup"><span data-stu-id="fe3eb-127">Furthermore, if there isn't a library that does what you need, you can also [write your own LINQ Provider](/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="reasons-to-use-the-query-syntax"></a><span data-ttu-id="fe3eb-128">使用查詢語法的原因</span><span class="sxs-lookup"><span data-stu-id="fe3eb-128">Reasons to use the query syntax</span></span>

<span data-ttu-id="fe3eb-129">為何要使用查詢語法？</span><span class="sxs-lookup"><span data-stu-id="fe3eb-129">Why use query syntax?</span></span> <span data-ttu-id="fe3eb-130">這是通常會出現的問題。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-130">This is a question that often comes up.</span></span> <span data-ttu-id="fe3eb-131">畢竟，下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="fe3eb-131">After all, the following code:</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

<span data-ttu-id="fe3eb-132">是比下列問題更簡潔︰</span><span class="sxs-lookup"><span data-stu-id="fe3eb-132">is a lot more concise than this:</span></span>

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

<span data-ttu-id="fe3eb-133">API 語法不是比較精確的查詢語法方式嗎？</span><span class="sxs-lookup"><span data-stu-id="fe3eb-133">Isn't the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="fe3eb-134">否。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-134">No.</span></span> <span data-ttu-id="fe3eb-135">查詢語法可讓您使用 **let** 子句，允許您在運算式的範圍內導入及繫結變數，並在運算式的後續片段中使用它。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-135">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="fe3eb-136">使用 API 語法來重現相同的程式碼可以完成，但很可能會導致難以閱讀的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-136">Reproducing the same code with only the API syntax can be done, but will most likely lead to code that's hard to read.</span></span>

<span data-ttu-id="fe3eb-137">而這就帶出了一個問題，**您應該只使用查詢語法嗎？**</span><span class="sxs-lookup"><span data-stu-id="fe3eb-137">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="fe3eb-138">如果有下列情況，則此問題的答案為 **yes** ：</span><span class="sxs-lookup"><span data-stu-id="fe3eb-138">The answer to this question is **yes** if:</span></span>

- <span data-ttu-id="fe3eb-139">您現有的程式碼基底已經使用查詢語法。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-139">Your existing codebase already uses the query syntax.</span></span>
- <span data-ttu-id="fe3eb-140">您必須在查詢中界定變數的範圍，因為複雜性太高。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-140">You need to scope variables within your queries because of complexity.</span></span>
- <span data-ttu-id="fe3eb-141">您偏好使用查詢語法，且它不會干擾您的程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-141">You prefer the query syntax and it won't distract from your codebase.</span></span>

<span data-ttu-id="fe3eb-142">如果你符合下列條件，則此問題的答案為**否**...</span><span class="sxs-lookup"><span data-stu-id="fe3eb-142">The answer to this question is **no** if...</span></span>

- <span data-ttu-id="fe3eb-143">現有的程式碼基底已經使用 API 語法</span><span class="sxs-lookup"><span data-stu-id="fe3eb-143">Your existing codebase already uses the API syntax</span></span>
- <span data-ttu-id="fe3eb-144">您不需要在查詢內指定變數的範圍</span><span class="sxs-lookup"><span data-stu-id="fe3eb-144">You have no need to scope variables within your queries</span></span>
- <span data-ttu-id="fe3eb-145">您偏好使用 API 語法，且它不會干擾您的程式碼基底</span><span class="sxs-lookup"><span data-stu-id="fe3eb-145">You prefer the API syntax and it won't distract from your codebase</span></span>

## <a name="essential-linq"></a><span data-ttu-id="fe3eb-146">基本 LINQ</span><span class="sxs-lookup"><span data-stu-id="fe3eb-146">Essential LINQ</span></span>

<span data-ttu-id="fe3eb-147">如需 LINQ 範例的真正完整清單，請瀏覽 [101 LINQ Samples](/samples/dotnet/try-samples/101-linq-samples/) (LINQ 範例入門)。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-147">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](/samples/dotnet/try-samples/101-linq-samples/).</span></span>

<span data-ttu-id="fe3eb-148">下列範例是 LINQ 的一些基本部分的快速示範。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-148">The following examples are a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="fe3eb-149">這並沒有完整的功能，因為 LINQ 提供的功能比這裡展示的還多。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-149">This is in no way comprehensive, as LINQ provides more functionality than what is showcased here.</span></span>

### <a name="the-bread-and-butter---where-select-and-aggregate"></a><span data-ttu-id="fe3eb-150">階層與基本要素- `Where` 、 `Select` 和 `Aggregate`</span><span class="sxs-lookup"><span data-stu-id="fe3eb-150">The bread and butter - `Where`, `Select`, and `Aggregate`</span></span>

```csharp
// Filtering a list.
var germanShepherds = dogs.Where(dog => dog.Breed == DogBreed.GermanShepherd);

// Using the query syntax.
var queryGermanShepherds = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepherd
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
Dim germanShepherds = dogs.Where(Function(dog) dog.Breed = DogBreed.GermanShepherd)

' Using the query syntax.
Dim queryGermanShepherds = From dog In dogs
                          Where dog.Breed = DogBreed.GermanShepherd
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

### <a name="flattening-a-list-of-lists"></a><span data-ttu-id="fe3eb-151">簡維清單清單</span><span class="sxs-lookup"><span data-stu-id="fe3eb-151">Flattening a list of lists</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

### <a name="union-between-two-sets-with-custom-comparator"></a><span data-ttu-id="fe3eb-152">兩個集合之間的聯集 (與自訂比較子) </span><span class="sxs-lookup"><span data-stu-id="fe3eb-152">Union between two sets (with custom comparator)</span></span>

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

### <a name="intersection-between-two-sets"></a><span data-ttu-id="fe3eb-153">兩個集合之間的交集</span><span class="sxs-lookup"><span data-stu-id="fe3eb-153">Intersection between two sets</span></span>

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

### <a name="ordering"></a><span data-ttu-id="fe3eb-154">排序</span><span class="sxs-lookup"><span data-stu-id="fe3eb-154">Ordering</span></span>

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

### <a name="equality-of-instance-properties"></a><span data-ttu-id="fe3eb-155">實例屬性的相等</span><span class="sxs-lookup"><span data-stu-id="fe3eb-155">Equality of instance properties</span></span>

<span data-ttu-id="fe3eb-156">最後是一項更進階的範例︰判斷兩個相同類型執行個體的屬性值是否相等 (從 [此 StackOverflow 文章](https://stackoverflow.com/a/844855)中借用並經過修改)：</span><span class="sxs-lookup"><span data-stu-id="fe3eb-156">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

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

## <a name="plinq"></a><span data-ttu-id="fe3eb-157">PLINQ</span><span class="sxs-lookup"><span data-stu-id="fe3eb-157">PLINQ</span></span>

<span data-ttu-id="fe3eb-158">PLINQ 或 Parallel LINQ，都是 LINQ 運算式的平行執行引擎。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-158">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="fe3eb-159">換句話說，標準 LINQ 運算式可以在任意數目的執行緒上進行完整的平行處理。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-159">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="fe3eb-160">這是透過在執行運算式之前呼叫 `AsParallel()` 所完成的。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-160">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="fe3eb-161">請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="fe3eb-161">Consider the following:</span></span>

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

<span data-ttu-id="fe3eb-162">此程式碼會視需要來跨系統執行緒進行 `facebookUsers` 分割、平行加總每個執行緒上的總相似項目、加總每個執行緒所計算的結果，並將結果投射至良好的字串。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-162">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="fe3eb-163">以圖表形式︰</span><span class="sxs-lookup"><span data-stu-id="fe3eb-163">In diagram form:</span></span>

![PLINQ 圖表](media/index/plinq-diagram.png)

<span data-ttu-id="fe3eb-165">可並行可透過 LINQ (輕鬆表示的 CPU 系結作業，也就是純虛擬函式，而且沒有副作用) 是 PLINQ 的絕佳候選項。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-165">Parallelizable CPU-bound jobs that can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="fe3eb-166">對於 _有副作用的作業_ ，請考慮使用工作平行連結 [庫](../parallel-programming/task-parallel-library-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="fe3eb-166">For jobs that _do_ have a side effect, consider using the [Task Parallel Library](../parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="more-resources"></a><span data-ttu-id="fe3eb-167">其他資源</span><span class="sxs-lookup"><span data-stu-id="fe3eb-167">More resources</span></span>

* [<span data-ttu-id="fe3eb-168">101 LINQ 範例</span><span class="sxs-lookup"><span data-stu-id="fe3eb-168">101 LINQ Samples</span></span>](/samples/dotnet/try-samples/101-linq-samples/)
* <span data-ttu-id="fe3eb-169">[Linqpad](https://www.linqpad.net/)，適用于 c #/F #/Visual Basic 的遊樂場環境和資料庫查詢引擎</span><span class="sxs-lookup"><span data-stu-id="fe3eb-169">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/Visual Basic</span></span>
* <span data-ttu-id="fe3eb-170">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/)，為學習 LINQ-to-object 如何實作的電子書</span><span class="sxs-lookup"><span data-stu-id="fe3eb-170">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
