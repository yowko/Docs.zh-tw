---
title: "格式化類型"
description: "格式化類型"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: cf497639-9f91-45cb-836f-998d1cea2f43
ms.translationtype: Human Translation
ms.sourcegitcommit: b967d8e55347f44a012e4ad8e916440ae228c8ec
ms.openlocfilehash: e9b8ad13a48dd43236769b130d6f8a75b7b023ca
ms.contentlocale: zh-tw
ms.lasthandoff: 03/10/2017

---

# <a name="formatting-types"></a><span data-ttu-id="92cdf-104">格式化類型</span><span class="sxs-lookup"><span data-stu-id="92cdf-104">Formatting types</span></span>

<span data-ttu-id="92cdf-105">格式化是將類別、結構或列舉值的執行個體轉換成字串表示的過程，通常是為了將結果字串展示予使用者，或是為了將字串藉還原序列化方式還原成原始的資料類型。</span><span class="sxs-lookup"><span data-stu-id="92cdf-105">Formatting is the process of converting an instance of a class, structure, or enumeration value to its string representation, often so that the resulting string can be displayed to users or deserialized to restore the original data type.</span></span> <span data-ttu-id="92cdf-106">這種轉換可能面臨幾項挑戰：</span><span class="sxs-lookup"><span data-stu-id="92cdf-106">This conversion can pose a number of challenges:</span></span>

