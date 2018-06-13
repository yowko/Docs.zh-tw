---
title: 組建運算式樹狀架構
description: 了解建置運算式樹狀架構的技術。
ms.date: 06/20/2016
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 52e03bd1ea2635d75da6d70af6918b33b64622b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216310"
---
# <a name="building-expression-trees"></a>組建運算式樹狀架構

[上一篇 - 解譯運算式](expression-trees-interpreting.md)

目前為止看到的所有運算式樹狀架構都是由 C# 編譯器建立。 您唯一要做的是建立 Lambda 運算式，指派給類型為 `Expression<Func<T>>` 的變數或類似類型。 這不是建立運算式樹狀結構的唯一方法。 在許多情況下，您會發現需要在執行階段的記憶體中建立一個運算式。 

組建運算式樹狀架構很複雜，因為這些運算式樹狀架構是不可變的。 所謂不可變，表示樹狀結構必須從分葉向上組建到根。 您要用來組建運算式樹狀架構的 API 反映這項事實︰組建節點要使用的方法會採用其所有子系作為引數。 讓我們逐步解說幾個範例，向您示範技巧。

## <a name="creating-nodes"></a>建立節點

讓我們再次從相對簡單的開始。 在下列各節中，我們會使用前面用過的加法運算式︰

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

若要建構該運算式樹狀架構，您必須建構分葉節點。
分葉節點為常數，因此您可以使用 `Expression.Constant` 方法建立節點︰

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

接下來，您要組建加法運算式︰

```csharp
var addition = Expression.Add(one, two);
```

建立加法運算式之後，您可以建立 Lambda 運算式︰

```csharp
var lamdba = Expression.Lambda(addition);
```

這是非常簡單的 LambdaExpression，因為它不包含任何引數。
稍後在本節中，您會看到引數如何對應至參數，並組建更複雜的運算式。

針對和這個同樣簡單的運算式，您可以將所有呼叫結合成單一陳述式︰

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a>組建樹狀結構

這就是在記憶體中組建運算式樹狀結構的基本概念。 更複雜的樹狀結構通常表示在樹狀目錄中有更多的節點類型和更多的節點。 讓我們再執行一個範例，並多顯示兩個當您建立運算式樹狀架構時，通常會組建的節點類型︰引數節點和方法呼叫節點。

我們要組建運算式樹狀架構來建立此運算式︰

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
您要從建立 `x` 和 `y` 的參數運算式開始：

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

建立乘法和加法運算式要遵循您已見過的模式︰

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

接下來，您需要為 `Math.Sqrt` 呼叫建立方法呼叫運算式。

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

最後，將方法呼叫放入 Lambda 運算式中，確定定義 Lambda 運算式的引數︰

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

在這個更複雜的範例中，您會多看到幾個建立運算式樹狀架構經常需要的技巧。

首先，您需要先建立代表參數或區域變數的物件，再使用它們。 建立這些物件之後，就可以在您的運算式樹狀架構中隨時使用它們。

其次，您需要使用反映 API 的子集來建立 `MethodInfo` 物件，以便可以建立運算式樹狀架構來存取該方法。 您必須將自己限制在 .NET Core 平台上可用的反映 API 子集。 同樣地，這些技巧會延伸到其他的運算式樹狀架構。

## <a name="building-code-in-depth"></a>深度組建程式碼

您不會受限於使用這些 API 所可以組建的項目。 不過，想要組建的運算式樹狀架構越複雜，程式碼就越難管理及閱讀。 

我們要組建相當於這個程式碼的運算式樹狀架構︰

```csharp
Func<int, int> factorialFunc = (n) =>
{
    var res = 1;
    while (n > 1)
    {
        res = res * n;
        n--;
    }
    return res;
};
```

請注意，上例中，我並未組建運算式樹狀架構，只有委派。 使用 `Expression` 類別就無法建立陳述式 Lambda。 以下是組建相同功能需要的程式碼。 它之所以複雜是因為沒有 API 可組建 `while` 迴圈，您需要改組建包含條件式測試的迴圈，以及脫離迴圈的標籤目標。 

```csharp
var nArgument = Expression.Parameter(typeof(int), "n");
var result = Expression.Variable(typeof(int), "result");

// Creating a label that represents the return value
LabelTarget label = Expression.Label(typeof(int));

var initializeResult = Expression.Assign(result, Expression.Constant(1));

// This is the inner block that performs the multiplication,
// and decrements the value of 'n'
var block = Expression.Block(
    Expression.Assign(result,
        Expression.Multiply(result, nArgument)),
    Expression.PostDecrementAssign(nArgument)
);

// Creating a method body.
BlockExpression body = Expression.Block(
    new[] { result },
    initializeResult,
    Expression.Loop(
        Expression.IfThenElse(
            Expression.GreaterThan(nArgument, Expression.Constant(1)),
            block,
            Expression.Break(label, result)
        ),
        label
    )
);
```

組建階乘函式運算式樹狀結構的程式碼相當長，也更複雜，滿是標籤和 break 陳述式及其他項目，是日常編碼工作想要避免的坑。 

我在本節中也更新了訪客程式碼，可瀏覽此運算式樹狀結構中的每個節點，並寫出此範例所建立之節點的相關資訊。 您可以在 dotnet/docs GitHub 存放庫[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/csharp/expression-trees)。 建置並執行範例來親自試驗。 如需下載指示，請參閱[範例和教學課程](../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

## <a name="examining-the-apis"></a>檢查 API

運算式樹狀架構 API 是較難在 .NET Core 中巡覽的項目，但是沒關係。 其目的是相當複雜的任務︰撰寫會在執行階段產生程式碼的程式碼。 它們必須得複雜才能在支援 C# 語言提供的所有控制結構，以及在合理範圍內保持最小的 API 介面區之間取得平衡。 這項平衡表示許多控制結構不是由其 C# 建構所呈現，而是由代表基礎邏輯的建構所呈現，此基礎邏輯是編譯器從這些較高層級的建構所產生。 

此外，在此階段中，還有不能直接使用內建 `Expression` 類別方法來組建的 C# 運算式。 這些通常是新增至 C# 5 和 C# 6 的最新運算子和運算式。 (例如，無法組建 `async` 運算式，也不能直接建立新的 `?.` 運算子。)

[下一篇 - 轉譯運算式](expression-trees-translating.md)
