---
title: "語言獨立性以及與語言無關的元件"
description: "語言獨立性以及與語言無關的元件"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.translationtype: Human Translation
ms.sourcegitcommit: b967d8e55347f44a012e4ad8e916440ae228c8ec
ms.openlocfilehash: 815d9c24c139ef738b256c7bee791756a2fdb3b3
ms.contentlocale: zh-tw
ms.lasthandoff: 03/10/2017

---

# <a name="language-independence-and-language-independent-components"></a>語言獨立性以及與語言無關的元件

.NET 平台與語言無關。 這表示，身為開發人員，您可以使用以 .NET 平台為目標的許多語言之一進行開發，例如 C#、F# 和 Visual Basic。 您可以存取為 .NET 平台開發之類別庫的類型和成員，而不必知道原始撰寫的語言，也不必遵循原始語言的任何慣例。 如果您是元件開發人員，則不論其語言為何，元件都可以由任何 .NET 應用程式存取。

> [!NOTE]
> 本文第一個部分將討論如何建立與語言無關的元件，也就是以任何語言撰寫的應用程式都可以使用的元件。 您也可以從以多種語言撰寫的原始程式碼建立單一元件或應用程式。請參閱本文第二部分的[跨語言互通性](#cross-language-interoperability)。 

若要充分與其他以任何語言撰寫的物件互動，這些物件必須只向呼叫端公開所有語言通用的功能。 這一組通用的功能是由 Common Language Specification (CLS) 所定義，CLS 是套用至所產生之組件的一組規則。 Common Language Specification 是定義在 [ECMA-335 Standard: Common Language Infrastructure](http://www.ecma-international.org/publications/standards/Ecma-335.htm) 的第一篇條款 7 到 11。 

如果您的元件符合 Common Language Specification，則保證其符合 CLS 標準，而且可以從支援 CLS 之任何程式語言所撰寫的組件中的程式碼來加以存取。 您可以在編譯時期將 [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 屬性套用至您的原始程式碼，判斷您的元件是否符合 Common Language Specification。 如需詳細資訊，請參閱 [CLSCompliantAttribute 屬性](#the-clscompliantattribute-attribute)。

本文內容：

* [CLS 合規性規則](#cls-compliance-rules)

    * [類型及類型成員簽章](#types-and-type-member-signatures)

    * [命名慣例](#naming-conventions)
    
    * [類型轉換](#type-conversion)
    
    * [陣列](#arrays)
    
    * [介面](#interfaces)
    
    * [列舉](#enumerations)
    
    * [一般類型成員](#type-members-in-general)
    
    * [成員存取範圍](#member-accessibility)
    
    * [泛型類型及成員](#generic-types-and-members)
    
    * [建構函式](#constructors)
    
    * [屬性](#properties)
    
    * [事件](#events)
    
    * [多載](#overloads)
    
    * [例外狀況](#exceptions)
    
    * [屬性](#attributes)
    
* [CLSCompliantAttribute 屬性](#the-clscompliantattribute-attribute)

* [不同語言之間的互通性](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a>CLS 符合性規則

本節討論建立符合 CLS 標準的元件的規則。 如需規則的完整清單，請參閱 [ECMA-335 Standard: Common Language Infrastructure](http://www.ecma-international.org/publications/standards/Ecma-335.htm) 的第一篇條款 11。

> [!NOTE]
> Common Language Specification 所討論的是適用於下列各項的 CLS 符合性的每個規則：消費者 (以程式設計方式存取符合 CLS 標準之元件的開發人員)、架構 (使用語言編譯器建立符合 CLS 標準之程式庫的開發人員) 和擴充項 (建立工具 (例如可建立符合 CLS 標準之元件的語言編譯器或程式碼剖析器) 的開發人員)。 本文旨在討論適用於架構的規則。 請注意，話雖如此，適用於擴充項的某些規則可能也適用於使用 [Reflection.Emit](xref:System.Reflection.Emit) 建立的組件。 

若要設計與語言無關的元件，您只需要將 CLS 符合性規則套用至元件的公用介面。 您的私用實作並不需要符合規格。 

> [!IMPORTANT]
> CLS 符合性規則只適用於元件的公用介面，不適用於其私用實作。 

例如，除了 [Byte](xref:System.Byte) 以外的不帶正負號的整數都不符合 CLS 標準。 因為下面範例中的 `Person` 類別會公開類型為 [UInt16](xref:System.UInt16) 的 `Age` 屬性，下面程式碼會顯示編譯器警告。

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

您可以藉由將 `Age` 屬性的類型從 `UInt16` 變更為符合 CLS 標準 16 位元帶正負號整數的 [Int16](xref:System.Int16)，使 Person 類別符合 CLS 標準。 您不需要變更 `personAge` 私用欄位的類型。 

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

程式庫的公用介面由下列各項組成：

* 公用類別的定義。

* 公用類別之公用成員的定義，以及衍生類別可存取之成員 (即 protected 成員) 的定義。 

* 公用類別之公用方法的參數和傳回類型，以及衍生類別可存取之方法的參數和傳回類型。 

下表列出 CLS 符合性的規則。 這些規則的英文是一字不差地擷取自 [ECMA-335 Standard: Common Language Infrastructure](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (Copyright 2012 by Ecma International)，然後再翻譯成繁體中文。 這些規則的其他詳細資訊可在下列章節中找到。 

分類 | 請參閱 | 規則 | 規則編號
-------- | --- | ---- | -----------
協助工具選項 | [成員存取範圍](#member-accessibility) | 在覆寫繼承的方法時，不得變更其存取範圍；但覆寫繼承自具有 `family-or-assembly` 存取範圍之不同組件的方法除外。 在這種情況下，覆寫應具有 `family` 存取範圍。 | 10
協助工具選項 | [成員存取範圍](#member-accessibility) | 類型和成員應該有可視性和存取範圍，以致每當成員本身為可見和可存取時，任何成員簽章中的類型也應該是可見和可存取的。 例如，在組件外部是可見的公用方法不得有引數，其類型只有在組件內可見。 構成類型應該有可視性和存取範圍，以致每當成員本身為可見和可存取時，任何成員簽章中所用的具現化泛型類型也應該是可見和可存取的。 例如，存在於組件外部可見成員的簽章中的具現化泛型類型，不得有類型只能在組件內可見的泛型引數。 | 12
陣列 | [陣列](#arrays) | 陣列必須有符合 CLS 標準之類型的項目，而且陣列所有維度的下限必須為零。 只有項目是陣列以及陣列的項目類型是需要在多載之間區別的事實。 當多載根據兩個或多個陣列類型時，項目類型應該是具名類型。 | 16
屬性 | [屬性](#attributes) | 屬性的類型必須為 [System.Attribute](xref:System.Attribute) 或繼承自它的類型。 | 41
屬性 | [屬性](#attributes) | CLS 只允許自訂屬性編碼的子集。 只有以下這些類型允許出現在這些編碼中 (請參閱第四篇)：[System.Type](xref:System.Type)、[System.String](xref:System.String)、[System.Char](xref:System.Char)、[System.Boolean](xref:System.Boolean)、[System.Byte](xref:System.Byte)、[System.Int16](xref:System.Int16)、[System.Int32](xref:System.Int32)、[System.Int64](xref:System.Int64)、[System.Single](xref:System.Single)、[System.Double](xref:System.Double)，以及以符合 CLS 標準之基底整數類型為基礎的所有列舉類型。 | 34
屬性 | [屬性](#attributes) | CLS 不允許公開可見的必要修飾詞 (`modreq`，請參閱第二篇)，不過，允許它不了解的選擇性修飾詞 (`modopt`，請參閱第二篇)。 | 35
建構函式 | [建構函式](#constructors) | 物件建構函式必須先呼叫基底類別的某個執行個體建構函式，才能對繼承的執行個體資料進行任何存取  (這不適用於不需要具有建構函式的實值類型)。  | 21
建構函式 | [建構函式](#constructors) | 除非是做為物件建立程序的一部分，否則是不能呼叫物件建構函式的，而且也不能初始化物件兩次。 | 22
列舉 | [列舉](#enumerations) | 列舉的基礎類型應該是內建 CLS 整數類型，欄位的名稱應該是 "value__"，而且該欄位應該標記為 `RTSpecialName`。 |  7
列舉 | [列舉](#enumerations) | 有兩種不同的列舉，由 [System.FlagsAttribute](xref:System.FlagsAttribute) (請參閱第四篇程式庫) 自訂屬性存在與否表示。 一個表示具名整數值；另一個則表示具名位元旗標 (可合併以產生未命名的值)。 `enum` 的值不限於指定的值。 |  8
列舉 | [列舉](#enumerations) | 列舉的常值靜態欄位必須有列舉本身的類型。 |  9
「事件」 | [事件](#events) | 實作事件的方法必須在中繼資料中標記為 `SpecialName`。 |29
「事件」 | [事件](#events) | 事件及其存取子的存取範圍必須是相同的。 |30
「事件」 | [事件](#events) | 事件的 `add` 和 `remove` 方法，兩者必須同時存在或同時不存在。 |31
「事件」 | [事件](#events) | 事件的 `add` 和 `remove` 方法應各自採用一個其類型會定義事件類型的參數，而且必須是衍生自 [System.Delegate](xref:System.Delegate)。 |32
「事件」 | [事件](#events) | 事件必須遵守特定的命名模式。 在適當的名稱比較中應忽略 CLS 第 29 條規則中所提及的 SpecialName 屬性，並且應遵循識別項規則。  |33
例外狀況 | [例外狀況](#exceptions) | 擲回之物件的類型必須為 [System.Exception](xref:System.Exception)，或繼承自它的類型。 然而，並不需要使用符合 CLS 標準的方法來封鎖其他類型例外狀況的傳播。 | 40
一般 | [CLS 合規性規則](#cls-compliance-rules) | CLS 規則只適用於類型的那些在定義組件以外可存取或可見的部分。 | 1
一般 | [CLS 合規性規則](#cls-compliance-rules) | 不符合 CLS 標準之類型的成員不得標記為符合 CLS 標準。 | 2
泛型 | [泛型類型及成員](#generic-types-and-members) | 巢狀類型應至少有與其封入類型 (Enclosing Type) 一樣多的泛型參數。 巢狀型別中的泛型參數，都與在其封入型別中泛型參數的位置對應。  | 42
泛型 | [泛型類型及成員](#generic-types-and-members) | 根據以上定義的規則，泛型類型的名稱必須編碼非巢狀類型上宣告的型別參數數目或在巢狀類型上新引入的型別參數數目。 | 43
泛型 | [泛型類型及成員](#generic-types-and-members) | 泛型類型必須宣告足夠的限制式，才能保證泛型類型限制式將會符合基底類型或介面上的所有限制式。 | 44
泛型 | [泛型類型及成員](#generic-types-and-members) | 用來做為泛型參數之條件約束的類型，本身也應符合 CLS 標準。 | 45
泛型 | [泛型類型及成員](#generic-types-and-members) | 具現化 (Instantiated) 泛型類型中成員 (包括巢狀型別) 的可視性和存取範圍，必須被視為屬於特定具現化的範圍，而非泛型類型宣告的範圍。 在此假設之下，CLS 第 12 條規則的可視性和存取範圍規則仍然適用。 | 46
泛型 | [泛型類型及成員](#generic-types-and-members) | 對於每個抽象或虛擬泛型方法，都必須具有預設具象 (非抽象) 實作 | 47
介面 | [介面](#interfaces) | 符合 CLS 標準的介面不可要求不符合 CLS 標準之方法的定義來實作它們。 | 18
介面 | [介面](#interfaces) | 符合 CLS 標準的介面不可定義靜態方法，也不可定義欄位。 | 19
Members | [一般類型成員](#type-members-in-general) | 全域靜態欄位和方法不符合 CLS 標準。 | 36
成員 | -- | 常值靜態欄位的值是透過使用欄位初始化中繼資料來指定。 符合 CLS 標準的常值必須具有欄位初始化中繼資料所指定的值，這個中繼資料與常值有完全相同的類型 (如果該常值是 `enum`，則為基礎類型)。 | 13
Members | [一般類型成員](#type-members-in-general) | vararg 條件約束不是 CLS 的一部分，CLS 所支援的唯一呼叫慣例是標準的 Managed 呼叫慣例。 | 15
命名規範 | [命名慣例](#naming-conventions) | 組件必須遵守 Unicode Standard 3.0 技術報告編號 15 附錄 7 的各項規則，它規定可以啟始並包含在識別項中的字元集，[Unicode Normalization Forms](http://www.unicode.org/unicode/reports/tr15/tr15-18.html) 線上提供這份報告。 識別項應使用 Unicode Normalization Form C 所定義的標準格式。基於 CLS 目的，如果其小寫對應 (如 Unicode 不區分地區設定、一對一小寫對應所指定) 相同，則兩個識別項相同。 也就是依據 CLS，兩個識別項若要被視為不同，不只是大小寫，還要有其他不同之處。 不過，為了覆寫繼承的定義，CLI 需要使用原始宣告的確切編碼。 | 4
多載化 | [命名慣例](#naming-conventions) | 在符合 CLS 標準的範圍中引入的所有名稱，除了名稱完全相同且透過多載解析的情況之外，都必須是不同的獨立類型。 也就是說，CTS 允許單一類型對方法和欄位使用同樣的名稱，但 CLS 不允許。 | 5
多載化 | [命名慣例](#naming-conventions) | 即使 CTS 允許區別不同簽章，還是必須單獨依據識別項比較來區別欄位和巢狀類型的不同。 經由識別項比較之後，具有相同名稱的方法、屬性和事件不可僅以傳回型別做區分，除非 CLS 第 39 條規則中另有指定 | 6
多載化 | [多載](#overloads) | 只有屬性和方法可以多載。 | 37
多載化 | [多載](#overloads) |屬性和方法只可以根據其參數數目和類型多載，除了名為 `op_Implicit` 和 `op_Explicit` 的轉換運算子，也可以根據其傳回類型多載。 | 38
多載化 | -- | 如果在有相同名稱的類型中宣告兩個或更多符合 CLS 標準的方法，則對一組特定的類型具現化來說，它們具有相同的參數和傳回型別，而且所有這些方法在語意上與這些類型具現化相等。 | 48
屬性 | [屬性](#properties) | 實作屬性之 getter 和 setter 方法的方法在中繼資料中應標記為 `SpecialName`。 | 24
屬性 | [屬性](#properties) | 屬性的存取子必須全部為 static、全部為 virtual 或全部為 instance。 | 26
屬性 | [屬性](#properties) | 屬性的類型應是 getter 的傳回型別和 setter 最後一個引數的類型。 屬性參數的類型必須是 getter 參數的類型和 setter 除了最後一個參數之外的所有參數類型。 所有這些類型都必須符合 CLS 規範，而且不能是 Managed 指標 (也就是，不能以傳址方式傳遞)。 | 27
屬性 | [屬性](#properties) | 屬性必須遵守特定的命名模式。 在適當的名稱比較中應忽略 CLS 第 24 條規則中所提及的 `SpecialName` 屬性，並且應遵循識別項規則。 屬性必須有 getter 方法、setter 方法或兩者皆有。 | 28
類型轉換 | [類型轉換](#type-conversion) | 如果有提供 op_Implicit 或 op_Explicit，則必須提供替代方式來提供強制型轉。 | 39
類型 | [類型及類型成員簽章](#types-and-type-member-signatures) | Boxed 實值類型不符合 CLS 標準。 | 3
類型 | [類型及類型成員簽章](#types-and-type-member-signatures) | 簽章中出現的所有類型都必須符合 CLS 標準。 構成具現化泛型類型的所有類型都必須符合 CLS 標準。 | 11
類型 | [類型及類型成員簽章](#types-and-type-member-signatures) | 具型別的參考不符合 CLS 標準 | 14
類型 | [類型及類型成員簽章](#types-and-type-member-signatures) | Unmanaged 指標類型不符合 CLS 標準。 | 17
類型 | [類型及類型成員簽章](#types-and-type-member-signatures) | 符合 CLS 標準的類別、實值型別和介面不能要求不符合 CLS 標準的成員實作 | 20
類型 | [類型及類型成員簽章](#types-and-type-member-signatures) | [System.Object](xref:System.Object) 符合 CLS 標準。 任何其他符合 CLS 標準的類別也都必須繼承自符合 CLS 標準的類別。 | 23

### <a name="types-and-type-member-signatures"></a>類型和類型成員簽章

[System.Object](xref:System.Object) 類型符合 CLS 標準，並且是 .NET Framework 型別系統中所有物件類型的基底類型。 .NET Framework 中的繼承若不是隱含的 (例如，[String](xref:System.String) 類別隱含自繼承 `Object` 類別)，就是明確的 (例如，[CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) 類別明確繼承自 [ArgumentException](xref:System.ArgumentException) 類別，後者又明確繼承自 [Exception](xref:System.Exception) 類別)。 若要讓衍生類型符合 CLS 標準，其基底類型必須符合 CLS 標準。 

下面範例會示範其基底類型不符合 CLS 標準的衍生類型。 它會定義基底 `Counter` 類別，這個類別使用不帶正負號的 32 位元整數做為計數器。 因為該類別會藉由包裝不帶正負號的整數提供計數器功能，所以該類別會標記為不符合 CLS 標準。 結果，衍生的類別 `NonZeroCounter` 也不符合 CLS 標準。 

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

成員簽章中出現的所有類型 (包括方法的傳回型別或屬性類型) 都必須符合 CLS 標準。 此外，如果是泛型類型： 

* 構成具現化泛型類型的所有類型都必須符合 CLS 標準。

* 所有用來做為泛型參數之限制式的類型，都必須符合 CLS 標準。 

.NET 的[一般型別系統](common-type-system.md)包含了幾個內建類型，這些內建類型直接受到 Common Language Runtime 的支援，並且在組譯碼的中繼資料中以特殊方式進行編碼。 在這些內建類型中，下表所列的類型符合 CLS 標準。 


符合 CLS 標準的類型 | 說明
------------------ | -----------
[Byte](xref:System.Byte) | 8 位元不帶正負號的整數 
[Int16](xref:System.Int16) | 16 位元帶正負號的整數 
[Int32](xref:System.Int32) | 32 位元帶正負號的整數 
[Int64](xref:System.Int64) | 64 位元帶正負號的整數
[Single](xref:System.Single) | 單精確度浮點值
[Double](xref:System.Double) | 雙精確度浮點值
[布林值](xref:System.Boolean) | true 或 false 實值型別 
[Char](xref:System.Char) | UTF-16 編碼程式碼單位
[Decimal](xref:System.Decimal) | 非浮點十進位數字
[IntPtr](xref:System.IntPtr) | 平台定義大小的指標或控制代碼
[String](xref:System.String) | 零個、一個或多個 Char 物件的集合 
 
下表所列的內建類型不符合 CLS 標準。


不符合標準的類型 | 描述 | 符合 CLS 標準的替代項目
------------------ | ----------- | -------------------------
[SByte](xref:System.SByte) | 8 位元帶正負號的整數資料類型 | [Int16](xref:System.Int16)
[UInt16](xref:System.UInt16) | 16 位元不帶正負號的整數 | [Int32](xref:System.Int32)
[UInt32](xref:System.UInt32) | 32 位元不帶正負號的整數 | [Int64](xref:System.Int64)
[UInt64](xref:System.UInt64) | 64 位元不帶正負號的整數 | [Int64](xref:System.Int64) (可能溢位)、[BigInteger](xref:System.Numerics.BigInteger) 或 [Double](xref:System.Double)
[UIntPtr](xref:System.UIntPtr) | 不帶正負號的指標或控制代碼 | [IntPtr](xref:System.IntPtr)
 
 .NET Framework 類別庫或其他類別庫可能包含不符合 CLS 標準的其他類型，例如： 
 
 * Boxed 實值類型。 下面 C# 範例會建立類別，具有類型為 `int` *的公用屬性，名為 `Value`。由於 `int`* 為 Boxed 實值型別，因此編譯器將其標示為不符合 CLS 標準。

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

* 具類型參考，是一種含有物件參考和類型參考的特殊建構。

如果類型不符合 CLS 標準，您應該套用 [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 屬性，並將值為 `false` 的 *isCompliant* 參數指派給它。 如需詳細資訊，請參閱 [CLSCompliantAttribute 屬性](#the-clscompliantattribute-attribute)一節。  

下面範例說明在方法簽章和泛型類型具現化中的 CLS 符合性問題。 它會定義 `InvoiceItem` 類別，包含 [UInt32](xref:System.UInt32) 類型的屬性、[Nullable(Of UInt32)](xref:System.Nullable%601) 類型的屬性，以及參數類型為 `UInt32` 和 `Nullable(Of UInt32)` 的建構函式。 當您嘗試編譯這個範例時，會收到四個編譯器警告。

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

若要排除編譯器警告，請將 `InvoiceItem` 公用介面中不符合 CLS 標準的類型取代為與符合標準的類型：

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

除了列出的特定類型之外，有些分類的類型也不符合 CLS 標準。 這些包括 Unmanaged 指標類型和函式指標類型。 下面範例會產生編譯器警告，因為它使用整數指標建立整數陣列。 

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

如果是符合 CLS 標準的抽象類別 (也就是在 C# 中標記為 `abstract`)，類別的所有成員也必須符合 CLS 標準。 

### <a name="naming-conventions"></a>命名規範

由於某些程式語言不區分大小寫，識別項 (例如命名空間、類型和成員的名稱) 必須透過區分大小寫以外的方式產生差異。 如果兩個識別項的小寫對應是相同的，則這兩個識別項是視為相等。 下面 C# 範例會定義兩個公用類別：`Person` 和 `person`。 因為只有大小寫不同，所以 C# 編譯器會將其標示為不符合 CLS 標準。 

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

程式語言識別項，例如命名空間、類型和成員的名稱，必須符合 [Unicode Standard 3.0 Technical Report 15 的 Annex 7](http://www.unicode.org/reports/tr15/tr15-18.html)。 這表示：

* 識別項的第一個字元可以是任何 Unicode 大寫字母、小寫字母、標題大寫字母、修飾詞字母、其他字母或字母數字。 如需 Unicode 字元分類的資訊，請參閱 [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) 列舉。 

* 接下來的字元可以來自和第一個字元相同的任何分類，而且也可以包含非間距記號、間距組合記號、十進位數字、連接子標點符號和格式化程式碼。 

在您比較識別項之前，應該先篩掉格式化程式碼，並將識別項轉換為 Unicode 正規化表單 C，因為單一字元可由多個 UTF 16 編碼字碼單位表示。 產生和 Unicode 正規化表單 C 相同的字碼單位的字元順序不符合 CLS 標準。 下面範例會定義名為 `Å` 的屬性和名為 `Å` 的第二個屬性。前者包含 ANGSTROM SIGN 字元 (U+212B)，後者包含 LATIN CAPITAL LETTER A WITH RING ABOVE 字元 (U+00C5)。 C# 編譯器會將原始程式碼標示為不符合 CLS 標準。

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

特定範圍內的成員名稱 (例如組件中的命名空間、命名空間中的類型或類型中的成員)，除了透過多載解析的名稱以外，都必須是唯一的。 這個需求比一般類型系統的需求更嚴格，後者允許在範圍內的多個成員具有相同名稱，只要它們是不同的類型成員 (例如，一個是方法，一個是欄位)。 特別是，如果是類型成員： 

* 欄位和巢狀類型只有依據名稱做區別。 

* 具有相同名稱的方法、屬性和事件不可僅以傳回類型做區分。 

下面範例說明成員名稱在其範圍內必須是唯一的這個需求。 它會定義名為 `Converter` 的類別，其中包含四個名為 `Conversion` 的成員。 三個是方法，一個是屬性。 包含 `Int64` 參數的方法具有唯一的名稱，但含有 `Int32` 參數的兩個方法則沒有唯一名稱，因為傳回值不視為成員簽章的一部分。 `Conversion` 屬性也違反這項需求，因為屬性不能與多載方法同名。 

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

個別語言包含唯一的關鍵字，因此以 Common Language Runtime 為目標的語言也必須提供一些參考符合關鍵字之識別碼 (例如類型名稱) 的機制。 例如，`case` 在 C# 和 Visual Basic 中都是關鍵字。 不過，下面 Visual Basic 範例可以使用左右大括號，讓名稱為 `case` 的類別與 `case` 關鍵字有所區分。 否則，這個範例會產生錯誤訊息「關鍵字做為識別項無效」，而無法編譯。 

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

下面 C# 範例可以使用 @ 符號區分識別項與語言關鍵字，以具現化 `case` 類別。 若沒有它，C# 編譯器會顯示兩個錯誤訊息：「必須是類型」和「無效的運算式詞彙 'case'」。 

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

### <a name="type-conversion"></a>類型轉換

Common Language Specification 定義兩個轉換運算子：

* `op_Implicit`，用於不會導致資料或精確度遺失的擴展轉換。 例如，[Decimal](xref:System.Decimal) 結構包含多載 `op_Implicit` 運算子，以便將整數類型的值和 [Char](xref:System.Char) 值轉換為 `Decimal` 值。 

* `op_Explicit`，用於可能會導致大小 (值轉換為某個範圍較小的值) 或精確度遺失的縮小轉換。 例如，`Decimal` 結構包含多載 `op_Explicit` 運算子，以便將 [Double](xref:System.Double) 和 [Single](xref:System.Single) 值轉換為 `Decimal`，以及將 `Decimal` 值轉換為整數值 `Double`、`Single` 和 `Char`。 

不過，並非所有語言都支援運算子多載或自訂運算子定義。 如果您選擇實作這些轉換運算子，也應該提供執行轉換的替代方式。 建議您提供 `From`Xxx 和 `To`Xxx 方法。 

下面範例定義了符合 CLS 標準的隱含和明確轉換。 它會建立 `UDouble` 類別，表示帶正負號的雙精確度浮點數。 它支援從 `UDouble` 到 `Double` 的隱含轉換，以及支援從 `UDouble` 到 `Single`、`Double` 到 `UDouble` 以及 `Single` 到 `UDouble` 的明確轉換。 它也會定義 `ToDouble` 方法做為隱含轉換運算子的替代方法，以及定義 `ToSingle`、`FromDouble` 和 `FromSingle` 方法做為明確轉換運算子的替代方法。 

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

### <a name="arrays"></a>陣列

符合 CLS 標準的陣列會遵守下列規則： 

* 陣列所有維度的下限都必須為零。 下面範例會建立下限為一、不符合 CLS 標準的陣列。 請注意，儘管 [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 屬性存在，編譯器並不會偵測出 `Numbers.GetTenPrimes` 方法傳回的陣列不符合 CLS 標準。 

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

* 所有陣列項目都必須包含符合 CLS 標準的類型。 下面範例會定義傳回不符合 CLS 標準的陣列的兩個方法。 第一個會傳回 [UInt32](xref:System.UInt32) 值的陣列。 第二個傳回包含 [Int32](xref:System.Int32) 和 `UInt32` 值的 [Object](xref:System.Object) 陣列。 雖然編譯器會因為其 `UInt32` 類型而將第一個陣列識別為不符合標準，但是無法辨識出第二個陣列包含了不符合 CLS 標準的項目。 

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

* 具有陣列參數之方法的多載解析是根據它們是陣列和其項目類型。 因此，下面多載 `GetSquares` 方法的定義符合 CLS 標準。 

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

### <a name="interfaces"></a>介面

符合 CLS 標準的介面可以定義屬性、事件和虛擬方法 (沒有實作的方法)。 符合 CLS 標準的介面不可含有下列任何一項： 

* 靜態方法或靜態欄位。 如果您在介面中定義了靜態成員，C# 編譯器會產生編譯器錯誤。 

* 欄位。 如果您在介面中定義了欄位，C# 編譯器會產生編譯器錯誤。

* 不符合 CLS 標準的方法。 例如，下面介面定義包含標記為符合 CLS 標準的方法 `INumber.GetUnsigned`。 這個範例會產生編譯器警告。 

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

  由於這項規則，在實作不符合 CLS 標準的成員時並不需要符合 CLS 標準的類型。 如果符合 CLS 標準的架構沒有公開實作不符合 CLS 標準介面的類別，也應該提供所有不符合 CLS 標準成員的具象實作。 

符合 CLS 標準的語言編譯器也必須允許類別提供在多個介面中具有相同名稱及簽章的成員實作。 C# 支援明確介面實作，以提供相同具名方法的不同實作。 下面範例會透過定義實作 `Temperature` 和 `ICelsius` 介面做為明確介面實作的 `IFahrenheit` 類別，來說明這種情況。 

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

### <a name="enumerations"></a>列舉

符合 CLS 標準的列舉必須遵守下列規則： 

* 列舉的基礎類型必須是內建符合 CLS 標準的整數 ([Byte](xref:System.Byte)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32) 或 [Int64](xref:System.Int64))。 例如，下面程式碼會嘗試定義其基礎類型為 [UInt32](xref:System.UInt32) 的列舉，並產生編譯器警告。 

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

* 列舉類型必須具有以 `Value__` 屬性標記的單一執行個體欄位，名稱為 `FieldAttributes.RTSpecialName`。 這可讓您隱含參考欄位值。 

* 列舉會包含其類型符合列舉本身類型的常值靜態欄位。 例如，如果您定義含有 `State` 和 `State.On` 值的 `State.Off` 列舉，則 `State.On` 和 `State.Off` 都是常值靜態欄位，其類型為 `State`。 

* 列舉有兩種： 
    
    * 表示一組互斥具名整數值的列舉。 這個列舉類型是由缺少 [System.FlagsAttribute](xref:System.FlagsAttribute) 自訂屬性來表示。
    
    * 表示一組可合併產生未命名值之位元旗標的列舉。 這個列舉類型是由存在 [System.FlagsAttribute](xref:System.FlagsAttribute) 自訂屬性來表示。
    
 如需詳細資訊，請參閱 [Enum](xref:System.Enum) 結構的說明文件。 

* 列舉的值不限於其指定值的範圍。 換句話說，列舉中的值範圍即是其基礎值的範圍。 您可以使用 `Enum.IsDefined` 方法來判斷某指定值是否為列舉的成員。 

### <a name="type-members-in-general"></a>一般類型成員

Common Language Specification 要求所有欄位和方法都必須當做特定類別的成員來加以存取。 因此，全域靜態欄位和方法 (也就是除了類型外定義的靜態欄位或方法) 不符合 CLS 標準。 如果您嘗試在原始程式碼中包含全域欄位或方法，則 C# 編譯器會產生編譯器錯誤。 

Common Language Specification 只支援標準的 Managed 呼叫慣例。 它不支援 Unmanaged 呼叫慣例和具有變數引數清單 (以 `varargs` 關鍵字標記) 的方法。 如果是與標準 Managed 呼叫慣例相容的變數引數清單，請使用 [ParamArrayAttribute](xref:System.ParamArrayAttribute) 屬性或個別語言的實作，例如 C# 中的 `params` 關鍵字或 Visual Basic 中的 `ParamArray` 關鍵字。 

### <a name="member-accessibility"></a>成員存取範圍

覆寫繼承的成員無法變更該成員的存取範圍。 例如，衍生類別中的私用方法無法覆寫基底類別中的公用方法。 有一個例外：由不同組件中的類型所覆寫的某個組件中的 `protected internal` (在 C# 中) 或 `Protected Friend` (在 Visual Basic 中) 成員。  在這種情況下，覆寫的存取範圍是 `Protected`。 

下面範例說明當 [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 屬性是設定為 `true`，並且 `Person` (衍生自 `Animal` 的類別) 嘗試將 `Species` 屬性的存取範圍從 public (公用) 變更為 private (私用) 時，所產生的錯誤。 如果它的存取範圍變更為 public (公用)，則此範例會編譯成功。 

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

每當成員本身為可存取時，成員簽章中的類型也必須是可存取的。 例如，這表示 public 成員不能包含類型為 private、protected 或 internal 的參數。 下面範例說明當 `StringWrapper` 類別建構函式公開內部 `StringOperationType` 列舉值，決定如何包裝字串值時，所產生的編譯器錯誤。 

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

### <a name="generic-types-and-members"></a>泛型類型和成員

巢狀類型一律至少具有與其封入類型 (Enclosing Type) 一樣多的泛型參數。 這些在位置上對應於封入類型中的泛型參數。 泛型類型也可以包含新的泛型參數。 

個別語言的語法可能會隱藏包含類型和其巢狀類型的泛型類型參數之間的關聯性。 在下面範例中，泛型類型 `Outer<T>` 包含兩個巢狀類別：`Inner1A` 和 `Inner1B<U>`。 對 `ToString` 方法 (每個類別都是從 `Object.ToString` 繼承這個方法) 的呼叫，顯示出每個巢狀類別都會包含其所包含類別的型別參數。 

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

泛型型別名稱的編碼格式為 *name*'*n*，其中 *name* 是類型名稱，*`* 是字元常值，而 *n* 則是在類型上宣告的參數數目，或是巢狀泛型型別中，新引入之型別參數的數目。 這個泛型類型名稱編碼方式主要適用於使用反映來存取程式庫中符合 CLS 標準之泛型類型的開發人員。 

如果限制式是套用至泛型類型，則任何當做限制式使用的類型也必須符合 CLS 標準。 下面範例定義了不符合 CLS 標準的類別 (名稱為 `BaseClass`) 以及類型參數必須衍生自 `BaseCollection` 的泛型類別 (名稱為 `BaseClass`)。 但是因為 `BaseClass` 不符合 CLS 標準，所以編譯器會發出警告。 

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

如果泛型類型是衍生自泛型基底類型，就必須重新宣告任何限制式，才能保證同時符合基底類型上的限制式。 下面範例會定義可代表任何數字類型的 `Number<T>`。 它也會定義表示浮點值的 `FloatingPoint<T>` 類別。 不過，因為未將 `Number<T>` (其中 T 必須是實值類型) 的限制式套用至 `FloatingPoint<T>`，所以無法編譯原始程式碼。

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

如果將該條件約束加入至 `FloatingPoint<T>` 類別，則這個範例會編譯成功。

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

Common Language Specification 會對巢狀類型和保護的成員施加保守的每一個具現化模型。 開放式泛型類型無法公開其簽章包含受保護巢狀泛型類型的特定具現化的欄位或成員。 可擴充泛型基底類別或介面之特定具現化的非泛型類型，無法公開其簽章包含受保護巢狀泛型類型的不同具現化的欄位或成員。

下列範例會定義泛型型別 `C1<T>` 和受保護的類別 `C1<T>.N`。 `C1<T>` 有兩個方法：`M1` 和 `M2`。 不過，`M1` 不符合 CLS 標準，因為它會嘗試從 `C1<T>` 傳回 `C1<int>.N` 物件。 第二個類別 `C2` 是衍生自 `C1<long>`。 它具有兩個方法：`M3` 和 `M4`。 因為 `M3` 會嘗試傳回 `C1<long>` 的 `C1<int>.N` 物件，所以不符合 CLS 標準。 請注意，語言編譯器的限制可能還要更嚴格。 在此範例中，Visual Basic 會在其嘗試編譯 `M4` 時顯示錯誤。 

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

### <a name="constructors"></a>建構函式

符合 CLS 標準之類別和結構中的建構函式必須遵守下列規則： 

* 衍生類別的建構函式必須先呼叫基底類別的建構函式，才能存取繼承的執行個體資料。 因為衍生類別不會繼承基底類別建構函式，所以才有這項需求。 此規則不會套用至結構，因為結構不支援直接繼承。 

  通常，編譯器會獨立強制執行此規則，而不需考慮 CLS 符合性，如下面範例所示。 它會建立衍生自 `Person` 類別的 `Doctor` 類別，但是 `Doctor` 類別無法呼叫 `Person` 類別建構函式來初始化繼承的執行個體欄位。 

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
    
* 物件建構函式除了建立物件之外，無法被呼叫。 此外，物件無法初始化兩次。 例如，這表示 `Object.MemberwiseClone` 不能呼叫建構函式。  

### <a name="properties"></a>屬性

符合 CLS 標準的類型中的屬性必須遵守下列規則：

* 屬性必須有 setter、getter 或兩者皆有。 在組件中，這些會實作為特殊方法，亦即在組件的中繼資料中，會以個別的方法出現 (getter 會命名為 `get`\_*propertyname*，setter 會命名為 `set*\_*propertyname*) marked as `SpecialName'。 C# 編譯器會自動強制執行這項規則，而不需要套用 [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 屬性。 

* 屬性的類型是屬性 getter 的傳回型別和 setter 的最後一個引數。 這些類型必須符合 CLS 標準，而且引數不能以傳址方式指派給屬性 (也就是它們不能是 Managed 指標)。 

* 如果屬性同時有 getter 和 setter，則兩者都必須是虛擬、靜態或者都是執行個體。 C# 編譯器會透過屬性定義語法，來自動強制執行這項規則。 

### <a name="events"></a>事件

事件是由它的名稱和類型來定義。 事件類型是用來表示事件的委派。 例如，`DbConnection.StateChange` 事件的類型為 `StateChangeEventHandler`。 除了事件本身之外，具有以事件名稱為根據之名稱的三個方法會提供事件的實作，並且在組件的中繼資料中標記為 `SpecialName`： 

* 用於加入事件處理常式的方法，名稱為 `add`_*EventName*。 例如，`DbConnection.StateChange` 事件的事件訂閱方法是命名為 `add_StateChange`。 

* 用於移除事件處理常式的方法，名稱為 `remove`_*EventName*。 例如，`DbConnection.StateChange` 事件的移除方法是命名為 `remove_StateChange`。

* 用於表示事件已發生的方法，名稱為 `raise`_*EventName*。 

> [!NOTE]
> 大部分與事件有關的 Common Language Specification 規則都是由語言編譯器實作，而且對元件開發人員而言是透明化的。 

用於加入、移除及引發事件的方法必須具有相同的存取範圍。 它們也必須全部是靜態、執行個體或虛擬的。 用於加入和移除事件的方法具有一個類型為事件委派類型的參數。 加入和移除方法兩者必須同時存在或同時不存在。 

下面範例定義了符合 CLS 標準的類別 (名稱為 `Temperature`)，如果兩個讀數之間的溫度變更等於或超過臨界值，這個類別會引發 `TemperatureChanged` 事件。 `Temperature` 類別會明確地定義 `raise_TemperatureChanged` 方法，讓它可以選擇性地執行事件處理常式。

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

### <a name="overloads"></a>Overloads

Common Language Specification 會對多載成員施加下列需求： 

* 成員可以根據參數的數目和任何參數的類型來多載。 辨別多載時，不會考慮呼叫慣例、傳回型別、套用至方法或其參數的自訂修飾詞，以及參數是以傳值或傳址方式傳遞。 如需範例，請參閱[命名慣例](#naming-conventions)一節中，要求範圍內的名稱必須是唯一名稱的程式碼。 

* 只有屬性和方法可以多載。 欄位和事件不可多載。 

* 泛型方法可以根據其泛型參數的數目來多載。 

> [!NOTE]
>多載解析時傳回值不會被視為方法簽章的一部分，這個規則的例外是 `op_Explicit` 和 `op_Implicit` 運算子。 這兩個運算子可以根據其參數以及其傳回值來多載。 

### <a name="exceptions"></a>例外狀況

例外狀況物件必須衍生自 [System.Exception](xref:System.Exception)，或衍生自另一個衍生自 `System.Exception` 的類型。 下面範例說明在名為 `ErrorClass` 的自訂類別用於例外狀況處理時，所造成的編譯器錯誤。

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

若要更正這個錯誤，`ErrorClass` 類別必須繼承自 `System.Exception`。 此外，還必須覆寫 Message 屬性。 下面範例會修正這些錯誤，以定義符合 CLS 標準的 `ErrorClass` 類別。  

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

### <a name="attributes"></a>屬性

在 .NET Framework 組件中，自訂屬性會提供可擴充機制，用於儲存自訂屬性和擷取程式設計物件 (例如組件、類型、成員和方法參數) 的相關中繼資料。 自訂屬性必須衍生自 [System.Attribute](xref:System.Attribute)，或從衍生自 `System.Attribute` 的類型衍生而來。

下面範例違反這項規則。 它會定義不是衍生自 `NumericAttribute` 的 `System.Attribute` 類別 請注意，只有在套用不符合 CLS 標準的屬性時，而不是在定義類別時，才會產生編譯器錯誤。 

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

建構函式或符合 CLS 標準的屬性 (attribute) 的屬性 (property) 只能公開下列類型：

* [布林值](xref:System.Boolean)

* [Byte](xref:System.Byte)

* [Char](xref:System.Char)

* [Double](xref:System.Double)

* [Int16](xref:System.Int16)

* [Int32](xref:System.Int32)

* [Int64](xref:System.Int64)

* [Single](xref:System.Single)

* [String](xref:System.String)

* [Type](xref:System.Type)

* 基礎類型為 `Byte`、`Int16`、`Int32` 或 `Int64` 的任何列舉類型。 

下面範例會定義衍生自 [Attribute](xref:System.Attribute) 的 `DescriptionAttribute` 類別。 類別建構函式具有類型為 `Descriptor` 的參數，因此類別不符合 CLS 標準。 請注意，C# 編譯器會發出警告，但編譯會成功。 

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

## <a name="the-clscompliantattribute-attribute"></a>CLSCompliantAttribute 屬性

[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 屬性用於表示程式項目是否符合 Common Language Specification。 `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` 建構函式包含單一必要參數 *isCompliant*，表示程式項目是否符合 CLS 標準。 

在編譯時間，編譯器會偵測到假設符合 CLS 標準之不符合標準的項目，並發出警告。 對於明確宣告為不符合標準的類型或成員，編譯器不會發出警告。 

元件開發人員可以透過兩種方式使用 `CLSCompliantAttribute` 屬性： 

* 定義元件所公開符合 CLS 標準的公用介面的組件和不符合 CLS 標準的組件。 當該屬性是用來將特定程式項目標記為符合 CLS 標準時，使用它可以確保目標為 .NET Framework 的所有語言和工具都可以存取這些項目。 

* 確定元件庫的公用介面只公開符合 CLS 標準的程式項目。 如果項目不符合 CLS 標準，編譯器通常會發出警告。

> [!WARNING]
> 在某些情況下，語言編譯器會強制執行符合 CLS 標準的規則，而不論是否使用 `CLSCompliantAttribute` 屬性。 例如，定義介面的 `*static` 成員會違反 CLS 規則。 不過，如果您在介面中定義 `*static` 成員，C# 編譯器會顯示錯誤訊息，並且無法編譯應用程式。

`CLSCompliantAttribute` 屬性標記著具有 `AttributeTargets.All` 值的 [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) 屬性。 此值可讓您將 `CLSCompliantAttribute` 屬性套用至任何程式項目，包括組件、模組、類型 (類別、結構、列舉、介面和委派)、類型成員 (建構函式、方法、屬性、欄位和事件)、參數、泛型參數和傳回值。 不過，在實務中，您應該只將該屬性套用至組件、類型和類型成員。 否則，當編譯器在您的程式庫的公用介面中遇到不符合標準的參數、泛型參數或傳回值時，會忽略該屬性並繼續產生編譯器警告。  

`CLSCompliantAttribute` 屬性的值是由內含的程式項目繼承。 例如，如果組件是標記為符合 CLS 標準，它的類型也會符合 CLS 標準。 如果類型是標記為符合 CLS 標準，其巢狀類型及成員也會符合 CLS 標準。 

您可以將 `CLSCompliantAttribute` 屬性套用至內含的程式項目，以明確覆寫繼承的符合性。 例如，您可以使用 *isCompliant* 值為 `false` 的 `CLSCompliantAttribute` 屬性，在符合標準的組件中定義不符合標準的類型，而且可以使用 *isComplian* 值為 `true` 的屬性，在不符合標準的組件中定義符合標準的類型。 您也可以在符合標準的類型中定義不符合標準的成員。 然而，不符合標準的類型不能具有符合標準的成員，因此您無法使用 *isCompliant* 值為 `true` 的屬性來覆寫不符合標準之類型的繼承。 

當您開發元件時，一定要使用 `CLSCompliantAttribute` 屬性來指出您的組件、其類型及其成員是否符合 CLS 標準。 

若要建立符合 CLS 標準的元件： 

1. 使用 `CLSCompliantAttribute` 將組件標記為符合 CLS 標準。

2. 將不符合 CLS 標準之組件中公開的任何類型標記為不符合標準。 

3. 將符合 CLS 標準之類型中公開的任何成員標記為不符合標準。 

4. 為不符合 CLS 標準的成員提供符合 CLS 標準的替代項目。 

如果成功標記了所有您不符合標準的類型和成員，則編譯器應該不會發出任何不符合標準的警告。 不過，您應該指出哪些成員不符合 CLS 標準，並在產品文件中列出符合 CLS 標準的替代項目。 

下面範例會使用 `CLSCompliantAttribute` 屬性來定義符合 CLS 標準的組件和類型 `CharacterUtilities`，該類型有兩個不符合 CLS 標準的成員。 由於兩個成員都是以 `CLSCompliant(false)` 屬性來標記，因此編譯器沒有產生警告。 該類別也為這兩個方法提供符合 CLS 標準的替代項目。 通常，我們會將兩個多載加入至 `ToUTF16` 方法，以提供符合 CLS 標準的替代項目。 不過，因為方法無法根據傳回值來多載，所以符合 CLS 標準之方法的名稱與不符合 CLS 標準之方法的名稱不同。  

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

如果您要開發的是應用程式而非程式庫 (也就是說，如果您不會公開可由其他應用程式開發人員使用的類型或成員)，則您的應用程式所使用之程式項目的 CLS 符合性，只有在您的語言不支援這些項目時才需要考慮。 在這種情況下，當您嘗試使用不符合 CLS 標準的項目時，您的語言編譯器會產生錯誤。 

## <a name="cross-language-interoperability"></a>跨語言互通性

語言獨立性的意義可能有許多種。 其中一種意義是指能夠在以某種語言撰寫的應用程式中，順利使用以另一種語言撰寫的類型。 第二種意義則是本文重點所在，是指將多種語言撰寫的程式碼合併至單一 .NET Framework 組件中。 

下列範例會建立名為 Utilities.dll 的類別程式庫，其中包含兩個類別 `NumericLib` 和 `StringLib`，藉以說明跨語言互通性。 `NumericLib` 類別是以 C# 撰寫，`StringLib` 類別是以 Visual Basic 撰寫。 以下是 `StringUtil.vb` 的原始程式碼，當中包含它的 `StringLib` 類別中的單一成員 `ToTitleCase`。

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

以下是 NumberUtil.cs 的原始程式碼，它會定義擁有 `NumericLib` 和 `IsEven` 這兩個成員的 `NearZero` 類別。

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

若要將兩個類別封裝在單一組件中，您必須將它們編譯成模組。 若要將 Visual Basic 原始程式碼檔編譯至模組中，請使用這個命令： 

```
vbc /t:module StringUtil.vb 
```

若要將 C# 原始程式碼檔編譯至模組中，請使用這個命令：

```
csc /t:module NumberUtil.cs
```

然後使用連結工具 (Link.exe) 將這兩個模組編譯成一個組件： 

```
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

接著，下列範例會呼叫 `NumericLib.NearZero` 和 `StringLib.ToTitleCase` 方法。 請注意，Visual Basic 程式碼和 C# 程式碼都能存取這兩個類別中的方法。

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

若要編譯 Visual Basic 程式碼，請使用這個命令：

```
vbc example.vb /r:UtilityLib.dll
```

若要使用 C# 編譯，請將編譯器名稱從 vbc 變更為 csc，並且將副檔名從 .vb 變更為 .cs：

```
csc example.cs /r:UtilityLib.dll
```


