---
title: "在 .NET 中剖析數值字串"
description: "在 .NET 中剖析數值字串"
keywords: ".NET、.NET Core"
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e393430a-731a-49fa-83de-ff7ed52d5704
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 85cd57d33b03f7a2105ee3f770b2f8bcc0a57ee4
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="parsing-numeric-strings-in-net"></a><span data-ttu-id="8be6f-104">在 .NET 中剖析數值字串</span><span class="sxs-lookup"><span data-stu-id="8be6f-104">Parsing numeric strings in .NET</span></span>

<span data-ttu-id="8be6f-105">所有數值類型皆有兩個靜態剖析方法：`Parse` 和 `TryParse`，可將數字的字串表示轉換成數值類型。</span><span class="sxs-lookup"><span data-stu-id="8be6f-105">All numeric types have two static parsing methods, `Parse` and `TryParse`, that you can use to convert the string representation of a number into a numeric type.</span></span> <span data-ttu-id="8be6f-106">這些方法可讓您剖析使用[標準數值格式字串](standard-numeric.md)和[自訂數值格式字串](custom-numeric.md)中記錄的格式字串所產生的字串。</span><span class="sxs-lookup"><span data-stu-id="8be6f-106">These methods enable you to parse strings that were produced by using the format strings documented in [Standard Numeric Format Strings](standard-numeric.md) and [Custom Numeric Format Strings](custom-numeric.md).</span></span> <span data-ttu-id="8be6f-107">根據預設，`Parse` 和 `TryParse` 方法只能將包含十進位數字的字串成功轉換為整數值。</span><span class="sxs-lookup"><span data-stu-id="8be6f-107">By default, the `Parse` and `TryParse` methods can successfully convert strings that contain integral decimal digits only to integer values.</span></span> <span data-ttu-id="8be6f-108">它們可以將包含整數和小數的十進位數字、群組分隔符號，以及小數分隔符號的字串，成功轉換為浮點值。</span><span class="sxs-lookup"><span data-stu-id="8be6f-108">They can successfully convert strings that contain integral and fractional decimal digits, group separators, and a decimal separator to floating-point values.</span></span> <span data-ttu-id="8be6f-109">如果作業失敗，即 `TryParse` 方法傳回 `false`，則 `Parse` 方法會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8be6f-109">The `Parse` method throws an exception if the operation fails, whereas the `TryParse` method returns `false`.</span></span>

## <a name="parsing-and-format-providers"></a><span data-ttu-id="8be6f-110">剖析及格式提供者</span><span class="sxs-lookup"><span data-stu-id="8be6f-110">Parsing and format providers</span></span>

<span data-ttu-id="8be6f-111">數值的字串表示通常會隨文化特性而不同。</span><span class="sxs-lookup"><span data-stu-id="8be6f-111">Typically, the string representations of numeric values differ by culture.</span></span> <span data-ttu-id="8be6f-112">數值字串的元素都會因文化特性而有所不同，包括貨幣符號、群組 (或千分位) 分隔符號以及小數分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8be6f-112">Elements of numeric strings such as currency symbols, group (or thousands) separators, and decimal separators all vary by culture.</span></span> <span data-ttu-id="8be6f-113">剖析方法會隱含或明確使用能夠辨識這些特定文化特性變化的格式提供者。</span><span class="sxs-lookup"><span data-stu-id="8be6f-113">Parsing methods either implicitly or explicitly use a format provider that recognizes these culture-specific variations.</span></span> <span data-ttu-id="8be6f-114">如果在 `Parse` 或 `TryParse` 方法的叫中不指定格式提供者，則會使用與目前執行緒文化特性相關聯的格式提供者 ([NumberFormatInfo.CurrentInfo](xref:System.Globalization.NumberFormatInfo.CurrentInfo) 屬性所傳回的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件)。</span><span class="sxs-lookup"><span data-stu-id="8be6f-114">If no format provider is specified in a call to the `Parse` or `TryParse` method, the format provider associated with the current thread culture (the [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object returned by the [NumberFormatInfo.CurrentInfo](xref:System.Globalization.NumberFormatInfo.CurrentInfo) property) is used.</span></span> 

