---
title: 字串插補教學課程 - C# 本機快速入門
description: 本快速入門示範如何使用 C# 字串插補功能，在較大字串中包含格式化運算式結果。
author: rpetrusha
ms.author: ronpet
ms.date: 04/14/2018
ms.custom: mvc
ms.openlocfilehash: 314626e276f50178e2855b8c8a1edc104546d574
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="string-interpolation"></a><span data-ttu-id="ec5cb-103">字串插補</span><span class="sxs-lookup"><span data-stu-id="ec5cb-103">String interpolation</span></span>

<span data-ttu-id="ec5cb-104">本快速入門教導您如何使用 C# [字串插補](../language-reference/tokens/interpolated.md)，在單一結果字串中插入值。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-104">This quickstart teaches you how to use C# [string interpolation](../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="ec5cb-105">您將會撰寫 C# 程式碼，並查看程式碼編譯和執行的結果。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="ec5cb-106">本快速入門包含一系列的課程，示範如何將值插入至字串，並以不同的方式設定那些值的格式。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-106">The quickstart contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="ec5cb-107">本快速入門需要您具備可用於開發的電腦。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-107">This quickstart expects that you have a machine you can use for development.</span></span> <span data-ttu-id="ec5cb-108">.NET 主題[只要 10 分鐘立即上手](https://www.microsoft.com/net/core) \(英文\) 中有關於在 Mac、PC 或 Linux 上設定本機開發環境的指示。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="ec5cb-109">您可以在[本機快速入門簡介](local-environment.md)中快速檢視將會用到的命令，並取得可提供詳細資料的連結。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-109">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span> <span data-ttu-id="ec5cb-110">您也可以在瀏覽器中完成本快速入門的[互動式版本](interpolated-strings.yml)。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-110">You also can complete the [interactive version](interpolated-strings.yml) of this quickstart in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="ec5cb-111">建立插入字串</span><span class="sxs-lookup"><span data-stu-id="ec5cb-111">Create an interpolated string</span></span>

<span data-ttu-id="ec5cb-112">建立名為 **interpolated** 的目錄。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-112">Create a directory named **interpolated**.</span></span> <span data-ttu-id="ec5cb-113">讓它成為目前目錄，並從主控台視窗中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="ec5cb-113">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console
```

<span data-ttu-id="ec5cb-114">此命令會在目前的目錄中建立新的 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="ec5cb-115">在您最愛的編輯器中開啟 **Program.cs**，並將 `Console.WriteLine("Hello World!");` 行取代為下列程式碼；其中，您可以將 `<name>` 取代為您的名稱：</span><span class="sxs-lookup"><span data-stu-id="ec5cb-115">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="ec5cb-116">在主控台視窗中鍵入 `dotnet run` 來嘗試此程式碼。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="ec5cb-117">當您執行程式時，它會顯示問候語中包含您名稱的單一字串。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-117">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="ec5cb-118"><xref:System.Console.WriteLine%2A> 方法呼叫中所含的字串是「插入字串」。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-118">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string*.</span></span> <span data-ttu-id="ec5cb-119">它是一種範本，可讓您從包含內嵌程式碼的字串建構單一字串 (稱為「結果字串」)。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-119">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="ec5cb-120">插入字串特別適用於將值插入至字串或將字串串連 (聯結在一起)。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-120">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="ec5cb-121">這個簡單範例包含每個插入字串都必須要有的兩個項目：</span><span class="sxs-lookup"><span data-stu-id="ec5cb-121">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="ec5cb-122">左引號字元之前開頭為 `$` 字元的字串常值。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-122">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="ec5cb-123">`$` 符號與引號字元之間不能有任何空格。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-123">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="ec5cb-124">(如果您想要查看包含空格時會發生什麼情況，請在 `$` 字元後面插入空格、儲存檔案，然後在主控台視窗中鍵入 `dotnet run` 以重新執行程式。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-124">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="ec5cb-125">C# 編譯器會顯示錯誤訊息「錯誤 CS1056: 未預期的字元 '$'」)。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-125">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="ec5cb-126">一或多個「插入運算式」。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-126">One or more *interpolated expressions*.</span></span> <span data-ttu-id="ec5cb-127">插入運算式是以左右大括號 (`{` 和 `}`) 指出。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-127">An interpolated expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="ec5cb-128">您可以放置任何 C# 運算式，以傳回大括號內的值 (包含 `null`)。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-128">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="ec5cb-129">嘗試更多包含一些其他資料類型的字串插補範例。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-129">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="ec5cb-130">包含不同的資料類型</span><span class="sxs-lookup"><span data-stu-id="ec5cb-130">Include different data types</span></span>

<span data-ttu-id="ec5cb-131">在上節中，您使用字串插補將某個字串插入至另一個字串內部。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-131">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="ec5cb-132">不過，插入運算式的結果可以是任意資料類型。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-132">The result of an interpolated expression can be of any data type, though.</span></span> <span data-ttu-id="ec5cb-133">請包含插入字串中各種資料類型的值。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-133">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="ec5cb-134">在下列範例中，首先，我們定義具有 `Name` [屬性](../properties.md) 和 `ToString` 方法的自訂資料類型 `Vegetable`。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-134">In the following example, first, we define a custom data type `Vegetable` that has the `Name` [property](../properties.md) and the `ToString` method.</span></span> <span data-ttu-id="ec5cb-135">用戶端程式碼可以使用該方法取得 `Vegetable` 執行個體的字串表示。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-135">The client code can use that method to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="ec5cb-136">在範例中，`Vegetable.ToString` 方法傳回 `Name` 屬性的值，而此屬性是在 `Vegetable` 建構函式初始化：</span><span class="sxs-lookup"><span data-stu-id="ec5cb-136">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` constructor:</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="ec5cb-137">我們使用 `new` 關鍵字並提供 `Vegetable` 建構函式的 name 參數，來建立 `Vegetable` 型別執行個體：</span><span class="sxs-lookup"><span data-stu-id="ec5cb-137">We create an instance of the `Vegetable` type by using `new` keyword and providing a name parameter for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="ec5cb-138">最後，我們將 `item` 變數併入插入字串，而此插入字串也包含 <xref:System.DateTime> 值、<xref:System.Decimal> 值和 `Unit` [enumeration](../programming-guide/enumeration-types.md) 值。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-138">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../programming-guide/enumeration-types.md) value.</span></span> <span data-ttu-id="ec5cb-139">將編輯器中的所有 C# 程式碼都取代為下列程式碼，然後使用 `dotnet run` 命令來執行此程式碼：</span><span class="sxs-lookup"><span data-stu-id="ec5cb-139">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

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

