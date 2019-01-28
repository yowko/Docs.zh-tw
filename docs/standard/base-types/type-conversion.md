---
title: .NET Framework 中的類型轉換
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- widening conversions
- explicit conversions
- narrowing conversions
- type conversion, about type conversion
- type conversion
- converting types
- narrowing coercion
- Explicit operator
- IConvertible interface
- base types, converting
- op_Implicit method
- widening coercion
- op_Explicit method
- Convert class
- implicit conversions
- Implicit operator
- data types [.NET Framework], converting
ms.assetid: ba36154f-064c-47d3-9f05-72f93a7ca96d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04ed4dcaab8d39d8a34cadef8285ea8307f198c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659757"
---
# <a name="type-conversion-in-the-net-framework"></a>.NET Framework 中的類型轉換
<a name="top"></a>每個值都有相關聯的類型，該類型定義屬性，例如配置給值的空間量、能夠擁有的可能值範圍，以及提供的成員。 許多值都可以表示成多種類型。 例如，數值 4 就可以表示成整數值或浮點 (Floating-Point) 值。 類型轉換會建立新類型的值，與舊類型的值相等，但是不一定會保留原始物件的識別 (或實際的值)。  
  
 .NET Framework 自動支援下列轉換︰  
  
-   從衍生類別轉換成基底類別。 舉例來說，這表示任何類別或結構的執行個體都可以轉換成 <xref:System.Object> 執行個體。  這種轉換不需要轉型或轉換運算子。  
  
-   從基底類別轉換回原始的衍生類別。 在 C# 中，這種轉換需要轉型運算子。 在 Visual Basic 中，如果已 `Option Strict` 開啟則需要 `CType` 運算子。  
  
-   從實作介面的類型轉換成代表該介面的介面物件。 這種轉換不需要轉型或轉換運算子。  
  
