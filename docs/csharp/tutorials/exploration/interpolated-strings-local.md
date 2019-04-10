---
title: 字串插補 - C# 教學課程
description: 此教學課程示範如何使用 C# 字串插補功能，在較大字串中包含格式化運算式結果。
author: rpetrusha
ms.author: ronpet
ms.date: 10/23/2018
ms.openlocfilehash: 97773659ea7dd00c291aa6a96401cac531adfdc8
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921364"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a>使用字串插補來建構格式化的字串

此教學課程將教您如何使用 C# [字串插補](../../language-reference/tokens/interpolated.md)，在單一結果字串中插入值。 您將會撰寫 C# 程式碼，並查看程式碼編譯和執行的結果。 此教學課程包含一系列的課程，示範如何將值插入至字串，並以不同的方式設定那些值的格式。

此教學課程要求您必須有可用於開發的電腦。 .NET 主題[只要 10 分鐘立即上手](https://www.microsoft.com/net/core) \(英文\) 中有關於在 Mac、PC 或 Linux 上設定本機開發環境的指示。 您也可以在瀏覽器中完成此教學課程的[互動式版本](interpolated-strings.yml)。

## <a name="create-an-interpolated-string"></a>建立插入字串

建立名為 **interpolated** 的目錄。 讓它成為目前目錄，並從主控台視窗中執行下列命令：

```console
dotnet new console
```

此命令會在目前的目錄中建立新的 .NET Core 主控台應用程式。

在您最愛的編輯器中開啟 **Program.cs**，並將 `Console.WriteLine("Hello World!");` 行取代為下列程式碼；其中，您可以將 `<name>` 取代為您的名稱：

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

在主控台視窗中鍵入 `dotnet run` 來嘗試此程式碼。 當您執行程式時，它會顯示問候語中包含您名稱的單一字串。 <xref:System.Console.WriteLine%2A> 方法呼叫中所含的字串是「插入字串」。 它是一種範本，可讓您從包含內嵌程式碼的字串建構單一字串 (稱為「結果字串」)。 插入字串特別適用於將值插入至字串或將字串串連 (聯結在一起)。

這個簡單範例包含每個插入字串都必須要有的兩個項目：

- 左引號字元之前開頭為 `$` 字元的字串常值。 `$` 符號與引號字元之間不能有任何空格。 (如果您想要查看包含空格時會發生什麼情況，請在 `$` 字元後面插入空格、儲存檔案，然後在主控台視窗中鍵入 `dotnet run` 以重新執行程式。 C# 編譯器會顯示錯誤訊息「錯誤 CS1056:未預期的字元 '$'」。)

- 一或多個「插入運算式」。 插入運算式是以左右大括號 (`{` 和 `}`) 指出。 您可以放置任何 C# 運算式，以傳回大括號內的值 (包含 `null`)。

嘗試更多包含一些其他資料類型的字串插補範例。

## <a name="include-different-data-types"></a>包含不同的資料類型

在上節中，您使用字串插補將某個字串插入至另一個字串內部。 不過，插入運算式的結果可以是任意資料類型。 請包含插入字串中各種資料類型的值。

在下列範例中，我們先定義具有 `Name` [屬性](../../properties.md)與 `ToString` [方法](../../methods.md)的[類別](../../programming-guide/classes-and-structs/classes.md)資料類型 `Vegetable`，它會[覆寫](../../language-reference/keywords/override.md) <xref:System.Object.ToString?displayProperty=nameWithType> 方法的行為。 [`public` 存取修飾詞](../../language-reference/keywords/public.md)會使該方法可用於取得任何用戶端程式碼，以取得 `Vegetable` 執行個體的字串表示。 在此範例中，`Vegetable.ToString` 方法會傳回 `Name` 屬性的值，此屬性會在 `Vegetable` [建構函式](../../programming-guide/classes-and-structs/constructors.md)中初始化：

```csharp
public Vegetable(string name) => Name = name;
```

接著，我們使用 [ `new`關鍵字](../../language-reference/keywords/new-operator.md)並提供建構函式名稱 `Vegetable`，建立名為 `item` 的 `Vegetable` 類別執行個體：

```csharp
var item = new Vegetable("eggplant");
```

最後，我們將 `item` 變數併入插入字串，而此插入字串也包含 <xref:System.DateTime> 值、<xref:System.Decimal> 值和 `Unit` [enumeration](../../programming-guide/enumeration-types.md) 值。 將編輯器中的所有 C# 程式碼都取代為下列程式碼，然後使用 `dotnet run` 命令來執行此程式碼：

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Program
{
   public enum Unit { item, kilogram, gram, dozen };

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

請注意，插入字串中的插入運算式 `item` 會解析為結果字串中的文字 "eggplant"。 原因是，運算式結果的型別不是字串時，會使用下列方式將結果解析為字串：

- 如果插入運算式評估為 `null`，則會使用空字串 (""，或 <xref:System.String.Empty?displayProperty=nameWithType>)。

- 如果插入運算式未評估為 `null`，一般會呼叫結果類型的 `ToString` 方法。 測試這項作業的方式是更新 `Vegetable.ToString` 方法的實作。 您甚至可能不需要實作 `ToString` 方法，因為每個類型都有這個方法的某種實作。 若要測試此作業，請將範例中 `Vegetable.ToString` 方法的定義註解化 (作法是在其前面放置註解符號 `//`)。 在輸出中，字串 "eggplant" 會取代為完整類型名稱 (在此範例中，為 "Vegetable")，這是 <xref:System.Object.ToString?displayProperty=nameWithType> 方法的預設行為。 列舉值 `ToString` 方法的預設行為是傳回該值的字串表示。

在此範例的輸出中，日期太過精確 (eggplant 價格不會因第二個而變更)，而價格值未指出貨幣單位。 在下節中，您將學習如何控制運算式結果的字串表示格式來修正這些問題。

## <a name="control-the-formatting-of-interpolated-expressions"></a>控制插入運算式的格式

在上節中，已將兩個格式不佳的字串插入至結果字串。 其中一個是只有日期才適合的日期和時間值。 第二個是未指出其貨幣單位的價格。 這兩個問題都很容易解決。 字串插補可讓您指定「格式字串」，以控制特定類型的格式。 修改前一個範例中的 `Console.WriteLine` 呼叫，使其包含日期和價格運算式的格式字串，如下行所示：

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

在插入運算式後面接著冒號 (":") 和格式字串，即可指定格式字串。 "d" 是[標準日期和時間格式字串](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier)，可呈現簡短日期格式。 "C2" 是[標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier)，可將數字呈現為小數點後面有兩位數的貨幣值。

.NET 程式庫中有多種類型都支援一組預先定義的格式字串。 其中包含所有數值類型以及日期和時間類型。 如需支援格式字串之類型的完整清單，請參閱[在 .NET 中格式化類型](../../../standard/base-types/formatting-types.md)一文中的[格式字串和 .NET 類別庫類型](../../../standard/base-types/formatting-types.md#stringRef)。

嘗試在文字編輯器中修改格式字串，並在每次進行變更時，重新執行程式以查看變更對日期和時間以及數值格式的影響。 將 `{date:d}` 中的 "d" 變更為 "t" (顯示簡短時間格式)、"y" (顯示年份和月份) 以及 "yyyy" (將年份顯示為四位數)。 將 `{price:C2}` 中的 "C2" 變更為 "e" (適用於指數標記法) 和 "F3" (適用於小數點後面有三位數的數值)。

除了控制格式之外，您也可以控制結果字串中所含格式化字串的欄位寬度和對齊方式。 在下節中，您將學習如何執行這項作業。

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a>控制插入運算式的欄位寬度和對齊方式

一般情況下，插入運算式的結果格式化為字串時，結果字串中會包含該字串，而且沒有前置或尾端空格。 特別是當您使用一組資料時，可控制欄位寬度和文字對齊方式有助於產生更容易讀取的輸出。 若要確認這一點，請將文字編輯器中的所有程式碼都取代為下列程式碼，然後鍵入 `dotnet run` 以執行程式：

```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>()
      {
          ["Doyle, Arthur Conan"] = "Hound of the Baskervilles, The",
          ["London, Jack"] = "Call of the Wild, The",
          ["Shakespeare, William"] = "Tempest, The"
      };

      Console.WriteLine("Author and Title List");
      Console.WriteLine();
      Console.WriteLine($"|{"Author",-25}|{"Title",30}|");
      foreach (var title in titles)
         Console.WriteLine($"|{title.Key,-25}|{title.Value,30}|");
   }
}
```

作者名稱會靠左對齊，而他們所撰寫的標題會靠右對齊。 在插入運算式後面新增逗號 (",")，並指定「最小」欄位寬度，即可指定對齊方式。 如果指定的值是正數，則欄位會靠右對齊。 如果它是負數，則欄位會靠左對齊。

嘗試移除 `{"Author",-25}` 和 `{title.Key,-25}` 程式碼中的負號，然後重新執行此範例，如下列程式碼所執行：

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

目前，作者資訊會靠右對齊。

您可以將對齊規範與格式字串結合為單一插入運算式。 若要這樣做，請先指定對齊方式，而且後面接著冒號和格式字串。 將 `Main` 方法內的所有程式碼都取代為下列程式碼，以顯示具有所定義欄位寬度的三個格式化字串。 然後輸入 `dotnet run` 命令，以執行程式。

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

輸出會與下列內容類似：

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

您已完成字串插補教學課程。

如需詳細資訊，請參閱[字串插補](../../language-reference/tokens/interpolated.md)主題和 [C# 中的字串插補](../../tutorials/string-interpolation.md)教學課程。
