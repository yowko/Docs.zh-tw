---
title: "插入字串教學課程 - C# 本機快速入門"
description: "在這個有關插入字串的快速入門中，您可以撰寫 C# 程式碼，以將運算式結果包含在較大的字串中。"
author: rpetrusha
ms.author: ronpet
ms.date: 01/11/2018
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 3cd9fc23dba104f92255b031eef32f80cca915b0
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="interpolated-strings"></a><span data-ttu-id="0fe12-103">插入字串</span><span class="sxs-lookup"><span data-stu-id="0fe12-103">Interpolated strings</span></span>

<span data-ttu-id="0fe12-104">本快速入門將教導您如何在 C# 中使用插入字串，以將值插入至單一輸出字串。</span><span class="sxs-lookup"><span data-stu-id="0fe12-104">This quickstart teaches you how to use interpolated strings in C# to insert values into a single ouput string.</span></span> <span data-ttu-id="0fe12-105">您將會撰寫 C# 程式碼，並查看程式碼編譯和執行的結果。</span><span class="sxs-lookup"><span data-stu-id="0fe12-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="0fe12-106">本快速入門包含一系列的課程，說明如何將值插入至字串，並以不同的方式設定那些值的格式。</span><span class="sxs-lookup"><span data-stu-id="0fe12-106">The quickstart contains a series of lessons that insert values into strings, and format those values in different ways.</span></span>

