---
title: ".NET 中的規則運算式"
description: ".NET 中的規則運算式"
keywords: ".NET、.NET Core"
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d1a640cf-09ca-48f7-800c-a627a6d549c9
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: ac26821819b22aa3ea47e6945bb5c8575dcd9807
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="regular-expressions-in-net"></a><span data-ttu-id="afa6c-104">.NET 中的規則運算式</span><span class="sxs-lookup"><span data-stu-id="afa6c-104">Regular expressions in .NET</span></span>

<span data-ttu-id="afa6c-105">規則運算式提供功能強大、彈性且有效率的方法來處理文字。</span><span class="sxs-lookup"><span data-stu-id="afa6c-105">Regular expressions provide a powerful, flexible, and efficient method for processing text.</span></span> <span data-ttu-id="afa6c-106">規則運算式的廣泛模式比對標記法可讓您快速剖析大量文字，以尋找特定的字元模式；驗證文字，以確保其符合預先定義的模式 (例如電子郵件地址)；擷取、編輯、取代或刪除文字子字串；以及將擷取的字串加入集合中，以產生報告。</span><span class="sxs-lookup"><span data-stu-id="afa6c-106">The extensive pattern-matching notation of regular expressions enables you to quickly parse large amounts of text to find specific character patterns; to validate text to ensure that it matches a predefined pattern (such as an e-mail address); to extract, edit, replace, or delete text substrings; and to add the extracted strings to a collection in order to generate a report.</span></span> <span data-ttu-id="afa6c-107">對許多處理字串或剖析大型文字區塊的應用程式而言，規則運算式是不可或缺的工具。</span><span class="sxs-lookup"><span data-stu-id="afa6c-107">For many applications that deal with strings or that parse large blocks of text, regular expressions are an indispensable tool.</span></span>

## <a name="how-regular-expressions-work"></a><span data-ttu-id="afa6c-108">規則運算式的運作方式</span><span class="sxs-lookup"><span data-stu-id="afa6c-108">How Regular Expressions Work</span></span>

<span data-ttu-id="afa6c-109">使用規則運算式來處理文字的核心是規則運算式引擎，以 .NET 中的 [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) 物件來表示。</span><span class="sxs-lookup"><span data-stu-id="afa6c-109">The centerpiece of text processing with regular expressions is the regular expression engine, which is represented by the [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) object in .NET.</span></span> <span data-ttu-id="afa6c-110">使用規則運算式來處理文字時，至少需要提供規則運算式引擎以及下列兩個資訊項目：</span><span class="sxs-lookup"><span data-stu-id="afa6c-110">At a minimum, processing text using regular expressions requires that the regular expression engine be provided with the following two items of information:</span></span>

* <span data-ttu-id="afa6c-111">要在文字中識別的規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="afa6c-111">The regular expression pattern to identify in the text.</span></span> 
  
  <span data-ttu-id="afa6c-112">在 .NET 中，規則運算式模式是以特殊的語法或語言來定義，其相容於 Perl 5 規則運算式，並新增一些其他功能，例如由右至左比對。</span><span class="sxs-lookup"><span data-stu-id="afa6c-112">In .NET, regular expression patterns are defined by a special syntax or language, which is compatible with Perl 5 regular expressions and adds some additional features such as right-to-left matching.</span></span> <span data-ttu-id="afa6c-113">如需詳細資訊，請參閱[規則運算式語言 - 快速參考](quick-ref.md)。</span><span class="sxs-lookup"><span data-stu-id="afa6c-113">For more information, see [Regular Expression Language - Quick Reference](quick-ref.md).</span></span>
  
* <span data-ttu-id="afa6c-114">要為規則運算式模式剖析的文字。</span><span class="sxs-lookup"><span data-stu-id="afa6c-114">The text to parse for the regular expression pattern.</span></span>

<span data-ttu-id="afa6c-115">[Regex](xref:System.Text.RegularExpressions.Regex) 類別的方法可讓您執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="afa6c-115">The methods of the [Regex](xref:System.Text.RegularExpressions.Regex) class let you perform the following operations:</span></span>

