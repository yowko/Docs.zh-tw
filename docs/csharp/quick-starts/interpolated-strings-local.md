---
title: "快速入門 - 插入字串 - C# 指南"
description: "在這個有關插入字串的快速入門中，您可以撰寫 C# 程式碼，以將運算式結果包含在較大的字串中。"
author: rpetrusha
ms.author: ronpet
ms.date: 01/11/2018
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 14185dd4e364f12756541ac6401d1c6ff3206fe9
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2018
---
# <a name="interpolated-strings"></a>插入字串

本快速入門將教導您如何在 C# 中使用插入字串，以將值插入至單一輸出字串。 您將會撰寫 C# 程式碼，並查看程式碼編譯和執行的結果。 快速入門包含一系列的課程，以將值插入至字串，並以不同的方式格式化這些值。

本快速入門需要您具備可用於開發的電腦。 .NET 主題[只要 10 分鐘立即上手](https://www.microsoft.com/net/core) \(英文\) 中有關於在 Mac、PC 或 Linux 上設定本機開發環境的指示。 您可以在[本機快速入門簡介](local-environment.md)中快速檢視將會用到的命令，並取得可提供詳細資料的連結。 

## <a name="create-an-interpolated-string"></a>建立插入字串

建立名為 **interpolated-quickstart** 的目錄。 讓它成為目前目錄，並從主控台視窗中執行下列命令：

```console
dotnet new console -n interpolated -o .
```

此命令會在目前的目錄中建立新的 .NET Core 主控台應用程式。

在您最愛的編輯器中開啟 **Program.cs**，並將 `Console.WriteLine("Hello World!");` 行取代為下列程式碼；其中，您可以將 `<name>` 取代為您的名稱：

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```
在主控台視窗中鍵入 `dotnet run` 來嘗試此程式碼。 當您執行程式時，它會顯示問候語中包含您名稱的單一字串。 <xref:System.Console.WriteLine%2A> 方法呼叫中所含的字串是「插入字串」。 它是一種範本，可讓您從包含內嵌程式碼的字串建構單一字串 (稱為「結果字串」)。 插入字串特別適用於將值插入至字串或將字串串連 (聯結在一起)。 
    
這個簡單範例包含每個插入字串都必須要有的兩個項目： 

- 左引號字元之前開頭為 `$` 字元的字串常值。 `$` 符號與引號字元之間不能有任何空格。 (如果您想要查看包含空格時會發生什麼情況，請在 `$` 字元後面插入空格、儲存檔案，然後在主控台視窗中鍵入 `dotnet run` 以重新執行程式。 C# 編譯器會顯示錯誤訊息「錯誤 CS1056: 未預期的字元 '$'」)。 

- 一或多個「插入運算式」。 插入運算式是以左右大括號 (`{` 和 `}`) 指出。 您可以放置任何 C# 運算式，以傳回大括號內的值 (包含 `null`)。 

嘗試更多包含一些其他資料類型的插入字串範例。
    
## <a name="include-different-data-types"></a>包含不同的資料類型

在上節中，您使用插入字串將某個字串插入至另一個字串內部。 不過，插入字串運算式可以是任意資料類型。 嘗試具有多個資料類型值的插入字串。 
    
下列範例包含具有 `Vegetable` 物件的插入運算式、`Unit` 列舉的成員、<xref:System.DateTime> 值和 <xref:System.Decimal> 值。 將編輯器中的所有 C# 程式碼都取代為下列程式碼，然後使用 `console run` 命令來執行此程式碼：

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Example
{
   public enum Unit { item, pound, ounce, dozen };
   
   public static void Main()
   {
      var item = new Vegetable("eggplant");
      var date = DateTime.Now;
      var price = 1.99m;
      var unit = Unit.item;
      Console.WriteLine($"On {date}, the price of {item} was {price} per {unit}.");
   }
}
```
    
請注意，第二個插入運算式包含向主控台顯示之結果字串中的 `item` 物件；而在此情況下，會將字串 "eggplant" 插入至結果字串。 原因是插入運算式的類型不是字串時，C# 編譯器會執行下列作業：

- 如果插入運算式是 `null`，則插入運算式會傳回空字串 ("" 或 <xref:System.String.Empty?displayProperty=nameWithType>)。

- 如果插入運算式不是 `null`，則會呼叫插入運算式類型的 `ToString` 方法。 您可以註銷範例中 `Vegetable.ToString` 方法的定義來進行測試，方式是在其前面放置註解符號 (`//`)。 在輸出中，字串 "eggplant" 會取代為類型名稱 "Vegetable"，這是 <xref:System.Object.ToString?displayProperty=nameWithType> 方法的預設行為。   

在此範例的輸出中，日期太過精確 (eggplant 價格不會因第二個而變更)，而價格值未指出貨幣單位。 在下節中，您將學習如何控制插入運算式所傳回字串的格式來修正這些問題。

## <a name="control-the-formatting-of-interpolated-expressions"></a>控制插入運算式的格式

在上節中，已將兩個格式不佳的字串插入至結果字串。 其中一個是只有日期才適合的日期和時間值。 第二個是未指出其貨幣單位的價格。 這兩個問題都很容易解決。 插入運算式可以包含「格式字串」，以控制特定類型的格式。 修改前一個範例中的 `Console.WriteLine` 呼叫，使其包含日期和價位欄位的格式規範，如下行所示：

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```
    
在插入運算式後面接著冒號和格式字串，即可指定格式字串。 "d" 是[標準日期和時間格式字串](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier)，可呈現簡短日期格式。 "C2" 是[標準數值格式字串](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier)，可將數字呈現為小數點後面有兩位數的貨幣值。

.NET Standard 程式庫中有多種類型都支援一組預先定義的格式字串。 其中包含所有數值類型以及日期和時間類型。 如需支援格式字串之類型的完整清單，請參閱[在 .NET 中格式化類型](../../standard/base-types/formatting-types.md)一文中的[格式字串和 .NET 類別庫類型](../../standard/base-types/formatting-types.md#stringRef)。 任何類型都可以支援一組格式字串，而且您也可以開發自訂格式延伸模組，以提供現有類型的自訂格式。 如需透過提供 <xref:System.ICustomFormatter> 實作以自訂格式的資訊，請參閱[在 .NET 中格式化類型](../../standard/base-types/formatting-types.md)一文中的[使用 ICustomFormatter 的自訂格式](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter)。

嘗試在文字編輯器中修改格式字串，並在每次進行變更時，重新執行程式以查看變更對日期和時間以及數值格式的影響。 將 `{date:d}` 中的 "d" 變更為 "t" (顯示簡短時間格式)、"y" (顯示年份和月份) 以及 "yyyy" (將年份顯示為四位數)。 將 `{price:C2}` 中的 "C2" 變更為 "e" (適用於指數標記法) 和 "F3" (適用於小數點後面有三位數的數值)。

除了控制格式之外，您也可以控制插入運算式所傳回字串的欄位寬度和對齊方式。 在下節中，您將學習如何執行這項作業。

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a>控制插入運算式的欄位寬度和對齊方式

一般情況下，結果字串中包含插入運算式所傳回的字串時，不會有任何前置或尾端空格。 特別是使用一組資料時，插入運算式可讓您指定欄位寬度和其對齊方式。 若要確認這一點，請將文字編輯器中的所有程式碼都取代為下列程式碼，然後鍵入 `console run` 以執行程式：
    
```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>();
      titles.Add("Doyle, Arthur Conan", "Hound of the Baskervilles, The");
      titles.Add("London, Jack", "Call of the Wild, The");
      titles.Add("Shakespeare, William", "Tempest, The");

      Console.WriteLine("Author and Title List");
      Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
      foreach (var title in titles)
         Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
   }
}
```
    
作者名稱會靠左對齊，而他們所撰寫的標題會靠右對齊。 在運算式後面新增逗號 (",")，並指定欄位寬度，即可指定對齊方式。 如果欄位寬度是正數，則欄位會靠右對齊：

```text
{expression, width}
```

如果欄位寬度是負數，則欄位會靠左對齊：

```text
{expression, -width}
```

嘗試移除 `{"Author",-25}` 和 `{title.Key,-25}` 插入運算式中的負號，然後重新執行此範例，如下列程式碼所執行：

```csharp
Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
foreach (var title in titles)
   Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
```

目前，作者資訊會靠右對齊。

您可以將欄位寬度和格式字串結合到單一插入運算式。 先出現欄位寬度，後面接著冒號和格式字串。 將 `Main` 方法內的所有程式碼都取代為下列程式碼，以顯示具有所定義欄位寬度的三個格式化字串。 然後輸入 `dotnet run` 命令，以執行程式。

```csharp
Console.WriteLine($"{DateTime.Now,-20:d} Hour {DateTime.Now,-10:HH} {1063.342,15:N2} feet");
```
輸出會與下列內容類似：

```console
1/11/2018            Hour 09                1,063.34 feet
```

您已完成插入字串快速入門。 
    
您可以在自己的開發環境中，繼續完成[陣列和集合](arrays-and-collections.md)快速入門中的內容。

您可以在＜C# 參考＞的[插入字串](../language-reference/keywords/interpolated-strings.md)主題中，深入了解如何使用插入字串。

