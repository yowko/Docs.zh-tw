---
title: "快速入門-分支和 lops-C# 手冊"
description: "在這個快速入門有關分支和迴圈中，撰寫 C# 程式碼來瀏覽支援條件式分支和迴圈重複執行陳述式的語言語法。"
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 4b077a29cf42072a93b054f50a13a4580ad54304
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2017
---
# <a name="branches-and-loops"></a>分支和迴圈

本快速入門將教導您如何撰寫程式碼，以檢查變數，並變更這些變數為基礎的執行路徑。 您撰寫 C# 程式碼，請參閱 < 編譯和執行它的結果。 快速入門中包含一系列的瀏覽分支和迴圈建構在 C# 中的課程。 這些課程會教導您 C# 語言的基本概念。

本快速入門預期要有可用於開發的機器。 .NET 主題[開始在 10 分鐘後](https://www.microsoft.com/net/core)已設定 Mac、 電腦或 Linux 本機開發環境的指示。

## <a name="make-decisions-using-the-if-statement"></a>使用進行決策`if`陳述式

建立名為目錄**分支快速入門**。 將該目錄設為目前的目錄，並執行 `dotnet new console -n BranchesAndLoops -o .`。 此命令會建立新的.NET Core 主控台應用程式目前的目錄中。 

開啟**Program.cs**中您最愛的編輯器和取代列`Console.Writeline("Hello World!");`為下列程式碼：

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

此程式碼嘗試輸入`dotnet run`在主控台視窗。 您應該會看到訊息 「 回應 」 大於 10。 列印至主控台。

修改 `b` 的宣告，讓總和小於 10： 

```csharp
int b = 3;
```

型別`dotnet run`一次。 因為答案小於 10，所以不會印出任何東西。 您正在測試的**條件**為 False。 您尚未有可執行的程式碼，因為您在 `if` 陳述式中僅撰寫了一個可能的分支：True 分支。

> [!TIP]
> 在您探索 C# (或任何程式設計語言) 時，可能會在撰寫程式碼時犯錯。 編譯器會尋找並報告該錯誤。 請仔細查看錯誤輸出，並且產生錯誤的程式碼。 Compler 錯誤通常可協助您找出問題。 

此第一個範例顯示的電源`if`和布林型別。 A*布林*是一個變數，可以有兩個值之一：`true`或`false`。 C# 定義一種特殊類型，`bool`的布林值變數。 `if` 陳述式會檢查 `bool` 的值。 當值為 `true` 時，就會執行 `if` 之後的陳述式。 否則，就會略過。 

這個流程可以檢查條件，並根據條件來執行陳述式，因此非常實用。


## <a name="make-if-and-else-work-together"></a>搭配使用 if 和 else

若要在 True 和 False 分支中執行不同的程式碼，則必須建立可在條件為 False 時執行的 `else` 分支。 試試看。 在下列程式碼，若要加入的最後兩行程式`Main`（您應該已經前四個） 的方法：

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

只有當測試的條件為 `false` 時，才會執行 `else` 關鍵字之後的陳述式。 結合`if`和`else`使用布林值條件提供您需要同時處理的所有電源`true`和`false`條件。

> [!IMPORTANT]
> `if` 和 `else` 陳述式之下的縮排是為了方便人類閱讀。
> C# 語言不會將縮排或空格視為有意義的內容。 `if` 或 `else` 關鍵字之後的陳述式將會根據條件來執行。 在這個快速入門中的所有範例，請依照都下列常見的作法是根據陳述式的控制流程的行縮排。

因為縮排沒有意義，當您要依條件執行的區塊中有超過一個陳述式時，就需要使用 `{` 和 `}` 來表示。 C# 程式設計人員通常會在所有的 `if` 和 `else` 子句上使用這些大括號。 下列範例是您剛才建立一個相同。 修改以符合下列程式碼上述程式碼：

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> 透過本快速入門的其餘部分，所有的程式碼範例包含大括號，接受的作法。

您可以測試更複雜的條件。 加入下列程式碼中的您`Main`到目前為止，您所撰寫的程式碼之後的方法：

```csharp
    int c = 4;
    if ((a + b + c > 10) && (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not greater than the second");
}
```

`&&` 代表「且」。 這表示兩個條件都必須為 True，才會執行 True 分支中的陳述式。  這些範例也示範在每個條件式分支中可以有多個陳述式，前提是必須將陳述式放在 `{` 和 `}` 之中。

您也可以使用`||`來代表 「 或 」。 加入下列程式碼之後您已經為止寫,：

```csharp
if ((a + b + c > 10) || (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not greater than the second");
}
```

您已完成的第一個步驟。 在開始下一節之前，讓我們將目前的程式碼移到另一個個別的方法。 這可讓您更輕鬆地開始處理新的範例。 將 `Main` 方法重新命名為 `ExploreIf`，然後撰寫會呼叫 `ExploreIf` 的新 `Main` 方法。 當您完成時，您的程式碼看起來應該像這樣：

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }            
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

