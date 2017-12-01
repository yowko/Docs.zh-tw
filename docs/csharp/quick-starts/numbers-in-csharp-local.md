---
title: "快速入門-C# 中的數字-C# 指南"
description: "了解 C# 中瀏覽數字型別、 屬性和方法。"
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 821cca4ea6d6148410e9b179f05d5b74c4844628
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2017
---
# <a name="numbers-in-c-quick-start"></a>在 C# 快速入門中的數字 #

本快速入門將教導您有關 C# 中的數字類型以互動方式。 您會將寫入少量程式碼，然後您會編譯並執行該程式碼。 快速入門中包含一系列的課程中，瀏覽數字和 C# 中的數學運算作業。 這些課程會教導您 C# 語言的基本概念。

本快速入門預期要有可用於開發的機器。 .NET 主題[開始在 10 分鐘後](https://www.microsoft.com/net/core)已設定 Mac、 電腦或 Linux 本機開發環境的指示。

## <a name="explore-integer-math"></a>探索整數運算

建立名為目錄**數字快速入門**。 將該目錄設為目前的目錄，並執行 `dotnet new console -n NumbersInCSharp -o .`。

開啟**Program.cs**中您最愛的編輯器和取代列`Console.Writeline("Hello World!");`為下列：

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

執行這個程式碼輸入`dotnet run`命令視窗中。 

您看到的只是一種基本的整數數學運算。 `int` 型別代表**整數**，也就是正整數或負整數。 您使用 `+` 符號來執行加法。 整數常用的其他數學運算包括：

- `-` 用於減法
- `*` 用於乘法
- `/` 用於除法

讓我們開始探索這些不同的運算。 值寫入的該行之後加入下列幾行`c`:

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

執行這個程式碼輸入`dotnet run`命令視窗中。 
    
如果您想要的話，也可以試著在同一行中執行多個數學運算。 再試一次`c = a + b - 12 * 17;`例如。 允許混合變數和常數的數字。

> [!TIP]
> 在您探索 C# (或任何程式設計語言) 時，可能會在撰寫程式碼時犯錯。 **編譯器**會找出那些錯誤並回報給您。 當輸出會包含錯誤訊息時，仔細查看範例程式碼和您的視窗來查看要修正的項目中的程式碼。
> 該練習將有助於您了解 C# 程式碼的結構。     

您已完成的第一個步驟。 在開始下一節之前，讓我們將目前的程式碼移到另一個個別的方法。 這可讓您更輕鬆地開始處理新的範例。 將 `Main` 方法重新命名為 `WorkingWithIntegers`，然後撰寫會呼叫 `WorkingWithIntegers` 的新 `Main` 方法。 當您完成時，您的程式碼看起來應該像這樣：

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a>探索運算的順序

註解的呼叫`WorkingWithIntegers()`。 如此可讓更整齊的您在這一節中工作的輸出：

```csharp
//WorkingWithIntegers();
```

`//`啟動**註解**C# 中。 註解是您想要保留在原始程式碼中，但不是會以程式碼執行的任何文字。 編譯器不從註解會產生任何可執行程式碼。

針對不同數學運算的優先順序，C# 語言所定義的規則與您在數學所學的規則一致。
乘法和除法的優先順序高於加法和減法。
瀏覽，加入下列程式碼加入您`Main`方法，以及 execuing `dotnet run`:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

輸出示範了程式會先執行乘法，然後再執行加法。

您可以強制不同作業的順序加入周圍的括號，或您希望的作業執行第一次。 加入下列幾行，然後再次執行：

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

結合許多不同的運算來深入探索。 結果類似下列幾行加入底部您`Main`方法。 再試一次`dotnet run`一次。

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

您可能已注意到整數某個有趣的行為。 整數除法一律會產生整數結果，即使您希望的結果以包含十進位或小數部分。

如果您還沒看過這項行為，請嘗試下列程式碼的結尾您`Main`方法：

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

型別`dotnet run`一次，以查看結果。

再移，讓我們看您撰寫的這一節，並將其放在新的方法的所有程式碼。 呼叫該新方法`OrderPrecedence`。
您應該得到結果類似這樣：

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {   
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a  + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a>探索整數的精確度與限制
上一個範例示範了整數除法運算會將結果截斷。
您可以取得**餘數**使用**模數**運算子，`%`字元。 請嘗試下列的程式碼中您`Main`方法：

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

C# 整數型別有一個地方與數學上的整數不同：`int` 型別有最小和最大限制。 將此程式碼加入您`Main`方法以查看這些限制：
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

如果計算產生的值超出這些限制，就會發生**反向溢位**或**溢位**的情況。 答案看起來會是從其中一個限制回繞至另一個限制。 加入至這兩行程式`Main`方法的範例，請參閱：

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
請注意，答案非常接近最小 (負) 整數。 這與 `min + 2` 相同。 此加法運算已**溢出**整數允許的值。
此答案是非常大的負數，這是因為溢位會從最大整數值「回繞」至最小整數值。

當 `int` 型別不符合您的需求時，還有其他具有不同限制和精確度的數字型別可供使用。 我們會在下一篇探索那些數字型別。

同樣地，我們將移到不同的方法本節中您撰寫的程式碼。 將它命名為 `TestLimits`。 

## <a name="work-with-the-double-type"></a>使用 Double 型別

`double` 數字型別代表雙精確度浮點數。 您可能不熟悉這些字詞。 A**浮點數**數目是用於表示非整數類資料可能非常大或最小範圍內的數字。 **雙精確度**表示這些數字使用比**單精確度**更高的精確度來儲存。 在現代的電腦上，比較常使用雙精確度而非單精確度數字。
讓我們開始探索吧。 加入下列程式碼，並查看結果：

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

請注意答案包括商數的小數部分。 請嘗試略為複雜的雙精確度浮點數運算式：

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

雙精確度浮點數值的範圍遠大於整數值。 請嘗試下列您完成為止撰寫下列程式碼：

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

這些值列印出來的科學記號標記法。 左邊的數字`E`是有效的數字。 右邊的數字則為指數，亦即 10 的次方。 

就像數學上的小數數字，C# 中的雙精確度浮點數會發生捨入誤差。 請嘗試此程式碼：

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

如您所知，`0.3` 循環與 `1/3` 並不完全相同。

***挑戰***

嘗試使用 `double` 型別搭配大型數字、小型數字、乘法和除法的其他計算。  嘗試更複雜的計算。

您會花費一些時間與挑戰之後，需要您所撰寫，並將它放在新的方法中的程式碼。 命名新方法`WorkWithDoubles`。

## <a name="work-with-fixed-point-types"></a>使用固定點型別

您已經看過 C# 中的基本數字型別：整數和雙精確度浮點數。  還有一個您要了解的其他型別：`decimal` 型別。 `decimal`類型具有較小的範圍，但精確度卻高於`double`。 **固定點**這個詞代表小數點 (或二進位點) 不會移動。 讓我們來看一下：

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

請注意該範圍小於 `double` 型別。 透過嘗試下列程式碼，您可以看到 decimal (小數) 型別有較高的精確度：

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

數字上的 `M` 尾碼乃是指示常數應使用 `decimal` 型別。

請注意，使用 decimal (小數) 型別的運算在小數點右邊會有更多的數字。 

***挑戰***

您已經了解不同的數字型別，接著請撰寫程式碼，以計算半徑 2.50 英吋的圓形面積。 提醒您圓形面積是 PI 乘以半徑的平方。 提示： C# 包含 PI 常數<xref:System.Math.PI?displayProperty=nameWithType>可讓您針對該值。 

您可以檢查您的答案，由[查看在 GitHub 上的 完成後的範例程式碼](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)

如果您想要，嘗試其他的公式。 

您已經完成 「 數字在 C# 中 「 快速入門。 您可以繼續使用[分支和迴圈](branches-and-loops-local.md)開發環境中的快速入門。

您可以在下列主題中深入了解 C# 中的數字：

[整數類型表](../language-reference/keywords/integral-types-table.md)   
[浮點類型表](../language-reference/keywords/floating-point-types-table.md)   
[內建類型表](../language-reference/keywords/built-in-types-table.md)   
[隱含數值轉換表](../language-reference/keywords/implicit-numeric-conversions-table.md)   
[明確數值轉換表](../language-reference/keywords/explicit-numeric-conversions-table.md)