<span data-ttu-id="ec5cb-140">請注意，插入字串中的插入運算式 `item` 會解析為結果字串中的文字 "eggplant"。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-140">Note that the interpolated expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="ec5cb-141">原因是，運算式結果的型別不是字串時，會使用下列方式將結果解析為字串：</span><span class="sxs-lookup"><span data-stu-id="ec5cb-141">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="ec5cb-142">如果插入運算式評估為 `null`，則會使用空字串 (""，或 <xref:System.String.Empty?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-142">If the interpolated expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="ec5cb-143">如果插入運算式未評估為 `null`，一般會呼叫結果類型的 `ToString` 方法。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-143">If the interpolated expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="ec5cb-144">測試這項作業的方式是更新 `Vegetable.ToString` 方法的實作。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-144">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="ec5cb-145">您甚至可能未實作 `ToString` 方法，因為每種 C# 資料類型都有這個方法的某種實作。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-145">You might even not implement `ToString` method since every C# data type has some implementation of this method.</span></span> <span data-ttu-id="ec5cb-146">若要測試該作業，請註銷範例中 `Vegetable.ToString` 方法的定義 (作法是在其前面放置註解符號 (`//`)。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-146">To test that, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol `//` in front of it).</span></span> <span data-ttu-id="ec5cb-147">在輸出中，字串 "eggplant" 會取代為完整類型名稱 (在此範例中，為 "Vegetable")，這是 <xref:System.Object.ToString?displayProperty=nameWithType> 方法的預設行為。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-147">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ec5cb-148">列舉型別之 `ToString` 方法的預設行為是傳回定義列舉時所使用值的字串表示。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-148">Default behavior of the `ToString` method for an enumeration type is to return the string representation of a value used at the definition of the enumeration.</span></span>

<span data-ttu-id="ec5cb-149">在此範例的輸出中，日期太過精確 (eggplant 價格不會因第二個而變更)，而價格值未指出貨幣單位。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-149">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="ec5cb-150">在下節中，您將學習如何控制運算式結果的字串表示格式來修正這些問題。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-150">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolated-expressions"></a><span data-ttu-id="ec5cb-151">控制插入運算式的格式</span><span class="sxs-lookup"><span data-stu-id="ec5cb-151">Control the formatting of interpolated expressions</span></span>

