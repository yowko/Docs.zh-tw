---
title: "類型轉換"
description: "類型轉換"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c9a53222-89cb-47e5-983d-4f0f204e31ba
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 0a774a170b7703b900c2044708b07faeb4e51548
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="type-conversion"></a><span data-ttu-id="53960-104">類型轉換</span><span class="sxs-lookup"><span data-stu-id="53960-104">Type conversion</span></span>

<span data-ttu-id="53960-105">每個值都有相關聯的類型，該類型定義屬性，例如配置給值的空間量、能夠擁有的可能值範圍，以及提供的成員。</span><span class="sxs-lookup"><span data-stu-id="53960-105">Every value has an associated type, which defines attributes such as the amount of space allocated to the value, the range of possible values it can have, and the members that it makes available.</span></span> <span data-ttu-id="53960-106">許多值都可以表示成多種類型。</span><span class="sxs-lookup"><span data-stu-id="53960-106">Many values can be expressed as more than one type.</span></span> <span data-ttu-id="53960-107">例如，數值 `4` 就可以表示成整數值或浮點數值。</span><span class="sxs-lookup"><span data-stu-id="53960-107">For example, the value `4` can be expressed as an integer or a floating-point value.</span></span> <span data-ttu-id="53960-108">類型轉換會建立新類型的值，與舊類型的值相等，但是不一定會保留原始物件的識別 (或實際的值)。</span><span class="sxs-lookup"><span data-stu-id="53960-108">Type conversion creates a value in a new type that is equivalent to the value of an old type, but does not necessarily preserve the identity (or exact value) of the original object.</span></span>

<span data-ttu-id="53960-109">.NET 自動支援下列轉換︰</span><span class="sxs-lookup"><span data-stu-id="53960-109">.NET automatically supports the following conversions:</span></span>

* <span data-ttu-id="53960-110">從衍生類別轉換成基底類別。</span><span class="sxs-lookup"><span data-stu-id="53960-110">Conversion from a derived class to a base class.</span></span> <span data-ttu-id="53960-111">舉例來說，這表示任何類別或結構的執行個體都可以轉換成 [Object](xref:System.Object) 執行個體。</span><span class="sxs-lookup"><span data-stu-id="53960-111">This means, for example, that an instance of any class or structure can be converted to an [Object](xref:System.Object) instance.</span></span> <span data-ttu-id="53960-112">這種轉換不需要轉型運算子。</span><span class="sxs-lookup"><span data-stu-id="53960-112">This conversion does not require a casting operator.</span></span>

* <span data-ttu-id="53960-113">從基底類別轉換回原始的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="53960-113">Conversion from a base class back to the original derived class.</span></span> <span data-ttu-id="53960-114">在 C# 中，這種轉換需要轉型運算子。</span><span class="sxs-lookup"><span data-stu-id="53960-114">In C#, this conversion requires a casting operator.</span></span> <span data-ttu-id="53960-115">在 Visual Basic 中，如果已 `Option Strict` 開啟則需要 `CType` 運算子。</span><span class="sxs-lookup"><span data-stu-id="53960-115">In Visual Basic, it requires the `CType` operator if `Option Strict` is on.</span></span> 

* <span data-ttu-id="53960-116">從實作介面的類型轉換成代表該介面的介面物件。</span><span class="sxs-lookup"><span data-stu-id="53960-116">Conversion from a type that implements an interface to an interface object that represents that interface.</span></span> <span data-ttu-id="53960-117">這種轉換不需要轉型運算子。</span><span class="sxs-lookup"><span data-stu-id="53960-117">This conversion does not require a casting operator.</span></span>

* <span data-ttu-id="53960-118">從介面物件轉換回實作該介面的原始類型。</span><span class="sxs-lookup"><span data-stu-id="53960-118">Conversion from an interface object back to the original type that implements that interface.</span></span> <span data-ttu-id="53960-119">在 C# 中，這種轉換需要轉型運算子。</span><span class="sxs-lookup"><span data-stu-id="53960-119">In C#, this conversion requires a casting operator.</span></span> <span data-ttu-id="53960-120">在 Visual Basic 中，如果已 `Option Strict` 開啟則需要 `CType` 運算子。</span><span class="sxs-lookup"><span data-stu-id="53960-120">In Visual Basic, it requires the `CType` operator if `Option Strict` is on.</span></span> 

<span data-ttu-id="53960-121">除了這些自動轉換以外，.NET 還提供多項支援自訂類型轉換的功能。</span><span class="sxs-lookup"><span data-stu-id="53960-121">In addition to these automatic conversions, .NET provides several features that support custom type conversion.</span></span> <span data-ttu-id="53960-122">這些需求包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="53960-122">These include the following:</span></span> 

* <span data-ttu-id="53960-123">`Implicit` 運算子，這個運算子定義類型之間可用的擴展轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-123">The `Implicit` operator, which defines the available widening conversions between types.</span></span> <span data-ttu-id="53960-124">如需詳細資訊，請參閱[使用 Implicit 運算子進行隱含轉換](#implicit-conversion-with-the-implicit-operator)一節。</span><span class="sxs-lookup"><span data-stu-id="53960-124">For more information, see the [Implicit conversion with the Implicit operator](#implicit-conversion-with-the-implicit-operator) section.</span></span>

* <span data-ttu-id="53960-125">`Explicit` 運算子，這個運算子定義類型之間可用的縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-125">The `Explicit` operator, which defines the available narrowing conversions between types.</span></span> <span data-ttu-id="53960-126">如需詳細資訊，請參閱[使用 Explicit 運算子進行明確轉換](#explicit-conversion-with-the-explicit-operator)一節。</span><span class="sxs-lookup"><span data-stu-id="53960-126">For more information, see the [Explicit conversion with the Explicit operator](#explicit-conversion-with-the-explicit-operator) section.</span></span>

