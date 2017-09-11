---
title: "使用 StringBuilder 類別"
description: "使用 StringBuilder 類別"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: f4f5d1c7-d84d-4867-810f-2708cd6de0da
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 076e10e095b50cc96187f2ec13ade2365d83dad3
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="using-the-stringbuilder-class"></a><span data-ttu-id="4bcd7-104">使用 StringBuilder 類別</span><span class="sxs-lookup"><span data-stu-id="4bcd7-104">Using the StringBuilder class</span></span>

<span data-ttu-id="4bcd7-105">[String](xref:System.String) 物件為不可變。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-105">The [String](xref:System.String) object is immutable.</span></span> <span data-ttu-id="4bcd7-106">每當您使用 [System.String](xref:System.String) 類別的其中一個方法時，您會在記憶體中建立新的字串物件，而系統即需為這個新物件配置新的空間。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-106">Every time you use one of the methods in the [System.String](xref:System.String) class, you create a new string object in memory, which requires a new allocation of space for that new object.</span></span> <span data-ttu-id="4bcd7-107">在您需要重複修改字串的情況下，建立新 [String](xref:System.String) 物件時產生的額外負荷可能成本高昂。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-107">In situations where you need to perform repeated modifications to a string, the overhead associated with creating a new [String](xref:System.String) object can be costly.</span></span> <span data-ttu-id="4bcd7-108">[System.Text.StringBuilder](xref:System.Text.StringBuilder) 類別可用於您想要修改字串，而不建立新的物件時。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-108">The [System.Text.StringBuilder](xref:System.Text.StringBuilder) class can be used when you want to modify a string without creating a new object.</span></span> <span data-ttu-id="4bcd7-109">例如，使用 [StringBuilder](xref:System.Text.StringBuilder) 類別可以在將許多字串一起串連在迴圈中時，提升效能。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-109">For example, using the [StringBuilder](xref:System.Text.StringBuilder) class can boost performance when concatenating many strings together in a loop.</span></span>

## <a name="importing-the-systemtext-namespace"></a><span data-ttu-id="4bcd7-110">匯入 System.Text 命名空間</span><span class="sxs-lookup"><span data-stu-id="4bcd7-110">Importing the System.Text Namespace</span></span>

<span data-ttu-id="4bcd7-111">[StringBuilder](xref:System.Text.StringBuilder) 類別位於 [System.Text](xref:System.Text) 命名空間。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-111">The [StringBuilder](xref:System.Text.StringBuilder) class is found in the [System.Text](xref:System.Text) namespace.</span></span> <span data-ttu-id="4bcd7-112">若要避免在程式碼中提供完整的類型名稱，您可以匯入 [System.Text](xref:System.Text) 命名空間：</span><span class="sxs-lookup"><span data-stu-id="4bcd7-112">To avoid having to provide a fully qualified type name in your code, you can import the [System.Text](xref:System.Text) namespace:</span></span> 

```csharp
using System;
using System.Text;
```

```vb
Imports System.Text
```

## <a name="instantiating-a-stringbuilder-object"></a><span data-ttu-id="4bcd7-113">具現化 StringBuilder 物件</span><span class="sxs-lookup"><span data-stu-id="4bcd7-113">Instantiating a StringBuilder Object</span></span>