* <span data-ttu-id="afa6c-116">呼叫 [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) 方法，以判定規則運算式模式是否出現在輸入文字中。</span><span class="sxs-lookup"><span data-stu-id="afa6c-116">Determine whether the regular expression pattern occurs in the input text by calling the [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) method.</span></span> <span data-ttu-id="afa6c-117">如需使用 [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) 方法來驗證文字的範例，請參閱[如何：確認字串是否為有效的電子郵件格式](verify-format.md)。</span><span class="sxs-lookup"><span data-stu-id="afa6c-117">For an example that uses the [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) method for validating text, see [How to: Verify that Strings Are in Valid Email Format](verify-format.md).</span></span>

* <span data-ttu-id="afa6c-118">呼叫 [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) 或 [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) 方法，以擷取符合規則運算式模式的所有文字。</span><span class="sxs-lookup"><span data-stu-id="afa6c-118">Retrieve one or all occurrences of text that matches the regular expression pattern by calling the [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) or [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) method.</span></span> <span data-ttu-id="afa6c-119">前一個方法會傳回 [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) 物件，提供相符文字的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="afa6c-119">The former method returns a [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) object that provides information about the matching text.</span></span> <span data-ttu-id="afa6c-120">後者傳回 [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) 物件，其包含在每個已剖析文字中找到之相符項目的一個 [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) 物件。</span><span class="sxs-lookup"><span data-stu-id="afa6c-120">The latter returns a [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) object that contains one [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) object for each match found in the parsed text.</span></span> 

* <span data-ttu-id="afa6c-121">呼叫 [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) 方法，以取代符合規則運算式模式的文字。</span><span class="sxs-lookup"><span data-stu-id="afa6c-121">Replace text that matches the regular expression pattern by calling the [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) method.</span></span> <span data-ttu-id="afa6c-122">如需使用 [Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) 方法來變更日期格式，以及移除字串中無效字元的範例，請參閱[如何：從字串中刪除無效的字元](strip-characters.md)和[規則運算式範例：變更日期格式](changing-formats.md)。</span><span class="sxs-lookup"><span data-stu-id="afa6c-122">For examples that use the [Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) method to change date formats and remove invalid characters from a string, see [How to: Strip Invalid Characters from a String](strip-characters.md) and [Regular Expression Example: Changing Date Formats](changing-formats.md).</span></span>

<span data-ttu-id="afa6c-123">如需規則運算式物件模型概觀，請參閱[規則運算式物件模型](object-model.md)。</span><span class="sxs-lookup"><span data-stu-id="afa6c-123">For an overview of the regular expression object model, see [The Regular Expression Object Model](object-model.md).</span></span>

<span data-ttu-id="afa6c-124">如需規則運算式語言的詳細資訊，請參閱[規則運算式語言 - 快速參考](quick-ref.md)。</span><span class="sxs-lookup"><span data-stu-id="afa6c-124">For more information about the regular expression language, see [Regular Expression Language - Quick Reference](quick-ref.md).</span></span>

## <a name="regular-expression-examples"></a><span data-ttu-id="afa6c-125">規則運算式範例</span><span class="sxs-lookup"><span data-stu-id="afa6c-125">Regular Expression Examples</span></span>

<span data-ttu-id="afa6c-126">[String](xref:System.String) 類別包含數種字串搜尋和取代方法，可供您在大型字串中尋找常值字串時使用。</span><span class="sxs-lookup"><span data-stu-id="afa6c-126">The [String](xref:System.String) class includes a number of string search and replacement methods that you can use when you want to locate literal strings in a larger string.</span></span> <span data-ttu-id="afa6c-127">當您想要在大型字串中尋找數個子字串時，或是當您想要識別字串中的模式時，規則運算式最為好用，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="afa6c-127">Regular expressions are most useful either when you want to locate one of several substrings in a larger string, or when you want to identify patterns in a string, as the following examples illustrate.</span></span> 

### <a name="example-1-replacing-substrings"></a><span data-ttu-id="afa6c-128">範例 1：取代子字串</span><span class="sxs-lookup"><span data-stu-id="afa6c-128">Example 1: Replacing Substrings</span></span>

