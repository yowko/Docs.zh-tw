---
title: 語言獨立性以及與語言無關的元件
description: 了解如何使用 .NET 中支援的許多語言之一進行開發，例如 C#、C++/CLI、F#、IronPython、VB、Visual COBOL 和 PowerShell。
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: 2e54f49f111c545a329a64ede400dc1354020f43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="language-independence-and-language-independent-components"></a><span data-ttu-id="05ed1-103">語言獨立性以及與語言無關的元件</span><span class="sxs-lookup"><span data-stu-id="05ed1-103">Language independence and language-independent components</span></span>

<span data-ttu-id="05ed1-104">.NET 與語言無關。</span><span class="sxs-lookup"><span data-stu-id="05ed1-104">.NET is language independent.</span></span> <span data-ttu-id="05ed1-105">這表示，身為開發人員，您可以使用以 .NET 實作為目標的許多語言之一進行開發，例如 C#、F# 和 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="05ed1-105">This means that, as a developer, you can develop in one of the many languages that target .NET implementations, such as C#, F#, and Visual Basic.</span></span> <span data-ttu-id="05ed1-106">您可以存取為 .NET 實作開發之類別庫的類型和成員，而不必知道原始撰寫的語言，也不必遵循原始語言的任何慣例。</span><span class="sxs-lookup"><span data-stu-id="05ed1-106">You can access the types and members of class libraries developed for .NET implementations without having to know the language in which they were originally written and without having to follow any of the original language's conventions.</span></span> <span data-ttu-id="05ed1-107">如果您是元件開發人員，則不論其語言為何，元件都可以由任何 .NET 應用程式存取。</span><span class="sxs-lookup"><span data-stu-id="05ed1-107">If you are a component developer, your component can be accessed by any .NET app regardless of its language.</span></span>