<span data-ttu-id="4bcd7-114">您可以使用其中一個多載建構函式方法，初始化變數來建立 [StringBuilder](xref:System.Text.StringBuilder) 類別的新執行個體，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-114">You can create a new instance of the [StringBuilder](xref:System.Text.StringBuilder) class by initializing your variable with one of the overloaded constructor methods, as illustrated in the following example.</span></span>

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
```

## <a name="setting-the-capacity-and-length"></a><span data-ttu-id="4bcd7-115">設定容量和長度</span><span class="sxs-lookup"><span data-stu-id="4bcd7-115">Setting the Capacity and Length</span></span>

<span data-ttu-id="4bcd7-116">雖然 [StringBuilder](xref:System.Text.StringBuilder) 是動態的物件 (可讓您擴展它所封裝之字串中的字元數)，但您仍可以指定它能容納的字元數上限值。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-116">Although the [StringBuilder](xref:System.Text.StringBuilder) is a dynamic object that allows you to expand the number of characters in the string that it encapsulates, you can specify a value for the maximum number of characters that it can hold.</span></span> <span data-ttu-id="4bcd7-117">這個值稱為物件的容量，不應該與目前 [StringBuilder](xref:System.Text.StringBuilder) 保存的字串長度混淆。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-117">This value is called the capacity of the object and should not be confused with the length of the string that the current [StringBuilder](xref:System.Text.StringBuilder) holds.</span></span> <span data-ttu-id="4bcd7-118">例如，您可以用字串 "Hello" 建立 [StringBuilder](xref:System.Text.StringBuilder) 類別的新執行個體，其長度為 5，而且您可能會指定物件的最大容量為 25。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-118">For example, you might create a new instance of the [StringBuilder](xref:System.Text.StringBuilder) class with the string "Hello", which has a length of 5, and you might specify that the object has a maximum capacity of 25.</span></span> <span data-ttu-id="4bcd7-119">當您修改 [StringBuilder](xref:System.Text.StringBuilder) 時，除非達到容量上限，否則它不會重新配置自己的大小。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-119">When you modify the [StringBuilder](xref:System.Text.StringBuilder), it does not reallocate size for itself until the capacity is reached.</span></span> <span data-ttu-id="4bcd7-120">發生這種情況時，會自動配置新的空間，而且容量加倍。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-120">When this occurs, the new space is allocated automatically and the capacity is doubled.</span></span> <span data-ttu-id="4bcd7-121">您可以使用其中一個多載建構函式，指定 [StringBuilder](xref:System.Text.StringBuilder) 類別的容量。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-121">You can specify the capacity of the [StringBuilder](xref:System.Text.StringBuilder) class using one of the overloaded constructors.</span></span> <span data-ttu-id="4bcd7-122">下列範例會指定 `MyStringBuilder` 物件可以擴展到最多 25 個空格。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-122">The following example specifies that the `MyStringBuilder` object can be expanded to a maximum of 25 spaces.</span></span>

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!", 25);
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!", 25) 
```

<span data-ttu-id="4bcd7-123">此外，您可以使用讀/寫 [Capacity](xref:System.Text.StringBuilder.Capacity) 屬性來設定物件的長度上限。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-123">Additionally, you can use the read/write [Capacity](xref:System.Text.StringBuilder.Capacity) property to set the maximum length of your object.</span></span> <span data-ttu-id="4bcd7-124">下列範例會使用 [Capacity](xref:System.Text.StringBuilder.Capacity) 屬性來定義物件長度上限。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-124">The following example uses the [Capacity](xref:System.Text.StringBuilder.Capacity) property to define the maximum object length.</span></span>

```csharp
MyStringBuilder.Capacity = 25;
```

```vb
MyStringBuilder.Capacity = 25
```

<span data-ttu-id="4bcd7-125">[EnsureCapacity](xref:System.Text.StringBuilder.EnsureCapacity(System.Int32)) 方法可用來檢查目前 [StringBuilder](xref:System.Text.StringBuilder) 的容量。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-125">The [EnsureCapacity](xref:System.Text.StringBuilder.EnsureCapacity(System.Int32)) method can be used to check the capacity of the current [StringBuilder](xref:System.Text.StringBuilder).</span></span> <span data-ttu-id="4bcd7-126">如果容量大於傳遞的值，不會進行任何變更。不過，如果容量小於傳遞的值，會變更目前的容量以符合傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-126">If the capacity is greater than the passed value, no change is made; however, if the capacity is smaller than the passed value, the current capacity is changed to match the passed value.</span></span>

<span data-ttu-id="4bcd7-127">您也可以檢視或設定 [Length](xref:System.Text.StringBuilder.Length) 屬性。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-127">The [Length](xref:System.Text.StringBuilder.Length) property can also be viewed or set.</span></span> <span data-ttu-id="4bcd7-128">如果您將 [Length](xref:System.Text.StringBuilder.Length) 屬性的值設成大於 [Capacity](xref:System.Text.StringBuilder.Capacity) 屬性的值，則 [Capacity](xref:System.Text.StringBuilder.Capacity) 屬性會自動變更為與 [Length](xref:System.Text.StringBuilder.Length) 屬性相同的值。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-128">If you set the [Length](xref:System.Text.StringBuilder.Length) property to a value that is greater than the [Capacity](xref:System.Text.StringBuilder.Capacity) property, the [Capacity](xref:System.Text.StringBuilder.Capacity) property is automatically changed to the same value as the [Length](xref:System.Text.StringBuilder.Length) property.</span></span> <span data-ttu-id="4bcd7-129">若將 [Length](xref:System.Text.StringBuilder.Length) 屬性的值設成小於目前 [StringBuilder](xref:System.Text.StringBuilder) 內字串長度的值，則會縮短該字串。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-129">Setting the [Length](xref:System.Text.StringBuilder.Length) property to a value that is less than the length of the string within the current [StringBuilder](xref:System.Text.StringBuilder) shortens the string.</span></span>

