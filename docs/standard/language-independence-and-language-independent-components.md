---
title: 語言獨立性以及與語言無關的元件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- language interoperability
- Common Language Specification
- cross-language interoperability
- CLS
- runtime, language interoperability
- common language runtime, language interoperability
ms.assetid: 4f0b77d0-4844-464f-af73-6e06bedeafc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b40e12c7cb077d6ef128d4ee1aada6086cb9c1d
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "57846463"
---
# <a name="language-independence-and-language-independent-components"></a>語言獨立性以及與語言無關的元件
.NET Framework 是與語言無關的。 這表示，身為開發人員，您可以用目標為 .NET Framework 的許多語言之一進行開發，例如 C#、C++/CLI、Eiffel、F#、IronPython、IronRuby、PowerBuilder、Visual Basic、Visual COBOL 和 Windows PowerShell。 您可以存取為 .NET Framework 開發的類別庫的類型和成員，而不需要知道最初的寫入語言，也不需遵循任何原始語言的語言慣例。 如果您是元件開發人員，則不論其語言為何，元件都可以由任何 .NET Framework 應用程式存取。  
  
> [!NOTE]
>  本文第一個部分將討論建立和語言無關的元件，也就是以任何語言撰寫的應用程式都可以使用這些元件。 您也可以從以多種語言撰寫的原始程式碼建立單一元件或應用程式。請參閱本文第二部分的[跨語言互通性](#CrossLang)。  
  
 若要充分與其他以任何語言撰寫的物件互動，這些物件必須只向呼叫端公開所有語言通用的功能。 這一組通用的功能是由 Common Language Specification (CLS) 所定義，CLS 是套用至所產生之組件的一組規則。 Common Language Specification 是定義在 [ECMA-335 Standard:Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm) 的第一篇條款 7 到 11。  
  
 如果您的元件符合 Common Language Specification，則保證其符合 CLS 標準，而且可以從支援 CLS 之任何程式語言所撰寫的組件中的程式碼來加以存取。 您可以在編譯時期將 <xref:System.CLSCompliantAttribute> 屬性套用至您的原始程式碼，判斷您的元件是否符合 Common Language Specification。 如需詳細資訊，請參閱 [CLSCompliantAttribute 屬性](#CLSAttribute)。  
  
 本文內容：  
  
-   [CLS 合規性規則](#Rules)  
  
    -   [類型及類型成員簽章](#Types)  
  
    -   [命名慣例](#naming)  
  
    -   [類型轉換](#conversion)  
  
    -   [陣列](#arrays)  
  
    -   [介面](#Interfaces)  
  
    -   [列舉](#enums)  
  
    -   [一般類型成員](#members)  
  
    -   [成員存取範圍](#MemberAccess)  
  
    -   [泛型類型及成員](#Generics)  
  
    -   [建構函式](#ctors)  
  
    -   [屬性](#properties)  
  
    -   [事件](#events)  
  
    -   [多載](#overloads)  
  
    -   [例外狀況](#exceptions)  
  
    -   [屬性](#attributes)  
  
-   [CLSCompliantAttribute 屬性](#CLSAttribute)  
  
-   [不同語言之間的互通性](#CrossLang)  
  
<a name="Rules"></a>   
## <a name="cls-compliance-rules"></a>CLS 符合性規則  
 本節討論建立符合 CLS 標準的元件的規則。 如需規則的完整清單，請參閱 [ECMA-335 Standard:Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm) 的第一篇條款 11。  
  
> [!NOTE]
>  Common Language Specification 所討論的是適用於下列各項的 CLS 符合性的每個規則：消費者 (以程式設計方式存取符合 CLS 標準之元件的開發人員)、架構 (使用語言編譯器建立符合 CLS 標準之程式庫的開發人員) 和擴充項 (建立工具 (例如可建立符合 CLS 標準之元件的語言編譯器或程式碼剖析器) 的開發人員)。 本文旨在討論適用於架構的規則。 請注意，話雖如此，適用於擴充項的某些規則可能也適用於使用 Reflection.Emit 建立的組件。  
  
 若要設計與語言無關的元件，您只需要將 CLS 符合性規則套用至元件的公用介面。 您的私用實作並不需要符合規格。  
  
> [!IMPORTANT]
>  CLS 符合性規則只適用於元件的公用介面，不適用於其私用實作。  
  
 例如，除了 <xref:System.Byte> 以外的不帶正負號的整數都不符合 CLS 標準。 因為下面範例中的 `Person` 類別會公開類型為 `Age` 的 <xref:System.UInt16> 屬性，下面程式碼會顯示編譯器警告。  
  
 [!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
 [!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]  
  
 您可以藉由將 `Person` 屬性的類型從 `Age` 變更為符合 CLS 標準 16 位元帶正負號整數的 <xref:System.UInt16>，使 <xref:System.Int16> 類別符合 CLS 標準。 您不需要變更 `personAge` 私用欄位的類型。  
  
 [!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
 [!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]  
  
 程式庫的公用介面由下列各項組成：  
  
-   公用類別的定義。  
  
-   公用類別之公用成員的定義，以及衍生類別可存取之成員 (即 protected 成員) 的定義。  
  
-   公用類別之公用方法的參數和傳回類型，以及衍生類別可存取之方法的參數和傳回類型。  
  
 下表列出 CLS 符合性的規則。 這些規則的英文是一字不差地擷取自 [ECMA-335 Standard:Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (Copyright 2012 by Ecma International)，然後再翻譯。 這些規則的其他詳細資訊可在下列章節中找到。  
  
|分類|請參閱|規則|規則編號|  
|--------------|---------|----------|-----------------|  
|協助工具選項|[成員存取範圍](#MemberAccess)|在覆寫繼承的方法時，不得變更其存取範圍；但覆寫繼承自具有 `family-or-assembly` 存取範圍之不同組件的方法除外。 在這種情況下，覆寫應具有 `family` 存取範圍。|10|  
|協助工具選項|[成員存取範圍](#MemberAccess)|類型和成員應該有可視性和存取範圍，以致每當成員本身為可見和可存取時，任何成員簽章中的類型也應該是可見和可存取的。 例如，在組件外部是可見的公用方法不得有引數，其類型只有在組件內可見。 構成類型應該有可視性和存取範圍，以致每當成員本身為可見和可存取時，任何成員簽章中所用的具現化泛型類型也應該是可見和可存取的。 例如，存在於組件外部可見成員的簽章中的具現化泛型類型，不得有類型只能在組件內可見的泛型引數。|12|  
|陣列|[陣列](#arrays)|陣列必須有符合 CLS 標準之類型的項目，而且陣列所有維度的下限必須為零。 只有項目是陣列以及陣列的項目類型是需要在多載之間區別的事實。 當多載根據兩個或多個陣列類型時，項目類型應該是具名類型。|16|  
|屬性|[屬性](#attributes)|屬性的類型必須為 <xref:System.Attribute?displayProperty=nameWithType> 或繼承自它的類型。|41|  
|屬性|[屬性](#attributes)|CLS 只允許自訂屬性編碼的子集。 只有以下這些類型允許出現在這些編碼方式中 (請參閱第四篇)：<xref:System.Type?displayProperty=nameWithType>、<xref:System.String?displayProperty=nameWithType>、<xref:System.Char?displayProperty=nameWithType>、<xref:System.Boolean?displayProperty=nameWithType>、<xref:System.Byte?displayProperty=nameWithType>、<xref:System.Int16?displayProperty=nameWithType>、<xref:System.Int32?displayProperty=nameWithType>、<xref:System.Int64?displayProperty=nameWithType>、<xref:System.Single?displayProperty=nameWithType>、<xref:System.Double?displayProperty=nameWithType>，以及以 CLS 標準基底整數類型為基礎的所有列舉類型。|34|  
|屬性|[屬性](#attributes)|CLS 不允許公開可見的必要修飾詞 (`modreq`，請參閱第二篇)，不過，允許它不了解的選擇性修飾詞 (`modopt`，請參閱第二篇)。|35|  
|建構函式|[建構函式](#ctors)|物件建構函式必須先呼叫基底類別的某個執行個體建構函式，才能對繼承的執行個體資料進行任何存取  (這不適用於不需要具有建構函式的實值類型)。|21|  
|建構函式|[建構函式](#ctors)|除非是做為物件建立程序的一部分，否則是不能呼叫物件建構函式的，而且也不能初始化物件兩次。|22|  
|列舉|[列舉](#enums)|列舉的基礎類型應該是內建 CLS 整數類型，欄位的名稱應該是 "value__"，而且該欄位應該標記為 `RTSpecialName`。|7|  
|列舉|[列舉](#enums)|有兩種不同的列舉，由 <xref:System.FlagsAttribute?displayProperty=nameWithType> (請參閱第四篇程式庫) 自訂屬性存在與否表示。 一個表示具名整數值；另一個則表示具名位元旗標 (可合併以產生未命名的值)。 `enum` 的值不限於指定的值。|8|  
|列舉|[列舉](#enums)|列舉的常值靜態欄位必須有列舉本身的類型。|9|  
|事件|[事件](#events)|實作事件的方法必須在中繼資料中標記為 `SpecialName`。|29|  
|事件|[事件](#events)|事件及其存取子的存取範圍必須是相同的。|30|  
|事件|[事件](#events)|事件的 `add` 和 `remove` 方法，兩者必須同時存在或同時不存在。|31|  
|事件|[事件](#events)|事件的 `add` 和 `remove` 方法應各自採用一個其類型會定義事件類型的參數，而且必須是衍生自 <xref:System.Delegate?displayProperty=nameWithType>。|32|  
|事件|[事件](#events)|事件必須遵守特定的命名模式。 在適當的名稱比較中應忽略 CLS 第 29 條規則中所提及的 `SpecialName` 屬性，並且應遵循識別項規則。|33|  
|例外狀況|[例外狀況](#exceptions)|擲回的物件的類型必須為 <xref:System.Exception?displayProperty=nameWithType>，或繼承自它的類型。 然而，並不需要使用符合 CLS 標準的方法來封鎖其他類型例外狀況的傳播。|40|  
|一般|[CLS 符合性：規則](#Rules)|CLS 規則只適用於類型中可在定義組件之外存取或可見的那些部分。|1|  
|一般|[CLS 符合性：規則](#Rules)|不符合 CLS 標準之類型的成員不得標記為符合 CLS 標準。|2|  
|泛型|[泛型類型及成員](#Generics)|巢狀類型應至少有與其封入類型 (Enclosing Type) 一樣多的泛型參數。 巢狀型別中的泛型參數，都與在其封入型別中泛型參數的位置對應。|42|  
|泛型|[泛型類型及成員](#Generics)|根據以上定義的規則，泛型類型的名稱必須編碼非巢狀類型上宣告的型別參數數目或在巢狀類型上新引入的型別參數數目。|43|  
|泛型|[泛型類型及成員](#Generics)|泛型類型必須宣告足夠的限制式，才能保證泛型類型限制式將會符合基底類型或介面上的所有限制式。|4444|  
|泛型|[泛型類型及成員](#Generics)|用來做為泛型參數之條件約束的類型，本身也應符合 CLS 標準。|45|  
|泛型|[泛型類型及成員](#Generics)|具現化 (Instantiated) 泛型類型中成員 (包括巢狀型別) 的可視性和存取範圍，必須被視為屬於特定具現化的範圍，而非泛型類型宣告的範圍。 在此假設之下，CLS 第 12 條規則的可視性和存取範圍規則仍然適用。|46|  
|泛型|[泛型類型及成員](#Generics)|對於每個抽象或虛擬泛型方法，都必須具有預設具象 (非抽象) 實作。|47|  
|介面|[介面](#Interfaces)|針對不符合 CLS 規範的方法，符合 CLS 規範的介面不需要其定義便能實作它們。|18|  
|介面|[介面](#Interfaces)|符合 CLS 標準的介面不可定義靜態方法，也不可定義欄位。|19|  
|成員|[一般類型成員](#members)|全域靜態欄位和方法不符合 CLS 標準。|36|  
|成員|--|常值靜態欄位的值是透過使用欄位初始化中繼資料來指定。 符合 CLS 標準的常值必須具有欄位初始化中繼資料所指定的值，這個中繼資料與常值有完全相同的類型 (如果該常值是 `enum`，則為基礎類型)。|13|  
|成員|[一般類型成員](#members)|vararg 條件約束不是 CLS 的一部分，CLS 所支援的唯一呼叫慣例是標準的 Managed 呼叫慣例。|15|  
|命名規範|[命名慣例](#naming)|組件必須遵循 Unicode Standard 3.0 技術報告編號 15 附錄 7，其規定可以啟始並包含在識別項中的字元集。如需取得此報告，請造訪 <https://www.unicode.org/unicode/reports/tr15/tr15-18.html> \(英文\)。 識別項應使用 Unicode Normalization 表格 C 所定義的標準格式。基於 CLS 目的，如果兩個識別項的小寫對應 (如 Unicode 不區分地區設定、一對一小寫對應所指定) 相同，則它們便為相同。 也就是依據 CLS，兩個識別項若要被視為不同，不只是大小寫，還要有其他不同之處。 不過，為了覆寫繼承的定義，CLI 需要使用原始宣告的確切編碼。|4|  
|多載化|[命名慣例](#naming)|在符合 CLS 標準的範圍中引入的所有名稱，除了名稱完全相同且透過多載解析的情況之外，都必須是不同的獨立類型。 也就是說，CTS 允許單一類型對方法和欄位使用同樣的名稱，但 CLS 不允許。|5|  
|多載化|[命名慣例](#naming)|即使 CTS 允許區別不同簽章，還是必須單獨依據識別項比較來區別欄位和巢狀類型。 經由識別項比較之後，具有相同名稱的方法、屬性和事件不可僅以傳回型別做區分，除非符合 CLS 第 39 條規則中所指定的內容。|6|  
|多載化|[多載](#overloads)|只有屬性和方法可以多載。|37|  
|多載化|[多載](#overloads)|屬性和方法只可以根據其參數數目和類型多載，除了名為 `op_Implicit` 和 `op_Explicit` 的轉換運算子，也可以根據其傳回類型多載。|38|  
|多載化|--|如果在有相同名稱的類型中宣告兩個或更多符合 CLS 標準的方法，則對一組特定的類型具現化來說，它們具有相同的參數和傳回型別，而且所有這些方法在語意上與這些類型具現化相等。|48|  
|型別|[類型和類型成員簽章](#Types)|<xref:System.Object?displayProperty=nameWithType> 符合 CLS 標準。 任何其他符合 CLS 標準的類別也都必須繼承自符合 CLS 標準的類別。|23|  
|屬性|[屬性](#properties)|實作屬性之 getter 和 setter 方法的方法在中繼資料中應標記為 `SpecialName`。|24|  
|屬性|[屬性](#properties)|屬性的存取子必須全部為 static、全部為 virtual 或全部為 instance。|26|  
|屬性|[屬性](#properties)|屬性的類型應是 getter 的傳回型別和 setter 最後一個引數的類型。 屬性參數的類型必須是 getter 參數的類型和 setter 除了最後一個參數之外的所有參數類型。 所有這些類型都必須符合 CLS 標準，而且不能是 Managed 指標 (也就是，不能以傳址方式傳遞)。|27|  
|屬性|[屬性](#properties)|屬性必須遵守特定的命名模式。 在適當的名稱比較中應忽略 CLS 第 24 條規則中所提及的 `SpecialName` 屬性，並且應遵循識別項規則。 屬性必須有 getter 方法、setter 方法或兩者皆有。|28|  
|類型轉換|[類型轉換](#conversion)|如果有提供 `op_Implicit` 或 `op_Explicit`，則必須提供替代方式來提供強制型轉。|39|  
|型別|[類型和類型成員簽章](#Types)|Boxed 實值類型不符合 CLS 標準。|3|  
|型別|[類型和類型成員簽章](#Types)|簽章中出現的所有類型都必須符合 CLS 標準。 構成具現化泛型類型的所有類型都必須符合 CLS 標準。|11|  
|型別|[類型和類型成員簽章](#Types)|具型別的參考不符合 CLS 標準|14|  
|型別|[類型和類型成員簽章](#Types)|Unmanaged 指標類型不符合 CLS 標準。|17|  
|型別|[類型和類型成員簽章](#Types)|符合 CLS 標準的類別、實值類型和介面不能要求不符合 CLS 標準的成員實作。|20|  
  
<a name="Types"></a>   
### <a name="types-and-type-member-signatures"></a>類型和類型成員簽章  
 <xref:System.Object?displayProperty=nameWithType> 類型符合 CLS 標準，並且是 .NET Framework 類型系統中所有物件類型的基底類型。 .NET Framework 中的繼承若不是隱含的 (例如，<xref:System.String> 類別隱含繼承 <xref:System.Object> 類別) 就是明確的 (例如，<xref:System.Globalization.CultureNotFoundException> 類別明確繼承 <xref:System.ArgumentException> 類別，後者又明確繼承 <xref:System.SystemException> 類別，再依次明確繼承 <xref:System.Exception> 類別)。 若要讓衍生類型符合 CLS 標準，其基底類型必須符合 CLS 標準。  
  
 下面範例會示範其基底類型不符合 CLS 標準的衍生類型。 它會定義基底 `Counter` 類別，這個類別使用不帶正負號的 32 位元整數做為計數器。 因為該類別會藉由包裝不帶正負號的整數提供計數器功能，所以該類別會標記為不符合 CLS 標準。 結果，衍生的類別 `NonZeroCounter` 也不符合 CLS 標準。  
  
 [!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
 [!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]  
  
 成員簽章中出現的所有類型 (包括方法的傳回型別或屬性類型) 都必須符合 CLS 標準。 此外，如果是泛型類型：  
  
-   構成具現化泛型類型的所有類型都必須符合 CLS 標準。  
  
-   所有用來做為泛型參數之限制式的類型，都必須符合 CLS 標準。  
  
 .NET Framework 的[一般類型系統](../../docs/standard/base-types/common-type-system.md)包含了幾個內建類型，這些內建類型直接受到 Common Language Runtime 的支援，並且在組譯碼的中繼資料中以特殊方式進行編碼。 在這些內建類型中，下表所列的類型符合 CLS 標準。  
  
|符合 CLS 標準的類型|說明|  
|-------------------------|-----------------|  
|<xref:System.Byte>|8 位元不帶正負號的整數|  
|<xref:System.Int16>|16 位元帶正負號的整數|  
|<xref:System.Int32>|32 位元帶正負號的整數|  
|<xref:System.Int64>|64 位元帶正負號的整數|  
|<xref:System.Single>|單精確度浮點值|  
|<xref:System.Double>|雙精確度浮點值|  
|<xref:System.Boolean>|`true` 或 `false` 值類型|  
|<xref:System.Char>|UTF-16 編碼程式碼單位|  
|<xref:System.Decimal>|非浮點十進位數字|  
|<xref:System.IntPtr>|平台定義大小的指標或控制代碼|  
|<xref:System.String>|零個、一個或多個 <xref:System.Char> 物件的集合。|  
  
 下表所列的內建類型不符合 CLS 標準。  
  
|不符合標準的類型|說明|符合 CLS 標準的替代項目|  
|-------------------------|-----------------|--------------------------------|  
|<xref:System.SByte>|8 位元帶正負號的整數資料類型|<xref:System.Int16>|  
|<xref:System.TypedReference>|物件和其執行階段類型的指標|無|  
|<xref:System.UInt16>|16 位元不帶正負號的整數|<xref:System.Int32>|  
|<xref:System.UInt32>|32 位元不帶正負號的整數|<xref:System.Int64>|  
|<xref:System.UInt64>|64 位元不帶正負號的整數|<xref:System.Int64> (可能溢位)、<xref:System.Numerics.BigInteger> 或 <xref:System.Double>。|  
|<xref:System.UIntPtr>|不帶正負號的指標或控制代碼|<xref:System.IntPtr>|  
  
 .NET Framework 類別庫或其他類別庫可能包含不符合 CLS 標準的其他類型，例如：  
  
-   Boxed 實值類型。 下面 C# 範例會建立類別，具有類型為 `int*` 的公用屬性，名為 `Value`。 由於 `int*` 為 Boxed 實值類型，因此編譯器將其標示為不符合 CLS 標準。  
  
     [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]  
  
-   具類型參考，是一種含有物件參考和類型參考的特殊建構。 具類型參考在 .NET Framework 中是由 <xref:System.TypedReference> 類別表示。  
  
 如果類型不符合 CLS 標準，您應將 <xref:System.CLSCompliantAttribute> 值為 `isCompliant` 的 `false` 屬性套用至該類型。 如需詳細資訊，請參閱 [CLSCompliantAttribute 屬性](#CLSAttribute)一節。  
  
 下面範例說明在方法簽章和泛型類型具現化中的 CLS 符合性問題。 它會定義 `InvoiceItem` 類別，包含 <xref:System.UInt32> 類型的屬性、`Nullable(Of UInt32)` 類型的屬性，以及參數類型為 <xref:System.UInt32> 和 `Nullable(Of UInt32)` 的建構函式。 當您嘗試編譯這個範例時，會收到四個編譯器警告。  
  
 [!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
 [!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]  
  
 若要排除編譯器警告，請將 `InvoiceItem` 公用介面中不符合 CLS 標準的類型取代為與符合標準的類型：  
  
 [!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
 [!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]  
  
 除了列出的特定類型之外，有些分類的類型也不符合 CLS 標準。 這些包括 Unmanaged 指標類型和函式指標類型。 下面範例會產生編譯器警告，因為它使用整數指標建立整數陣列。  
  
 [!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]  
  
 如果是符合 CLS 標準的抽象類別 (也就是，在 C# 中標記為 `abstract`，或在 Visual Basic 中標記為 `MustInherit` 的類別)，類別的所有成員也必須符合 CLS 標準。  
  
<a name="naming"></a>   
### <a name="naming-conventions"></a>命名規範  
 由於某些程式語言不區分大小寫，識別項 (例如命名空間、類型和成員的名稱) 必須透過區分大小寫以外的方式產生差異。 如果兩個識別項的小寫對應是相同的，則這兩個識別項是視為相等。 下面 C# 範例會定義兩個公用類別：`Person` 和 `person`。 因為只有大小寫不同，所以 C# 編譯器會將其標示為不符合 CLS 標準。  
  
 [!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]  
  
 程式語言識別項，例如命名空間、類型和成員的名稱，必須符合 [Unicode Standard 3.0 Technical Report 15 的 Annex 7](https://www.unicode.org/reports/tr15/tr15-18.html)。 這表示：  
  
-   識別項的第一個字元可以是任何 Unicode 大寫字母、小寫字母、標題大寫字母、修飾詞字母、其他字母或字母數字。 如需 Unicode 字元分類的詳細資訊，請參閱 <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType> 列舉。  
  
-   接下來的字元可以來自和第一個字元相同的任何分類，而且也可以包含非間距記號、間距組合記號、十進位數字、連接子標點符號和格式化程式碼。  
  
 在您比較識別項之前，應該先篩掉格式化程式碼，並將識別項轉換為 Unicode 正規化表單 C，因為單一字元可由多個 UTF 16 編碼字碼單位表示。 產生和 Unicode 正規化表單 C 相同的字碼單位的字元順序不符合 CLS 標準。 下面範例會定義名為 `Å` 的屬性和名為 `Å` 的第二個屬性。前者包含 ANGSTROM SIGN 字元 (U+212B)，後者包含 LATIN CAPITAL LETTER A WITH RING ABOVE 字元 (U+00C5)。 C# 和 Visual Basic 編譯器都會將原始程式碼標示為不符合 CLS 標準。  
  
 [!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
 [!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]  
  
 特定範圍內的成員名稱 (例如組件中的命名空間、命名空間中的類型或類型中的成員)，除了透過多載解析的名稱以外，都必須是唯一的。 這個需求比一般類型系統的需求更嚴格，後者允許在範圍內的多個成員具有相同名稱，只要它們是不同的類型成員 (例如，一個是方法，一個是欄位)。 特別是，如果是類型成員：  
  
-   欄位和巢狀類型只有依據名稱做區別。  
  
-   具有相同名稱的方法、屬性和事件不可僅以傳回類型做區分。  
  
 下面範例說明成員名稱在其範圍內必須是唯一的這個需求。 它會定義名為 `Converter` 的類別，其中包含四個名為 `Conversion` 的成員。 三個是方法，一個是屬性。 包含 <xref:System.Int64> 參數的方法具有唯一的名稱，但含有 <xref:System.Int32> 參數的兩個方法則沒有唯一名稱，因為傳回值不視為成員簽章的一部分。 `Conversion` 屬性也違反這項需求，因為屬性不能與多載方法同名。  
  
 [!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
 [!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]  
  
 個別語言包含唯一的關鍵字，因此以 Common Language Runtime 為目標的語言也必須提供一些參考符合關鍵字之識別碼 (例如類型名稱) 的機制。 例如，`case` 在 C# 和 Visual Basic 中都是關鍵字。 不過，下面 Visual Basic 範例可以使用左右大括號，讓名稱為 `case` 的類別與 `case` 關鍵字有所區分。 否則，這個範例會產生錯誤訊息「關鍵字做為識別項無效」，而無法編譯。  
  
 [!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]  
  
 下面 C# 範例可以使用 `case` 符號區分識別項與語言關鍵字，以具現化 `@` 類別。 若沒有它，C# 編譯器會顯示兩個錯誤訊息：「必須是類型」和「無效的運算式詞彙 'case'」。  
  
 [!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]  
  
<a name="conversion"></a>   
### <a name="type-conversion"></a>類型轉換  
 Common Language Specification 定義兩個轉換運算子：  
  
-   `op_Implicit`，用於不會導致資料或精確度遺失的擴展轉換。 例如，<xref:System.Decimal> 結構包含多載 `op_Implicit` 運算子，以便將整數類型的值和 <xref:System.Char> 值轉換為 <xref:System.Decimal> 值。  
  
-   `op_Explicit`，用於可能會導致大小 (值轉換為某個範圍較小的值) 或精確度遺失的縮小轉換。 例如，<xref:System.Decimal> 結構包含多載 `op_Explicit` 運算子，以便將 <xref:System.Double> 和 <xref:System.Single> 值轉換為 <xref:System.Decimal>，以及將 <xref:System.Decimal> 值轉換為整數值 <xref:System.Double>、<xref:System.Single> 和 <xref:System.Char>。  
  
 不過，並非所有語言都支援運算子多載或自訂運算子定義。 如果您選擇實作這些轉換運算子，也應該提供執行轉換的替代方式。 建議您提供 `From`Xxx 和 `To`Xxx 方法。  
  
 下面範例定義了符合 CLS 標準的隱含和明確轉換。 它會建立 `UDouble` 類別，表示帶正負號的雙精確度浮點數。 它支援從 `UDouble` 到 <xref:System.Double> 的隱含轉換，以及支援從 `UDouble` 到 <xref:System.Single>、<xref:System.Double> 到 `UDouble` 以及 <xref:System.Single> 到 `UDouble` 的明確轉換。 它也會定義 `ToDouble` 方法做為隱含轉換運算子的替代方法，以及定義 `ToSingle`、`FromDouble` 和 `FromSingle` 方法做為明確轉換運算子的替代方法。  
  
 [!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
 [!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]  
  
<a name="arrays"></a>   
### <a name="arrays"></a>陣列  
 符合 CLS 標準的陣列會遵守下列規則：  
  
-   陣列所有維度的下限都必須為零。 下面範例會建立下限為一、不符合 CLS 標準的陣列。 請注意，儘管 <xref:System.CLSCompliantAttribute> 屬性存在，編譯器並不會偵測出 `Numbers.GetTenPrimes` 方法傳回的陣列不符合 CLS 標準。  
  
     [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
     [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]  
  
-   所有陣列項目都必須包含符合 CLS 標準的類型。 下面範例會定義傳回不符合 CLS 標準的陣列的兩個方法。 第一個會傳回 <xref:System.UInt32> 值的陣列。 第二個傳回包含 <xref:System.Object> 和 <xref:System.Int32> 值的 <xref:System.UInt32> 陣列。 雖然編譯器會因為其 <xref:System.UInt32> 類型而將第一個陣列識別為不符合標準，但是無法辨識出第二個陣列包含了不符合 CLS 標準的項目。  
  
     [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
     [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]  
  
-   具有陣列參數之方法的多載解析是根據它們是陣列和其項目類型。 因此，下面多載 `GetSquares` 方法的定義符合 CLS 標準。  
  
     [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
     [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>介面  
 符合 CLS 標準的介面可以定義屬性、事件和虛擬方法 (沒有實作的方法)。 符合 CLS 標準的介面不可含有下列任何一項：  
  
-   靜態方法或靜態欄位。 如果您在介面中定義了靜態成員，C# 和 Visual Basic 編譯器會產生編譯器錯誤。  
  
-   欄位。 如果您在介面中定義了欄位，C# 和 Visual Basic 編譯器會產生編譯器錯誤。  
  
-   不符合 CLS 標準的方法。 例如，下面介面定義包含標記為符合 CLS 標準的方法 `INumber.GetUnsigned`。 這個範例會產生編譯器警告。  
  
     [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
     [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]  
  
     由於這項規則，在實作不符合 CLS 標準的成員時並不需要符合 CLS 標準的類型。 如果符合 CLS 標準的架構沒有公開實作不符合 CLS 標準介面的類別，也應該提供所有不符合 CLS 標準成員的具象實作。  
  
 符合 CLS 標準的語言編譯器也必須允許類別提供在多個介面中具有相同名稱及簽章的成員實作。  C# 和 Visual Basic 支援[明確介面實作](../csharp/programming-guide/interfaces/explicit-interface-implementation.md)，以提供相同具名方法的不同實作。 Visual Basic 也支援 `Implements` 關鍵字，可讓您明確指定特定成員實作的介面和成員。 下面範例會透過定義實作 `Temperature` 和 `ICelsius` 介面做為明確介面實作的 `IFahrenheit` 類別，來說明這種情況。  
  
 [!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
 [!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]  
  
<a name="enums"></a>   
### <a name="enumerations"></a>列舉  
 符合 CLS 標準的列舉必須遵守下列規則：  
  
-   列舉的基礎類型必須是內建的 CLS 標準整數 (<xref:System.Byte>、<xref:System.Int16>、<xref:System.Int32> 或 <xref:System.Int64>)。 例如，下面程式碼會嘗試定義其基礎類型為 <xref:System.UInt32> 的列舉，並產生編譯器警告。  
  
     [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
     [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]  
  
-   列舉類型必須具有以 `Value__` 屬性標記的單一執行個體欄位，名稱為 <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType>。 這可讓您隱含參考欄位值。  
  
-   列舉會包含其類型符合列舉本身類型的常值靜態欄位。 例如，如果您定義含有 `State` 和 `State.On` 值的 `State.Off` 列舉，則 `State.On` 和 `State.Off` 都是常值靜態欄位，其類型為 `State`。  
  
-   列舉有兩種：  
  
    -   表示一組互斥具名整數值的列舉。 這個列舉類型是由缺少 <xref:System.FlagsAttribute?displayProperty=nameWithType> 自訂屬性來表示。  
  
    -   表示一組可合併產生未命名值之位元旗標的列舉。 這個列舉類型是由存在 <xref:System.FlagsAttribute?displayProperty=nameWithType> 自訂屬性來表示。  
  
     如需詳細資訊，請參閱 <xref:System.Enum> 結構的說明文件。  
  
-   列舉的值不限於其指定值的範圍。 換句話說，列舉中的值範圍即是其基礎值的範圍。 您可以使用 <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> 方法來判斷某指定值是否為列舉的成員。  
  
<a name="members"></a>   
### <a name="type-members-in-general"></a>一般類型成員  
 Common Language Specification 要求所有欄位和方法都必須當做特定類別的成員來加以存取。 因此，全域靜態欄位和方法 (也就是除了類型外定義的靜態欄位或方法) 不符合 CLS 標準。 如果您嘗試在原始程式碼中包含全域欄位或方法，則 C# 和 Visual Basic 編譯器都會產生編譯器錯誤。  
  
 Common Language Specification 只支援標準的 Managed 呼叫慣例。 它不支援 Unmanaged 呼叫慣例和具有變數引數清單 (以 `varargs` 關鍵字標記) 的方法。 如果是與標準 Managed 呼叫慣例相容的變數引數清單，請使用 <xref:System.ParamArrayAttribute> 屬性或個別語言的實作，例如 C# 中的 `params` 關鍵字或 Visual Basic 中的 `ParamArray` 關鍵字。  
  
<a name="MemberAccess"></a>   
### <a name="member-accessibility"></a>成員存取範圍  
 覆寫繼承的成員無法變更該成員的存取範圍。 例如，衍生類別中的私用方法無法覆寫基底類別中的公用方法。 有一個例外：由不同組件中的類型所覆寫的某個組件中的 `protected internal` (在 C# 中) 或 `Protected Friend` (在 Visual Basic 中) 成員。 在這種情況下，覆寫的存取範圍是 `Protected`。  
  
 下面範例說明當 <xref:System.CLSCompliantAttribute> 屬性是設定為 `true`，並且 `Human` (衍生自 `Animal` 的類別) 嘗試將 `Species` 屬性的存取範圍從 public (公用) 變更為 private (私用) 時，所產生的錯誤。 如果它的存取範圍變更為 public (公用)，則此範例會編譯成功。  
  
 [!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
 [!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]  
  
 每當成員本身為可存取時，成員簽章中的類型也必須是可存取的。 例如，這表示 public 成員不能包含類型為 private、protected 或 internal 的參數。 下面範例說明當 `StringWrapper` 類別建構函式公開內部 `StringOperationType` 列舉值，決定如何包裝字串值時，所產生的編譯器錯誤。  
  
 [!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
 [!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]  
  
<a name="Generics"></a>   
### <a name="generic-types-and-members"></a>泛型類型和成員  
 巢狀類型一律至少具有與其封入類型 (Enclosing Type) 一樣多的泛型參數。 這些在位置上對應於封入類型中的泛型參數。 泛型類型也可以包含新的泛型參數。  
  
 個別語言的語法可能會隱藏包含類型和其巢狀類型的泛型類型參數之間的關聯性。 在下面範例中，泛型類型 `Outer<T>` 包含兩個巢狀類別：`Inner1A` 和 `Inner1B<U>`。 對 `ToString` 方法 (每個類別都是從 <xref:System.Object.ToString%2A?displayProperty=nameWithType> 繼承這個方法) 的呼叫，顯示出每個巢狀類別都會包含其所包含類別的類型參數。  
  
 [!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
 [!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]  
  
 泛型類型名稱的編碼格式為 *name\`n*，其中 *name* 是類型名稱、\` 是字元常值，而 *n* 則是在類型上宣告的參數數目，或是巢狀泛型類型中，新引入之型別參數的數目。 這個泛型類型名稱編碼方式主要適用於使用反映來存取程式庫中符合 CLS 標準之泛型類型的開發人員。  
  
 如果限制式是套用至泛型類型，則任何當做限制式使用的類型也必須符合 CLS 標準。 下面範例定義了不符合 CLS 標準的類別 (名稱為 `BaseClass`) 以及類型參數必須衍生自 `BaseCollection` 的泛型類別 (名稱為 `BaseClass`)。 但是因為 `BaseClass` 不符合 CLS 標準，所以編譯器會發出警告。  
  
 [!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
 [!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]  
  
 如果泛型類型是衍生自泛型基底類型，就必須重新宣告任何限制式，才能保證同時符合基底類型上的限制式。 下面範例會定義可代表任何數字類型的 `Number<T>`。 它也會定義表示浮點值的 `FloatingPoint<T>` 類別。 不過，因為未將 `Number<T>` (其中 T 必須是實值類型) 的限制式套用至 `FloatingPoint<T>`，所以無法編譯原始程式碼。  
  
 [!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
 [!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]  
  
 如果將該條件約束加入至 `FloatingPoint<T>` 類別，則這個範例會編譯成功。  
  
 [!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
 [!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]  
  
 Common Language Specification 會對巢狀類型和保護的成員施加保守的每一個具現化模型。 開放式泛型類型無法公開其簽章包含受保護巢狀泛型類型的特定具現化的欄位或成員。 可擴充泛型基底類別或介面之特定具現化的非泛型類型，無法公開其簽章包含受保護巢狀泛型類型的不同具現化的欄位或成員。  
  
 下面範例會定義泛型類型 `C1<T>` (在 Visual Basic 中為 `C1(Of T)`) 和受保護的類別 `C1<T>.N` (在 Visual Basic 中為 `C1(Of T).N`)。 `C1<T>` 有兩個方法：`M1` 和 `M2`。 不過，`M1` 不符合 CLS 標準，因為它會嘗試從 C1\<T> (或 `C1(Of T)`) 傳回 `C1<int>.N` (或 `C1(Of Integer).N`) 物件。 第二個類別 `C2` 是衍生自 `C1<long>` (或 `C1(Of Long)`)。 它具有兩個方法：`M3` 和 `M4`。 `M3` 不符合 CLS 標準，因為它會嘗試從 `C1<int>.N` 的子類別傳回 `C1(Of Integer).N` (或 `C1<long>`) 物件。 請注意，語言編譯器的限制可能還要更嚴格。 在此範例中，Visual Basic 會在其嘗試編譯 `M4` 時顯示錯誤。  
  
 [!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
 [!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]  
  
<a name="ctors"></a>   
### <a name="constructors"></a>建構函式  
 符合 CLS 標準之類別和結構中的建構函式必須遵守下列規則：  
  
-   衍生類別的建構函式必須先呼叫基底類別的建構函式，才能存取繼承的執行個體資料。 因為衍生類別不會繼承基底類別建構函式，所以才有這項需求。 此規則不會套用至結構，因為結構不支援直接繼承。  
  
     通常，編譯器會獨立強制執行此規則，而不需考慮 CLS 符合性，如下面範例所示。 它會建立衍生自 `Doctor` 類別的 `Person` 類別，但是 `Doctor` 類別無法呼叫 `Person` 類別建構函式來初始化繼承的執行個體欄位。  
  
     [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
     [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]  
  
-   物件建構函式除了建立物件之外，無法被呼叫。 此外，物件無法初始化兩次。 例如，這表示 <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> 和還原序列化方法 (例如 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>) 不能呼叫建構函式。  
  
<a name="properties"></a>   
### <a name="properties"></a>屬性  
 符合 CLS 標準的類型中的屬性必須遵守下列規則：  
  
-   屬性必須有 setter、getter 或兩者皆有。 在組件中，這些會實作為特殊方法，也就是，會顯示為不同的方法 (getter 命名為 `get_`propertyname，而 setter 則為 `set_`propertyname)，並在組件的中繼資料中標記為 `SpecialName`。 C# 和 Visual Basic 編譯器會自動強制執行這項規則，而不需要套用 <xref:System.CLSCompliantAttribute> 屬性。  
  
-   屬性的類型是屬性 getter 的傳回型別和 setter 的最後一個引數。 這些類型必須符合 CLS 標準，而且引數不能以傳址方式指派給屬性 (也就是它們不能是 Managed 指標)。  
  
-   如果屬性同時有 getter 和 setter，則兩者都必須是虛擬、靜態或者都是執行個體。 C# 和 Visual Basic 編譯器會透過它們的屬性定義語法，來自動強制執行這項規則。  
  
<a name="events"></a>   
### <a name="events"></a>事件  
 事件是由它的名稱和類型來定義。 事件類型是用來表示事件的委派。 例如，<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件的類型為 <xref:System.ResolveEventHandler>。 除了事件本身之外，具有以事件名稱為根據之名稱的三個方法會提供事件的實作，並且在組件的中繼資料中標記為 `SpecialName`：  
  
-   用於加入事件處理常式的方法，名稱為 `add_`EventName。 例如，<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件的事件訂閱方法是命名為 `add_AssemblyResolve`。  
  
-   用於移除事件處理常式的方法，名稱為 `remove_`EventName。 例如，<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件的移除方法是命名為 `remove_AssemblyResolve`。  
  
-   用於表示事件已發生的方法，名稱為 `raise_`EventName。  
  
> [!NOTE]
>  大部分與事件有關的 Common Language Specification 規則都是由語言編譯器實作，而且對元件開發人員而言是透明化的。  
  
 用於加入、移除及引發事件的方法必須具有相同的存取範圍。 它們也必須全部是靜態、執行個體或虛擬的。 用於加入和移除事件的方法具有一個類型為事件委派類型的參數。 加入和移除方法兩者必須同時存在或同時不存在。  
  
 下面範例定義了符合 CLS 標準的類別 (名稱為 `Temperature`)，如果兩個讀數之間的溫度變更等於或超過臨界值，這個類別會引發 `TemperatureChanged` 事件。 `Temperature` 類別會明確地定義 `raise_TemperatureChanged` 方法，讓它可以選擇性地執行事件處理常式。  
  
 [!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
 [!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]  
  
<a name="overloads"></a>   
### <a name="overloads"></a>Overloads  
 Common Language Specification 會對多載成員施加下列需求：  
  
-   成員可以根據參數的數目和任何參數的類型來多載。 辨別多載時，不會考慮呼叫慣例、傳回型別、套用至方法或其參數的自訂修飾詞，以及參數是以傳值或傳址方式傳遞。 如需範例，請參閱[命名慣例](#naming)一節中，要求範圍內的名稱必須是唯一名稱的程式碼。  
  
-   只有屬性和方法可以多載。 欄位和事件不可多載。  
  
-   泛型方法可以根據其泛型參數的數目來多載。  
  
> [!NOTE]
>  多載解析時傳回值不會被視為方法簽章的一部分，這個規則的例外是 `op_Explicit` 和 `op_Implicit` 運算子。 這兩個運算子可以根據其參數以及其傳回值來多載。  
  
<a name="exceptions"></a>   
### <a name="exceptions"></a>例外狀況  
 例外狀況物件必須衍生自 <xref:System.Exception?displayProperty=nameWithType>，或衍生自另一個衍生自 <xref:System.Exception?displayProperty=nameWithType> 的類型。 下面範例說明在名為 `ErrorClass` 的自訂類別用於例外狀況處理時，所造成的編譯器錯誤。  
  
 [!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
 [!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]  
  
 若要更正這個錯誤，`ErrorClass` 類別必須繼承自 <xref:System.Exception?displayProperty=nameWithType>。 此外，還必須覆寫 `Message` 屬性。 下面範例會修正這些錯誤，以定義符合 CLS 標準的 `ErrorClass` 類別。  
  
 [!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
 [!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]  
  
<a name="attributes"></a>   
### <a name="attributes"></a>屬性  
 在 .NET Framework 組件中，自訂屬性會提供可擴充機制，用於儲存自訂屬性和擷取程式設計物件 (例如組件、類型、成員和方法參數) 的相關中繼資料。 自訂屬性必須衍生自 <xref:System.Attribute?displayProperty=nameWithType>，或從衍生自 <xref:System.Attribute?displayProperty=nameWithType> 的類型衍生而來。  
  
 下面範例違反這項規則。 它會定義不是衍生自 `NumericAttribute` 的 <xref:System.Attribute?displayProperty=nameWithType> 類別 請注意，只有在套用不符合 CLS 標準的屬性時，而不是在定義類別時，才會產生編譯器錯誤。  
  
 [!code-csharp[Conceptual.CLSCompliant#18](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute1.cs#18)]
 [!code-vb[Conceptual.CLSCompliant#18](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute1.vb#18)]  
  
 建構函式或符合 CLS 標準的屬性 (attribute) 的屬性 (property) 只能公開下列類型：  
  
-   <xref:System.Boolean>  
  
-   <xref:System.Byte>  
  
-   <xref:System.Char>  
  
-   <xref:System.Double>  
  
-   <xref:System.Int16>  
  
-   <xref:System.Int32>  
  
-   <xref:System.Int64>  
  
-   <xref:System.Single>  
  
-   <xref:System.String>  
  
-   <xref:System.Type>  
  
-   基礎類型為 <xref:System.Byte>、<xref:System.Int16>、<xref:System.Int32> 或 <xref:System.Int64> 的任何列舉類型。  
  
 下面範例會定義衍生自 `DescriptionAttribute` 的 <xref:System.Attribute> 類別。 類別建構函式具有類型為 `Descriptor` 的參數，因此類別不符合 CLS 標準。 請注意，C# 編譯器會發出警告，但編譯會成功，而 Visual Basic 編譯器則不會發出警告和錯誤。  
  
 [!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
 [!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]  
  
<a name="CLSAttribute"></a>   
## <a name="the-clscompliantattribute-attribute"></a>CLSCompliantAttribute 屬性  
 <xref:System.CLSCompliantAttribute> 屬性用於表示程式項目是否符合 Common Language Specification。 <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29?displayProperty=nameWithType> 建構函式包含單一必要參數 `isCompliant`，表示程式項目是否符合 CLS 標準。  
  
 在編譯時間，編譯器會偵測到假設符合 CLS 標準之不符合標準的項目，並發出警告。 對於明確宣告為不符合標準的類型或成員，編譯器不會發出警告。  
  
 元件開發人員可以透過兩種方式使用 <xref:System.CLSCompliantAttribute> 屬性：  
  
-   定義元件所公開符合 CLS 標準的公用介面的組件和不符合 CLS 標準的組件。 當該屬性是用來將特定程式項目標記為符合 CLS 標準時，使用它可以確保目標為 .NET Framework 的所有語言和工具都可以存取這些項目。  
  
-   確定元件庫的公用介面只公開符合 CLS 標準的程式項目。 如果項目不符合 CLS 標準，編譯器通常會發出警告。  
  
> [!WARNING]
>  在某些情況下，語言編譯器會強制執行符合 CLS 標準的規則，而不論是否使用 <xref:System.CLSCompliantAttribute> 屬性。 例如，定義介面的靜態成員會違反 CLS 規則。 就這一點而言，如果您在介面中定義 `static` (在 C# 中) 或 `Shared` (在 Visual Basic 中) 成員，則 C# 和 Visual Basic 編譯器都會顯示錯誤訊息，並且無法編譯應用程式。  
  
 <xref:System.CLSCompliantAttribute> 屬性標記著具有 <xref:System.AttributeUsageAttribute> 值的 <xref:System.AttributeTargets.All?displayProperty=nameWithType> 屬性。 此值可讓您將 <xref:System.CLSCompliantAttribute> 屬性套用至任何程式項目，包括組件、模組、類型 (類別、結構、列舉、介面和委派)、類型成員 (建構函式、方法、屬性、欄位和事件)、參數、泛型參數和傳回值。 不過，在實務中，您應該只將該屬性套用至組件、類型和類型成員。 否則，當編譯器在您的程式庫的公用介面中遇到不符合標準的參數、泛型參數或傳回值時，會忽略該屬性並繼續產生編譯器警告。  
  
 <xref:System.CLSCompliantAttribute> 屬性的值是由內含的程式項目繼承。 例如，如果組件是標記為符合 CLS 標準，它的類型也會符合 CLS 標準。 如果類型是標記為符合 CLS 標準，其巢狀類型及成員也會符合 CLS 標準。  
  
 您可以將 <xref:System.CLSCompliantAttribute> 屬性套用至內含的程式項目，以明確覆寫繼承的符合性。 例如，您可以使用 <xref:System.CLSCompliantAttribute> 值為 `isCompliant` 的 `false` 屬性，在符合標準的組件中定義不符合標準的類型，而且可以使用 `isCompliant` 值為 `true` 的屬性，在不符合標準的組件中定義符合標準的類型。 您也可以在符合標準的類型中定義不符合標準的成員。 然而，不符合標準的類型不能具有符合標準的成員，因此您無法使用 `isCompliant` 值為 `true` 的屬性來覆寫不符合標準之類型的繼承。  
  
 當您開發元件時，一定要使用 <xref:System.CLSCompliantAttribute> 屬性來指出您的組件、其類型及其成員是否符合 CLS 標準。  
  
 若要建立符合 CLS 標準的元件：  
  
1.  使用 <xref:System.CLSCompliantAttribute> 將組件標記為符合 CLS 標準。  
  
2.  將不符合 CLS 標準之組件中公開的任何類型標記為不符合標準。  
  
3.  將符合 CLS 標準之類型中公開的任何成員標記為不符合標準。  
  
4.  為不符合 CLS 標準的成員提供符合 CLS 標準的替代項目。  
  
 如果成功標記了所有您不符合標準的類型和成員，則編譯器應該不會發出任何不符合標準的警告。 不過，您應該指出哪些成員不符合 CLS 標準，並在產品文件中列出符合 CLS 標準的替代項目。  
  
 下面範例會使用 <xref:System.CLSCompliantAttribute> 屬性來定義符合 CLS 標準的組件和類型 `CharacterUtilities`，該類型有兩個不符合 CLS 標準的成員。 由於兩個成員都是以 `CLSCompliant(false)` 屬性來標記，因此編譯器沒有產生警告。 該類別也為這兩個方法提供符合 CLS 標準的替代項目。 通常，我們會將兩個多載加入至 `ToUTF16` 方法，以提供符合 CLS 標準的替代項目。 不過，因為方法無法根據傳回值來多載，所以符合 CLS 標準之方法的名稱與不符合 CLS 標準之方法的名稱不同。  
  
 [!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
 [!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]  
  
 如果您要開發的是應用程式而非程式庫 (也就是說，如果您不會公開可由其他應用程式開發人員使用的類型或成員)，則您的應用程式所使用之程式項目的 CLS 符合性，只有在您的語言不支援這些項目時才需要考慮。 在這種情況下，當您嘗試使用不符合 CLS 標準的項目時，您的語言編譯器會產生錯誤。  
  
<a name="CrossLang"></a>   
## <a name="cross-language-interoperability"></a>跨語言互通性  
 語言獨立性的意義可能有許多種。 其中一種意義是指能夠順利使用以某種語言撰寫的應用程式中，以另一種語言撰寫的類型，這種意義將在[語言獨立性和語言獨立元件](../../docs/standard/language-independence-and-language-independent-components.md)中討論。 第二種意義則是本文重點所在，是指將多種語言撰寫的程式碼合併至單一 .NET Framework 組件中。  
  
 下列範例會建立名為 Utilities.dll 的類別程式庫，其中包含兩個類別 `NumericLib` 和 `StringLib`，藉以說明跨語言互通性。 `NumericLib` 類別是以 C# 撰寫，`StringLib` 類別是以 Visual Basic 撰寫。 以下是 StringUtil.vb 的原始程式碼，當中包含它的 `ToTitleCase` 類別中的單一成員 `StringLib`。  
  
 [!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]  
  
 以下是 NumberUtil.cs 的原始程式碼，它會定義擁有 `NumericLib` 和 `IsEven` 這兩個成員的 `NearZero` 類別。  
  
 [!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]  
  
 若要將兩個類別封裝在單一組件中，您必須將它們編譯成模組。 若要將 Visual Basic 原始程式碼檔編譯至模組中，請使用這個命令：  
  
```console  
vbc /t:module StringUtil.vb   
```  
  
 如需 Visual Basic 編譯器的命令列語法詳細資訊，請參閱[從命令列建置](../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。  
  
 若要將 C# 原始程式碼檔編譯至模組中，請使用這個命令：  
  
```console  
csc /t:module NumberUtil.cs  
```  
  
 如需 C# 編譯器的命令列語法詳細資訊，請參閱[使用 csc.exe 建置命令列](../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  
  
 然後使用[連結器選項](/cpp/build/reference/linker-options)將這兩個模組編譯成一個組件：  
  
```console  
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll   
```  
  
 接著，下列範例會呼叫 `NumericLib.NearZero` 和 `StringLib.ToTitleCase` 方法。 請注意，Visual Basic 程式碼和 C# 程式碼都能存取這兩個類別中的方法。  
  
 [!code-csharp[Conceptual.CrossLanguage#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/useutilities1.cs#3)]
 [!code-vb[Conceptual.CrossLanguage#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/useutilities1.vb#3)]  
  
 若要編譯 Visual Basic 程式碼，請使用這個命令：  
  
```console  
vbc example.vb /r:UtilityLib.dll  
```  
  
 若要使用 C# 編譯，請將編譯器名稱從 **vbc** 變更為 **csc**，並且將副檔名從 .vb 變更為 .cs：  
  
```console  
csc example.cs /r:UtilityLib.dll  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.CLSCompliantAttribute>
