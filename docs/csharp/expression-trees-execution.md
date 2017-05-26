---
title: "執行運算式樹狀架構"
description: "執行運算式樹狀架構"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 8423e19047d3c967a69566ebd863f677d11a0898
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---

# <a name="executing-expression-trees"></a>執行運算式樹狀架構

[上一個課程 -- 支援運算式樹狀架構的架構類型](expression-classes.md)

「運算式樹狀架構」是一種表示特定程式碼的資料結構。
它不是已編譯且可執行的程式碼。 如果您想要執行由運算式樹狀架構表示的 .NET 程式碼，您必須將它轉換成可執行 IL 指令。 
## <a name="lambda-expressions-to-functions"></a>將 Lambda 運算式轉換成函式
您可以將任何 LambdaExpression 或衍生自 LambdaExpression 的任何類型，轉換成可執行 IL。 其他運算式類型則無法直接轉換成程式碼。 這項限制實際上不會造成太大影響。 Lambda 運算式是您想要轉換成可執行中繼語言 (IL) 以便執行的唯一運算式類型。 (想想直接執行 `ConstantExpression` 的用意。 是否有任何用處？)任何 `LamdbaExpression` 的運算式樹狀架構或衍生自 `LambdaExpression` 的類型，都可以轉換成 IL。
運算式類型 `Expression<TDelegate>` 是 .NET Core 程式庫中唯一的具體範例。 它可用來表示對應至任何委派類型的運算式。 因為此類型對應至委派類型，所以 .NET 可以查看運算式，並為符合 Lambda 運算式簽章的適當委派產生 IL。 

在大多數情況下，這會在運算式和其對應委派之間建立一個簡單的對應。 例如，由 `Expression<Func<int>>` 表示的運算式樹狀架構會轉換成 `Func<int>` 類型的委派。 對於具有任何傳回型別和引數清單的 Lambda 運算式，會有一個委派類型，它是由該 Lambda 運算式表示之可執行程式碼的目標類型。

`LamdbaExpression` 類型包含將運算式樹狀架構轉換成可執行程式碼時所使用的 `Compile` 和 `CompileToMethod` 成員。 `Compile` 方法會建立委派。 `ConmpileToMethod` 方法會以表示運算式樹狀架構之編譯輸出的 IL 來更新 `MethodBuilder` 物件。 請注意，`CompileToMethod` 僅適用於完整桌面架構，而不適用於 .NET Core 架構。

或者，您也可以提供 `DebugInfoGenerator`，以接收所產生之委派物件的符號偵錯資訊。 這可讓您將運算式樹狀架構轉換成委派物件，並具有所產生之委派的完整偵錯資訊。

您會使用下列程式碼，將運算式轉換成委派：

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

請注意，委派類型是以運算式類型為基礎。 如果您想要以強型別方式來使用委派物件，您必須了解傳回型別和引數清單。 `LambdaExpression.Compile()` 方法會傳回 `Delegate` 類型。 您必須將它轉換成正確的委派類型，才能讓任何編譯時期工具檢查傳回型別的引數清單。

## <a name="execution-and-lifetimes"></a>執行和存留期

您可以藉由叫用在呼叫 `LamdbaExpression.Compile()` 時所建立的委派，來執行程式碼。 如上所示，`add.Compile()` 會傳回委派。 叫用該委派 (藉由呼叫 `func()`) 即可執行程式碼。

該委派代表運算式樹狀架構中的程式碼。 您可以保留該委派的控制代碼，稍後再叫用它。 您不需要在每次想要執行運算式樹狀架構所表示的程式碼時編譯運算式樹狀架構 (請記住，運算式樹狀架構為不可變，稍後編譯相同的運算式樹狀架構將會建立執行相同程式碼的委派)。

建議您不要嘗試建立任何更複雜的快取機制來提升效能，方法是避免不必要的編譯呼叫。 比較兩個任意運算式樹狀架構以判斷其是否代表相同的演算法，執行起來也很耗時。 您可能會發現避免任何額外的 `LambdaExpression.Compile()` 呼叫所省下的計算時間，超過執行程式碼以判斷兩個不同的運算式樹狀架構是否產生相同的可執行程式碼所花費的時間。

## <a name="caveats"></a>警告

您可以使用運算式樹狀架構執行的其中一個最簡單的作業，就是將 Lambda 運算式編譯成委派並叫用該委派。 不過，即使這是簡單的作業，還是必須注意幾點。 

Lambda 運算式會透過運算式中參考的任何區域變數建立結束型別。 您必須確保屬於該委派的任何變數都可用於呼叫 `Compile` 的位置，以及在執行所產生的委派時使用。

一般而言，編譯器會確保這點。 不過，如果您的運算式存取實作 `IDisposable` 的變數，您的程式碼可能會處置運算式樹狀架構仍持有的物件。

例如，因為 `int` 不會實作 `IDisposable`，所以下列程式碼會正常運作：

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

委派擷取了區域變數 `constant` 的參考。
您可以在稍後於 `CreateBoundFunc` 傳回的函式執行時，隨時存取該變數。

不過，請考慮實作 `IDisposable` 的這個類別 (而不是經過人為操作的類別)：

```csharp
public class Resource : IDisposable
{
    private bool isDisposed = false;
    public int Argument
    {
        get
        {
            if (!isDisposed)
                return 5;
            else throw new ObjectDisposedException("Resource");
        }
    }

    public void Dispose()
    {
        isDisposed = true;
    }
}
```

如果您將它用於以下所示的運算式中，當您執行 `Resource.Argument` 屬性所參考的程式碼時，您會得到 `ObjectDisposedException`：

```csharp
private static Func<int, int> CreateBoundResource()
{
    using (var constant = new Resource()) // constant is captured by the expression tree
    {
        Expression<Func<int, int>> expression = (b) => constant.Argument + b;
        var rVal = expression.Compile();
        return rVal;
    }
}
```

此方法所傳回的委派已透過 `constant` 物件關閉，該物件已經過處置 (因為已在 `using` 陳述式中宣告，所以已經過處置)。 

現在，當您執行此方法所傳回的委派時，執行當下會擲回 `ObjecctDisposedException`。

以執行階段錯誤表示編譯時期建構看起來很奇怪，但這是使用運算式樹狀架構時會面臨到的情況。

此問題有許多變化組合，因此很難提供一般指引予以避免。 定義運算式時，請小心存取區域變數；建立可由公用 API 傳回的運算式樹狀架構時，請小心存取目前物件 (以 `this` 表示) 中的狀態。

運算式中的程式碼可能會參考其他組件中的方法或屬性。 定義運算式、編譯運算式及叫用所產生的委派時，都必須存取該組件。 如果沒有該組件，則會發生 `ReferencedAssemblyNotFoundException`。

## <a name="summary"></a>總結

您可以編譯表示 Lambda 運算式的運算式樹狀架構，以建立可執行的委派。 這提供一個機制來執行由運算式樹狀架構表示的程式碼。

運算式樹狀架構可表示針對您所建立之任何指定建構執行的程式碼。 只要您編譯和執行程式碼的環境符合您建立運算式的環境，一切就會如預期運作。 如果不是這種情況，則預期會發生錯誤，而且會在第一次測試使用運算式樹狀架構的任何程式碼時攔截到這些錯誤。

[下一個主題 -- 解譯運算式](expression-trees-interpreting.md)