* <span data-ttu-id="53960-127">[IConvertible](xref:System.IConvertible) 介面，這個介面定義轉換至每一個基底 .NET 資料類型的方式。</span><span class="sxs-lookup"><span data-stu-id="53960-127">The [IConvertible](xref:System.IConvertible) interface, which defines conversions to each of the base .NET data types.</span></span> <span data-ttu-id="53960-128">如需詳細資訊，請參閱 [IConvertible 介面](#the-iconvertible-interface)一節。</span><span class="sxs-lookup"><span data-stu-id="53960-128">For more information, see the [The IConvertible interface](#the-iconvertible-interface) section.</span></span>

* <span data-ttu-id="53960-129">[Convert](xref:System.Convert) 類別，這個類別提供一組方法以實作 `IConvertible` 介面中的方法。</span><span class="sxs-lookup"><span data-stu-id="53960-129">The [Convert](xref:System.Convert) class, which provides a set of methods that implement the methods in the `IConvertible` interface.</span></span> <span data-ttu-id="53960-130">如需詳細資訊，請參閱 [Convert 類別](#the-convert-class)一節。</span><span class="sxs-lookup"><span data-stu-id="53960-130">For more information, see the [The Convert class](#the-convert-class) section.</span></span>

* <span data-ttu-id="53960-131">[TypeConverter](xref:System.ComponentModel.TypeConverter) 類別，這個類別是基底類別，並可擴充以支援從指定的類型轉換至其他任何類型。</span><span class="sxs-lookup"><span data-stu-id="53960-131">The [TypeConverter](xref:System.ComponentModel.TypeConverter) class, which is a base class that can be extended to support the conversion of a specified type to any other type.</span></span> <span data-ttu-id="53960-132">如需詳細資訊，請參閱 [TypeConverter 類別](#the-typeconverter-class)一節。</span><span class="sxs-lookup"><span data-stu-id="53960-132">For more information, see the [The TypeConverter class](#the-typeconverter-class) section.</span></span>

## <a name="implicit-conversion-with-the-implicit-operator"></a><span data-ttu-id="53960-133">使用 Implicit 運算子進行隱含轉換</span><span class="sxs-lookup"><span data-stu-id="53960-133">Implicit conversion with the Implicit operator</span></span>

<span data-ttu-id="53960-134">擴展轉換包含從現有類型的值來建立新的值，這個類型具有比目標類型更嚴格的範圍或更受限制的成員清單。</span><span class="sxs-lookup"><span data-stu-id="53960-134">Widening conversions involve the creation of a new value from the value of an existing type that has either a more restrictive range or a more restricted member list than the target type.</span></span> <span data-ttu-id="53960-135">擴展轉換不可能導致資料遺失 (雖然可能導致精確度降低)。</span><span class="sxs-lookup"><span data-stu-id="53960-135">Widening conversions cannot result in data loss (although they may result in a loss of precision).</span></span> <span data-ttu-id="53960-136">因為不可能遺失資料，編譯器可以隱含地 (或直接地) 處理轉換，而不需要使用明確的轉換方法或轉型運算子。</span><span class="sxs-lookup"><span data-stu-id="53960-136">Because data cannot be lost, compilers can handle the conversion implicitly or transparently, without requiring the use of an explicit conversion method or a casting operator.</span></span>

> [!NOTE]
> <span data-ttu-id="53960-137">雖然執行隱含轉換的程式碼可以呼叫轉換方法或使用轉型運算子，但支援隱含轉換的編譯器並不需要這些動作。</span><span class="sxs-lookup"><span data-stu-id="53960-137">Although code that performs an implicit conversion can call a conversion method or use a casting operator, their use is not required by compilers that support implicit conversions.</span></span>

<span data-ttu-id="53960-138">例如，[Decimal](xref:System.Decimal) 類型支援從 [Byte](xref:System.Byte)、[Char](xref:System.Char)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32) 和 [UInt64](xref:System.UInt64) 值的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-138">For example, the [Decimal](xref:System.Decimal) type supports implicit conversions from [Byte](xref:System.Byte), [Char](xref:System.Char), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), and [UInt64](xref:System.UInt64) values.</span></span> <span data-ttu-id="53960-139">下列範例說明其中一部分隱含轉換在指派值給 `Decimal` 變數時的情形。</span><span class="sxs-lookup"><span data-stu-id="53960-139">The following example illustrates some of these implicit conversions in assigning values to a `Decimal` variable.</span></span>

```csharp
byte byteValue = 16;
short shortValue = -1024;
int intValue = -1034000;
long longValue = 1152921504606846976;
ulong ulongValue = UInt64.MaxValue;

decimal decimalValue;

decimalValue = byteValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  byteValue.GetType().Name, decimalValue); 

decimalValue = shortValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  shortValue.GetType().Name, decimalValue); 

decimalValue = intValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  intValue.GetType().Name, decimalValue); 

decimalValue = longValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  longValue.GetType().Name, decimalValue); 

decimalValue = ulongValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  longValue.GetType().Name, decimalValue); 
// The example displays the following output:
//    After assigning a Byte value, the Decimal value is 16.
//    After assigning a Int16 value, the Decimal value is -1024.
//    After assigning a Int32 value, the Decimal value is -1034000.
//    After assigning a Int64 value, the Decimal value is 1152921504606846976.
//    After assigning a Int64 value, the Decimal value is 18446744073709551615.
```

```vb
Dim byteValue As Byte = 16
Dim shortValue As Short = -1024
Dim intValue As Integer = -1034000
Dim longValue As Long = CLng(1024^6)
Dim ulongValue As ULong = ULong.MaxValue

Dim decimalValue As Decimal

decimalValue = byteValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  byteValue.GetType().Name, decimalValue) 

decimalValue = shortValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  shortValue.GetType().Name, decimalValue) 

decimalValue = intValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  intValue.GetType().Name, decimalValue) 

decimalValue = longValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  longValue.GetType().Name, decimalValue) 

decimalValue = ulongValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  longValue.GetType().Name, decimalValue) 
' The example displays the following output:
'    After assigning a Byte value, the Decimal value is 16.
'    After assigning a Int16 value, the Decimal value is -1024.
'    After assigning a Int32 value, the Decimal value is -1034000.
'    After assigning a Int64 value, the Decimal value is 1152921504606846976.
'    After assigning a Int64 value, the Decimal value is 18446744073709551615.
```

<span data-ttu-id="53960-140">如果特定的語言編譯器支援自訂運算子，您也可以在自己的自訂類型中定義隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-140">If a particular language compiler supports custom operators, you can also define implicit conversions in your own custom types.</span></span> <span data-ttu-id="53960-141">下列範例針對使用正負號和大小表示之名為 `ByteWithSign` 的帶正負號位元組資料類型，提供部分實作。</span><span class="sxs-lookup"><span data-stu-id="53960-141">The following example provides a partial implementation of a signed byte data type named `ByteWithSign` that uses sign-and-magnitude representation.</span></span> <span data-ttu-id="53960-142">它支援將 [Byte](xref:System.Byte) 和 [SByte](xref:System.SByte) 值隱含轉換為 `ByteWithSign` 值。</span><span class="sxs-lookup"><span data-stu-id="53960-142">It supports implicit conversion of [Byte](xref:System.Byte) and [SByte](xref:System.SByte) values to `ByteWithSign` values.</span></span>

```csharp
public struct ByteWithSign
{
   private SByte signValue; 
   private Byte value;

   public static implicit operator ByteWithSign(SByte value) 
   {
      ByteWithSign newValue;
      newValue.signValue = (SByte) Math.Sign(value);
      newValue.value = (byte) Math.Abs(value);
      return newValue;
   }  

   public static implicit operator ByteWithSign(Byte value)
   {
      ByteWithSign  newValue;
      newValue.signValue = 1;
      newValue.value = value;
      return newValue;
   }

   public override string ToString()
   { 
      return (signValue * value).ToString();
   }
}
```

```vb
Public Structure ByteWithSign
   Private signValue As SByte 
   Private value As Byte

   Public Overloads Shared Widening Operator CType(value As SByte) As ByteWithSign
      Dim newValue As ByteWithSign
      newValue.signValue = CSByte(Math.Sign(value))
      newValue.value = CByte(Math.Abs(value))
      Return newValue
   End Operator  

   Public Overloads Shared Widening Operator CType(value As Byte) As ByteWithSign
      Dim NewValue As ByteWithSign
      newValue.signValue = 1
      newValue.value = value
      Return newValue
   End Operator

   Public Overrides Function ToString() As String 
      Return (signValue * value).ToString()
   End Function
End Structure
```

<span data-ttu-id="53960-143">然後，用戶端程式碼可以宣告 `ByteWithSign` 變數並指派 [Byte](xref:System.Byte) 和 [SByte](xref:System.SByte) 值給它，而不需要執行任何明確的轉換，也不需要使用任何轉型運算子，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="53960-143">Client code can then declare a `ByteWithSign` variable and assign it [Byte](xref:System.Byte) and [SByte](xref:System.SByte) values without performing any explicit conversions or using any casting operators, as the following example shows.</span></span>

```csharp
SByte sbyteValue = -120;
ByteWithSign value = sbyteValue;
Console.WriteLine(value);
value = Byte.MaxValue;
Console.WriteLine(value);
// The example displays the following output:
//       -120
//       255
```

```vb
Dim sbyteValue As SByte = -120
Dim value As ByteWithSign = sbyteValue
Console.WriteLine(value.ToString()) 
value = Byte.MaxValue
Console.WriteLine(value.ToString()) 
' The example displays the following output:
'       -120
'       255
```

## <a name="explicit-conversion-with-the-explicit-operator"></a><span data-ttu-id="53960-144">使用 Explicit 運算子進行明確轉換</span><span class="sxs-lookup"><span data-stu-id="53960-144">Explicit conversion with the Explicit operator</span></span>

<span data-ttu-id="53960-145">縮小轉換包含從現有類型的值來建立新的值，這個類型具有比目標類型更廣的範圍或更大的成員清單。</span><span class="sxs-lookup"><span data-stu-id="53960-145">Narrowing conversions involve the creation of a new value from the value of an existing type that has either a greater range or a larger member list than the target type.</span></span> <span data-ttu-id="53960-146">因為縮小轉換可能導致資料遺失，編譯器通常會要求必須透過呼叫轉換方法或轉型運算子來明確執行轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-146">Because a narrowing conversion can result in a loss of data, compilers often require that the conversion be made explicit through a call to a conversion method or a casting operator.</span></span> <span data-ttu-id="53960-147">也就是說，開發人員程式碼中必須明確處理轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-147">That is, the conversion must be handled explicitly in developer code.</span></span> 

> [!NOTE]
> <span data-ttu-id="53960-148">縮小轉換之所以需要轉換方法或轉型運算子，主要目的是讓開發人員知道可能遺失資料，或可能發生 [OverflowException](xref:System.OverflowException)，以便在程式碼中處理。</span><span class="sxs-lookup"><span data-stu-id="53960-148">The major purpose of requiring a conversion method or casting operator for narrowing conversions is to make the developer aware of the possibility of data loss or an [OverflowException](xref:System.OverflowException) so that it can be handled in code.</span></span> <span data-ttu-id="53960-149">不過，某些編譯器可能會放寬這項需求。</span><span class="sxs-lookup"><span data-stu-id="53960-149">However, some compilers can relax this requirement.</span></span> <span data-ttu-id="53960-150">例如，在 Visual Basic 中，如果 `Option Strict` 已關閉 (此為預設)，則 Visual Basic 編譯器會嘗試隱含地執行縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-150">For example, in Visual Basic, if `Option Strict` is off (its default setting), the Visual Basic compiler tries to perform narrowing conversions implicitly.</span></span>

<span data-ttu-id="53960-151">例如，[UInt32](xref:System.UInt32)、[Int64](xref:System.Int64) 和 [UInt64](xref:System.UInt64) 資料類型的範圍超過 [Int32](xref:System.Int32) 資料類型的範圍，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="53960-151">For example, the [UInt32](xref:System.UInt32), [Int64](xref:System.Int64), and [UInt64](xref:System.UInt64) data types have ranges that exceed that the [Int32](xref:System.Int32) data type, as the following table shows.</span></span>

<span data-ttu-id="53960-152">類型</span><span class="sxs-lookup"><span data-stu-id="53960-152">Type</span></span> | <span data-ttu-id="53960-153">與 Int32 的範圍比較</span><span class="sxs-lookup"><span data-stu-id="53960-153">Comparison with range of Int32</span></span>
---- | ------------------------------
[<span data-ttu-id="53960-154">Int64</span><span class="sxs-lookup"><span data-stu-id="53960-154">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="53960-155">[Int64.MaxValue](xref:System.Int64.MaxValue) 大於 [Int32.MaxValue](xref:System.Int32#System_Int32_MaxValue)，而 [Int64.MinValue](xref:System.Int64.MinValue) 小於 (負值範圍大於) [Int32.MinValue](xref:System.Int32#System_Int32_MinValue)。</span><span class="sxs-lookup"><span data-stu-id="53960-155">[Int64.MaxValue](xref:System.Int64.MaxValue) is greater than [Int32.MaxValue](xref:System.Int32#System_Int32_MaxValue), and [Int64.MinValue](xref:System.Int64.MinValue) is less than (has a greater negative range than) [Int32.MinValue](xref:System.Int32#System_Int32_MinValue).</span></span>
[<span data-ttu-id="53960-156">UInt32</span><span class="sxs-lookup"><span data-stu-id="53960-156">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="53960-157">[UInt32.MaxValue](xref:System.UInt32.MaxValue) 大於 [Int32.MaxValue](xref:System.Int32.MaxValue)。</span><span class="sxs-lookup"><span data-stu-id="53960-157">[UInt32.MaxValue](xref:System.UInt32.MaxValue) is greater than [Int32.MaxValue](xref:System.Int32.MaxValue).</span></span>
[<span data-ttu-id="53960-158">UInt64</span><span class="sxs-lookup"><span data-stu-id="53960-158">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="53960-159">[UInt64.MaxValue](xref:System.UInt64.MaxValue) 大於 [Int32.MaxValue](xref:System.Int32.MaxValue)。</span><span class="sxs-lookup"><span data-stu-id="53960-159">[UInt64.MaxValue](xref:System.UInt64.MaxValue) is greater than [Int32.MaxValue](xref:System.Int32.MaxValue).</span></span>

<span data-ttu-id="53960-160">為了處理縮小轉換，.NET 允許類型定義 `Explicit` 運算子。</span><span class="sxs-lookup"><span data-stu-id="53960-160">To handle such narrowing conversions, .NET allows types to define an `Explicit` operator.</span></span> <span data-ttu-id="53960-161">然後，個別語言編譯器就可以使用自己的語法來實作這個運算子，也可以呼叫 [Convert](xref:System.Convert) 類型的成員來執行轉換 </span><span class="sxs-lookup"><span data-stu-id="53960-161">Individual language compilers can then implement this operator using their own syntax, or a member of the [Convert](xref:System.Convert) class can be called to perform the conversion.</span></span> <span data-ttu-id="53960-162">(如需 `Convert` 類別的詳細資訊，請參閱本主題後文的 [Convert 類別](#the-convert-class))。下列範例說明如何使用語言功能，將這些可能超出範圍的整數值明確轉換至 [Int32](xref:System.Int32) 值。</span><span class="sxs-lookup"><span data-stu-id="53960-162">(For more information about the `Convert` class, see [The Convert class](#the-convert-class) later in this topic.) The following example illustrates the use of language features to handle the explicit conversion of these potentially out-of-range integer values to [Int32](xref:System.Int32) values.</span></span> 

```csharp
long number1 = int.MaxValue + 20L;
uint number2 = int.MaxValue - 1000;
ulong number3 = int.MaxValue;

int intNumber;

try {
   intNumber = checked((int) number1);
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                     number1.GetType().Name, intNumber); 
}
catch (OverflowException) {
   if (number1 > int.MaxValue)
      Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                        number1, int.MaxValue);
   else
      Console.WriteLine("Conversion failed: {0} is less than {1}.", 
                        number1, int.MinValue);
}

try {
   intNumber = checked((int) number2);
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                     number2.GetType().Name, intNumber); 
}
catch (OverflowException) {
   Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                     number2, int.MaxValue);
}

try {
   intNumber = checked((int) number3);
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                     number3.GetType().Name, intNumber); 
}
catch (OverflowException) {
   Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                     number1, int.MaxValue);
}

// The example displays the following output:
//    Conversion failed: 2147483667 exceeds 2147483647.
//    After assigning a UInt32 value, the Integer value is 2147482647.
//    After assigning a UInt64 value, the Integer value is 2147483647.
```

```vb
Dim number1 As Long = Integer.MaxValue + 20L
Dim number2 As UInteger = Integer.MaxValue - 1000
Dim number3 As ULong = Integer.MaxValue

Dim intNumber As Integer

Try
   intNumber = CInt(number1)
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                       number1.GetType().Name, intNumber)
Catch e As OverflowException
   If number1 > Integer.MaxValue Then
      Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                                        number1, Integer.MaxValue)
   Else
      Console.WriteLine("Conversion failed: {0} is less than {1}.\n", 
                                        number1, Integer.MinValue)
   End If
End Try

Try
   intNumber = CInt(number2)
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                       number2.GetType().Name, intNumber)
Catch e As OverflowException
   Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                                     number2, Integer.MaxValue)
End Try

Try
   intNumber = CInt(number3)
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                       number3.GetType().Name, intNumber)
Catch e As OverflowException
   Console.WriteLine("Conversion failed: {0} exceeds {1}.",
                                     number1, Integer.MaxValue)
End Try
' The example displays the following output:
'    Conversion failed: 2147483667 exceeds 2147483647.
'    After assigning a UInt32 value, the Integer value is 2147482647.
'    After assigning a UInt64 value, the Integer value is 2147483647.
```

<span data-ttu-id="53960-163">明確轉換在不同的語言中可能會產生不同的結果，這些結果可能與對應的 [Convert](xref:System.Convert) 方法所傳回的值不同。</span><span class="sxs-lookup"><span data-stu-id="53960-163">Explicit conversions can produce different results in different languages, and these results can differ from the value returned by the corresponding [Convert](xref:System.Convert) method.</span></span> <span data-ttu-id="53960-164">好比說，如果 [Double](xref:System.Double) 值 **12.63251** 轉換為 [Int32](xref:System.Int32)，則 .NET [Convert.ToInt32(Double)](xref:System.Convert.ToInt32(System.Double)) 和 Visual Basic `CInt` 方法都會四捨五入 [Double](xref:System.Double) 而傳回 **13**，但 C# `(int)` 運算子會截斷 [Double](xref:System.Double) 而傳回 **12**。</span><span class="sxs-lookup"><span data-stu-id="53960-164">For example, if the [Double](xref:System.Double) value **12.63251** is converted to an [Int32](xref:System.Int32), both the .NET [Convert.ToInt32(Double)](xref:System.Convert.ToInt32(System.Double)) and the Visual Basic `CInt` method method rounds the [Double](xref:System.Double) to return a value of **13**, but the C# `(int)` operator truncates the [Double](xref:System.Double) to return a value of **12**.</span></span> <span data-ttu-id="53960-165">同樣地，C# `(int)` 運算子不支援布林值對整數的轉換，但 Visual Basic `CInt` 方法會將 `true` 的值轉換為 **-1**。</span><span class="sxs-lookup"><span data-stu-id="53960-165">Similarly, the C# `(int)` operator does not support Boolean-to-integer conversion, but the Visual Basic `CInt` method converts a value of `true` to **-1**.</span></span> <span data-ttu-id="53960-166">反之，[Convert.ToInt32(Boolean)](xref:System.Convert.ToInt32(System.Boolean)) 方法會將 `true` 的值轉換為 **1**。</span><span class="sxs-lookup"><span data-stu-id="53960-166">On the other hand, the [Convert.ToInt32(Boolean)](xref:System.Convert.ToInt32(System.Boolean)) method converts a value of `true` to **1**.</span></span>

<span data-ttu-id="53960-167">大多數的編譯器都允許明確轉換以已檢查或未檢查的方式執行。</span><span class="sxs-lookup"><span data-stu-id="53960-167">Most compilers allow explicit conversions to be performed in a checked or unchecked manner.</span></span> <span data-ttu-id="53960-168">如果執行已檢查的轉換，當要轉換之類型的值不在目標類型的範圍內時，會擲回 [OverflowException](xref:System.OverflowException)。</span><span class="sxs-lookup"><span data-stu-id="53960-168">When a checked conversion is performed, an [OverflowException](xref:System.OverflowException) is thrown when the value of the type to be converted is outside the range of the target type.</span></span> <span data-ttu-id="53960-169">在同樣的狀況下執行未檢查的轉換時，轉換可能不會擲回例外狀況，但實際行為會變得不明確，且可能產生不正確的值。</span><span class="sxs-lookup"><span data-stu-id="53960-169">When an unchecked conversion is performed under the same conditions, the conversion might not throw an exception, but the exact behavior becomes undefined and an incorrect value might result.</span></span>

> [!NOTE]
> <span data-ttu-id="53960-170">在 C# 中，已檢查的轉換可以透過使用 `checked` 關鍵字搭配轉型運算子來執行，也可以指定 `/checked+` 編譯器選項來執行。</span><span class="sxs-lookup"><span data-stu-id="53960-170">In C#, checked conversions can be performed by using the `checked` keyword together with a casting operator, or by specifying the `/checked+` compiler option.</span></span> <span data-ttu-id="53960-171">相反地，未檢查的轉換可使用 `unchecked` 關鍵字搭配轉型運算子來執行，或可以指定 `/checked-` 編譯器選項來執行。</span><span class="sxs-lookup"><span data-stu-id="53960-171">Conversely, unchecked conversions can be performed by using the `unchecked` keyword together with the casting operator, or by specifying the `/checked-` compiler option.</span></span> <span data-ttu-id="53960-172">根據預設，明確轉換是未檢查的。</span><span class="sxs-lookup"><span data-stu-id="53960-172">By default, explicit conversions are unchecked.</span></span> <span data-ttu-id="53960-173">在 Visual Basic 中，您可以指定 `/removeintchecks-` 編譯器選項來執行已檢查的轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-173">In Visual Basic, checked conversions can be performed by specifying the `/removeintchecks-` compiler option.</span></span> <span data-ttu-id="53960-174">反之，您可以指定 `/removeintchecks+` 編譯器選項來執行未檢查的轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-174">Conversely, unchecked conversions can be performed by specifying the `/removeintchecks+` compiler option.</span></span> <span data-ttu-id="53960-175">根據預設，明確轉換是檢查的。</span><span class="sxs-lookup"><span data-stu-id="53960-175">By default, explicit conversions are checked.</span></span>

<span data-ttu-id="53960-176">下列 C# 範例使用 `checked` 和 `unchecked` 關鍵字，說明將超出 [Byte](xref:System.Byte) 範圍的值轉換為 `Byte` 時的行為差異。</span><span class="sxs-lookup"><span data-stu-id="53960-176">The following C# example uses the `checked` and `unchecked` keywords to illustrate the difference in behavior when a value outside the range of a [Byte](xref:System.Byte) is converted to a `Byte`.</span></span> <span data-ttu-id="53960-177">已檢查的轉換會擲回例外狀況，但未檢查的轉換會指派 [Byte.MaxValue](xref:System.Byte.MaxValue) 給 `Byte` 變數。</span><span class="sxs-lookup"><span data-stu-id="53960-177">The checked conversion throws an exception, but the unchecked conversion assigns [Byte.MaxValue](xref:System.Byte.MaxValue) to the `Byte` variable.</span></span>

```csharp
int largeValue = Int32.MaxValue;
byte newValue;

try {
   newValue = unchecked((byte) largeValue);
   Console.WriteLine("Converted the {0} value {1} to the {2} value {3}.", 
                     largeValue.GetType().Name, largeValue,
                     newValue.GetType().Name, newValue);
}
catch (OverflowException) {
   Console.WriteLine("{0} is outside the range of the Byte data type.", 
                     largeValue);
}

try {
   newValue = checked((byte) largeValue);
   Console.WriteLine("Converted the {0} value {1} to the {2} value {3}.", 
                     largeValue.GetType().Name, largeValue,
                     newValue.GetType().Name, newValue);
}
catch (OverflowException) {
   Console.WriteLine("{0} is outside the range of the Byte data type.", 
                     largeValue);
}
// The example displays the following output:
//    Converted the Int32 value 2147483647 to the Byte value 255.
//    2147483647 is outside the range of the Byte data type.
```

<span data-ttu-id="53960-178">如果特定的語言編譯器支援自訂多載運算子，您也可以在自己的自訂類型中定義明確轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-178">If a particular language compiler supports custom overloaded operators, you can also define explicit conversions in your own custom types.</span></span> <span data-ttu-id="53960-179">下列範例針對使用正負號和大小表示之名為 `ByteWithSign` 的帶正負號位元組資料類型，提供部分實作。</span><span class="sxs-lookup"><span data-stu-id="53960-179">The following example provides a partial implementation of a signed byte data type named `ByteWithSign` that uses sign-and-magnitude representation.</span></span> <span data-ttu-id="53960-180">它支援將 [Int32](xref:System.Int32) 和 [UInt32](xref:System.UInt32) 值明確轉換為 `ByteWithSign` 值。</span><span class="sxs-lookup"><span data-stu-id="53960-180">It supports explicit conversion of [Int32](xref:System.Int32) and [UInt32](xref:System.UInt32) values to `ByteWithSign` values.</span></span>

```csharp
public struct ByteWithSign
{
   private SByte signValue; 
   private Byte value;

   private const byte MaxValue = byte.MaxValue;
   private const int MinValue = -1 * byte.MaxValue;

   public static explicit operator ByteWithSign(int value) 
   {
      // Check for overflow.
      if (value > ByteWithSign.MaxValue || value < ByteWithSign.MinValue)
         throw new OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", 
                                                   value));

      ByteWithSign newValue;
      newValue.signValue = (SByte) Math.Sign(value);
      newValue.value = (byte) Math.Abs(value);
      return newValue;
   }  

   public static explicit operator ByteWithSign(uint value)
   {
      if (value > ByteWithSign.MaxValue) 
         throw new OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", 
                                                   value));

      ByteWithSign newValue;
      newValue.signValue = 1;
      newValue.value = (byte) value;
      return newValue;
   }

   public override string ToString()
   { 
      return (signValue * value).ToString();
   }
}
```

```vb
Public Structure ByteWithSign
   Private signValue As SByte 
   Private value As Byte

   Private Const MaxValue As Byte = Byte.MaxValue
   Private Const MinValue As Integer = -1 * Byte.MaxValue

   Public Overloads Shared Narrowing Operator CType(value As Integer) As ByteWithSign
      ' Check for overflow.
      If value > ByteWithSign.MaxValue Or value < ByteWithSign.MinValue Then
         Throw New OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", value))
      End If

      Dim newValue As ByteWithSign

      newValue.signValue = CSByte(Math.Sign(value))
      newValue.value = CByte(Math.Abs(value))
      Return newValue
   End Operator

   Public Overloads Shared Narrowing Operator CType(value As UInteger) As ByteWithSign
      If value > ByteWithSign.MaxValue Then 
         Throw New OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", value))
      End If

      Dim NewValue As ByteWithSign

      newValue.signValue = 1
      newValue.value = CByte(value)
      Return newValue
   End Operator

   Public Overrides Function ToString() As String 
      Return (signValue * value).ToString()
   End Function
End Structure
```

<span data-ttu-id="53960-181">然後，用戶端程式碼可以宣告 `ByteWithSign` 變數並指派 [Int32](xref:System.Int32) 和 [UInt32](xref:System.UInt32) 值給它 (如果指派包含轉型運算子的話)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="53960-181">Client code can then declare a `ByteWithSign` variable and assign it [Int32](xref:System.Int32) and [UInt32](xref:System.UInt32) values if the assignments include a casting operator, as the following example shows.</span></span>

```csharp
ByteWithSign value;

try {
   int intValue = -120;
   value = (ByteWithSign) intValue;
   Console.WriteLine(value);
}
catch (OverflowException e) {
   Console.WriteLine(e.Message);
}

try {
   uint uintValue = 1024;
   value = (ByteWithSign) uintValue;
   Console.WriteLine(value);
}
catch (OverflowException e) {
    Console.WriteLine(e.Message);
}
// The example displays the following output:
//       -120
//       '1024' is out of range of the ByteWithSign data type.
```

```vb
Dim value As ByteWithSign

Try  
   Dim intValue As Integer = -120
   value = CType(intValue, ByteWithSign)
   Console.WriteLine(value) 
Catch e As OverflowException
   Console.WriteLine(e.Message)
End Try

Try
   Dim uintValue As UInteger = 1024
   value = CType(uintValue, ByteWithSign)
   Console.WriteLine(value) 
Catch e As OverflowException
   Console.WriteLine(e.Message)
End Try
' The example displays the following output:
'       -120
'       '1024' is out of range of the ByteWithSign data type.
```

## <a name="the-iconvertible-interface"></a><span data-ttu-id="53960-182">IConvertible 介面</span><span class="sxs-lookup"><span data-stu-id="53960-182">The IConvertible interface</span></span>

<span data-ttu-id="53960-183">為了支援從任何類型轉換至通用語言執行平台基底類型，.NET 提供 [IConvertible](xref:System.IConvertible) 介面。</span><span class="sxs-lookup"><span data-stu-id="53960-183">To support the conversion of any type to a common language runtime base type, .NET provides the [IConvertible](xref:System.IConvertible) interface.</span></span> <span data-ttu-id="53960-184">實作類型需要提供下列項目：</span><span class="sxs-lookup"><span data-stu-id="53960-184">The implementing type is required to provide the following:</span></span>

* <span data-ttu-id="53960-185">傳回實作類型 [TypeCode](xref:System.TypeCode) 的方法。</span><span class="sxs-lookup"><span data-stu-id="53960-185">A method that returns the [TypeCode](xref:System.TypeCode) of the implementing type.</span></span>

* <span data-ttu-id="53960-186">將實作類型轉換為每一個通用語言執行平台基底類型 ([Boolean](xref:System.Boolean)、[Byte](xref:System.Byte)、[DateTime](xref:System.DateTime)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double) 等) 的方法。</span><span class="sxs-lookup"><span data-stu-id="53960-186">Methods to convert the implementing type to each common language runtime base type ([Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), and so on).</span></span>

* <span data-ttu-id="53960-187">將實作類型的執行個體轉換為另一個指定之類型的通用轉換方法。</span><span class="sxs-lookup"><span data-stu-id="53960-187">A generalized conversion method to convert an instance of the implementing type to another specified type.</span></span> <span data-ttu-id="53960-188">不支援的轉換應該擲回 [InvalidCastException](xref:System.InvalidCastException)。</span><span class="sxs-lookup"><span data-stu-id="53960-188">Conversions that are not supported should throw an [InvalidCastException](xref:System.InvalidCastException).</span></span>

<span data-ttu-id="53960-189">每一個通用語言執行平台基底類型 (亦即 [Boolean](xref:System.Boolean)、[Byte](xref:System.Byte)、[Char](xref:System.Char)、[DateTime](xref:System.DateTime)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte), [Single](xref:System.Single)、[String](xref:System.String)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32) 和 [UInt64](xref:System.UInt64)，以及 [DBNull](xref:System.DBNull) 和 [Enum](xref:System.Enum) 類型)，皆會實作 [IConvertible](xref:System.IConvertible) 介面。</span><span class="sxs-lookup"><span data-stu-id="53960-189">Each common language runtime base type (that is, the [Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [String](xref:System.String), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), and [UInt64](xref:System.UInt64), as well as the [DBNull](xref:System.DBNull) and [Enum](xref:System.Enum) types, implement the [IConvertible](xref:System.IConvertible) interface.</span></span> <span data-ttu-id="53960-190">不過，這些都是明確的介面實作，且只能透過 [IConvertible](xref:System.IConvertible) 介面變數來呼叫轉換方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="53960-190">However, these are explicit interface implementations; the conversion method can be called only through an [IConvertible](xref:System.IConvertible) interface variable, as the following example shows.</span></span> <span data-ttu-id="53960-191">這個範例將 [Int32](xref:System.Int32) 值轉換為其對等的 [Char](xref:System.Char) 值。</span><span class="sxs-lookup"><span data-stu-id="53960-191">This example converts an [Int32](xref:System.Int32) value to its equivalent [Char](xref:System.Char) value.</span></span>

```csharp
int codePoint = 1067;
IConvertible iConv = codePoint;
char ch = iConv.ToChar(null);
Console.WriteLine("Converted {0} to {1}.", codePoint, ch);
```

```vb
Dim codePoint As Integer = 1067
Dim iConv As IConvertible = codePoint
Dim ch As Char = iConv.ToChar(Nothing)
Console.WriteLine("Converted {0} to {1}.", codePoint, ch)
```

<span data-ttu-id="53960-192">由於必須呼叫其介面上的轉換方法，而不是呼叫實作類型上的轉換方法，這種需求使得明確介面實作相當耗費資源。</span><span class="sxs-lookup"><span data-stu-id="53960-192">The requirement to call the conversion method on its interface rather than on the implementing type makes explicit interface implementations relatively expensive.</span></span> <span data-ttu-id="53960-193">因此，在通用語言執行平台基底類型之間轉換時，我們建議您改為呼叫 [Convert](xref:System.Convert) 類別的適當成員。</span><span class="sxs-lookup"><span data-stu-id="53960-193">Instead, we recommend that you call the appropriate member of the [Convert](xref:System.Convert) class to convert between common language runtime base types.</span></span> <span data-ttu-id="53960-194">如需詳細資訊，請參閱下節的 [Convert 類別](#the-convert-class)。</span><span class="sxs-lookup"><span data-stu-id="53960-194">For more information, see the next section, [The Convert class](#the-convert-class).</span></span> 

> [!NOTE]
> <span data-ttu-id="53960-195">除了 .NET 提供的 [IConvertible](xref:System.IConvertible) 介面和 [Convert](xref:System.Convert) 類別之外，個別語言可能還會提供執行轉換的方式。</span><span class="sxs-lookup"><span data-stu-id="53960-195">In addition to the [IConvertible](xref:System.IConvertible) interface and the [Convert](xref:System.Convert) class provided by .NET, individual languages may also provide ways to perform conversions.</span></span> <span data-ttu-id="53960-196">例如，C# 使用轉型 (Casting) 運算子、Visual Basic 使用編譯器實作的轉換函式，例如 `CType`、`CInt` 和 `DirectCast`。</span><span class="sxs-lookup"><span data-stu-id="53960-196">For example, C# uses casting operators; Visual Basic uses compiler-implemented conversion functions such as `CType`, `CInt`, and `DirectCast`.</span></span>

<span data-ttu-id="53960-197">在大多數情況下，[IConvertible](xref:System.IConvertible) 介面的設計主要是支援在 .NET 中各基底類型之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-197">For the most part, the [IConvertible](xref:System.IConvertible) interface is designed to support conversion between the base types in .NET.</span></span> <span data-ttu-id="53960-198">不過，也可以使用自訂類型來實作介面，以支援從該類型轉換至其他自訂類型。</span><span class="sxs-lookup"><span data-stu-id="53960-198">However, the interface can also be implemented by a custom type to support conversion of that type to other custom types.</span></span> <span data-ttu-id="53960-199">如需詳細資訊，請參閱本主題後文的[使用 ChangeType 方法進行自訂轉換](#custom-conversions-with-the-changetype-method)一節。</span><span class="sxs-lookup"><span data-stu-id="53960-199">For more information, see the section [Custom conversions with the ChangeType method](#custom-conversions-with-the-changetype-method) later in this topic.</span></span>

## <a name="the-convert-class"></a><span data-ttu-id="53960-200">Convert 類別</span><span class="sxs-lookup"><span data-stu-id="53960-200">The Convert class</span></span>

<span data-ttu-id="53960-201">雖然可以呼叫每一個基底類別的 [IConvertible](xref:System.IConvertible) 介面實作來執行類型轉換，但建議的語言中立方式是呼叫 [System.Convert](xref:System.Convert) 類別的方法，在不同的基底類型之間轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-201">Although each base type's [IConvertible](xref:System.IConvertible) interface implementation can be called to perform a type conversion, calling the methods of the [System.Convert](xref:System.Convert) class is the recommended language-neutral way to convert from one base type to another.</span></span> <span data-ttu-id="53960-202">此外，也可以使用 [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) 方法將指定的自訂類型轉換為另一種類型。</span><span class="sxs-lookup"><span data-stu-id="53960-202">In addition, the [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) method can be used to convert from a specified custom type to another type.</span></span> 

### <a name="conversions-between-base-types"></a><span data-ttu-id="53960-203">基底類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="53960-203">Conversions between base types</span></span>

<span data-ttu-id="53960-204">[Convert](xref:System.Convert) 類別提供在基底類型之間執行轉換的語言中立方式，且適用於所有以通用語言執行平台為目標的語言。</span><span class="sxs-lookup"><span data-stu-id="53960-204">The [Convert](xref:System.Convert) class provides a language-neutral way to perform conversions between base types and is available to all languages that target the common language runtime.</span></span> <span data-ttu-id="53960-205">它對於擴展和縮小轉換提供一組完整的方法，且對於不支援的轉換 (例如，將 [DateTime](xref:System.DateTime) 值轉換為整數值) 會擲回 [InvalidCastException](xref:System.InvalidCastException)。</span><span class="sxs-lookup"><span data-stu-id="53960-205">It provides a complete set of methods for both widening and narrowing conversions, and throws an [InvalidCastException](xref:System.InvalidCastException) for conversions that are not supported (such as the conversion of a [DateTime](xref:System.DateTime) value to an integer value).</span></span> <span data-ttu-id="53960-206">縮小轉換是在已檢查的內容中執行，如果轉換失敗，則會擲回 [OverflowException](xref:System.OverflowException)。</span><span class="sxs-lookup"><span data-stu-id="53960-206">Narrowing conversions are performed in a checked context, and an [OverflowException](xref:System.OverflowException) is thrown if the conversion fails.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53960-207">因為 [Convert](xref:System.Convert) 類別包含在每一個基底類型之間來回轉換的方法，所以不需要呼叫每一個基底類型的 [IConvertible](xref:System.IConvertible) 明確介面實作。</span><span class="sxs-lookup"><span data-stu-id="53960-207">Because the [Convert](xref:System.Convert) class includes methods to convert to and from each base type, it eliminates the need to call each base type's [IConvertible](xref:System.IConvertible) explicit interface implementation.</span></span>

<span data-ttu-id="53960-208">下列範例說明如何使用 [System.Convert](xref:System.Convert) 類別，在 .NET 基底類型之間執行數個擴展和縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-208">The following example illustrates the use of the [System.Convert](xref:System.Convert) class to perform several widening and narrowing conversions between .NET base types.</span></span>

```csharp
// Convert an Int32 value to a Decimal (a widening conversion).
int integralValue = 12534;
decimal decimalValue = Convert.ToDecimal(integralValue);
Console.WriteLine("Converted the {0} value {1} to " +  
                                  "the {2} value {3:N2}.", 
                                  integralValue.GetType().Name, 
                                  integralValue, 
                                  decimalValue.GetType().Name, 
                                  decimalValue);
// Convert a Byte value to an Int32 value (a widening conversion).
byte byteValue = Byte.MaxValue;
int integralValue2 = Convert.ToInt32(byteValue);                                  
Console.WriteLine("Converted the {0} value {1} to " +  
                                  "the {2} value {3:G}.", 
                                  byteValue.GetType().Name, 
                                  byteValue, 
                                  integralValue2.GetType().Name, 
                                  integralValue2);

// Convert a Double value to an Int32 value (a narrowing conversion).
double doubleValue = 16.32513e12;
try {
   long longValue = Convert.ToInt64(doubleValue);
   Console.WriteLine("Converted the {0} value {1:E} to " +  
                                     "the {2} value {3:N0}.", 
                                     doubleValue.GetType().Name, 
                                     doubleValue, 
                                     longValue.GetType().Name, 
                                     longValue);
}
catch (OverflowException) {
   Console.WriteLine("Unable to convert the {0:E} value {1}.", 
                                     doubleValue.GetType().Name, doubleValue);
}

// Convert a signed byte to a byte (a narrowing conversion).     
sbyte sbyteValue = -16;
try {
   byte byteValue2 = Convert.ToByte(sbyteValue);
   Console.WriteLine("Converted the {0} value {1} to " +  
                                     "the {2} value {3:G}.", 
                                     sbyteValue.GetType().Name, 
                                     sbyteValue, 
                                     byteValue2.GetType().Name, 
                                     byteValue2);
}
catch (OverflowException) {
   Console.WriteLine("Unable to convert the {0} value {1}.", 
                                     sbyteValue.GetType().Name, sbyteValue);
}                                         
// The example displays the following output:
//       Converted the Int32 value 12534 to the Decimal value 12,534.00.
//       Converted the Byte value 255 to the Int32 value 255.
//       Converted the Double value 1.632513E+013 to the Int64 value 16,325,130,000,000.
//       Unable to convert the SByte value -16.
```

```vb
' Convert an Int32 value to a Decimal (a widening conversion).
Dim integralValue As Integer = 12534
Dim decimalValue As Decimal = Convert.ToDecimal(integralValue)
Console.WriteLine("Converted the {0} value {1} to the {2} value {3:N2}.", 
                  integralValue.GetType().Name,
                  integralValue,
                  decimalValue.GetType().Name,
                  decimalValue)

' Convert a Byte value to an Int32 value (a widening conversion).
Dim byteValue As Byte = Byte.MaxValue
Dim integralValue2 As Integer = Convert.ToInt32(byteValue)                                  
Console.WriteLine("Converted the {0} value {1} to " + 
                                  "the {2} value {3:G}.",
                                  byteValue.GetType().Name,
                                  byteValue,
                                  integralValue2.GetType().Name,
                                  integralValue2)

' Convert a Double value to an Int32 value (a narrowing conversion).
Dim doubleValue As Double = 16.32513e12
Try
   Dim longValue As Long = Convert.ToInt64(doubleValue)
   Console.WriteLine("Converted the {0} value {1:E} to " + 
                                     "the {2} value {3:N0}.",
                                     doubleValue.GetType().Name,
                                     doubleValue,
                                     longValue.GetType().Name,
                                     longValue)
Catch e As OverflowException
   Console.WriteLine("Unable to convert the {0:E} value {1}.",
                                     doubleValue.GetType().Name, doubleValue)
End Try                                                             

' Convert a signed byte to a byte (a narrowing conversion).     
Dim sbyteValue As SByte = -16
Try
   Dim byteValue2 As Byte = Convert.ToByte(sbyteValue)
   Console.WriteLine("Converted the {0} value {1} to " + 
                                     "the {2} value {3:G}.",
                                     sbyteValue.GetType().Name,
                                     sbyteValue,
                                     byteValue2.GetType().Name,
                                     byteValue2)
Catch e As OverflowException
   Console.WriteLine("Unable to convert the {0} value {1}.",
                                     sbyteValue.GetType().Name, sbyteValue)
End Try 
' The example displays the following output:
'       Converted the Int32 value 12534 to the Decimal value 12,534.00.
'       Converted the Byte value 255 to the Int32 value 255.
'       Converted the Double value 1.632513E+013 to the Int64 value 16,325,130,000,000.
'       Unable to convert the SByte value -16.
```

<span data-ttu-id="53960-209">在某些情況下，尤其是在浮點數值之間來回轉換時，即使沒有擲回 [OverflowException](xref:System.OverflowException)，轉換也可能會降低精確度。</span><span class="sxs-lookup"><span data-stu-id="53960-209">In some cases, particularly when converting to and from floating-point values, a conversion may involve a loss of precision, even though it does not throw an [OverflowException](xref:System.OverflowException).</span></span> <span data-ttu-id="53960-210">下列範例說明這種精確度降低情況。</span><span class="sxs-lookup"><span data-stu-id="53960-210">The following example illustrates this loss of precision.</span></span> <span data-ttu-id="53960-211">在第一種情況下，[Decimal](xref:System.Decimal) 值在轉換為 [Double](xref:System.Double) 時會降低精確度 (有效位數較少)。</span><span class="sxs-lookup"><span data-stu-id="53960-211">In the first case, a [Decimal](xref:System.Decimal) value has less precision (fewer significant digits) when it is converted to a [Double](xref:System.Double).</span></span> <span data-ttu-id="53960-212">在第二種情況下，[Double](xref:System.Double) 值會從 **42.72** 四捨五入為 **43**，以完成轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-212">In the second case, a [Double](xref:System.Double) value is rounded from **42.72** to **43** in order to complete the conversion.</span></span>

```csharp
double doubleValue; 

// Convert a Double to a Decimal.
decimal decimalValue = 13956810.96702888123451471211m;
doubleValue = Convert.ToDouble(decimalValue);
Console.WriteLine("{0} converted to {1}.", decimalValue, doubleValue);

doubleValue = 42.72;
try {
   int integerValue = Convert.ToInt32(doubleValue);
   Console.WriteLine("{0} converted to {1}.", 
                                     doubleValue, integerValue);
}
catch (OverflowException) {      
   Console.WriteLine("Unable to convert {0} to an integer.", 
                                     doubleValue);
}   
// The example displays the following output:
//       13956810.96702888123451471211 converted to 13956810.9670289.
//       42.72 converted to 43.
```

```vb
Dim doubleValue As Double 

' Convert a Double to a Decimal.
Dim decimalValue As Decimal = 13956810.96702888123451471211d
doubleValue = Convert.ToDouble(decimalValue)
Console.WriteLine("{0} converted to {1}.", decimalValue, doubleValue)

doubleValue = 42.72
Try
   Dim integerValue As Integer = Convert.ToInt32(doubleValue)
   Console.WriteLine("{0} converted to {1}.",
                                     doubleValue, integerValue)
Catch e As OverflowException
   Console.WriteLine("Unable to convert {0} to an integer.",
                                     doubleValue)
End Try   
' The example displays the following output:
'       13956810.96702888123451471211 converted to 13956810.9670289.
'       42.72 converted to 43.
```

<span data-ttu-id="53960-213">如需列有 [Convert](xref:System.Convert) 類別支援之擴展與縮小轉換的表格，請參閱[類型轉換表](conversion-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="53960-213">For a table that lists both the widening and narrowing conversions supported by the [Convert](xref:System.Convert) class, see [Type conversion tables](conversion-tables.md).</span></span>

### <a name="custom-conversions-with-the-changetype-method"></a><span data-ttu-id="53960-214">使用 ChangeType 方法進行自訂轉換</span><span class="sxs-lookup"><span data-stu-id="53960-214">Custom conversions with the ChangeType method</span></span>

<span data-ttu-id="53960-215">[Convert](xref:System.Convert) 類別除了支援每一個基底類型的轉換，也可以用於將自訂類型轉換為一個或多個預先定義的類型。</span><span class="sxs-lookup"><span data-stu-id="53960-215">In addition to supporting conversions to each of the base types, the [Convert](xref:System.Convert) class can be used to convert a custom type to one or more predefined types.</span></span> <span data-ttu-id="53960-216">這種轉換由 [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) 方法執行，而這個方法會進一步包裝值參數之 [IConvertible.ToType](xref:System.IConvertible.ToType(System.Type,System.IFormatProvider)) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="53960-216">This conversion is performed by the [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) method, which in turn wraps a call to the [IConvertible.ToType](xref:System.IConvertible.ToType(System.Type,System.IFormatProvider)) method of the value parameter.</span></span> <span data-ttu-id="53960-217">這表示由值參數所表示的物件必須提供 [IConvertible](xref:System.IConvertible) 介面的實作。</span><span class="sxs-lookup"><span data-stu-id="53960-217">This means that the object represented by the value parameter must provide an implementation of the [IConvertible](xref:System.IConvertible) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="53960-218">由於 [Convert.ChangeType(Object, Type)](xref:System.Convert.ChangeType(System.Object,System.Type)) 和 [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) 方法會使用 [Type](xref:System.Type) 物件指定轉換 值的目標類型，因此這兩種方法可以在編譯時期用來動態轉換不明類型的物件。</span><span class="sxs-lookup"><span data-stu-id="53960-218">Because the [Convert.ChangeType(Object, Type)](xref:System.Convert.ChangeType(System.Object,System.Type)) and [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) methods use a [Type](xref:System.Type) object to specify the target type to which value is converted, they can be used to perform a dynamic conversion to an object whose type is not known at compile time.</span></span> <span data-ttu-id="53960-219">但請注意，值的 [IConvertible](xref:System.IConvertible) 實作仍然必須支援這項轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-219">However, note that the [IConvertible](xref:System.IConvertible) implementation of value must still support this conversion.</span></span> 

<span data-ttu-id="53960-220">下列範例說明 [IConvertible](xref:System.IConvertible) 介面可能的實作，這種實作允許 `TemperatureCelsius` 物件轉換為 `TemperatureFahrenheit` 物件，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="53960-220">The following example illustrates a possible implementation of the [IConvertible](xref:System.IConvertible) interface that allows a `TemperatureCelsius` object to be converted to a `TemperatureFahrenheit` object and vice versa.</span></span> <span data-ttu-id="53960-221">範例中定義一個基底類別 `Temperature`，這個類別實作 [IConvertible](xref:System.IConvertible) 介面並覆寫 [Object.ToString](xref:System.Object.ToString) 方法。</span><span class="sxs-lookup"><span data-stu-id="53960-221">The example defines a base class, `Temperature`, that implements the [IConvertible](xref:System.IConvertible) interface and overrides the [Object.ToString](xref:System.Object.ToString) method.</span></span> <span data-ttu-id="53960-222">衍生的 `TemperatureCelsius` 和 `TemperatureFahrenheit` 類別分別覆寫基底類別的 `ToType` 和 `ToString` 方法。</span><span class="sxs-lookup"><span data-stu-id="53960-222">The derived `TemperatureCelsius` and `TemperatureFahrenheit` classes each override the `ToType` and the `ToString` methods of the base class.</span></span> 

```csharp
using System;

public abstract class Temperature : IConvertible
{
   protected decimal temp;

   public Temperature(decimal temperature)
   {
      this.temp = temperature;
   }

   public decimal Value
   { 
      get { return this.temp; } 
      set { this.temp = Value; }        
   }

   public override string ToString()
   {
      return temp.ToString(null as IFormatProvider) + "º";
   }

   // IConvertible implementations.
   public TypeCode GetTypeCode() { 
      return TypeCode.Object;
   }   

   public bool ToBoolean(IFormatProvider provider) {
      throw new InvalidCastException(String.Format("Temperature-to-Boolean conversion is not supported."));
   }

   public byte ToByte(IFormatProvider provider) {
      if (temp < Byte.MinValue || temp > Byte.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Byte data type.", temp));
      else
         return (byte) temp;
   }

   public char ToChar(IFormatProvider provider) {
      throw new InvalidCastException("Temperature-to-Char conversion is not supported.");
   }

   public DateTime ToDateTime(IFormatProvider provider) {
      throw new InvalidCastException("Temperature-to-DateTime conversion is not supported.");
   }

   public decimal ToDecimal(IFormatProvider provider) {
      return temp;
   }

   public double ToDouble(IFormatProvider provider) {
      return (double) temp;
   }

   public short ToInt16(IFormatProvider provider) {
      if (temp < Int16.MinValue || temp > Int16.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Int16 data type.", temp));
      else
         return (short) Math.Round(temp);
   }

   public int ToInt32(IFormatProvider provider) {
      if (temp < Int32.MinValue || temp > Int32.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Int32 data type.", temp));
      else
         return (int) Math.Round(temp);
   }

   public long ToInt64(IFormatProvider provider) {
      if (temp < Int64.MinValue || temp > Int64.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Int64 data type.", temp));
      else
         return (long) Math.Round(temp);
   }

   public sbyte ToSByte(IFormatProvider provider) {
      if (temp < SByte.MinValue || temp > SByte.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the SByte data type.", temp));
      else
         return (sbyte) temp;
   }

   public float ToSingle(IFormatProvider provider) {
      return (float) temp;
   }

   public virtual string ToString(IFormatProvider provider) {
      return temp.ToString(provider) + "°";
   }

   // If conversionType is implemented by another IConvertible method, call it.
   public virtual object ToType(Type conversionType, IFormatProvider provider) {
      switch (Type.GetTypeCode(conversionType))
      {
         case TypeCode.Boolean:
            return this.ToBoolean(provider);
         case TypeCode.Byte:
            return this.ToByte(provider);
         case TypeCode.Char:
            return this.ToChar(provider);
         case TypeCode.DateTime:
            return this.ToDateTime(provider);
         case TypeCode.Decimal:
            return this.ToDecimal(provider);
         case TypeCode.Double:
            return this.ToDouble(provider);
         case TypeCode.Empty:
            throw new NullReferenceException("The target type is null.");
         case TypeCode.Int16:
            return this.ToInt16(provider);
         case TypeCode.Int32:
            return this.ToInt32(provider);
         case TypeCode.Int64:
            return this.ToInt64(provider);
         case TypeCode.Object:
            // Leave conversion of non-base types to derived classes.
            throw new InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", 
                                           conversionType.Name));
         case TypeCode.SByte:
            return this.ToSByte(provider);
         case TypeCode.Single:
            return this.ToSingle(provider);
         case TypeCode.String:
            IConvertible iconv = this;
            return iconv.ToString(provider);
         case TypeCode.UInt16:
            return this.ToUInt16(provider);
         case TypeCode.UInt32:
            return this.ToUInt32(provider);
         case TypeCode.UInt64:
            return this.ToUInt64(provider);
         default:
            throw new InvalidCastException("Conversion not supported.");
      }
   }

   public ushort ToUInt16(IFormatProvider provider) {
      if (temp < UInt16.MinValue || temp > UInt16.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the UInt16 data type.", temp));
      else
         return (ushort) Math.Round(temp);
   }

   public uint ToUInt32(IFormatProvider provider) {
      if (temp < UInt32.MinValue || temp > UInt32.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the UInt32 data type.", temp));
      else
         return (uint) Math.Round(temp);
   }

   public ulong ToUInt64(IFormatProvider provider) {
      if (temp < UInt64.MinValue || temp > UInt64.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the UInt64 data type.", temp));
      else
         return (ulong) Math.Round(temp);
   }
}

public class TemperatureCelsius : Temperature, IConvertible
{
   public TemperatureCelsius(decimal value) : base(value)
   {
   }

   // Override ToString methods.
   public override string ToString()
   {
      return this.ToString(null);
   }

   public override string ToString(IFormatProvider provider)
   {
      return temp.ToString(provider) + "°C"; 
   }

   // If conversionType is a implemented by another IConvertible method, call it.
   public override object ToType(Type conversionType, IFormatProvider provider) {
      // For non-objects, call base method.
      if (Type.GetTypeCode(conversionType) != TypeCode.Object) {
         return base.ToType(conversionType, provider);
      }   
      else
      {   
         if (conversionType.Equals(typeof(TemperatureCelsius)))
            return this;
         else if (conversionType.Equals(typeof(TemperatureFahrenheit)))
            return new TemperatureFahrenheit((decimal) this.temp * 9 / 5 + 32);
         else
            throw new InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", 
                                           conversionType.Name));
      }
   }
}

public class TemperatureFahrenheit : Temperature, IConvertible 
{
   public TemperatureFahrenheit(decimal value) : base(value)
   {
   }

   // Override ToString methods.
   public override string ToString()
   {
      return this.ToString(null);
   }

   public override string ToString(IFormatProvider provider)
   {
      return temp.ToString(provider) + "°F"; 
   }

   public override object ToType(Type conversionType, IFormatProvider provider)
   { 
      // For non-objects, call base methood.
      if (Type.GetTypeCode(conversionType) != TypeCode.Object) {
         return base.ToType(conversionType, provider);
      }   
      else
      {   
         // Handle conversion between derived classes.
         if (conversionType.Equals(typeof(TemperatureFahrenheit))) 
            return this;
         else if (conversionType.Equals(typeof(TemperatureCelsius)))
            return new TemperatureCelsius((decimal) (this.temp - 32) * 5 / 9);
         // Unspecified object type: throw an InvalidCastException.
         else
            throw new InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", 
                                           conversionType.Name));
      }                                 
   }
}
```

```vb
Public MustInherit Class Temperature
   Implements IConvertible

   Protected temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.temp = temperature
   End Sub

   Public Property Value As Decimal
      Get 
         Return Me.temp
      End Get
      Set
         Me.temp = Value
      End Set   
   End Property

   Public Overrides Function ToString() As String
      Return temp.ToString() & "º"
   End Function

   ' IConvertible implementations.
   Public Function GetTypeCode() As TypeCode Implements IConvertible.GetTypeCode
      Return TypeCode.Object
   End Function   

   Public Function ToBoolean(provider As IFormatProvider) As Boolean Implements IConvertible.ToBoolean
      Throw New InvalidCastException(String.Format("Temperature-to-Boolean conversion is not supported."))
   End Function

   Public Function ToByte(provider As IFormatProvider) As Byte Implements IConvertible.ToByte
      If temp < Byte.MinValue Or temp > Byte.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Byte data type.", temp))
      Else
         Return CByte(temp)
      End If    
   End Function

   Public Function ToChar(provider As IFormatProvider) As Char Implements IConvertible.ToChar
      Throw New InvalidCastException("Temperature-to-Char conversion is not supported.")
   End Function

   Public Function ToDateTime(provider As IFormatProvider) As DateTime Implements IConvertible.ToDateTime
      Throw New InvalidCastException("Temperature-to-DateTime conversion is not supported.")
   End Function

   Public Function ToDecimal(provider As IFormatProvider) As Decimal Implements IConvertible.ToDecimal
      Return temp
   End Function

   Public Function ToDouble(provider As IFormatProvider) As Double Implements IConvertible.ToDouble
      Return CDbl(temp)
   End Function

   Public Function ToInt16(provider As IFormatProvider) As Int16 Implements IConvertible.ToInt16
      If temp < Int16.MinValue Or temp > Int16.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Int16 data type.", temp))
      End If
      Return CShort(Math.Round(temp))
   End Function

   Public Function ToInt32(provider As IFormatProvider) As Int32 Implements IConvertible.ToInt32
      If temp < Int32.MinValue Or temp > Int32.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Int32 data type.", temp))
      End If
      Return CInt(Math.Round(temp))
   End Function

   Public Function ToInt64(provider As IFormatProvider) As Int64 Implements IConvertible.ToInt64
      If temp < Int64.MinValue Or temp > Int64.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Int64 data type.", temp))
      End If
      Return CLng(Math.Round(temp))
   End Function

   Public Function ToSByte(provider As IFormatProvider) As SByte Implements IConvertible.ToSByte
      If temp < SByte.MinValue Or temp > SByte.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the SByte data type.", temp))
      Else
         Return CSByte(temp)
      End If    
   End Function

   Public Function ToSingle(provider As IFormatProvider) As Single Implements IConvertible.ToSingle
      Return CSng(temp)
   End Function

   Public Overridable Overloads Function ToString(provider As IFormatProvider) As String Implements IConvertible.ToString
      Return temp.ToString(provider) & " °C"
   End Function

   ' If conversionType is a implemented by another IConvertible method, call it.
   Public Overridable Function ToType(conversionType As Type, provider As IFormatProvider) As Object Implements IConvertible.ToType
      Select Case Type.GetTypeCode(conversionType)
         Case TypeCode.Boolean
            Return Me.ToBoolean(provider)
         Case TypeCode.Byte
            Return Me.ToByte(provider)
         Case TypeCode.Char
            Return Me.ToChar(provider)   
         Case TypeCode.DateTime
            Return Me.ToDateTime(provider)
         Case TypeCode.Decimal
            Return Me.ToDecimal(provider)
         Case TypeCode.Double
            Return Me.ToDouble(provider)
         Case TypeCode.Empty
            Throw New NullReferenceException("The target type is null.")
         Case TypeCode.Int16
            Return Me.ToInt16(provider)
         Case TypeCode.Int32
            Return Me.ToInt32(provider)
         Case TypeCode.Int64
            Return Me.ToInt64(provider)
         Case TypeCode.Object
            ' Leave conversion of non-base types to derived classes.
            Throw New InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", _
                                           conversionType.Name))
         Case TypeCode.SByte
            Return Me.ToSByte(provider)
         Case TypeCode.Single
            Return Me.ToSingle(provider)
         Case TypeCode.String
            Return Me.ToString(provider)
         Case TypeCode.UInt16
            Return Me.ToUInt16(provider)
         Case TypeCode.UInt32
            Return Me.ToUInt32(provider)
         Case TypeCode.UInt64
            Return Me.ToUInt64(provider)
         Case Else
            Throw New InvalidCastException("Conversion not supported.")   
      End Select
   End Function

   Public Function ToUInt16(provider As IFormatProvider) As UInt16 Implements IConvertible.ToUInt16
      If temp < UInt16.MinValue Or temp > UInt16.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the UInt16 data type.", temp))
      End If
      Return CUShort(Math.Round(temp))
   End Function

   Public Function ToUInt32(provider As IFormatProvider) As UInt32 Implements IConvertible.ToUInt32
      If temp < UInt32.MinValue Or temp > UInt32.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the UInt32 data type.", temp))
      End If
      Return CUInt(Math.Round(temp))
   End Function

   Public Function ToUInt64(provider As IFormatProvider) As UInt64 Implements IConvertible.ToUInt64
      If temp < UInt64.MinValue Or temp > UInt64.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the UInt64 data type.", temp))
      End If
      Return CULng(Math.Round(temp))
   End Function
End Class

Public Class TemperatureCelsius : Inherits Temperature : Implements IConvertible
   Public Sub New(value As Decimal)
      MyBase.New(value)
   End Sub

   ' Override ToString methods.
   Public Overrides Function ToString() As String
      Return Me.ToString(Nothing)
   End Function

   Public Overrides Function ToString(provider As IFormatProvider ) As String
      Return temp.ToString(provider) + "°C" 
   End Function

  ' If conversionType is a implemented by another IConvertible method, call it.
   Public Overrides Function ToType(conversionType As Type, provider As IFormatProvider) As Object
      ' For non-objects, call base method.
      If Type.GetTypeCode(conversionType) <> TypeCode.Object Then
         Return MyBase.ToType(conversionType, provider)
      Else   
         If conversionType.Equals(GetType(TemperatureCelsius)) Then
            Return Me
         ElseIf conversionType.Equals(GetType(TemperatureFahrenheit))
            Return New TemperatureFahrenheit(CDec(Me.temp * 9 / 5 + 32))
         ' Unspecified object type: throw an InvalidCastException.
         Else
            Throw New InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", _ 
                                           conversionType.Name))
         End If
      End If                                  
   End Function
End Class

Public Class TemperatureFahrenheit : Inherits Temperature : Implements IConvertible
   Public Sub New(value As Decimal)
      MyBase.New(value)
   End Sub

   ' Override ToString methods.
   Public Overrides Function ToString() As String
      Return Me.ToString(Nothing)
   End Function

   Public Overrides Function ToString(provider As IFormatProvider ) As String
      Return temp.ToString(provider) + "°F" 
   End Function

   Public Overrides Function ToType(conversionType As Type, provider As IFormatProvider) As Object
      ' For non-objects, call base methood.
      If Type.GetTypeCode(conversionType) <> TypeCode.Object Then
         Return MyBase.ToType(conversionType, provider)
      Else   
         ' Handle conversion between derived classes.
         If conversionType.Equals(GetType(TemperatureFahrenheit)) Then 
            Return Me
         ElseIf conversionType.Equals(GetType(TemperatureCelsius))
            Return New TemperatureCelsius(CDec((MyBase.temp - 32) * 5 / 9))
         ' Unspecified object type: throw an InvalidCastException.
         Else
            Throw New InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", _
                                           conversionType.Name))
         End If
      End If                                  
   End Function
End Class
```

<span data-ttu-id="53960-223">下列範例說明對這些 [IConvertible](xref:System.IConvertible) 實作的多個呼叫，以將 `TemperatureCelsius` 物件轉換為 `TemperatureFahrenheit` 物件，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="53960-223">The following example illustrates several calls to these [IConvertible](xref:System.IConvertible) implementations to convert `TemperatureCelsius` objects to `TemperatureFahrenheit` objects and vice versa.</span></span>

```csharp
TemperatureCelsius tempC1 = new TemperatureCelsius(0);
TemperatureFahrenheit tempF1 = (TemperatureFahrenheit) Convert.ChangeType(tempC1, typeof(TemperatureFahrenheit), null);
Console.WriteLine("{0} equals {1}.", tempC1, tempF1);
TemperatureCelsius tempC2 = (TemperatureCelsius) Convert.ChangeType(tempC1, typeof(TemperatureCelsius), null);
Console.WriteLine("{0} equals {1}.", tempC1, tempC2);
TemperatureFahrenheit tempF2 = new TemperatureFahrenheit(212);
TemperatureCelsius tempC3 = (TemperatureCelsius) Convert.ChangeType(tempF2, typeof(TemperatureCelsius), null);
Console.WriteLine("{0} equals {1}.", tempF2, tempC3);
TemperatureFahrenheit tempF3 = (TemperatureFahrenheit) Convert.ChangeType(tempF2, typeof(TemperatureFahrenheit), null);
Console.WriteLine("{0} equals {1}.", tempF2, tempF3);
// The example displays the following output:
//       0°C equals 32°F.
//       0°C equals 0°C.
//       212°F equals 100°C.
//       212°F equals 212°F.
```

```vb
Dim tempC1 As New TemperatureCelsius(0)
Dim tempF1 As TemperatureFahrenheit = CType(Convert.ChangeType(tempC1, GetType(TemperatureFahrenheit), Nothing), TemperatureFahrenheit)
Console.WriteLine("{0} equals {1}.", tempC1, tempF1) 
Dim tempC2 As TemperatureCelsius = CType(Convert.ChangeType(tempC1, GetType(TemperatureCelsius), Nothing), TemperatureCelsius)
Console.WriteLine("{0} equals {1}.", tempC1, tempC2) 
Dim tempF2 As New TemperatureFahrenheit(212)
Dim tempC3 As TEmperatureCelsius = CType(Convert.ChangeType(tempF2, GEtType(TemperatureCelsius), Nothing), TemperatureCelsius)
Console.WriteLine("{0} equals {1}.", tempF2, tempC3) 
Dim tempF3 As TemperatureFahrenheit = CType(Convert.ChangeType(tempF2, GetType(TemperatureFahrenheit), Nothing), TemperatureFahrenheit)
Console.WriteLine("{0} equals {1}.", tempF2, tempF3)
' The example displays the following output:
'       0°C equals 32°F.
'       0°C equals 0°C.
'       212°F equals 100°C.
'       212°F equals 212°F.
```

## <a name="the-typeconverter-class"></a><span data-ttu-id="53960-224">TypeConverter 類別</span><span class="sxs-lookup"><span data-stu-id="53960-224">The TypeConverter class</span></span>

<span data-ttu-id="53960-225">.NET 也可讓您延伸 [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter) 類別，並透過 [System.ComponentModel.TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute) 屬性來建立類型轉換器與類型之間的關聯，以定義自訂類型的類型轉換器。</span><span class="sxs-lookup"><span data-stu-id="53960-225">.NET also allows you to define a type converter for a custom type by extending the [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter) class and associating the type converter with the type through a [System.ComponentModel.TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute) attribute.</span></span> <span data-ttu-id="53960-226">下表特別強調這種作法與實作自訂類型之 [IConvertible](xref:System.IConvertible) 介面的差異。</span><span class="sxs-lookup"><span data-stu-id="53960-226">The following table highlights the differences between this approach and implementing the [IConvertible](xref:System.IConvertible) interface for a custom type.</span></span>

> [!NOTE]
> <span data-ttu-id="53960-227">只要自訂類型有為其定義的類型轉換子，即會提供設計階段支援給自訂類型。</span><span class="sxs-lookup"><span data-stu-id="53960-227">Design-time support can be provided for a custom type only if it has a type converter defined for it.</span></span>

<span data-ttu-id="53960-228">使用 TypeConverter 的轉換</span><span class="sxs-lookup"><span data-stu-id="53960-228">Conversion using TypeConverter</span></span> | <span data-ttu-id="53960-229">使用 IConvertible 的轉換</span><span class="sxs-lookup"><span data-stu-id="53960-229">Conversion using IConvertible</span></span>
------------------------------ | -----------------------------
<span data-ttu-id="53960-230">是從 [TypeConverter](xref:System.ComponentModel.TypeConverter) 衍生另外一個類別，以針對自訂類型來實作。</span><span class="sxs-lookup"><span data-stu-id="53960-230">Is implemented for a custom type by deriving a separate class from [TypeConverter](xref:System.ComponentModel.TypeConverter).</span></span> <span data-ttu-id="53960-231">透過套用 [TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute) 屬性，將這個衍生類別與自訂類型建立關聯。</span><span class="sxs-lookup"><span data-stu-id="53960-231">This derived class is associated with the custom type by applying a [TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute) attribute.</span></span> | <span data-ttu-id="53960-232">是由自訂類型所實作來執行轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-232">Is implemented by a custom type to perform conversion.</span></span> <span data-ttu-id="53960-233">該類型的使用者可在該類型上叫用 [IConvertible](xref:System.IConvertible) 轉換方法。</span><span class="sxs-lookup"><span data-stu-id="53960-233">A user of the type invokes an [IConvertible](xref:System.IConvertible) conversion method on the type.</span></span>
<span data-ttu-id="53960-234">可以在設計階段和在執行階段兩處使用。</span><span class="sxs-lookup"><span data-stu-id="53960-234">Can be used both at design time and at run time.</span></span> | <span data-ttu-id="53960-235">只能在執行階段使用。</span><span class="sxs-lookup"><span data-stu-id="53960-235">Can be used only at run time.</span></span>
<span data-ttu-id="53960-236">使用反映功能；因此，速度比 [IConvertible](xref:System.IConvertible) 所啟用的轉換還要慢。</span><span class="sxs-lookup"><span data-stu-id="53960-236">Uses reflection; therefore, is slower than conversion enabled by [IConvertible](xref:System.IConvertible).</span></span> | <span data-ttu-id="53960-237">不使用反映。</span><span class="sxs-lookup"><span data-stu-id="53960-237">Does not use reflection.</span></span>
<span data-ttu-id="53960-238">允許在自訂類型與其他資料類型之間的雙向類型轉換。</span><span class="sxs-lookup"><span data-stu-id="53960-238">Allows two-way type conversions from the custom type to other data types, and from other data types to the custom type.</span></span> <span data-ttu-id="53960-239">比方說，針對 `MyType` 所定義的 [TypeConverter](xref:System.ComponentModel.TypeConverter) 允許從 `MyType` 轉換為 [String](xref:System.String)，也允許從 [String](xref:System.String) 轉換為 `MyType`。</span><span class="sxs-lookup"><span data-stu-id="53960-239">For example, a [TypeConverter](xref:System.ComponentModel.TypeConverter) defined for `MyType` allows conversions from `MyType` to [String](xref:System.String), and from [String](xref:System.String) to `MyType`.</span></span> | <span data-ttu-id="53960-240">允許從自訂類型轉換為其他資料類型，但不允許從其他資料類型轉換為自訂類型。</span><span class="sxs-lookup"><span data-stu-id="53960-240">Allows conversion from a custom type to other data types, but not from other data types to the custom type.</span></span>

<span data-ttu-id="53960-241">如需使用類型轉換器執行轉換的詳細資訊，請參閱 [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter)。</span><span class="sxs-lookup"><span data-stu-id="53960-241">For more information about using type converters to perform conversions, see [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter).</span></span>

## <a name="see-also"></a><span data-ttu-id="53960-242">請參閱</span><span class="sxs-lookup"><span data-stu-id="53960-242">See also</span></span>

[<span data-ttu-id="53960-243">System.Convert</span><span class="sxs-lookup"><span data-stu-id="53960-243">System.Convert</span></span>](xref:System.Convert)

[<span data-ttu-id="53960-244">IConvertible</span><span class="sxs-lookup"><span data-stu-id="53960-244">IConvertible</span></span>](xref:System.IConvertible)

[<span data-ttu-id="53960-245">類型轉換表</span><span class="sxs-lookup"><span data-stu-id="53960-245">Type conversion tables</span></span>](conversion-tables.md)