## <a name="modifying-the-stringbuilder-string"></a><span data-ttu-id="4bcd7-130">修改 StringBuilder 字串</span><span class="sxs-lookup"><span data-stu-id="4bcd7-130">Modifying the StringBuilder String</span></span>

<span data-ttu-id="4bcd7-131">下表列出您可用來修改 [StringBuilder](xref:System.Text.StringBuilder) 內容的方法。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-131">The following table lists the methods you can use to modify the contents of a [StringBuilder](xref:System.Text.StringBuilder).</span></span>

<span data-ttu-id="4bcd7-132">方法名稱</span><span class="sxs-lookup"><span data-stu-id="4bcd7-132">Method name</span></span> | <span data-ttu-id="4bcd7-133">用法</span><span class="sxs-lookup"><span data-stu-id="4bcd7-133">Use</span></span>
----------- | ---
<span data-ttu-id="4bcd7-134">[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char))</span><span class="sxs-lookup"><span data-stu-id="4bcd7-134">[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char))</span></span> | <span data-ttu-id="4bcd7-135">將資訊附加至目前 [StringBuilder](xref:System.Text.StringBuilder) 的結尾。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-135">Appends information to the end of the current [StringBuilder](xref:System.Text.StringBuilder).</span></span>
<span data-ttu-id="4bcd7-136">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="4bcd7-136">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span></span> | <span data-ttu-id="4bcd7-137">將字串中傳遞的格式規範取代為格式化的文字。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-137">Replaces a format specifier passed in a string with formatted text.</span></span>
<span data-ttu-id="4bcd7-138">[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char))</span><span class="sxs-lookup"><span data-stu-id="4bcd7-138">[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char))</span></span> | <span data-ttu-id="4bcd7-139">將字串或物件插入目前 [StringBuilder](xref:System.Text.StringBuilder) 的指定索引。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-139">Inserts a string or object into the specified index of the current [StringBuilder](xref:System.Text.StringBuilder).</span></span>
<span data-ttu-id="4bcd7-140">[StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="4bcd7-140">[StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32))</span></span> | <span data-ttu-id="4bcd7-141">從目前 [StringBuilder](xref:System.Text.StringBuilder) 移除指定的字元數。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-141">Removes a specified number of characters from the current [StringBuilder](xref:System.Text.StringBuilder).</span></span>
<span data-ttu-id="4bcd7-142">[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char))</span><span class="sxs-lookup"><span data-stu-id="4bcd7-142">[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char))</span></span> | <span data-ttu-id="4bcd7-143">取代指定索引處的指定字元。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-143">Replaces a specified character at a specified index.</span></span>

### <a name="append"></a><span data-ttu-id="4bcd7-144">附加</span><span class="sxs-lookup"><span data-stu-id="4bcd7-144">Append</span></span>