<span data-ttu-id="8be6f-115">格式提供者是由 [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) 實作代表。</span><span class="sxs-lookup"><span data-stu-id="8be6f-115">A format provider is represented by an [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) implementation.</span></span> <span data-ttu-id="8be6f-116">此介面有單一成員 [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 方法，其單一參數是表示要格式化類型的 [Type](xref:System.Type) 物件。</span><span class="sxs-lookup"><span data-stu-id="8be6f-116">This interface has a single member, the [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method, whose single parameter is a [Type](xref:System.Type) object that represents the type to be formatted.</span></span> <span data-ttu-id="8be6f-117">此方法會傳回提供格式設定資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="8be6f-117">This method returns the object that provides formatting information.</span></span> <span data-ttu-id="8be6f-118">.NET 支援下列兩個剖析數值字串的 [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) 實作︰</span><span class="sxs-lookup"><span data-stu-id="8be6f-118">.NET supports the following two [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) implementations for parsing numeric strings:</span></span>

* <span data-ttu-id="8be6f-119">[CultureInfo](xref:System.Globalization.CultureInfo) 物件，其 [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) 方法會傳回提供特定文化特性格式資訊的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件。</span><span class="sxs-lookup"><span data-stu-id="8be6f-119">A [CultureInfo](xref:System.Globalization.CultureInfo) object whose [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) method returns a [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object that provides culture-specific formatting information.</span></span>

* <span data-ttu-id="8be6f-120">[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件，其 [NumberFormatInfo.GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) 方法會傳回自己本身。</span><span class="sxs-lookup"><span data-stu-id="8be6f-120">A [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object whose [NumberFormatInfo.GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) method returns itself.</span></span>

<span data-ttu-id="8be6f-121">下例嘗試將陣列中的每個字串轉換成 [Double](xref:System.Double) 值。</span><span class="sxs-lookup"><span data-stu-id="8be6f-121">The following example tries to convert each string in an array to a [Double](xref:System.Double) value.</span></span> <span data-ttu-id="8be6f-122">它會先嘗試使用反映英文 (美國) 文化特性慣例的格式提供者剖析字串。</span><span class="sxs-lookup"><span data-stu-id="8be6f-122">It first tries to parse the string by using a format provider that reflects the conventions of the English (United States) culture.</span></span> <span data-ttu-id="8be6f-123">如果此作業擲回 [FormatException](xref:System.FormatException)，它會嘗試使用來映法文 (法國) 文化特性慣例的格式提供者剖析字串。</span><span class="sxs-lookup"><span data-stu-id="8be6f-123">If this operation throws a [FormatException](xref:System.FormatException), it tries to parse the string by using a format provider that reflects the conventions of the French (France) culture.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string[] values = { "1,304.16", "$1,456.78", "1,094", "152", 
                          "123,45 €", "1 304,16", "Ae9f" };
      double number;
      CultureInfo culture = null;

      foreach (string value in values) {
         try {
            culture = CultureInfo.CreateSpecificCulture("en-US");
            number = Double.Parse(value, culture);
            Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number);
         }   
         catch (FormatException) {
            Console.WriteLine("{0}: Unable to parse '{1}'.", 
                              culture.Name, value);
            culture = CultureInfo.CreateSpecificCulture("fr-FR");
            try {
               number = Double.Parse(value, culture);
               Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number);
            }
            catch (FormatException) {
               Console.WriteLine("{0}: Unable to parse '{1}'.", 
                                 culture.Name, value);
            }
         }
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//    en-US: 1,304.16 --> 1304.16
//    
//    en-US: Unable to parse '$1,456.78'.
//    fr-FR: Unable to parse '$1,456.78'.
//    
//    en-US: 1,094 --> 1094
//    
//    en-US: 152 --> 152
//    
//    en-US: Unable to parse '123,45 €'.
//    fr-FR: Unable to parse '123,45 €'.
//    
//    en-US: Unable to parse '1 304,16'.
//    fr-FR: 1 304,16 --> 1304.16
//    
//    en-US: Unable to parse 'Ae9f'.
//    fr-FR: Unable to parse 'Ae9f'.
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim values() As String = { "1,304.16", "$1,456.78", "1,094", "152", 
                                 "123,45 €", "1 304,16", "Ae9f" }
      Dim number As Double
      Dim culture As CultureInfo = Nothing

      For Each value As String In values
         Try
            culture = CultureInfo.CreateSpecificCulture("en-US")
            number = Double.Parse(value, culture)
            Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number)
         Catch e As FormatException
            Console.WriteLine("{0}: Unable to parse '{1}'.", 
                              culture.Name, value)
            culture = CultureInfo.CreateSpecificCulture("fr-FR")
            Try
               number = Double.Parse(value, culture)
               Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number)
            Catch ex As FormatException
               Console.WriteLine("{0}: Unable to parse '{1}'.", 
                                 culture.Name, value)
            End Try
         End Try
         Console.WriteLine()
      Next
   End Sub
End Module
' The example displays the following output:
'    en-US: 1,304.16 --> 1304.16
'    
'    en-US: Unable to parse '$1,456.78'.
'    fr-FR: Unable to parse '$1,456.78'.
'    
'    en-US: 1,094 --> 1094
'    
'    en-US: 152 --> 152
'    
'    en-US: Unable to parse '123,45 €'.
'    fr-FR: Unable to parse '123,45 €'.
'    
'    en-US: Unable to parse '1 304,16'.
'    fr-FR: 1 304,16 --> 1304.16
'    
'    en-US: Unable to parse 'Ae9f'.
'    fr-FR: Unable to parse 'Ae9f'.
```

## <a name="parsing-and-numberstyles-values"></a><span data-ttu-id="8be6f-124">剖析及 NumberStyles 值</span><span class="sxs-lookup"><span data-stu-id="8be6f-124">Parsing and NumberStyles values</span></span>

<span data-ttu-id="8be6f-125">剖析作業可以處理的樣式項目 (例如空白字元、群組分隔符號和小數分隔符號)，是由 [NumberStyles](xref:System.Globalization.NumberStyles) 列舉值所定義。</span><span class="sxs-lookup"><span data-stu-id="8be6f-125">The style elements (such as white space, group separators, and decimal separator) that the parse operation can handle are defined by a [NumberStyles](xref:System.Globalization.NumberStyles) enumeration value.</span></span> <span data-ttu-id="8be6f-126">根據預設，代表整數值的字串是使用 [NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer) 值剖析，這僅允許數字、前置和後置空白字元和前置正負號。</span><span class="sxs-lookup"><span data-stu-id="8be6f-126">By default, strings that represent integer values are parsed by using the [NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer) value, which permits only numeric digits, leading and trailing white space, and a leading sign.</span></span> <span data-ttu-id="8be6f-127">表示浮點值的字串是使用 [NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) 和 [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) 的組合值剖析，此複合樣式允許十進位數字及前置和後置空白字元、前置正負號、小數分隔符號、群組分隔符號和指數。</span><span class="sxs-lookup"><span data-stu-id="8be6f-127">Strings that represent floating-point values are parsed using a combination of the [NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) and [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) values; this composite style permits decimal digits along with leading and trailing white space, a leading sign, a decimal separator, a group separator, and an exponent.</span></span> <span data-ttu-id="8be6f-128">藉由呼叫包含 [NumberStyles](xref:System.Globalization.NumberStyles) 類型參數的 `Parse` 或 `TryParse` 方法的多載，及設定一或多個 [NumberStyles](xref:System.Globalization.NumberStyles) 旗標，您可以控制字串得以顯示的樣式項目，成功進行利剖析作業。</span><span class="sxs-lookup"><span data-stu-id="8be6f-128">By calling an overload of the `Parse` or `TryParse` method that includes a parameter of type [NumberStyles](xref:System.Globalization.NumberStyles) and setting one or more [NumberStyles](xref:System.Globalization.NumberStyles) flags, you can control the style elements that can be present in the string for the parse operation to succeed.</span></span> 

<span data-ttu-id="8be6f-129">例如，使用 [Int32.Parse(String)](xref:System.Int32.Parse(System.String)) 方法無法將包含群組分隔符號的字串轉換為 [Int32](xref:System.Int32) 值。</span><span class="sxs-lookup"><span data-stu-id="8be6f-129">For example, a string that contains a group separator cannot be converted to an [Int32](xref:System.Int32) value by using the [Int32.Parse(String)](xref:System.Int32.Parse(System.String)) method.</span></span> <span data-ttu-id="8be6f-130">但若使用 [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) 旗標，則轉換會成功，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8be6f-130">However, the conversion succeeds if you use the [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) flag, as the following example illustrates.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string value = "1,304";
      int number;
      IFormatProvider provider = CultureInfo.CreateSpecificCulture("en-US");
      if (Int32.TryParse(value, out number))
         Console.WriteLine("{0} --> {1}", value, number);
      else
         Console.WriteLine("Unable to convert '{0}'", value);

      if (Int32.TryParse(value, NumberStyles.Integer | NumberStyles.AllowThousands, 
                        provider, out number))
         Console.WriteLine("{0} --> {1}", value, number);
      else
         Console.WriteLine("Unable to convert '{0}'", value);
   }
}
// The example displays the following output:
//       Unable to convert '1,304'
//       1,304 --> 1304
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As String = "1,304"
      Dim number As Integer
      Dim provider As IFormatProvider = CultureInfo.CreateSpecificCulture("en-US")
      If Int32.TryParse(value, number) Then
         Console.WriteLine("{0} --> {1}", value, number)
      Else
         Console.WriteLine("Unable to convert '{0}'", value)
      End If

      If Int32.TryParse(value, NumberStyles.Integer Or NumberStyles.AllowThousands, 
                        provider, number) Then
         Console.WriteLine("{0} --> {1}", value, number)
      Else
         Console.WriteLine("Unable to convert '{0}'", value)
      End If
   End Sub
End Module
' The example displays the following output:
'       Unable to convert '1,304'
'       1,304 --> 1304
```

> <span data-ttu-id="8be6f-131">**警告**</span><span class="sxs-lookup"><span data-stu-id="8be6f-131">**Warning**</span></span>
>
> <span data-ttu-id="8be6f-132">剖析作業一律使用特定文化特性的格式化慣例。</span><span class="sxs-lookup"><span data-stu-id="8be6f-132">The parse operation always uses the formatting conventions of a particular culture.</span></span> <span data-ttu-id="8be6f-133">如果不藉由傳遞 [CultureInfo](xref:System.Globalization.CultureInfo) 或 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件來指定文化特性，就會使用與目前執行緒相關聯的文化特性。</span><span class="sxs-lookup"><span data-stu-id="8be6f-133">If you do not specify a culture by passing a [CultureInfo](xref:System.Globalization.CultureInfo) or [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object, the culture associated with the current thread is used.</span></span>
 
<span data-ttu-id="8be6f-134">下表列出 [NumberStyles](xref:System.Globalization.NumberStyles) 列舉的成員，並說明它們對剖析作業的影響。</span><span class="sxs-lookup"><span data-stu-id="8be6f-134">The following table lists the members of the [NumberStyles](xref:System.Globalization.NumberStyles) enumeration and describes the effect that they have on the parsing operation.</span></span>

<span data-ttu-id="8be6f-135">NumberStyles 值</span><span class="sxs-lookup"><span data-stu-id="8be6f-135">NumberStyles value</span></span> | <span data-ttu-id="8be6f-136">對要剖析字串的影響</span><span class="sxs-lookup"><span data-stu-id="8be6f-136">Effect on the string to be parsed</span></span>
------------------ | --------------------------------- 
[<span data-ttu-id="8be6f-137">NumberStyles.None</span><span class="sxs-lookup"><span data-stu-id="8be6f-137">NumberStyles.None</span></span>](xref:System.Globalization.NumberStyles.None) | <span data-ttu-id="8be6f-138">只允許數字。</span><span class="sxs-lookup"><span data-stu-id="8be6f-138">Only numeric digits are permitted.</span></span>
[<span data-ttu-id="8be6f-139">NumberStyles.AllowDecimalPoint</span><span class="sxs-lookup"><span data-stu-id="8be6f-139">NumberStyles.AllowDecimalPoint</span></span>](xref:System.Globalization.NumberStyles.AllowDecimalPoint) | <span data-ttu-id="8be6f-140">允許小數分隔符號和小數位。</span><span class="sxs-lookup"><span data-stu-id="8be6f-140">The decimal separator and fractional digits are permitted.</span></span> <span data-ttu-id="8be6f-141">若為整數值，小數位只允許零。</span><span class="sxs-lookup"><span data-stu-id="8be6f-141">For integer values, only zero is permitted as a fractional digit.</span></span> <span data-ttu-id="8be6f-142">有效的十進位分隔符號由 [NumberFormatInfo.NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) 或 [NumberFormatInfo.CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) 屬性決定。</span><span class="sxs-lookup"><span data-stu-id="8be6f-142">Valid decimal separators are determined by the [NumberFormatInfo.NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) or [NumberFormatInfo.CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) property.</span></span>
[<span data-ttu-id="8be6f-143">NumberStyles.AllowExponent</span><span class="sxs-lookup"><span data-stu-id="8be6f-143">NumberStyles.AllowExponent</span></span>](xref:System.Globalization.NumberStyles.AllowExponent) | <span data-ttu-id="8be6f-144">可以使用 "e" 或 "E" 字元表示指數標記法。</span><span class="sxs-lookup"><span data-stu-id="8be6f-144">The "e" or "E" character can be used to indicate exponential notation.</span></span>
[<span data-ttu-id="8be6f-145">NumberStyles.AllowLeadingWhite</span><span class="sxs-lookup"><span data-stu-id="8be6f-145">NumberStyles.AllowLeadingWhite</span></span>](xref:System.Globalization.NumberStyles.AllowLeadingWhite) | <span data-ttu-id="8be6f-146">可以使用前置空白字元。</span><span class="sxs-lookup"><span data-stu-id="8be6f-146">Leading white space is permitted.</span></span>
[<span data-ttu-id="8be6f-147">NumberStyles.AllowTrailingWhite</span><span class="sxs-lookup"><span data-stu-id="8be6f-147">NumberStyles.AllowTrailingWhite</span></span>](xref:System.Globalization.NumberStyles.AllowTrailingWhite) | <span data-ttu-id="8be6f-148">可以使用後置空白字元。</span><span class="sxs-lookup"><span data-stu-id="8be6f-148">Trailing white space is permitted.</span></span>
[<span data-ttu-id="8be6f-149">NumberStyles.AllowLeadingSign</span><span class="sxs-lookup"><span data-stu-id="8be6f-149">NumberStyles.AllowLeadingSign</span></span>](xref:System.Globalization.NumberStyles.AllowLeadingSign) | <span data-ttu-id="8be6f-150">數字前面可以使用正負號。</span><span class="sxs-lookup"><span data-stu-id="8be6f-150">A positive or negative sign can precede numeric digits.</span></span>
[<span data-ttu-id="8be6f-151">NumberStyles.AllowTrailingSign</span><span class="sxs-lookup"><span data-stu-id="8be6f-151">NumberStyles.AllowTrailingSign</span></span>](xref:System.Globalization.NumberStyles.AllowTrailingSign) | <span data-ttu-id="8be6f-152">數字後面可以使用正負號。</span><span class="sxs-lookup"><span data-stu-id="8be6f-152">A positive or negative sign can follow numeric digits.</span></span>
[<span data-ttu-id="8be6f-153">NumberStyles.AllowParentheses</span><span class="sxs-lookup"><span data-stu-id="8be6f-153">NumberStyles.AllowParentheses</span></span>](xref:System.Globalization.NumberStyles.AllowParentheses) | <span data-ttu-id="8be6f-154">可以使用括號表示負數值。</span><span class="sxs-lookup"><span data-stu-id="8be6f-154">Parentheses can be used to indicate negative values.</span></span>
[<span data-ttu-id="8be6f-155">NumberStyles.AllowThousands</span><span class="sxs-lookup"><span data-stu-id="8be6f-155">NumberStyles.AllowThousands</span></span>](xref:System.Globalization.NumberStyles.AllowThousands) | <span data-ttu-id="8be6f-156">允許群組分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8be6f-156">The group separator is permitted.</span></span> <span data-ttu-id="8be6f-157">群組分隔符號字元由 [NumberFormatInfo.NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) 或 [NumberFormatInfo.CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) 屬性決定。</span><span class="sxs-lookup"><span data-stu-id="8be6f-157">The group separator character is determined by the [NumberFormatInfo.NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) or [NumberFormatInfo.CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) property.</span></span>
[<span data-ttu-id="8be6f-158">NumberStyles.AllowCurrencySymbol</span><span class="sxs-lookup"><span data-stu-id="8be6f-158">NumberStyles.AllowCurrencySymbol</span></span>](xref:System.Globalization.NumberStyles.AllowCurrencySymbol) | <span data-ttu-id="8be6f-159">允許使用貨幣符號。</span><span class="sxs-lookup"><span data-stu-id="8be6f-159">The currency symbol is permitted.</span></span> <span data-ttu-id="8be6f-160">根據貨幣符號是由 [NumberFormatInfo.CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) 屬性定義。</span><span class="sxs-lookup"><span data-stu-id="8be6f-160">The currency symbol is defined by the [NumberFormatInfo.CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) property.</span></span>
[<span data-ttu-id="8be6f-161">NumberStyles.AllowHexSpecifier</span><span class="sxs-lookup"><span data-stu-id="8be6f-161">NumberStyles.AllowHexSpecifier</span></span>](xref:System.Globalization.NumberStyles.AllowHexSpecifier) | <span data-ttu-id="8be6f-162">要剖析的字串會解譯為十六進位數字。</span><span class="sxs-lookup"><span data-stu-id="8be6f-162">The string to be parsed is interpreted as a hexadecimal number.</span></span> <span data-ttu-id="8be6f-163">它可以包含十六進位數字 0-9、A-F 和 a-f。</span><span class="sxs-lookup"><span data-stu-id="8be6f-163">It can include the hexadecimal digits 0-9, A-F, and a-f.</span></span> <span data-ttu-id="8be6f-164">這個旗標只能用於剖析整數值。</span><span class="sxs-lookup"><span data-stu-id="8be6f-164">This flag can be used only to parse integer values.</span></span>
 
<span data-ttu-id="8be6f-165">此外，[NumberStyles](xref:System.Globalization.NumberStyles) 列舉提供下列複合樣式，包括多個 [NumberStyles](xref:System.Globalization.NumberStyles) 旗標。</span><span class="sxs-lookup"><span data-stu-id="8be6f-165">In addition, the [NumberStyles](xref:System.Globalization.NumberStyles) enumeration provides the following composite styles, which include multiple [NumberStyles](xref:System.Globalization.NumberStyles) flags.</span></span> 

<span data-ttu-id="8be6f-166">複合的 NumberStyles 值</span><span class="sxs-lookup"><span data-stu-id="8be6f-166">Composite NumberStyles value</span></span> | <span data-ttu-id="8be6f-167">包含成員</span><span class="sxs-lookup"><span data-stu-id="8be6f-167">Includes members</span></span>
---------------------------- | ---------------- 
[<span data-ttu-id="8be6f-168">NumberStyles.Integer</span><span class="sxs-lookup"><span data-stu-id="8be6f-168">NumberStyles.Integer</span></span>](xref:System.Globalization.NumberStyles.Integer) | <span data-ttu-id="8be6f-169">包含 [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) 和 [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign) 樣式。</span><span class="sxs-lookup"><span data-stu-id="8be6f-169">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), and [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign) styles.</span></span> <span data-ttu-id="8be6f-170">這是用來剖析整數值的預設樣式。</span><span class="sxs-lookup"><span data-stu-id="8be6f-170">This is the default style used to parse integer values.</span></span>
[<span data-ttu-id="8be6f-171">NumberStyles.Number</span><span class="sxs-lookup"><span data-stu-id="8be6f-171">NumberStyles.Number</span></span>](xref:System.Globalization.NumberStyles.Number) | <span data-ttu-id="8be6f-172">包含 [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite)、[NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign)、[NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign)、[NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) 和 [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) 樣式。</span><span class="sxs-lookup"><span data-stu-id="8be6f-172">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint), and [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) styles.</span></span>
[<span data-ttu-id="8be6f-173">NumberStyles.Float</span><span class="sxs-lookup"><span data-stu-id="8be6f-173">NumberStyles.Float</span></span>](xref:System.Globalization.NumberStyles.Float) | <span data-ttu-id="8be6f-174">包含 [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite)、[NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign)、[NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) 和 [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) 樣式。</span><span class="sxs-lookup"><span data-stu-id="8be6f-174">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint), and [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) styles.</span></span>
[<span data-ttu-id="8be6f-175">NumberStyles.Currency</span><span class="sxs-lookup"><span data-stu-id="8be6f-175">NumberStyles.Currency</span></span>](xref:System.Globalization.NumberStyles.Currency) | <span data-ttu-id="8be6f-176">包含所有樣式，但 [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) 和 [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) 除外。</span><span class="sxs-lookup"><span data-stu-id="8be6f-176">Includes all styles except [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) and [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).</span></span>
[<span data-ttu-id="8be6f-177">NumberStyles.Any</span><span class="sxs-lookup"><span data-stu-id="8be6f-177">NumberStyles.Any</span></span>](xref:System.Globalization.NumberStyles.Any) | <span data-ttu-id="8be6f-178">包含所有樣式，但 [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) 除外。</span><span class="sxs-lookup"><span data-stu-id="8be6f-178">Includes all styles except [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).</span></span>
[<span data-ttu-id="8be6f-179">NumberStyles.HexNumber</span><span class="sxs-lookup"><span data-stu-id="8be6f-179">NumberStyles.HexNumber</span></span>](xref:System.Globalization.NumberStyles.HexNumber) | <span data-ttu-id="8be6f-180">包含 [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) 和 [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) 樣式。</span><span class="sxs-lookup"><span data-stu-id="8be6f-180">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), and [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) styles.</span></span>
 
