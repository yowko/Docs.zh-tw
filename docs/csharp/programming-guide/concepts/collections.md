---
title: "集合 (C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
caps.latest.revision: "6"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 271939b869433742f8b5720ba05955169ea5c410
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="collections-c"></a>集合 (C#)
在許多應用程式中，您想要建立和管理相關物件的群組。 有兩種方式可以群組物件：建立物件的陣列和建立物件的集合。  
  
 陣列是最適用於建立和處理固定數目的強類型物件。 如需陣列的資訊，請參閱[陣列](../../../csharp/programming-guide/arrays/index.md)。  
  
 集合會提供較具彈性的方式來使用物件群組。 與陣列不同的是，您使用的物件群組可依程式變更的需要來動態增減。 對於某些集合，您可以將鍵值指派給您放入集合的任何物件，讓您可以藉由使用鍵值快速擷取物件。  
  
 集合是類別，因此您必須在將項目加入該集合之前，宣告類別的執行個體。  
  
 如果集合包含只有一個資料類型的項目，則可使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間內的其中一個類別。 泛型集合會強制類型安全，如此就不會加入其他資料類型。 當您從泛型集合中擷取項目時，並不需要判斷其資料類型或將其轉換。  
  
> [!NOTE]
>  在本主題的範例中，請包括 `System.Collections.Generic` 和 `System.Linq` 命名空間的 [using](../../../csharp/language-reference/keywords/using-directive.md) 指示詞。  
  
 **本主題內容**  
  
-   [使用簡單的集合](#BKMK_SimpleCollection)  
  
-   [集合的種類](#BKMK_KindsOfCollections)  
  
    -   [System.Collections.Generic 類別](#BKMK_Generic)  
  
    -   [System.Collections.Concurrent 類別](#BKMK_Concurrent)  
  
    -   [System.Collections 類別](#BKMK_Collections)  
  
-   [實作索引鍵/值組集合](#BKMK_KeyValuePairs)  
  
-   [使用 LINQ 存取集合](#BKMK_LINQ)  
  
-   [排序集合](#BKMK_Sorting)  
  
-   [定義自訂集合](#BKMK_CustomCollection)  
  
-   [迭代器](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>使用簡單的集合  
 本節中的範例使用泛型 <xref:System.Collections.Generic.List%601> 類別，能夠讓您使用強型別物件清單。  
  
 下列範例會建立字串清單，並使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式逐一查看字串。  
  
```csharp  
// Create a list of strings.  
var salmons = new List<string>();  
salmons.Add("chinook");  
salmons.Add("coho");  
salmons.Add("pink");  
salmons.Add("sockeye");  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 如果預先知道集合的內容，即可使用「集合初始設定式」來初始化集合。 如需詳細資訊，請參閱[物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。  
  
 下列範例與前一個範例相同，但有一點除外，就是集合初始設定式是用來將項目加入集合中。  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 您可以使用 [for](../../../csharp/language-reference/keywords/for.md) 陳述式來逐一查看集合，而不是使用 `foreach` 陳述式。 您可以藉由依索引位置存取集合項目來完成這項作業。 項目的索引以 0 開始，並以項目計數減 1 結束。  
  
 下列範例會使用 `for` 來逐一查看集合的項目，而不是使用 `foreach`。  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
for (var index = 0; index < salmons.Count; index++)  
{  
    Console.Write(salmons[index] + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 下列範例透過指定要移除的物件，從集合中移除項目。  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
// Remove an element from the list by specifying  
// the object.  
salmons.Remove("coho");  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook pink sockeye  
```  
  
 下列範例會移除泛型清單中的項目。 使用以遞減順序反覆運算的 [for](../../../csharp/language-reference/keywords/for.md) 陳述式，而不是 `foreach` 陳述式。 這是因為 <xref:System.Collections.Generic.List%601.RemoveAt%2A> 方法導致在已移除之項目後面的項目具有較低的索引值。  
  
```csharp  
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
  
// Remove odd numbers.  
for (var index = numbers.Count - 1; index >= 0; index--)  
{  
    if (numbers[index] % 2 == 1)  
    {  
        // Remove the element by specifying  
        // the zero-based index in the list.  
        numbers.RemoveAt(index);  
    }  
}  
  
// Iterate through the list.  
// A lambda expression is placed in the ForEach method  
// of the List(T) object.  
numbers.ForEach(  
    number => Console.Write(number + " "));  
// Output: 0 2 4 6 8  
```  
  
 如需 <xref:System.Collections.Generic.List%601> 中的項目類型，您也可以定義自己的類別。 在下列範例中，<xref:System.Collections.Generic.List%601> 使用的 `Galaxy` 類別是在程式碼中定義的。  
  
```csharp  
private static void IterateThroughList()  
{  
    var theGalaxies = new List<Galaxy>  
        {  
            new Galaxy() { Name="Tadpole", MegaLightYears=400},  
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},  
            new Galaxy() { Name="Milky Way", MegaLightYears=0},  
            new Galaxy() { Name="Andromeda", MegaLightYears=3}  
        };  
  
    foreach (Galaxy theGalaxy in theGalaxies)  
    {  
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);  
    }  
  
    // Output:  
    //  Tadpole  400  
    //  Pinwheel  25  
    //  Milky Way  0  
    //  Andromeda  3  
}  
  
public class Galaxy  
{  
    public string Name { get; set; }  
    public int MegaLightYears { get; set; }  
}  
```  

<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a>集合的種類 
 .NET Framework 會提供很多常見的集合。 各個類型的集合都是針對特定用途來設計。  
  
 下列集合類別的群組將在本節介紹：  
  
-   <xref:System.Collections.Generic> 類別  
  
-   <xref:System.Collections.Concurrent> 類別  
  
-   <xref:System.Collections> 類別  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a>System.Collections.Generic 類別  
 藉由使用 <xref:System.Collections.Generic> 命名空間的其中一個類別，您可以建立泛型集合。 當集合中每個項目的資料類型相同時，泛型集合就相當有用。 泛型集合會透過只允許加入所需資料類型的方式，強制使用強式類型。  
  
 下表列出 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間的一些常用類別：  

|類別|描述| 
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|表示根據索引鍵所整理的索引鍵/值組集合。|  
|<xref:System.Collections.Generic.List%601>|表示可以依照索引存取的物件清單。 提供搜尋、排序和修改清單的方法。|  
|<xref:System.Collections.Generic.Queue%601>|表示物件的先進先出 (FIFO) 集合。|  
|<xref:System.Collections.Generic.SortedList%602>|代表根據關聯的 <xref:System.Collections.Generic.IComparer%601> 實作，依索引鍵所排序的索引鍵/值組集合。|  
|<xref:System.Collections.Generic.Stack%601>|表示物件的後進先出 (LIFO) 集合。|  
  
 如需其他資訊，請參閱[常用的集合類型](../../../standard/collections/commonly-used-collection-types.md)、[選取集合類別](../../../standard/collections/selecting-a-collection-class.md)和 <xref:System.Collections.Generic>。  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a>System.Collections.Concurrent 類別  
 在 .NET Framework 4 或更新版本中，<xref:System.Collections.Concurrent> 命名空間中的集合提供了有效率的安全執行緒作業，可從多個執行緒存取集合項目。  
  
 每當有多個執行緒同時存取集合時，應該使用 <xref:System.Collections.Concurrent> 命名空間中的類別來代替 <xref:System.Collections.Generic?displayProperty=nameWithType> 和 <xref:System.Collections?displayProperty=nameWithType> 命名空間中的對應類型。 如需詳細資訊，請參閱[安全執行緒集合](../../../standard/collections/thread-safe/index.md)和 <xref:System.Collections.Concurrent>。  
  
 <xref:System.Collections.Concurrent> 命名空間中包含一些類別，包括 <xref:System.Collections.Concurrent.BlockingCollection%601>、<xref:System.Collections.Concurrent.ConcurrentDictionary%602>、<xref:System.Collections.Concurrent.ConcurrentQueue%601> 和 <xref:System.Collections.Concurrent.ConcurrentStack%601>。  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a>System.Collections 類別  
 <xref:System.Collections?displayProperty=nameWithType> 命名空間中的類別不會將項目儲存為特別類型物件，而是會儲存為 `Object` 類型的物件。  
  
 可能的話，您應該使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間或 <xref:System.Collections.Concurrent> 命名空間中的泛型集合，而非 `System.Collections` 命名空間中的傳統類型。  
  
 下表列出 `System.Collections` 命名空間的一些常用類別：  
  
|類別|描述|  
|---|---|  
|<xref:System.Collections.ArrayList>|代表會視需要動態增加大小的物件陣列。|  
|<xref:System.Collections.Hashtable>|代表根據索引鍵的雜湊程式碼，所整理的索引鍵/值組集合。|  
|<xref:System.Collections.Queue>|表示物件的先進先出 (FIFO) 集合。|  
|<xref:System.Collections.Stack>|表示物件的後進先出 (LIFO) 集合。|  
  
 <xref:System.Collections.Specialized> 命名空間會提供特製化類型和強型別集合類別，例如只有字串的集合，以及連結串列和 Hybrid 字典。  

<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>實作索引鍵/值組集合。  
 <xref:System.Collections.Generic.Dictionary%602> 泛型集合可讓您使用每個項目的索引鍵來存取集合中的項目。 加入字典中的每一個項目都是由值及其關聯索引鍵所組成。 使用其索引鍵擷取值的速度非常快，因為 `Dictionary` 類別是實作為雜湊表。  
  
 下列範例會使用 `foreach` 陳述式建立 `Dictionary` 集合並逐一查看字典。  
  
```csharp  
private static void IterateThruDictionary()  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    foreach (KeyValuePair<string, Element> kvp in elements)  
    {  
        Element theElement = kvp.Value;  
  
        Console.WriteLine("key: " + kvp.Key);  
        Console.WriteLine("values: " + theElement.Symbol + " " +  
            theElement.Name + " " + theElement.AtomicNumber);  
    }  
}  
  
private static Dictionary<string, Element> BuildDictionary()  
{  
    var elements = new Dictionary<string, Element>();  
  
    AddToDictionary(elements, "K", "Potassium", 19);  
    AddToDictionary(elements, "Ca", "Calcium", 20);  
    AddToDictionary(elements, "Sc", "Scandium", 21);  
    AddToDictionary(elements, "Ti", "Titanium", 22);  
  
    return elements;  
}  
  
private static void AddToDictionary(Dictionary<string, Element> elements,  
    string symbol, string name, int atomicNumber)  
{  
    Element theElement = new Element();  
  
    theElement.Symbol = symbol;  
    theElement.Name = name;  
    theElement.AtomicNumber = atomicNumber;  
  
    elements.Add(key: theElement.Symbol, value: theElement);  
}  
  
public class Element  
{  
    public string Symbol { get; set; }  
    public string Name { get; set; }  
    public int AtomicNumber { get; set; }  
}  
```  
  
 若要改為使用集合初始設定式建置 `Dictionary` 集合，您可以使用下列方法取代 `BuildDictionary` 和 `AddToDictionary` 方法。  
  
```csharp  
private static Dictionary<string, Element> BuildDictionary2()  
{  
    return new Dictionary<string, Element>  
    {  
        {"K",  
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},  
        {"Ca",  
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},  
        {"Sc",  
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},  
        {"Ti",  
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}  
    };  
}  
```  
  
 下列範例會使用 <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> 方法和 `Dictionary` 的 <xref:System.Collections.Generic.Dictionary%602.Item%2A> 屬性來依索引鍵快速尋找項目。 藉由使用 C# 中的 `elements[symbol]`，`Item` 屬性可讓您存取 `elements` 集合中的項目。  
  
```csharp  
private static void FindInDictionary(string symbol)  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    if (elements.ContainsKey(symbol) == false)  
    {  
        Console.WriteLine(symbol + " not found");  
    }  
    else  
    {  
        Element theElement = elements[symbol];  
        Console.WriteLine("found: " + theElement.Name);  
    }  
}  
```  
  
 下列範例會使用 <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 方法依索引鍵來快速尋找項目。  
  
```csharp  
private static void FindInDictionary2(string symbol)  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    Element theElement = null;  
    if (elements.TryGetValue(symbol, out theElement) == false)  
        Console.WriteLine(symbol + " not found");  
    else  
        Console.WriteLine("found: " + theElement.Name);  
}  
```  

<a name="BKMK_LINQ"></a>
## <a name="using-linq-to-access-a-collection"></a>使用 LINQ 存取集合  
 LINQ (Language-Integrated Query (LINQ)) 可用來存取集合。 LINQ 查詢提供篩選、排序和分組功能。 如需詳細資訊，請參閱[開始使用 C# 中的 LINQ](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)。  
  
 下列範例會對泛型 `List` 執行 LINQ 查詢。 LINQ 查詢會傳回包含結果的不同集合。  
  
```csharp  
private static void ShowLINQ()  
{  
    List<Element> elements = BuildList();  
  
    // LINQ Query.  
    var subset = from theElement in elements  
                 where theElement.AtomicNumber < 22  
                 orderby theElement.Name  
                 select theElement;  
  
    foreach (Element theElement in subset)  
    {  
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);  
    }  
  
    // Output:  
    //  Calcium 20  
    //  Potassium 19  
    //  Scandium 21  
}  
  
private static List<Element> BuildList()  
{  
    return new List<Element>  
    {  
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},  
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},  
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},  
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}  
    };  
}  
  
public class Element  
{  
    public string Symbol { get; set; }  
    public string Name { get; set; }  
    public int AtomicNumber { get; set; }  
}  
```  

<a name="BKMK_Sorting"></a>
## <a name="sorting-a-collection"></a>為集合排序  
 下列範例說明排序集合的程序。 此範例排序儲存在 <xref:System.Collections.Generic.List%601> 中的 `Car` 類別執行個體。 `Car` 類別實作 <xref:System.IComparable%601> 介面，而這個介面要求實作 <xref:System.IComparable%601.CompareTo%2A> 方法。  
  
 每次對 <xref:System.IComparable%601.CompareTo%2A> 方法的呼叫都會進行用於排序的單一比較。 當目前物件和另一個物件比較時，在 `CompareTo` 方法中的使用者撰寫程式碼會傳回值。 如果目前物件比另一個物件小則傳回的值小於零，如果目前物件比另一個物件大則傳回的值大於零，如果它們相等則傳回零。 這可讓您以程式碼定義大於、小於、等於的準則。  
  
 在 `ListCars` 方法中，`cars.Sort()` 陳述式會排序清單。 對 <xref:System.Collections.Generic.List%601> 之 <xref:System.Collections.Generic.List%601.Sort%2A> 方法的這個呼叫，會導致 `CompareTo` 方法對 `List` 的 `Car` 物件自動呼叫。  
  
```csharp  
private static void ListCars()  
{  
    var cars = new List<Car>  
    {  
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},  
        { new Car() { Name = "car2", Color = "red", Speed = 50}},  
        { new Car() { Name = "car3", Color = "green", Speed = 10}},  
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},  
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},  
        { new Car() { Name = "car6", Color = "red", Speed = 60}},  
        { new Car() { Name = "car7", Color = "green", Speed = 50}}  
    };  
  
    // Sort the cars by color alphabetically, and then by speed  
    // in descending order.  
    cars.Sort();  
  
    // View all of the cars.  
    foreach (Car thisCar in cars)  
    {  
        Console.Write(thisCar.Color.PadRight(5) + " ");  
        Console.Write(thisCar.Speed.ToString() + " ");  
        Console.Write(thisCar.Name);  
        Console.WriteLine();  
    }  
  
    // Output:  
    //  blue  50 car4  
    //  blue  30 car5  
    //  blue  20 car1  
    //  green 50 car7  
    //  green 10 car3  
    //  red   60 car6  
    //  red   50 car2  
}  
  
public class Car : IComparable<Car>  
{  
    public string Name { get; set; }  
    public int Speed { get; set; }  
    public string Color { get; set; }  
  
    public int CompareTo(Car other)  
    {  
        // A call to this method makes a single comparison that is  
        // used for sorting.  
  
        // Determine the relative order of the objects being compared.  
        // Sort by color alphabetically, and then by speed in  
        // descending order.  
  
        // Compare the colors.  
        int compare;  
        compare = String.Compare(this.Color, other.Color, true);  
  
        // If the colors are the same, compare the speeds.  
        if (compare == 0)  
        {  
            compare = this.Speed.CompareTo(other.Speed);  
  
            // Use descending order for speed.  
            compare = -compare;  
        }  
  
        return compare;  
    }  
}  
```  
  
<a name="BKMK_CustomCollection"></a>
## <a name="defining-a-custom-collection"></a>定義自訂集合  
 您可以透過實作 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Collections.IEnumerable> 介面來定義集合。 如需其他資訊，請參閱[如何：使用 foreach 存取集合類別](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)。  
  
 雖然您可以定義自訂集合，但是使用包含在 .NET Framework 中的集合 (本主題稍早在[集合的種類](#BKMK_KindsOfCollections)中所述) 通常會比較好。  
  
 下列範例會定義名為 `AllColors` 的自訂集合類別。 這個類別實作 <xref:System.Collections.IEnumerable> 介面，該介面要求實作 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。  
  
 `GetEnumerator` 方法會傳回 `ColorEnumerator` 類別的執行個體。 `ColorEnumerator` 實作 <xref:System.Collections.IEnumerator> 介面，而此介面會要求實作 <xref:System.Collections.IEnumerator.Current%2A> 屬性、<xref:System.Collections.IEnumerator.MoveNext%2A> 方法和 <xref:System.Collections.IEnumerator.Reset%2A> 方法。  
  
```csharp  
private static void ListColors()  
{  
    var colors = new AllColors();  
  
    foreach (Color theColor in colors)  
    {  
        Console.Write(theColor.Name + " ");  
    }  
    Console.WriteLine();  
    // Output: red blue green  
}  
  
// Collection class.  
public class AllColors : System.Collections.IEnumerable  
{  
    Color[] _colors =  
    {  
        new Color() { Name = "red" },  
        new Color() { Name = "blue" },  
        new Color() { Name = "green" }  
    };  
  
    public System.Collections.IEnumerator GetEnumerator()  
    {  
        return new ColorEnumerator(_colors);  
  
        // Instead of creating a custom enumerator, you could  
        // use the GetEnumerator of the array.  
        //return _colors.GetEnumerator();  
    }  
  
    // Custom enumerator.  
    private class ColorEnumerator : System.Collections.IEnumerator  
    {  
        private Color[] _colors;  
        private int _position = -1;  
  
        public ColorEnumerator(Color[] colors)  
        {  
            _colors = colors;  
        }  
  
        object System.Collections.IEnumerator.Current  
        {  
            get  
            {  
                return _colors[_position];  
            }  
        }  
  
        bool System.Collections.IEnumerator.MoveNext()  
        {  
            _position++;  
            return (_position < _colors.Length);  
        }  
  
        void System.Collections.IEnumerator.Reset()  
        {  
            _position = -1;  
        }  
    }  
}  
  
// Element class.  
public class Color  
{  
    public string Name { get; set; }  
}  
```  

<a name="BKMK_Iterators"></a> 
##  <a name="iterators"></a>迭代器  
 「迭代器」是用來在集合上執行自訂反覆項目。 迭代器可以是方法或 `get` 存取子。 迭代器會使用 [yield return](../../../csharp/language-reference/keywords/yield.md) 陳述式，一次一個地傳回集合中的每個項目。  
  
 您會使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式來呼叫迭代器。 `foreach` 迴圈的每個反覆項目都會呼叫迭代器。 在迭代器中到達 `yield return` 陳述式時，會傳回運算式，並保留程式碼中的目前位置。 下一次呼叫迭代器時，便會從這個位置重新開始執行。  
  
 如需詳細資訊，請參閱[迭代器 (C#)](../../../csharp/programming-guide/concepts/iterators.md)。  
  
 下列範例使用了 iterator 方法。 Iterator 方法具有 [for](../../../csharp/language-reference/keywords/for.md) 迴圈內的 `yield return` 陳述式。 在 `ListEvenNumbers` 方法中，`foreach` 陳述式主體的每個反覆項目都會建立對 Iterator 方法的呼叫，這個方法將繼續執行下一個 `yield return` 陳述式。  
  
```csharp  
private static void ListEvenNumbers()  
{  
    foreach (int number in EvenSequence(5, 18))  
    {  
        Console.Write(number.ToString() + " ");  
    }  
    Console.WriteLine();  
    // Output: 6 8 10 12 14 16 18  
}  
  
private static IEnumerable<int> EvenSequence(  
    int firstNumber, int lastNumber)  
{  
    // Yield even numbers in the range.  
    for (var number = firstNumber; number <= lastNumber; number++)  
    {  
        if (number % 2 == 0)  
        {  
            yield return number;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [程式設計概念 (C#)](../../../csharp/programming-guide/concepts/index.md)  
 [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [LINQ to Objects (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [平行 LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [集合和資料結構](../../../standard/collections/index.md)  
 [建立和操作集合](http://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
 [選取集合類別](../../../standard/collections/selecting-a-collection-class.md)  
 [在集合內比較和排序](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [何時使用泛型集合](../../../standard/collections/when-to-use-generic-collections.md)  
 [如何：使用 foreach 存取集合類別](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)