<span data-ttu-id="ec5cb-152">在上節中，已將兩個格式不佳的字串插入至結果字串。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-152">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="ec5cb-153">其中一個是只有日期才適合的日期和時間值。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-153">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="ec5cb-154">第二個是未指出其貨幣單位的價格。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-154">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="ec5cb-155">這兩個問題都很容易解決。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-155">Both issues are easy to address.</span></span> <span data-ttu-id="ec5cb-156">字串插補可讓您指定「格式字串」，以控制特定類型的格式。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-156">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="ec5cb-157">修改前一個範例中的 `Console.WriteLine` 呼叫，使其包含日期和價格運算式的格式字串，如下行所示：</span><span class="sxs-lookup"><span data-stu-id="ec5cb-157">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="ec5cb-158">在插入運算式後面接著冒號 (":") 和格式字串，即可指定格式字串。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-158">You specify a format string by following the interpolated expression with a colon (":") and the format string.</span></span> <span data-ttu-id="ec5cb-159">"d" 是[標準日期和時間格式字串](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier)，可呈現簡短日期格式。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-159">"d" is a [standard date and time format string](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="ec5cb-160">"C2" 是[標準數值格式字串](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier)，可將數字呈現為小數點後面有兩位數的貨幣值。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-160">"C2" is a  [standard numeric format string](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="ec5cb-161">.NET 程式庫中有多種類型都支援一組預先定義的格式字串。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-161">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="ec5cb-162">其中包含所有數值類型以及日期和時間類型。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-162">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="ec5cb-163">如需支援格式字串之類型的完整清單，請參閱[在 .NET 中格式化類型](../../standard/base-types/formatting-types.md)一文中的[格式字串和 .NET 類別庫類型](../../standard/base-types/formatting-types.md#stringRef)。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-163">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="ec5cb-164">嘗試在文字編輯器中修改格式字串，並在每次進行變更時，重新執行程式以查看變更對日期和時間以及數值格式的影響。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-164">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="ec5cb-165">將 `{date:d}` 中的 "d" 變更為 "t" (顯示簡短時間格式)、"y" (顯示年份和月份) 以及 "yyyy" (將年份顯示為四位數)。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-165">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="ec5cb-166">將 `{price:C2}` 中的 "C2" 變更為 "e" (適用於指數標記法) 和 "F3" (適用於小數點後面有三位數的數值)。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-166">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="ec5cb-167">除了控制格式之外，您也可以控制結果字串中所含格式化字串的欄位寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-167">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="ec5cb-168">在下節中，您將學習如何執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-168">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a><span data-ttu-id="ec5cb-169">控制插入運算式的欄位寬度和對齊方式</span><span class="sxs-lookup"><span data-stu-id="ec5cb-169">Control the field width and alignment of interpolated expressions</span></span>

<span data-ttu-id="ec5cb-170">一般情況下，插入運算式的結果格式化為字串時，結果字串中會包含該字串，而且沒有前置或尾端空格。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-170">Ordinarily, when the result of an interpolated expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="ec5cb-171">特別是當您使用一組資料時，可控制欄位寬度和文字對齊方式有助於產生更容易讀取的輸出。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-171">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="ec5cb-172">若要確認這一點，請將文字編輯器中的所有程式碼都取代為下列程式碼，然後鍵入 `dotnet run` 以執行程式：</span><span class="sxs-lookup"><span data-stu-id="ec5cb-172">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

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

<span data-ttu-id="ec5cb-173">作者名稱會靠左對齊，而他們所撰寫的標題會靠右對齊。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-173">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="ec5cb-174">在插入運算式後面新增逗號 (",")，並指定「最小」欄位寬度，即可指定對齊方式。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-174">You specify the alignment by adding a comma (",") after an interpolated expression and designating the *minimum* field width.</span></span> <span data-ttu-id="ec5cb-175">如果指定的值是正數，則欄位會靠右對齊。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-175">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="ec5cb-176">如果它是負數，則欄位會靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-176">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="ec5cb-177">嘗試移除 `{"Author",-25}` 和 `{title.Key,-25}` 程式碼中的負號，然後重新執行此範例，如下列程式碼所執行：</span><span class="sxs-lookup"><span data-stu-id="ec5cb-177">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="ec5cb-178">目前，作者資訊會靠右對齊。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-178">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="ec5cb-179">您可以將對齊規範與格式字串結合為單一插入運算式。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-179">You can combine an alignment specifier and a format string for a single interpolated expression.</span></span> <span data-ttu-id="ec5cb-180">若要這樣做，請先指定對齊方式，而且後面接著冒號和格式字串。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-180">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="ec5cb-181">將 `Main` 方法內的所有程式碼都取代為下列程式碼，以顯示具有所定義欄位寬度的三個格式化字串。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-181">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="ec5cb-182">然後輸入 `dotnet run` 命令，以執行程式。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-182">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="ec5cb-183">輸出會與下列內容類似：</span><span class="sxs-lookup"><span data-stu-id="ec5cb-183">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="ec5cb-184">您已完成字串插補快速入門。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-184">You've completed the string interpolation quickstart.</span></span>

<span data-ttu-id="ec5cb-185">您可以在自己的開發環境中，繼續完成[清單集合](arrays-and-collections.md)快速入門中的內容。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-185">You can continue with the [List collection](arrays-and-collections.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="ec5cb-186">如需詳細資訊，請參閱[字串插補](../language-reference/tokens/interpolated.md)主題和 [C# 中的字串插補](../tutorials/string-interpolation.md)教學課程。</span><span class="sxs-lookup"><span data-stu-id="ec5cb-186">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>