## <a name="parsing-and-unicode-digits"></a><span data-ttu-id="8be6f-181">剖析及 Unicode 數字</span><span class="sxs-lookup"><span data-stu-id="8be6f-181">Parsing and Unicode digits</span></span>

<span data-ttu-id="8be6f-182">Unicode 標準會定義各種書寫系統中數字的字碼指標。</span><span class="sxs-lookup"><span data-stu-id="8be6f-182">The Unicode standard defines code points for digits in various writing systems.</span></span> <span data-ttu-id="8be6f-183">例如，U+0030 到 U+0039 的字碼指標表示基本拉丁文數字 0 到 9，U+09E6 到 U+09EF 字碼指標表示孟加拉文數字 0 到 9，而 U+FF10 到 U+FF19 字碼指數表示全形數字 0 到 9。</span><span class="sxs-lookup"><span data-stu-id="8be6f-183">For example, code points from U+0030 to U+0039 represent the basic Latin digits 0 through 9, code points from U+09E6 to U+09EF represent the Bangla digits 0 through 9, and code points from U+FF10 to U+FF19 represent the Fullwidth digits 0 through 9.</span></span> <span data-ttu-id="8be6f-184">不過，剖析方法唯一認識的數字是基本拉丁文數字 0-9 與 U+0030 到 U+0039 字碼指標。</span><span class="sxs-lookup"><span data-stu-id="8be6f-184">However, the only numeric digits recognized by parsing methods are the basic Latin digits 0-9 with code points from U+0030 to U+0039.</span></span> <span data-ttu-id="8be6f-185">如果數值剖析方法傳遞的字串包含任何其他數字，則方法會擲回 [FormatException](xref:System.FormatException)。</span><span class="sxs-lookup"><span data-stu-id="8be6f-185">If a numeric parsing method is passed a string that contains any other digits, the method throws a [FormatException](xref:System.FormatException).</span></span>