註解的呼叫`ExploreIf()`。 如此可讓更整齊的您在這一節中工作的輸出：

```csharp
//ExploreIf();
```

`//`啟動**註解**C# 中。 註解是您想要保留在原始程式碼中，但不是會以程式碼執行的任何文字。 編譯器不從註解會產生任何可執行程式碼。

## <a name="use-loops-to-repeat-operations"></a>使用迴圈重複執行作業

在您使用這一節**迴圈**重複陳述式。 請嘗試此程式碼中的您`Main`方法：

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

`while`陳述式會檢查條件，並執行陳述式或之後的陳述式區塊`while`。 它會重複檢查的條件和執行這些陳述式，直到條件為 false。

在此範例中有一個新的運算子。 `counter` 變數之後的 `++` 是**遞增**運算子。 它將值加 1 `counter` ，並將此值於`counter`變數。

> [!IMPORTANT]
> 請確定`while`迴圈條件變更為 false，因為執行的程式碼。 否則，您建立的**無限迴圈**程式永遠不會結束。 不會示範在此範例中，因此您可以強制執行您的程式，若要結束使用**CTRL-C**或其他方式。

`while` 迴圈會先測試條件，然後才執行 `while` 之後的程式碼。 `do` ... `while` 迴圈會先執行程式碼，然後才檢查條件。 執行下列程式碼所示迴圈時：

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

這`do`迴圈及更早版本`while`迴圈產生相同的輸出。

## <a name="work-with-the-for-loop"></a>使用 for 迴圈

**如**迴圈常用於 C#。 請嘗試在您的 main （） 方法中的這段程式碼：

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

這與先前使用的 `while` 迴圈和 `do` 迴圈有相同的功能。 `for` 陳述式有三個部分來控制其運作方式。 

第一個部分是 **for 初始設定式**：`for index = 0;` 宣告 `index` 是迴圈變數，然後將它的初始值設為 `0`。

中間的部分是 **for 條件**：`index < 10` 宣告此 `for` 迴圈只要 counter (計數器) 的值小於 10，就會繼續執行。

最後一個部分是 **for 迭代器**：`index++` 會指定在執行 `for` 陳述式之後的區塊後，如何修改迴圈變數。 在這裡，它指定 `index` 應該在每次執行區塊之後遞增 1。

您可以自行實驗這些部分。 請嘗試下列各項：

- 變更初始設定式，以不同的值開始。
- 變更條件，以不同的值停止。

當您完成後，我們會繼續使用您學到的內容來撰寫一些程式碼。

## <a name="combine-branches-and-loops"></a>結合分支和迴圈

您已經了解 C# 語言中的 `if` 陳述式和迴圈建構，接著看看您是否能夠撰寫 C# 程式碼，以找出從整數 1 至 20 能夠被 3 整除之數字的總和。  下列提供幾個提示：

- `%` 運算子可提供除法運算的餘數。
- `if`陳述式可讓您的條件，請參閱是否數字應該加總的一部分。
- `for` 迴圈可協助您將 1 到 20 的所有數字重複一系列的步驟。

請自己試試看。 然後檢查成果。 您可以看到所可能解答[GitHub 上檢視已完成的程式碼](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54)。

您已經完成 「 分支和迴圈 」 的快速入門。

您可以繼續使用[陣列與集合](arrays-and-collections.md)開發環境中的快速入門。

您可以在下列主題中深入了解這些概念：

[If 和 else 陳述式](../language-reference/keywords/if-else.md)   
[While 陳述式](../language-reference/keywords/while.md)   
[Do 陳述式](../language-reference/keywords/do.md)   
[For 陳述式](../language-reference/keywords/for.md)   