<span data-ttu-id="afa6c-129">假設郵寄清單包含的名稱有時候會包括稱謂 (Mr.、Mrs.、Miss 或 Ms.) 以及姓名。</span><span class="sxs-lookup"><span data-stu-id="afa6c-129">Assume that a mailing list contains names that sometimes include a title (Mr., Mrs., Miss, or Ms.) along with a first and last name.</span></span> <span data-ttu-id="afa6c-130">當您從清單產生信封標籤時，如果不想包括稱謂，就可以使用規則運算式來移除稱謂，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="afa6c-130">If you do not want to include the titles when you generate envelope labels from the list, you can use a regular expression to remove the titles, as the following example illustrates.</span></span>

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "(Mr\\.? |Mrs\\.? |Miss |Ms\\.? )";
      string[] names = { "Mr. Henry Hunt", "Ms. Sara Samuels", 
                         "Abraham Adams", "Ms. Nicole Norris" };
      foreach (string name in names)
         Console.WriteLine(Regex.Replace(name, pattern, String.Empty));
   }
}
// The example displays the following output:
//    Henry Hunt
//    Sara Samuels
//    Abraham Adams
//    Nicole Norris
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(Mr\.? |Mrs\.? |Miss |Ms\.? )"
      Dim names() As String = { "Mr. Henry Hunt", "Ms. Sara Samuels", _
                                "Abraham Adams", "Ms. Nicole Norris" }
      For Each name As String In names
         Console.WriteLine(Regex.Replace(name, pattern, String.Empty))
      Next                                
   End Sub
End Module
' The example displays the following output:
'    Henry Hunt
'    Sara Samuels
'    Abraham Adams
'    Nicole Norris
```

<span data-ttu-id="afa6c-131">規則運算式模式 `(Mr\.? |Mrs\.? |Miss |Ms\.? )` 會比對所出現的任何 "Mr "、"Mr. "、"Mrs "、"Mrs. "、"Miss "、"Ms 或 "Ms. "。</span><span class="sxs-lookup"><span data-stu-id="afa6c-131">The regular expression pattern `(Mr\.? |Mrs\.? |Miss |Ms\.? )` matches any occurrence of "Mr ", "Mr. ", "Mrs ", "Mrs. ", "Miss ", "Ms or "Ms. ".</span></span> <span data-ttu-id="afa6c-132">呼叫 [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) 方法會以 [String.Empty](xref:System.String.Empty) 取代相符的字串；換句話說，就是從原始字串中移除它。</span><span class="sxs-lookup"><span data-stu-id="afa6c-132">The call to the [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) method replaces the matched string with [String.Empty](xref:System.String.Empty); in other words, it removes it from the original string.</span></span>

### <a name="example-2-identifying-duplicated-words"></a><span data-ttu-id="afa6c-133">範例 2：識別重複的文字</span><span class="sxs-lookup"><span data-stu-id="afa6c-133">Example 2: Identifying Duplicated Words</span></span>

<span data-ttu-id="afa6c-134">不小心重複文字是作者常犯的錯誤。</span><span class="sxs-lookup"><span data-stu-id="afa6c-134">Accidentally duplicating words is a common error that writers make.</span></span> <span data-ttu-id="afa6c-135">規則運算式可用來識別重複的文字，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="afa6c-135">A regular expression can be used to identify duplicated words, as the following example shows.</span></span>

```csharp
using System;
using System.Text.RegularExpressions;

public class Class1
{
   public static void Main()
   {
      string pattern = @"\b(\w+?)\s\1\b";
      string input = "This this is a nice day. What about this? This tastes good. I saw a a dog.";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine("{0} (duplicates '{1}') at position {2}", 
                           match.Value, match.Groups[1].Value, match.Index);
   }
}
// The example displays the following output:
//       This this (duplicates 'This)' at position 0
//       a a (duplicates 'a)' at position 66
```

```vb
Imports System.Text.RegularExpressions

