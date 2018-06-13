---
title: 索引子
description: 了解 C# 索引子，以及其如何實作索引的屬性，而索引的屬性就是使用一或多個引數所參考的屬性。
ms.date: 06/20/2016
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 73f79f58cd20187a6fd0de29f53f1a31a269e0e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218295"
---
# <a name="indexers"></a><span data-ttu-id="2b1ec-103">索引子</span><span class="sxs-lookup"><span data-stu-id="2b1ec-103">Indexers</span></span>

<span data-ttu-id="2b1ec-104">「索引子」類似於屬性。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-104">*Indexers* are similar to properties.</span></span> <span data-ttu-id="2b1ec-105">從許多方面來看，索引子是建立在與[屬性](properties.md)相同的語言功能之上。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-105">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="2b1ec-106">索引子可啟用「索引」屬性，也就是使用一或多個引數參考的屬性。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-106">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="2b1ec-107">這些引數可對某些數值集合進行索引。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-107">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="2b1ec-108">索引子語法</span><span class="sxs-lookup"><span data-stu-id="2b1ec-108">Indexer Syntax</span></span>

<span data-ttu-id="2b1ec-109">您可以透過變數名稱和方括號來存取索引子。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-109">You access an indexer through a variable name and square brackets .</span></span> <span data-ttu-id="2b1ec-110">您會將索引子引數放在方括號內：</span><span class="sxs-lookup"><span data-stu-id="2b1ec-110">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="2b1ec-111">若要宣告索引子，請使用 `this` 關鍵字作為屬性名稱，然後宣告方括號內的引數。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-111">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="2b1ec-112">此宣告會比對上一個段落中所示的使用方式：</span><span class="sxs-lookup"><span data-stu-id="2b1ec-112">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="2b1ec-113">在第一個範例中，您可以看到屬性語法和索引子語法之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-113">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="2b1ec-114">這點相似性會出現在索引子的大部分語法規則中。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-114">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="2b1ec-115">索引子可以有任何有效的存取修飾詞 (public、protected internal、protected、internal、private 或 private protected)。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-115">Indexers can have any valid access modifiers (public, protected internal, protected, internal, private or private protected).</span></span> <span data-ttu-id="2b1ec-116">它們可能是密封、虛擬或抽象的。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-116">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="2b1ec-117">如同屬性，您可以為索引子中 get 和 set 存取子，指定不同的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-117">As with properties, you can specify different access modifiers for the get and set accesssors in an indexer.</span></span>
<span data-ttu-id="2b1ec-118">您也可以指定唯讀索引子 (藉由省略 set 存取子) 或唯寫索引子 (藉由省略 get 存取子)。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-118">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="2b1ec-119">您可以將使用屬性時所學到的幾乎所有知識應用到索引子。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-119">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="2b1ec-120">這項規則的唯一例外是「自動實作屬性」。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-120">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="2b1ec-121">編譯器不一定可為索引子產生正確的儲存體。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-121">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="2b1ec-122">索引子和屬性的不同之處，在於具有可參考一組項目中某個項目的引數。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-122">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="2b1ec-123">您可以在一個類型上定義多個索引子，但前提是每個索引子的引數清單必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-123">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="2b1ec-124">讓我們探索幾個不同的案例，在這些案例中，您可以在類別定義中使用一或多個索引子。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-124">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span> 

## <a name="scenarios"></a><span data-ttu-id="2b1ec-125">案例</span><span class="sxs-lookup"><span data-stu-id="2b1ec-125">Scenarios</span></span>

