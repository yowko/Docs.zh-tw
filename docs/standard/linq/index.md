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
# <a name="linq-overview"></a>LINQ 概觀

 (LINQ) 的語言整合式查詢提供語言層級的查詢功能，以及可讓您撰寫明確宣告式程式碼的 [高序位函式](https://en.wikipedia.org/wiki/Higher-order_function) API （c # 和 Visual Basic）。

## <a name="language-level-query-syntax"></a>語言層級查詢語法

這是語言層級的查詢語法：

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

這是使用 API 的相同範例 `IEnumerable<T>` ：

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a>LINQ 為表達

假設您有一份寵物清單，但想要將它轉換成字典，讓您可以藉由其 `RFID` 值直接存取寵物。

這是傳統的命令式程式碼：

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

程式碼背後的目的並不是透過迴圈來建立新的 `Dictionary<int, Pet>` 並新增至該程式碼，而是將現有的清單轉換成字典！ LINQ 會保留意圖，而命令式程式碼則不會。

這是對等的 LINQ 運算式：

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

使用 LINQ 的程式碼之所以重要，是因為它在程式設計師思考時為目的和程式碼之間提供了平衡。 另一個好處是讓程式碼保持簡潔。 想像一下減少 1/3 程式碼基底的情況，就如同以上所做一樣。 太棒了，對吧？

## <a name="linq-providers-simplify-data-access"></a>LINQ 提供者簡化資料存取

針對大量的軟體，大部分的工作都是處理來自某些來源 (資料庫、JSON、) XML 等等的資料。 通常這牽涉到針對每個資料來源學習新的 API，這可能很煩人。 LINQ 簡化了這項工作，方法是將資料存取的通用元素抽象化成查詢語法，不論您選擇哪一種資料來源都一樣。

這會尋找具有特定屬性值的所有 XML 元素：

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

撰寫程式碼以手動方式流覽 XML 檔以進行這項工作，是更具挑戰性的。

與 XML 互動不是您唯一可以使用 LINQ 提供者進行的作業。 [Linq to SQL](../../framework/data/adonet/sql/linq/index.md) 是相當基本的 MSSQL 伺服器資料庫物件關聯式對應程式 (ORM)。 [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) 程式庫提供透過 LINQ 的具效率 JSON 文件周遊。 此外，如果沒有可執行所需功能的程式庫，您也可以 [撰寫自己的 LINQ 提供者](/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))！

## <a name="reasons-to-use-the-query-syntax"></a>使用查詢語法的原因

為何要使用查詢語法？ 這是通常會出現的問題。 畢竟，下列程式碼：

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

是比下列問題更簡潔︰

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

API 語法不是比較精確的查詢語法方式嗎？

否。 查詢語法可讓您使用 **let** 子句，允許您在運算式的範圍內導入及繫結變數，並在運算式的後續片段中使用它。 使用 API 語法來重現相同的程式碼可以完成，但很可能會導致難以閱讀的程式碼。

而這就帶出了一個問題，**您應該只使用查詢語法嗎？**

如果有下列情況，則此問題的答案為 **yes** ：

- 您現有的程式碼基底已經使用查詢語法。
- 您必須在查詢中界定變數的範圍，因為複雜性太高。
- 您偏好使用查詢語法，且它不會干擾您的程式碼基底。

如果你符合下列條件，則此問題的答案為**否**...

- 現有的程式碼基底已經使用 API 語法
- 您不需要在查詢內指定變數的範圍
- 您偏好使用 API 語法，且它不會干擾您的程式碼基底

## <a name="essential-linq"></a>基本 LINQ

如需 LINQ 範例的真正完整清單，請瀏覽 [101 LINQ Samples](/samples/dotnet/try-samples/101-linq-samples/) (LINQ 範例入門)。

下列範例是 LINQ 的一些基本部分的快速示範。 這並沒有完整的功能，因為 LINQ 提供的功能比這裡展示的還多。

### <a name="the-bread-and-butter---where-select-and-aggregate"></a>階層與基本要素- `Where` 、 `Select` 和 `Aggregate`

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

### <a name="flattening-a-list-of-lists"></a>簡維清單清單

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

### <a name="union-between-two-sets-with-custom-comparator"></a>兩個集合之間的聯集 (與自訂比較子) 

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

### <a name="intersection-between-two-sets"></a>兩個集合之間的交集

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

### <a name="ordering"></a>排序

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

### <a name="equality-of-instance-properties"></a>實例屬性的相等

最後是一項更進階的範例︰判斷兩個相同類型執行個體的屬性值是否相等 (從 [此 StackOverflow 文章](https://stackoverflow.com/a/844855)中借用並經過修改)：

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

此程式碼會視需要來跨系統執行緒進行 `facebookUsers` 分割、平行加總每個執行緒上的總相似項目、加總每個執行緒所計算的結果，並將結果投射至良好的字串。

以圖表形式︰

![PLINQ 圖表](media/index/plinq-diagram.png)

可並行可透過 LINQ (輕鬆表示的 CPU 系結作業，也就是純虛擬函式，而且沒有副作用) 是 PLINQ 的絕佳候選項。 對於 _有副作用的作業_ ，請考慮使用工作平行連結 [庫](../parallel-programming/task-parallel-library-tpl.md)。

## <a name="more-resources"></a>其他資源

* [101 LINQ 範例](/samples/dotnet/try-samples/101-linq-samples/)
* [Linqpad](https://www.linqpad.net/)，適用于 c #/F #/Visual Basic 的遊樂場環境和資料庫查詢引擎
* [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/)，為學習 LINQ-to-object 如何實作的電子書