<span data-ttu-id="4bcd7-145">[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) 方法可以用來將物件的文字或字串表示新增至目前 [StringBuilder](xref:System.Text.StringBuilder) 所代表的字串結尾。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-145">The [StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) method can be used to add text or a string representation of an object to the end of a string represented by the current [StringBuilder](xref:System.Text.StringBuilder).</span></span> <span data-ttu-id="4bcd7-146">下列範例會將 [StringBuilder](xref:System.Text.StringBuilder) 初始化為 "Hello World"，然後附加一些文字到物件的結尾。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-146">The following example initializes a [StringBuilder](xref:System.Text.StringBuilder) to "Hello World" and then appends some text to the end of the object.</span></span> <span data-ttu-id="4bcd7-147">會視需要自動配置空格。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-147">Space is allocated automatically as needed.</span></span>

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Append(" What a beautiful day.");
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello World! What a beautiful day.
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Append(" What a beautiful day.")
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello World! What a beautiful day.
```

### <a name="appendformat"></a><span data-ttu-id="4bcd7-148">AppendFormat</span><span class="sxs-lookup"><span data-stu-id="4bcd7-148">AppendFormat</span></span>

<span data-ttu-id="4bcd7-149">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) 方法會將文字新增至 [StringBuilder](xref:System.Text.StringBuilder) 物件的結尾。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-149">The [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) method adds text to the end of the [StringBuilder](xref:System.Text.StringBuilder) object.</span></span> <span data-ttu-id="4bcd7-150">它支援複合格式設定功能 (如需詳細資訊，請參閱[複合格式設定](composite-format.md))，方法是呼叫要格式化之物件的 [IFormattable](xref:System.IFormattable) 實作。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-150">It supports the composite formatting feature (for more information, see [Composite Formatting](composite-format.md)) by calling the [IFormattable](xref:System.IFormattable) implementation of the object or objects to be formatted.</span></span> <span data-ttu-id="4bcd7-151">因此，它接受數值、日期和時間，以及列舉值的標準格式字串，數值及日期和時間的自訂格式字串，以及為自訂類型定義的格式字串。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-151">Therefore, it accepts the standard format strings for numeric, date and time, and enumeration values, the custom format strings for numeric and date and time values, and the format strings defined for custom types.</span></span> <span data-ttu-id="4bcd7-152">(如需格式設定的資訊，請參閱[格式化類型](formatting-types.md)。)您可以使用這個方法，自訂變數的格式，並將那些值附加到 [StringBuilder](xref:System.Text.StringBuilder)。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-152">(For information about formatting, see [Formatting Types](formatting-types.md).) You can use this method to customize the format of variables and append those values to a [StringBuilder](xref:System.Text.StringBuilder).</span></span> <span data-ttu-id="4bcd7-153">下列範例會使用 AppendFormat 方法，將格式化為貨幣值的整數值，放到 [StringBuilder](xref:System.Text.StringBuilder) 物件的結尾。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-153">The following example uses the AppendFormat method to place an integer value formatted as a currency value at the end of a [StringBuilder](xref:System.Text.StringBuilder) object.</span></span>

```csharp
int MyInt = 25; 
StringBuilder MyStringBuilder = new StringBuilder("Your total is ");
MyStringBuilder.AppendFormat("{0:C} ", MyInt);
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Your total is $25.00
```

```vb
Dim MyInt As Integer = 25
Dim MyStringBuilder As New StringBuilder("Your total is ")
MyStringBuilder.AppendFormat("{0:C} ", MyInt)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'     Your total is $25.00 
```

### <a name="insert"></a><span data-ttu-id="4bcd7-154">Insert</span><span class="sxs-lookup"><span data-stu-id="4bcd7-154">Insert</span></span>

<span data-ttu-id="4bcd7-155">[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) 方法會將字串或物件新增至目前 [StringBuilder](xref:System.Text.StringBuilder) 物件中的指定位置。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-155">The [StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) method adds a string or object to a specified position in the current [StringBuilder](xref:System.Text.StringBuilder) object.</span></span> <span data-ttu-id="4bcd7-156">下列範例會使用這個方法，在 [StringBuilder](xref:System.Text.StringBuilder) 物件的第六個位置插入一個字。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-156">The following example uses this method to insert a word into the sixth position of a [StringBuilder](xref:System.Text.StringBuilder) object.</span></span>

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Insert(6,"Beautiful ");
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello Beautiful World!
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Insert(6, "Beautiful ")
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'      Hello Beautiful World!
```

### <a name="remove"></a><span data-ttu-id="4bcd7-157">移除</span><span class="sxs-lookup"><span data-stu-id="4bcd7-157">Remove</span></span>