-   從介面物件轉換回實作該介面的原始類型。  在 C# 中，這種轉換需要轉型運算子。 在 Visual Basic 中，如果已 `Option Strict` 開啟則需要 `CType` 運算子。  
  
 除了這些自動轉換以外，[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 還提供多項支援自訂類型轉換的功能。 這些需求包括下列各項：  
  
-   `Implicit` 運算子，這個運算子定義類型之間可用的擴展轉換。 如需詳細資訊，請參閱[使用 Implicit 運算子的隱含轉換](#implicit_conversion_with_the_implicit_operator)一節。  
  
-   `Explicit` 運算子，這個運算子定義類型之間可用的縮小轉換。 如需詳細資訊，請參閱[使用 Explicit 運算子的明確轉換](#explicit_conversion_with_the_explicit_operator)一節。  
  
-   <xref:System.IConvertible> 介面，這個介面定義轉換至每一個基底 .NET Framework 資料類型的方式。 如需詳細資訊，請參閱 [IConvertible 介面](#the_iconvertible_interface)一節。  
  
-   <xref:System.Convert> 類別，這個類別提供一組方法，這些方法實作 <xref:System.IConvertible> 介面中的方法。 如需詳細資訊，請參閱 [Convert 類別](#Convert)一節。  
  
-   <xref:System.ComponentModel.TypeConverter> 類別，這個類別是基底類別，可以擴充來支援從指定的類型轉換至其他任何類型。 如需詳細資訊，請參閱 [TypeConverter 類別](#the_typeconverter_class)一節。  
  
<a name="implicit_conversion_with_the_implicit_operator"></a>   
## <a name="implicit-conversion-with-the-implicit-operator"></a>使用隱含運算子的隱含轉換  
 擴展轉換包含從現有類型的值來建立新的值，這個類型具有比目標類型更嚴格的範圍或更受限制的成員清單。 擴展轉換不可能導致資料遺失 (雖然可能導致精確度降低)。 因為不可能遺失資料，編譯器可以隱含地 (或直接地) 處理轉換，而不需要使用明確的轉換方法或轉型運算子。  
  
> [!NOTE]
>  雖然執行隱含轉換的程式碼可以呼叫轉換方法或使用轉型運算子，但支援隱含轉換的編譯器並不需要這些動作。  
  
 例如，<xref:System.Decimal> 類型支援從 <xref:System.Byte>、<xref:System.Char>、<xref:System.Int16>、<xref:System.Int32>、<xref:System.Int64>、<xref:System.SByte>、<xref:System.UInt16>、<xref:System.UInt32> 和 <xref:System.UInt64> 值的隱含轉換。 下列範例說明其中一部分隱含轉換在指派值給 <xref:System.Decimal> 變數時的情形。  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 如果特定的語言編譯器支援自訂運算子，您也可以在自己的自訂類型中定義隱含轉換。 下列範例針對使用正負號和大小表示之名為 `ByteWithSign` 的帶正負號位元組資料類型，提供部分實作。 它支援將 <xref:System.Byte> 和 <xref:System.SByte> 值隱含轉換為 `ByteWithSign` 值。  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 然後，用戶端程式碼可以宣告 `ByteWithSign` 變數並指派 <xref:System.Byte> 和 <xref:System.SByte> 值給它，而不需要執行任何明確的轉換，也不需要使用任何轉型運算子，如下列範例所示。  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  
  
 [回到頁首](#top)  
  
<a name="explicit_conversion_with_the_explicit_operator"></a>   
## <a name="explicit-conversion-with-the-explicit-operator"></a>使用明確運算子的明確轉換  
 縮小轉換包含從現有類型的值來建立新的值，這個類型具有比目標類型更廣的範圍或更大的成員清單。 因為縮小轉換可能導致資料遺失，編譯器通常會要求必須透過呼叫轉換方法或轉型運算子來明確執行轉換。 也就是說，開發人員程式碼中必須明確處理轉換。  
  
> [!NOTE]
>  縮小轉換需要轉換方法或轉型運算子的主要目的是讓開發人員知道可能遺失資料，或可能發生 <xref:System.OverflowException>，以便在程式碼中處理。 不過，某些編譯器可能會放寬這項需求。 例如，在 Visual Basic 中，如果 `Option Strict` 已關閉 (此為預設)，則 Visual Basic 編譯器會嘗試隱含地執行縮小轉換。  
  
 例如，<xref:System.UInt32>、<xref:System.Int64> 和 <xref:System.UInt64> 資料類型的範圍超過 <xref:System.Int32> 資料類型的範圍，如下表所示。  
  
|類型|與 Int32 的範圍比較|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType> 大於 <xref:System.Int32.MaxValue?displayProperty=nameWithType>，而 <xref:System.Int64.MinValue?displayProperty=nameWithType> 小於 (負值範圍大於) <xref:System.Int32.MinValue?displayProperty=nameWithType>。|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType> 大於 <xref:System.Int32.MaxValue?displayProperty=nameWithType>。|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType> 大於 <xref:System.Int32.MaxValue?displayProperty=nameWithType>。|  
  
 為了處理縮小轉換，[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 允許類型定義 `Explicit` 運算子。 然後，個別語言編譯器就可以使用自己的語法來實作這個運算子，也可以呼叫 <xref:System.Convert> 類別的成員來執行轉換。 (如需 <xref:System.Convert> 類別的詳細資訊，請參閱本主題稍後的 [Convert 類別](#Convert))。下列範例說明如何使用語言功能，處理從這些可能超出範圍的整數值至 <xref:System.Int32> 值的明確轉換。  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 明確轉換在不同的語言中可能會產生不同的結果，這些結果可能與對應的 <xref:System.Convert> 方法所傳回的值不同。 例如，如果 <xref:System.Double> 值 12.63251 轉換為 <xref:System.Int32>，則 Visual Basic `CInt` 方法與 .NET Framework <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> 方法都會四捨五入 <xref:System.Double> 而傳回 13，但 C# `(int)` 運算子會截斷 <xref:System.Double> 而傳回 12。 同樣地，C# `(int)` 運算子不支援布林值對整數的轉換，但 Visual Basic `CInt` 方法會將 `true` 的值轉換為 -1。 另一方面，<xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> 方法會將 `true` 的值轉換為 1。  
  
 大多數的編譯器都允許明確轉換以已檢查或未檢查的方式執行。 如果執行已檢查的轉換，當要轉換之類型的值不在目標類型的範圍內時，則會擲回 <xref:System.OverflowException>。 在同樣的狀況下執行未檢查的轉換時，轉換可能不會擲回例外狀況，但實際行為會變得不明確，且可能產生不正確的值。  
  
> [!NOTE]
>  在 C# 中，已檢查的轉換可以透過使用 `checked` 關鍵字搭配轉型運算子來執行，也可以指定 `/checked+` 編譯器選項來執行。 相反地，未檢查的轉換可使用 `unchecked` 關鍵字搭配轉型運算子來執行，或可以指定 `/checked-` 編譯器選項來執行。 根據預設，明確轉換是未檢查的。 在 Visual Basic 中，已檢查的轉換可藉由清除專案的 [進階編譯器設定] 對話方塊中的 [移除整數的溢位檢查] 核取方塊來執行，或可以指定 `/removeintchecks-` 編譯器選項來執行。 相反地，未檢查的轉換可以藉由選取專案的 [進階編譯器設定] 對話方塊中的 [移除整數的溢位檢查] 核取方塊來執行，也可以指定 `/removeintchecks+` 編譯器選項來執行。 根據預設，明確轉換是檢查的。  
  
 下列 C# 範例使用 `checked` 和 `unchecked` 關鍵字，說明將超出 <xref:System.Byte> 範圍的值轉換為 <xref:System.Byte> 時的行為差異。 已檢查的轉換會擲回例外狀況，但未檢查的轉換會指派 <xref:System.Byte.MaxValue?displayProperty=nameWithType> 給 <xref:System.Byte> 變數。  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 如果特定的語言編譯器支援自訂多載運算子，您也可以在自己的自訂類型中定義明確轉換。 下列範例針對使用正負號和大小表示之名為 `ByteWithSign` 的帶正負號位元組資料類型，提供部分實作。 它支援將 <xref:System.Int32> 和 <xref:System.UInt32> 值明確轉換為 `ByteWithSign` 值。  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 然後，用戶端程式碼可以宣告 `ByteWithSign` 變數並指派 <xref:System.Int32> 和 <xref:System.UInt32> 值給它 (如果指派包含轉型運算子或轉換方法的話)，如下列範例所示。  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  
  
 [回到頁首](#top)  
  
<a name="the_iconvertible_interface"></a>   
## <a name="the-iconvertible-interface"></a>IConvertible 介面  
 為了支援從任何類型轉換至通用語言執行平台基底類型，[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 提供 <xref:System.IConvertible> 介面。 實作類型需要提供下列項目：  
  
-   傳回實作類型之 <xref:System.TypeCode> 的方法。  
  
-   將實作類型轉換為每一個通用語言執行平台基底類型 (<xref:System.Boolean>、<xref:System.Byte>、<xref:System.DateTime>、<xref:System.Decimal>、<xref:System.Double> 等) 的方法。  
  
-   將實作類型的執行個體轉換為另一個指定之類型的通用轉換方法。 不支援的轉換應該擲回 <xref:System.InvalidCastException>。  
  
 每一個通用語言執行平台基底類型 (也就是 <xref:System.Boolean>、<xref:System.Byte>、<xref:System.Char>、<xref:System.DateTime>、<xref:System.Decimal>、<xref:System.Double>、<xref:System.Int16>、<xref:System.Int32>、<xref:System.Int64>、<xref:System.SByte>、<xref:System.Single>、<xref:System.String>、<xref:System.UInt16>、<xref:System.UInt32> 和 <xref:System.UInt64>)，以及 <xref:System.DBNull> 和 <xref:System.Enum> 類型，都實作 <xref:System.IConvertible> 介面。 不過，這些都是明確的介面實作，且只能透過 <xref:System.IConvertible> 介面變數來呼叫轉換方法，如下列範例所示。 這個範例將 <xref:System.Int32> 值轉換為其對等的 <xref:System.Char> 值。  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 由於必須呼叫其介面上的轉換方法，而不是呼叫實作類型上的轉換方法，這種需求使得明確介面實作相當耗費資源。 相反地，在通用語言執行平台基底類型之間轉換時，我們建議您呼叫 <xref:System.Convert> 類別的適當成員。 如需詳細資訊，請參閱下一節 [Convert 類別](#Convert)。  
  
> [!NOTE]
>  除了 <xref:System.IConvertible> 提供的 <xref:System.Convert> 介面和 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 類別之外，個別語言可能還會提供執行轉換的方式。 例如，C# 使用轉型 (Casting) 運算子、Visual Basic 使用編譯器實作的轉換函式，例如 `CType`、`CInt` 和 `DirectCast`。  
  
 在大多數情況下，<xref:System.IConvertible> 介面的設計主要是支援在 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中的各基底類型之間轉換。 不過，也可以使用自訂類型來實作介面，以支援從該類型轉換至其他自訂類型。 如需詳細資訊，請參閱本主題稍後的[使用 ChangeType 方法的自訂轉換](#ChangeType)一節。  
  
 [回到頁首](#top)  
  
<a name="Convert"></a>   
## <a name="the-convert-class"></a>Convert 類別  
 雖然可以呼叫每一個基底類別的 <xref:System.IConvertible> 介面實作來執行類型轉換，但建議的語言中立方式是呼叫 <xref:System.Convert?displayProperty=nameWithType> 類別的方法，在不同的基底類型之間轉換。 此外，也可以使用 <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 方法將指定的自訂類型轉換為另一種類型。  
  
### <a name="conversions-between-base-types"></a>在基底類型之間轉換  
 <xref:System.Convert> 類別提供在基底類型之間轉換的語言中立方式，且所有以通用語言執行平台為目標的語言都可以使用。 它對於擴展和縮小轉換提供一組完整的方法，且對於不支援的轉換會擲回 <xref:System.InvalidCastException> (例如，將 <xref:System.DateTime> 值轉換為整數值)。 縮小轉換是在已檢查的情況下執行，如果轉換失敗，則會擲回 <xref:System.OverflowException>。  
  
> [!IMPORTANT]
>  因為 <xref:System.Convert> 類別包含在每一個基底類型之間來回轉換的方法，所以不需要呼叫每一個基底類型的 <xref:System.IConvertible> 明確介面實作。  
  
 下列範例說明如何使用 <xref:System.Convert?displayProperty=nameWithType> 類別，在 .NET Framework 基底類型之間執行數個擴展和縮小轉換。  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 在某些情況下，尤其是在浮點值之間來回轉換時，即使沒有擲回 <xref:System.OverflowException>，轉換也可能會降低精確度。 下列範例說明這種精確度降低情況。 在第一種情況下，<xref:System.Decimal> 值在轉換為 <xref:System.Double> 時會降低精確度 (有效位數較少)。 在第二種情況下，<xref:System.Double> 值會從 42.72 四捨五入為 43，以完成轉換。  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 如需同時列出 <xref:System.Convert> 類別所支援之擴展和縮小轉換的表格，請參閱[類型轉換表](../../../docs/standard/base-types/conversion-tables.md)。  
  
<a name="ChangeType"></a>   
### <a name="custom-conversions-with-the-changetype-method"></a>使用 ChangeType 方法的自訂轉換  
 <xref:System.Convert> 類別除了支援轉換為每一個基底類型，也可以用於將自訂類型轉換為一個或多個預先定義的類型。 這種轉換由 <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 方法執行，而這個方法會進一步包裝對於 <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> 參數之 `value` 方法的呼叫。 這表示由 `value` 參數所表示的物件必須提供 <xref:System.IConvertible> 介面的實作。  
  
> [!NOTE]
>  由於 <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> 和 <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 方法會使用 <xref:System.Type> 物件指定轉換 `value` 的目標類型，因此這兩種方法可以在編譯時期用來動態轉換不明類型的物件。 但請注意，<xref:System.IConvertible> 的 `value` 實作仍然必須支援這項轉換。  
  
 下列範例說明 <xref:System.IConvertible> 介面可能的實作，這種實作允許 `TemperatureCelsius` 物件轉換為 `TemperatureFahrenheit` 物件，反之亦然。 範例中定義一個基底類別 `Temperature`，這個類別實作 <xref:System.IConvertible> 介面並覆寫 <xref:System.Object.ToString%2A?displayProperty=nameWithType> 方法。 衍生的 `TemperatureCelsius` 和 `TemperatureFahrenheit` 類別分別覆寫基底類別的 `ToType` 和 `ToString` 方法。  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 下列範例說明對這些 <xref:System.IConvertible> 實作的多個呼叫，以將 `TemperatureCelsius` 物件轉換為 `TemperatureFahrenheit` 物件，反之亦然。  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  
  
 [回到頁首](#top)  
  
<a name="the_typeconverter_class"></a>   
## <a name="the-typeconverter-class"></a>TypeConverter 類別  
 .NET Framework 也可讓您延伸 <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> 類別，並透過 <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> 屬性來建立類型轉換子與類型之間的關聯，以定義自訂類型的類型轉換子。 下表特別強調這種作法與實作自訂類型之 <xref:System.IConvertible> 介面的差異。  
  
> [!NOTE]
>  只要自訂類型有為其定義的類型轉換子，即會提供設計階段支援給自訂類型。  
  
|使用 TypeConverter 的轉換|使用 IConvertible 的轉換|  
|------------------------------------|-----------------------------------|  
|是從 <xref:System.ComponentModel.TypeConverter> 衍生另外一個類別，以針對自訂類型來實作。 透過套用 <xref:System.ComponentModel.TypeConverterAttribute> 屬性，將這個衍生類別與自訂類型建立關聯。|是由自訂類型所實作來執行轉換。 該類型的使用者在該類型上叫用 <xref:System.IConvertible> 轉換方法。|  
|可以在設計階段和在執行階段兩處使用。|只能在執行階段使用。|  
|使用反映，因此，速度比 <xref:System.IConvertible> 所啟用的轉換還要慢。|不使用反映。|  
|允許在自訂類型與其他資料類型之間的雙向類型轉換。 例如，針對 <xref:System.ComponentModel.TypeConverter> 所定義的 `MyType` 允許從 `MyType` 轉換為 <xref:System.String>，也允許從 <xref:System.String> 轉換為 `MyType`。|允許從自訂類型轉換為其他資料類型，但不允許從其他資料類型轉換為自訂類型。|  
  
 如需使用類型轉換子執行轉換的詳細資訊，請參閱 <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.IConvertible>
- [類型轉換表](../../../docs/standard/base-types/conversion-tables.md)