* <span data-ttu-id="92cdf-107">值的內部儲存方式不見得反映出使用者想要的檢視方式。</span><span class="sxs-lookup"><span data-stu-id="92cdf-107">The way that values are stored internally does not necessarily reflect the way that users want to view them.</span></span> <span data-ttu-id="92cdf-108">例如，電話號碼可能以 **8009999999** 的格式儲存，但這並不太符合使用者的閱讀習慣。</span><span class="sxs-lookup"><span data-stu-id="92cdf-108">For example, a telephone number might be stored in the form **8009999999**, which is not user-friendly.</span></span> <span data-ttu-id="92cdf-109">應該改以顯示成 **800-999-9999**。</span><span class="sxs-lookup"><span data-stu-id="92cdf-109">It should instead be displayed as **800-999-9999**.</span></span> <span data-ttu-id="92cdf-110">如需以此方式格式化數字的範例，請參閱[自訂格式字串](#custom-format-strings)一節。</span><span class="sxs-lookup"><span data-stu-id="92cdf-110">See the [Custom format strings](#custom-format-strings) section for an example that formats a number in this way.</span></span> 

* <span data-ttu-id="92cdf-111">物件轉換後的字串表示有時候並不符合直覺。</span><span class="sxs-lookup"><span data-stu-id="92cdf-111">Sometimes the conversion of an object to its string representation is not intuitive.</span></span> <span data-ttu-id="92cdf-112">例如，**Temperature** 物件或 **Person** 物件的字串表示應該為何種格式，就不是那麼清楚。</span><span class="sxs-lookup"><span data-stu-id="92cdf-112">For example, it is not clear how the string representation of a **Temperature** object or a **Person** object should appear.</span></span> <span data-ttu-id="92cdf-113">如需以各種方式格式化 **Temperature** 物件的範例，請參閱[標準格式字串](#standard-format-strings)一節。</span><span class="sxs-lookup"><span data-stu-id="92cdf-113">For an example that formats a **Temperature** object in a variety of ways, see the [Standard format strings](#standard-format-strings) section.</span></span>

* <span data-ttu-id="92cdf-114">值的格式通常需要符合文化特性。</span><span class="sxs-lookup"><span data-stu-id="92cdf-114">Values often require culture-sensitive formatting.</span></span> <span data-ttu-id="92cdf-115">例如，如果應用程式需要使用數字來表達貨幣值，則數值字串應該包含目前文化特性的貨幣符號、群組分隔符號 (即大部分文化特性中的千位分隔符號) 和小數點符號。</span><span class="sxs-lookup"><span data-stu-id="92cdf-115">For example, in an application that uses numbers to reflect monetary values, numeric strings should include the current culture’s currency symbol, group separator (which, in most cultures, is the thousands separator), and decimal symbol.</span></span> <span data-ttu-id="92cdf-116">如需範例，請參閱[使用格式提供者及 IFormatProvider 介面執行區分文化特性的格式化](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)一節。</span><span class="sxs-lookup"><span data-stu-id="92cdf-116">For an example, see the [Culture-sensitive formatting with format providers and the IFormatProvider interface](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface) section.</span></span> 

* <span data-ttu-id="92cdf-117">應用程式可能需要以不同的方式來顯示相同的值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-117">An application may have to display the same value in different ways.</span></span> <span data-ttu-id="92cdf-118">例如，應用程式在表示列舉成員時，在做法上可能是顯示其名稱的字串表示，或顯示其基礎值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-118">For example, an application may represent an enumeration member by displaying a string representation of its name or by displaying its underlying value.</span></span> <span data-ttu-id="92cdf-119">如需以不同方式格式化 [DayOfWeek](xref:System.DayOfWeek) 列舉成員的範例，請參閱[標準格式字串](#standard-format-strings)一節。</span><span class="sxs-lookup"><span data-stu-id="92cdf-119">For an example that formats a member of the [DayOfWeek](xref:System.DayOfWeek) enumeration in different ways, see the [Standard format strings](#standard-format-strings) section.</span></span>

<span data-ttu-id="92cdf-120">.NET 提供豐富的格式化支援，可滿足開發人員的這些需求。</span><span class="sxs-lookup"><span data-stu-id="92cdf-120">.NET provides rich formatting support that enables developers to address these requirements.</span></span> 

> [!NOTE]
> <span data-ttu-id="92cdf-121">格式化會將某種類型的值轉換為字串表示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-121">Formatting converts the value of a type into a string representation.</span></span> <span data-ttu-id="92cdf-122">剖析是格式化的反向操作。</span><span class="sxs-lookup"><span data-stu-id="92cdf-122">Parsing is the inverse of formatting.</span></span> <span data-ttu-id="92cdf-123">剖析作業會從資料類型的字串表示來建立資料類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="92cdf-123">A parsing operation creates an instance of a data type from its string representation.</span></span> <span data-ttu-id="92cdf-124">如需將字串轉換為其他資料類型的資訊，請參閱[剖析字串](parsing-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="92cdf-124">For information about converting strings to other data types, see [Parsing strings](parsing-strings.md).</span></span>

<span data-ttu-id="92cdf-125">本概觀包含下列各節：</span><span class="sxs-lookup"><span data-stu-id="92cdf-125">This overview contains the following sections:</span></span>

* [<span data-ttu-id="92cdf-126">.NET 中的格式化​​</span><span class="sxs-lookup"><span data-stu-id="92cdf-126">Formatting in .NET</span></span>](#formatting-in-net)

* [<span data-ttu-id="92cdf-127">使用 ToString 方法的預設格式</span><span class="sxs-lookup"><span data-stu-id="92cdf-127">Default formatting using the ToString method</span></span>](#default-formatting-using-the-tostring-method)

* [<span data-ttu-id="92cdf-128">覆寫 ToString 方法</span><span class="sxs-lookup"><span data-stu-id="92cdf-128">Overriding the ToString method</span></span>](#overriding-the-tostring-method)

* [<span data-ttu-id="92cdf-129">ToString 方法及格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-129">The ToString method and format strings</span></span>](#the-tostring-method-and-format-strings)

    * [<span data-ttu-id="92cdf-130">標準格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-130">Standard format strings</span></span>](#standard-format-strings)
    
    * [<span data-ttu-id="92cdf-131">自訂格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-131">Custom format strings</span></span>](#custom-format-strings)
    
    * [<span data-ttu-id="92cdf-132">格式字串與 .NET 類型</span><span class="sxs-lookup"><span data-stu-id="92cdf-132">Format strings and .NET types</span></span>](#format-strings-and-net-types)
    
* [<span data-ttu-id="92cdf-133">使用格式提供者及 IFormatProvider 介面執行區分文化特性的格式化</span><span class="sxs-lookup"><span data-stu-id="92cdf-133">Culture-sensitive formatting with format providers and the IFormatProvider interface</span></span>](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)

    * [<span data-ttu-id="92cdf-134">區分文化特性格式的數值</span><span class="sxs-lookup"><span data-stu-id="92cdf-134">Culture-sensitive formatting of numeric values</span></span>](#culture-sensitive-formatting-of-numeric-values)
    
    * [<span data-ttu-id="92cdf-135">區分文化特性格式的日期與時間值</span><span class="sxs-lookup"><span data-stu-id="92cdf-135">Culture-sensitive formatting of date and time values</span></span>](#culture-sensitive-formatting-of-date-and-time-values)
    
* [<span data-ttu-id="92cdf-136">IFormattable 介面</span><span class="sxs-lookup"><span data-stu-id="92cdf-136">The IFormattable interface</span></span>](#the-iformattable-interface)

* [<span data-ttu-id="92cdf-137">複合格式</span><span class="sxs-lookup"><span data-stu-id="92cdf-137">Composite formatting</span></span>](#composite-formatting)

* [<span data-ttu-id="92cdf-138">使用 ICustomFormatter 的自訂格式</span><span class="sxs-lookup"><span data-stu-id="92cdf-138">Custom formatting with ICustomFormatter</span></span>](#custom-formatting-with-icustomformatter)

* [<span data-ttu-id="92cdf-139">相關主題</span><span class="sxs-lookup"><span data-stu-id="92cdf-139">Related topics</span></span>](#related-topics)

* [<span data-ttu-id="92cdf-140">參考</span><span class="sxs-lookup"><span data-stu-id="92cdf-140">Reference</span></span>](#reference)

## <a name="formatting-in-net"></a><span data-ttu-id="92cdf-141">.NET 中的格式化​​</span><span class="sxs-lookup"><span data-stu-id="92cdf-141">Formatting in .NET</span></span>

<span data-ttu-id="92cdf-142">[Object.ToString](xref:System.Object.ToString)預設會實作格式化的基本機制。本主題後文的[使用 ToString 方法的預設格式](#default-formatting-using-the-tostring-method)一節將有所討論。</span><span class="sxs-lookup"><span data-stu-id="92cdf-142">The basic mechanism for formatting is the default implementation of the [Object.ToString](xref:System.Object.ToString) method, which is discussed in the [Default formatting using the ToString method](#default-formatting-using-the-tostring-method) section later in this topic.</span></span> <span data-ttu-id="92cdf-143">不過，.NET 提供幾種方式來修改和擴充其預設格式化支援。</span><span class="sxs-lookup"><span data-stu-id="92cdf-143">However, .NET provides several ways to modify and extend its default formatting support.</span></span> <span data-ttu-id="92cdf-144">這些需求包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="92cdf-144">These include the following:</span></span>

* <span data-ttu-id="92cdf-145">覆寫 [Object.ToString](xref:System.Object.ToString) 方法來定義物件值的自訂字串表示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-145">Overriding the [Object.ToString](xref:System.Object.ToString) method to define a custom string representation of an object’s value.</span></span> <span data-ttu-id="92cdf-146">如需詳細資訊，請參閱本主題後文的[覆寫 ToString 方法](#overriding-the-tostring-method)一節。</span><span class="sxs-lookup"><span data-stu-id="92cdf-146">For more information, see the [Overriding the ToString method](#overriding-the-tostring-method) section later in this topic.</span></span>

* <span data-ttu-id="92cdf-147">定義格式規範，格式規範讓物件值的字串表示可以採用多種形式。</span><span class="sxs-lookup"><span data-stu-id="92cdf-147">Defining format specifiers that enable the string representation of an object’s value to take multiple forms.</span></span> <span data-ttu-id="92cdf-148">例如，下列陳述式中的 "X" 格式規範會將整數轉換為十六進位值的字串表示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-148">For example, the "X" format specifier in the following statement converts an integer to the string representation of a hexadecimal value.</span></span>

  ```csharp
  int integerValue = 60312;
  Console.WriteLine(integerValue.ToString("X"));   // Displays EB98.
  ```

  ```vb
  Dim integerValue As Integer = 60312
  Console.WriteLine(integerValue.ToString("X"))   ' Displays EB98.
  ```
  
  <span data-ttu-id="92cdf-149">如需格式規範的詳細資訊，請參閱 [ToString 方法與格式字串](#the-tostring-method-and-format-strings)一節。</span><span class="sxs-lookup"><span data-stu-id="92cdf-149">For more information about format specifiers, see the [The ToString method and format strings](#the-tostring-method-and-format-strings) section.</span></span>
  
* <span data-ttu-id="92cdf-150">透過格式提供者來採用特定文化特性的格式化慣例。</span><span class="sxs-lookup"><span data-stu-id="92cdf-150">Using format providers to take advantage of the formatting conventions of a specific culture.</span></span> <span data-ttu-id="92cdf-151">例如，下列陳述式會使用 en-US 文化特性的格式化慣例來顯示貨幣值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-151">For example, the following statement displays a currency value by using the formatting conventions of the en-US culture.</span></span> 

  ```csharp
  double cost = 1632.54; 
  Console.WriteLine(cost.ToString("C", 
                  new System.Globalization.CultureInfo("en-US")));   
  // The example displays the following output:
  //       $1,632.54
  ```

  ```vb
  Dim cost As Double = 1632.54
  Console.WriteLine(cost.ToString("C", New System.Globalization.CultureInfo("en-US")))
  ' The example displays the following output:
  '       $1,632.54
  ```
  
  <span data-ttu-id="92cdf-152">如需如何使用格式提供者及 IFormatProvider 介面的詳細資訊，請參閱[使用格式提供者及 IFormatProvider 介面執行區分文化特性的格式化](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)一節。</span><span class="sxs-lookup"><span data-stu-id="92cdf-152">For more information about formatting with format providers, see the [Culture-sensitive formatting with format providers and the IFormatProvider interface](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface) section.</span></span>  
  
* <span data-ttu-id="92cdf-153">實作 [IFormattable](xref:System.IFormattable) 介面，以同時支援使用 [Convert](xref:System.Convert) 類別和複合格式來轉換字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-153">Implementing the [IFormattable](xref:System.IFormattable) interface to support both string conversion with the [Convert](xref:System.Convert) class and composite formatting.</span></span> <span data-ttu-id="92cdf-154">如需詳細資訊，請參閱 [IFormattable 介面](#the-iformattable-interface)一節。</span><span class="sxs-lookup"><span data-stu-id="92cdf-154">For more information, see the [The IFormattable interface](#the-iformattable-interface) section.</span></span>

* <span data-ttu-id="92cdf-155">使用複合格式將值的字串表示嵌入更大的字串中。</span><span class="sxs-lookup"><span data-stu-id="92cdf-155">Using composite formatting to embed the string representation of a value in a larger string.</span></span> <span data-ttu-id="92cdf-156">如需詳細資訊，請參閱[複合格式](#composite-formatting)一節。</span><span class="sxs-lookup"><span data-stu-id="92cdf-156">For more information, see the [Composite formatting](#composite-formatting) section.</span></span>

* <span data-ttu-id="92cdf-157">實作 [ICustomFormatter](xref:System.ICustomFormatter) 和 [IFormatProvider](xref:System.IFormatProvider) 來提供完整的自訂格式解決方案。</span><span class="sxs-lookup"><span data-stu-id="92cdf-157">Implementing [ICustomFormatter](xref:System.ICustomFormatter) and [IFormatProvider](xref:System.IFormatProvider) to provide a complete custom formatting solution.</span></span> <span data-ttu-id="92cdf-158">如需詳細資訊，請參閱[使用 ICustomFormatter 的自訂格式](#custom-formatting-with-icustomformatter)一節。</span><span class="sxs-lookup"><span data-stu-id="92cdf-158">For more information, see the [Custom formatting with ICustomFormatter](#custom-formatting-with-icustomformatter) section.</span></span>

<span data-ttu-id="92cdf-159">下列各節會討論這些將物件轉換為其字串表示的方法。</span><span class="sxs-lookup"><span data-stu-id="92cdf-159">The following sections examine these methods for converting an object to its string representation.</span></span>

## <a name="default-formatting-using-the-tostring-method"></a><span data-ttu-id="92cdf-160">使用 ToString 方法的預設格式</span><span class="sxs-lookup"><span data-stu-id="92cdf-160">Default formatting using the ToString method</span></span>

<span data-ttu-id="92cdf-161">每個衍生自 [System.Object](xref:System.Object) 的類型都會自動繼承無參數的 [ToString](xref:System.Object.ToString) 方法，這個方法預設會傳回型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="92cdf-161">Every type that is derived from [System.Object](xref:System.Object) automatically inherits a parameterless [ToString](xref:System.Object.ToString) method, which returns the name of the type by default.</span></span> <span data-ttu-id="92cdf-162">下列範例示範預設的 [ToString](xref:System.Object.ToString) 方法。</span><span class="sxs-lookup"><span data-stu-id="92cdf-162">The following example illustrates the default [ToString](xref:System.Object.ToString) method.</span></span> <span data-ttu-id="92cdf-163">範例中會定義一個不具任何實作的 `Automobile` 類別。</span><span class="sxs-lookup"><span data-stu-id="92cdf-163">It defines a class named `Automobile` that has no implementation.</span></span> <span data-ttu-id="92cdf-164">當具現化這個類別並呼叫其 [ToString](xref:System.Object.ToString) 方法時，會顯示這個類別的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="92cdf-164">When the class is instantiated and its [ToString](xref:System.Object.ToString) method is called, it displays its type name.</span></span> <span data-ttu-id="92cdf-165">請注意，在範例中不會明確呼叫 [ToString](xref:System.Object.ToString) 方法。</span><span class="sxs-lookup"><span data-stu-id="92cdf-165">Note that the [ToString](xref:System.Object.ToString) method is not explicitly called in the example.</span></span> <span data-ttu-id="92cdf-166">[Console.WriteLine(Object)](xref:System.Console.WriteLine(System.Object)) 方法會隱含呼叫本身所收到作為引數傳遞之物件的 [ToString](xref:System.Object.ToString) 方法。</span><span class="sxs-lookup"><span data-stu-id="92cdf-166">The [Console.WriteLine(Object)](xref:System.Console.WriteLine(System.Object)) method implicitly calls the [ToString](xref:System.Object.ToString) method of the object passed to it as an argument.</span></span> 

```csharp
using System;

public class Automobile
{
   // No implementation. All members are inherited from Object.
}

public class Example
{
   public static void Main()
   {
      Automobile firstAuto = new Automobile();
      Console.WriteLine(firstAuto);
   }
}
// The example displays the following output:
//       Automobile
```

```vb 
Public Class Automobile
   ' No implementation. All members are inherited from Object.
End Class

Module Example
   Public Sub Main()
      Dim firstAuto As New Automobile()
      Console.WriteLine(firstAuto)
   End Sub
End Module
' The example displays the following output:
'       Automobile
```

<span data-ttu-id="92cdf-167">因為除介面以外的所有其他類型都會衍生自 [Object](xref:System.Object)，所以您的自訂類別或結構會自動被賦予此功能。</span><span class="sxs-lookup"><span data-stu-id="92cdf-167">Because all types other than interfaces are derived from [Object](xref:System.Object), this functionality is automatically provided to your custom classes or structures.</span></span> <span data-ttu-id="92cdf-168">不過，預設的 [ToString](xref:System.Object.ToString) 方法提供的功能有限：它雖然可以識別類型，但無法提供類型執行個體的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="92cdf-168">However, the functionality offered by the default [ToString](xref:System.Object.ToString) method, is limited: Although it identifies the type, it fails to provide any information about an instance of the type.</span></span> <span data-ttu-id="92cdf-169">若要提供物件的字串表示來表達該物件的相關資訊，您必須覆寫 [ToString](xref:System.Object.ToString) 方法。</span><span class="sxs-lookup"><span data-stu-id="92cdf-169">To provide a string representation of an object that provides information about that object, you must override the [ToString](xref:System.Object.ToString) method.</span></span>

> [!NOTE]
> <span data-ttu-id="92cdf-170">結構會繼承自 [ValueType](xref:System.ValueType)，而後者又會衍生自 [Object](xref:System.Object)。</span><span class="sxs-lookup"><span data-stu-id="92cdf-170">Structures inherit from [ValueType](xref:System.ValueType), which in turn is derived from [Object](xref:System.Object).</span></span> <span data-ttu-id="92cdf-171">雖然 [ValueType](xref:System.ValueType) 會覆寫 [Object.ToString](xref:System.Object.ToString)，但實作方法是相同的。</span><span class="sxs-lookup"><span data-stu-id="92cdf-171">Although [ValueType](xref:System.ValueType) overrides [Object.ToString](xref:System.Object.ToString), its implementation is identical.</span></span>

## <a name="overriding-the-tostring-method"></a><span data-ttu-id="92cdf-172">覆寫 ToString 方法</span><span class="sxs-lookup"><span data-stu-id="92cdf-172">Overriding the ToString method</span></span>

<span data-ttu-id="92cdf-173">顯示類型的名稱通常用途不大，亦無法讓您類型的使用者藉以區分不同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="92cdf-173">Displaying the name of a type is often of limited use and does not allow consumers of your types to differentiate one instance from another.</span></span> <span data-ttu-id="92cdf-174">不過，您可以覆寫 [ToString](xref:System.Object.ToString) 方法，以更實用的方式表示物件的值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-174">However, you can override the [ToString](xref:System.Object.ToString) method to provide a more useful representation of an object’s value.</span></span> <span data-ttu-id="92cdf-175">下列範例定義 `Temperature` 物件，並覆寫其 [ToString](xref:System.Object.ToString) 方法來顯示攝氏溫度。</span><span class="sxs-lookup"><span data-stu-id="92cdf-175">The following example defines a `Temperature` object and overrides its [ToString](xref:System.Object.ToString) method to display the temperature in degrees Celsius.</span></span>

```csharp
using System;

public class Temperature
{
   private decimal temp;

   public Temperature(decimal temperature)
   {
      this.temp = temperature;   
   }

   public override string ToString()
   {
      return this.temp.ToString("N1") + "°C";
   }
}

public class Example
{
   public static void Main()
   {
      Temperature currentTemperature = new Temperature(23.6m);
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString());
   }
}
// The example displays the following output:
//       The current temperature is 23.6°C.
```

```vb
Public Class Temperature
   Private temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.temp = temperature
   End Sub

   Public Overrides Function ToString() As String
      Return Me.temp.ToString("N1") + "°C"   
   End Function
End Class

Module Example
   Public Sub Main()
      Dim currentTemperature As New Temperature(23.6d)
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString())
   End Sub
End Module
' The example displays the following output:
'       The current temperature is 23.6°C.
```

<span data-ttu-id="92cdf-176">在 .NET 中，每個基本實值型別的 [ToString](xref:System.Object.ToString) 方法都已經過覆寫來顯示物件的值，而非物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="92cdf-176">In .NET, the [ToString](xref:System.Object.ToString) method of each primitive value type has been overridden to display the object’s value instead of its name.</span></span> <span data-ttu-id="92cdf-177">下表顯示各基本類型如何覆寫 ToString 方法。</span><span class="sxs-lookup"><span data-stu-id="92cdf-177">The following table shows the override for each primitive type.</span></span> <span data-ttu-id="92cdf-178">請注意，大部分經過覆寫的方法都會呼叫 [ToString](xref:System.Object.ToString) 方法的另一個多載，並且將 "G" 格式規範 (此規範定義此類型的一般格式) 和 [IFormatProvider](xref:System.IFormatProvider) 物件 (此物件表示目前文化特性) 傳遞至這個多載。</span><span class="sxs-lookup"><span data-stu-id="92cdf-178">Note that most of the overridden methods call another overload of the [ToString](xref:System.Object.ToString) method and pass it the "G" format specifier, which defines the general format for its type, and an [IFormatProvider](xref:System.IFormatProvider) object that represents the current culture.</span></span>

<span data-ttu-id="92cdf-179">類型</span><span class="sxs-lookup"><span data-stu-id="92cdf-179">Type</span></span> | <span data-ttu-id="92cdf-180">ToString 覆寫</span><span class="sxs-lookup"><span data-stu-id="92cdf-180">ToString override</span></span>
---- | -----------------
[<span data-ttu-id="92cdf-181">布林值</span><span class="sxs-lookup"><span data-stu-id="92cdf-181">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="92cdf-182">傳回 [Boolean.TrueString](xref:System.Boolean.TrueString) 或 [Boolean.FalseString](xref:System.Boolean.FalseString)。</span><span class="sxs-lookup"><span data-stu-id="92cdf-182">Returns either [Boolean.TrueString](xref:System.Boolean.TrueString) or [Boolean.FalseString](xref:System.Boolean.FalseString).</span></span>
[<span data-ttu-id="92cdf-183">Byte</span><span class="sxs-lookup"><span data-stu-id="92cdf-183">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="92cdf-184">呼叫 `Byte.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [Byte](xref:System.Byte) 值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-184">Calls `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Byte](xref:System.Byte) value for the current culture.</span></span>
[<span data-ttu-id="92cdf-185">Char</span><span class="sxs-lookup"><span data-stu-id="92cdf-185">Char</span></span>](xref:System.Char) | <span data-ttu-id="92cdf-186">以字串形式傳回字元。</span><span class="sxs-lookup"><span data-stu-id="92cdf-186">Returns the character as a string.</span></span>
[<span data-ttu-id="92cdf-187">DateTime</span><span class="sxs-lookup"><span data-stu-id="92cdf-187">DateTime</span></span>](xref:System.DateTime) | <span data-ttu-id="92cdf-188">呼叫 `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)`，以根據對目前的文化特性來格式化日期和時間值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-188">Calls `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` to format the date and time value for the current culture.</span></span> 
[<span data-ttu-id="92cdf-189">Decimal</span><span class="sxs-lookup"><span data-stu-id="92cdf-189">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="92cdf-190">呼叫 `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [Decimal](xref:System.Decimal) 值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-190">Calls `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Decimal](xref:System.Decimal) value for the current culture.</span></span>
[<span data-ttu-id="92cdf-191">Double</span><span class="sxs-lookup"><span data-stu-id="92cdf-191">Double</span></span>](xref:System.Double) | <span data-ttu-id="92cdf-192">呼叫 `Double.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [Double](xref:System.Double) 值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-192">Calls `Double.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Double](xref:System.Double) value for the current culture.</span></span>
[<span data-ttu-id="92cdf-193">Int16</span><span class="sxs-lookup"><span data-stu-id="92cdf-193">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="92cdf-194">呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [Int16](xref:System.Int16) 值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-194">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Int16](xref:System.Int16) value for the current culture.</span></span>
[<span data-ttu-id="92cdf-195">Int32</span><span class="sxs-lookup"><span data-stu-id="92cdf-195">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="92cdf-196">呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [Int32](xref:System.Int32) 值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-196">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Int32](xref:System.Int32) value for the current culture.</span></span>
[<span data-ttu-id="92cdf-197">Int64</span><span class="sxs-lookup"><span data-stu-id="92cdf-197">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="92cdf-198">呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [Int64](xref:System.Int64) 值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-198">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Int64](xref:System.Int64) value for the current culture.</span></span>
[<span data-ttu-id="92cdf-199">SByte</span><span class="sxs-lookup"><span data-stu-id="92cdf-199">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="92cdf-200">呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [SByte](xref:System.SByte)</span><span class="sxs-lookup"><span data-stu-id="92cdf-200">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [SByte](xref:System.SByte)</span></span> | <span data-ttu-id="92cdf-201">值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-201">value for the current culture.</span></span>
[<span data-ttu-id="92cdf-202">Single</span><span class="sxs-lookup"><span data-stu-id="92cdf-202">Single</span></span>](xref:System.Single) | <span data-ttu-id="92cdf-203">呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [Single](xref:System.Single) 值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-203">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Single](xref:System.Single) value for the current culture.</span></span>
[<span data-ttu-id="92cdf-204">UInt32</span><span class="sxs-lookup"><span data-stu-id="92cdf-204">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="92cdf-205">呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [UInt32](xref:System.UInt32) 值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-205">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [UInt32](xref:System.UInt32)value for the current culture.</span></span>
[<span data-ttu-id="92cdf-206">UInt32</span><span class="sxs-lookup"><span data-stu-id="92cdf-206">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="92cdf-207">呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [UInt32](xref:System.UInt32) 值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-207">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [UInt32](xref:System.UInt32) value for the current culture.</span></span>
[<span data-ttu-id="92cdf-208">UInt64</span><span class="sxs-lookup"><span data-stu-id="92cdf-208">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="92cdf-209">呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [UInt64](xref:System.UInt64) 值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-209">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [UInt64](xref:System.UInt64)  value for the current culture.</span></span>

## <a name="the-tostring-method-and-format-strings"></a><span data-ttu-id="92cdf-210">ToString 方法及格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-210">The ToString method and format strings</span></span>

<span data-ttu-id="92cdf-211">當物件只有單一字串表示時，使用預設 [ToString](xref:System.Object.ToString) 方法或覆寫 [ToString](xref:System.Object.ToString) 都沒有問題。</span><span class="sxs-lookup"><span data-stu-id="92cdf-211">Relying on the default [ToString](xref:System.Object.ToString) method or overriding [ToString](xref:System.Object.ToString) is appropriate when an object has a single string representation.</span></span> <span data-ttu-id="92cdf-212">不過，物件的值通常有多種表示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-212">However, the value of an object often has multiple representations.</span></span> <span data-ttu-id="92cdf-213">例如，溫度可以用華氏、攝氏或開氏溫度表示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-213">For example, a temperature can be expressed in degrees Fahrenheit, degrees Celsius, or kelvins.</span></span> <span data-ttu-id="92cdf-214">同樣地，整數值 10 可以用許多方式表示，包括 10、10.0、1.0e01 或 $10.00。</span><span class="sxs-lookup"><span data-stu-id="92cdf-214">Similarly, the integer value 10 can be represented in numerous ways, including 10, 10.0, 1.0e01, or $10.00.</span></span>

<span data-ttu-id="92cdf-215">為了讓單一值可以具有多種字串表示，.NET 使用格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-215">To enable a single value to have multiple string representations, .NET uses format strings.</span></span> <span data-ttu-id="92cdf-216">格式字串是包含一個或多個預先定義之格式規範的字串，這個字串是單一字元或字元群組，用於定義 [ToString](xref:System.Object.ToString) 方法應採用的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="92cdf-216">A format string is a string that contains one or more predefined format specifiers, which are single characters or groups of characters that define how the [ToString](xref:System.Object.ToString) method should format its output.</span></span> <span data-ttu-id="92cdf-217">然後，格式字串會當做參數傳遞至物件的 [ToString](xref:System.Object.ToString) 方法，以決定如何呈現該物件值的字串表示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-217">The format string is then passed as a parameter to the object's [ToString](xref:System.Object.ToString) method and determines how the string representation of that object's value should appear.</span></span>

<span data-ttu-id="92cdf-218">.NET 中所有的數值類型、日期和時間類型，以及列舉類型，都支援一組預先定義的格式規範。</span><span class="sxs-lookup"><span data-stu-id="92cdf-218">All numeric types, date and time types, and enumeration types in .NET support a predefined set of format specifiers.</span></span> <span data-ttu-id="92cdf-219">您也可以利用格式字串定義多種字串表示給您應用程式中定義的資料類型。</span><span class="sxs-lookup"><span data-stu-id="92cdf-219">You can also use format strings to define multiple string representations of your application-defined data types.</span></span>

### <a name="standard-format-strings"></a><span data-ttu-id="92cdf-220">標準格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-220">Standard format strings</span></span>

<span data-ttu-id="92cdf-221">標準格式字串包含單一格式規範 (一個字母字元，定義套用此規範之物件的字串表示) 和選擇性的精確度規範 (這個規範影響結果字串中顯示的位數)。</span><span class="sxs-lookup"><span data-stu-id="92cdf-221">A standard format string contains a single format specifier, which is an alphabetic character that defines the string representation of the object to which it is applied, along with an optional precision specifier that affects how many digits are displayed in the result string.</span></span> <span data-ttu-id="92cdf-222">如果省略或不支援精確度規範，則標準格式規範與標準格式字串無異。</span><span class="sxs-lookup"><span data-stu-id="92cdf-222">If the precision specifier is omitted or is not supported, a standard format specifier is equivalent to a standard format string.</span></span> 

<span data-ttu-id="92cdf-223">.NET 定義一組適用於所有數值類型、所有日期和時間類型，以及所有列舉類型的標準格式規範。</span><span class="sxs-lookup"><span data-stu-id="92cdf-223">.NET defines a set of standard format specifiers for all numeric types, all date and time types, and all enumeration types.</span></span> <span data-ttu-id="92cdf-224">例如，這些分類每個都支援 "G" 標準格式規範 (這個規範定義該類型之值的一般字串表示)。</span><span class="sxs-lookup"><span data-stu-id="92cdf-224">For example, each of these categories supports a "G" standard format specifier, which defines a general string representation of a value of that type.</span></span>

<span data-ttu-id="92cdf-225">列舉類型的標準格式字串直接控制了值的字串表示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-225">Standard format strings for enumeration types directly control the string representation of a value.</span></span> <span data-ttu-id="92cdf-226">傳遞給列舉值之 [ToString](xref:System.Object.ToString) 方法的格式字串決定了該值是以其字串名稱 ("G" 和 "F" 格式規範)、基礎整數值 ("D" 格式規範)，還是十六進位值 ("X" 格式規範) 來顯示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-226">The format strings passed to an enumeration value’s [ToString](xref:System.Object.ToString) method determine whether the value is displayed using its string name (the "G" and "F" format specifiers), its underlying integral value (the "D" format specifier), or its hexadecimal value (the "X" format specifier).</span></span> <span data-ttu-id="92cdf-227">下列範例示範如何使用標準格式字串來格式化 [DayOfWeek](xref:System.DayOfWeek) 列舉值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-227">The following example illustrates the use of standard format strings to format a [DayOfWeek](xref:System.DayOfWeek) enumeration value.</span></span> 

```csharp
DayOfWeek thisDay = DayOfWeek.Monday;
string[] formatStrings = {"G", "F", "D", "X"};

foreach (string formatString in formatStrings)
   Console.WriteLine(thisDay.ToString(formatString));
// The example displays the following output:
//       Monday
//       Monday
//       1
//       00000001
```

```vb
Dim thisDay As DayOfWeek = DayOfWeek.Monday
Dim formatStrings() As String = {"G", "F", "D", "X"}

For Each formatString As String In formatStrings
   Console.WriteLine(thisDay.ToString(formatString))
Next
' The example displays the following output:
'       Monday
'       Monday
'       1
'       00000001
```

<span data-ttu-id="92cdf-228">如需列舉格式字串的資訊，請參閱[列舉格式字串](enumeration-format.md)。</span><span class="sxs-lookup"><span data-stu-id="92cdf-228">For information about enumeration format strings, see [Enumeration format strings](enumeration-format.md).</span></span>

<span data-ttu-id="92cdf-229">數值類型的標準格式字串定義出的結果字串之確切外觀通常是由一個或多個屬性值所控制。</span><span class="sxs-lookup"><span data-stu-id="92cdf-229">Standard format strings for numeric types usually define a result string whose precise appearance is controlled by one or more property values.</span></span> <span data-ttu-id="92cdf-230">例如，"C" 格式規範會將數字格式化為貨幣值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-230">For example, the "C" format specifier formats a number as a currency value.</span></span> <span data-ttu-id="92cdf-231">當您將 "C" 格式規範作為唯一參數來呼叫 [ToString](xref:System.Object.ToString) 方法時，會使用目前文化特性之 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件中的下列屬性值來定義數值的字串表示：</span><span class="sxs-lookup"><span data-stu-id="92cdf-231">When you call the [ToString](xref:System.Object.ToString) method with the "C" format specifier as the only parameter, the following property values from the current culture’s [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object are used to define the string representation of the numeric value:</span></span>

* <span data-ttu-id="92cdf-232">[CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) 屬性，指定目前文化特性的貨幣符號。</span><span class="sxs-lookup"><span data-stu-id="92cdf-232">The [CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) property, which specifies the current culture’s currency symbol.</span></span>

* <span data-ttu-id="92cdf-233">[CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) 或 [CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern) 屬性，這個屬性傳回的整數會決定：</span><span class="sxs-lookup"><span data-stu-id="92cdf-233">The [CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) or [CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern) property, which returns an integer that determines the following:</span></span> 

    * <span data-ttu-id="92cdf-234">貨幣符號的位置。</span><span class="sxs-lookup"><span data-stu-id="92cdf-234">The placement of the currency symbol.</span></span>
    
    * <span data-ttu-id="92cdf-235">負值是以開頭負號、結尾負號還是括號來表示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-235">Whether negative values are indicated by a leading negative sign, a trailing negative sign, or parentheses.</span></span>
    
    * <span data-ttu-id="92cdf-236">數值和貨幣符號之間是否顯示一個空格。</span><span class="sxs-lookup"><span data-stu-id="92cdf-236">Whether a space appears between the numeric value and the currency symbol.</span></span>
    
* <span data-ttu-id="92cdf-237">[CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) 屬性，定義結果字串中的小數位數。</span><span class="sxs-lookup"><span data-stu-id="92cdf-237">The [CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) property, which defines the number of fractional digits in the result string.</span></span>

* <span data-ttu-id="92cdf-238">[CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) 屬性，定義結果字串中的十進位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="92cdf-238">The [CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) property, which defines the decimal separator symbol in the result string.</span></span>

* <span data-ttu-id="92cdf-239">[CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) 屬性，定義群組分隔符號。</span><span class="sxs-lookup"><span data-stu-id="92cdf-239">The [CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) property, which defines the group separator symbol.</span></span>

* <span data-ttu-id="92cdf-240">[CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes) 屬性，定義小數點左邊每個群組的位數。</span><span class="sxs-lookup"><span data-stu-id="92cdf-240">The [CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes) property, which defines the number of digits in each group to the left of the decimal.</span></span>

* <span data-ttu-id="92cdf-241">[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) 屬性，決定當不使用括號來表示負值時，要在結果字串中使用的負號。</span><span class="sxs-lookup"><span data-stu-id="92cdf-241">The [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) property, which determines the negative sign used in the result string if parentheses are not used to indicate negative values.</span></span>

<span data-ttu-id="92cdf-242">此外，數值格式字串也可以包含精確度規範。</span><span class="sxs-lookup"><span data-stu-id="92cdf-242">In addition, numeric format strings may include a precision specifier.</span></span> <span data-ttu-id="92cdf-243">這個規範的意義視搭配使用的格式字串而定，但通常是表示結果字串中應該顯示的總位數或小數位數。</span><span class="sxs-lookup"><span data-stu-id="92cdf-243">The meaning of this specifier depends on the format string with which it is used, but it typically indicates either the total number of digits or the number of fractional digits that should appear in the result string.</span></span> <span data-ttu-id="92cdf-244">例如，下列範例會使用 "X4" 標準數值字串和精確度規範，建立具有四個十六進位數字的字串值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-244">For example, the following example uses the "X4" standard numeric string and a precision specifier to create a string value that has four hexadecimal digits.</span></span>

```csharp
byte[] byteValues = { 12, 163, 255 };
foreach (byte byteValue in byteValues)
   Console.WriteLine(byteValue.ToString("X4"));
// The example displays the following output:
//       000C
//       00A3
//       00FF
```

```vb
Dim byteValues() As Byte = { 12, 163, 255 }
For Each byteValue As Byte In byteValues
   Console.WriteLine(byteValue.ToString("X4"))
Next
' The example displays the following output:
'       000C
'       00A3
'       00FF
```

<span data-ttu-id="92cdf-245">如需標準數值格式字串的詳細資訊，請參閱[標準數值格式字串](standard-numeric.md)。</span><span class="sxs-lookup"><span data-stu-id="92cdf-245">For more information about standard numeric formatting strings, see [Standard numeric format strings](standard-numeric.md).</span></span> 

<span data-ttu-id="92cdf-246">日期和時間值的標準格式字串是特定 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 類別所儲存之自訂格式字串的別名。</span><span class="sxs-lookup"><span data-stu-id="92cdf-246">Standard format strings for date and time values are aliases for custom format strings stored by a particular [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) class.</span></span> <span data-ttu-id="92cdf-247">例如，以 "D" 格式規範來呼叫日期和時間值的 [ToString](xref:System.Object.ToString) 方法，將會使用目前文化特性之 [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) 屬性中所儲存的自訂格式字串來顯示日期和時間</span><span class="sxs-lookup"><span data-stu-id="92cdf-247">For example, calling the [ToString](xref:System.Object.ToString) method of a date and time value with the "D" format specifier displays the date and time by using the custom format string stored in the current culture’s [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) property.</span></span> <span data-ttu-id="92cdf-248">(如需自訂格式字串的詳細資訊，請參閱[自訂格式字串](#custom-format-strings)一節)。下列範例示範這種關聯性。</span><span class="sxs-lookup"><span data-stu-id="92cdf-248">(For more information about custom format strings, see the [Custom format strings](#custom-format-strings) section.) The following example illustrates this relationship.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      DateTime date1 = new DateTime(2017, 6, 30);
      Console.WriteLine("D Format Specifier:     {0:D}", date1);
      string longPattern = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern;
      Console.WriteLine("'{0}' custom format string:     {1}", 
                        longPattern, date1.ToString(longPattern));
   }
}
// The example displays the following output when run on a system whose
// current culture is en-US:
//    D Format Specifier:     Tuesday, June 30, 2017
//    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2017
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim date1 As Date = #6/30/2009#
      Console.WriteLine("D Format Specifier:     {0:D}", date1)
      Dim longPattern As String = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern
      Console.WriteLine("'{0}' custom format string:     {1}", _
                        longPattern, date1.ToString(longPattern))
   End Sub
End Module
' The example displays the following output when run on a system whose
' current culture is en-US:
'    D Format Specifier:     Tuesday, June 30, 2009
'    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2009
```

<span data-ttu-id="92cdf-249">如需標準日期與時間格式字串的詳細資訊，請參閱[標準日期與時間格式字串](standard-datetime.md)。</span><span class="sxs-lookup"><span data-stu-id="92cdf-249">For more information about standard date and time format strings, see [Standard date and time format strings](standard-datetime.md).</span></span>

<span data-ttu-id="92cdf-250">對於應用程式定義的物件，您也可以使用標準格式字串來定義由該物件的 `ToString(String)` 方法所產生的字串表示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-250">You can also use standard format strings to define the string representation of an application-defined object that is produced by the object’s `ToString(String)` method.</span></span> <span data-ttu-id="92cdf-251">您可以定義您的物件所支援的特定標準格式規範，並且決定這項規範是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="92cdf-251">You can define the specific standard format specifiers that your object supports, and you can determine whether they are case-sensitive or case-insensitive.</span></span> <span data-ttu-id="92cdf-252">您對 `ToString(String)` 方法的實作應該要能支援：</span><span class="sxs-lookup"><span data-stu-id="92cdf-252">Your implementation of the `ToString(String)` method should support the following:</span></span>

* <span data-ttu-id="92cdf-253">"G" 格式規範，表示物件的慣用或通用格式。</span><span class="sxs-lookup"><span data-stu-id="92cdf-253">A "G" format specifier that represents a customary or common format of the object.</span></span> <span data-ttu-id="92cdf-254">您物件的 `ToString` 方法的無參數多載應該要呼叫這個方法的 `ToString(String)` 多載，並且將 "G" 標準格式字串傳遞給這個方法。</span><span class="sxs-lookup"><span data-stu-id="92cdf-254">The parameterless overload of your object's `ToString` method should call its `ToString(String)` overload and pass it the "G" standard format string.</span></span>

* <span data-ttu-id="92cdf-255">支援等於 null 參考的格式規範。</span><span class="sxs-lookup"><span data-stu-id="92cdf-255">Support for a format specifier that is equal to a null reference.</span></span> <span data-ttu-id="92cdf-256">等於 null 參考的格式規範應該要視為相當於 "G" 格式規範。</span><span class="sxs-lookup"><span data-stu-id="92cdf-256">A format specifier that is equal to a null reference should be considered equivalent to the "G" format specifier.</span></span>

<span data-ttu-id="92cdf-257">例如，`Temperature` 類別可以在內部以攝氏儲存溫度，並透過格式規範以攝氏、華氏和開氏溫度來表示 `Temperature` 物件的值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-257">For example, a `Temperature` class can internally store the temperature in degrees Celsius and use format specifiers to represent the value of the `Temperature` object in degrees Celsius, degrees Fahrenheit, and kelvins.</span></span> <span data-ttu-id="92cdf-258">下列範例提供一個實例。</span><span class="sxs-lookup"><span data-stu-id="92cdf-258">The following example provides an illustration.</span></span>

```csharp
using System;

public class Temperature
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round(((decimal) (this.m_Temp * 9 / 5 + 32)), 2); }
   }

   public override string ToString()
   {
      return this.ToString("C");
   }

   public string ToString(string format)
   {  
      // Handle null or empty string.
      if (String.IsNullOrEmpty(format)) format = "C";
      // Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant();      

      // Convert temperature to Fahrenheit and return string.
      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2") + " °F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2") + " K";
         // return temperature in Celsius.
         case "G":
         case "C":
            return this.Celsius.ToString("N2") + " °C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}

public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(0m);
      Console.WriteLine(temp1.ToString());
      Console.WriteLine(temp1.ToString("G"));
      Console.WriteLine(temp1.ToString("C"));
      Console.WriteLine(temp1.ToString("F"));
      Console.WriteLine(temp1.ToString("K"));

      Temperature temp2 = new Temperature(-40m);
      Console.WriteLine(temp2.ToString());
      Console.WriteLine(temp2.ToString("G"));
      Console.WriteLine(temp2.ToString("C"));
      Console.WriteLine(temp2.ToString("F"));
      Console.WriteLine(temp2.ToString("K"));

      Temperature temp3 = new Temperature(16m);
      Console.WriteLine(temp3.ToString());
      Console.WriteLine(temp3.ToString("G"));
      Console.WriteLine(temp3.ToString("C"));
      Console.WriteLine(temp3.ToString("F"));
      Console.WriteLine(temp3.ToString("K"));

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3));
   }
}
// The example displays the following output:
//       0.00 °C
//       0.00 °C
//       0.00 °C
//       32.00 °F
//       273.15 K
//       -40.00 °C
//       -40.00 °C
//       -40.00 °C
//       -40.00 °F
//       233.15 K
//       16.00 °C
//       16.00 °C
//       16.00 °C
//       60.80 °F
//       289.15 K
//       The temperature is now 16.00 °C.
```

```vb
Public Class Temperature
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("C")
   End Function

   Public Overloads Function ToString(format As String) As String  
      ' Handle null or empty string.
      If String.IsNullOrEmpty(format) Then format = "C"
      ' Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant()      

      Select Case format
         Case "F"
           ' Convert temperature to Fahrenheit and return string.
            Return Me.Fahrenheit.ToString("N2") & " °F"
         Case "K"
            ' Convert temperature to Kelvin and return string.
            Return Me.Kelvin.ToString("N2") & " K"
         Case "C", "G"
            ' Return temperature in Celsius.
            Return Me.Celsius.ToString("N2") & " °C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(0d)
      Console.WriteLine(temp1.ToString())
      Console.WriteLine(temp1.ToString("G"))
      Console.WriteLine(temp1.ToString("C"))
      Console.WriteLine(temp1.ToString("F"))
      Console.WriteLine(temp1.ToString("K"))

      Dim temp2 As New Temperature(-40d)
      Console.WriteLine(temp2.ToString())
      Console.WriteLine(temp2.ToString("G"))
      Console.WriteLine(temp2.ToString("C"))
      Console.WriteLine(temp2.ToString("F"))
      Console.WriteLine(temp2.ToString("K"))

      Dim temp3 As New Temperature(16d)
      Console.WriteLine(temp3.ToString())
      Console.WriteLine(temp3.ToString("G"))
      Console.WriteLine(temp3.ToString("C"))
      Console.WriteLine(temp3.ToString("F"))
      Console.WriteLine(temp3.ToString("K"))

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3))
   End Sub
End Module
' The example displays the following output:
'       0.00 °C
'       0.00 °C
'       0.00 °C
'       32.00 °F
'       273.15 K
'       -40.00 °C
'       -40.00 °C
'       -40.00 °C
'       -40.00 °F
'       233.15 K
'       16.00 °C
'       16.00 °C
'       16.00 °C
'       60.80 °F
'       289.15 K
'       The temperature is now 16.00 °C.
```

### <a name="custom-format-strings"></a><span data-ttu-id="92cdf-259">自訂格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-259">Custom format strings</span></span>

<span data-ttu-id="92cdf-260">除了標準格式字串，.NET 也為數值以及日期和時間值定義了自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-260">In addition to the standard format strings, .NET defines custom format strings for both numeric values and date and time values.</span></span> <span data-ttu-id="92cdf-261">自訂格式字串由一個或多個自訂格式規範組成，這些規範定義了值的字串表示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-261">A custom format string consists of one or more custom format specifiers that define the string representation of a value.</span></span> <span data-ttu-id="92cdf-262">例如，自訂日期和時間格式字串 "yyyy/mm/dd hh:mm:ss.ffff t zzz" 會將日期轉換為其字串表示，以 en-US 文化特性而言為 "2008/11/15 07:45:00.0000 P -08:00" 形式。</span><span class="sxs-lookup"><span data-stu-id="92cdf-262">For example, the custom date and time format string "yyyy/mm/dd hh:mm:ss.ffff t zzz" converts a date to its string representation in the form "2008/11/15 07:45:00.0000 P -08:00" for the en-US culture.</span></span> <span data-ttu-id="92cdf-263">同樣地，自訂格式字串 "0000" 會將整數值 12 轉換為 "0012"。</span><span class="sxs-lookup"><span data-stu-id="92cdf-263">Similarly, the custom format string "0000" converts the integer value 12 to "0012".</span></span> <span data-ttu-id="92cdf-264">如需完整的自訂格式字串清單，請參閱[自訂日期與時間格式字串](custom-datetime.md)及[自訂數值格式字串](custom-numeric.md)。</span><span class="sxs-lookup"><span data-stu-id="92cdf-264">For a complete list of custom format strings, see [Custom date and time format strings](custom-datetime.md) and [Custom numeric format strings](custom-numeric.md).</span></span>

<span data-ttu-id="92cdf-265">如果格式字串由單一自訂格式規範組成，則應該在格式規範前面加上百分比 (%) 符號，以避免與標準格式規範產生混淆。</span><span class="sxs-lookup"><span data-stu-id="92cdf-265">If a format string consists of a single custom format specifier, the format specifier should be preceded by the percent (%) symbol to avoid confusion with a standard format specifier.</span></span> <span data-ttu-id="92cdf-266">下列範例會使用 "M" 自訂格式規範來顯示特定日期的一位數或兩位數月份。</span><span class="sxs-lookup"><span data-stu-id="92cdf-266">The following example uses the "M" custom format specifier to display a one-digit or two-digit number of the month of a particular date.</span></span>

```csharp
DateTime date1 = new DateTime(2009, 9, 8);
Console.WriteLine(date1.ToString("%M"));       
// Displays 9
```

```vb
Dim date1 As Date = #09/08/2009#
Console.WriteLine(date1.ToString("%M"))      ' Displays 9
```

<span data-ttu-id="92cdf-267">日期和時間值的許多標準格式字串都是自訂格式字串 (這些自訂格式字串由 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件的屬性所定義) 的別名。</span><span class="sxs-lookup"><span data-stu-id="92cdf-267">Many standard format strings for date and time values are aliases for custom format strings that are defined by properties of the [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object.</span></span> <span data-ttu-id="92cdf-268">自訂格式字串也提供極大的彈性，來提供應用程式定義的數值或日期和時間值格式。</span><span class="sxs-lookup"><span data-stu-id="92cdf-268">Custom format strings also offer considerable flexibility in providing application-defined formatting for numeric values or date and time values.</span></span> <span data-ttu-id="92cdf-269">您可以將多個自訂格式規範結合成單一自訂格式字串，以自訂您的數值及日期和時間值結果字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-269">You can define your own custom result strings for both numeric values and date and time values by combining multiple custom format specifiers into a single custom format string.</span></span> <span data-ttu-id="92cdf-270">下列範例定義的自訂格式字串，會在月份名稱、日期和年後面顯示加上括號的星期。</span><span class="sxs-lookup"><span data-stu-id="92cdf-270">The following example defines a custom format string that displays the day of the week in parentheses after the month name, day, and year.</span></span>

```csharp
string customFormat = "MMMM dd, yyyy (dddd)";
DateTime date1 = new DateTime(2009, 8, 28);
Console.WriteLine(date1.ToString(customFormat));   
// The example displays the following output if run on a system
// whose language is English:
//       August 28, 2009 (Friday) 
```

```vb
Dim customFormat As String = "MMMM dd, yyyy (dddd)"
Dim date1 As Date = #8/28/2009#
Console.WriteLine(date1.ToString(customFormat))   
' The example displays the following output if run on a system
' whose language is English:
'       August 28, 2009 (Friday) 
```

<span data-ttu-id="92cdf-271">下列範例會定義自訂格式字串，該字串會將 [Int64](xref:System.Int64) 值顯示為標準的七位數美國電話號碼且包含其區碼。</span><span class="sxs-lookup"><span data-stu-id="92cdf-271">The following example defines a custom format string that displays an [Int64](xref:System.Int64) value as a standard, seven-digit U.S. telephone number along with its area code.</span></span> 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      long number = 8009999999;
      string fmt = "000-000-0000";
      Console.WriteLine(number.ToString(fmt));
   }
}
// The example displays the following output:
//        800-999-9999
```

```vb
Module Example
   Public Sub Main()
      Dim number As Long = 8009999999
      Dim fmt As String = "000-000-0000"
      Console.WriteLine(number.ToString(fmt))
   End Sub
End Module
' The example displays the following output:

' The example displays the following output:
'       800-999-9999
```

<span data-ttu-id="92cdf-272">雖然標準格式字串通常能夠為應用程式定義的類型解決大部分的格式需求，但您也可以定義自訂格式規範來格式化您的類型。</span><span class="sxs-lookup"><span data-stu-id="92cdf-272">Although standard format strings can generally handle most of the formatting needs for your application-defined types, you may also define custom format specifiers to format your types.</span></span> 

### <a name="format-strings-and-net-types"></a><span data-ttu-id="92cdf-273">格式字串與 .NET 類型</span><span class="sxs-lookup"><span data-stu-id="92cdf-273">Format strings and .NET types</span></span>

<span data-ttu-id="92cdf-274">所有數值類型 (也就是 [Byte](xref:System.Byte)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte)、[Single](xref:System.Single)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64) 和 [BigInteger](xref:System.Numerics.BigInteger) 類型)，以及 [DateTime](xref:System.DateTime)、[DateTimeOffset](xref:System.DateTimeOffset)、[TimeSpan](xref:System.TimeSpan)、[Guid](xref:System.Guid) 和所有列舉類型，都支援以格式字串進行格式化。</span><span class="sxs-lookup"><span data-stu-id="92cdf-274">All numeric types (that is, the [Byte](xref:System.Byte), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64), and [BigInteger](xref:System.Numerics.BigInteger) types), as well as the [DateTime](xref:System.DateTime), [DateTimeOffset](xref:System.DateTimeOffset), [TimeSpan](xref:System.TimeSpan), [Guid](xref:System.Guid), and all enumeration types, support formatting with format strings.</span></span> <span data-ttu-id="92cdf-275">如需每個類型所支援特定格式字串的資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="92cdf-275">For information on the specific format strings supported by each type, see the following topics:</span></span> 

<span data-ttu-id="92cdf-276">標題</span><span class="sxs-lookup"><span data-stu-id="92cdf-276">Title</span></span> | <span data-ttu-id="92cdf-277">定義</span><span class="sxs-lookup"><span data-stu-id="92cdf-277">Definition</span></span>
----- | ----------
[<span data-ttu-id="92cdf-278">標準數值格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-278">Standard numeric format strings</span></span>](standard-numeric.md) | <span data-ttu-id="92cdf-279">說明建立數值常用之字串表示的標準格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-279">Describes standard format strings that create commonly used string representations of numeric values.</span></span> 
[<span data-ttu-id="92cdf-280">自訂數值格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-280">Custom numeric format strings</span></span>](custom-numeric.md) | <span data-ttu-id="92cdf-281">說明建立應用程式專屬數值格式的自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-281">Describes custom format strings that create application-specific formats for numeric values.</span></span>
[<span data-ttu-id="92cdf-282">標準日期與時間格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-282">Standard date and time format strings</span></span>](standard-datetime.md) | <span data-ttu-id="92cdf-283">說明建立 [DateTime](xref:System.DateTime) 值之常用字串表示的標準格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-283">Describes standard format strings that create commonly used string representations of [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="92cdf-284">自訂日期與時間格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-284">Custom date and time format strings</span></span>](custom-datetime.md) | <span data-ttu-id="92cdf-285">說明為 [DateTime](xref:System.DateTime)值建立應用程式專屬格式的自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-285">Describes custom format strings that create application-specific formats for [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="92cdf-286">標準 TimeSpan 格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-286">Standard TimeSpan format Strings</span></span>](standard-timespan.md) | <span data-ttu-id="92cdf-287">說明建立時間間隔之常用字串表示的標準格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-287">Describes standard format strings that create commonly used string representations of time intervals.</span></span>
[<span data-ttu-id="92cdf-288">自訂 TimeSpan 格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-288">Custom TimeSpan format strings</span></span>](custom-timespan.md) | <span data-ttu-id="92cdf-289">說明建立應用程式專屬數值格式的自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-289">Describes custom format strings that create application-specific formats for time intervals.</span></span>
[<span data-ttu-id="92cdf-290">列舉格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-290">Enumeration format strings</span></span>](enumeration-format.md) | <span data-ttu-id="92cdf-291">說明用來建立列舉值之字串表示的標準格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-291">Describes standard format strings that are used to create string representations of enumeration values.</span></span>
<span data-ttu-id="92cdf-292">[Guid.ToString(String)](xref:System.Guid.ToString(System.String))</span><span class="sxs-lookup"><span data-stu-id="92cdf-292">[Guid.ToString(String)](xref:System.Guid.ToString(System.String))</span></span> | <span data-ttu-id="92cdf-293">描述 [Guid](xref:System.Guid) 值的標準格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-293">Describes standard format strings for [Guid](xref:System.Guid) values.</span></span>

## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a><span data-ttu-id="92cdf-294">以格式提供者和 IFormatProvider 介面進行符合文化特性的格式化</span><span class="sxs-lookup"><span data-stu-id="92cdf-294">Culture-Sensitive Formatting with Format Providers and the IFormatProvider Interface</span></span>

<span data-ttu-id="92cdf-295">雖然格式規範可讓您自訂物件的格式，但如果要為物件產生有意義的字串表示，您通常還需要其他格式設定資訊。</span><span class="sxs-lookup"><span data-stu-id="92cdf-295">Although format specifiers let you customize the formatting of objects, producing a meaningful string representation of objects often requires additional formatting information.</span></span> <span data-ttu-id="92cdf-296">例如，如果要使用 "C" 標準格式字串或自訂格式字串 (例如 "$ #,#.00") 將數字格式化為貨幣值，您至少還需要有正確的貨幣符號、群組分隔符號和小數分隔符號的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="92cdf-296">For example, formatting a number as a currency value by using either the "C" standard format string or a custom format string such as "$ #,#.00" requires, at a minimum, information about the correct currency symbol, group separator, and decimal separator to be available to include in the formatted string.</span></span> <span data-ttu-id="92cdf-297">在 .NET 中，這項額外的格式資訊是透過 [IFormatProvider](xref:System.IFormatProvider) 介面取得，而這個介面會當做傳遞至數值類型以及日期和時間類型的 `ToString` 方法之一個或多個多載的參數來提供。</span><span class="sxs-lookup"><span data-stu-id="92cdf-297">In .NET, this additional formatting information is made available through the [IFormatProvider](xref:System.IFormatProvider) interface, which is provided as a parameter to one or more overloads of the `ToString` method of numeric types and date and time types.</span></span> <span data-ttu-id="92cdf-298">[IFormatProvider](xref:System.IFormatProvider) 實作會在 .NET 中用來支援文化特性專屬格式。</span><span class="sxs-lookup"><span data-stu-id="92cdf-298">[IFormatProvider](xref:System.IFormatProvider) implementations are used in .NET to support culture-specific formatting.</span></span> <span data-ttu-id="92cdf-299">下列範例示範以代表不同文化特性的三個 [IFormatProvider](xref:System.IFormatProvider) 物件進行格式化時，物件的字串表示會有什麼樣的變化。</span><span class="sxs-lookup"><span data-stu-id="92cdf-299">The following example illustrates how the string representation of an object changes when it is formatted with three [IFormatProvider](xref:System.IFormatProvider) objects that represent different cultures.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      decimal value = 1603.42m;
      Console.WriteLine(value.ToString("C3", new CultureInfo("en-US")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("fr-FR")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("de-DE")));
   }
}
// The example displays the following output:
//       $1,603.420
//       1 603,420 €
//       1.603,420 €
```

```vb
Imports System.Globalization

Public Module Example
   Public Sub Main()
      Dim value As Decimal = 1603.42d
      Console.WriteLine(value.ToString("C3", New CultureInfo("en-US")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("fr-FR")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("de-DE")))
   End Sub
End Module
' The example displays the following output:
'       $1,603.420
'       1 603,420 €
'       1.603,420 €
```

<span data-ttu-id="92cdf-300">[IFormatProvider](xref:System.IFormatProvider) 介面包含一個 [GetFormat(Type)](xref:System.IFormatProvider.GetFormat(System.Type)) 方法，這個方法具有單一參數來指定可提供格式設定資訊之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="92cdf-300">The [IFormatProvider](xref:System.IFormatProvider) interface includes one method, [GetFormat(Type)](xref:System.IFormatProvider.GetFormat(System.Type)), which has a single parameter that specifies the type of object that provides formatting information.</span></span> <span data-ttu-id="92cdf-301">如果這個方法可以提供該類型的物件，則會傳回該物件。</span><span class="sxs-lookup"><span data-stu-id="92cdf-301">If the method can provide an object of that type, it returns it.</span></span> <span data-ttu-id="92cdf-302">否則會傳回 null 參考。</span><span class="sxs-lookup"><span data-stu-id="92cdf-302">Otherwise, it returns a null reference.</span></span>

<span data-ttu-id="92cdf-303">[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 是一種回呼方法。</span><span class="sxs-lookup"><span data-stu-id="92cdf-303">[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) is a callback method.</span></span> <span data-ttu-id="92cdf-304">當您呼叫包含 [IFormatProvider](xref:System.IFormatProvider) 參數的 `ToString` 方法多載時，這個多載會呼叫該 [IFormatProvider](xref:System.IFormatProvider) 物件的 [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 方法。</span><span class="sxs-lookup"><span data-stu-id="92cdf-304">When you call a `ToString` method overload that includes an [IFormatProvider](xref:System.IFormatProvider) parameter, it calls the [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method of that [IFormatProvider](xref:System.IFormatProvider) object.</span></span> <span data-ttu-id="92cdf-305">[GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 方法負責將提供必要格式資訊的物件 (由其 *formatType* 參數指定)，傳回給 `ToString` 方法。</span><span class="sxs-lookup"><span data-stu-id="92cdf-305">The [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method is responsible for returning an object that provides the necessary formatting information, as specified by its *formatType* parameter, to the `ToString` method.</span></span> 

<span data-ttu-id="92cdf-306">有幾個格式化或字串轉換方法都包含 [IFormatProvider](xref:System.IFormatProvider) 類型的參數，但通常呼叫方法時，會忽略這個參數的值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-306">A number of formatting or string conversion methods include a parameter of type [IFormatProvider](xref:System.IFormatProvider), but in many cases the value of the parameter is ignored when the method is called.</span></span> <span data-ttu-id="92cdf-307">下表列出一些使用這個參數的格式化方法，以及這些方法傳遞至 [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 方法之 [Type](xref:System.Type) 物件的類型。</span><span class="sxs-lookup"><span data-stu-id="92cdf-307">The following table lists some of the formatting methods that use the parameter and the type of the [Type](xref:System.Type) object that they pass to the [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method.</span></span> 

<span data-ttu-id="92cdf-308">方法</span><span class="sxs-lookup"><span data-stu-id="92cdf-308">Method</span></span> | <span data-ttu-id="92cdf-309">*formatType* 參數的類型</span><span class="sxs-lookup"><span data-stu-id="92cdf-309">Type of *formatType* parameter</span></span>
------ | ------------------------------
<span data-ttu-id="92cdf-310">數字類型的 `ToString` 方法</span><span class="sxs-lookup"><span data-stu-id="92cdf-310">`ToString` method of numeric types</span></span> | [<span data-ttu-id="92cdf-311">System.Globalization.NumberFormatInfo</span><span class="sxs-lookup"><span data-stu-id="92cdf-311">System.Globalization.NumberFormatInfo</span></span>](xref:System.Globalization.NumberFormatInfo)
<span data-ttu-id="92cdf-312">日期和時間類型的 `ToString` 方法</span><span class="sxs-lookup"><span data-stu-id="92cdf-312">`ToString` method of date and time types</span></span> | [<span data-ttu-id="92cdf-313">System.Globalization.DateTimeFormatInfo</span><span class="sxs-lookup"><span data-stu-id="92cdf-313">System.Globalization.DateTimeFormatInfo</span></span>](xref:System.Globalization.DateTimeFormatInfo)
<span data-ttu-id="92cdf-314">[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="92cdf-314">[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))</span></span> | [<span data-ttu-id="92cdf-315">System.ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="92cdf-315">System.ICustomFormatter</span></span>](xref:System.ICustomFormatter)
<span data-ttu-id="92cdf-316">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="92cdf-316">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span></span> | [<span data-ttu-id="92cdf-317">System.ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="92cdf-317">System.ICustomFormatter</span></span>](xref:System.ICustomFormatter)

<span data-ttu-id="92cdf-318">.NET 提供三個實作 [IFormatProvider](xref:System.IFormatProvider) 的類別：</span><span class="sxs-lookup"><span data-stu-id="92cdf-318">.NET provides three classes that implement [IFormatProvider](xref:System.IFormatProvider):</span></span> 

* <span data-ttu-id="92cdf-319">[DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo)，這個類別提供特定文化特性之日期和時間值的格式資訊。</span><span class="sxs-lookup"><span data-stu-id="92cdf-319">[DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo), a class that provides formatting information for date and time values for a specific culture.</span></span> <span data-ttu-id="92cdf-320">它的 [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 實作會傳回本身的執行個體。</span><span class="sxs-lookup"><span data-stu-id="92cdf-320">Its [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) implementation returns an instance of itself.</span></span>

* <span data-ttu-id="92cdf-321">[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)，這個類別提供特定文化特性的數值格式資訊。</span><span class="sxs-lookup"><span data-stu-id="92cdf-321">[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo), a class that provides numeric formatting information for a specific culture.</span></span> <span data-ttu-id="92cdf-322">它的 [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 實作會傳回本身的執行個體。</span><span class="sxs-lookup"><span data-stu-id="92cdf-322">Its [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) implementation returns an instance of itself.</span></span>

* <span data-ttu-id="92cdf-323">[CultureInfo](xref:System.Globalization.CultureInfo)。</span><span class="sxs-lookup"><span data-stu-id="92cdf-323">[CultureInfo](xref:System.Globalization.CultureInfo).</span></span> <span data-ttu-id="92cdf-324">它的 [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 實作可以傳回 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件來提供數值格式資訊，或傳回 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件來提供日期和時間值的格式資訊。</span><span class="sxs-lookup"><span data-stu-id="92cdf-324">Its [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) implementation can return either a [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object to provide numeric formatting information or a [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object to provide formatting information for date and time values.</span></span> 

<span data-ttu-id="92cdf-325">您也可以實作自己的格式提供者來取代上述任何一個類別。</span><span class="sxs-lookup"><span data-stu-id="92cdf-325">You can also implement your own format provider to replace any one of these classes.</span></span> <span data-ttu-id="92cdf-326">不過，您實作的 `GetFormat` 方法如果必須提供格式設定資訊給 `ToString` 方法，則必須傳回上表所列之類型的物件。</span><span class="sxs-lookup"><span data-stu-id="92cdf-326">However, your implementation’s `GetFormat` method must return an object of the type listed in the previous table if it has to provide formatting information to the `ToString` method.</span></span>

### <a name="culture-sensitive-formatting-of-numeric-values"></a><span data-ttu-id="92cdf-327">區分文化特性的數值格式</span><span class="sxs-lookup"><span data-stu-id="92cdf-327">Culture-sensitive formatting of numeric values</span></span>

<span data-ttu-id="92cdf-328">根據預設，數值格式會區分文化特性。</span><span class="sxs-lookup"><span data-stu-id="92cdf-328">By default, the formatting of numeric values is culture-sensitive.</span></span> <span data-ttu-id="92cdf-329">如果當您呼叫格式化方法時未指定文化特性，則會使用目前執行緒文化特性的格式設定慣例。</span><span class="sxs-lookup"><span data-stu-id="92cdf-329">If you do not specify a culture when you call a formatting method, the formatting conventions of the current thread culture are used.</span></span> <span data-ttu-id="92cdf-330">下列範例將說明這種情形，其中目前執行緒文化特性會變更四次，然後呼叫 [Decimal.ToString(String)](xref:System.Decimal.ToString(System.String)) 方法。</span><span class="sxs-lookup"><span data-stu-id="92cdf-330">This is illustrated in the following example, which changes the current thread culture four times and then calls the [Decimal.ToString(String)](xref:System.Decimal.ToString(System.String)) method.</span></span> <span data-ttu-id="92cdf-331">在各案例中，結果字串都會反映目前文化特性的格式設定慣例。</span><span class="sxs-lookup"><span data-stu-id="92cdf-331">In each case, the result string reflects the formatting conventions of the current culture.</span></span> <span data-ttu-id="92cdf-332">這是因為 `ToString` 和 `ToString(String)` 方法會包裝對每個數值類型之 `ToString(String, IFormatProvider)` 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="92cdf-332">This is because the `ToString` and `ToString(String)` methods wrap calls to each numeric type's `ToString(String, IFormatProvider)` method.</span></span> 

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      Decimal value = 1043.17m;

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(value.ToString("C2"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       $1,043.17
//       
//       The current culture is fr-FR
//       1 043,17 €
//       
//       The current culture is es-MX
//       $1,043.17
//       
//       The current culture is de-DE
//       1.043,17 €
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim value As Decimal = 1043.17d 

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(value.ToString("C2"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       $1,043.17
'       
'       The current culture is fr-FR
'       1 043,17 €
'       
'       The current culture is es-MX
'       $1,043.17
'       
'       The current culture is de-DE
'       1.043,17 €
```

<span data-ttu-id="92cdf-333">您也可以呼叫具有 *provider* 參數的 `ToString` 多載並且將下列任一項傳遞給它，藉此格式化特定文化特性的數值：</span><span class="sxs-lookup"><span data-stu-id="92cdf-333">You can also format a numeric value for a specific culture by calling a `ToString` overload that has a *provider* parameter and passing it either of the following:</span></span> 

* <span data-ttu-id="92cdf-334">[CultureInfo](xref:System.Globalization.CultureInfo) 物件，表示要使用其格式化慣例的文化特性。</span><span class="sxs-lookup"><span data-stu-id="92cdf-334">A [CultureInfo](xref:System.Globalization.CultureInfo) object that represents the culture whose formatting conventions are to be used.</span></span> <span data-ttu-id="92cdf-335">它的 [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) 方法會傳回 [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) 屬性的值，也就是為數值提供文化特性專屬格式資訊的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件。</span><span class="sxs-lookup"><span data-stu-id="92cdf-335">Its [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) method returns the value of the [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) property, which is the [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object that provides culture-specific formatting information for numeric values.</span></span>

* <span data-ttu-id="92cdf-336">[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件，該物件會定義要使用的文化特性專屬格式化慣例。</span><span class="sxs-lookup"><span data-stu-id="92cdf-336">A [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object that defines the culture-specific formatting conventions to be used.</span></span> <span data-ttu-id="92cdf-337">它的 [GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) 方法會傳回本身的執行個體。</span><span class="sxs-lookup"><span data-stu-id="92cdf-337">Its [GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) method returns an instance of itself.</span></span>

<span data-ttu-id="92cdf-338">下列範例將使用 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件，該物件表示用於格式化浮點數的英文 (美國) 和英文 (英國) 文化特性，以及法文和俄文中性文化特性。</span><span class="sxs-lookup"><span data-stu-id="92cdf-338">The following example uses [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) objects that represent the English (United States) and English (Great Britain) cultures and the French and Russian neutral cultures to format a floating-point number.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      Double value = 1043.62957;
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         NumberFormatInfo nfi = CultureInfo.CreateSpecificCulture(name).NumberFormat;
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 1,043.630
//       en-GB: 1,043.630
//       ru:    1 043,630
//       fr:    1 043,630
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As Double = 1043.62957
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim nfi As NumberFormatInfo = CultureInfo.CreateSpecificCulture(name).NumberFormat
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 1,043.630
'       en-GB: 1,043.630
'       ru:    1 043,630
'       fr:    1 043,630
```

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a><span data-ttu-id="92cdf-339">區分文化特性的日期與時間值格式</span><span class="sxs-lookup"><span data-stu-id="92cdf-339">Culture-sensitive formatting of date and time values</span></span>

<span data-ttu-id="92cdf-340">根據預設，日期和時間值的格式區分文化特性。</span><span class="sxs-lookup"><span data-stu-id="92cdf-340">By default, the formatting of date and time values is culture-sensitive.</span></span> <span data-ttu-id="92cdf-341">如果當您呼叫格式化方法時未指定文化特性，則會使用目前執行緒文化特性的格式設定慣例。</span><span class="sxs-lookup"><span data-stu-id="92cdf-341">If you do not specify a culture when you call a formatting method, the formatting conventions of the current thread culture are used.</span></span> <span data-ttu-id="92cdf-342">下列範例將說明這種情形，其中目前執行緒文化特性會變更四次，然後呼叫 [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) 方法。</span><span class="sxs-lookup"><span data-stu-id="92cdf-342">This is illustrated in the following example, which changes the current thread culture four times and then calls the [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) method.</span></span> <span data-ttu-id="92cdf-343">在各案例中，結果字串都會反映目前文化特性的格式設定慣例。</span><span class="sxs-lookup"><span data-stu-id="92cdf-343">In each case, the result string reflects the formatting conventions of the current culture.</span></span> <span data-ttu-id="92cdf-344">這是因為 [DateTime.ToString()](xref:System.DateTime.ToString)、[DateTime.ToString(String)](xref:System.DateTime.ToString(System.String))、[DateTimeOffset.ToString()](xref:System.DateTimeOffset.ToString(System.String)) 和 [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) 方法會包裝 [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) 和 [DateTimeOffset.ToString(String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="92cdf-344">This is because the [DateTime.ToString()](xref:System.DateTime.ToString), [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)), [DateTimeOffset.ToString()](xref:System.DateTimeOffset.ToString(System.String)), and [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) methods wrap calls to the [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) and [DateTimeOffset.ToString(String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) methods.</span></span>

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      DateTime dateToFormat = new DateTime(2012, 5, 28, 11, 30, 0);

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(dateToFormat.ToString("F"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       Monday, May 28, 2012 11:30:00 AM
//       
//       The current culture is fr-FR
//       lundi 28 mai 2012 11:30:00
//       
//       The current culture is es-MX
//       lunes, 28 de mayo de 2012 11:30:00 a.m.
//       
//       The current culture is de-DE
//       Montag, 28. Mai 2012 11:30:00
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim dateToFormat As Date = #5/28/2012 11:30AM#

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(dateToFormat.ToString("F"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       Monday, May 28, 2012 11:30:00 AM
'       
'       The current culture is fr-FR
'       lundi 28 mai 2012 11:30:00
'       
'       The current culture is es-MX
'       lunes, 28 de mayo de 2012 11:30:00 a.m.
'       
'       The current culture is de-DE
'       Montag, 28. Mai 2012 11:30:00
```

<span data-ttu-id="92cdf-345">您也可以呼叫具有 provider 參數的 [DateTime.ToString](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) 或 [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) 多載並且將下列任一項傳遞給它，藉此格式化特定文化特性的日期和時間值：</span><span class="sxs-lookup"><span data-stu-id="92cdf-345">You can also format a date and time value for a specific culture by calling a [DateTime.ToString](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) or [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) overload that has a provider parameter and passing it either of the following:</span></span> 

* <span data-ttu-id="92cdf-346">[CultureInfo](xref:System.Globalization.CultureInfo) 物件，表示要使用其格式化慣例的文化特性。</span><span class="sxs-lookup"><span data-stu-id="92cdf-346">A [CultureInfo](xref:System.Globalization.CultureInfo) object that represents the culture whose formatting conventions are to be used.</span></span> <span data-ttu-id="92cdf-347">它的 [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) 方法會傳回 [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) 屬性的值，也就是為數值提供文化特性專屬格式資訊的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件。</span><span class="sxs-lookup"><span data-stu-id="92cdf-347">Its [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) method returns the value of the [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) property, which is the [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object that provides culture-specific formatting information for numeric values.</span></span>

* <span data-ttu-id="92cdf-348">[DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件，該物件會定義要使用的文化特性專屬格式化慣例。</span><span class="sxs-lookup"><span data-stu-id="92cdf-348">A [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object that defines the culture-specific formatting conventions to be used.</span></span> <span data-ttu-id="92cdf-349">它的 [GetFormat](xref:System.Globalization.DateTimeFormatInfo.GetFormat(System.Type)) 方法會傳回本身的執行個體。</span><span class="sxs-lookup"><span data-stu-id="92cdf-349">Its [GetFormat](xref:System.Globalization.DateTimeFormatInfo.GetFormat(System.Type)) method returns an instance of itself.</span></span>

<span data-ttu-id="92cdf-350">下列範例將使用 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件，該物件表示用於格式化日期的英文 (美國) 和英文 (英國) 文化特性，以及法文和俄文中性文化特性。</span><span class="sxs-lookup"><span data-stu-id="92cdf-350">The following example uses [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) objects that represent the English (United States) and English (Great Britain) cultures and the French and Russian neutral cultures to format a date.</span></span> 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      DateTime dat1 = new DateTime(2012, 5, 28, 11, 30, 0);
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         DateTimeFormatInfo dtfi = CultureInfo.CreateSpecificCulture(name).DateTimeFormat;
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 5/28/2012 11:30:00 AM
//       en-GB: 28/05/2012 11:30:00
//       ru: 28.05.2012 11:30:00
//       fr: 28/05/2012 11:30:00
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dat1 As Date = #5/28/2012 11:30AM#
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim dtfi As DateTimeFormatInfo = CultureInfo.CreateSpecificCulture(name).DateTimeFormat
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 5/28/2012 11:30:00 AM
'       en-GB: 28/05/2012 11:30:00
'       ru: 28.05.2012 11:30:00
'       fr: 28/05/2012 11:30:00
```

## <a name="the-iformattable-interface"></a><span data-ttu-id="92cdf-351">IFormattable 介面</span><span class="sxs-lookup"><span data-stu-id="92cdf-351">The IFormattable interface</span></span>

<span data-ttu-id="92cdf-352">以格式字串和 [IFormatProvider](xref:System.IFormatProvider) 參數來多載 `ToString` 方法的類型，通常也會實作 [IFormattable](xref:System.IFormattable) 介面。</span><span class="sxs-lookup"><span data-stu-id="92cdf-352">Typically, types that overload the `ToString` method with a format string and an [IFormatProvider](xref:System.IFormatProvider) parameter also implement the [IFormattable](xref:System.IFormattable) interface.</span></span> <span data-ttu-id="92cdf-353">這個介面具有單一成員 [IFormattable.ToString(String, IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider))，這個成員同時包含格式字串和格式提供者作為參數。</span><span class="sxs-lookup"><span data-stu-id="92cdf-353">This interface has a single member, [IFormattable.ToString(String, IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)), that includes both a format string and a format provider as parameters.</span></span>

<span data-ttu-id="92cdf-354">針對您的應用程式定義類別來實作 [IFormattable](xref:System.IFormattable) 介面有兩項好處：</span><span class="sxs-lookup"><span data-stu-id="92cdf-354">Implementing the [IFormattable](xref:System.IFormattable) interface for your application-defined class offers two advantages:</span></span> 

* <span data-ttu-id="92cdf-355">支援透過 [Convert](xref:System.Convert) 類別來轉換字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-355">Support for string conversion by the [Convert](xref:System.Convert) class.</span></span> <span data-ttu-id="92cdf-356">呼叫 [Convert.ToString(Object)](xref:System.Convert.ToString(System.Object)) 和 [Convert.ToString(Object, IFormatProvider)](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) 方法時，會自動呼叫您的 [IFormattable](xref:System.IFormattable) 實作。</span><span class="sxs-lookup"><span data-stu-id="92cdf-356">Calls to the [Convert.ToString(Object)](xref:System.Convert.ToString(System.Object)) and [Convert.ToString(Object, IFormatProvider)](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) methods call your [IFormattable](xref:System.IFormattable) implementation automatically.</span></span>

* <span data-ttu-id="92cdf-357">支援複合格式。</span><span class="sxs-lookup"><span data-stu-id="92cdf-357">Support for composite formatting.</span></span> <span data-ttu-id="92cdf-358">如果使用包含格式字串的格式項目來格式化您的自訂類型，則 Common Language Runtime 會自動呼叫您的 [IFormattable](xref:System.IFormattable) 實作並將格式字串傳遞給這個實作。</span><span class="sxs-lookup"><span data-stu-id="92cdf-358">If a format item that includes a format string is used to format your custom type, the Common Language Runtime automatically calls your [IFormattable](xref:System.IFormattable) implementation and passes it the format string.</span></span> <span data-ttu-id="92cdf-359">如需各種方法之複合格式 (例如 `String.Format` 或 `Console.WriteLine`) 的詳細資訊，請參閱[複合格式](#composite-formatting)一節。</span><span class="sxs-lookup"><span data-stu-id="92cdf-359">For more information about composite formatting with methods such as `String.Format` or `Console.WriteLine`, see the [Composite formatting](#composite-formatting) section.</span></span>

<span data-ttu-id="92cdf-360">下列範例定義一個實作 [IFormattable](xref:System.IFormattable) 介面的 `Temperature` 類別。</span><span class="sxs-lookup"><span data-stu-id="92cdf-360">The following example defines a `Temperature` class that implements the [IFormattable](xref:System.IFormattable) interface.</span></span> <span data-ttu-id="92cdf-361">這個類別支援 "C" 或 "G" 格式規範來顯示攝氏溫度、支援 "F" 格式規範來顯示華氏溫度，也支援 "K" 格式規範來顯示絕對溫度。</span><span class="sxs-lookup"><span data-stu-id="92cdf-361">It supports the "C" or "G" format specifiers to display the temperature in Celsius, the "F" format specifier to display the temperature in Fahrenheit, and the "K" format specifier to display the temperature in Kelvin.</span></span>

```csharp
using System;
using System.Globalization;

public class Temperature : IFormattable
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round((decimal) this.m_Temp * 9 / 5 + 32, 2); }
   }

   public override string ToString()
   {
      return this.ToString("G", null);
   }

   public string ToString(string format)
   {
      return this.ToString(format, null);
   }

   public string ToString(string format, IFormatProvider provider)  
   {
      // Handle null or empty arguments.
      if (String.IsNullOrEmpty(format)) format = "G";
      // Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant();

      if (provider == null) provider = NumberFormatInfo.CurrentInfo;

      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2", provider) + "°F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2", provider) + "K";
         // Return temperature in Celsius.
         case "C":
         case "G":
            return this.Celsius.ToString("N2", provider) + "°C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}
```

```vb
Imports System.Globalization

Public Class Temperature : Implements IFormattable
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("G", Nothing)
   End Function

   Public Overloads Function ToString(format As String) As String
      Return Me.ToString(format, Nothing)
   End Function

   Public Overloads Function ToString(format As String, provider As IFormatProvider) As String _  
      Implements IFormattable.ToString

      ' Handle null or empty arguments.
      If String.IsNullOrEmpty(format) Then format = "G"
      ' Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant()

      If provider Is Nothing Then provider = NumberFormatInfo.CurrentInfo

      Select Case format
         ' Convert temperature to Fahrenheit and return string.
         Case "F"
            Return Me.Fahrenheit.ToString("N2", provider) & "°F"
         ' Convert temperature to Kelvin and return string.
         Case "K"
            Return Me.Kelvin.ToString("N2", provider) & "K"
         ' Return temperature in Celsius.
         Case "C", "G"
            Return Me.Celsius.ToString("N2", provider) & "°C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class
```

<span data-ttu-id="92cdf-362">下列範例會執行個體化 `Temperature` 物件。</span><span class="sxs-lookup"><span data-stu-id="92cdf-362">The following example instantiates a `Temperature` object.</span></span> <span data-ttu-id="92cdf-363">然後呼叫 [ToString](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) 方法，並使用數個複合格式字串來取得 `Temperature` 物件的不同字串表示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-363">It then calls the [ToString](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) method and uses several composite format strings to obtain different string representations of a `Temperature` object.</span></span> <span data-ttu-id="92cdf-364">其中每個方法又呼叫 `Temperature` 類別的 [IFormattable](xref:System.IFormattable) 實作。</span><span class="sxs-lookup"><span data-stu-id="92cdf-364">Each of these method calls, in turn, calls the [IFormattable](xref:System.IFormattable) implementation of the `Temperature` class.</span></span>

```csharp
public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(22m);
      Console.WriteLine(Convert.ToString(temp1, new CultureInfo("ja-JP")));
      Console.WriteLine("Temperature: {0:K}", temp1);
      Console.WriteLine("Temperature: {0:F}", temp1);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), "Temperature: {0:F}", temp1));
   }
}
// The example displays the following output:
//       22.00°C
//       Temperature: 295.15°K
//       Temperature: 71.60°F
//       Temperature: 71,60°F
```

```vb
Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(22d)
      Console.WriteLine(Convert.ToString(temp1, New CultureInfo("ja-JP")))
      Console.WriteLine("Temperature: {0:K}", temp1)
      Console.WriteLine("Temperature: {0:F}", temp1)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), "Temperature: {0:F}", temp1)) 
   End Sub
End Module
' The example displays the following output:
'       22.00°C
'       Temperature: 295.15°K
'       Temperature: 71.60°F
'       Temperature: 71,60°F
```

## <a name="composite-formatting"></a><span data-ttu-id="92cdf-365">複合格式</span><span class="sxs-lookup"><span data-stu-id="92cdf-365">Composite formatting</span></span>

<span data-ttu-id="92cdf-366">某些方法 (例如 `String.Format` 和 `StringBuilder.AppendFormat`) 支援複合格式。</span><span class="sxs-lookup"><span data-stu-id="92cdf-366">Some methods, such as `String.Format` and `StringBuilder.AppendFormat`, support composite formatting.</span></span> <span data-ttu-id="92cdf-367">複合格式字串是一種範本，可傳回由零個、一個或更多物件的字串表示所組成的單一字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-367">A composite format string is a kind of template that returns a single string that incorporates the string representation of zero, one, or more objects.</span></span> <span data-ttu-id="92cdf-368">複合格式字串中的每個物件都以有索引的格式項目來表示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-368">Each object is represented in the composite format string by an indexed format item.</span></span> <span data-ttu-id="92cdf-369">格式項目的索引對應至其所表示的物件在方法的參數清單中的位置。</span><span class="sxs-lookup"><span data-stu-id="92cdf-369">The index of the format item corresponds to the position of the object that it represents in the method's parameter list.</span></span> <span data-ttu-id="92cdf-370">索引以零為起始。</span><span class="sxs-lookup"><span data-stu-id="92cdf-370">Indexes are zero-based.</span></span> <span data-ttu-id="92cdf-371">例如，在下列對 `String.Format` 方法的呼叫中，第一個格式項目 `{0:D}` 由 `thatDate` 的字串表示所取代、第二個格式項目 `{1}` 由 `item1` 的字串表示所取代，而第三個格式項目 `{2:C2}` 由 `item1.Value` 的字串表示所取代。</span><span class="sxs-lookup"><span data-stu-id="92cdf-371">For example, in the following call to the `String.Format` method, the first format item, `{0:D}`, is replaced by the string representation of `thatDate`; the second format item, `{1}`, is replaced by the string representation of `item1`; and the third format item, `{2:C2}`, is replaced by the string representation of `item1.Value`.</span></span>

```csharp
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", 
                       thatDate, item1, item1.Value);
Console.WriteLine(result);                            
// The example displays output like the following if run on a system
// whose current culture is en-US:
//       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

```vb
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", _
                       thatDate, item1, item1.Value)
Console.WriteLine(result)                            
' The example displays output like the following if run on a system
' whose current culture is en-US:
'       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

<span data-ttu-id="92cdf-372">除了取代具有對應物件字串表示格式的項目，格式項目也可讓您控制下列幾項：</span><span class="sxs-lookup"><span data-stu-id="92cdf-372">In addition to replacing a format item with the string representation of its corresponding object, format items also let you control the following:</span></span> 

* <span data-ttu-id="92cdf-373">當物件實作 [IFormattable](xref:System.IFormattable) 介面，並支援格式字串時，物件表示為字串的特定方式。</span><span class="sxs-lookup"><span data-stu-id="92cdf-373">The specific way in which an object is represented as a string, if the object implements the [IFormattable](xref:System.IFormattable) interface and supports format strings.</span></span> <span data-ttu-id="92cdf-374">您可將格式項目索引後面接上 : (冒號) ，後面再接有效的格式字串，以執行此作業。</span><span class="sxs-lookup"><span data-stu-id="92cdf-374">You do this by following the format item's index with a : (colon) followed by a valid format string.</span></span> <span data-ttu-id="92cdf-375">前一個範例採用的方法是用 "d" (簡短日期模式) 格式字串來格式化日期值 (例如 `{0:d}`) 以及用 "C2" 格式字串 (例如 `{2:C2}`) 來格式化數值，以表示具有兩個小數位數的十進位數字之貨幣值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-375">The previous example did this by formatting a date value with the "d" (short date pattern) format string (for example, `{0:d}`) and by formatting a numeric value with the "C2" format string (for example, `{2:C2}` to represent the number as a currency value with two fractional decimal digits).</span></span> 

* <span data-ttu-id="92cdf-376">包含物件字串表示法及在該欄位中對齊方式的字串表示法之欄位寬度。</span><span class="sxs-lookup"><span data-stu-id="92cdf-376">The width of the field that contains the object's string representation, and the alignment of the string representation in that field.</span></span> <span data-ttu-id="92cdf-377">您可將格式項目索引後面接上 , (逗號) ，後面再接欄位寬度，以執行此作業。</span><span class="sxs-lookup"><span data-stu-id="92cdf-377">You do this by following the format item's index with a , (comma) followed the field width.</span></span> <span data-ttu-id="92cdf-378">如果欄位寬度是正值，則此欄位中的字串為靠右對齊；如果欄位寬度是負值，則為靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="92cdf-378">The string is right-aligned in the field if the field width is a positive value, and it is left-aligned if the field width is a negative value.</span></span> <span data-ttu-id="92cdf-379">下列範例在長 20 個字元的欄位中將日期值靠左對齊，並在長 11 個字元的欄位中將具有一位小數位數的十進位值靠右對齊。</span><span class="sxs-lookup"><span data-stu-id="92cdf-379">The following example left-aligns date values in a 20-character field, and it right-aligns decimal values with one fractional digit in an 11-character field.</span></span> 

```csharp
DateTime startDate = new DateTime(2015, 8, 28, 6, 0, 0);
decimal[] temps = { 73.452m, 68.98m, 72.6m, 69.24563m,
                   74.1m, 72.156m, 72.228m };
Console.WriteLine("{0,-20} {1,11}\n", "Date", "Temperature");
for (int ctr = 0; ctr < temps.Length; ctr++)
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps[ctr]);

// The example displays the following output:
//       Date                 Temperature
//
//       8/28/2015 6:00 AM           73.5
//       8/29/2015 6:00 AM           69.0
//       8/30/2015 6:00 AM           72.6
//       8/31/2015 6:00 AM           69.2
//       9/1/2015 6:00 AM            74.1
//       9/2/2015 6:00 AM            72.2
//       9/3/2015 6:00 AM            72.2
```

```vb
Dim startDate As New Date(2015, 8, 28, 6, 0, 0)
Dim temps() As Decimal = { 73.452, 68.98, 72.6, 69.24563,
                           74.1, 72.156, 72.228 }
Console.WriteLine("{0,-20} {1,11}", "Date", "Temperature")
Console.WriteLine()
For ctr As Integer = 0 To temps.Length - 1
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps(ctr))
Next
' The example displays the following output:
'       Date                 Temperature
'
'       8/28/2015 6:00 AM           73.5
'       8/29/2015 6:00 AM           69.0
'       8/30/2015 6:00 AM           72.6
'       8/31/2015 6:00 AM           69.2
'       9/1/2015 6:00 AM            74.1
'       9/2/2015 6:00 AM            72.2
'       9/3/2015 6:00 AM            72.2
```

<span data-ttu-id="92cdf-380">請注意如果對齊字串元件和格式字串元件都存在，則前者優先於後者 (例如，`{0,-20:g}`)。</span><span class="sxs-lookup"><span data-stu-id="92cdf-380">Note that, if both the alignment string component and the format string component are present, the former precedes the latter (for example, `{0,-20:g}`.</span></span> 

<span data-ttu-id="92cdf-381">如需複合格式的詳細資訊，請參閱[複合格式](composite-format.md)。</span><span class="sxs-lookup"><span data-stu-id="92cdf-381">For more information about composite formatting, see [Composite formatting](composite-format.md).</span></span>

## <a name="custom-formatting-with-icustomformatter"></a><span data-ttu-id="92cdf-382">使用 ICustomFormatter 的自訂格式</span><span class="sxs-lookup"><span data-stu-id="92cdf-382">Custom formatting with ICustomFormatter</span></span>

<span data-ttu-id="92cdf-383">[String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object[])) 和 [StringBuilder.AppendFormat(IFormatProvider, String, Object[])](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) 這兩個複合格式化方法包含支援自訂格式的格式提供者參數。</span><span class="sxs-lookup"><span data-stu-id="92cdf-383">Two composite formatting methods, [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object[])) and [StringBuilder.AppendFormat(IFormatProvider, String, Object[])](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)), include a format provider parameter that supports custom formatting.</span></span> <span data-ttu-id="92cdf-384">呼叫這兩種格式化方法的任一種時，會將表示 [ICustomFormatter](xref:System.ICustomFormatter) 介面的 [Type](xref:System.Type) 物件傳遞至格式提供者的 `GetFormat` 方法。</span><span class="sxs-lookup"><span data-stu-id="92cdf-384">When either of these formatting methods is called, it passes a [Type](xref:System.Type) object that represents an [ICustomFormatter](xref:System.ICustomFormatter) interface to the format provider’s `GetFormat` method.</span></span> <span data-ttu-id="92cdf-385">然後，`GetFormat` 方法負責傳回 [ICustomFormatter](xref:System.ICustomFormatter) 實作，這個實作提供自訂格式。</span><span class="sxs-lookup"><span data-stu-id="92cdf-385">The `GetFormat` method is then responsible for returning the [ICustomFormatter](xref:System.ICustomFormatter) implementation that provides custom formatting.</span></span>

<span data-ttu-id="92cdf-386">[ICustomFormatter](xref:System.ICustomFormatter) 介面具有單一方法 [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider))，複合格式化方法會自動針對複合格式字串中的每個格式項目，各呼叫一次這個方法。</span><span class="sxs-lookup"><span data-stu-id="92cdf-386">The [ICustomFormatter](xref:System.ICustomFormatter) interface has a single method, [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)), that is called automatically by a composite formatting method, once for each format item in a composite format string.</span></span> <span data-ttu-id="92cdf-387">[Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) 方法具有三個參數：格式字串 (表示格式項目中的 *formatString* 引數)、要格式化的物件，以及提供格式化服務的 [IFormatProvider](xref:System.IFormatProvider) 物件。</span><span class="sxs-lookup"><span data-stu-id="92cdf-387">The [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) method has three parameters: a format string, which represents the *formatString* argument in a format item, an object to format, and an [IFormatProvider](xref:System.IFormatProvider) object that provides formatting services.</span></span> <span data-ttu-id="92cdf-388">實作 [ICustomFormatter](xref:System.ICustomFormatter) 的類別通常也會實作 [IFormatProvider](xref:System.IFormatProvider)，所以這最後一個參數是對自訂格式類別的參考。</span><span class="sxs-lookup"><span data-stu-id="92cdf-388">Typically, the class that implements [ICustomFormatter](xref:System.ICustomFormatter) also implements [IFormatProvider](xref:System.IFormatProvider), so this last parameter is a reference to the custom formatting class itself.</span></span> <span data-ttu-id="92cdf-389">方法會傳回要格式化之物件的自訂格式化字串表示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-389">The method returns a custom formatted string representation of the object to be formatted.</span></span> <span data-ttu-id="92cdf-390">如果方法無法格式化物件，則應該傳回 null 參考。</span><span class="sxs-lookup"><span data-stu-id="92cdf-390">If the method cannot format the object, it should return a null reference.</span></span>

<span data-ttu-id="92cdf-391">下列範例提供一個名為 `ByteByByteFormatter` 的 [ICustomFormatter](xref:System.ICustomFormatter) 實作，這個實作會將整數值顯示為一連串由兩位數十六進位值再加上一個空格所組成的數列。</span><span class="sxs-lookup"><span data-stu-id="92cdf-391">The following example provides an [ICustomFormatter](xref:System.ICustomFormatter) implementation named `ByteByByteFormatter` that displays integer values as a sequence of two-digit hexadecimal values followed by a space.</span></span>

```csharp
public class ByteByByteFormatter : IFormatProvider, ICustomFormatter
{
   public object GetFormat(Type formatType)
   { 
      if (formatType == typeof(ICustomFormatter))
         return this;
      else
         return null;
   }

   public string Format(string format, object arg, 
                          IFormatProvider formatProvider)
   {   
      if (! formatProvider.Equals(this)) return null;

      // Handle only hexadecimal format string.
      if (! format.StartsWith("X")) return null;

      byte[] bytes;
      string output = null;

      // Handle only integral types.
      if (arg is Byte) 
         bytes = BitConverter.GetBytes((Byte) arg);
      else if (arg is Int16)
         bytes = BitConverter.GetBytes((Int16) arg);
      else if (arg is Int32)
         bytes = BitConverter.GetBytes((Int32) arg);
      else if (arg is Int64)   
         bytes = BitConverter.GetBytes((Int64) arg);
      else if (arg is SByte)
         bytes = BitConverter.GetBytes((SByte) arg);
      else if (arg is UInt16)
         bytes = BitConverter.GetBytes((UInt16) arg);
      else if (arg is UInt32)
         bytes = BitConverter.GetBytes((UInt32) arg);
      else if (arg is UInt64)
         bytes = BitConverter.GetBytes((UInt64) arg);
      else
         return null;

      for (int ctr = bytes.Length - 1; ctr >= 0; ctr--)
         output += String.Format("{0:X2} ", bytes[ctr]);   

      return output.Trim();
   }
}
```

```vb
Public Class ByteByByteFormatter : Implements IFormatProvider, ICustomFormatter
   Public Function GetFormat(formatType As Type) As Object _
                   Implements IFormatProvider.GetFormat
      If formatType Is GetType(ICustomFormatter) Then
         Return Me
      Else
         Return Nothing
      End If
   End Function

   Public Function Format(fmt As String, arg As Object, 
                          formatProvider As IFormatProvider) As String _
                          Implements ICustomFormatter.Format

      If Not formatProvider.Equals(Me) Then Return Nothing

      ' Handle only hexadecimal format string.
      If Not fmt.StartsWith("X") Then 
            Return Nothing
      End If

      ' Handle only integral types.
      If Not typeof arg Is Byte AndAlso
         Not typeof arg Is Int16 AndAlso
         Not typeof arg Is Int32 AndAlso
         Not typeof arg Is Int64 AndAlso
         Not typeof arg Is SByte AndAlso
         Not typeof arg Is UInt16 AndAlso
         Not typeof arg Is UInt32 AndAlso
         Not typeof arg Is UInt64 Then _
            Return Nothing

      Dim bytes() As Byte = BitConverter.GetBytes(arg)
      Dim output As String = Nothing

      For ctr As Integer = bytes.Length - 1 To 0 Step -1
         output += String.Format("{0:X2} ", bytes(ctr))   
      Next

      Return output.Trim()
   End Function
End Class
```

<span data-ttu-id="92cdf-392">下列範例會使用 `ByteByByteFormatter` 類別來格式化整數值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-392">The following example uses the `ByteByByteFormatter` class to format integer values.</span></span> <span data-ttu-id="92cdf-393">請注意，[ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) 方法在第二個 [String.Format(IFormatProvider, String, Object[])](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) 方法呼叫中被呼叫不只一次，且第三個方法呼叫中使用預設 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 提供者，因為 `.ByteByByteFormatter.Format` 方法無法辨認 "N0" 格式字串而傳回 null 參考。</span><span class="sxs-lookup"><span data-stu-id="92cdf-393">Note that the [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) method is called more than once in the second [String.Format(IFormatProvider, String, Object[])](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) method call, and that the default [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) provider is used in the third method call because the `.ByteByByteFormatter.Format` method does not recognize the "N0" format string and returns a null reference.</span></span>

```csharp
public class Example
{
   public static void Main()
   {
      long value = 3210662321; 
      byte value1 = 214;
      byte value2 = 19;

      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X}", value));
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 & value2));                                
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0,10:N0}", value));
   }
}
// The example displays the following output:
//       00 00 00 00 BF 5E D1 B1
//       00 D6 And 00 13 = 00 12 (018)
//       3,210,662,321
```

```vb
Public Module Example
   Public Sub Main()
      Dim value As Long = 3210662321 
      Dim value1 As Byte = 214
      Dim value2 As Byte = 19

      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X}", value)))
      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 And value2)))                                
      Console.WriteLine(String.Format(New ByteByByteFormatter(), "{0,10:N0}", value))
   End Sub
End Module
' The example displays the following output:
'       00 00 00 00 BF 5E D1 B1
'       00 D6 And 00 13 = 00 12 (018)
'       3,210,662,321
```

## <a name="related-topics"></a><span data-ttu-id="92cdf-394">相關主題</span><span class="sxs-lookup"><span data-stu-id="92cdf-394">Related topics</span></span>

<span data-ttu-id="92cdf-395">標題</span><span class="sxs-lookup"><span data-stu-id="92cdf-395">Title</span></span> | <span data-ttu-id="92cdf-396">定義</span><span class="sxs-lookup"><span data-stu-id="92cdf-396">Definition</span></span>
----- | ----------
[<span data-ttu-id="92cdf-397">標準數值格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-397">Standard numeric format strings</span></span>](standard-numeric.md) | <span data-ttu-id="92cdf-398">說明建立數值常用之字串表示的標準格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-398">Describes standard format strings that create commonly used string representations of numeric values.</span></span> 
[<span data-ttu-id="92cdf-399">自訂數值格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-399">Custom numeric format strings</span></span>](custom-numeric.md) | <span data-ttu-id="92cdf-400">說明建立應用程式專屬數值格式的自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-400">Describes custom format strings that create application-specific formats for numeric values.</span></span>
[<span data-ttu-id="92cdf-401">標準日期與時間格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-401">Standard date and time format strings</span></span>](standard-datetime.md) |  <span data-ttu-id="92cdf-402">說明建立 [DateTime](xref:System.DateTime) 值之常用字串表示的標準格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-402">Describes standard format strings that create commonly used string representations of [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="92cdf-403">自訂日期與時間格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-403">Custom date and time format strings</span></span>](custom-datetime.md) | <span data-ttu-id="92cdf-404">說明為 [DateTime](xref:System.DateTime)值建立應用程式專屬格式的自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-404">Describes custom format strings that create application-specific formats for [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="92cdf-405">標準 TimeSpan 格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-405">Standard TimeSpan format strings</span></span>](standard-timespan.md) | <span data-ttu-id="92cdf-406">說明建立時間間隔之常用字串表示的標準格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-406">Describes standard format strings that create commonly used string representations of time intervals.</span></span>
[<span data-ttu-id="92cdf-407">自訂 TimeSpan 格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-407">Custom TimeSpan format strings</span></span>](custom-timespan.md) | <span data-ttu-id="92cdf-408">說明建立應用程式專屬數值格式的自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-408">Describes custom format strings that create application-specific formats for time intervals.</span></span>
[<span data-ttu-id="92cdf-409">列舉格式字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-409">Enumeration format strings</span></span>](enumeration-format.md) | <span data-ttu-id="92cdf-410">說明用來建立列舉值之字串表示的標準格式字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-410">Describes standard format strings that are used to create string representations of enumeration values.</span></span>
[<span data-ttu-id="92cdf-411">複合格式</span><span class="sxs-lookup"><span data-stu-id="92cdf-411">Composite formatting</span></span>](composite-format.md) | <span data-ttu-id="92cdf-412">描述如何將一個或更多的格式化值嵌入字串。</span><span class="sxs-lookup"><span data-stu-id="92cdf-412">Describes how to embed one or more formatted values in a string.</span></span> <span data-ttu-id="92cdf-413">字串可以隨後顯示在主控台 (Console) 或寫入資料流。</span><span class="sxs-lookup"><span data-stu-id="92cdf-413">The string can subsequently be displayed on the console or written to a stream.</span></span>
[<span data-ttu-id="92cdf-414">執行格式化作業</span><span class="sxs-lookup"><span data-stu-id="92cdf-414">Performing formatting operations</span></span>](performing-formatting-operations.md) | <span data-ttu-id="92cdf-415">列出各主題，提供執行特定格式設定作業的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="92cdf-415">Lists topics that provide step-by-step instructions for performing specific formatting operations.</span></span>
[<span data-ttu-id="92cdf-416">剖析字串</span><span class="sxs-lookup"><span data-stu-id="92cdf-416">Parsing strings</span></span>](parsing-strings.md) | <span data-ttu-id="92cdf-417">說明如何將物件初始化為這些物件的字串表示所描述的值。</span><span class="sxs-lookup"><span data-stu-id="92cdf-417">Describes how to initialize objects to the values described by string representations of those objects.</span></span> <span data-ttu-id="92cdf-418">剖析是格式化的反向作業。</span><span class="sxs-lookup"><span data-stu-id="92cdf-418">Parsing is the inverse operation of formatting.</span></span>

## <a name="reference"></a><span data-ttu-id="92cdf-419">參考資料</span><span class="sxs-lookup"><span data-stu-id="92cdf-419">Reference</span></span>

[<span data-ttu-id="92cdf-420">System.IFormattable</span><span class="sxs-lookup"><span data-stu-id="92cdf-420">System.IFormattable</span></span>](xref:System.IFormattable)

[<span data-ttu-id="92cdf-421">System.IFormatProvider</span><span class="sxs-lookup"><span data-stu-id="92cdf-421">System.IFormatProvider</span></span>](xref:System.IFormatProvider)

[<span data-ttu-id="92cdf-422">System.ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="92cdf-422">System.ICustomFormatter</span></span>](xref:System.ICustomFormatter)