Module modMain
   Public Sub Main()
      Dim pattern As String = "\b(\w+?)\s\1\b"
      Dim input As String = "This this is a nice day. What about this? This tastes good. I saw a a dog."
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine("{0} (duplicates '{1}') at position {2}", _
                           match.Value, match.Groups(1).Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       This this (duplicates 'This)' at position 0
'       a a (duplicates 'a)' at position 66
```

<span data-ttu-id="afa6c-136">規則運算式模式 `\b(\w+?)\s\1\b` 可解譯如下：</span><span class="sxs-lookup"><span data-stu-id="afa6c-136">The regular expression pattern `\b(\w+?)\s\1\b` can be interpreted as follows:</span></span>

<span data-ttu-id="afa6c-137">語法</span><span class="sxs-lookup"><span data-stu-id="afa6c-137">Syntax</span></span> | <span data-ttu-id="afa6c-138">意義</span><span class="sxs-lookup"><span data-stu-id="afa6c-138">Meaning</span></span>
------ | -------
`\b` | <span data-ttu-id="afa6c-139">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="afa6c-139">Start at a word boundary.</span></span>
`(\w+?)` | <span data-ttu-id="afa6c-140">比對一或多個字元，但字元數愈少愈好。</span><span class="sxs-lookup"><span data-stu-id="afa6c-140">Match one or more word characters, but as few characters as possible.</span></span> <span data-ttu-id="afa6c-141">這些一起構成可稱之為 `\1` 的群組。</span><span class="sxs-lookup"><span data-stu-id="afa6c-141">Together, they form a group that can be referred to as `\1`.</span></span>
`\s` | <span data-ttu-id="afa6c-142">比對空白字元。</span><span class="sxs-lookup"><span data-stu-id="afa6c-142">Match a white-space character.</span></span>
`\1` | <span data-ttu-id="afa6c-143">比對等同於名為 `\1` 之群組的子字串。</span><span class="sxs-lookup"><span data-stu-id="afa6c-143">Match the substring that is equal to the group named `\1`.</span></span>
`\b` | <span data-ttu-id="afa6c-144">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="afa6c-144">Match a word boundary.</span></span>

<span data-ttu-id="afa6c-145">[Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) 方法是以設為 [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) 的規則運算式選項呼叫。</span><span class="sxs-lookup"><span data-stu-id="afa6c-145">The [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) method is called with regular expression options set to [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase).</span></span> <span data-ttu-id="afa6c-146">因此，比對作業不區分大小寫，而且此範例會將子字串 "This this" 視為重複。</span><span class="sxs-lookup"><span data-stu-id="afa6c-146">Therefore, the match operation is case-insensitive, and the example identifies the substring "This this" as a duplication.</span></span>

<span data-ttu-id="afa6c-147">請注意，輸入字串包括子字串 "this?</span><span class="sxs-lookup"><span data-stu-id="afa6c-147">Note that the input string includes the substring "this?</span></span> <span data-ttu-id="afa6c-148">This"。</span><span class="sxs-lookup"><span data-stu-id="afa6c-148">This".</span></span> <span data-ttu-id="afa6c-149">不過，因為中間有標點符號，所以不會將其視為重複。</span><span class="sxs-lookup"><span data-stu-id="afa6c-149">However, because of the intervening punctuation mark, it is not identified as a duplication.</span></span>

### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a><span data-ttu-id="afa6c-150">範例 3：動態建立區分文化特性的規則運算式</span><span class="sxs-lookup"><span data-stu-id="afa6c-150">Example 3: Dynamically Building a Culture-Sensitive Regular Expression</span></span>

<span data-ttu-id="afa6c-151">下列範例說明規則運算式結合 .NET 全球化功能所提供的彈性，功能有多麼強大。</span><span class="sxs-lookup"><span data-stu-id="afa6c-151">The following example illustrates the power of regular expressions combined with the flexibility offered by .NET's globalization features.</span></span> <span data-ttu-id="afa6c-152">它會使用 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件來判定系統目前文化特性中的幣值格式，</span><span class="sxs-lookup"><span data-stu-id="afa6c-152">It uses the [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object to determine the format of currency values in the system's current culture.</span></span> <span data-ttu-id="afa6c-153">然後利用該資訊動態建構可從文字擷取幣值的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="afa6c-153">It then uses that information to dynamically construct a regular expression that extracts currency values from the text.</span></span> <span data-ttu-id="afa6c-154">針對每個比對，它會擷取僅包含數值字串的子群組，將其轉換成[十進位](xref:System.Decimal)值，並計算執行總計。</span><span class="sxs-lookup"><span data-stu-id="afa6c-154">For each match, it extracts the subgroup that contains the numeric string only, converts it to a [Decimal](xref:System.Decimal) value, and calculates a running total.</span></span> 

```csharp
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      // Define text to be parsed.
      string input = "Office expenses on 2/13/2008:\n" + 
                     "Paper (500 sheets)                      $3.95\n" + 
                     "Pencils (box of 10)                     $1.00\n" + 
                     "Pens (box of 10)                        $4.49\n" + 
                     "Erasers                                 $2.19\n" + 
                     "Ink jet printer                        $69.95\n\n" + 
                     "Total Expenses                        $ 81.58\n"; 

      // Get current culture's NumberFormatInfo object.
      NumberFormatInfo nfi = CultureInfo.CurrentCulture.NumberFormat;
      // Assign needed property values to variables.
      string currencySymbol = nfi.CurrencySymbol;
      bool symbolPrecedesIfPositive = nfi.CurrencyPositivePattern % 2 == 0;
      string groupSeparator = nfi.CurrencyGroupSeparator;
      string decimalSeparator = nfi.CurrencyDecimalSeparator;

      // Form regular expression pattern.
      string pattern = Regex.Escape( symbolPrecedesIfPositive ? currencySymbol : "") + 
                       @"\s*[-+]?" + "([0-9]{0,3}(" + groupSeparator + "[0-9]{3})*(" + 
                       Regex.Escape(decimalSeparator) + "[0-9]+)?)" + 
                       (! symbolPrecedesIfPositive ? currencySymbol : ""); 
      Console.WriteLine( "The regular expression pattern is:");
      Console.WriteLine("   " + pattern);      

      // Get text that matches regular expression pattern.
      MatchCollection matches = Regex.Matches(input, pattern, 
                                              RegexOptions.IgnorePatternWhitespace);               
      Console.WriteLine("Found {0} matches.", matches.Count); 

      // Get numeric string, convert it to a value, and add it to List object.
      List<decimal> expenses = new List<Decimal>();

      foreach (Match match in matches)
         expenses.Add(Decimal.Parse(match.Groups[1].Value));      

      // Determine whether total is present and if present, whether it is correct.
      decimal total = 0;
      foreach (decimal value in expenses)
         total += value;

      if (total / 2 == expenses[expenses.Count - 1]) 
         Console.WriteLine("The expenses total {0:C2}.", expenses[expenses.Count - 1]);
      else
         Console.WriteLine("The expenses total {0:C2}.", total);
   }  
}
// The example displays the following output:
//       The regular expression pattern is:
//          \$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)
//       Found 6 matches.
//       The expenses total $81.58.
```

```vb
Imports System.Collections.Generic
Imports System.Globalization
Imports System.Text.RegularExpressions