<span data-ttu-id="2b1ec-126">當您的類型 API 建立一些集合的模型，以供您在其中定義該集合的引數時，您會在此類型中定義「索引子」。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-126">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="2b1ec-127">您的索引子不一定會直接對應至屬於 .NET Core Framework 的集合類型。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-127">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="2b1ec-128">您的類型除了建立集合的模型之外，可能還有其他職責。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-128">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="2b1ec-129">索引子可讓您提供符合類型抽象概念的 API，而不會公開有關該抽象概念的值如何儲存或計算的內部詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-129">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="2b1ec-130">讓我們逐步解說使用「索引子」的一些常見案例。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-130">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="2b1ec-131">您可以存取[索引子的範例資料夾](https://github.com/dotnet/samples/tree/master/csharp/indexers)。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-131">You can access the [sample folder for indexers](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span></span> <span data-ttu-id="2b1ec-132">如需下載指示，請參閱[範例和教學課程](../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-132">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="2b1ec-133">陣列和向量</span><span class="sxs-lookup"><span data-stu-id="2b1ec-133">Arrays and Vectors</span></span>

<span data-ttu-id="2b1ec-134">建立索引子的其中一個最常見案例，就是當您的類型建立陣列或向量的模型時。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-134">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="2b1ec-135">您可以建立索引子來建立已排序資料清單的模型。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-135">You can create an indexer to model an ordered list of data.</span></span> 

<span data-ttu-id="2b1ec-136">建立您自己的索引子的優點，就是您可以定義該集合的儲存體以符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-136">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="2b1ec-137">假設您的類型所建立的歷程資料模型太大，而無法一次全部載入記憶體。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-137">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="2b1ec-138">您需要根據使用情況載入和卸載集合區段。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-138">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="2b1ec-139">下列範例會建立此行為的模型。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-139">The example following models this behavior.</span></span> <span data-ttu-id="2b1ec-140">它會報告有多少資料點。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-140">It reports on how many data points exist.</span></span> <span data-ttu-id="2b1ec-141">它會建立頁面，以視需要保留資料區段。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-141">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="2b1ec-142">它會從記憶體中刪除頁面，以挪出空間給較新要求所需的頁面使用。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-142">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

```csharp
public class DataSamples
{
    private class Page
    {
        private readonly List<Measurements> pageData = new List<Measurements>();
        private readonly int startingIndex;
        private readonly int length;
        private bool dirty;
        private DateTime lastAccess;

        public Page(int startingIndex, int length)
        {
            this.startingIndex = startingIndex;
            this.length = length;
            lastAccess = DateTime.Now;

            // This stays as random stuff:
            var generator = new Random();
            for(int i=0; i < length; i++)
            {
                var m = new Measurements
                {
                    HiTemp = generator.Next(50, 95),
                    LoTemp = generator.Next(12, 49),
                    AirPressure = 28.0 + generator.NextDouble() * 4
                };
                pageData.Add(m);
            }
        }
        public bool HasItem(int index) =>
            ((index >= startingIndex) &&
            (index < startingIndex + length));

        public Measurements this[int index]
        {
            get
            {
                lastAccess = DateTime.Now;
                return pageData[index - startingIndex];
            }
            set
            {
                pageData[index - startingIndex] = value;
                dirty = true;
                lastAccess = DateTime.Now;
            }
        }

        public bool Dirty => dirty;
        public DateTime LastAccess => lastAccess;
    }

    private readonly int totalSize;
    private readonly List<Page> pagesInMemory = new List<Page>();

    public DataSamples(int totalSize)
    {
        this.totalSize = totalSize;
    }

    public Measurements this[int index]
    {
        get
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");

            var page = updateCachedPagesForAccess(index);
            return page[index];
        }
        set
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");
            var page = updateCachedPagesForAccess(index);

            page[index] = value;
        }
    }

    private Page updateCachedPagesForAccess(int index)
    {
        foreach (var p in pagesInMemory)
        {
            if (p.HasItem(index))
            {
                return p;
            }
        }
        var startingIndex = (index / 1000) * 1000;
        var newPage = new Page(startingIndex, 1000);
        addPageToCache(newPage);
        return newPage;
    }

    private void addPageToCache(Page p)
    {
        if (pagesInMemory.Count > 4)
        {
            // remove oldest non-dirty page:
            var oldest = pagesInMemory
                .Where(page => !page.Dirty)
                .OrderBy(page => page.LastAccess)
                .FirstOrDefault();
            // Note that this may keep more than 5 pages in memory
            // if too much is dirty
            if (oldest != null)
                pagesInMemory.Remove(oldest);
        }
        pagesInMemory.Add(p);
    }
}
```

<span data-ttu-id="2b1ec-143">您可以遵循此設計慣例，來建立各式各樣的集合模型，在此情況下，您有很好的理由不將整組資料載入記憶體內部集合中。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-143">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="2b1ec-144">請注意，`Page` 類別是不屬於公用介面的私用巢狀類別。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-144">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="2b1ec-145">此類別的所有使用者都不會看到這些詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-145">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="2b1ec-146">字典</span><span class="sxs-lookup"><span data-stu-id="2b1ec-146">Dictionaries</span></span>

<span data-ttu-id="2b1ec-147">另一個常見案例是當您需要建立字典或對應的模型時。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-147">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="2b1ec-148">當您的類型根據索引鍵 (通常是文字索引鍵) 儲存值時，就會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-148">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="2b1ec-149">此範例會建立將命令列引數對應至管理這些選項之 [Lamdba 運算式](delegates-overview.md)的字典。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-149">This example creates a dictionary that maps command line arguments to [lamdba expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="2b1ec-150">下列範例顯示兩個類別︰將命令列選項對應至 `Action` 委派的 `ArgsActions` 類別，以及遇到該選項時會使用 `ArgsActions` 執行每個 `Action` 的 `ArgsProcessor`。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-150">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

```csharp
public class ArgsProcessor
{
    private readonly ArgsActions actions;

    public ArgsProcessor(ArgsActions actions)
    {
        this.actions = actions;
    }

    public void Process(string[] args)
    {
        foreach(var arg in args)
        {
            actions[arg]?.Invoke();
        }
    }

}
public class ArgsActions
{
    readonly private Dictionary<string, Action> argsActions = new Dictionary<string, Action>();

    public Action this[string s]
    {
        get
        {
            Action action;
            Action defaultAction = () => {} ;
            return argsActions.TryGetValue(s, out action) ? action : defaultAction;
        }
    }

    public void SetOption(string s, Action a)
    {
        argsActions[s] = a;
    }
}
```

<span data-ttu-id="2b1ec-151">在此範例中，`ArgsAction` 集合會緊密對應至基礎集合。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-151">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="2b1ec-152">`get` 會判斷是否已設定指定的選項。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-152">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="2b1ec-153">如果已設定，則會傳回與該選項相關聯的 `Action`。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-153">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="2b1ec-154">如果未設定，則會傳回不執行任何動作的 `Action`。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-154">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="2b1ec-155">公用存取子不包含 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-155">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="2b1ec-156">相反地，此設計使用公用方法來設定選項。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-156">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="2b1ec-157">多維對應</span><span class="sxs-lookup"><span data-stu-id="2b1ec-157">Multi-Dimensional Maps</span></span>

<span data-ttu-id="2b1ec-158">您可以建立使用多個引數的索引子。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-158">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="2b1ec-159">此外，這些引數並不限於相同的類型。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-159">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="2b1ec-160">讓我們來看以下兩個範例。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-160">Let's look at two examples.</span></span>   

<span data-ttu-id="2b1ec-161">第一個範例顯示產生 Mandelbrot 集合值的類別。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-161">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="2b1ec-162">如需該集合背後數學的詳細資訊，請參閱[這篇文章](https://en.wikipedia.org/wiki/Mandelbrot_set)。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-162">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span> <span data-ttu-id="2b1ec-163">索引子使用兩個雙精度浮點數在 X, Y 平面中定義一個點。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-163">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="2b1ec-164">get 存取子會計算反覆運算次數，直到某個點經判斷不在集合內為止。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-164">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="2b1ec-165">如果到達最高次數，該點是在集合內，而且會傳回類別的 maxIterations 值</span><span class="sxs-lookup"><span data-stu-id="2b1ec-165">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="2b1ec-166">(為了 Mandelbrot 集合所普及化的電腦產生影像，會定義決定點在集合之外所需之反覆運算次數的色彩)。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-166">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

```csharp
public class Mandelbrot
{
    readonly private int maxIterations;

    public Mandelbrot(int maxIterations)
    {
        this.maxIterations = maxIterations;
    }

    public int this [double x, double y]
    {
        get
        {
            var iterations = 0;
            var x0 = x;
            var y0 = y;

            while ((x*x + y * y < 4) &&
                (iterations < maxIterations))
            {
                var newX = x * x - y * y + x0;
                y = 2 * x * y + y0;
                x = newX;
                iterations++;
            }
            return iterations;
        }
    }
}
```

<span data-ttu-id="2b1ec-167">Mandelbrot 集合會在每個 (x,y) 座標定義實數值的值。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-167">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="2b1ec-168">這會定義可能包含無限數目之值的字典。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-168">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="2b1ec-169">因此，該集合背後沒有任何儲存體。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-169">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="2b1ec-170">相反地，當程式碼呼叫 `get` 存取子時，此類別會計算每個點的值；</span><span class="sxs-lookup"><span data-stu-id="2b1ec-170">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="2b1ec-171">但不會使用任何基礎儲存體。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-171">There's no underlying storage used.</span></span>

<span data-ttu-id="2b1ec-172">讓我們來看上次使用的索引子，該索引子接受多個不同類型的引數。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-172">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="2b1ec-173">假設有個管理歷程溫度資料的程式。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-173">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="2b1ec-174">此索引子使用城市和日期來設定或取得該地點的高低溫度：</span><span class="sxs-lookup"><span data-stu-id="2b1ec-174">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

```csharp
using DateMeasurements = 
    System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = 
    System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;

public class HistoricalWeatherData
{
    readonly CityDataMeasurements storage = new CityDataMeasurements();

    public Measurements this[string city, DateTime date]
    {
        get
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
                throw new ArgumentOutOfRangeException(nameof(city), "City not found");

            // strip out any time portion:
            var index = date.Date;
            var measure = default(Measurements);
            if (cityData.TryGetValue(index, out measure))
                return measure;
            throw new ArgumentOutOfRangeException(nameof(date), "Date not found");
        }
        set
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
            {
                cityData = new DateMeasurements();
                storage.Add(city, cityData);
            }

            // Strip out any time portion:
            var index = date.Date;
            cityData[index] = value;
        }
    }
}
```

<span data-ttu-id="2b1ec-175">此範例會建立對應兩個不同引數之天氣資料的索引子︰城市 (以 `string` 表示) 和日期 (以 `DateTime` 表示)。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-175">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="2b1ec-176">內部儲存體使用兩個 `Dictionary` 類別來代表二維字典。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-176">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="2b1ec-177">此公用 API 不再代表基礎儲存體。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-177">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="2b1ec-178">相反地，索引子的語言功能可讓您建立公用介面來代表您的抽象概念，不過基礎儲存體必須使用不同的核心集合類型。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-178">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="2b1ec-179">有些開發人員對此程式碼的其中兩部分可能不熟悉。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-179">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="2b1ec-180">這兩個 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="2b1ec-180">These two `using` statements:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="2b1ec-181">會為建構的泛型型別建立「別名」。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-181">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="2b1ec-182">這些陳述式可讓程式碼稍後使用更具描述性的 `DateMeasurements` 和 `CityDateMeasurements` 名稱，而不是 `Dictionary<DateTime, Measurements>` 和 `Dictionary<string, Dictionary<DateTime, Measurements> >` 的泛型建構。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-182">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span> <span data-ttu-id="2b1ec-183">此建構確實需要在 `=` 符號右側使用完整的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-183">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="2b1ec-184">第二個方法是移除用來對集合進行索引之任何 `DateTime` 物件的時間部分。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-184">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="2b1ec-185">.NET Framework 不包含只有日期的類型。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-185">The .NET framework does not include a Date only type.</span></span>
<span data-ttu-id="2b1ec-186">開發人員使用 `DateTime` 類型，但使用 `Date` 屬性來確保該日期的任何 `DateTime` 物件都相等。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-186">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="2b1ec-187">總結</span><span class="sxs-lookup"><span data-stu-id="2b1ec-187">Summing Up</span></span>

<span data-ttu-id="2b1ec-188">每當您的類別中有屬性類元素，且該屬性不代表單一值，而代表數值集合 (其中每個項目是由一組引數所識別) 時，就應該建立索引子。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-188">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="2b1ec-189">這些引數可唯一識別應參考集合中的哪個項目。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-189">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="2b1ec-190">索引子延伸[屬性](properties.md)的概念，其中的成員會當做類別外部的資料項目來處理，但索引子類似一旁的方法。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-190">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the side.</span></span> <span data-ttu-id="2b1ec-191">索引子允許引數在代表一組項目的屬性中尋找單一項目。</span><span class="sxs-lookup"><span data-stu-id="2b1ec-191">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>