<span data-ttu-id="8be6f-186">下例使用 [Int32.Parse](xref:System.Int32.Parse(System.String)) 方法剖析以不同書寫系統數字組成的字串。</span><span class="sxs-lookup"><span data-stu-id="8be6f-186">The following example uses the [Int32.Parse](xref:System.Int32.Parse(System.String)) method to parse strings that consist of digits in different writing systems.</span></span> <span data-ttu-id="8be6f-187">如範例的輸出所示，嘗試剖析基本拉丁文數字會成功，而嘗試剖析全型、阿拉伯-印度文和孟加拉文數字則會失敗。</span><span class="sxs-lookup"><span data-stu-id="8be6f-187">As the output from the example shows, the attempt to parse the basic Latin digits succeeds, but the attempt to parse the Fullwidth, Arabic-Indic, and Bangla digits fails.</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string value;
      // Define a string of basic Latin digits 1-5.
      value = "\u0031\u0032\u0033\u0034\u0035";
      ParseDigits(value);

      // Define a string of Fullwidth digits 1-5.
      value = "\uFF11\uFF12\uFF13\uFF14\uFF15";
      ParseDigits(value);

      // Define a string of Arabic-Indic digits 1-5.
      value = "\u0661\u0662\u0663\u0664\u0665";
      ParseDigits(value);

      // Define a string of Bangla digits 1-5.
      value = "\u09e7\u09e8\u09e9\u09ea\u09eb";
      ParseDigits(value);
   }

   static void ParseDigits(string value)
   {
      try {
         int number = Int32.Parse(value);
         Console.WriteLine("'{0}' --> {1}", value, number);
      }   
      catch (FormatException) {
         Console.WriteLine("Unable to parse '{0}'.", value);      
      }     
   }
}
// The example displays the following output:
//       '12345' --> 12345
//       Unable to parse '１２３４５'.
//       Unable to parse '١٢٣٤٥'.
//       Unable to parse '১২৩৪৫'.
```

```vb
Module Example
   Public Sub Main()
      Dim value As String
      ' Define a string of basic Latin digits 1-5.
      value = ChrW(&h31) + ChrW(&h32) + ChrW(&h33) + ChrW(&h34) + ChrW(&h35)
      ParseDigits(value)

      ' Define a string of Fullwidth digits 1-5.
      value = ChrW(&hff11) + ChrW(&hff12) + ChrW(&hff13) + ChrW(&hff14) + ChrW(&hff15)
      ParseDigits(value)

      ' Define a string of Arabic-Indic digits 1-5.
      value = ChrW(&h661) + ChrW(&h662) + ChrW(&h663) + ChrW(&h664) + ChrW(&h665)
      ParseDigits(value)

      ' Define a string of Bangla digits 1-5.
      value = ChrW(&h09e7) + ChrW(&h09e8) + ChrW(&h09e9) + ChrW(&h09ea) + ChrW(&h09eb)
      ParseDigits(value)
   End Sub

   Sub ParseDigits(value As String)
      Try
         Dim number As Integer = Int32.Parse(value)
         Console.WriteLine("'{0}' --> {1}", value, number)
      Catch e As FormatException
         Console.WriteLine("Unable to parse '{0}'.", value)      
      End Try     
   End Sub
End Module
' The example displays the following output:
'       '12345' --> 12345
'       Unable to parse '１２３４５'.
'       Unable to parse '١٢٣٤٥'.
'       Unable to parse '১২৩৪৫'.
```

## <a name="see-also"></a><span data-ttu-id="8be6f-188">請參閱</span><span class="sxs-lookup"><span data-stu-id="8be6f-188">See also</span></span>

[<span data-ttu-id="8be6f-189">System.Globalization.NumberStyles</span><span class="sxs-lookup"><span data-stu-id="8be6f-189">System.Globalization.NumberStyles</span></span>](xref:System.Globalization.NumberStyles)

[<span data-ttu-id="8be6f-190">在 .NET 中剖析字串</span><span class="sxs-lookup"><span data-stu-id="8be6f-190">Parsing strings in .NET</span></span>](parsing-strings.md)

[<span data-ttu-id="8be6f-191">在 .NET 中格式化類型</span><span class="sxs-lookup"><span data-stu-id="8be6f-191">Formatting types in .NET</span></span>](formatting-types.md)