Public Module Example
   Public Sub Main()
      ' Define text to be parsed.
      Dim input As String = "Office expenses on 2/13/2008:" + vbCrLf + _
                            "Paper (500 sheets)                      $3.95" + vbCrLf + _
                            "Pencils (box of 10)                     $1.00" + vbCrLf + _
                            "Pens (box of 10)                        $4.49" + vbCrLf + _
                            "Erasers                                 $2.19" + vbCrLf + _
                            "Ink jet printer                        $69.95" + vbCrLf + vbCrLf + _
                            "Total Expenses                        $ 81.58" + vbCrLf
      ' Get current culture's NumberFormatInfo object.
      Dim nfi As NumberFormatInfo = CultureInfo.CurrentCulture.NumberFormat
      ' Assign needed property values to variables.
      Dim currencySymbol As String = nfi.CurrencySymbol
      Dim symbolPrecedesIfPositive As Boolean = CBool(nfi.CurrencyPositivePattern Mod 2 = 0)
      Dim groupSeparator As String = nfi.CurrencyGroupSeparator
      Dim decimalSeparator As String = nfi.CurrencyDecimalSeparator

      ' Form regular expression pattern.
      Dim pattern As String = Regex.Escape(CStr(IIf(symbolPrecedesIfPositive, currencySymbol, ""))) + _
                              "\s*[-+]?" + "([0-9]{0,3}(" + groupSeparator + "[0-9]{3})*(" + _
                              Regex.Escape(decimalSeparator) + "[0-9]+)?)" + _
                              CStr(IIf(Not symbolPrecedesIfPositive, currencySymbol, "")) 
      Console.WriteLine("The regular expression pattern is: ")
      Console.WriteLine("   " + pattern)      

      ' Get text that matches regular expression pattern.
      Dim matches As MatchCollection = Regex.Matches(input, pattern, RegexOptions.IgnorePatternWhitespace)               
      Console.WriteLine("Found {0} matches. ", matches.Count)

      ' Get numeric string, convert it to a value, and add it to List object.
      Dim expenses As New List(Of Decimal)

      For Each match As Match In matches
         expenses.Add(Decimal.Parse(match.Groups.Item(1).Value))      
      Next

      ' Determine whether total is present and if present, whether it is correct.
      Dim total As Decimal
      For Each value As Decimal In expenses
         total += value
      Next

      If total / 2 = expenses(expenses.Count - 1) Then
         Console.WriteLine("The expenses total {0:C2}.", expenses(expenses.Count - 1))
      Else
         Console.WriteLine("The expenses total {0:C2}.", total)
      End If   
   End Sub