<span data-ttu-id="0fe12-107">本快速入門需要您具備可用於開發的電腦。</span><span class="sxs-lookup"><span data-stu-id="0fe12-107">This quickstart expects that you have a machine you can use for development.</span></span> <span data-ttu-id="0fe12-108">.NET 主題[只要 10 分鐘立即上手](https://www.microsoft.com/net/core) \(英文\) 中有關於在 Mac、PC 或 Linux 上設定本機開發環境的指示。</span><span class="sxs-lookup"><span data-stu-id="0fe12-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="0fe12-109">您可以在[本機快速入門簡介](local-environment.md)中快速檢視將會用到的命令，並取得可提供詳細資料的連結。</span><span class="sxs-lookup"><span data-stu-id="0fe12-109">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span> 

## <a name="create-an-interpolated-string"></a><span data-ttu-id="0fe12-110">建立插入字串</span><span class="sxs-lookup"><span data-stu-id="0fe12-110">Create an interpolated string</span></span>

<span data-ttu-id="0fe12-111">建立名為 **interpolated-quickstart** 的目錄。</span><span class="sxs-lookup"><span data-stu-id="0fe12-111">Create a directory named **interpolated-quickstart**.</span></span> <span data-ttu-id="0fe12-112">讓它成為目前目錄，並從主控台視窗中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="0fe12-112">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console -n interpolated -o .
```

<span data-ttu-id="0fe12-113">此命令會在目前的目錄中建立新的 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="0fe12-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="0fe12-114">在您最愛的編輯器中開啟 **Program.cs**，並將 `Console.WriteLine("Hello World!");` 行取代為下列程式碼；其中，您可以將 `<name>` 取代為您的名稱：</span><span class="sxs-lookup"><span data-stu-id="0fe12-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```
<span data-ttu-id="0fe12-115">在主控台視窗中輸入 `dotnet run` 來嘗試此程式碼。</span><span class="sxs-lookup"><span data-stu-id="0fe12-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="0fe12-116">當您執行程式時，它會顯示問候語中包含您名稱的單一字串。</span><span class="sxs-lookup"><span data-stu-id="0fe12-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="0fe12-117"><xref:System.Console.WriteLine%2A> 方法呼叫中所含的字串是「插入字串」。</span><span class="sxs-lookup"><span data-stu-id="0fe12-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string*.</span></span> <span data-ttu-id="0fe12-118">它是一種範本，可讓您從包含內嵌程式碼的字串建構單一字串 (稱為「結果字串」)。</span><span class="sxs-lookup"><span data-stu-id="0fe12-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="0fe12-119">插入字串特別適用於將值插入至字串或將字串串連 (聯結在一起)。</span><span class="sxs-lookup"><span data-stu-id="0fe12-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span> 
    
<span data-ttu-id="0fe12-120">這個簡單範例包含每個插入字串都必須要有的兩個項目：</span><span class="sxs-lookup"><span data-stu-id="0fe12-120">This simple example contains the two elements that every interpolated string must have:</span></span> 

- <span data-ttu-id="0fe12-121">左引號字元之前開頭為 `$` 字元的字串常值。</span><span class="sxs-lookup"><span data-stu-id="0fe12-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="0fe12-122">`$` 符號與引號字元之間不能有任何空格。</span><span class="sxs-lookup"><span data-stu-id="0fe12-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="0fe12-123">(如果您想要查看包含空格時會發生什麼情況，請在 `$` 字元後面插入空格、儲存檔案，然後在主控台視窗中輸入 `dotnet run` 以重新執行程式。</span><span class="sxs-lookup"><span data-stu-id="0fe12-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="0fe12-124">C# 編譯器會顯示錯誤訊息「錯誤 CS1056: 未預期的字元 '$'」)。</span><span class="sxs-lookup"><span data-stu-id="0fe12-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span> 

- <span data-ttu-id="0fe12-125">一或多個「插入運算式」。</span><span class="sxs-lookup"><span data-stu-id="0fe12-125">One or more *interpolated expressions*.</span></span> <span data-ttu-id="0fe12-126">插入運算式是以左右大括號 (`{` 和 `}`) 指出。</span><span class="sxs-lookup"><span data-stu-id="0fe12-126">An interpolated expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="0fe12-127">您可以放置任何 C# 運算式，以傳回大括號內的值 (包含 `null`)。</span><span class="sxs-lookup"><span data-stu-id="0fe12-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span> 

<span data-ttu-id="0fe12-128">嘗試更多包含一些其他資料類型的插入字串範例。</span><span class="sxs-lookup"><span data-stu-id="0fe12-128">Let's try a few more interpolated string examples with some other data types.</span></span>
    
## <a name="include-different-data-types"></a><span data-ttu-id="0fe12-129">包含不同的資料類型</span><span class="sxs-lookup"><span data-stu-id="0fe12-129">Include different data types</span></span>

<span data-ttu-id="0fe12-130">在上節中，您使用插入字串將某個字串插入至另一個字串內部。</span><span class="sxs-lookup"><span data-stu-id="0fe12-130">In the previous section, you used an interpolated string to insert one string inside of another.</span></span> <span data-ttu-id="0fe12-131">不過，插入字串運算式可以是任意資料類型。</span><span class="sxs-lookup"><span data-stu-id="0fe12-131">An interpolated string expression can be any data type, though.</span></span> <span data-ttu-id="0fe12-132">嘗試具有多個資料類型值的插入字串。</span><span class="sxs-lookup"><span data-stu-id="0fe12-132">Let's try an interpolated string that has values of multiple data types.</span></span> 
    
<span data-ttu-id="0fe12-133">下列範例包含具有 `Vegetable` 物件的插入運算式、`Unit` 列舉的成員、<xref:System.DateTime> 值和 <xref:System.Decimal> 值。</span><span class="sxs-lookup"><span data-stu-id="0fe12-133">The following example includes interpolated expressions with a `Vegetable` object, a member of the `Unit` enumeration, a <xref:System.DateTime> value, and a <xref:System.Decimal> value.</span></span> <span data-ttu-id="0fe12-134">將編輯器中的所有 C# 程式碼都取代為下列程式碼，然後使用 `console run` 命令來執行此程式碼：</span><span class="sxs-lookup"><span data-stu-id="0fe12-134">Replace all of the C# code in your editor with the following code, and then use the `console run` command to run it:</span></span>

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
    
<span data-ttu-id="0fe12-135">請注意，第二個插入運算式包含向主控台顯示之結果字串中的 `item` 物件；而在此情況下，會將字串 "eggplant" 插入至結果字串。</span><span class="sxs-lookup"><span data-stu-id="0fe12-135">Note that the second interpolated expression includes the `item` object in the result string that's displayed to the console, and in this case the string "eggplant" is inserted into the result string.</span></span> <span data-ttu-id="0fe12-136">原因是插入運算式的類型不是字串時，C# 編譯器會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="0fe12-136">That's because, when the type of an interpolated expression is not a string, the C# compiler does the following:</span></span>

- <span data-ttu-id="0fe12-137">如果插入運算式是 `null`，則插入運算式會傳回空字串 ("" 或 <xref:System.String.Empty?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="0fe12-137">If the interpolated expression is `null`, the interpolated expression returns an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>).</span></span>

- <span data-ttu-id="0fe12-138">如果插入運算式不是 `null`，則會呼叫插入運算式類型的 `ToString` 方法。</span><span class="sxs-lookup"><span data-stu-id="0fe12-138">If the interpolated expression is not `null`, the `ToString` method of the type of the interpolated expression is called.</span></span> <span data-ttu-id="0fe12-139">您可以註銷範例中 `Vegetable.ToString` 方法的定義來進行測試，方式是在其前面放置註解符號 (`//`)。</span><span class="sxs-lookup"><span data-stu-id="0fe12-139">You can test this by commenting out the definition of the `Vegetable.ToString` method in the example by putting a comment symbol (`//`) in front of it.</span></span> <span data-ttu-id="0fe12-140">在輸出中，字串 "eggplant" 會取代為類型名稱 "Vegetable"，這是 <xref:System.Object.ToString?displayProperty=nameWithType> 方法的預設行為。</span><span class="sxs-lookup"><span data-stu-id="0fe12-140">In the output, the string "eggplant" is replaced by the type name, "Vegetable", which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span>   

<span data-ttu-id="0fe12-141">在此範例的輸出中，日期太過精確 (eggplant 價格不會因第二個而變更)，而價格值未指出貨幣單位。</span><span class="sxs-lookup"><span data-stu-id="0fe12-141">In the output from this example, the date is too precise (the price of eggplant does not vary by the second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="0fe12-142">在下節中，您將學習如何控制插入運算式所傳回字串的格式來修正這些問題。</span><span class="sxs-lookup"><span data-stu-id="0fe12-142">In the next section, you'll learn how to fix those issues by controlling the format of strings returned by interpolated expressions.</span></span>

## <a name="control-the-formatting-of-interpolated-expressions"></a><span data-ttu-id="0fe12-143">控制插入運算式的格式</span><span class="sxs-lookup"><span data-stu-id="0fe12-143">Control the formatting of interpolated expressions</span></span>

<span data-ttu-id="0fe12-144">在上節中，已將兩個格式不佳的字串插入至結果字串。</span><span class="sxs-lookup"><span data-stu-id="0fe12-144">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="0fe12-145">其中一個是只有日期才適合的日期和時間值。</span><span class="sxs-lookup"><span data-stu-id="0fe12-145">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="0fe12-146">第二個是未指出其貨幣單位的價格。</span><span class="sxs-lookup"><span data-stu-id="0fe12-146">The second was a price that did not indicate its unit of currency.</span></span> <span data-ttu-id="0fe12-147">這兩個問題都很容易解決。</span><span class="sxs-lookup"><span data-stu-id="0fe12-147">Both issues are easy to address.</span></span> <span data-ttu-id="0fe12-148">插入運算式可以包含「格式字串」，以控制特定類型的格式。</span><span class="sxs-lookup"><span data-stu-id="0fe12-148">Interpolated expressions can include *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="0fe12-149">修改前一個範例中的 `Console.WriteLine` 呼叫，使其包含日期和價位欄位的格式規範，如下行所示：</span><span class="sxs-lookup"><span data-stu-id="0fe12-149">Modify the call to `Console.WriteLine` from the previous example to include the format specifier for the date and price fields as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```
    
<span data-ttu-id="0fe12-150">在插入運算式後面接著冒號和格式字串，即可指定格式字串。</span><span class="sxs-lookup"><span data-stu-id="0fe12-150">You specify a format string by following the interpolated expression with a colon and the format string.</span></span> <span data-ttu-id="0fe12-151">"d" 是[標準日期和時間格式字串](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier)，可呈現簡短日期格式。</span><span class="sxs-lookup"><span data-stu-id="0fe12-151">"d" is a [standard date and time format string](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="0fe12-152">"C2" 是[標準數值格式字串](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier)，可將數字呈現為小數點後面有兩位數的貨幣值。</span><span class="sxs-lookup"><span data-stu-id="0fe12-152">"C2" is a  [standard numeric format string](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="0fe12-153">.NET Standard 程式庫中有多種類型都支援一組預先定義的格式字串。</span><span class="sxs-lookup"><span data-stu-id="0fe12-153">A number of types in the .NET Standard libraries support a predefined set of format strings.</span></span> <span data-ttu-id="0fe12-154">其中包含所有數值類型以及日期和時間類型。</span><span class="sxs-lookup"><span data-stu-id="0fe12-154">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="0fe12-155">如需支援格式字串之類型的完整清單，請參閱[在 .NET 中格式化類型](../../standard/base-types/formatting-types.md)一文中的[格式字串和 .NET 類別庫類型](../../standard/base-types/formatting-types.md#stringRef)。</span><span class="sxs-lookup"><span data-stu-id="0fe12-155">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span> <span data-ttu-id="0fe12-156">任何類型都可以支援一組格式字串，而且您也可以開發自訂格式延伸模組，以提供現有類型的自訂格式。</span><span class="sxs-lookup"><span data-stu-id="0fe12-156">Any type can support a set of format strings, and you can also develop custom formatting extensions that provide custom formatting for existing types.</span></span> <span data-ttu-id="0fe12-157">如需透過提供 <xref:System.ICustomFormatter> 實作以自訂格式的資訊，請參閱[在 .NET 中格式化類型](../../standard/base-types/formatting-types.md)一文中的[使用 ICustomFormatter 的自訂格式](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter)。</span><span class="sxs-lookup"><span data-stu-id="0fe12-157">For information on custom formatting by providing an <xref:System.ICustomFormatter> implementation, see [Custom Formatting with ICustomFormatter](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="0fe12-158">嘗試在文字編輯器中修改格式字串，並在每次進行變更時，重新執行程式以查看變更對日期和時間以及數值格式的影響。</span><span class="sxs-lookup"><span data-stu-id="0fe12-158">Try modifying the the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="0fe12-159">將 `{date:d}` 中的 "d" 變更為 "t" (顯示簡短時間格式)、"y" (顯示年份和月份) 以及 "yyyy" (將年份顯示為四位數)。</span><span class="sxs-lookup"><span data-stu-id="0fe12-159">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="0fe12-160">將 `{price:C2}` 中的 "C2" 變更為 "e" (適用於指數標記法) 和 "F3" (適用於小數點後面有三位數的數值)。</span><span class="sxs-lookup"><span data-stu-id="0fe12-160">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="0fe12-161">除了控制格式之外，您也可以控制插入運算式所傳回字串的欄位寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="0fe12-161">In addition to controlling formatting, you can also control the field width and alignment of the strings returned by an interpolated expression.</span></span> <span data-ttu-id="0fe12-162">在下節中，您將學習如何執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="0fe12-162">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a><span data-ttu-id="0fe12-163">控制插入運算式的欄位寬度和對齊方式</span><span class="sxs-lookup"><span data-stu-id="0fe12-163">Control the field width and alignment of interpolated expressions</span></span>

<span data-ttu-id="0fe12-164">一般情況下，結果字串中包含插入運算式所傳回的字串時，不會有任何前置或尾端空格。</span><span class="sxs-lookup"><span data-stu-id="0fe12-164">Ordinarily, when the string returned by an interpolated expression is included in a result string, it has no leading or trailing spaces.</span></span> <span data-ttu-id="0fe12-165">特別是使用一組資料時，插入運算式可讓您指定欄位寬度和其對齊方式。</span><span class="sxs-lookup"><span data-stu-id="0fe12-165">Particularly for instances in which you are working with a set of data, interpolated expressions let you specify a field width and its alignment.</span></span> <span data-ttu-id="0fe12-166">若要確認這一點，請將文字編輯器中的所有程式碼都取代為下列程式碼，然後輸入 `console run` 以執行程式：</span><span class="sxs-lookup"><span data-stu-id="0fe12-166">To see this, replace all the code in your text editor with the following code, then type `console run` to execute the program:</span></span>
    
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
    
<span data-ttu-id="0fe12-167">作者名稱會靠左對齊，而他們所撰寫的標題會靠右對齊。</span><span class="sxs-lookup"><span data-stu-id="0fe12-167">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="0fe12-168">在運算式後面新增逗號 (",")，並指定欄位寬度，即可指定對齊方式。</span><span class="sxs-lookup"><span data-stu-id="0fe12-168">You specify the alignment by adding a comma (",") after the expression and designating the field width.</span></span> <span data-ttu-id="0fe12-169">如果欄位寬度是正數，則欄位會靠右對齊：</span><span class="sxs-lookup"><span data-stu-id="0fe12-169">If the field width is a positive number, the field is right-aligned:</span></span>

```text
{expression, width}
```

<span data-ttu-id="0fe12-170">如果欄位寬度是負數，則欄位會靠左對齊：</span><span class="sxs-lookup"><span data-stu-id="0fe12-170">If the field width is a negative number, the field is left-aligned:</span></span>

```text
{expression, -width}
```

<span data-ttu-id="0fe12-171">嘗試移除 `{"Author",-25}` 和 `{title.Key,-25}` 插入運算式中的負號，然後重新執行此範例，如下列程式碼所執行：</span><span class="sxs-lookup"><span data-stu-id="0fe12-171">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` interpolated expressions and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
foreach (var title in titles)
   Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
```

<span data-ttu-id="0fe12-172">目前，作者資訊會靠右對齊。</span><span class="sxs-lookup"><span data-stu-id="0fe12-172">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="0fe12-173">您可以將欄位寬度和格式字串結合到單一插入運算式。</span><span class="sxs-lookup"><span data-stu-id="0fe12-173">You can combine a field width and a format string in a single interpolated expression.</span></span> <span data-ttu-id="0fe12-174">先出現欄位寬度，後面接著冒號和格式字串。</span><span class="sxs-lookup"><span data-stu-id="0fe12-174">The field width comes first, followed by a colon and the format string.</span></span> <span data-ttu-id="0fe12-175">將 `Main` 方法內的所有程式碼都取代為下列程式碼，以顯示具有所定義欄位寬度的三個格式化字串。</span><span class="sxs-lookup"><span data-stu-id="0fe12-175">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="0fe12-176">然後輸入 `dotnet run` 命令，以執行程式。</span><span class="sxs-lookup"><span data-stu-id="0fe12-176">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"{DateTime.Now,-20:d} Hour {DateTime.Now,-10:HH} {1063.342,15:N2} feet");
```
<span data-ttu-id="0fe12-177">輸出會與下列內容類似：</span><span class="sxs-lookup"><span data-stu-id="0fe12-177">The output looks something like the following:</span></span>

```console
1/11/2018            Hour 09                1,063.34 feet
```

<span data-ttu-id="0fe12-178">您已完成插入字串快速入門。</span><span class="sxs-lookup"><span data-stu-id="0fe12-178">You've completed the interpolated strings quickstart.</span></span> 
    
<span data-ttu-id="0fe12-179">您可以在自己的開發環境中，繼續完成[陣列和集合](arrays-and-collections.md)快速入門中的內容。</span><span class="sxs-lookup"><span data-stu-id="0fe12-179">You can continue with the [Arrays and collections](arrays-and-collections.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="0fe12-180">您可以在＜C# 參考＞的[插入字串](../language-reference/keywords/interpolated-strings.md)主題中，深入了解如何使用插入字串。</span><span class="sxs-lookup"><span data-stu-id="0fe12-180">You can learn more about working with interpolated strings in the [Interpolated Strings](../language-reference/keywords/interpolated-strings.md) topic in the C# Reference.</span></span>