<span data-ttu-id="4bcd7-158">您可以使用 [StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) 方法，從目前 [StringBuilder](xref:System.Text.StringBuilder) 物件移除指定的字元數 (從指定的以零為起始的索引處開始移除)。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-158">You can use the [StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) method to remove a specified number of characters from the current [StringBuilder](xref:System.Text.StringBuilder) object, beginning at a specified zero-based index.</span></span> <span data-ttu-id="4bcd7-159">下列範例會使用 [Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) 方法來縮短 [StringBuilder](xref:System.Text.StringBuilder) 物件。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-159">The following example uses the [Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) method to shorten a [StringBuilder](xref:System.Text.StringBuilder) object.</span></span>

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Remove(5,7);
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Remove(5, 7)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello
```

### <a name="replace"></a><span data-ttu-id="4bcd7-160">取代</span><span class="sxs-lookup"><span data-stu-id="4bcd7-160">Replace</span></span>

<span data-ttu-id="4bcd7-161">[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | 取代指定索引處的指定字元。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-161">The [StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Replaces a specified character at a specified index.</span></span>
<span data-ttu-id="4bcd7-162">方法可以用來將 [StringBuilder](xref:System.Text.StringBuilder) 物件內的字元取代為另一個指定的字元。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-162">method can be used to replace characters within the [StringBuilder](xref:System.Text.StringBuilder) object with another specified character.</span></span> <span data-ttu-id="4bcd7-163">下列範例使用 [StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | 取代指定索引處的指定字元。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-163">The following example uses the [Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Replaces a specified character at a specified index.</span></span>
<span data-ttu-id="4bcd7-164">方法來搜尋 [StringBuilder](xref:System.Text.StringBuilder) 物件中所有的驚嘆號字元 (!) 執行個體，並取代為問號字元 (?)。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-164">method to search a [StringBuilder](xref:System.Text.StringBuilder) object for all instances of the exclamation point character (!) and replace them with the question mark character (?).</span></span>
 
 ```csharp
 StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Replace('!', '?');
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello World?
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Replace("!"c, "?"c)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello World?
```

## <a name="converting-a-stringbuilder-object-to-a-string"></a><span data-ttu-id="4bcd7-165">將 StringBuilder 物件轉換為字串</span><span class="sxs-lookup"><span data-stu-id="4bcd7-165">Converting a StringBuilder Object to a String</span></span>

<span data-ttu-id="4bcd7-166">您必須先將 [StringBuilder](xref:System.Text.StringBuilder) 物件轉換成 [String](xref:System.String) 物件，才能將 [StringBuilder](xref:System.Text.StringBuilder) 物件所代表的字串傳遞給具有 [String](xref:System.String) 參數的方法，或將它顯示在使用者介面。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-166">You must convert the [StringBuilder](xref:System.Text.StringBuilder) object to a [String](xref:System.String) object before you can pass the string represented by the [StringBuilder](xref:System.Text.StringBuilder) object to a method that has a [String](xref:System.String) parameter or display it in the user interface.</span></span> <span data-ttu-id="4bcd7-167">您可以藉由呼叫 [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) 方法執行這項轉換。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-167">You do this conversion by calling the [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) method.</span></span> <span data-ttu-id="4bcd7-168">下列範例會呼叫許多 [StringBuilder](xref:System.Text.StringBuilder) 方法，然後呼叫 [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) 方法來顯示字串。</span><span class="sxs-lookup"><span data-stu-id="4bcd7-168">The following example calls a number of [StringBuilder](xref:System.Text.StringBuilder) methods and then calls the [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) method to display the string.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      StringBuilder sb = new StringBuilder();
      bool flag = true;
      string[] spellings = { "recieve", "receeve", "receive" };
      sb.AppendFormat("Which of the following spellings is {0}:", flag);
      sb.AppendLine();
      for (int ctr = 0; ctr <= spellings.GetUpperBound(0); ctr++) {
         sb.AppendFormat("   {0}. {1}", ctr, spellings[ctr]);
         sb.AppendLine();
      }
      sb.AppendLine();
      Console.WriteLine(sb.ToString());
   }
}
// The example displays the following output:
//       Which of the following spellings is True:
//          0. recieve
//          1. receeve
//          2. receive
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim sb As New StringBuilder()
      Dim flag As Boolean = True
      Dim spellings() As String = { "recieve", "receeve", "receive" }
      sb.AppendFormat("Which of the following spellings is {0}:", flag)
      sb.AppendLine()
      For ctr As Integer = 0 To spellings.GetUpperBound(0)
         sb.AppendFormat("   {0}. {1}", ctr, spellings(ctr))
         sb.AppendLine()
      Next
      sb.AppendLine()
      Console.WriteLine(sb.ToString())
   End Sub
End Module
' The example displays the following output:
'       Which of the following spellings is True:
'          0. recieve
'          1. receeve
'          2. receive
```

## <a name="see-also"></a><span data-ttu-id="4bcd7-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bcd7-169">See Also</span></span>

[<span data-ttu-id="4bcd7-170">System.Text.StringBuilder</span><span class="sxs-lookup"><span data-stu-id="4bcd7-170">System.Text.StringBuilder</span></span>](xref:System.Text.StringBuilder)

[<span data-ttu-id="4bcd7-171">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="4bcd7-171">Basic string operations</span></span>](basic-string-operations.md)

[<span data-ttu-id="4bcd7-172">格式化類型</span><span class="sxs-lookup"><span data-stu-id="4bcd7-172">Formatting types</span></span>](formatting-types.md)