End Module
' The example displays the following output:
'       The regular expression pattern is:
'          \$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)
'       Found 6 matches.
'       The expenses total $81.58.
```

<span data-ttu-id="afa6c-155">在目前文化特性為 English - United States (en-US) 的電腦上，此範例會動態建立規則運算式 `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`。</span><span class="sxs-lookup"><span data-stu-id="afa6c-155">On a computer whose current culture is English - United States (en-US), the example dynamically builds the regular expression `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`.</span></span> <span data-ttu-id="afa6c-156">此規則運算式模式可解譯如下：</span><span class="sxs-lookup"><span data-stu-id="afa6c-156">This regular expression pattern can be interpreted as follows:</span></span>

<span data-ttu-id="afa6c-157">語法</span><span class="sxs-lookup"><span data-stu-id="afa6c-157">Syntax</span></span> | <span data-ttu-id="afa6c-158">意義</span><span class="sxs-lookup"><span data-stu-id="afa6c-158">Meaning</span></span>
------ | -------
`\$` | <span data-ttu-id="afa6c-159">在輸入字串中尋找單獨出現的貨幣符號 ($)。</span><span class="sxs-lookup"><span data-stu-id="afa6c-159">Look for a single occurrence of the dollar symbol ($) in the input string.</span></span> <span data-ttu-id="afa6c-160">規則運算式模式字串包含反斜線，表示貨幣符號要解譯為字面意義，而不是規則運算式錨點。</span><span class="sxs-lookup"><span data-stu-id="afa6c-160">The regular expression pattern string includes a backslash to indicate that the dollar symbol is to be interpreted literally rather than as a regular expression anchor.</span></span> <span data-ttu-id="afa6c-161">($ 符號單獨出現表示規則運算式引擎應該嘗試在字串結尾處開始其比對。)為了確保目前文化特性的貨幣符號不會誤譯為規則運算式符號，此範例呼叫 [Escape](xref:System.Text.RegularExpressions.Regex.Escape(System.String)) 方法以逸出字元。</span><span class="sxs-lookup"><span data-stu-id="afa6c-161">(The $ symbol alone would indicate that the regular expression engine should try to begin its match at the end of a string.) To ensure that the current culture's currency symbol is not misinterpreted as a regular expression symbol, the example calls the [Escape](xref:System.Text.RegularExpressions.Regex.Escape(System.String)) method to escape the character.</span></span>
`\s*` | <span data-ttu-id="afa6c-162">尋找出現零或多次的空格字元。</span><span class="sxs-lookup"><span data-stu-id="afa6c-162">Look for zero or more occurrences of a white-space character.</span></span>
`[-+]?` | <span data-ttu-id="afa6c-163">尋找出現一或多次的正號或負號。</span><span class="sxs-lookup"><span data-stu-id="afa6c-163">Look for zero or one occurrence of either a positive sign or a negative sign.</span></span>
`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)` | <span data-ttu-id="afa6c-164">此運算式外面括號將其定義成擷取群組或子運算式。</span><span class="sxs-lookup"><span data-stu-id="afa6c-164">The outer parentheses around this expression define it as a capturing group or a subexpression.</span></span> <span data-ttu-id="afa6c-165">如果找到相符項目，從 [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) 屬性傳回之 [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 物件中的第二個 [Group](xref:System.Text.RegularExpressions.Group) 物件，擷取此部分比對字串的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="afa6c-165">If a match is found, information about this part of the matching string can be retrieved from the second [Group](xref:System.Text.RegularExpressions.Group) object in the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) object returned by the [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) property.</span></span> <span data-ttu-id="afa6c-166">(集合中的第一個項目代表整個比對。)</span><span class="sxs-lookup"><span data-stu-id="afa6c-166">(The first element in the collection represents the entire match.)</span></span>
`[0-9]{0,3}` | <span data-ttu-id="afa6c-167">尋找出現零到三次的十進位數字 0 到 9。</span><span class="sxs-lookup"><span data-stu-id="afa6c-167">Look for zero to three occurrences of the decimal digits 0 through 9.</span></span>
`(,[0-9]{3})*` | <span data-ttu-id="afa6c-168">尋找出現零或多次、後面接三個十進位數字的群組分隔符號。</span><span class="sxs-lookup"><span data-stu-id="afa6c-168">Look for zero or more occurrences of a group separator followed by three decimal digits.</span></span>
`\.` | <span data-ttu-id="afa6c-169">尋找單次出現的十進位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="afa6c-169">Look for a single occurrence of the decimal separator.</span></span>
`[0-9]+` | <span data-ttu-id="afa6c-170">尋找一或多個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="afa6c-170">Look for one or more decimal digits.</span></span>
`(\.[0-9]+)?` | <span data-ttu-id="afa6c-171">尋找出現零或一次、後接至少一個十進位數字的十進位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="afa6c-171">Look for zero or one occurrence of the decimal separator followed by at least one decimal digit.</span></span>

## <a name="related-topics"></a><span data-ttu-id="afa6c-172">相關主題</span><span class="sxs-lookup"><span data-stu-id="afa6c-172">Related Topics</span></span>

<span data-ttu-id="afa6c-173">標題</span><span class="sxs-lookup"><span data-stu-id="afa6c-173">Title</span></span> | <span data-ttu-id="afa6c-174">說明</span><span class="sxs-lookup"><span data-stu-id="afa6c-174">Description</span></span>
----- | -----------
[<span data-ttu-id="afa6c-175">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="afa6c-175">Regular expression language - quick reference</span></span>](quick-ref.md) | <span data-ttu-id="afa6c-176">提供您可以用來定義規則運算式之字元、運算子和建構組合的資訊。</span><span class="sxs-lookup"><span data-stu-id="afa6c-176">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
[<span data-ttu-id="afa6c-177">規則運算式物件模型</span><span class="sxs-lookup"><span data-stu-id="afa6c-177">The regular expression object model</span></span>](object-model.md) | <span data-ttu-id="afa6c-178">提供資訊和程式碼範例，說明如何使用規則運算式類別。</span><span class="sxs-lookup"><span data-stu-id="afa6c-178">Provides information and code examples that illustrate how to use the regular expression classes.</span></span>
[<span data-ttu-id="afa6c-179">規則運算式行為的詳細資料</span><span class="sxs-lookup"><span data-stu-id="afa6c-179">Details of regular expression behavior</span></span>](regex-behavior.md) | <span data-ttu-id="afa6c-180">提供 .NET 規則運算式之功能和行為的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="afa6c-180">Provides information about the capabilities and behavior of .NETregular expressions.</span></span>
[<span data-ttu-id="afa6c-181">規則運算式範例</span><span class="sxs-lookup"><span data-stu-id="afa6c-181">Regular expression examples</span></span>](regex-examples.md) | <span data-ttu-id="afa6c-182">提供程式碼範例，以說明規則運算式的一般用法。</span><span class="sxs-lookup"><span data-stu-id="afa6c-182">Provides code examples that illustrate typical uses of regular expressions.</span></span>


## <a name="reference"></a><span data-ttu-id="afa6c-183">參考資料</span><span class="sxs-lookup"><span data-stu-id="afa6c-183">Reference</span></span>

[<span data-ttu-id="afa6c-184">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="afa6c-184">System.Text.RegularExpressions</span></span>](xref:System.Text.RegularExpressions)

[<span data-ttu-id="afa6c-185">System.Text.RegularExpressions.Regex</span><span class="sxs-lookup"><span data-stu-id="afa6c-185">System.Text.RegularExpressions.Regex</span></span>](xref:System.Text.RegularExpressions.Regex)


