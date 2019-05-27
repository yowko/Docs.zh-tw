---
title: LINQ (Language Integrated Query)
description: 了解 LINQ 如何將語言層級查詢功能和 API 提供給 C# 和 VB，來撰寫易懂的宣告式程式碼。
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: 941bfa624bfcc05457714b2f342054bbebfdf908
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557894"
---
# <a name="linq-language-integrated-query"></a>LINQ (Language Integrated Query)

## <a name="what-is-it"></a>這是什麼？

LINQ 將語言層級查詢功能和[較高順序的函式](https://en.wikipedia.org/wiki/Higher-order_function) API 提供給 C# 和 VB，來撰寫易懂的宣告式程式碼。

語言層級查詢語法︰

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

使用 `IEnumerable<T>` API 的相同範例：

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a>LINQ 簡單易懂

假設您有一份寵物清單，但想要將它轉換成字典，讓您可以藉由其 `RFID` 值直接存取寵物。

傳統的命令式程式碼︰

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

程式碼背後的目的不是用來建立新的 `Dictionary<int, Pet>` 並透過迴圈將其加入程式碼中，而是將現有的清單轉換為字典！ LINQ 會保留這項目的，而命令式程式碼不會。

對等的 LINQ 運算式︰

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

使用 LINQ 的程式碼之所以重要，是因為它在程式設計師思考時為目的和程式碼之間提供了平衡。 另一個好處是讓程式碼保持簡潔。 想像一下減少 1/3 程式碼基底的情況，就如同以上所做一樣。 很不錯，對吧？

## <a name="linq-providers-simplify-data-access"></a>LINQ 提供者簡化資料存取

在現實世界的軟體中，大部分的程序都圍繞在從某個來源處理資料 (資料庫、JSON、XML 等)。 通常這牽涉到針對每個資料來源學習新的 API，這可能很煩人。 LINQ 藉由將常見元素提取至查詢語法內，而該語法在哪一個資料來源中看起來都相同來簡化此工作。

請考慮下列項目︰尋找具有特定屬性值的所有 XML 元素。

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

撰寫程式碼以手動周遊 XML 文件來執行此工作會是更大的挑戰。

與 XML 互動不是您可以使用 LINQ 提供者來執行的唯一工作。 [Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) 是相當基本的 MSSQL 伺服器資料庫物件關聯式對應程式 (ORM)。 [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) 程式庫提供透過 LINQ 的具效率 JSON 文件周遊。 此外，如果沒有您所需的程式庫，您也可以[撰寫你自己的 LINQ 提供者](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))！

## <a name="why-use-the-query-syntax"></a>為何要使用查詢語法？

這是常常被人提起的問題。 畢竟，這方法，

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

是比下列問題更簡潔︰

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

API 語法只是一個使用查詢語法的更簡潔方法嗎？

否。 查詢語法可讓您使用 **let** 子句，允許您在運算式的範圍內導入及繫結變數，並在運算式的後續片段中使用它。 可以僅使用 API 語法來重新產生相同的程式碼，但很可能會產生難以閱讀的程式碼。

而這就帶出了一個問題，**您應該只使用查詢語法嗎？**

如果你符合下列條件，則此問題的答案為**是**...

* 現有的程式碼基底已經使用查詢語法
* 為了避免過於複雜，您需要在查詢內指定變數的範圍
* 您偏好查詢語法，且它不會偏離程式碼基底

如果你符合下列條件，則此問題的答案為**否**...

* 現有的程式碼基底已經使用 API 語法
* 您不需要在查詢內指定變數的範圍
* 您偏好 API 語法，且它不會影響程式碼基底

## <a name="essential-samples"></a>基本範例

如需 LINQ 範例的真正完整清單，請瀏覽 [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b) (LINQ 範例入門)。

以下是一些 LINQ 基本部分的簡單示範。 這些示範並不完整，因為 LINQ 提供的功能遠比此處說明的功能還多。

* 基本要素 - `Where``Select`和 `Aggregate`：

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

// Summing the lengths of a set of strings
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

* 簡維清單的清單︰

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

* 兩組集合之間的聯集 (使用自訂比較子)︰

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
        return d.GetHashCode();
    }
}

...

// Gets all the short-haired dogs between two different kennels
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());
```

* 兩組集合之間的交集︰

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

* 排序︰

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

* 最後是一項更進階的範例︰判斷兩個相同類型執行個體的屬性值是否相等 (從 [此 StackOverflow 文章](https://stackoverflow.com/a/844855)中借用並經過修改)：

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

## <a name="plinq"></a>PLINQ

PLINQ 或 Parallel LINQ，都是 LINQ 運算式的平行執行引擎。 換句話說，標準 LINQ 運算式可以在任意數目的執行緒上進行完整的平行處理。 這是透過在執行運算式之前呼叫 `AsParallel()` 所完成的。

請考慮下列事項：

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

此程式碼會視需要來跨系統執行緒進行 `facebookUsers` 分割、平行加總每個執行緒上的總相似項目、加總每個執行緒所計算的結果，並將結果投射至良好的字串。

以圖表形式︰

![PLINQ 圖表](./media/using-linq/plinq-diagram.png)

可以輕鬆地透過 LINQ 表示可平行的 CPU-bound 工作 (亦即，純虛擬函式，而且沒有任何副作用)，是 PLINQ 的絕佳候選項目。 針對 _do_ 會產生副作用的工作，請考慮使用 [Task Parallel Library (TPL)](./parallel-programming/task-parallel-library-tpl.md) (工作平行程式庫)。

## <a name="further-resources"></a>其他資源︰

* [101 LINQ 範例](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
* [Linqpad](https://www.linqpad.net/)為 C#/F#/VB 的遊樂場環境和資料庫查詢引擎
* [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/)，為學習 LINQ-to-object 如何實作的電子書