> [!NOTE]
> <span data-ttu-id="05ed1-108">本文第一個部分將討論如何建立與語言無關的元件，也就是以任何語言撰寫的應用程式都可以使用的元件。</span><span class="sxs-lookup"><span data-stu-id="05ed1-108">This first part of this article discusses creating language-independent components - that is, components that can be consumed by apps that are written in any language.</span></span> <span data-ttu-id="05ed1-109">您也可以從以多種語言撰寫的原始程式碼建立單一元件或應用程式。請參閱本文第二部分的[跨語言互通性](#cross-language-interoperability)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-109">You can also create a single component or app from source code written in multiple languages; see [Cross-Language Interoperability](#cross-language-interoperability) in the second part of this article.</span></span> 

<span data-ttu-id="05ed1-110">若要充分與其他以任何語言撰寫的物件互動，這些物件必須只向呼叫端公開所有語言通用的功能。</span><span class="sxs-lookup"><span data-stu-id="05ed1-110">To fully interact with other objects written in any language, objects must expose to callers only those features that are common to all languages.</span></span> <span data-ttu-id="05ed1-111">這一組通用的功能是由 Common Language Specification (CLS) 所定義，CLS 是套用至所產生之組件的一組規則。</span><span class="sxs-lookup"><span data-stu-id="05ed1-111">This common set of features is defined by the Common Language Specification (CLS), which is a set of rules that apply to generated assemblies.</span></span> <span data-ttu-id="05ed1-112">Common Language Specification 是定義在 [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm) 的第一篇條款 7 到 11。</span><span class="sxs-lookup"><span data-stu-id="05ed1-112">The Common Language Specification is defined in Partition I, Clauses 7 through 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span> 

<span data-ttu-id="05ed1-113">如果您的元件符合 Common Language Specification，則保證其符合 CLS 標準，而且可以從支援 CLS 之任何程式語言所撰寫的組件中的程式碼來加以存取。</span><span class="sxs-lookup"><span data-stu-id="05ed1-113">If your component conforms to the Common Language Specification, it is guaranteed to be CLS-compliant and can be accessed from code in assemblies written in any programming language that supports the CLS.</span></span> <span data-ttu-id="05ed1-114">您可以在編譯時期將 [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 屬性套用至您的原始程式碼，判斷您的元件是否符合 Common Language Specification。</span><span class="sxs-lookup"><span data-stu-id="05ed1-114">You can determine whether your component conforms to the Common Language Specification at compile time by applying the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute to your source code.</span></span> <span data-ttu-id="05ed1-115">如需詳細資訊，請參閱 [CLSCompliantAttribute 屬性](#the-clscompliantattribute-attribute)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-115">For more information, see The [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute).</span></span>

<span data-ttu-id="05ed1-116">本文內容：</span><span class="sxs-lookup"><span data-stu-id="05ed1-116">In this article:</span></span>

* [<span data-ttu-id="05ed1-117">CLS 合規性規則</span><span class="sxs-lookup"><span data-stu-id="05ed1-117">CLS compliance rules</span></span>](#cls-compliance-rules)

    * [<span data-ttu-id="05ed1-118">類型及類型成員簽章</span><span class="sxs-lookup"><span data-stu-id="05ed1-118">Types and type member signatures</span></span>](#types-and-type-member-signatures)

    * [<span data-ttu-id="05ed1-119">命名慣例</span><span class="sxs-lookup"><span data-stu-id="05ed1-119">Naming conventions</span></span>](#naming-conventions)
    
    * [<span data-ttu-id="05ed1-120">類型轉換</span><span class="sxs-lookup"><span data-stu-id="05ed1-120">Type conversion</span></span>](#type-conversion)
    
    * [<span data-ttu-id="05ed1-121">陣列</span><span class="sxs-lookup"><span data-stu-id="05ed1-121">Arrays</span></span>](#arrays)
    
    * [<span data-ttu-id="05ed1-122">介面</span><span class="sxs-lookup"><span data-stu-id="05ed1-122">Interfaces</span></span>](#interfaces)
    
    * [<span data-ttu-id="05ed1-123">列舉</span><span class="sxs-lookup"><span data-stu-id="05ed1-123">Enumerations</span></span>](#enumerations)
    
    * [<span data-ttu-id="05ed1-124">一般類型成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-124">Type members in general</span></span>](#type-members-in-general)
    
    * [<span data-ttu-id="05ed1-125">成員存取範圍</span><span class="sxs-lookup"><span data-stu-id="05ed1-125">Member accessibility</span></span>](#member-accessibility)
    
    * [<span data-ttu-id="05ed1-126">泛型類型及成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-126">Generic types and members</span></span>](#generic-types-and-members)
    
    * [<span data-ttu-id="05ed1-127">建構函式</span><span class="sxs-lookup"><span data-stu-id="05ed1-127">Constructors</span></span>](#constructors)
    
    * [<span data-ttu-id="05ed1-128">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-128">Properties</span></span>](#properties)
    
    * [<span data-ttu-id="05ed1-129">事件</span><span class="sxs-lookup"><span data-stu-id="05ed1-129">Events</span></span>](#events)
    
    * [<span data-ttu-id="05ed1-130">多載</span><span class="sxs-lookup"><span data-stu-id="05ed1-130">Overloads</span></span>](#overloads)
    
    * [<span data-ttu-id="05ed1-131">例外狀況</span><span class="sxs-lookup"><span data-stu-id="05ed1-131">Exceptions</span></span>](#exceptions)
    
    * [<span data-ttu-id="05ed1-132">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-132">Attributes</span></span>](#attributes)
    
* [<span data-ttu-id="05ed1-133">CLSCompliantAttribute 屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-133">CLSCompliantAttribute attribute</span></span>](#the-clscompliantattribute-attribute)

* [<span data-ttu-id="05ed1-134">不同語言之間的互通性</span><span class="sxs-lookup"><span data-stu-id="05ed1-134">Cross-Language Interoperability</span></span>](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a><span data-ttu-id="05ed1-135">CLS 符合性規則</span><span class="sxs-lookup"><span data-stu-id="05ed1-135">CLS compliance rules</span></span>

<span data-ttu-id="05ed1-136">本節討論建立符合 CLS 標準的元件的規則。</span><span class="sxs-lookup"><span data-stu-id="05ed1-136">This section discusses the rules for creating a CLS-compliant component.</span></span> <span data-ttu-id="05ed1-137">如需規則的完整清單，請參閱 [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm) 的第一篇條款 11。</span><span class="sxs-lookup"><span data-stu-id="05ed1-137">For a complete list of rules, see Partition I, Clause 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

> [!NOTE]
> <span data-ttu-id="05ed1-138">Common Language Specification 所討論的是適用於下列各項的 CLS 符合性的每個規則：消費者 (以程式設計方式存取符合 CLS 標準之元件的開發人員)、架構 (使用語言編譯器建立符合 CLS 標準之程式庫的開發人員) 和擴充項 (建立工具 (例如可建立符合 CLS 標準之元件的語言編譯器或程式碼剖析器) 的開發人員)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-138">The Common Language Specification discusses each rule for CLS compliance as it applies to consumers (developers who are programmatically accessing a component that is CLS-compliant), frameworks (developers who are using a language compiler to create CLS-compliant libraries), and extenders (developers who are creating a tool such as a language compiler or a code parser that creates CLS-compliant components).</span></span> <span data-ttu-id="05ed1-139">本文旨在討論適用於架構的規則。</span><span class="sxs-lookup"><span data-stu-id="05ed1-139">This article focuses on the rules as they apply to frameworks.</span></span> <span data-ttu-id="05ed1-140">請注意，話雖如此，適用於擴充項的某些規則可能也適用於使用 [Reflection.Emit](xref:System.Reflection.Emit) 建立的組件。</span><span class="sxs-lookup"><span data-stu-id="05ed1-140">Note, though, that some of the rules that apply to extenders may also apply to assemblies that are created using [Reflection.Emit](xref:System.Reflection.Emit).</span></span> 

<span data-ttu-id="05ed1-141">若要設計與語言無關的元件，您只需要將 CLS 符合性規則套用至元件的公用介面。</span><span class="sxs-lookup"><span data-stu-id="05ed1-141">To design a component that is language independent, you only need to apply the rules for CLS compliance to your component's public interface.</span></span> <span data-ttu-id="05ed1-142">您的私用實作並不需要符合規格。</span><span class="sxs-lookup"><span data-stu-id="05ed1-142">Your private implementation does not have to conform to the specification.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="05ed1-143">CLS 符合性規則只適用於元件的公用介面，不適用於其私用實作。</span><span class="sxs-lookup"><span data-stu-id="05ed1-143">The rules for CLS compliance apply only to a component's public interface, not to its private implementation.</span></span> 

<span data-ttu-id="05ed1-144">例如，除了 [Byte](xref:System.Byte) 以外的不帶正負號的整數都不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-144">For example, unsigned integers other than [Byte](xref:System.Byte) are not CLS-compliant.</span></span> <span data-ttu-id="05ed1-145">因為下面範例中的 `Person` 類別會公開類型為 [UInt16](xref:System.UInt16) 的 `Age` 屬性，下面程式碼會顯示編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="05ed1-145">Because the `Person` class in the following example exposes an `Age` property of type [UInt16](xref:System.UInt16), the following code displays a compiler warning.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private UInt16 personAge = 0;

   public UInt16 Age 
   { get { return personAge; } }
}
// The attempt to compile the example displays the following compiler warning:
//    Public1.cs(10,18): warning CS3003: Type of 'Person.Age' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)> 

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As UInt16
      Get
         Return personAge      
      End Get   
   End Property
End Class
' The attempt to compile the example displays the following compiler warning:
'    Public1.vb(9) : warning BC40027: Return type of function 'Age' is not CLS-compliant.
'    
'       Public ReadOnly Property Age As UInt16
'                                ~~~
```

<span data-ttu-id="05ed1-146">您可以藉由將 `Age` 屬性的類型從 `UInt16` 變更為符合 CLS 標準 16 位元帶正負號整數的 [Int16](xref:System.Int16)，使 Person 類別符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-146">You can make the Person class CLS-compliant by changing the type of `Age` property from `UInt16` to [Int16](xref:System.Int16), which is a CLS-compliant, 16-bit signed integer.</span></span> <span data-ttu-id="05ed1-147">您不需要變更 `personAge` 私用欄位的類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-147">You do not have to change the type of the private `personAge` field.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private Int16 personAge = 0;

   public Int16 Age 
   { get { return personAge; } }
}
```

```vb
<Assembly: CLSCompliant(True)> 

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As Int16
      Get
         Return CType(personAge, Int16)      
      End Get   
   End Property
End Class
```

<span data-ttu-id="05ed1-148">程式庫的公用介面由下列各項組成：</span><span class="sxs-lookup"><span data-stu-id="05ed1-148">A library's public interface consists of the following:</span></span>

* <span data-ttu-id="05ed1-149">公用類別的定義。</span><span class="sxs-lookup"><span data-stu-id="05ed1-149">Definitions of public classes.</span></span>

* <span data-ttu-id="05ed1-150">公用類別之公用成員的定義，以及衍生類別可存取之成員 (即 protected 成員) 的定義。</span><span class="sxs-lookup"><span data-stu-id="05ed1-150">Definitions of the public members of public classes, and definitions of members accessible to derived classes (that is, protected members).</span></span> 

* <span data-ttu-id="05ed1-151">公用類別之公用方法的參數和傳回類型，以及衍生類別可存取之方法的參數和傳回類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-151">Parameters and return types of public methods of public classes, and parameters and return types of methods accessible to derived classes.</span></span> 

<span data-ttu-id="05ed1-152">下表列出 CLS 符合性的規則。</span><span class="sxs-lookup"><span data-stu-id="05ed1-152">The rules for CLS compliance are listed in the following table.</span></span> <span data-ttu-id="05ed1-153">這些規則的英文是一字不差地擷取自 [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (Copyright 2012 by Ecma International)，然後再翻譯成繁體中文。</span><span class="sxs-lookup"><span data-stu-id="05ed1-153">The text of the rules is taken verbatim from the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), which is Copyright 2012 by Ecma International.</span></span> <span data-ttu-id="05ed1-154">這些規則的其他詳細資訊可在下列章節中找到。</span><span class="sxs-lookup"><span data-stu-id="05ed1-154">More detailed information about these rules is found in the following sections.</span></span> 

<span data-ttu-id="05ed1-155">分類</span><span class="sxs-lookup"><span data-stu-id="05ed1-155">Category</span></span> | <span data-ttu-id="05ed1-156">請參閱</span><span class="sxs-lookup"><span data-stu-id="05ed1-156">See</span></span> | <span data-ttu-id="05ed1-157">規則</span><span class="sxs-lookup"><span data-stu-id="05ed1-157">Rule</span></span> | <span data-ttu-id="05ed1-158">規則編號</span><span class="sxs-lookup"><span data-stu-id="05ed1-158">Rule Number</span></span>
-------- | --- | ---- | -----------
<span data-ttu-id="05ed1-159">協助工具選項</span><span class="sxs-lookup"><span data-stu-id="05ed1-159">Accessibility</span></span> | [<span data-ttu-id="05ed1-160">成員存取範圍</span><span class="sxs-lookup"><span data-stu-id="05ed1-160">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="05ed1-161">在覆寫繼承的方法時，不得變更其存取範圍；但覆寫繼承自具有 `family-or-assembly` 存取範圍之不同組件的方法除外。</span><span class="sxs-lookup"><span data-stu-id="05ed1-161">Accessibility shall not be changed when overriding inherited methods, except when overriding a method inherited from a different assembly with accessibility `family-or-assembly`.</span></span> <span data-ttu-id="05ed1-162">在這種情況下，覆寫應具有 `family` 存取範圍。</span><span class="sxs-lookup"><span data-stu-id="05ed1-162">In this case, the override shall have accessibility `family`.</span></span> | <span data-ttu-id="05ed1-163">10</span><span class="sxs-lookup"><span data-stu-id="05ed1-163">10</span></span>
<span data-ttu-id="05ed1-164">協助工具選項</span><span class="sxs-lookup"><span data-stu-id="05ed1-164">Accessibility</span></span> | [<span data-ttu-id="05ed1-165">成員存取範圍</span><span class="sxs-lookup"><span data-stu-id="05ed1-165">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="05ed1-166">類型和成員應該有可視性和存取範圍，以致每當成員本身為可見和可存取時，任何成員簽章中的類型也應該是可見和可存取的。</span><span class="sxs-lookup"><span data-stu-id="05ed1-166">The visibility and accessibility of types and members shall be such that types in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="05ed1-167">例如，在組件外部是可見的公用方法不得有引數，其類型只有在組件內可見。</span><span class="sxs-lookup"><span data-stu-id="05ed1-167">For example, a public method that is visible outside its assembly shall not have an argument whose type is visible only within the assembly.</span></span> <span data-ttu-id="05ed1-168">構成類型應該有可視性和存取範圍，以致每當成員本身為可見和可存取時，任何成員簽章中所用的具現化泛型類型也應該是可見和可存取的。</span><span class="sxs-lookup"><span data-stu-id="05ed1-168">The visibility and accessibility of types composing an instantiated generic type used in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="05ed1-169">例如，存在於組件外部可見成員的簽章中的具現化泛型類型，不得有類型只能在組件內可見的泛型引數。</span><span class="sxs-lookup"><span data-stu-id="05ed1-169">For example, an instantiated generic type present in the signature of a member that is visible outside its assembly shall not have a generic argument whose type is visible only within the assembly.</span></span> | <span data-ttu-id="05ed1-170">12</span><span class="sxs-lookup"><span data-stu-id="05ed1-170">12</span></span>
<span data-ttu-id="05ed1-171">陣列</span><span class="sxs-lookup"><span data-stu-id="05ed1-171">Arrays</span></span> | [<span data-ttu-id="05ed1-172">陣列</span><span class="sxs-lookup"><span data-stu-id="05ed1-172">Arrays</span></span>](#arrays) | <span data-ttu-id="05ed1-173">陣列必須有符合 CLS 標準之類型的項目，而且陣列所有維度的下限必須為零。</span><span class="sxs-lookup"><span data-stu-id="05ed1-173">Arrays shall have elements with a CLS-compliant type, and all dimensions of the array shall have lower bounds of zero.</span></span> <span data-ttu-id="05ed1-174">只有項目是陣列以及陣列的項目類型是需要在多載之間區別的事實。</span><span class="sxs-lookup"><span data-stu-id="05ed1-174">Only the fact that an item is an array and the element type of the array shall be required to distinguish between overloads.</span></span> <span data-ttu-id="05ed1-175">當多載根據兩個或多個陣列類型時，項目類型應該是具名類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-175">When overloading is based on two or more array types the element types shall be named types.</span></span> | <span data-ttu-id="05ed1-176">16</span><span class="sxs-lookup"><span data-stu-id="05ed1-176">16</span></span>
<span data-ttu-id="05ed1-177">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-177">Attributes</span></span> | [<span data-ttu-id="05ed1-178">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-178">Attributes</span></span>](#attributes) | <span data-ttu-id="05ed1-179">屬性的類型必須為 [System.Attribute](xref:System.Attribute) 或繼承自它的類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-179">Attributes shall be of type [System.Attribute](xref:System.Attribute), or a type inheriting from it.</span></span> | <span data-ttu-id="05ed1-180">41</span><span class="sxs-lookup"><span data-stu-id="05ed1-180">41</span></span>
<span data-ttu-id="05ed1-181">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-181">Attributes</span></span> | [<span data-ttu-id="05ed1-182">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-182">Attributes</span></span>](#attributes) | <span data-ttu-id="05ed1-183">CLS 只允許自訂屬性編碼的子集。</span><span class="sxs-lookup"><span data-stu-id="05ed1-183">The CLS only allows a subset of the encodings of custom attributes.</span></span> <span data-ttu-id="05ed1-184">只有以下這些類型允許出現在這些編碼中 (請參閱第四篇)：[System.Type](xref:System.Type)、[System.String](xref:System.String)、[System.Char](xref:System.Char)、[System.Boolean](xref:System.Boolean)、[System.Byte](xref:System.Byte)、[System.Int16](xref:System.Int16)、[System.Int32](xref:System.Int32)、[System.Int64](xref:System.Int64)、[System.Single](xref:System.Single)、[System.Double](xref:System.Double)，以及以符合 CLS 標準之基底整數類型為基礎的所有列舉類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-184">The only types that shall appear in these encodings are (see Partition IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), and any enumeration type based on a CLS-compliant base integer type.</span></span> | <span data-ttu-id="05ed1-185">34</span><span class="sxs-lookup"><span data-stu-id="05ed1-185">34</span></span>
<span data-ttu-id="05ed1-186">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-186">Attributes</span></span> | [<span data-ttu-id="05ed1-187">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-187">Attributes</span></span>](#attributes) | <span data-ttu-id="05ed1-188">CLS 不允許公開可見的必要修飾詞 (`modreq`，請參閱第二篇)，不過，允許它不了解的選擇性修飾詞 (`modopt`，請參閱第二篇)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-188">The CLS does not allow publicly visible required modifiers (`modreq`, see Partition II), but does allow optional modifiers (`modopt`, see Partition II) it does not understand.</span></span> | <span data-ttu-id="05ed1-189">35</span><span class="sxs-lookup"><span data-stu-id="05ed1-189">35</span></span>
<span data-ttu-id="05ed1-190">建構函式</span><span class="sxs-lookup"><span data-stu-id="05ed1-190">Constructors</span></span> | [<span data-ttu-id="05ed1-191">建構函式</span><span class="sxs-lookup"><span data-stu-id="05ed1-191">Constructors</span></span>](#constructors) | <span data-ttu-id="05ed1-192">物件建構函式必須先呼叫基底類別的某個執行個體建構函式，才能對繼承的執行個體資料進行任何存取 </span><span class="sxs-lookup"><span data-stu-id="05ed1-192">An object constructor shall call some instance constructor of its base class before any access occurs to inherited instance data.</span></span> <span data-ttu-id="05ed1-193">(這不適用於不需要具有建構函式的實值類型)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-193">(This does not apply to value types, which need not have constructors.)</span></span>  | <span data-ttu-id="05ed1-194">21</span><span class="sxs-lookup"><span data-stu-id="05ed1-194">21</span></span>
<span data-ttu-id="05ed1-195">建構函式</span><span class="sxs-lookup"><span data-stu-id="05ed1-195">Constructors</span></span> | [<span data-ttu-id="05ed1-196">建構函式</span><span class="sxs-lookup"><span data-stu-id="05ed1-196">Constructors</span></span>](#constructors) | <span data-ttu-id="05ed1-197">除非是做為物件建立程序的一部分，否則是不能呼叫物件建構函式的，而且也不能初始化物件兩次。</span><span class="sxs-lookup"><span data-stu-id="05ed1-197">An object constructor shall not be called except as part of the creation of an object, and an object shall not be initialized twice.</span></span> | <span data-ttu-id="05ed1-198">22</span><span class="sxs-lookup"><span data-stu-id="05ed1-198">22</span></span>
<span data-ttu-id="05ed1-199">列舉</span><span class="sxs-lookup"><span data-stu-id="05ed1-199">Enumerations</span></span> | [<span data-ttu-id="05ed1-200">列舉</span><span class="sxs-lookup"><span data-stu-id="05ed1-200">Enumerations</span></span>](#enumerations) | <span data-ttu-id="05ed1-201">列舉的基礎類型應該是內建 CLS 整數類型，欄位的名稱應該是 "value__"，而且該欄位應該標記為 `RTSpecialName`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-201">The underlying type of an enum shall be a built-in CLS integer type, the name of the field shall be "value__", and that field shall be marked `RTSpecialName`.</span></span> |  <span data-ttu-id="05ed1-202">7</span><span class="sxs-lookup"><span data-stu-id="05ed1-202">7</span></span>
<span data-ttu-id="05ed1-203">列舉</span><span class="sxs-lookup"><span data-stu-id="05ed1-203">Enumerations</span></span> | [<span data-ttu-id="05ed1-204">列舉</span><span class="sxs-lookup"><span data-stu-id="05ed1-204">Enumerations</span></span>](#enumerations) | <span data-ttu-id="05ed1-205">有兩種不同的列舉，由 [System.FlagsAttribute](xref:System.FlagsAttribute) (請參閱第四篇程式庫) 自訂屬性存在與否表示。</span><span class="sxs-lookup"><span data-stu-id="05ed1-205">There are two distinct kinds of enums, indicated by the presence or absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) (see Partition IV Library) custom attribute.</span></span> <span data-ttu-id="05ed1-206">一個表示具名整數值；另一個則表示具名位元旗標 (可合併以產生未命名的值)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-206">One represents named integer values; the other represents named bit flags that can be combined to generate an unnamed value.</span></span> <span data-ttu-id="05ed1-207">`enum` 的值不限於指定的值。</span><span class="sxs-lookup"><span data-stu-id="05ed1-207">The value of an `enum` is not limited to the specified values.</span></span> |  <span data-ttu-id="05ed1-208">8</span><span class="sxs-lookup"><span data-stu-id="05ed1-208">8</span></span>
<span data-ttu-id="05ed1-209">列舉</span><span class="sxs-lookup"><span data-stu-id="05ed1-209">Enumerations</span></span> | [<span data-ttu-id="05ed1-210">列舉</span><span class="sxs-lookup"><span data-stu-id="05ed1-210">Enumerations</span></span>](#enumerations) | <span data-ttu-id="05ed1-211">列舉的常值靜態欄位必須有列舉本身的類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-211">Literal static fields of an enum shall have the type of the enum itself.</span></span> |  <span data-ttu-id="05ed1-212">9</span><span class="sxs-lookup"><span data-stu-id="05ed1-212">9</span></span>
<span data-ttu-id="05ed1-213">事件</span><span class="sxs-lookup"><span data-stu-id="05ed1-213">Events</span></span> | [<span data-ttu-id="05ed1-214">事件</span><span class="sxs-lookup"><span data-stu-id="05ed1-214">Events</span></span>](#events) | <span data-ttu-id="05ed1-215">實作事件的方法必須在中繼資料中標記為 `SpecialName`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-215">The methods that implement an event shall be marked `SpecialName` in the metadata.</span></span> |<span data-ttu-id="05ed1-216">29</span><span class="sxs-lookup"><span data-stu-id="05ed1-216">29</span></span>
<span data-ttu-id="05ed1-217">事件</span><span class="sxs-lookup"><span data-stu-id="05ed1-217">Events</span></span> | [<span data-ttu-id="05ed1-218">事件</span><span class="sxs-lookup"><span data-stu-id="05ed1-218">Events</span></span>](#events) | <span data-ttu-id="05ed1-219">事件及其存取子的存取範圍必須是相同的。</span><span class="sxs-lookup"><span data-stu-id="05ed1-219">The accessibility of an event and of its accessors shall be identical.</span></span> |<span data-ttu-id="05ed1-220">30</span><span class="sxs-lookup"><span data-stu-id="05ed1-220">30</span></span>
<span data-ttu-id="05ed1-221">事件</span><span class="sxs-lookup"><span data-stu-id="05ed1-221">Events</span></span> | [<span data-ttu-id="05ed1-222">事件</span><span class="sxs-lookup"><span data-stu-id="05ed1-222">Events</span></span>](#events) | <span data-ttu-id="05ed1-223">事件的 `add` 和 `remove` 方法，兩者必須同時存在或同時不存在。</span><span class="sxs-lookup"><span data-stu-id="05ed1-223">The `add` and `remove` methods for an event shall both either be present or absent.</span></span> |<span data-ttu-id="05ed1-224">31</span><span class="sxs-lookup"><span data-stu-id="05ed1-224">31</span></span>
<span data-ttu-id="05ed1-225">事件</span><span class="sxs-lookup"><span data-stu-id="05ed1-225">Events</span></span> | [<span data-ttu-id="05ed1-226">事件</span><span class="sxs-lookup"><span data-stu-id="05ed1-226">Events</span></span>](#events) | <span data-ttu-id="05ed1-227">事件的 `add` 和 `remove` 方法應各自採用一個其類型會定義事件類型的參數，而且必須是衍生自 [System.Delegate](xref:System.Delegate)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-227">The `add` and `remove` methods for an event shall each take one parameter whose type defines the type of the event and that shall be derived from [System.Delegate](xref:System.Delegate).</span></span> |<span data-ttu-id="05ed1-228">32</span><span class="sxs-lookup"><span data-stu-id="05ed1-228">32</span></span>
<span data-ttu-id="05ed1-229">事件</span><span class="sxs-lookup"><span data-stu-id="05ed1-229">Events</span></span> | [<span data-ttu-id="05ed1-230">事件</span><span class="sxs-lookup"><span data-stu-id="05ed1-230">Events</span></span>](#events) | <span data-ttu-id="05ed1-231">事件必須遵守特定的命名模式。</span><span class="sxs-lookup"><span data-stu-id="05ed1-231">Events shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="05ed1-232">在適當的名稱比較中應忽略 CLS 第 29 條規則中所提及的 SpecialName 屬性，並且應遵循識別項規則。</span><span class="sxs-lookup"><span data-stu-id="05ed1-232">The SpecialName attribute referred to in CLS rule 29 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span>  |<span data-ttu-id="05ed1-233">33</span><span class="sxs-lookup"><span data-stu-id="05ed1-233">33</span></span>
<span data-ttu-id="05ed1-234">例外狀況</span><span class="sxs-lookup"><span data-stu-id="05ed1-234">Exceptions</span></span> | [<span data-ttu-id="05ed1-235">例外狀況</span><span class="sxs-lookup"><span data-stu-id="05ed1-235">Exceptions</span></span>](#exceptions) | <span data-ttu-id="05ed1-236">擲回之物件的類型必須為 [System.Exception](xref:System.Exception)，或繼承自它的類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-236">Objects that are thrown shall be of type [System.Exception](xref:System.Exception) or a type inheriting from it.</span></span> <span data-ttu-id="05ed1-237">然而，並不需要使用符合 CLS 標準的方法來封鎖其他類型例外狀況的傳播。</span><span class="sxs-lookup"><span data-stu-id="05ed1-237">Nonetheless, CLS-compliant methods are not required to block the propagation of other types of exceptions.</span></span> | <span data-ttu-id="05ed1-238">40</span><span class="sxs-lookup"><span data-stu-id="05ed1-238">40</span></span>
<span data-ttu-id="05ed1-239">一般</span><span class="sxs-lookup"><span data-stu-id="05ed1-239">General</span></span> | [<span data-ttu-id="05ed1-240">CLS 合規性規則</span><span class="sxs-lookup"><span data-stu-id="05ed1-240">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="05ed1-241">CLS 規則只適用於類型的那些在定義組件以外可存取或可見的部分。</span><span class="sxs-lookup"><span data-stu-id="05ed1-241">CLS rules apply only to those parts of a type that are accessible or visible outsideof the defining assembly.</span></span> | <span data-ttu-id="05ed1-242">1</span><span class="sxs-lookup"><span data-stu-id="05ed1-242">1</span></span>
<span data-ttu-id="05ed1-243">一般</span><span class="sxs-lookup"><span data-stu-id="05ed1-243">General</span></span> | [<span data-ttu-id="05ed1-244">CLS 合規性規則</span><span class="sxs-lookup"><span data-stu-id="05ed1-244">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="05ed1-245">不符合 CLS 標準之類型的成員不得標記為符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-245">Members of non-CLS compliant types shall not be marked CLS-compliant.</span></span> | <span data-ttu-id="05ed1-246">2</span><span class="sxs-lookup"><span data-stu-id="05ed1-246">2</span></span>
<span data-ttu-id="05ed1-247">泛型</span><span class="sxs-lookup"><span data-stu-id="05ed1-247">Generics</span></span> | [<span data-ttu-id="05ed1-248">泛型類型及成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-248">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="05ed1-249">巢狀類型應至少有與其封入類型 (Enclosing Type) 一樣多的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="05ed1-249">Nested types shall have at least as many generic parameters as the enclosing type.</span></span> <span data-ttu-id="05ed1-250">巢狀型別中的泛型參數，都與在其封入型別中泛型參數的位置對應。</span><span class="sxs-lookup"><span data-stu-id="05ed1-250">Generic parameters in a nested type correspond by position to the generic parameters in its enclosing type.</span></span>  | <span data-ttu-id="05ed1-251">42</span><span class="sxs-lookup"><span data-stu-id="05ed1-251">42</span></span>
<span data-ttu-id="05ed1-252">泛型</span><span class="sxs-lookup"><span data-stu-id="05ed1-252">Generics</span></span> | [<span data-ttu-id="05ed1-253">泛型類型及成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-253">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="05ed1-254">根據以上定義的規則，泛型類型的名稱必須編碼非巢狀類型上宣告的型別參數數目或在巢狀類型上新引入的型別參數數目。</span><span class="sxs-lookup"><span data-stu-id="05ed1-254">The name of a generic type shall encode the number of type parameters declared on the non-nested type, or newly introduced to the type if nested, according to the rules defined above.</span></span> | <span data-ttu-id="05ed1-255">43</span><span class="sxs-lookup"><span data-stu-id="05ed1-255">43</span></span>
<span data-ttu-id="05ed1-256">泛型</span><span class="sxs-lookup"><span data-stu-id="05ed1-256">Generics</span></span> | [<span data-ttu-id="05ed1-257">泛型類型及成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-257">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="05ed1-258">泛型類型必須宣告足夠的限制式，才能保證泛型類型限制式將會符合基底類型或介面上的所有限制式。</span><span class="sxs-lookup"><span data-stu-id="05ed1-258">A generic type shall redeclare sufficient constraints to guarantee that any constraints on the base type, or interfaces would be satisfied by the generic type constraints.</span></span> | <span data-ttu-id="05ed1-259">44</span><span class="sxs-lookup"><span data-stu-id="05ed1-259">44</span></span>
<span data-ttu-id="05ed1-260">泛型</span><span class="sxs-lookup"><span data-stu-id="05ed1-260">Generics</span></span> | [<span data-ttu-id="05ed1-261">泛型類型及成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-261">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="05ed1-262">用來做為泛型參數之條件約束的類型，本身也應符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-262">Types used as constraints on generic parameters shall themselves be CLS-compliant.</span></span> | <span data-ttu-id="05ed1-263">45</span><span class="sxs-lookup"><span data-stu-id="05ed1-263">45</span></span>
<span data-ttu-id="05ed1-264">泛型</span><span class="sxs-lookup"><span data-stu-id="05ed1-264">Generics</span></span> | [<span data-ttu-id="05ed1-265">泛型類型及成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-265">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="05ed1-266">具現化 (Instantiated) 泛型類型中成員 (包括巢狀型別) 的可視性和存取範圍，必須被視為屬於特定具現化的範圍，而非泛型類型宣告的範圍。</span><span class="sxs-lookup"><span data-stu-id="05ed1-266">The visibility and accessibility of members (including nested types) in an instantiated generic type shall be considered to be scoped to the specific instantiation rather than the generic type declaration as a whole.</span></span> <span data-ttu-id="05ed1-267">在此假設之下，CLS 第 12 條規則的可視性和存取範圍規則仍然適用。</span><span class="sxs-lookup"><span data-stu-id="05ed1-267">Assuming this, the visibility and accessibility rules of CLS rule 12 still apply.</span></span> | <span data-ttu-id="05ed1-268">46</span><span class="sxs-lookup"><span data-stu-id="05ed1-268">46</span></span>
<span data-ttu-id="05ed1-269">泛型</span><span class="sxs-lookup"><span data-stu-id="05ed1-269">Generics</span></span> | [<span data-ttu-id="05ed1-270">泛型類型及成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-270">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="05ed1-271">對於每個抽象或虛擬泛型方法，都必須具有預設具象 (非抽象) 實作</span><span class="sxs-lookup"><span data-stu-id="05ed1-271">For each abstract or virtual generic method, there shall be a default concrete (nonabstract) implementation</span></span> | <span data-ttu-id="05ed1-272">47</span><span class="sxs-lookup"><span data-stu-id="05ed1-272">47</span></span>
<span data-ttu-id="05ed1-273">介面</span><span class="sxs-lookup"><span data-stu-id="05ed1-273">Interfaces</span></span> | [<span data-ttu-id="05ed1-274">介面</span><span class="sxs-lookup"><span data-stu-id="05ed1-274">Interfaces</span></span>](#interfaces) | <span data-ttu-id="05ed1-275">符合 CLS 標準的介面不可要求不符合 CLS 標準之方法的定義來實作它們。</span><span class="sxs-lookup"><span data-stu-id="05ed1-275">CLS-compliant interfaces shall not require the definition of non-CLS compliantmethods in order to implement them.</span></span> | <span data-ttu-id="05ed1-276">18</span><span class="sxs-lookup"><span data-stu-id="05ed1-276">18</span></span>
<span data-ttu-id="05ed1-277">介面</span><span class="sxs-lookup"><span data-stu-id="05ed1-277">Interfaces</span></span> | [<span data-ttu-id="05ed1-278">介面</span><span class="sxs-lookup"><span data-stu-id="05ed1-278">Interfaces</span></span>](#interfaces) | <span data-ttu-id="05ed1-279">符合 CLS 標準的介面不可定義靜態方法，也不可定義欄位。</span><span class="sxs-lookup"><span data-stu-id="05ed1-279">CLS-compliant interfaces shall not define static methods, nor shall they define fields.</span></span> | <span data-ttu-id="05ed1-280">19</span><span class="sxs-lookup"><span data-stu-id="05ed1-280">19</span></span>
<span data-ttu-id="05ed1-281">成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-281">Members</span></span> | [<span data-ttu-id="05ed1-282">一般類型成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-282">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="05ed1-283">全域靜態欄位和方法不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-283">Global static fields and methods are not CLS-compliant.</span></span> | <span data-ttu-id="05ed1-284">36</span><span class="sxs-lookup"><span data-stu-id="05ed1-284">36</span></span>
<span data-ttu-id="05ed1-285">成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-285">Members</span></span> | -- | <span data-ttu-id="05ed1-286">常值靜態欄位的值是透過使用欄位初始化中繼資料來指定。</span><span class="sxs-lookup"><span data-stu-id="05ed1-286">The value of a literal static is specified through the use of field initialization metadata.</span></span> <span data-ttu-id="05ed1-287">符合 CLS 標準的常值必須具有欄位初始化中繼資料所指定的值，這個中繼資料與常值有完全相同的類型 (如果該常值是 `enum`，則為基礎類型)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-287">A CLS-compliant literal must have a value specified in field initialization metadata that is of exactly the same type as the literal (or of the underlying type, if that literal is an `enum`).</span></span> | <span data-ttu-id="05ed1-288">13</span><span class="sxs-lookup"><span data-stu-id="05ed1-288">13</span></span>
<span data-ttu-id="05ed1-289">成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-289">Members</span></span> | [<span data-ttu-id="05ed1-290">一般類型成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-290">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="05ed1-291">vararg 條件約束不是 CLS 的一部分，CLS 所支援的唯一呼叫慣例是標準的 Managed 呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="05ed1-291">The vararg constraint is not part of the CLS, and the only calling convention supported by the CLS is the standard managed calling convention.</span></span> | <span data-ttu-id="05ed1-292">15</span><span class="sxs-lookup"><span data-stu-id="05ed1-292">15</span></span>
<span data-ttu-id="05ed1-293">命名規範</span><span class="sxs-lookup"><span data-stu-id="05ed1-293">Naming conventions</span></span> | [<span data-ttu-id="05ed1-294">命名慣例</span><span class="sxs-lookup"><span data-stu-id="05ed1-294">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="05ed1-295">組件必須遵守 Unicode Standard 3.0 技術報告編號 15 附錄 7 的各項規則，它規定可以啟始並包含在識別項中的字元集，[Unicode Normalization Forms](http://www.unicode.org/unicode/reports/tr15/tr15-18.html) 線上提供這份報告。</span><span class="sxs-lookup"><span data-stu-id="05ed1-295">Assemblies shall follow Annex 7 of Technical Report 15 of the Unicode Standard3.0 governing the set of characters permitted to start and be included in identifiers, available online at [Unicode Normalization Forms](http://www.unicode.org/unicode/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="05ed1-296">識別項應使用 Unicode Normalization Form C 所定義的標準格式。基於 CLS 目的，如果其小寫對應 (如 Unicode 不區分地區設定、一對一小寫對應所指定) 相同，則兩個識別項相同。</span><span class="sxs-lookup"><span data-stu-id="05ed1-296">Identifiers shall be in the canonical format defined by Unicode Normalization Form C. For CLS purposes, two identifiersare the same if their lowercase mappings (as specified by the Unicode locale-insensitive, one-to-one lowercase mappings) are the same.</span></span> <span data-ttu-id="05ed1-297">也就是依據 CLS，兩個識別項若要被視為不同，不只是大小寫，還要有其他不同之處。</span><span class="sxs-lookup"><span data-stu-id="05ed1-297">That is, for two identifiers to be considered different under the CLS they shall differ in more than simply their case.</span></span> <span data-ttu-id="05ed1-298">不過，為了覆寫繼承的定義，CLI 需要使用原始宣告的確切編碼。</span><span class="sxs-lookup"><span data-stu-id="05ed1-298">However, in order to override an inherited definition the CLI requires the precise encoding of the original declaration be used.</span></span> | <span data-ttu-id="05ed1-299">4</span><span class="sxs-lookup"><span data-stu-id="05ed1-299">4</span></span>
<span data-ttu-id="05ed1-300">多載化</span><span class="sxs-lookup"><span data-stu-id="05ed1-300">Overloading</span></span> | [<span data-ttu-id="05ed1-301">命名慣例</span><span class="sxs-lookup"><span data-stu-id="05ed1-301">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="05ed1-302">在符合 CLS 標準的範圍中引入的所有名稱，除了名稱完全相同且透過多載解析的情況之外，都必須是不同的獨立類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-302">All names introduced in a CLS-compliant scope shall be distinct independent of kind, except where the names are identical and resolved via overloading.</span></span> <span data-ttu-id="05ed1-303">也就是說，CTS 允許單一類型對方法和欄位使用同樣的名稱，但 CLS 不允許。</span><span class="sxs-lookup"><span data-stu-id="05ed1-303">That is, while the CTS allows a single type to use the same name for a method and a field, the CLS does not.</span></span> | <span data-ttu-id="05ed1-304">5</span><span class="sxs-lookup"><span data-stu-id="05ed1-304">5</span></span>
<span data-ttu-id="05ed1-305">多載化</span><span class="sxs-lookup"><span data-stu-id="05ed1-305">Overloading</span></span> | [<span data-ttu-id="05ed1-306">命名慣例</span><span class="sxs-lookup"><span data-stu-id="05ed1-306">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="05ed1-307">即使 CTS 允許區別不同簽章，還是必須單獨依據識別項比較來區別欄位和巢狀類型的不同。</span><span class="sxs-lookup"><span data-stu-id="05ed1-307">Fields and nested types shall be distinct by identifier comparison alone, eventhough the CTS allows distinct signatures to be distinguished.</span></span> <span data-ttu-id="05ed1-308">經由識別項比較之後，具有相同名稱的方法、屬性和事件不可僅以傳回型別做區分，除非 CLS 第 39 條規則中另有指定</span><span class="sxs-lookup"><span data-stu-id="05ed1-308">Methods, properties, and events that have the same name (by identifier comparison) shall differ by more than just the return type,except as specified in CLS Rule 39</span></span> | <span data-ttu-id="05ed1-309">6</span><span class="sxs-lookup"><span data-stu-id="05ed1-309">6</span></span>
<span data-ttu-id="05ed1-310">多載化</span><span class="sxs-lookup"><span data-stu-id="05ed1-310">Overloading</span></span> | [<span data-ttu-id="05ed1-311">多載</span><span class="sxs-lookup"><span data-stu-id="05ed1-311">Overloads</span></span>](#overloads) | <span data-ttu-id="05ed1-312">只有屬性和方法可以多載。</span><span class="sxs-lookup"><span data-stu-id="05ed1-312">Only properties and methods can be overloaded.</span></span> | <span data-ttu-id="05ed1-313">37</span><span class="sxs-lookup"><span data-stu-id="05ed1-313">37</span></span>
<span data-ttu-id="05ed1-314">多載化</span><span class="sxs-lookup"><span data-stu-id="05ed1-314">Overloading</span></span> | [<span data-ttu-id="05ed1-315">多載</span><span class="sxs-lookup"><span data-stu-id="05ed1-315">Overloads</span></span>](#overloads) |<span data-ttu-id="05ed1-316">屬性和方法只可以根據其參數數目和類型多載，除了名為 `op_Implicit` 和 `op_Explicit` 的轉換運算子，也可以根據其傳回類型多載。</span><span class="sxs-lookup"><span data-stu-id="05ed1-316">Properties and methods can be overloaded based only on the number and types of their parameters, except the conversion operators named `op_Implicit` and `op_Explicit`, which can also be overloaded based on their return type.</span></span> | <span data-ttu-id="05ed1-317">38</span><span class="sxs-lookup"><span data-stu-id="05ed1-317">38</span></span>
<span data-ttu-id="05ed1-318">多載化</span><span class="sxs-lookup"><span data-stu-id="05ed1-318">Overloading</span></span> | -- | <span data-ttu-id="05ed1-319">如果在有相同名稱的類型中宣告兩個或更多符合 CLS 標準的方法，則對一組特定的類型具現化來說，它們具有相同的參數和傳回型別，而且所有這些方法在語意上與這些類型具現化相等。</span><span class="sxs-lookup"><span data-stu-id="05ed1-319">If two or more CLS-compliant methods declared in a type have the same nameand, for a specific set of type instantiations, they have the same parameter and return types, then all these methods shall be semantically equivalent at those type instantiations.</span></span> | <span data-ttu-id="05ed1-320">48</span><span class="sxs-lookup"><span data-stu-id="05ed1-320">48</span></span>
<span data-ttu-id="05ed1-321">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-321">Properties</span></span> | [<span data-ttu-id="05ed1-322">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-322">Properties</span></span>](#properties) | <span data-ttu-id="05ed1-323">實作屬性之 getter 和 setter 方法的方法在中繼資料中應標記為 `SpecialName`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-323">The methods that implement the getter and setter methods of a property shall be marked `SpecialName` in the metadata.</span></span> | <span data-ttu-id="05ed1-324">24</span><span class="sxs-lookup"><span data-stu-id="05ed1-324">24</span></span>
<span data-ttu-id="05ed1-325">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-325">Properties</span></span> | [<span data-ttu-id="05ed1-326">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-326">Properties</span></span>](#properties) | <span data-ttu-id="05ed1-327">屬性的存取子必須全部為 static、全部為 virtual 或全部為 instance。</span><span class="sxs-lookup"><span data-stu-id="05ed1-327">A property’s accessors shall all be static, all be virtual, or all be instance.</span></span> | <span data-ttu-id="05ed1-328">26</span><span class="sxs-lookup"><span data-stu-id="05ed1-328">26</span></span>
<span data-ttu-id="05ed1-329">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-329">Properties</span></span> | [<span data-ttu-id="05ed1-330">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-330">Properties</span></span>](#properties) | <span data-ttu-id="05ed1-331">屬性的類型應是 getter 的傳回型別和 setter 最後一個引數的類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-331">The type of a property shall be the return type of the getter and the type of the last argument of the setter.</span></span> <span data-ttu-id="05ed1-332">屬性參數的類型必須是 getter 參數的類型和 setter 除了最後一個參數之外的所有參數類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-332">The types of the parameters of the property shall be the types of the parameters to the getter and the types of all but the final parameter of the setter.</span></span> <span data-ttu-id="05ed1-333">所有這些類型都必須符合 CLS 規範，而且不能是 Managed 指標 (也就是，不能以傳址方式傳遞)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-333">All of these types shall be CLS-compliant, and shall not be managed pointers (that is, shall not be passed by reference).</span></span> | <span data-ttu-id="05ed1-334">27</span><span class="sxs-lookup"><span data-stu-id="05ed1-334">27</span></span>
<span data-ttu-id="05ed1-335">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-335">Properties</span></span> | [<span data-ttu-id="05ed1-336">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-336">Properties</span></span>](#properties) | <span data-ttu-id="05ed1-337">屬性必須遵守特定的命名模式。</span><span class="sxs-lookup"><span data-stu-id="05ed1-337">Properties shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="05ed1-338">在適當的名稱比較中應忽略 CLS 第 24 條規則中所提及的 `SpecialName` 屬性，並且應遵循識別項規則。</span><span class="sxs-lookup"><span data-stu-id="05ed1-338">The `SpecialName` attribute referred to in CLS rule 24 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span> <span data-ttu-id="05ed1-339">屬性必須有 getter 方法、setter 方法或兩者皆有。</span><span class="sxs-lookup"><span data-stu-id="05ed1-339">A property shall have a getter method, a setter method, or both.</span></span> | <span data-ttu-id="05ed1-340">28</span><span class="sxs-lookup"><span data-stu-id="05ed1-340">28</span></span>
<span data-ttu-id="05ed1-341">類型轉換</span><span class="sxs-lookup"><span data-stu-id="05ed1-341">Type conversion</span></span> | [<span data-ttu-id="05ed1-342">類型轉換</span><span class="sxs-lookup"><span data-stu-id="05ed1-342">Type conversion</span></span>](#type-conversion) | <span data-ttu-id="05ed1-343">如果有提供 op_Implicit 或 op_Explicit，則必須提供替代方式來提供強制型轉。</span><span class="sxs-lookup"><span data-stu-id="05ed1-343">If either op_Implicit or op_Explicit is provided, an alternate means of providing the coercion shall be provided.</span></span> | <span data-ttu-id="05ed1-344">39</span><span class="sxs-lookup"><span data-stu-id="05ed1-344">39</span></span>
<span data-ttu-id="05ed1-345">類型</span><span class="sxs-lookup"><span data-stu-id="05ed1-345">Types</span></span> | [<span data-ttu-id="05ed1-346">類型及類型成員簽章</span><span class="sxs-lookup"><span data-stu-id="05ed1-346">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="05ed1-347">Boxed 實值類型不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-347">Boxed value types are not CLS-compliant.</span></span> | <span data-ttu-id="05ed1-348">3</span><span class="sxs-lookup"><span data-stu-id="05ed1-348">3</span></span>
<span data-ttu-id="05ed1-349">類型</span><span class="sxs-lookup"><span data-stu-id="05ed1-349">Types</span></span> | [<span data-ttu-id="05ed1-350">類型及類型成員簽章</span><span class="sxs-lookup"><span data-stu-id="05ed1-350">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="05ed1-351">簽章中出現的所有類型都必須符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-351">All types appearing in a signature shall be CLS-compliant.</span></span> <span data-ttu-id="05ed1-352">構成具現化泛型類型的所有類型都必須符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-352">All types composing an instantiated generic type shall be CLS-compliant.</span></span> | <span data-ttu-id="05ed1-353">11</span><span class="sxs-lookup"><span data-stu-id="05ed1-353">11</span></span>
<span data-ttu-id="05ed1-354">類型</span><span class="sxs-lookup"><span data-stu-id="05ed1-354">Types</span></span> | [<span data-ttu-id="05ed1-355">類型及類型成員簽章</span><span class="sxs-lookup"><span data-stu-id="05ed1-355">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="05ed1-356">具型別的參考不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="05ed1-356">Typed references are not CLS-compliant.</span></span> | <span data-ttu-id="05ed1-357">14</span><span class="sxs-lookup"><span data-stu-id="05ed1-357">14</span></span>
<span data-ttu-id="05ed1-358">類型</span><span class="sxs-lookup"><span data-stu-id="05ed1-358">Types</span></span> | [<span data-ttu-id="05ed1-359">類型及類型成員簽章</span><span class="sxs-lookup"><span data-stu-id="05ed1-359">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="05ed1-360">Unmanaged 指標類型不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-360">Unmanaged pointer types are not CLS-compliant.</span></span> | <span data-ttu-id="05ed1-361">17</span><span class="sxs-lookup"><span data-stu-id="05ed1-361">17</span></span>
<span data-ttu-id="05ed1-362">類型</span><span class="sxs-lookup"><span data-stu-id="05ed1-362">Types</span></span> | [<span data-ttu-id="05ed1-363">類型及類型成員簽章</span><span class="sxs-lookup"><span data-stu-id="05ed1-363">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="05ed1-364">符合 CLS 標準的類別、實值型別和介面不能要求不符合 CLS 標準的成員實作</span><span class="sxs-lookup"><span data-stu-id="05ed1-364">CLS-compliant classes, value types, and interfaces shall not require the implementation of non-CLS-compliant members</span></span> | <span data-ttu-id="05ed1-365">20</span><span class="sxs-lookup"><span data-stu-id="05ed1-365">20</span></span>
<span data-ttu-id="05ed1-366">類型</span><span class="sxs-lookup"><span data-stu-id="05ed1-366">Types</span></span> | [<span data-ttu-id="05ed1-367">類型及類型成員簽章</span><span class="sxs-lookup"><span data-stu-id="05ed1-367">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="05ed1-368">[System.Object](xref:System.Object) 符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-368">[System.Object](xref:System.Object) is CLS-compliant.</span></span> <span data-ttu-id="05ed1-369">任何其他符合 CLS 標準的類別也都必須繼承自符合 CLS 標準的類別。</span><span class="sxs-lookup"><span data-stu-id="05ed1-369">Any other CLS-compliant class shall inherit from a CLS-compliant class.</span></span> | <span data-ttu-id="05ed1-370">23</span><span class="sxs-lookup"><span data-stu-id="05ed1-370">23</span></span>

### <a name="types-and-type-member-signatures"></a><span data-ttu-id="05ed1-371">類型和類型成員簽章</span><span class="sxs-lookup"><span data-stu-id="05ed1-371">Types and type member signatures</span></span>

<span data-ttu-id="05ed1-372">[System.Object](xref:System.Object) 類型符合 CLS 標準，並且是 .NET Framework 型別系統中所有物件類型的基底類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-372">The [System.Object](xref:System.Object) type is CLS-compliant and is the base type of all object types in the .NET Framework type system.</span></span> <span data-ttu-id="05ed1-373">.NET Framework 中的繼承若不是隱含的 (例如，[String](xref:System.String) 類別隱含自繼承 `Object` 類別)，就是明確的 (例如，[CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) 類別明確繼承自 [ArgumentException](xref:System.ArgumentException) 類別，後者又明確繼承自 [Exception](xref:System.Exception) 類別)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-373">Inheritance in the .NET Framework is either implicit (for example, the [String](xref:System.String) class implicitly inherits from the `Object` class) or explicit (for example, the [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) class explicitly inherits from the [ArgumentException](xref:System.ArgumentException) class, which explicitly inherits from the [Exception](xref:System.Exception) class.</span></span> <span data-ttu-id="05ed1-374">若要讓衍生類型符合 CLS 標準，其基底類型必須符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-374">For a derived type to be CLS compliant, its base type must also be CLS-compliant.</span></span> 

<span data-ttu-id="05ed1-375">下面範例會示範其基底類型不符合 CLS 標準的衍生類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-375">The following example shows a derived type whose base type is not CLS-compliant.</span></span> <span data-ttu-id="05ed1-376">它會定義基底 `Counter` 類別，這個類別使用不帶正負號的 32 位元整數做為計數器。</span><span class="sxs-lookup"><span data-stu-id="05ed1-376">It defines a base `Counter` class that uses an unsigned 32-bit integer as a counter.</span></span> <span data-ttu-id="05ed1-377">因為該類別會藉由包裝不帶正負號的整數提供計數器功能，所以該類別會標記為不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-377">Because the class provides counter functionality by wrapping an unsigned integer, the class is marked as non-CLS-compliant.</span></span> <span data-ttu-id="05ed1-378">結果，衍生的類別 `NonZeroCounter` 也不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-378">As a result, a derived class, `NonZeroCounter`, is also not CLS-compliant.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

[CLSCompliant(false)] 
public class Counter
{
   UInt32 ctr;

   public Counter()
   {
      ctr = 0;
   }

   protected Counter(UInt32 ctr)
   {
      this.ctr = ctr;
   }

   public override string ToString()
   {
      return String.Format("{0}). ", ctr);
   }

   public UInt32 Value
   {
      get { return ctr; }
   }

   public void Increment() 
   {
      ctr += (uint) 1;
   }
}

public class NonZeroCounter : Counter
{
   public NonZeroCounter(int startIndex) : this((uint) startIndex)
   {
   }

   private NonZeroCounter(UInt32 startIndex) : base(startIndex)
   {
   }
}
// Compilation produces a compiler warning like the following:
//    Type3.cs(37,14): warning CS3009: 'NonZeroCounter': base type 'Counter' is not
//            CLS-compliant
//    Type3.cs(7,14): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>

<CLSCompliant(False)> _ 
Public Class Counter
   Dim ctr As UInt32

   Public Sub New
      ctr = 0
   End Sub

   Protected Sub New(ctr As UInt32)
      ctr = ctr
   End Sub

   Public Overrides Function ToString() As String
      Return String.Format("{0}). ", ctr)
   End Function

   Public ReadOnly Property Value As UInt32
      Get
         Return ctr
      End Get
   End Property

   Public Sub Increment()
      ctr += CType(1, UInt32)
   End Sub
End Class

Public Class NonZeroCounter : Inherits Counter
   Public Sub New(startIndex As Integer)
      MyClass.New(CType(startIndex, UInt32))
   End Sub

   Private Sub New(startIndex As UInt32)
      MyBase.New(CType(startIndex, UInt32))
   End Sub
End Class
' Compilation produces a compiler warning like the following:
'    Type3.vb(34) : warning BC40026: 'NonZeroCounter' is not CLS-compliant 
'    because it derives from 'Counter', which is not CLS-compliant.
'    
'    Public Class NonZeroCounter : Inherits Counter
'                 ~~~~~~~~~~~~~~
```

<span data-ttu-id="05ed1-379">成員簽章中出現的所有類型 (包括方法的傳回型別或屬性類型) 都必須符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-379">All types that appear in member signatures, including a method's return type or a property type, must be CLS-compliant.</span></span> <span data-ttu-id="05ed1-380">此外，如果是泛型類型：</span><span class="sxs-lookup"><span data-stu-id="05ed1-380">In addition, for generic types:</span></span> 

* <span data-ttu-id="05ed1-381">構成具現化泛型類型的所有類型都必須符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-381">All types that compose an instantiated generic type must be CLS-compliant.</span></span>

* <span data-ttu-id="05ed1-382">所有用來做為泛型參數之限制式的類型，都必須符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-382">All types used as constraints on generic parameters must be CLS-compliant.</span></span> 

<span data-ttu-id="05ed1-383">.NET 的[一般型別系統](common-type-system.md)包含了幾個內建類型，這些內建類型直接受到 Common Language Runtime 的支援，並且在組譯碼的中繼資料中以特殊方式進行編碼。</span><span class="sxs-lookup"><span data-stu-id="05ed1-383">The .NET [common type system](common-type-system.md) includes a number of built-in types that are supported directly by the common language runtime and are specially encoded in an assembly's metadata.</span></span> <span data-ttu-id="05ed1-384">在這些內建類型中，下表所列的類型符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-384">Of these intrinsic types, the types listed in the following table are CLS-compliant.</span></span> 


<span data-ttu-id="05ed1-385">符合 CLS 標準的類型</span><span class="sxs-lookup"><span data-stu-id="05ed1-385">CLS-compliant type</span></span> | <span data-ttu-id="05ed1-386">描述</span><span class="sxs-lookup"><span data-stu-id="05ed1-386">Description</span></span>
------------------ | -----------
[<span data-ttu-id="05ed1-387">Byte</span><span class="sxs-lookup"><span data-stu-id="05ed1-387">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="05ed1-388">8 位元不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="05ed1-388">8-bit unsigned integer</span></span> 
[<span data-ttu-id="05ed1-389">Int16</span><span class="sxs-lookup"><span data-stu-id="05ed1-389">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="05ed1-390">16 位元帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="05ed1-390">16-bit signed integer</span></span> 
[<span data-ttu-id="05ed1-391">Int32</span><span class="sxs-lookup"><span data-stu-id="05ed1-391">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="05ed1-392">32 位元帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="05ed1-392">32-bit signed integer</span></span> 
[<span data-ttu-id="05ed1-393">Int64</span><span class="sxs-lookup"><span data-stu-id="05ed1-393">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="05ed1-394">64 位元帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="05ed1-394">64-bit signed integer</span></span>
[<span data-ttu-id="05ed1-395">Single</span><span class="sxs-lookup"><span data-stu-id="05ed1-395">Single</span></span>](xref:System.Single) | <span data-ttu-id="05ed1-396">單精確度浮點值</span><span class="sxs-lookup"><span data-stu-id="05ed1-396">Single-precision floating-point value</span></span>
[<span data-ttu-id="05ed1-397">Double</span><span class="sxs-lookup"><span data-stu-id="05ed1-397">Double</span></span>](xref:System.Double) | <span data-ttu-id="05ed1-398">雙精確度浮點值</span><span class="sxs-lookup"><span data-stu-id="05ed1-398">Double-precision floating-point value</span></span>
[<span data-ttu-id="05ed1-399">布林值</span><span class="sxs-lookup"><span data-stu-id="05ed1-399">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="05ed1-400">true 或 false 實值型別</span><span class="sxs-lookup"><span data-stu-id="05ed1-400">true or false value type</span></span> 
[<span data-ttu-id="05ed1-401">Char</span><span class="sxs-lookup"><span data-stu-id="05ed1-401">Char</span></span>](xref:System.Char) | <span data-ttu-id="05ed1-402">UTF-16 編碼程式碼單位</span><span class="sxs-lookup"><span data-stu-id="05ed1-402">UTF-16 encoded code unit</span></span>
[<span data-ttu-id="05ed1-403">Decimal</span><span class="sxs-lookup"><span data-stu-id="05ed1-403">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="05ed1-404">非浮點十進位數字</span><span class="sxs-lookup"><span data-stu-id="05ed1-404">Non-floating-point decimal number</span></span>
[<span data-ttu-id="05ed1-405">IntPtr</span><span class="sxs-lookup"><span data-stu-id="05ed1-405">IntPtr</span></span>](xref:System.IntPtr) | <span data-ttu-id="05ed1-406">平台定義大小的指標或控制代碼</span><span class="sxs-lookup"><span data-stu-id="05ed1-406">Pointer or handle of a platform-defined size</span></span>
[<span data-ttu-id="05ed1-407">String</span><span class="sxs-lookup"><span data-stu-id="05ed1-407">String</span></span>](xref:System.String) | <span data-ttu-id="05ed1-408">零個、一個或多個 Char 物件的集合</span><span class="sxs-lookup"><span data-stu-id="05ed1-408">Collection of zero, one, or more Char objects</span></span> 
 
<span data-ttu-id="05ed1-409">下表所列的內建類型不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-409">The intrinsic types listed in the following table are not CLS-Compliant.</span></span>


<span data-ttu-id="05ed1-410">不符合標準的類型</span><span class="sxs-lookup"><span data-stu-id="05ed1-410">Non-compliant type</span></span> | <span data-ttu-id="05ed1-411">描述</span><span class="sxs-lookup"><span data-stu-id="05ed1-411">Description</span></span> | <span data-ttu-id="05ed1-412">符合 CLS 標準的替代項目</span><span class="sxs-lookup"><span data-stu-id="05ed1-412">CLS-compliant alternative</span></span>
------------------ | ----------- | -------------------------
[<span data-ttu-id="05ed1-413">SByte</span><span class="sxs-lookup"><span data-stu-id="05ed1-413">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="05ed1-414">8 位元帶正負號的整數資料類型</span><span class="sxs-lookup"><span data-stu-id="05ed1-414">8-bit signed integer data type</span></span> | [<span data-ttu-id="05ed1-415">Int16</span><span class="sxs-lookup"><span data-stu-id="05ed1-415">Int16</span></span>](xref:System.Int16)
[<span data-ttu-id="05ed1-416">UInt16</span><span class="sxs-lookup"><span data-stu-id="05ed1-416">UInt16</span></span>](xref:System.UInt16) | <span data-ttu-id="05ed1-417">16 位元不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="05ed1-417">16-bit unsigned integer</span></span> | [<span data-ttu-id="05ed1-418">Int32</span><span class="sxs-lookup"><span data-stu-id="05ed1-418">Int32</span></span>](xref:System.Int32)
[<span data-ttu-id="05ed1-419">UInt32</span><span class="sxs-lookup"><span data-stu-id="05ed1-419">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="05ed1-420">32 位元不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="05ed1-420">32-bit unsigned integer</span></span> | [<span data-ttu-id="05ed1-421">Int64</span><span class="sxs-lookup"><span data-stu-id="05ed1-421">Int64</span></span>](xref:System.Int64)
[<span data-ttu-id="05ed1-422">UInt64</span><span class="sxs-lookup"><span data-stu-id="05ed1-422">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="05ed1-423">64 位元不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="05ed1-423">64-bit unsigned integer</span></span> | <span data-ttu-id="05ed1-424">[Int64](xref:System.Int64) (可能溢位)、[BigInteger](xref:System.Numerics.BigInteger) 或 [Double](xref:System.Double)</span><span class="sxs-lookup"><span data-stu-id="05ed1-424">[Int64](xref:System.Int64) (may overflow), [BigInteger](xref:System.Numerics.BigInteger), or [Double](xref:System.Double)</span></span>
[<span data-ttu-id="05ed1-425">UIntPtr</span><span class="sxs-lookup"><span data-stu-id="05ed1-425">UIntPtr</span></span>](xref:System.UIntPtr) | <span data-ttu-id="05ed1-426">不帶正負號的指標或控制代碼</span><span class="sxs-lookup"><span data-stu-id="05ed1-426">Unsigned pointer or handle</span></span> | [<span data-ttu-id="05ed1-427">IntPtr</span><span class="sxs-lookup"><span data-stu-id="05ed1-427">IntPtr</span></span>](xref:System.IntPtr)
 
 <span data-ttu-id="05ed1-428">.NET Framework 類別庫或其他類別庫可能包含不符合 CLS 標準的其他類型，例如：</span><span class="sxs-lookup"><span data-stu-id="05ed1-428">The .NET Framework Class Library or any other class library may include other types that aren't CLS-compliant; for example:</span></span> 
 
 * <span data-ttu-id="05ed1-429">Boxed 實值類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-429">Boxed value types.</span></span> <span data-ttu-id="05ed1-430">下面 C# 範例會建立類別，具有類型為 `int`\* 且名為 `Value` 的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="05ed1-430">The following C# example creates a class that has a public property of type `int`\* named `Value`.</span></span> <span data-ttu-id="05ed1-431">由於 `int`\* 為 Boxed 實值型別，因此編譯器將其標示為不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-431">Because an `int`\* is a boxed value type, the compiler flags it as non-CLS-compliant.</span></span>

  ```csharp
  using System;

  [assembly:CLSCompliant(true)]

  public unsafe class TestClass
  {
     private int* val;

     public TestClass(int number)
     {
        val = (int*) number;
     }

     public int* Value {
        get { return val; }        
     }
  }
  // The compiler generates the following output when compiling this example:
  //        warning CS3003: Type of 'TestClass.Value' is not CLS-compliant
  ```

* <span data-ttu-id="05ed1-432">具類型參考，是一種含有物件參考和類型參考的特殊建構。</span><span class="sxs-lookup"><span data-stu-id="05ed1-432">Typed references, which are special constructs that contain a reference to an object and a reference to a type.</span></span>

<span data-ttu-id="05ed1-433">如果類型不符合 CLS 標準，您應該套用 [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 屬性，並將值為 `false` 的 *isCompliant* 參數指派給它。</span><span class="sxs-lookup"><span data-stu-id="05ed1-433">If a type is not CLS-compliant, you should apply the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute with an *isCompliant* parameter with a value of `false` to it.</span></span> <span data-ttu-id="05ed1-434">如需詳細資訊，請參閱 [CLSCompliantAttribute 屬性](#the-clscompliantattribute-attribute)一節。</span><span class="sxs-lookup"><span data-stu-id="05ed1-434">For more information, see the [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute) section.</span></span>  

<span data-ttu-id="05ed1-435">下面範例說明在方法簽章和泛型類型具現化中的 CLS 符合性問題。</span><span class="sxs-lookup"><span data-stu-id="05ed1-435">The following example illustrates the problem of CLS compliance in a method signature and in generic type instantiation.</span></span> <span data-ttu-id="05ed1-436">它會定義 `InvoiceItem` 類別，包含 [UInt32](xref:System.UInt32) 類型的屬性、[Nullable(Of UInt32)](xref:System.Nullable%601) 類型的屬性，以及參數類型為 `UInt32` 和 `Nullable(Of UInt32)` 的建構函式。</span><span class="sxs-lookup"><span data-stu-id="05ed1-436">It defines an `InvoiceItem` class with a property of type [UInt32](xref:System.UInt32), a property of type [Nullable(Of UInt32)](xref:System.Nullable%601), and a constructor with parameters of type `UInt32` and `Nullable(Of UInt32)`.</span></span> <span data-ttu-id="05ed1-437">當您嘗試編譯這個範例時，會收到四個編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="05ed1-437">You get four compiler warnings when you try to compile this example.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<uint> qty;

   public InvoiceItem(uint sku, Nullable<uint> quantity)
   {
      itemId = sku;
      qty = quantity;
   }

   public Nullable<uint> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public uint InvoiceId
   {
      get { return invId; }
      set { invId = value; }
   }
}
// The attempt to compile the example displays the following output:
//    Type1.cs(13,23): warning CS3001: Argument type 'uint' is not CLS-compliant
//    Type1.cs(13,33): warning CS3001: Argument type 'uint?' is not CLS-compliant
//    Type1.cs(19,26): warning CS3003: Type of 'InvoiceItem.Quantity' is not CLS-compliant
//    Type1.cs(25,16): warning CS3003: Type of 'InvoiceItem.InvoiceId' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of UInteger)

   Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
      itemId = sku
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of UInteger)
      Get
         Return qty
      End Get   
      Set 
         qty = value
      End Set   
   End Property

   Public Property InvoiceId As UInteger
      Get   
         Return invId
      End Get
      Set 
         invId = value
      End Set   
   End Property
End Class
' The attempt to compile the example displays output similar to the following:
'    Type1.vb(13) : warning BC40028: Type of parameter 'sku' is not CLS-compliant.
'    
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                      ~~~
'    Type1.vb(13) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'    
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                                                               ~~~~~~~~
'    Type1.vb(18) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'    
'       Public Property Quantity As Nullable(Of UInteger)
'                                               ~~~~~~~~
'    Type1.vb(27) : warning BC40027: Return type of function 'InvoiceId' is not CLS-compliant.
'    
'       Public Property InvoiceId As UInteger
```

<span data-ttu-id="05ed1-438">若要排除編譯器警告，請將 `InvoiceItem` 公用介面中不符合 CLS 標準的類型取代為與符合標準的類型：</span><span class="sxs-lookup"><span data-stu-id="05ed1-438">To eliminate the compiler warnings, replace the non-CLS-compliant types in the `InvoiceItem` public interface with compliant types:</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<int> qty;

   public InvoiceItem(int sku, Nullable<int> quantity)
   {
      if (sku <= 0)
         throw new ArgumentOutOfRangeException("The item number is zero or negative.");
      itemId = (uint) sku;

      qty = quantity;
   }

   public Nullable<int> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public int InvoiceId
   {
      get { return (int) invId; }
      set { 
         if (value <= 0)
            throw new ArgumentOutOfRangeException("The invoice number is zero or negative.");
         invId = (uint) value; }
   }
}
```

```vb
Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of Integer)

   Public Sub New(sku As Integer, quantity As Nullable(Of Integer))
      If sku <= 0 Then
         Throw New ArgumentOutOfRangeException("The item number is zero or negative.")
      End If
      itemId = CUInt(sku)
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of Integer)
      Get
         Return qty
      End Get   
      Set 
         qty = value
      End Set   
   End Property

   Public Property InvoiceId As Integer
      Get   
         Return CInt(invId)
      End Get
      Set 
         invId = CUInt(value)
      End Set   
   End Property
End Class
```

<span data-ttu-id="05ed1-439">除了列出的特定類型之外，有些分類的類型也不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-439">In addition to the specific types listed, some categories of types are not CLS compliant.</span></span> <span data-ttu-id="05ed1-440">這些包括 Unmanaged 指標類型和函式指標類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-440">These include unmanaged pointer types and function pointer types.</span></span> <span data-ttu-id="05ed1-441">下面範例會產生編譯器警告，因為它使用整數指標建立整數陣列。</span><span class="sxs-lookup"><span data-stu-id="05ed1-441">The following example generates a compiler warning because it uses a pointer to an integer to create an array of integers.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}   
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

```vb
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}   
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

<span data-ttu-id="05ed1-442">如果是符合 CLS 標準的抽象類別 (也就是在 C# 中標記為 `abstract`)，類別的所有成員也必須符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-442">For CLS-compliant abstract classes (that is, classes marked as `abstract` in C#), all members of the class must also be CLS-compliant.</span></span> 

### <a name="naming-conventions"></a><span data-ttu-id="05ed1-443">命名規範</span><span class="sxs-lookup"><span data-stu-id="05ed1-443">Naming conventions</span></span>

<span data-ttu-id="05ed1-444">由於某些程式語言不區分大小寫，識別項 (例如命名空間、類型和成員的名稱) 必須透過區分大小寫以外的方式產生差異。</span><span class="sxs-lookup"><span data-stu-id="05ed1-444">Because some programming languages are case-insensitive, identifiers (such as the names of namespaces, types, and members) must differ by more than case.</span></span> <span data-ttu-id="05ed1-445">如果兩個識別項的小寫對應是相同的，則這兩個識別項是視為相等。</span><span class="sxs-lookup"><span data-stu-id="05ed1-445">Two identifiers are considered equivalent if their lowercase mappings are the same.</span></span> <span data-ttu-id="05ed1-446">下面 C# 範例會定義兩個公用類別：`Person` 和 `person`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-446">The following C# example defines two public classes, `Person` and `person`.</span></span> <span data-ttu-id="05ed1-447">因為只有大小寫不同，所以 C# 編譯器會將其標示為不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-447">Because they differ only by case, the C# compiler flags them as not CLS-compliant.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person : person
{

}

public class person
{

}
// Compilation produces a compiler warning like the following:
//    Naming1.cs(11,14): warning CS3005: Identifier 'person' differing 
//                       only in case is not CLS-compliant
//    Naming1.cs(6,14): (Location of symbol related to previous warning)
```

<span data-ttu-id="05ed1-448">程式語言識別項，例如命名空間、類型和成員的名稱，必須符合 [Unicode Standard 3.0 Technical Report 15 的 Annex 7](https://www.unicode.org/reports/tr15/tr15-18.html)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-448">Programming language identifiers, such as the names of namespaces, types, and members, must conform to the [Unicode Standard 3.0, Technical Report 15, Annex 7](https://www.unicode.org/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="05ed1-449">這表示：</span><span class="sxs-lookup"><span data-stu-id="05ed1-449">This means that:</span></span>

* <span data-ttu-id="05ed1-450">識別項的第一個字元可以是任何 Unicode 大寫字母、小寫字母、標題大寫字母、修飾詞字母、其他字母或字母數字。</span><span class="sxs-lookup"><span data-stu-id="05ed1-450">The first character of an identifier can be any Unicode uppercase letter, lowercase letter, title case letter, modifier letter, other letter, or letter number.</span></span> <span data-ttu-id="05ed1-451">如需 Unicode 字元分類的資訊，請參閱 [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) 列舉。</span><span class="sxs-lookup"><span data-stu-id="05ed1-451">For information on Unicode character categories, see the [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) enumeration.</span></span> 

* <span data-ttu-id="05ed1-452">接下來的字元可以來自和第一個字元相同的任何分類，而且也可以包含非間距記號、間距組合記號、十進位數字、連接子標點符號和格式化程式碼。</span><span class="sxs-lookup"><span data-stu-id="05ed1-452">Subsequent characters can be from any of the categories as the first character, and can also include non-spacing marks, spacing combining marks, decimal numbers, connector punctuations, and formatting codes.</span></span> 

<span data-ttu-id="05ed1-453">在您比較識別項之前，應該先篩掉格式化程式碼，並將識別項轉換為 Unicode 正規化表單 C，因為單一字元可由多個 UTF 16 編碼字碼單位表示。</span><span class="sxs-lookup"><span data-stu-id="05ed1-453">Before you compare identifiers, you should filter out formatting codes and convert the identifiers to Unicode Normalization Form C, because a single character can be represented by multiple UTF-16-encoded code units.</span></span> <span data-ttu-id="05ed1-454">產生和 Unicode 正規化表單 C 相同的字碼單位的字元順序不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-454">Character sequences that produce the same code units in Unicode Normalization Form C are not CLS-compliant.</span></span> <span data-ttu-id="05ed1-455">下面範例會定義名為 `Å` 的屬性和名為 `Å` 的第二個屬性。前者包含 ANGSTROM SIGN 字元 (U+212B)，後者包含 LATIN CAPITAL LETTER A WITH RING ABOVE 字元 (U+00C5)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-455">The following example defines a property named `Å`, which consists of the character ANGSTROM SIGN (U+212B), and a second property named `Å` which consists of the character LATIN CAPITAL LETTER A WITH RING ABOVE (U+00C5).</span></span> <span data-ttu-id="05ed1-456">C# 編譯器會將原始程式碼標示為不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-456">The C# compiler flags the source code as non-CLS-compliant.</span></span>

```csharp
public class Size
{
   private double a1;
   private double a2;

   public double Å
   {
       get { return a1; }
       set { a1 = value; }
   }         

   public double Å
   {
       get { return a2; }
       set { a2 = value; }
   }
}
// Compilation produces a compiler warning like the following:
//    Naming2a.cs(16,18): warning CS3005: Identifier 'Size.Å' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(10,18): (Location of symbol related to previous warning)
//    Naming2a.cs(18,8): warning CS3005: Identifier 'Size.Å.get' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(12,8): (Location of symbol related to previous warning)
//    Naming2a.cs(19,8): warning CS3005: Identifier 'Size.Å.set' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(13,8): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>
Public Class Size
   Private a1 As Double
   Private a2 As Double

   Public Property Å As Double
       Get
          Return a1
       End Get
       Set 
          a1 = value
       End Set
   End Property         

   Public Property Å As Double
       Get
          Return a2
       End Get
       Set
          a2 = value
       End Set   
   End Property
End Class
' Compilation produces a compiler warning like the following:
'    Naming1.vb(9) : error BC30269: 'Public Property Å As Double' has multiple definitions
'     with identical signatures.
'    
'       Public Property Å As Double
'                       ~
```

<span data-ttu-id="05ed1-457">特定範圍內的成員名稱 (例如組件中的命名空間、命名空間中的類型或類型中的成員)，除了透過多載解析的名稱以外，都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="05ed1-457">Member names within a particular scope (such as the namespaces within an assembly, the types within a namespace, or the members within a type) must be unique except for names that are resolved through overloading.</span></span> <span data-ttu-id="05ed1-458">這個需求比一般類型系統的需求更嚴格，後者允許在範圍內的多個成員具有相同名稱，只要它們是不同的類型成員 (例如，一個是方法，一個是欄位)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-458">This requirement is more stringent than that of the common type system, which allows multiple members within a scope to have identical names as long as they are different kinds of members (for example, one is a method and one is a field).</span></span> <span data-ttu-id="05ed1-459">特別是，如果是類型成員：</span><span class="sxs-lookup"><span data-stu-id="05ed1-459">In particular, for type members:</span></span> 

* <span data-ttu-id="05ed1-460">欄位和巢狀類型只有依據名稱做區別。</span><span class="sxs-lookup"><span data-stu-id="05ed1-460">Fields and nested types are distinguished by name alone.</span></span> 

* <span data-ttu-id="05ed1-461">具有相同名稱的方法、屬性和事件不可僅以傳回類型做區分。</span><span class="sxs-lookup"><span data-stu-id="05ed1-461">Methods, properties, and events that have the same name must differ by more than just return type.</span></span> 

<span data-ttu-id="05ed1-462">下面範例說明成員名稱在其範圍內必須是唯一的這個需求。</span><span class="sxs-lookup"><span data-stu-id="05ed1-462">The following example illustrates the requirement that member names must be unique within their scope.</span></span> <span data-ttu-id="05ed1-463">它會定義名為 `Converter` 的類別，其中包含四個名為 `Conversion` 的成員。</span><span class="sxs-lookup"><span data-stu-id="05ed1-463">It defines a class named `Converter` that includes four members named `Conversion`.</span></span> <span data-ttu-id="05ed1-464">三個是方法，一個是屬性。</span><span class="sxs-lookup"><span data-stu-id="05ed1-464">Three are methods, and one is a property.</span></span> <span data-ttu-id="05ed1-465">包含 `Int64` 參數的方法具有唯一的名稱，但含有 `Int32` 參數的兩個方法則沒有唯一名稱，因為傳回值不視為成員簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="05ed1-465">The method that includes an `Int64` parameter is uniquely named, but the two methods with an `Int32` parameter are not, because return value is not considered a part of a member's signature.</span></span> <span data-ttu-id="05ed1-466">`Conversion` 屬性也違反這項需求，因為屬性不能與多載方法同名。</span><span class="sxs-lookup"><span data-stu-id="05ed1-466">The `Conversion` property also violates this requirement, because properties cannot have the same name as overloaded methods.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Converter
{
   public double Conversion(int number)
   {
      return (double) number;
   }

   public float Conversion(int number)
   {
      return (float) number;
   }

   public double Conversion(long number)
   {
      return (double) number;
   }

   public bool Conversion
   {
      get { return true; }
   }     
}  
// Compilation produces a compiler error like the following:
//    Naming3.cs(13,17): error CS0111: Type 'Converter' already defines a member called
//            'Conversion' with the same parameter types
//    Naming3.cs(8,18): (Location of symbol related to previous error)
//    Naming3.cs(23,16): error CS0102: The type 'Converter' already contains a definition for
//            'Conversion'
//    Naming3.cs(8,18): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Converter
   Public Function Conversion(number As Integer) As Double
      Return CDbl(number)
   End Function

   Public Function Conversion(number As Integer) As Single
      Return CSng(number)
   End Function

   Public Function Conversion(number As Long) As Double
      Return CDbl(number)
   End Function

   Public ReadOnly Property Conversion As Boolean
      Get
         Return True
      End Get   
   End Property     
End Class
' Compilation produces a compiler error like the following:
'    Naming3.vb(8) : error BC30301: 'Public Function Conversion(number As Integer) As Double' 
'                    and 'Public Function Conversion(number As Integer) As Single' cannot 
'                    overload each other because they differ only by return types.
'    
'       Public Function Conversion(number As Integer) As Double
'                       ~~~~~~~~~~
'    Naming3.vb(20) : error BC30260: 'Conversion' is already declared as 'Public Function 
'                     Conversion(number As Integer) As Single' in this class.
'    
'       Public ReadOnly Property Conversion As Boolean
'                                ~~~~~~~~~~
```

<span data-ttu-id="05ed1-467">個別語言包含唯一的關鍵字，因此以 Common Language Runtime 為目標的語言也必須提供一些參考符合關鍵字之識別碼 (例如類型名稱) 的機制。</span><span class="sxs-lookup"><span data-stu-id="05ed1-467">Individual languages include unique keywords, so languages that target the common language runtime must also provide some mechanism for referencing identifiers (such as type names) that coincide with keywords.</span></span> <span data-ttu-id="05ed1-468">例如，`case` 在 C# 和 Visual Basic 中都是關鍵字。</span><span class="sxs-lookup"><span data-stu-id="05ed1-468">For example, `case` is a keyword in both C# and Visual Basic.</span></span> <span data-ttu-id="05ed1-469">不過，下面 Visual Basic 範例可以使用左右大括號，讓名稱為 `case` 的類別與 `case` 關鍵字有所區分。</span><span class="sxs-lookup"><span data-stu-id="05ed1-469">However, the following Visual Basic example is able to disambiguate a class named `case` from the `case` keyword by using opening and closing braces.</span></span> <span data-ttu-id="05ed1-470">否則，這個範例會產生錯誤訊息「關鍵字做為識別項無效」，而無法編譯。</span><span class="sxs-lookup"><span data-stu-id="05ed1-470">Otherwise, the example would produce the error message, "Keyword is not valid as an identifier," and fail to compile.</span></span> 

```vb
Public Class [case]
   Private _id As Guid
   Private name As String  

   Public Sub New(name As String)
      _id = Guid.NewGuid()
      Me.name = name 
   End Sub   

   Public ReadOnly Property ClientName As String
      Get
         Return name
      End Get
   End Property
End Class
```

<span data-ttu-id="05ed1-471">下面 C# 範例可以使用 @ 符號區分識別項與語言關鍵字，以具現化 `case` 類別。</span><span class="sxs-lookup"><span data-stu-id="05ed1-471">The following C# example is able to instantiate the `case` class by using the @ symbol to disambiguate the identifier from the language keyword.</span></span> <span data-ttu-id="05ed1-472">若沒有它，C# 編譯器會顯示兩個錯誤訊息：「必須是類型」和「無效的運算式詞彙 'case'」。</span><span class="sxs-lookup"><span data-stu-id="05ed1-472">Without it, the C# compiler would display two error messages, "Type expected" and "Invalid expression term 'case'."</span></span> 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      @case c = new @case("John");
      Console.WriteLine(c.ClientName);
   }
}
```

### <a name="type-conversion"></a><span data-ttu-id="05ed1-473">類型轉換</span><span class="sxs-lookup"><span data-stu-id="05ed1-473">Type conversion</span></span>

<span data-ttu-id="05ed1-474">Common Language Specification 定義兩個轉換運算子：</span><span class="sxs-lookup"><span data-stu-id="05ed1-474">The Common Language Specification defines two conversion operators:</span></span>

* <span data-ttu-id="05ed1-475">`op_Implicit`，用於不會導致資料或精確度遺失的擴展轉換。</span><span class="sxs-lookup"><span data-stu-id="05ed1-475">`op_Implicit`, which is used for widening conversions that do not result in loss of data or precision.</span></span> <span data-ttu-id="05ed1-476">例如，[Decimal](xref:System.Decimal) 結構包含多載 `op_Implicit` 運算子，以便將整數類型的值和 [Char](xref:System.Char) 值轉換為 `Decimal` 值。</span><span class="sxs-lookup"><span data-stu-id="05ed1-476">For example, the [Decimal](xref:System.Decimal) structure includes an overloaded `op_Implicit` operator to convert values of integral types and [Char](xref:System.Char) values to `Decimal` values.</span></span> 

* <span data-ttu-id="05ed1-477">`op_Explicit`，用於可能會導致大小 (值轉換為某個範圍較小的值) 或精確度遺失的縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="05ed1-477">`op_Explicit`, which is used for narrowing conversions that can result in loss of magnitude (a value is converted to a value that has a smaller range) or precision.</span></span> <span data-ttu-id="05ed1-478">例如，`Decimal` 結構包含多載 `op_Explicit` 運算子，以便將 [Double](xref:System.Double) 和 [Single](xref:System.Single) 值轉換為 `Decimal`，以及將 `Decimal` 值轉換為整數值 `Double`、`Single` 和 `Char`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-478">For example, the `Decimal` structure includes an overloaded `op_Explicit` operator to convert [Double](xref:System.Double) and [Single](xref:System.Single) values to `Decimal` and to convert `Decimal` values to integral values, `Double`, `Single`, and `Char`.</span></span> 

<span data-ttu-id="05ed1-479">不過，並非所有語言都支援運算子多載或自訂運算子定義。</span><span class="sxs-lookup"><span data-stu-id="05ed1-479">However, not all languages support operator overloading or the definition of custom operators.</span></span> <span data-ttu-id="05ed1-480">如果您選擇實作這些轉換運算子，也應該提供執行轉換的替代方式。</span><span class="sxs-lookup"><span data-stu-id="05ed1-480">If you choose to implement these conversion operators, you should also provide an alternate way to perform the conversion.</span></span> <span data-ttu-id="05ed1-481">建議您提供 `From`Xxx 和 `To`Xxx 方法。</span><span class="sxs-lookup"><span data-stu-id="05ed1-481">We recommend that you provide `From`Xxx and `To`Xxx methods.</span></span> 

<span data-ttu-id="05ed1-482">下面範例定義了符合 CLS 標準的隱含和明確轉換。</span><span class="sxs-lookup"><span data-stu-id="05ed1-482">The following example defines CLS-compliant implicit and explicit conversions.</span></span> <span data-ttu-id="05ed1-483">它會建立 `UDouble` 類別，表示帶正負號的雙精確度浮點數。</span><span class="sxs-lookup"><span data-stu-id="05ed1-483">It creates a `UDouble` class that represents an signed double-precision, floating-point number.</span></span> <span data-ttu-id="05ed1-484">它支援從 `UDouble` 到 `Double` 的隱含轉換，以及支援從 `UDouble` 到 `Single`、`Double` 到 `UDouble` 以及 `Single` 到 `UDouble` 的明確轉換。</span><span class="sxs-lookup"><span data-stu-id="05ed1-484">It provides for implicit conversions from `UDouble` to `Double` and for explicit conversions from `UDouble` to `Single`, `Double` to `UDouble`, and `Single` to `UDouble`.</span></span> <span data-ttu-id="05ed1-485">它也會定義 `ToDouble` 方法做為隱含轉換運算子的替代方法，以及定義 `ToSingle`、`FromDouble` 和 `FromSingle` 方法做為明確轉換運算子的替代方法。</span><span class="sxs-lookup"><span data-stu-id="05ed1-485">It also defines a `ToDouble` method as an alternative to the implicit conversion operator and the `ToSingle`, `FromDouble`, and `FromSingle` methods as alternatives to the explicit conversion operators.</span></span> 

```csharp
using System;

public struct UDouble
{
   private double number;

   public UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public static readonly UDouble MinValue = (UDouble) 0.0;
   public static readonly UDouble MaxValue = (UDouble) Double.MaxValue;

   public static explicit operator Double(UDouble value)
   {
      return value.number;
   }

   public static implicit operator Single(UDouble value)
   {
      if (value.number > (double) Single.MaxValue) 
         throw new InvalidCastException("A UDouble value is out of range of the Single type.");

      return (float) value.number;         
   }

   public static explicit operator UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   } 

   public static implicit operator UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   } 

   public static Double ToDouble(UDouble value)
   {
      return (Double) value;
   }   

   public static float ToSingle(UDouble value)
   {
      return (float) value;
   }   

   public static UDouble FromDouble(double value)
   {
      return new UDouble(value);
   }

   public static UDouble FromSingle(float value)
   {
      return new UDouble(value);
   }   
}
```

```vb
Public Structure UDouble
   Private number As Double

   Public Sub New(value As Double)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Sub New(value As Single)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Shared ReadOnly MinValue As UDouble = CType(0.0, UDouble)
   Public Shared ReadOnly MaxValue As UDouble = Double.MaxValue

   Public Shared Widening Operator CType(value As UDouble) As Double
      Return value.number
   End Operator

   Public Shared Narrowing Operator CType(value As UDouble) As Single
      If value.number > CDbl(Single.MaxValue) Then
         Throw New InvalidCastException("A UDouble value is out of range of the Single type.")
      End If
      Return CSng(value.number)         
   End Operator

   Public Shared Narrowing Operator CType(value As Double) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator 

   Public Shared Narrowing Operator CType(value As Single) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator 

   Public Shared Function ToDouble(value As UDouble) As Double
      Return CType(value, Double)
   End Function   

   Public Shared Function ToSingle(value As UDouble) As Single
      Return CType(value, Single)
   End Function   

   Public Shared Function FromDouble(value As Double) As UDouble
      Return New UDouble(value)
   End Function

   Public Shared Function FromSingle(value As Single) As UDouble
      Return New UDouble(value)
   End Function   
End Structure
```

### <a name="arrays"></a><span data-ttu-id="05ed1-486">陣列</span><span class="sxs-lookup"><span data-stu-id="05ed1-486">Arrays</span></span>

<span data-ttu-id="05ed1-487">符合 CLS 標準的陣列會遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="05ed1-487">CLS-compliant arrays conform to the following rules:</span></span> 

* <span data-ttu-id="05ed1-488">陣列所有維度的下限都必須為零。</span><span class="sxs-lookup"><span data-stu-id="05ed1-488">All dimensions of an array must have a lower bound of zero.</span></span> <span data-ttu-id="05ed1-489">下面範例會建立下限為一、不符合 CLS 標準的陣列。</span><span class="sxs-lookup"><span data-stu-id="05ed1-489">The following example creates a non-CLS-compliant array with a lower bound of one.</span></span> <span data-ttu-id="05ed1-490">請注意，儘管 [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 屬性存在，編譯器並不會偵測出 `Numbers.GetTenPrimes` 方法傳回的陣列不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-490">Note that, despite the presence of the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute, the compiler does not detect that the array returned by the `Numbers.GetTenPrimes` method is not CLS-compliant.</span></span> 

  ```csharp
  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static Array GetTenPrimes()
    {
        Array arr = Array.CreateInstance(typeof(Int32), new int[] {10}, new int[] {1});
        arr.SetValue(1, 1);
        arr.SetValue(2, 2);
        arr.SetValue(3, 3);
        arr.SetValue(5, 4);
        arr.SetValue(7, 5);
        arr.SetValue(11, 6); 
        arr.SetValue(13, 7);
        arr.SetValue(17, 8);
        arr.SetValue(19, 9);
        arr.SetValue(23, 10);

        return arr; 
    }
  }
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As Array
        Dim arr As Array = Array.CreateInstance(GetType(Int32), {10}, {1})
        arr.SetValue(1, 1)
        arr.SetValue(2, 2)
        arr.SetValue(3, 3)
        arr.SetValue(5, 4)
        arr.SetValue(7, 5)
        arr.SetValue(11, 6)
        arr.SetValue(13, 7)
        arr.SetValue(17, 8)
        arr.SetValue(19, 9)
        arr.SetValue(23, 10)
        Return arr
     End Function
  End Class
  ```

* <span data-ttu-id="05ed1-491">所有陣列項目都必須包含符合 CLS 標準的類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-491">All array elements must consist of CLS-compliant types.</span></span> <span data-ttu-id="05ed1-492">下面範例會定義傳回不符合 CLS 標準的陣列的兩個方法。</span><span class="sxs-lookup"><span data-stu-id="05ed1-492">The following example defines two methods that return non-CLS-compliant arrays.</span></span> <span data-ttu-id="05ed1-493">第一個會傳回 [UInt32](xref:System.UInt32) 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="05ed1-493">The first returns an array of [UInt32](xref:System.UInt32) values.</span></span> <span data-ttu-id="05ed1-494">第二個傳回包含 [Int32](xref:System.Int32) 和 `UInt32` 值的 [Object](xref:System.Object) 陣列。</span><span class="sxs-lookup"><span data-stu-id="05ed1-494">The second returns an [Object](xref:System.Object) array that includes [Int32](xref:System.Int32) and `UInt32` values.</span></span> <span data-ttu-id="05ed1-495">雖然編譯器會因為其 `UInt32` 類型而將第一個陣列識別為不符合標準，但是無法辨識出第二個陣列包含了不符合 CLS 標準的項目。</span><span class="sxs-lookup"><span data-stu-id="05ed1-495">Although the compiler identifies the first array as non-compliant because of its `UInt32` type, it fails to recognize that the second array includes non-CLS-compliant elements.</span></span> 

  ```csharp
  using System;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static UInt32[] GetTenPrimes()
    {
        uint[] arr = { 1u, 2u, 3u, 5u, 7u, 11u, 13u, 17u, 19u };
        return arr;
    }

    public static Object[] GetFivePrimes()
    {
        Object[] arr = { 1, 2, 3, 5u, 7u };
        return arr;
    }
  }
  // Compilation produces a compiler warning like the following:
  //    Array2.cs(8,27): warning CS3002: Return type of 'Numbers.GetTenPrimes()' is not
  //            CLS-compliant
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As UInt32()
        Return { 1ui, 2ui, 3ui, 5ui, 7ui, 11ui, 13ui, 17ui, 19ui }
     End Function
     Public Shared Function GetFivePrimes() As Object()
        Dim arr() As Object = { 1, 2, 3, 5ui, 7ui }
        Return arr
     End Function
  End Class
  ' Compilation produces a compiler warning like the following:
  '    warning BC40027: Return type of function 'GetTenPrimes' is not CLS-compliant.
  ```                             

* <span data-ttu-id="05ed1-496">具有陣列參數之方法的多載解析是根據它們是陣列和其項目類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-496">Overload resolution for methods that have array parameters is based on the fact that they are arrays and on their element type.</span></span> <span data-ttu-id="05ed1-497">因此，下面多載 `GetSquares` 方法的定義符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-497">For this reason, the following definition of an overloaded `GetSquares` method is CLS-compliant.</span></span> 

  ```csharp
  using System;
  using System.Numerics;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static byte[] GetSquares(byte[] numbers)
    {
        byte[] numbersOut = new byte[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++) {
            int square = ((int) numbers[ctr]) * ((int) numbers[ctr]); 
            if (square <= Byte.MaxValue)
                numbersOut[ctr] = (byte) square;
            // If there's an overflow, assign MaxValue to the corresponding 
            // element.
            else
                numbersOut[ctr] = Byte.MaxValue;

        }
        return numbersOut;
    }

    public static BigInteger[] GetSquares(BigInteger[] numbers)
  {
        BigInteger[] numbersOut = new BigInteger[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++)
            numbersOut[ctr] = numbers[ctr] * numbers[ctr]; 

       return numbersOut;
    }
  }
  ```

  ```vb
  Imports System.Numerics

  <Assembly: CLSCompliant(True)>

  Public Module Numbers
     Public Function GetSquares(numbers As Byte()) As Byte()
        Dim numbersOut(numbers.Length - 1) As Byte
        For ctr As Integer = 0 To numbers.Length - 1
           Dim square As Integer = (CInt(numbers(ctr)) * CInt(numbers(ctr))) 
           If square <= Byte.MaxValue Then
              numbersOut(ctr) = CByte(square)
           ' If there's an overflow, assign MaxValue to the corresponding 
           ' element.
           Else
              numbersOut(ctr) = Byte.MaxValue
           End If   
        Next
        Return numbersOut
     End Function

     Public Function GetSquares(numbers As BigInteger()) As BigInteger()
         Dim numbersOut(numbers.Length - 1) As BigInteger
         For ctr As Integer = 0 To numbers.Length - 1
            numbersOut(ctr) = numbers(ctr) * numbers(ctr) 
         Next
         Return numbersOut
     End Function
  End Module
  ```

### <a name="interfaces"></a><span data-ttu-id="05ed1-498">介面</span><span class="sxs-lookup"><span data-stu-id="05ed1-498">Interfaces</span></span>

<span data-ttu-id="05ed1-499">符合 CLS 標準的介面可以定義屬性、事件和虛擬方法 (沒有實作的方法)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-499">CLS-compliant interfaces can define properties, events, and virtual methods (methods with no implementation).</span></span> <span data-ttu-id="05ed1-500">符合 CLS 標準的介面不可含有下列任何一項：</span><span class="sxs-lookup"><span data-stu-id="05ed1-500">A CLS-compliant interface cannot have any of the following:</span></span> 

* <span data-ttu-id="05ed1-501">靜態方法或靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="05ed1-501">Static methods or static fields.</span></span> <span data-ttu-id="05ed1-502">如果您在介面中定義了靜態成員，C# 編譯器會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="05ed1-502">The C# compiler generatse compiler errors if you define a static member in an interface.</span></span> 

* <span data-ttu-id="05ed1-503">欄位。</span><span class="sxs-lookup"><span data-stu-id="05ed1-503">Fields.</span></span> <span data-ttu-id="05ed1-504">如果您在介面中定義了欄位，C# 編譯器會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="05ed1-504">The C# acompiler generates compiler errors if you define a field in an interface.</span></span>

* <span data-ttu-id="05ed1-505">不符合 CLS 標準的方法。</span><span class="sxs-lookup"><span data-stu-id="05ed1-505">Methods that are not CLS-compliant.</span></span> <span data-ttu-id="05ed1-506">例如，下面介面定義包含標記為符合 CLS 標準的方法 `INumber.GetUnsigned`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-506">For example, the following interface definition includes a method, `INumber.GetUnsigned`, that is marked as non-CLS-compliant.</span></span> <span data-ttu-id="05ed1-507">這個範例會產生編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="05ed1-507">This example generates a compiler warning.</span></span> 

  ```csharp
  using System;

  [assembly:CLSCompliant(true)]

  public interface INumber
  {
      int Length();
      [CLSCompliant(false)] ulong GetUnsigned();
  }
  // Attempting to compile the example displays output like the following:
  //    Interface2.cs(8,32): warning CS3010: 'INumber.GetUnsigned()': CLS-compliant interfaces
  //            must have only CLS-compliant members
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Interface INumber
    Function Length As Integer
      <CLSCompliant(False)> Function GetUnsigned As ULong   
    End Interface
    ' Attempting to compile the example displays output like the following:
    '    Interface2.vb(9) : warning BC40033: Non CLS-compliant 'function' is not allowed in a 
    '    CLS-compliant interface.
    '    
    '       <CLSCompliant(False)> Function GetUnsigned As ULong
    '                                      ~~~~~~~~~~~
  ```

  <span data-ttu-id="05ed1-508">由於這項規則，在實作不符合 CLS 標準的成員時並不需要符合 CLS 標準的類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-508">Because of this rule, CLS-compliant types are not required to implement non-CLS-compliant members.</span></span> <span data-ttu-id="05ed1-509">如果符合 CLS 標準的架構沒有公開實作不符合 CLS 標準介面的類別，也應該提供所有不符合 CLS 標準成員的具象實作。</span><span class="sxs-lookup"><span data-stu-id="05ed1-509">If a CLS-compliant framework does expose a class that implements a non-CLS compliant interface, it should also provide concrete implementations of all non-CLS-compliant members.</span></span> 

<span data-ttu-id="05ed1-510">符合 CLS 標準的語言編譯器也必須允許類別提供在多個介面中具有相同名稱及簽章的成員實作。</span><span class="sxs-lookup"><span data-stu-id="05ed1-510">CLS-compliant language compilers must also allow a class to provide separate implementations of members that have the same name and signature in multiple interfaces.</span></span> <span data-ttu-id="05ed1-511">C# 支援明確介面實作，以提供相同具名方法的不同實作。</span><span class="sxs-lookup"><span data-stu-id="05ed1-511">C# supports explicit interface implementations to provide different implementations of identically named methods.</span></span> <span data-ttu-id="05ed1-512">下面範例會透過定義實作 `Temperature` 和 `ICelsius` 介面做為明確介面實作的 `IFahrenheit` 類別，來說明這種情況。</span><span class="sxs-lookup"><span data-stu-id="05ed1-512">The following example illustrates this scenario by defining a `Temperature` class that implements the `ICelsius` and `IFahrenheit` interfaces as explicit interface implementations.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

public interface IFahrenheit
{
   decimal GetTemperature();
}

public interface ICelsius
{
   decimal GetTemperature();
}

public class Temperature : ICelsius, IFahrenheit
{
   private decimal _value;

   public Temperature(decimal value)
   {
      // We assume that this is the Celsius value.
      _value = value;
   } 

   decimal IFahrenheit.GetTemperature()
   {
      return _value * 9 / 5 + 32;
   }

   decimal ICelsius.GetTemperature()
   {
      return _value;
   } 
}
public class Example
{
   public static void Main()
   {
      Temperature temp = new Temperature(100.0m);
      ICelsius cTemp = temp;
      IFahrenheit fTemp = temp;
      Console.WriteLine("Temperature in Celsius: {0} degrees", 
                        cTemp.GetTemperature());
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees", 
                        fTemp.GetTemperature());
   }
}
// The example displays the following output:
//       Temperature in Celsius: 100.0 degrees
//       Temperature in Fahrenheit: 212.0 degrees
```

```vb
Assembly: CLSCompliant(True)>

Public Interface IFahrenheit
   Function GetTemperature() As Decimal
End Interface

Public Interface ICelsius
   Function GetTemperature() As Decimal
End Interface

Public Class Temperature : Implements ICelsius, IFahrenheit
   Private _value As Decimal

   Public Sub New(value As Decimal)
      ' We assume that this is the Celsius value.
      _value = value
   End Sub 

   Public Function GetFahrenheit() As Decimal _
          Implements IFahrenheit.GetTemperature
      Return _value * 9 / 5 + 32
   End Function

   Public Function GetCelsius() As Decimal _
          Implements ICelsius.GetTemperature
      Return _value
   End Function 
End Class

Module Example
   Public Sub Main()
      Dim temp As New Temperature(100.0d)
      Console.WriteLine("Temperature in Celsius: {0} degrees", 
                        temp.GetCelsius())
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees", 
                        temp.GetFahrenheit())
   End Sub
End Module
' The example displays the following output:
'       Temperature in Celsius: 100.0 degrees
'       Temperature in Fahrenheit: 212.0 degrees
```

### <a name="enumerations"></a><span data-ttu-id="05ed1-513">列舉</span><span class="sxs-lookup"><span data-stu-id="05ed1-513">Enumerations</span></span>

<span data-ttu-id="05ed1-514">符合 CLS 標準的列舉必須遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="05ed1-514">CLS-compliant enumerations must follow these rules:</span></span> 

* <span data-ttu-id="05ed1-515">列舉的基礎類型必須是內建符合 CLS 標準的整數 ([Byte](xref:System.Byte)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32) 或 [Int64](xref:System.Int64))。</span><span class="sxs-lookup"><span data-stu-id="05ed1-515">The underlying type of the enumeration must be an intrinsic CLS-compliant integer ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), or [Int64](xref:System.Int64)).</span></span> <span data-ttu-id="05ed1-516">例如，下面程式碼會嘗試定義其基礎類型為 [UInt32](xref:System.UInt32) 的列舉，並產生編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="05ed1-516">For example, the following code tries to define an enumeration whose underlying type is [UInt32](xref:System.UInt32) and generates a compiler warning.</span></span> 

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public enum Size : uint { 
        Unspecified = 0, 
        XSmall = 1, 
        Small = 2, 
        Medium = 3, 
        Large = 4, 
        XLarge = 5 
    };

    public class Clothing
    {
        public string Name; 
        public string Type;
        public string Size;
    }
    // The attempt to compile the example displays a compiler warning like the following:
    //    Enum3.cs(6,13): warning CS3009: 'Size': base type 'uint' is not CLS-compliant
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Enum Size As UInt32
       Unspecified = 0
       XSmall = 1
       Small = 2
       Medium = 3
       Large = 4
       XLarge = 5
    End Enum

    Public Class Clothing
       Public Name As String
       Public Type As String
       Public Size As Size
    End Class
    ' The attempt to compile the example displays a compiler warning like the following:
    '    Enum3.vb(6) : warning BC40032: Underlying type 'UInt32' of Enum is not CLS-compliant.
    '    
    '    Public Enum Size As UInt32
    '                ~~~~
    ```

* <span data-ttu-id="05ed1-517">列舉類型必須具有以 `Value__` 屬性標記的單一執行個體欄位，名稱為 `FieldAttributes.RTSpecialName`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-517">An enumeration type must have a single instance field named `Value__` that is marked with the `FieldAttributes.RTSpecialName` attribute.</span></span> <span data-ttu-id="05ed1-518">這可讓您隱含參考欄位值。</span><span class="sxs-lookup"><span data-stu-id="05ed1-518">This enables you to reference the field value implicitly.</span></span> 

* <span data-ttu-id="05ed1-519">列舉會包含其類型符合列舉本身類型的常值靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="05ed1-519">An enumeration includes literal static fields whose types match the type of the enumeration itself.</span></span> <span data-ttu-id="05ed1-520">例如，如果您定義含有 `State` 和 `State.On` 值的 `State.Off` 列舉，則 `State.On` 和 `State.Off` 都是常值靜態欄位，其類型為 `State`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-520">For example, if you define a `State` enumeration with values of `State.On` and `State.Off`, `State.On` and `State.Off` are both literal static fields whose type is `State`.</span></span> 

* <span data-ttu-id="05ed1-521">列舉有兩種：</span><span class="sxs-lookup"><span data-stu-id="05ed1-521">There are two kinds of enumerations:</span></span> 
    
    * <span data-ttu-id="05ed1-522">表示一組互斥具名整數值的列舉。</span><span class="sxs-lookup"><span data-stu-id="05ed1-522">An enumeration that represents a set of mutually exclusive, named integer values.</span></span> <span data-ttu-id="05ed1-523">這個列舉類型是由缺少 [System.FlagsAttribute](xref:System.FlagsAttribute) 自訂屬性來表示。</span><span class="sxs-lookup"><span data-stu-id="05ed1-523">This type of enumeration is indicated by the absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>
    
    * <span data-ttu-id="05ed1-524">表示一組可合併產生未命名值之位元旗標的列舉。</span><span class="sxs-lookup"><span data-stu-id="05ed1-524">An enumeration that represents a set of bit flags that can combine to generate an unnamed value.</span></span> <span data-ttu-id="05ed1-525">這個列舉類型是由存在 [System.FlagsAttribute](xref:System.FlagsAttribute) 自訂屬性來表示。</span><span class="sxs-lookup"><span data-stu-id="05ed1-525">This type of enumeration is indicated by the presence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>
    
 <span data-ttu-id="05ed1-526">如需詳細資訊，請參閱 [Enum](xref:System.Enum) 結構的說明文件。</span><span class="sxs-lookup"><span data-stu-id="05ed1-526">For more information, see the documentation for the [Enum](xref:System.Enum) structure.</span></span> 

* <span data-ttu-id="05ed1-527">列舉的值不限於其指定值的範圍。</span><span class="sxs-lookup"><span data-stu-id="05ed1-527">The value of an enumeration is not limited to the range of its specified values.</span></span> <span data-ttu-id="05ed1-528">換句話說，列舉中的值範圍即是其基礎值的範圍。</span><span class="sxs-lookup"><span data-stu-id="05ed1-528">In other words, the range of values in an enumeration is the range of its underlying value.</span></span> <span data-ttu-id="05ed1-529">您可以使用 `Enum.IsDefined` 方法來判斷某指定值是否為列舉的成員。</span><span class="sxs-lookup"><span data-stu-id="05ed1-529">You can use the `Enum.IsDefined` method to determine whether a specified value is a member of an enumeration.</span></span> 

### <a name="type-members-in-general"></a><span data-ttu-id="05ed1-530">一般類型成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-530">Type members in general</span></span>

<span data-ttu-id="05ed1-531">Common Language Specification 要求所有欄位和方法都必須當做特定類別的成員來加以存取。</span><span class="sxs-lookup"><span data-stu-id="05ed1-531">The Common Language Specification requires all fields and methods to be accessed as members of a particular class.</span></span> <span data-ttu-id="05ed1-532">因此，全域靜態欄位和方法 (也就是除了類型外定義的靜態欄位或方法) 不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-532">Therefore, global static fields and methods (that is, static fields or methods that are defined apart from a type) are not CLS-compliant.</span></span> <span data-ttu-id="05ed1-533">如果您嘗試在原始程式碼中包含全域欄位或方法，則 C# 編譯器會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="05ed1-533">If you try to include a global field or method in your source code, the C# compiler generates a compiler error.</span></span> 

<span data-ttu-id="05ed1-534">Common Language Specification 只支援標準的 Managed 呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="05ed1-534">The Common Language Specification supports only the standard managed calling convention.</span></span> <span data-ttu-id="05ed1-535">它不支援 Unmanaged 呼叫慣例和具有變數引數清單 (以 `varargs` 關鍵字標記) 的方法。</span><span class="sxs-lookup"><span data-stu-id="05ed1-535">It doesn't support unmanaged calling conventions and methods with variable argument lists marked with the `varargs` keyword.</span></span> <span data-ttu-id="05ed1-536">如果是與標準 Managed 呼叫慣例相容的變數引數清單，請使用 [ParamArrayAttribute](xref:System.ParamArrayAttribute) 屬性或個別語言的實作，例如 C# 中的 `params` 關鍵字或 Visual Basic 中的 `ParamArray` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="05ed1-536">For variable argument lists that are compatible with the standard managed calling convention, use the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute or the individual language's implementation, such as the `params` keyword in C# and the `ParamArray` keyword in Visual Basic.</span></span> 

### <a name="member-accessibility"></a><span data-ttu-id="05ed1-537">成員存取範圍</span><span class="sxs-lookup"><span data-stu-id="05ed1-537">Member accessibility</span></span>

<span data-ttu-id="05ed1-538">覆寫繼承的成員無法變更該成員的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="05ed1-538">Overriding an inherited member cannot change the accessibility of that member.</span></span> <span data-ttu-id="05ed1-539">例如，衍生類別中的私用方法無法覆寫基底類別中的公用方法。</span><span class="sxs-lookup"><span data-stu-id="05ed1-539">For example, a public method in a base class cannot be overridden by a private method in a derived class.</span></span> <span data-ttu-id="05ed1-540">有一個例外：由不同組件中的類型所覆寫的某個組件中的 `protected internal` (在 C# 中) 或 `Protected Friend` (在 Visual Basic 中) 成員。</span><span class="sxs-lookup"><span data-stu-id="05ed1-540">There is one exception: a `protected internal` (in C#) or `Protected Friend` (in Visual Basic) member in one assembly that is overridden by a type in a different assembly.</span></span>  <span data-ttu-id="05ed1-541">在這種情況下，覆寫的存取範圍是 `Protected`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-541">In that case, the accessibility of the override is `Protected`.</span></span> 

<span data-ttu-id="05ed1-542">下面範例說明當 [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 屬性是設定為 `true`，並且 `Person` (衍生自 `Animal` 的類別) 嘗試將 `Species` 屬性的存取範圍從 public (公用) 變更為 private (私用) 時，所產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="05ed1-542">The following example illustrates the error that is generated when the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is set to `true`, and `Person`, which is a class derived from `Animal`, tries to change the accessibility of the `Species` property from public to private.</span></span> <span data-ttu-id="05ed1-543">如果它的存取範圍變更為 public (公用)，則此範例會編譯成功。</span><span class="sxs-lookup"><span data-stu-id="05ed1-543">The example compiles successfully if its accessibility is changed to public.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Animal
{
   private string _species;

   public Animal(string species)
   {
      _species = species;
   }

   public virtual string Species 
   {    
      get { return _species; }
   }

   public override string ToString()
   {
      return _species;   
   } 
}

public class Human : Animal
{
   private string _name;

   public Human(string name) : base("Homo Sapiens")
   {
      _name = name;
   }

   public string Name
   {
      get { return _name; }
   }

   private override string Species 
   {
      get { return base.Species; }
   }

   public override string ToString() 
   {
      return _name;
   }
}

public class Example
{
   public static void Main()
   {
      Human p = new Human("John");
      Console.WriteLine(p.Species);
      Console.WriteLine(p.ToString());
   }
}
// The example displays the following output:
//    error CS0621: 'Human.Species': virtual or abstract members cannot be private
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Animal
   Private _species As String

   Public Sub New(species As String)
      _species = species
   End Sub

   Public Overridable ReadOnly Property Species As String
      Get
         Return _species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _species   
   End Function 
End Class

Public Class Human : Inherits Animal
   Private _name As String

   Public Sub New(name As String)
      MyBase.New("Homo Sapiens")
      _name = name
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return _name
      End Get
   End Property

   Private Overrides ReadOnly Property Species As String
      Get
         Return MyBase.Species
      End Get   
   End Property

   Public Overrides Function ToString() As String
      Return _name
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim p As New Human("John")
      Console.WriteLine(p.Species)
      Console.WriteLine(p.ToString())
   End Sub
End Module
' The example displays the following output:
'     'Private Overrides ReadOnly Property Species As String' cannot override 
'     'Public Overridable ReadOnly Property Species As String' because
'      they have different access levels.
' 
'         Private Overrides ReadOnly Property Species As String
```

<span data-ttu-id="05ed1-544">每當成員本身為可存取時，成員簽章中的類型也必須是可存取的。</span><span class="sxs-lookup"><span data-stu-id="05ed1-544">Types in the signature of a member must be accessible whenever that member is accessible.</span></span> <span data-ttu-id="05ed1-545">例如，這表示 public 成員不能包含類型為 private、protected 或 internal 的參數。</span><span class="sxs-lookup"><span data-stu-id="05ed1-545">For example, this means that a public member cannot include a parameter whose type is private, protected, or internal.</span></span> <span data-ttu-id="05ed1-546">下面範例說明當 `StringWrapper` 類別建構函式公開內部 `StringOperationType` 列舉值，決定如何包裝字串值時，所產生的編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="05ed1-546">The following example illustrates the compiler error that results when a `StringWrapper` class constructor exposes an internal `StringOperationType` enumeration value that determines how a string value should be wrapped.</span></span> 

```csharp
using System;
using System.Text;

public class StringWrapper
{
   string internalString;
   StringBuilder internalSB = null;
   bool useSB = false;

   public StringWrapper(StringOperationType type)
   {   
      if (type == StringOperationType.Normal) {
         useSB = false;
      }   
      else {
         useSB = true;
         internalSB = new StringBuilder();
      }    
   }

   // The remaining source code...
}

internal enum StringOperationType { Normal, Dynamic }
// The attempt to compile the example displays the following output:
//    error CS0051: Inconsistent accessibility: parameter type
//            'StringOperationType' is less accessible than method
//            'StringWrapper.StringWrapper(StringOperationType)'
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class StringWrapper

   Dim internalString As String
   Dim internalSB As StringBuilder = Nothing
   Dim useSB As Boolean = False

   Public Sub New(type As StringOperationType)   
      If type = StringOperationType.Normal Then
         useSB = False
      Else
         internalSB = New StringBuilder() 
         useSB = True
      End If    
   End Sub

   ' The remaining source code...
End Class

Friend Enum StringOperationType As Integer
   Normal = 0
   Dynamic = 1
End Enum
' The attempt to compile the example displays the following output:
'    error BC30909: 'type' cannot expose type 'StringOperationType'
'     outside the project through class 'StringWrapper'.
'    
'       Public Sub New(type As StringOperationType)
'                              ~~~~~~~~~~~~~~~~~~~
```

### <a name="generic-types-and-members"></a><span data-ttu-id="05ed1-547">泛型類型和成員</span><span class="sxs-lookup"><span data-stu-id="05ed1-547">Generic types and members</span></span>

<span data-ttu-id="05ed1-548">巢狀類型一律至少具有與其封入類型 (Enclosing Type) 一樣多的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="05ed1-548">Nested types always have at least as many generic parameters as their enclosing type.</span></span> <span data-ttu-id="05ed1-549">這些在位置上對應於封入類型中的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="05ed1-549">These correspond by position to the generic parameters in the enclosing type.</span></span> <span data-ttu-id="05ed1-550">泛型類型也可以包含新的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="05ed1-550">The generic type can also include new generic parameters.</span></span> 

<span data-ttu-id="05ed1-551">個別語言的語法可能會隱藏包含類型和其巢狀類型的泛型類型參數之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="05ed1-551">The relationship between the generic type parameters of a containing type and its nested types may be hidden by the syntax of individual languages.</span></span> <span data-ttu-id="05ed1-552">在下面範例中，泛型類型 `Outer<T>` 包含兩個巢狀類別：`Inner1A` 和 `Inner1B<U>`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-552">In the following example, a generic type `Outer<T>` contains two nested classes, `Inner1A` and `Inner1B<U>`.</span></span> <span data-ttu-id="05ed1-553">對 `ToString` 方法 (每個類別都是從 `Object.ToString` 繼承這個方法) 的呼叫，顯示出每個巢狀類別都會包含其所包含類別的型別參數。</span><span class="sxs-lookup"><span data-stu-id="05ed1-553">The calls to the `ToString` method, which each class inherits from `Object.ToString`, show that each nested class includes the type parameters of its containing class.</span></span> 

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Outer<T>
{
   T value;

   public Outer(T value)
   {
      this.value = value;
   }

   public class Inner1A : Outer<T>
   {
      public Inner1A(T value) : base(value)
      {  }
   }

   public class Inner1B<U> : Outer<T>
   {
      U value2;

      public Inner1B(T value1, U value2) : base(value1)
      {
         this.value2 = value2;
      }
   }
}

public class Example
{
   public static void Main()
   {
      var inst1 = new Outer<String>("This");
      Console.WriteLine(inst1);

      var inst2 = new Outer<String>.Inner1A("Another");
      Console.WriteLine(inst2);

      var inst3 = new Outer<String>.Inner1B<int>("That", 2);
      Console.WriteLine(inst3);
   }
}
// The example displays the following output:
//       Outer`1[System.String]
//       Outer`1+Inner1A[System.String]
//       Outer`1+Inner1B`1[System.String,System.Int32]
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Outer(Of T)
   Dim value As T

   Public Sub New(value As T)
      Me.value = value
   End Sub

   Public Class Inner1A : Inherits Outer(Of T)
      Public Sub New(value As T)
         MyBase.New(value)
      End Sub
   End Class

   Public Class Inner1B(Of U) : Inherits Outer(Of T)
      Dim value2 As U

      Public Sub New(value1 As T, value2 As U)
         MyBase.New(value1)
         Me.value2 = value2
      End Sub
   End Class
End Class

Public Module Example
   Public Sub Main()
      Dim inst1 As New Outer(Of String)("This")
      Console.WriteLine(inst1)

      Dim inst2 As New Outer(Of String).Inner1A("Another")
      Console.WriteLine(inst2)

      Dim inst3 As New Outer(Of String).Inner1B(Of Integer)("That", 2)
      Console.WriteLine(inst3)
   End Sub
End Module
' The example displays the following output:
'       Outer`1[System.String]
'       Outer`1+Inner1A[System.String]
'       Outer`1+Inner1B`1[System.String,System.Int32]
```

<span data-ttu-id="05ed1-554">泛型型別名稱的編碼格式為 *name*'*n*，其中 *name* 是類型名稱，*\`* 是字元常值，而 *n* 則是在類型上宣告的參數數目，或是巢狀泛型型別中，新引入之型別參數的數目。</span><span class="sxs-lookup"><span data-stu-id="05ed1-554">Generic type names are encoded in the form *name*'*n*, where *name* is the type name, *\`* is a character literal, and *n* is the number of parameters declared on the type, or, for nested generic types, the number of newly introduced type parameters.</span></span> <span data-ttu-id="05ed1-555">這個泛型類型名稱編碼方式主要適用於使用反映來存取程式庫中符合 CLS 標準之泛型類型的開發人員。</span><span class="sxs-lookup"><span data-stu-id="05ed1-555">This encoding of generic type names is primarily of interest to developers who use reflection to access CLS-complaint generic types in a library.</span></span> 

<span data-ttu-id="05ed1-556">如果限制式是套用至泛型類型，則任何當做限制式使用的類型也必須符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-556">If constraints are applied to a generic type, any types used as constraints must also be CLS-compliant.</span></span> <span data-ttu-id="05ed1-557">下面範例定義了不符合 CLS 標準的類別 (名稱為 `BaseClass`) 以及類型參數必須衍生自 `BaseCollection` 的泛型類別 (名稱為 `BaseClass`)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-557">The following example defines a class named `BaseClass` that is not CLS-compliant and a generic class named `BaseCollection` whose type parameter must derive from `BaseClass`.</span></span> <span data-ttu-id="05ed1-558">但是因為 `BaseClass` 不符合 CLS 標準，所以編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="05ed1-558">But because `BaseClass` is not CLS-compliant, the compiler emits a warning.</span></span> 

```csharp
using System;

[assembly:CLSCompliant(true)]

[CLSCompliant(false)] public class BaseClass
{}


public class BaseCollection<T> where T : BaseClass
{}
// Attempting to compile the example displays the following output:
//    warning CS3024: Constraint type 'BaseClass' is not CLS-compliant
```

```vb
Assembly: CLSCompliant(True)>

<CLSCompliant(False)> Public Class BaseClass
End Class


Public Class BaseCollection(Of T As BaseClass)
End Class
' Attempting to compile the example displays the following output:
'    warning BC40040: Generic parameter constraint type 'BaseClass' is not 
'    CLS-compliant.
'    
'    Public Class BaseCollection(Of T As BaseClass)
'                                        ~~~~~~~~~
```

<span data-ttu-id="05ed1-559">如果泛型類型是衍生自泛型基底類型，就必須重新宣告任何限制式，才能保證同時符合基底類型上的限制式。</span><span class="sxs-lookup"><span data-stu-id="05ed1-559">If a generic type is derived from a generic base type, it must redeclare any constraints so that it can guarantee that constraints on the base type are also satisfied.</span></span> <span data-ttu-id="05ed1-560">下面範例會定義可代表任何數字類型的 `Number<T>`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-560">The following example defines a `Number<T>` that can represent any numeric type.</span></span> <span data-ttu-id="05ed1-561">它也會定義表示浮點值的 `FloatingPoint<T>` 類別。</span><span class="sxs-lookup"><span data-stu-id="05ed1-561">It also defines a `FloatingPoint<T>` class that represents a floating point value.</span></span> <span data-ttu-id="05ed1-562">不過，因為未將 `Number<T>` (其中 T 必須是實值類型) 的限制式套用至 `FloatingPoint<T>`，所以無法編譯原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="05ed1-562">However, the source code fails to compile, because it does not apply the constraint on `Number<T>` (that T must be a value type) to `FloatingPoint<T>`.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }  
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T> 
{
   public FloatingPoint(T number) : base(number) 
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() || 
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else   
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }       
}           
// The attempt to comple the example displays the following output:
//       error CS0453: The type 'T' must be a non-nullable value type in
//               order to use it as parameter 'T' in the generic type or method 'Number<T>'
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T) : Inherits Number(Of T) 
   Public Sub New(number As T)
      MyBase.New(number) 
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then 
         Me.number = Convert.ToDouble(number)
      Else   
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If   
   End Sub       
End Class           
' The attempt to comple the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'    
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

<span data-ttu-id="05ed1-563">如果將該條件約束加入至 `FloatingPoint<T>` 類別，則這個範例會編譯成功。</span><span class="sxs-lookup"><span data-stu-id="05ed1-563">The example compiles successfully if the constraint is added to the `FloatingPoint<T>` class.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]


public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }  
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T> where T : struct 
{
   public FloatingPoint(T number) : base(number) 
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() || 
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else   
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }       
}      
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T As Structure) : Inherits Number(Of T) 
   Public Sub New(number As T)
      MyBase.New(number) 
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then 
         Me.number = Convert.ToDouble(number)
      Else   
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If   
   End Sub       
End Class
```

<span data-ttu-id="05ed1-564">Common Language Specification 會對巢狀類型和保護的成員施加保守的每一個具現化模型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-564">The Common Language Specification imposes a conservative per-instantiation model for nested types and protected members.</span></span> <span data-ttu-id="05ed1-565">開放式泛型類型無法公開其簽章包含受保護巢狀泛型類型的特定具現化的欄位或成員。</span><span class="sxs-lookup"><span data-stu-id="05ed1-565">Open generic types cannot expose fields or members with signatures that contain a specific instantiation of a nested, protected generic type.</span></span> <span data-ttu-id="05ed1-566">可擴充泛型基底類別或介面之特定具現化的非泛型類型，無法公開其簽章包含受保護巢狀泛型類型的不同具現化的欄位或成員。</span><span class="sxs-lookup"><span data-stu-id="05ed1-566">Non-generic types that extend a specific instantiation of a generic base class or interface cannot expose fields or members with signatures that contain a different instantiation of a nested, protected generic type.</span></span>

<span data-ttu-id="05ed1-567">下列範例會定義泛型型別 `C1<T>` 和受保護的類別 `C1<T>.N`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-567">The following example defines a generic type, `C1<T>`, and a protected class, `C1<T>.N`.</span></span> <span data-ttu-id="05ed1-568">`C1<T>` 有兩個方法：`M1` 和 `M2`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-568">`C1<T>` has two methods, `M1` and `M2`.</span></span> <span data-ttu-id="05ed1-569">不過，`M1` 不符合 CLS 標準，因為它會嘗試從 `C1<T>` 傳回 `C1<int>.N` 物件。</span><span class="sxs-lookup"><span data-stu-id="05ed1-569">However, `M1` is not CLS-compliant because it tries to return a `C1<int>.N` object from `C1<T>`.</span></span> <span data-ttu-id="05ed1-570">第二個類別 `C2` 是衍生自 `C1<long>`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-570">A second class, `C2`, is derived from `C1<long>`.</span></span> <span data-ttu-id="05ed1-571">它具有兩個方法：`M3` 和 `M4`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-571">It has two methods, `M3` and `M4`.</span></span> <span data-ttu-id="05ed1-572">因為 `M3` 會嘗試傳回 `C1<long>` 的 `C1<int>.N` 物件，所以不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-572">`M3` is not CLS-compliant because it tries to return a `C1<int>.N` object from a subclass of `C1<long>`.</span></span> <span data-ttu-id="05ed1-573">請注意，語言編譯器的限制可能還要更嚴格。</span><span class="sxs-lookup"><span data-stu-id="05ed1-573">Note that language compilers can be even more restrictive.</span></span> <span data-ttu-id="05ed1-574">在此範例中，Visual Basic 會在其嘗試編譯 `M4` 時顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="05ed1-574">In this example, Visual Basic displays an error when it tries to compile `M4`.</span></span> 

```csharp
using System;

[assembly:CLSCompliant(true)]

public class C1<T> 
{
   protected class N { }

   protected void M1(C1<int>.N n) { } // Not CLS-compliant - C1<int>.N not
                                      // accessible from within C1<T> in all
                                      // languages
   protected void M2(C1<T>.N n) { }   // CLS-compliant – C1<T>.N accessible
                                      // inside C1<T>
}

public class C2 : C1<long> 
{
   protected void M3(C1<int>.N n) { }  // Not CLS-compliant – C1<int>.N is not
                                       // accessible in C2 (extends C1<long>)

   protected void M4(C1<long>.N n) { } // CLS-compliant, C1<long>.N is
                                       // accessible in C2 (extends C1<long>)
}
// Attempting to compile the example displays output like the following:
//       Generics4.cs(9,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
//       Generics4.cs(18,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
```

```vb
<Assembly:CLSCompliant(True)>

Public Class C1(Of T) 
   Protected Class N
   End Class

   Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
                                             ' accessible from within C1(Of T) in all
   End Sub                                   ' languages


   Protected Sub M2(n As C1(Of T).N)     ' CLS-compliant – C1(Of T).N accessible
   End Sub                               ' inside C1(Of T)
End Class

Public Class C2 : Inherits C1(Of Long) 
   Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant – C1(Of Integer).N is not
   End Sub                                   ' accessible in C2 (extends C1(Of Long))

   Protected Sub M4(n As C1(Of Long).N)   
   End Sub                                
End Class
' Attempting to compile the example displays output like the following:
'    error BC30508: 'n' cannot expose type 'C1(Of Integer).N' in namespace 
'    '<Default>' through class 'C1'.
'    
'       Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
'                             ~~~~~~~~~~~~~~~~
'    error BC30389: 'C1(Of T).N' is not accessible in this context because 
'    it is 'Protected'.
'    
'       Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant - C1(Of Integer).N is not
'    
'                             ~~~~~~~~~~~~~~~~
'    
'    error BC30389: 'C1(Of T).N' is not accessible in this context because it is 'Protected'.
'    
'       Protected Sub M4(n As C1(Of Long).N)  
'                             ~~~~~~~~~~~~~
```

### <a name="constructors"></a><span data-ttu-id="05ed1-575">建構函式</span><span class="sxs-lookup"><span data-stu-id="05ed1-575">Constructors</span></span>

<span data-ttu-id="05ed1-576">符合 CLS 標準之類別和結構中的建構函式必須遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="05ed1-576">Constructors in CLS-compliant classes and structures must follow these rules:</span></span> 

* <span data-ttu-id="05ed1-577">衍生類別的建構函式必須先呼叫基底類別的建構函式，才能存取繼承的執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="05ed1-577">A constructor of a derived class must call the instance constructor of its base class before it accesses inherited instance data.</span></span> <span data-ttu-id="05ed1-578">因為衍生類別不會繼承基底類別建構函式，所以才有這項需求。</span><span class="sxs-lookup"><span data-stu-id="05ed1-578">This requirement is due to the fact that base class constructors are not inherited by their derived classes.</span></span> <span data-ttu-id="05ed1-579">此規則不會套用至結構，因為結構不支援直接繼承。</span><span class="sxs-lookup"><span data-stu-id="05ed1-579">This rule does not apply to structures, which do not support direct inheritance.</span></span> 

  <span data-ttu-id="05ed1-580">通常，編譯器會獨立強制執行此規則，而不需考慮 CLS 符合性，如下面範例所示。</span><span class="sxs-lookup"><span data-stu-id="05ed1-580">Typically, compilers enforce this rule independently of CLS compliance, as the following example shows.</span></span> <span data-ttu-id="05ed1-581">它會建立衍生自 `Doctor` 類別的 `Person` 類別，但是 `Doctor` 類別無法呼叫 `Person` 類別建構函式來初始化繼承的執行個體欄位。</span><span class="sxs-lookup"><span data-stu-id="05ed1-581">It creates a `Doctor` class that is derived from a `Person` class, but the `Doctor` class fails to call the `Person` class constructor to initialize inherited instance fields.</span></span> 

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public class Person
    {
    private string fName, lName, _id;

    public Person(string firstName, string lastName, string id)
    {
        if (String.IsNullOrEmpty(firstName + lastName))
            throw new ArgumentNullException("Either a first name or a last name must be provided.");    

        fName = firstName;
        lName = lastName;
        _id = id;
    }

    public string FirstName 
    {
        get { return fName; }
    }

    public string LastName 
    {
        get { return lName; }
    }

    public string Id 
    {
        get { return _id; }
    }

    public override string ToString()
    {
        return String.Format("{0}{1}{2}", fName, 
                            String.IsNullOrEmpty(fName) ?  "" : " ",
                            lName);
    }
    }

    public class Doctor : Person
    {
    public Doctor(string firstName, string lastName, string id)
    {
    }

    public override string ToString()
    {
        return "Dr. " + base.ToString();
    }
    }
    // Attempting to compile the example displays output like the following:
    //    ctor1.cs(45,11): error CS1729: 'Person' does not contain a constructor that takes 0
    //            arguments
    //    ctor1.cs(10,11): (Location of symbol related to previous error)
    ```

    ```vb
    <Assembly: CLSCompliant(True)> 

    Public Class Person
       Private fName, lName, _id As String

       Public Sub New(firstName As String, lastName As String, id As String)
          If String.IsNullOrEmpty(firstName + lastName) Then
             Throw New ArgumentNullException("Either a first name or a last name must be provided.")    
          End If

          fName = firstName
          lName = lastName
          _id = id
       End Sub

       Public ReadOnly Property FirstName As String
          Get
             Return fName
          End Get
       End Property

       Public ReadOnly Property LastName As String
          Get
             Return lName
          End Get
       End Property

       Public ReadOnly Property Id As String
          Get
             Return _id
          End Get
       End Property

       Public Overrides Function ToString() As String
          Return String.Format("{0}{1}{2}", fName, 
                               If(String.IsNullOrEmpty(fName), "", " "),
                               lName)
       End Function
    End Class

    Public Class Doctor : Inherits Person
       Public Sub New(firstName As String, lastName As String, id As String)
       End Sub

       Public Overrides Function ToString() As String
          Return "Dr. " + MyBase.ToString()
       End Function
    End Class
    ' Attempting to compile the example displays output like the following:
    '    Ctor1.vb(46) : error BC30148: First statement of this 'Sub New' must be a call 
    '    to 'MyBase.New' or 'MyClass.New' because base class 'Person' of 'Doctor' does 
    '    not have an accessible 'Sub New' that can be called with no arguments.
    '    
    '       Public Sub New()
    '                  ~~~
    ````
    
* <span data-ttu-id="05ed1-582">物件建構函式除了建立物件之外，無法被呼叫。</span><span class="sxs-lookup"><span data-stu-id="05ed1-582">An object constructor cannot be called except to create an object.</span></span> <span data-ttu-id="05ed1-583">此外，物件無法初始化兩次。</span><span class="sxs-lookup"><span data-stu-id="05ed1-583">In addition, an object cannot be initialized twice.</span></span> <span data-ttu-id="05ed1-584">例如，這表示 `Object.MemberwiseClone` 不能呼叫建構函式。</span><span class="sxs-lookup"><span data-stu-id="05ed1-584">For example, this means that `Object.MemberwiseClone` must not call constructors.</span></span>  

### <a name="properties"></a><span data-ttu-id="05ed1-585">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-585">Properties</span></span>

<span data-ttu-id="05ed1-586">符合 CLS 標準的類型中的屬性必須遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="05ed1-586">Properties in CLS-compliant types must follow these rules:</span></span>

* <span data-ttu-id="05ed1-587">屬性必須有 setter、getter 或兩者皆有。</span><span class="sxs-lookup"><span data-stu-id="05ed1-587">A property must have a setter, a getter, or both.</span></span> <span data-ttu-id="05ed1-588">在組件中，這些會實作為特殊方法，亦即在組件的中繼資料中，會以個別的方法出現 (getter 會命名為 `get`\_*propertyname*，setter 會命名為 `set*\_*propertyname*) marked as `SpecialName'。</span><span class="sxs-lookup"><span data-stu-id="05ed1-588">In an assembly, these are implemented as special methods, which means that they will appear as separate methods (the getter is named `get`\_*propertyname* and the setter is `set*\_*propertyname*) marked as `SpecialName\` in the assembly's metadata.</span></span> <span data-ttu-id="05ed1-589">C# 編譯器會自動強制執行這項規則，而不需要套用 [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 屬性。</span><span class="sxs-lookup"><span data-stu-id="05ed1-589">The C# compiler enforces this rule automatically without the need to apply the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute.</span></span> 

* <span data-ttu-id="05ed1-590">屬性的類型是屬性 getter 的傳回型別和 setter 的最後一個引數。</span><span class="sxs-lookup"><span data-stu-id="05ed1-590">A property's type is the return type of the property getter and the last argument of the setter.</span></span> <span data-ttu-id="05ed1-591">這些類型必須符合 CLS 標準，而且引數不能以傳址方式指派給屬性 (也就是它們不能是 Managed 指標)。</span><span class="sxs-lookup"><span data-stu-id="05ed1-591">These types must be CLS compliant, and arguments cannot be assigned to the property by reference (that is, they cannot be managed pointers).</span></span> 

* <span data-ttu-id="05ed1-592">如果屬性同時有 getter 和 setter，則兩者都必須是虛擬、靜態或者都是執行個體。</span><span class="sxs-lookup"><span data-stu-id="05ed1-592">If a property has both a getter and a setter, they must both be virtual, both static, or both instance.</span></span> <span data-ttu-id="05ed1-593">C# 編譯器會透過屬性定義語法，來自動強制執行這項規則。</span><span class="sxs-lookup"><span data-stu-id="05ed1-593">The C# compiler automatically enforces this rule through property definition syntax.</span></span> 

### <a name="events"></a><span data-ttu-id="05ed1-594">事件</span><span class="sxs-lookup"><span data-stu-id="05ed1-594">Events</span></span>

<span data-ttu-id="05ed1-595">事件是由它的名稱和類型來定義。</span><span class="sxs-lookup"><span data-stu-id="05ed1-595">An event is defined by its name and its type.</span></span> <span data-ttu-id="05ed1-596">事件類型是用來表示事件的委派。</span><span class="sxs-lookup"><span data-stu-id="05ed1-596">The event type is a delegate that is used to indicate the event.</span></span> <span data-ttu-id="05ed1-597">例如，`DbConnection.StateChange` 事件的類型為 `StateChangeEventHandler`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-597">For example, the `DbConnection.StateChange` event is of type `StateChangeEventHandler`.</span></span> <span data-ttu-id="05ed1-598">除了事件本身之外，具有以事件名稱為根據之名稱的三個方法會提供事件的實作，並且在組件的中繼資料中標記為 `SpecialName`：</span><span class="sxs-lookup"><span data-stu-id="05ed1-598">In addition to the event itself, three methods with names based on the event name provide the event's implementation and are marked as `SpecialName` in the assembly's metadata:</span></span> 

* <span data-ttu-id="05ed1-599">用於加入事件處理常式的方法，名稱為 `add`_*EventName*。</span><span class="sxs-lookup"><span data-stu-id="05ed1-599">A method for adding an event handler, named `add`_*EventName*.</span></span> <span data-ttu-id="05ed1-600">例如，`DbConnection.StateChange` 事件的事件訂閱方法是命名為 `add_StateChange`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-600">For example, the event subscription method for the `DbConnection.StateChange` event is named `add_StateChange`.</span></span> 

* <span data-ttu-id="05ed1-601">用於移除事件處理常式的方法，名稱為 `remove`_*EventName*。</span><span class="sxs-lookup"><span data-stu-id="05ed1-601">A method for removing an event handler, named `remove`_*EventName*.</span></span> <span data-ttu-id="05ed1-602">例如，`DbConnection.StateChange` 事件的移除方法是命名為 `remove_StateChange`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-602">For example, the removal method for the `DbConnection.StateChange` event is named `remove_StateChange`.</span></span>

* <span data-ttu-id="05ed1-603">用於表示事件已發生的方法，名稱為 `raise`_*EventName*。</span><span class="sxs-lookup"><span data-stu-id="05ed1-603">A method for indicating that the event has occurred, named `raise`_*EventName*.</span></span> 

> [!NOTE]
> <span data-ttu-id="05ed1-604">大部分與事件有關的 Common Language Specification 規則都是由語言編譯器實作，而且對元件開發人員而言是透明化的。</span><span class="sxs-lookup"><span data-stu-id="05ed1-604">Most of the Common Language Specification's rules regarding events are implemented by language compilers and are transparent to component developers.</span></span> 

<span data-ttu-id="05ed1-605">用於加入、移除及引發事件的方法必須具有相同的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="05ed1-605">The methods for adding, removing, and raising the event must have the same accessibility.</span></span> <span data-ttu-id="05ed1-606">它們也必須全部是靜態、執行個體或虛擬的。</span><span class="sxs-lookup"><span data-stu-id="05ed1-606">They must also all be static, instance, or virtual.</span></span> <span data-ttu-id="05ed1-607">用於加入和移除事件的方法具有一個類型為事件委派類型的參數。</span><span class="sxs-lookup"><span data-stu-id="05ed1-607">The methods for adding and removing an event have one parameter whose type is the event delegate type.</span></span> <span data-ttu-id="05ed1-608">加入和移除方法兩者必須同時存在或同時不存在。</span><span class="sxs-lookup"><span data-stu-id="05ed1-608">The add and remove methods must both be present or both be absent.</span></span> 

<span data-ttu-id="05ed1-609">下面範例定義了符合 CLS 標準的類別 (名稱為 `Temperature`)，如果兩個讀數之間的溫度變更等於或超過臨界值，這個類別會引發 `TemperatureChanged` 事件。</span><span class="sxs-lookup"><span data-stu-id="05ed1-609">The following example defines a CLS-compliant class named `Temperature` that raises a `TemperatureChanged` event if the change in temperature between two readings equals or exceeds a threshold value.</span></span> <span data-ttu-id="05ed1-610">`Temperature` 類別會明確地定義 `raise_TemperatureChanged` 方法，讓它可以選擇性地執行事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="05ed1-610">The `Temperature` class explicitly defines a `raise_TemperatureChanged` method so that it can selectively execute event handlers.</span></span>

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

[assembly: CLSCompliant(true)]

public class TemperatureChangedEventArgs : EventArgs
{
   private Decimal originalTemp;
   private Decimal newTemp; 
   private DateTimeOffset when;

   public TemperatureChangedEventArgs(Decimal original, Decimal @new, DateTimeOffset time)
   {
      originalTemp = original;
      newTemp = @new;
      when = time;
   }   

   public Decimal OldTemperature
   {
      get { return originalTemp; }
   } 

   public Decimal CurrentTemperature
   {
      get { return newTemp; }
   } 

   public DateTimeOffset Time
   {
      get { return when; }
   }
}

public delegate void TemperatureChanged(Object sender, TemperatureChangedEventArgs e);

public class Temperature
{
   private struct TemperatureInfo
   {
      public Decimal Temperature;
      public DateTimeOffset Recorded;
   }

   public event TemperatureChanged TemperatureChanged;

   private Decimal previous;
   private Decimal current;
   private Decimal tolerance;
   private List<TemperatureInfo> tis = new List<TemperatureInfo>();

   public Temperature(Decimal temperature, Decimal tolerance)
   {
      current = temperature;
      TemperatureInfo ti = new TemperatureInfo();
      ti.Temperature = temperature;
      tis.Add(ti);
      ti.Recorded = DateTimeOffset.UtcNow;
      this.tolerance = tolerance;
   }

   public Decimal CurrentTemperature
   {
      get { return current; }
      set {
         TemperatureInfo ti = new TemperatureInfo();
         ti.Temperature = value;
         ti.Recorded = DateTimeOffset.UtcNow;
         previous = current;
         current = value;
         if (Math.Abs(current - previous) >= tolerance) 
            raise_TemperatureChanged(new TemperatureChangedEventArgs(previous, current, ti.Recorded));
      }
   }

   public void raise_TemperatureChanged(TemperatureChangedEventArgs eventArgs)
   {
      if (TemperatureChanged == null)
         return; 

      foreach (TemperatureChanged d in TemperatureChanged.GetInvocationList()) {
         if (d.Method.Name.Contains("Duplicate"))
            Console.WriteLine("Duplicate event handler; event handler not executed.");
         else
            d.Invoke(this, eventArgs);
      }
   }
}

public class Example
{
   public Temperature temp;

   public static void Main()
   {
      Example ex = new Example();
   }

   public Example()
   {
      temp = new Temperature(65, 3);
      temp.TemperatureChanged += this.TemperatureNotification;
      RecordTemperatures();
      Example ex = new Example(temp);
      ex.RecordTemperatures();
   }

   public Example(Temperature t)
   {
      temp = t;
      RecordTemperatures();
   }

   public void RecordTemperatures()
   {
      temp.TemperatureChanged += this.DuplicateTemperatureNotification;
      temp.CurrentTemperature = 66;
      temp.CurrentTemperature = 63;
   }

   internal void TemperatureNotification(Object sender, TemperatureChangedEventArgs e) 
   {
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);   
   }

   public void DuplicateTemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   { 
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);   
   }
}
```

```vb
Imports System.Collections
Imports System.Collections.Generic

<Assembly: CLSCompliant(True)>

Public Class TemperatureChangedEventArgs   : Inherits EventArgs
   Private originalTemp As Decimal
   Private newTemp As Decimal 
   Private [when] As DateTimeOffset

   Public Sub New(original As Decimal, [new] As Decimal, [time] As DateTimeOffset)
      originalTemp = original
      newTemp = [new]
      [when] = [time]
   End Sub   

   Public ReadOnly Property OldTemperature As Decimal
      Get
         Return originalTemp
      End Get
   End Property 

   Public ReadOnly Property CurrentTemperature As Decimal
      Get
         Return newTemp
      End Get
   End Property 

   Public ReadOnly Property [Time] As DateTimeOffset
      Get
         Return [when]
      End Get
   End Property
End Class

Public Delegate Sub TemperatureChanged(sender As Object, e As TemperatureChangedEventArgs)

Public Class Temperature
   Private Structure TemperatureInfo
      Dim Temperature As Decimal
      Dim Recorded As DateTimeOffset
   End Structure

   Public Event TemperatureChanged As TemperatureChanged

   Private previous As Decimal
   Private current As Decimal
   Private tolerance As Decimal
   Private tis As New List(Of TemperatureInfo)

   Public Sub New(temperature As Decimal, tolerance As Decimal)
      current = temperature
      Dim ti As New TemperatureInfo()
      ti.Temperature = temperature
      ti.Recorded = DateTimeOffset.UtcNow
      tis.Add(ti)
      Me.tolerance = tolerance
   End Sub

   Public Property CurrentTemperature As Decimal
      Get
         Return current
      End Get
      Set
         Dim ti As New TemperatureInfo
         ti.Temperature = value
         ti.Recorded = DateTimeOffset.UtcNow
         previous = current
         current = value
         If Math.Abs(current - previous) >= tolerance Then
            raise_TemperatureChanged(New TemperatureChangedEventArgs(previous, current, ti.Recorded))
         End If
      End Set
   End Property

   Public Sub raise_TemperatureChanged(eventArgs As TemperatureChangedEventArgs)
      If TemperatureChangedEvent Is Nothing Then Exit Sub

      Dim ListenerList() As System.Delegate = TemperatureChangedEvent.GetInvocationList()
      For Each d As TemperatureChanged In TemperatureChangedEvent.GetInvocationList()
         If d.Method.Name.Contains("Duplicate") Then
            Console.WriteLine("Duplicate event handler; event handler not executed.")
         Else
            d.Invoke(Me, eventArgs)
         End If
      Next
   End Sub
End Class

Public Class Example
   Public WithEvents temp As Temperature

   Public Shared Sub Main()
      Dim ex As New Example()
   End Sub

   Public Sub New()
      temp = New Temperature(65, 3)
      RecordTemperatures()
      Dim ex As New Example(temp)
      ex.RecordTemperatures()
   End Sub

   Public Sub New(t As Temperature)
      temp = t
      RecordTemperatures()
   End Sub

   Public Sub RecordTemperatures()
      temp.CurrentTemperature = 66
      temp.CurrentTemperature = 63

   End Sub

   Friend Shared Sub TemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)   
   End Sub

   Friend Shared Sub DuplicateTemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)   
   End Sub
End Class
```

### <a name="overloads"></a><span data-ttu-id="05ed1-611">Overloads</span><span class="sxs-lookup"><span data-stu-id="05ed1-611">Overloads</span></span>

<span data-ttu-id="05ed1-612">Common Language Specification 會對多載成員施加下列需求：</span><span class="sxs-lookup"><span data-stu-id="05ed1-612">The Common Language Specification imposes the following requirements on overloaded members:</span></span> 

* <span data-ttu-id="05ed1-613">成員可以根據參數的數目和任何參數的類型來多載。</span><span class="sxs-lookup"><span data-stu-id="05ed1-613">Members can be overloaded based on the number of parameters and the type of any parameter.</span></span> <span data-ttu-id="05ed1-614">辨別多載時，不會考慮呼叫慣例、傳回型別、套用至方法或其參數的自訂修飾詞，以及參數是以傳值或傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="05ed1-614">Calling convention, return type, custom modifiers applied to the method or its parameter, and whether parameters are passed by value or by reference are not considered when differentiating between overloads.</span></span> <span data-ttu-id="05ed1-615">如需範例，請參閱[命名慣例](#naming-conventions)一節中，要求範圍內的名稱必須是唯一名稱的程式碼。</span><span class="sxs-lookup"><span data-stu-id="05ed1-615">For an example, see the code for the requirement that names must be unique within a scope in the [Naming conventions](#naming-conventions) section.</span></span> 

* <span data-ttu-id="05ed1-616">只有屬性和方法可以多載。</span><span class="sxs-lookup"><span data-stu-id="05ed1-616">Only properties and methods can be overloaded.</span></span> <span data-ttu-id="05ed1-617">欄位和事件不可多載。</span><span class="sxs-lookup"><span data-stu-id="05ed1-617">Fields and events cannot be overloaded.</span></span> 

* <span data-ttu-id="05ed1-618">泛型方法可以根據其泛型參數的數目來多載。</span><span class="sxs-lookup"><span data-stu-id="05ed1-618">Generic methods can be overloaded based on the number of their generic parameters.</span></span> 

> [!NOTE]
><span data-ttu-id="05ed1-619">多載解析時傳回值不會被視為方法簽章的一部分，這個規則的例外是 `op_Explicit` 和 `op_Implicit` 運算子。</span><span class="sxs-lookup"><span data-stu-id="05ed1-619">The `op_Explicit` and `op_Implicit` operators are exceptions to the rule that return value is not considered part of a method signature for overload resolution.</span></span> <span data-ttu-id="05ed1-620">這兩個運算子可以根據其參數以及其傳回值來多載。</span><span class="sxs-lookup"><span data-stu-id="05ed1-620">These two operators can be overloaded based on both their parameters and their return value.</span></span> 

### <a name="exceptions"></a><span data-ttu-id="05ed1-621">例外狀況</span><span class="sxs-lookup"><span data-stu-id="05ed1-621">Exceptions</span></span>

<span data-ttu-id="05ed1-622">例外狀況物件必須衍生自 [System.Exception](xref:System.Exception)，或衍生自另一個衍生自 `System.Exception` 的類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-622">Exception objects must derive from [System.Exception](xref:System.Exception) or from another type derived from `System.Exception`.</span></span> <span data-ttu-id="05ed1-623">下面範例說明在名為 `ErrorClass` 的自訂類別用於例外狀況處理時，所造成的編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="05ed1-623">The following example illustrates the compiler error that results when a custom class named `ErrorClass` is used for exception handling.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass
{ 
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1), 
                          value.Substring(index) };
      return retVal;
   }
}
// Compilation produces a compiler error like the following:
//    Exceptions1.cs(26,16): error CS0155: The type caught or thrown must be derived from
//            System.Exception
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass 
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public ReadOnly Property Message As String
      Get
         Return msg
      End Get   
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1), 
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
' Compilation produces a compiler error like the following:
'    Exceptions1.vb(27) : error BC30665: 'Throw' operand must derive from 'System.Exception'.
'    
'             Throw BadIndex
'             ~~~~~~~~~~~~~~
```

<span data-ttu-id="05ed1-624">若要更正這個錯誤，`ErrorClass` 類別必須繼承自 `System.Exception`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-624">To correct this error, the `ErrorClass` class must inherit from `System.Exception`.</span></span> <span data-ttu-id="05ed1-625">此外，還必須覆寫 Message 屬性。</span><span class="sxs-lookup"><span data-stu-id="05ed1-625">In addition, the Message property must be overridden.</span></span> <span data-ttu-id="05ed1-626">下面範例會修正這些錯誤，以定義符合 CLS 標準的 `ErrorClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="05ed1-626">The following example corrects these errors to define an `ErrorClass` class that is CLS-compliant.</span></span>  

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass : Exception
{ 
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public override string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1), 
                          value.Substring(index) };
      return retVal;
   }
}
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass : Inherits Exception
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public Overrides ReadOnly Property Message As String
      Get
         Return msg
      End Get   
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1), 
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
```

### <a name="attributes"></a><span data-ttu-id="05ed1-627">屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-627">Attributes</span></span>

<span data-ttu-id="05ed1-628">在 .NET Framework 組件中，自訂屬性會提供可擴充機制，用於儲存自訂屬性和擷取程式設計物件 (例如組件、類型、成員和方法參數) 的相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="05ed1-628">In.NET Framework assemblies, custom attributes provide an extensible mechanism for storing custom attributes and retrieving metadata about programming objects, such as assemblies, types, members, and method parameters.</span></span> <span data-ttu-id="05ed1-629">自訂屬性必須衍生自 [System.Attribute](xref:System.Attribute)，或從衍生自 `System.Attribute` 的類型衍生而來。</span><span class="sxs-lookup"><span data-stu-id="05ed1-629">Custom attributes must derive from [System.Attribute](xref:System.Attribute) or from a type derived from `System.Attribute`.</span></span>

<span data-ttu-id="05ed1-630">下面範例違反這項規則。</span><span class="sxs-lookup"><span data-stu-id="05ed1-630">The following example violates this rule.</span></span> <span data-ttu-id="05ed1-631">它會定義不是衍生自 `NumericAttribute` 的 `System.Attribute` 類別</span><span class="sxs-lookup"><span data-stu-id="05ed1-631">It defines a `NumericAttribute` class that does not derive from `System.Attribute`.</span></span> <span data-ttu-id="05ed1-632">請注意，只有在套用不符合 CLS 標準的屬性時，而不是在定義類別時，才會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="05ed1-632">Note that a compiler error results only when the non-CLS-compliant attribute is applied, not when the class is defined.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

[AttributeUsageAttribute(AttributeTargets.Class | AttributeTargets.Struct)] 
public class NumericAttribute
{
   private bool _isNumeric;

   public NumericAttribute(bool isNumeric)
   {
      _isNumeric = isNumeric;
   }

   public bool IsNumeric 
   {
      get { return _isNumeric; }
   }
}

[Numeric(true)] public struct UDouble
{
   double Value;
}
// Compilation produces a compiler error like the following:
//    Attribute1.cs(22,2): error CS0616: 'NumericAttribute' is not an attribute class
//    Attribute1.cs(7,14): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

<AttributeUsageAttribute(AttributeTargets.Class Or AttributeTargets.Struct)> _
Public Class NumericAttribute
   Private _isNumeric As Boolean

   Public Sub New(isNumeric As Boolean)
      _isNumeric = isNumeric
   End Sub

   Public ReadOnly Property IsNumeric As Boolean
      Get
         Return _isNumeric
      End Get
   End Property
End Class

<Numeric(True)> Public Structure UDouble
   Dim Value As Double
End Structure
' Compilation produces a compiler error like the following:
'    error BC31504: 'NumericAttribute' cannot be used as an attribute because it 
'    does not inherit from 'System.Attribute'.
'    
'    <Numeric(True)> Public Structure UDouble
'     ~~~~~~~~~~~~~
```

<span data-ttu-id="05ed1-633">建構函式或符合 CLS 標準的屬性 (attribute) 的屬性 (property) 只能公開下列類型：</span><span class="sxs-lookup"><span data-stu-id="05ed1-633">The constructor or the properties of a CLS-compliant attribute can expose only the following types:</span></span>

* [<span data-ttu-id="05ed1-634">布林值</span><span class="sxs-lookup"><span data-stu-id="05ed1-634">Boolean</span></span>](xref:System.Boolean)

* [<span data-ttu-id="05ed1-635">Byte</span><span class="sxs-lookup"><span data-stu-id="05ed1-635">Byte</span></span>](xref:System.Byte)

* [<span data-ttu-id="05ed1-636">Char</span><span class="sxs-lookup"><span data-stu-id="05ed1-636">Char</span></span>](xref:System.Char)

* [<span data-ttu-id="05ed1-637">Double</span><span class="sxs-lookup"><span data-stu-id="05ed1-637">Double</span></span>](xref:System.Double)

* [<span data-ttu-id="05ed1-638">Int16</span><span class="sxs-lookup"><span data-stu-id="05ed1-638">Int16</span></span>](xref:System.Int16)

* [<span data-ttu-id="05ed1-639">Int32</span><span class="sxs-lookup"><span data-stu-id="05ed1-639">Int32</span></span>](xref:System.Int32)

* [<span data-ttu-id="05ed1-640">Int64</span><span class="sxs-lookup"><span data-stu-id="05ed1-640">Int64</span></span>](xref:System.Int64)

* [<span data-ttu-id="05ed1-641">Single</span><span class="sxs-lookup"><span data-stu-id="05ed1-641">Single</span></span>](xref:System.Single)

* [<span data-ttu-id="05ed1-642">String</span><span class="sxs-lookup"><span data-stu-id="05ed1-642">String</span></span>](xref:System.String)

* [<span data-ttu-id="05ed1-643">類型</span><span class="sxs-lookup"><span data-stu-id="05ed1-643">Type</span></span>](xref:System.Type)

* <span data-ttu-id="05ed1-644">基礎類型為 `Byte`、`Int16`、`Int32` 或 `Int64` 的任何列舉類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-644">Any enumeration type whose underlying type is `Byte`, `Int16`, `Int32`, or `Int64`.</span></span> 

<span data-ttu-id="05ed1-645">下面範例會定義衍生自 [Attribute](xref:System.Attribute) 的 `DescriptionAttribute` 類別。</span><span class="sxs-lookup"><span data-stu-id="05ed1-645">The following example defines a `DescriptionAttribute` class that derives from [Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="05ed1-646">類別建構函式具有類型為 `Descriptor` 的參數，因此類別不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-646">The class constructor has a parameter of type `Descriptor`, so the class is not CLS-compliant.</span></span> <span data-ttu-id="05ed1-647">請注意，C# 編譯器會發出警告，但編譯會成功。</span><span class="sxs-lookup"><span data-stu-id="05ed1-647">Note that the C# compiler emits a warning but compiles successfully.</span></span> 

```csharp
using System;

[assembly:CLSCompliantAttribute(true)]

public enum DescriptorType { type, member };

public class Descriptor
{
   public DescriptorType Type;
   public String Description; 
}

[AttributeUsage(AttributeTargets.All)]
public class DescriptionAttribute : Attribute
{
   private Descriptor desc;

   public DescriptionAttribute(Descriptor d)
   {
      desc = d; 
   }

   public Descriptor Descriptor
   { get { return desc; } } 
}
// Attempting to compile the example displays output like the following:
//       warning CS3015: 'DescriptionAttribute' has no accessible
//               constructors which use only CLS-compliant types
```

```vb
<Assembly:CLSCompliantAttribute(True)>

Public Enum DescriptorType As Integer
   Type = 0
   Member = 1
End Enum

Public Class Descriptor
   Public Type As DescriptorType 
   Public Description As String 
End Class

<AttributeUsage(AttributeTargets.All)> _
Public Class DescriptionAttribute : Inherits Attribute
   Private desc As Descriptor

   Public Sub New(d As Descriptor)
      desc = d 
   End Sub

   Public ReadOnly Property Descriptor As Descriptor
      Get 
         Return desc
      End Get    
   End Property
End Class
```

## <a name="the-clscompliantattribute-attribute"></a><span data-ttu-id="05ed1-648">CLSCompliantAttribute 屬性</span><span class="sxs-lookup"><span data-stu-id="05ed1-648">The CLSCompliantAttribute attribute</span></span>

<span data-ttu-id="05ed1-649">[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 屬性用於表示程式項目是否符合 Common Language Specification。</span><span class="sxs-lookup"><span data-stu-id="05ed1-649">The [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is used to indicate whether a program element complies with the Common Language Specification.</span></span> <span data-ttu-id="05ed1-650">`CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` 建構函式包含單一必要參數 *isCompliant*，表示程式項目是否符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-650">The `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` constructor includes a single required parameter, *isCompliant*, that indicates whether the program element is CLS-compliant.</span></span> 

<span data-ttu-id="05ed1-651">在編譯時間，編譯器會偵測到假設符合 CLS 標準之不符合標準的項目，並發出警告。</span><span class="sxs-lookup"><span data-stu-id="05ed1-651">At compile time, the compiler detects non-compliant elements that are presumed to be CLS-compliant and emits a warning.</span></span> <span data-ttu-id="05ed1-652">對於明確宣告為不符合標準的類型或成員，編譯器不會發出警告。</span><span class="sxs-lookup"><span data-stu-id="05ed1-652">The compiler does not emit warnings for types or members that are explicitly declared to be non-compliant.</span></span> 

<span data-ttu-id="05ed1-653">元件開發人員可以透過兩種方式使用 `CLSCompliantAttribute` 屬性：</span><span class="sxs-lookup"><span data-stu-id="05ed1-653">Component developers can use the `CLSCompliantAttribute` attribute in two ways:</span></span> 

* <span data-ttu-id="05ed1-654">定義元件所公開符合 CLS 標準的公用介面的組件和不符合 CLS 標準的組件。</span><span class="sxs-lookup"><span data-stu-id="05ed1-654">To define the parts of the public interface exposed by a component that are CLS-compliant and the parts that are not CLS-compliant.</span></span> <span data-ttu-id="05ed1-655">當該屬性是用來將特定程式項目標記為符合 CLS 標準時，使用它可以確保目標為 .NET Framework 的所有語言和工具都可以存取這些項目。</span><span class="sxs-lookup"><span data-stu-id="05ed1-655">When the attribute is used to mark particular program elements as CLS-compliant, its use guarantees that those elements are accessible from all languages and tools that target the .NET Framework.</span></span> 

* <span data-ttu-id="05ed1-656">確定元件庫的公用介面只公開符合 CLS 標準的程式項目。</span><span class="sxs-lookup"><span data-stu-id="05ed1-656">To ensure that the component library's public interface exposes only program elements that are CLS-compliant.</span></span> <span data-ttu-id="05ed1-657">如果項目不符合 CLS 標準，編譯器通常會發出警告。</span><span class="sxs-lookup"><span data-stu-id="05ed1-657">If elements are not CLS-compliant, compilers will generally issue a warning.</span></span>

> [!WARNING]
> <span data-ttu-id="05ed1-658">在某些情況下，語言編譯器會強制執行符合 CLS 標準的規則，而不論是否使用 `CLSCompliantAttribute` 屬性。</span><span class="sxs-lookup"><span data-stu-id="05ed1-658">In some cases, language compilers enforce CLS-compliant rules regardless of whether the `CLSCompliantAttribute` attribute is used.</span></span> <span data-ttu-id="05ed1-659">例如，定義介面的 `*static` 成員會違反 CLS 規則。</span><span class="sxs-lookup"><span data-stu-id="05ed1-659">For example, defining a `*static` member in an interface violates a CLS rule.</span></span> <span data-ttu-id="05ed1-660">不過，如果您在介面中定義 `*static` 成員，C# 編譯器會顯示錯誤訊息，並且無法編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="05ed1-660">However, if you define a `*static` member in an interface, the C# compiler displays an error message and fails to compile the app.</span></span>

<span data-ttu-id="05ed1-661">`CLSCompliantAttribute` 屬性標記著具有 `AttributeTargets.All` 值的 [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) 屬性。</span><span class="sxs-lookup"><span data-stu-id="05ed1-661">The `CLSCompliantAttribute` attribute is marked with an [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) attribute that has a value of `AttributeTargets.All`.</span></span> <span data-ttu-id="05ed1-662">此值可讓您將 `CLSCompliantAttribute` 屬性套用至任何程式項目，包括組件、模組、類型 (類別、結構、列舉、介面和委派)、類型成員 (建構函式、方法、屬性、欄位和事件)、參數、泛型參數和傳回值。</span><span class="sxs-lookup"><span data-stu-id="05ed1-662">This value allows you to apply the `CLSCompliantAttribute` attribute to any program element, including assemblies, modules, types (classes, structures, enumerations, interfaces, and delegates), type members (constructors, methods, properties, fields, and events), parameters, generic parameters, and return values.</span></span> <span data-ttu-id="05ed1-663">不過，在實務中，您應該只將該屬性套用至組件、類型和類型成員。</span><span class="sxs-lookup"><span data-stu-id="05ed1-663">However, in practice, you should apply the attribute only to assemblies, types, and type members.</span></span> <span data-ttu-id="05ed1-664">否則，當編譯器在您的程式庫的公用介面中遇到不符合標準的參數、泛型參數或傳回值時，會忽略該屬性並繼續產生編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="05ed1-664">Otherwise, compilers ignore the attribute and continue to generate compiler warnings whenever they encounter a non-compliant parameter, generic parameter, or return value in your library's public interface.</span></span>  

<span data-ttu-id="05ed1-665">`CLSCompliantAttribute` 屬性的值是由內含的程式項目繼承。</span><span class="sxs-lookup"><span data-stu-id="05ed1-665">The value of the `CLSCompliantAttribute` attribute is inherited by contained program elements.</span></span> <span data-ttu-id="05ed1-666">例如，如果組件是標記為符合 CLS 標準，它的類型也會符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-666">For example, if an assembly is marked as CLS-compliant, its types are also CLS-compliant.</span></span> <span data-ttu-id="05ed1-667">如果類型是標記為符合 CLS 標準，其巢狀類型及成員也會符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-667">If a type is marked as CLS-compliant, its nested types and members are also CLS-compliant.</span></span> 

<span data-ttu-id="05ed1-668">您可以將 `CLSCompliantAttribute` 屬性套用至內含的程式項目，以明確覆寫繼承的符合性。</span><span class="sxs-lookup"><span data-stu-id="05ed1-668">You can explicitly override the inherited compliance by applying the `CLSCompliantAttribute` attribute to a contained program element.</span></span> <span data-ttu-id="05ed1-669">例如，您可以使用 *isCompliant* 值為 `false` 的 `CLSCompliantAttribute` 屬性，在符合標準的組件中定義不符合標準的類型，而且可以使用 *isComplian* 值為 `true` 的屬性，在不符合標準的組件中定義符合標準的類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-669">For example, you can use the `CLSCompliantAttribute` attribute with an *isCompliant* value of `false` to define a non-compliant type in a compliant assembly, and you can use the attribute with an *isComplian* value of `true` to define a compliant type in a non-compliant assembly.</span></span> <span data-ttu-id="05ed1-670">您也可以在符合標準的類型中定義不符合標準的成員。</span><span class="sxs-lookup"><span data-stu-id="05ed1-670">You can also define non-compliant members in a compliant type.</span></span> <span data-ttu-id="05ed1-671">然而，不符合標準的類型不能具有符合標準的成員，因此您無法使用 *isCompliant* 值為 `true` 的屬性來覆寫不符合標準之類型的繼承。</span><span class="sxs-lookup"><span data-stu-id="05ed1-671">However, a non-compliant type cannot have compliant members, so you cannot use the attribute with an *isCompliant* value of `true` to override inheritance from a non-compliant type.</span></span> 

<span data-ttu-id="05ed1-672">當您開發元件時，一定要使用 `CLSCompliantAttribute` 屬性來指出您的組件、其類型及其成員是否符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-672">When you are developing components, you should always use the `CLSCompliantAttribute` attribute to indicate whether your assembly, its types, and its members are CLS-compliant.</span></span> 

<span data-ttu-id="05ed1-673">若要建立符合 CLS 標準的元件：</span><span class="sxs-lookup"><span data-stu-id="05ed1-673">To create CLS-compliant components:</span></span> 

1. <span data-ttu-id="05ed1-674">使用 `CLSCompliantAttribute` 將組件標記為符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-674">Use the `CLSCompliantAttribute` to mark you assembly as CLS-compliant.</span></span>

2. <span data-ttu-id="05ed1-675">將不符合 CLS 標準之組件中公開的任何類型標記為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-675">Mark any publicly exposed types in the assembly that are not CLS-compliant as non-compliant.</span></span> 

3. <span data-ttu-id="05ed1-676">將符合 CLS 標準之類型中公開的任何成員標記為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="05ed1-676">Mark any publicly exposed members in CLS-compliant types as non-compliant.</span></span> 

4. <span data-ttu-id="05ed1-677">為不符合 CLS 標準的成員提供符合 CLS 標準的替代項目。</span><span class="sxs-lookup"><span data-stu-id="05ed1-677">Provide a CLS-compliant alternative for non-CLS-compliant members.</span></span> 

<span data-ttu-id="05ed1-678">如果成功標記了所有您不符合標準的類型和成員，則編譯器應該不會發出任何不符合標準的警告。</span><span class="sxs-lookup"><span data-stu-id="05ed1-678">If you've successfully marked all your non-compliant types and members, your compiler should not emit any non-compliance warnings.</span></span> <span data-ttu-id="05ed1-679">不過，您應該指出哪些成員不符合 CLS 標準，並在產品文件中列出符合 CLS 標準的替代項目。</span><span class="sxs-lookup"><span data-stu-id="05ed1-679">However, you should indicate which members are not CLS-compliant and list their CLS-compliant alternatives in your product documentation.</span></span> 

<span data-ttu-id="05ed1-680">下面範例會使用 `CLSCompliantAttribute` 屬性來定義符合 CLS 標準的組件和類型 `CharacterUtilities`，該類型有兩個不符合 CLS 標準的成員。</span><span class="sxs-lookup"><span data-stu-id="05ed1-680">The following example uses the `CLSCompliantAttribute` attribute to define a CLS-compliant assembly and a type, `CharacterUtilities`, that has two non-CLS-compliant members.</span></span> <span data-ttu-id="05ed1-681">由於兩個成員都是以 `CLSCompliant(false)` 屬性來標記，因此編譯器沒有產生警告。</span><span class="sxs-lookup"><span data-stu-id="05ed1-681">Because both members are tagged with the `CLSCompliant(false)` attribute, the compiler produces no warnings.</span></span> <span data-ttu-id="05ed1-682">該類別也為這兩個方法提供符合 CLS 標準的替代項目。</span><span class="sxs-lookup"><span data-stu-id="05ed1-682">The class also provides a CLS-compliant alternative for both methods.</span></span> <span data-ttu-id="05ed1-683">通常，我們會將兩個多載加入至 `ToUTF16` 方法，以提供符合 CLS 標準的替代項目。</span><span class="sxs-lookup"><span data-stu-id="05ed1-683">Ordinarily, we would just add two overloads to the `ToUTF16` method to provide CLS-compliant alternatives.</span></span> <span data-ttu-id="05ed1-684">不過，因為方法無法根據傳回值來多載，所以符合 CLS 標準之方法的名稱與不符合 CLS 標準之方法的名稱不同。</span><span class="sxs-lookup"><span data-stu-id="05ed1-684">However, because methods cannot be overloaded based on return value, the names of the CLS-compliant methods are different from the names of the non-compliant methods.</span></span>  

```csharp
using System;
using System.Text;

[assembly:CLSCompliant(true)]

public class CharacterUtilities
{
   [CLSCompliant(false)] public static ushort ToUTF16(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return Convert.ToUInt16(s[0]);
   }

   [CLSCompliant(false)] public static ushort ToUTF16(Char ch)
   {
      return Convert.ToUInt16(ch); 
   }

   // CLS-compliant alternative for ToUTF16(String).
   public static int ToUTF16CodeUnit(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return (int) Convert.ToUInt16(s[0]);
   }

   // CLS-compliant alternative for ToUTF16(Char).
   public static int ToUTF16CodeUnit(Char ch)
   {
      return Convert.ToInt32(ch);
   }

   public bool HasMultipleRepresentations(String s)
   {
      String s1 = s.Normalize(NormalizationForm.FormC);
      return s.Equals(s1);   
   }

   public int GetUnicodeCodePoint(Char ch)
   {
      if (Char.IsSurrogate(ch))
         throw new ArgumentException("ch cannot be a high or low surrogate.");

      return Char.ConvertToUtf32(ch.ToString(), 0);   
   }

   public int GetUnicodeCodePoint(Char[] chars)
   {
      if (chars.Length > 2)
         throw new ArgumentException("The array has too many characters.");

      if (chars.Length == 2) {
         if (! Char.IsSurrogatePair(chars[0], chars[1]))
            throw new ArgumentException("The array must contain a low and a high surrogate.");
         else
            return Char.ConvertToUtf32(chars[0], chars[1]);
      }
      else {
         return Char.ConvertToUtf32(chars.ToString(), 0);
      } 
   }
}
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class CharacterUtilities
   <CLSCompliant(False)> Public Shared Function ToUTF16(s As String) As UShort
      s = s.Normalize(NormalizationForm.FormC)
      Return Convert.ToUInt16(s(0))
   End Function

   <CLSCompliant(False)> Public Shared Function ToUTF16(ch As Char) As UShort
      Return Convert.ToUInt16(ch) 
   End Function

   ' CLS-compliant alternative for ToUTF16(String).
   Public Shared Function ToUTF16CodeUnit(s As String) As Integer
      s = s.Normalize(NormalizationForm.FormC)
      Return CInt(Convert.ToInt16(s(0)))
   End Function

   ' CLS-compliant alternative for ToUTF16(Char).
   Public Shared Function ToUTF16CodeUnit(ch As Char) As Integer
      Return Convert.ToInt32(ch)
   End Function

   Public Function HasMultipleRepresentations(s As String) As Boolean
      Dim s1 As String = s.Normalize(NormalizationForm.FormC)
      Return s.Equals(s1)   
   End Function

   Public Function GetUnicodeCodePoint(ch As Char) As Integer
      If Char.IsSurrogate(ch) Then
         Throw New ArgumentException("ch cannot be a high or low surrogate.")
      End If
      Return Char.ConvertToUtf32(ch.ToString(), 0)   
   End Function

   Public Function GetUnicodeCodePoint(chars() As Char) As Integer
      If chars.Length > 2 Then
         Throw New ArgumentException("The array has too many characters.")
      End If
      If chars.Length = 2 Then
         If Not Char.IsSurrogatePair(chars(0), chars(1)) Then
            Throw New ArgumentException("The array must contain a low and a high surrogate.")
         Else
            Return Char.ConvertToUtf32(chars(0), chars(1))
         End If
      Else
         Return Char.ConvertToUtf32(chars.ToString(), 0)
      End If 
   End Function            
End Class
```

<span data-ttu-id="05ed1-685">如果您要開發的是應用程式而非程式庫 (也就是說，如果您不會公開可由其他應用程式開發人員使用的類型或成員)，則您的應用程式所使用之程式項目的 CLS 符合性，只有在您的語言不支援這些項目時才需要考慮。</span><span class="sxs-lookup"><span data-stu-id="05ed1-685">If you are developing an app rather than a library (that is, if you aren't exposing types or members that can be consumed by other app developers), the CLS compliance of the program elements that your app consumes are of interest only if your language does not support them.</span></span> <span data-ttu-id="05ed1-686">在這種情況下，當您嘗試使用不符合 CLS 標準的項目時，您的語言編譯器會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="05ed1-686">In that case, your language compiler will generate an error when you try to use a non-CLS-compliant element.</span></span> 

## <a name="cross-language-interoperability"></a><span data-ttu-id="05ed1-687">跨語言互通性</span><span class="sxs-lookup"><span data-stu-id="05ed1-687">Cross-Language Interoperability</span></span>

<span data-ttu-id="05ed1-688">語言獨立性的意義可能有許多種。</span><span class="sxs-lookup"><span data-stu-id="05ed1-688">Language independence has a number of possible meanings.</span></span> <span data-ttu-id="05ed1-689">其中一種意義是指能夠在以某種語言撰寫的應用程式中，順利使用以另一種語言撰寫的類型。</span><span class="sxs-lookup"><span data-stu-id="05ed1-689">One meaning involves seamlessly consuming types written in one language from an app written in another language.</span></span> <span data-ttu-id="05ed1-690">第二種意義則是本文重點所在，是指將多種語言撰寫的程式碼合併至單一 .NET Framework 組件中。</span><span class="sxs-lookup"><span data-stu-id="05ed1-690">A second meaning, which is the focus of this article, involves combining code written in multiple languages into a single .NET Framework assembly.</span></span> 

<span data-ttu-id="05ed1-691">下列範例會建立名為 Utilities.dll 的類別程式庫，其中包含兩個類別 `NumericLib` 和 `StringLib`，藉以說明跨語言互通性。</span><span class="sxs-lookup"><span data-stu-id="05ed1-691">The following example illustrates cross-language interoperability by creating a class library named Utilities.dll that includes two classes, `NumericLib` and `StringLib`.</span></span> <span data-ttu-id="05ed1-692">`NumericLib` 類別是以 C# 撰寫，`StringLib` 類別是以 Visual Basic 撰寫。</span><span class="sxs-lookup"><span data-stu-id="05ed1-692">The `NumericLib` class is written in C#, and the `StringLib` class is written in Visual Basic.</span></span> <span data-ttu-id="05ed1-693">以下是 `StringUtil.vb` 的原始程式碼，當中包含它的 `StringLib` 類別中的單一成員 `ToTitleCase`。</span><span class="sxs-lookup"><span data-stu-id="05ed1-693">Here's the source code for `StringUtil.vb`, which includes a single member, `ToTitleCase`, in its `StringLib` class.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Runtime.CompilerServices

Public Module StringLib
   Private exclusions As List(Of String) 

   Sub New()
      Dim words() As String = { "a", "an", "and", "of", "the" }
      exclusions = New List(Of String)
      exclusions.AddRange(words)
   End Sub

   <Extension()> _
   Public Function ToTitleCase(title As String) As String
      Dim words() As String = title.Split() 
      Dim result As String = String.Empty

      For ctr As Integer = 0 To words.Length - 1
         Dim word As String = words(ctr)
         If ctr = 0 OrElse Not exclusions.Contains(word.ToLower()) Then
            result += word.Substring(0, 1).ToUpper() + _
                      word.Substring(1).ToLower()
         Else
            result += word.ToLower()
         End If
         If ctr <= words.Length - 1 Then
            result += " "             
         End If   
      Next 
      Return result 
   End Function
End Module
```

<span data-ttu-id="05ed1-694">以下是 NumberUtil.cs 的原始程式碼，它會定義擁有 `NumericLib` 和 `IsEven` 這兩個成員的 `NearZero` 類別。</span><span class="sxs-lookup"><span data-stu-id="05ed1-694">Here's the source code for NumberUtil.cs, which defines a `NumericLib` class that has two members, `IsEven` and `NearZero`.</span></span>

```csharp
using System;

public static class NumericLib 
{
   public static bool IsEven(this IConvertible number)
   {
      if (number is Byte ||
          number is SByte ||
          number is Int16 ||
          number is UInt16 || 
          number is Int32 || 
          number is UInt32 ||
          number is Int64)
         return ((long) number) % 2 == 0;
      else if (number is UInt64)
         return ((ulong) number) %2 == 0;
      else
         throw new NotSupportedException("IsEven called for a non-integer value.");
   }

   public static bool NearZero(double number)
   {
      return number < .00001; 
   }
}
```

<span data-ttu-id="05ed1-695">若要將兩個類別封裝在單一組件中，您必須將它們編譯成模組。</span><span class="sxs-lookup"><span data-stu-id="05ed1-695">To package the two classes in a single assembly, you must compile them into modules.</span></span> <span data-ttu-id="05ed1-696">若要將 Visual Basic 原始程式碼檔編譯至模組中，請使用這個命令：</span><span class="sxs-lookup"><span data-stu-id="05ed1-696">To compile the Visual Basic source code file into a module, use this command:</span></span> 

```
vbc /t:module StringUtil.vb 
```

<span data-ttu-id="05ed1-697">若要將 C# 原始程式碼檔編譯至模組中，請使用這個命令：</span><span class="sxs-lookup"><span data-stu-id="05ed1-697">To compile the C# source code file into a module, use this command:</span></span>

```
csc /t:module NumberUtil.cs
```

<span data-ttu-id="05ed1-698">然後使用連結工具 (Link.exe) 將這兩個模組編譯成一個組件：</span><span class="sxs-lookup"><span data-stu-id="05ed1-698">You then use the Link tool (Link.exe) to compile the two modules into an assembly:</span></span> 

```
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

<span data-ttu-id="05ed1-699">接著，下列範例會呼叫 `NumericLib.NearZero` 和 `StringLib.ToTitleCase` 方法。</span><span class="sxs-lookup"><span data-stu-id="05ed1-699">The following example then calls the `NumericLib.NearZero` and `StringLib.ToTitleCase` methods.</span></span> <span data-ttu-id="05ed1-700">請注意，Visual Basic 程式碼和 C# 程式碼都能存取這兩個類別中的方法。</span><span class="sxs-lookup"><span data-stu-id="05ed1-700">Note that both the Visual Basic code and the C# code are able to access the methods in both classes.</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double dbl = 0.0 - Double.Epsilon;
      Console.WriteLine(NumericLib.NearZero(dbl));

      string s = "war and peace";
      Console.WriteLine(s.ToTitleCase());
   }
}
// The example displays the following output:
//       True
//       War and Peace
```

```vb
Module Example
   Public Sub Main()
      Dim dbl As Double = 0.0 - Double.Epsilon
      Console.WriteLine(NumericLib.NearZero(dbl))

      Dim s As String = "war and peace"
      Console.WriteLine(s.ToTitleCase())
   End Sub
End Module
' The example displays the following output:
'       True
'       War and Peace
```

<span data-ttu-id="05ed1-701">若要編譯 Visual Basic 程式碼，請使用這個命令：</span><span class="sxs-lookup"><span data-stu-id="05ed1-701">To compile the Visual Basic code, use this command:</span></span>

```
vbc example.vb /r:UtilityLib.dll
```

<span data-ttu-id="05ed1-702">若要使用 C# 編譯，請將編譯器名稱從 vbc 變更為 csc，並且將副檔名從 .vb 變更為 .cs：</span><span class="sxs-lookup"><span data-stu-id="05ed1-702">To compile with C#, change the name of the compiler from vbc to csc, and change the file extension from .vb to .cs:</span></span>

```
csc example.cs /r:UtilityLib.dll
```

