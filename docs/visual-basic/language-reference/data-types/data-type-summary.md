---
title: "Data Type Summary (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Boolean data type, supported types in Visual Basic"
  - "storage, order of storage"
  - "data types [Visual Basic], Visual Basic"
  - "Single data type, supported types in Visual Basic"
  - "notation, scientific"
  - "memory requirements, data types"
  - "user-defined data types, Visual Basic"
  - "Date data type, Visual Basic"
  - "Visual Basic, data types"
  - "storage, allocation"
  - "Integer data type, Visual Basic data types"
  - "storage, space"
  - "Variant data types, supported types in Visual Basic"
  - "Char data type, Visual Basic data types"
  - "intrinsic data types"
  - "memory consumption, data types"
  - "single-precision numbers"
  - "data types [Visual Basic], order of storage"
  - "Long data type, supported types in Visual Basic"
  - "String data type, Visual Basic data types"
  - "storage order, data types"
  - "StructLayoutAttribute class, Visual Basic data type storage"
  - "scientific notation"
  - "Double data type, Visual Basic data types"
  - "Byte data type, Visual Basic data types"
  - "Object data type, supported types in Visual Basic"
  - "data types [Visual Basic], storage allocation"
  - "double-precision numbers"
  - "data types [Visual Basic], summary"
  - "dates [Visual Basic], data types"
  - "strings [Visual Basic], data types"
  - "memory consumption"
  - "storage order, controlling in Visual Basic"
  - "data types [Visual Basic], memory requirements"
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Data Type Summary (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

下表顯示 Visual Basic 資料型別，它們對 Common Language Runtime 型別的支援、它們的表面儲存配置和數值範圍。  
  
|Visual Basic 型別|Common Language Runtime 型別結構|表面儲存配置|數值範圍|  
|---------------------|----------------------------------|------------|----------|  
|[Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|視實作平台而定|`True` 或 `False`|  
|[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 個位元組|0 至 255 \(不帶正負號\)|  
|[Char](../../../visual-basic/language-reference/data-types/char-data-type.md) \(單一字元\)|<xref:System.Char>|2 個位元組|0 至 65535 \(不帶正負號\)|  
|[日期](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 個位元組|0001 年 1 月 1 日 0:00:00 \(午夜\) 至 9999 年 12 月 31 日 11:59:59 PM|  
|[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 個位元組|0 到 \+\/\-79,228,162,514,264,337,593,543,950,335 \(\+\/\-7.9...E\+28\) <sup>†</sup> \(無小數點\)，0 到 \+\/\-7.9228162514264337593543950335 \(小數點右邊有 28 位數\)，<br /><br /> 最小的非零數字是 \+\/\-0.0000000000000000000000000001 \(\+\/\-1E\-28\) <sup>†</sup>|  
|[Double](../../../visual-basic/language-reference/data-types/double-data-type.md) \(雙精度浮點數\)|<xref:System.Double>|8 個位元組|\-1.79769313486231570E\+308 到 \-4.94065645841246544E\-324 <sup>†</sup> \(負值\)，<br /><br /> 4.94065645841246544E\-324 到 1.79769313486231570E\+308 <sup>†</sup> \(正值\)|  
|[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 個位元組|\-2,147,483,648 至 2,147,483,647 \(帶正負號\)|  
|[Long](../../../visual-basic/language-reference/data-types/long-data-type.md) \(長整數\)|<xref:System.Int64>|8 個位元組|\-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807 \(9.2...E\+18 <sup>†</sup>\) \(帶正負號\)|  
|[物件](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object> \(類別\)|32 位元平台上 4 個位元組<br /><br /> 64 位元平台上 8 個位元組|可以用 `Object` 型別之變數加以儲存的任何型別|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 個位元組|\-128 至 127 \(帶正負號\)|  
|[Short](../../../visual-basic/language-reference/data-types/short-data-type.md) \(短整數\)|<xref:System.Int16>|2 個位元組|\-32,768 至 32,767 \(帶正負號\)|  
|[Single](../../../visual-basic/language-reference/data-types/single-data-type.md) \(單精確度浮點數\)|<xref:System.Single>|4 個位元組|\-3.4028235E\+38 到 \-1.401298E\-45 <sup>†</sup> \(負值\)，<br /><br /> 1.401298E\-45 到 3.4028235E\+38 <sup>†</sup> \(正值\)|  
|[String](../../../visual-basic/language-reference/data-types/string-data-type.md) \(可變長度\)|<xref:System.String> \(類別\)|視實作平台而定|0 至大約二十億個 Unicode 字元|  
|[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 個位元組|0 至 4,294,967,295 \(不帶正負號\)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 個位元組|0 到 18,446,744,073,709,551,615 \(1.8...E\+19 <sup>†</sup>\) \(不帶正負號\)|  
|[User\-Defined](../../../visual-basic/language-reference/data-types/user-defined-data-type.md) \(結構\)|\(繼承自 <xref:System.ValueType>\)|視實作平台而定|結構的每個成員都有由其資料型別所決定的範圍，與其他成員的範圍無關|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 個位元組|0 至 65,535 \(不帶正負號\)|  
  
 <sup>†</sup> 在「*科學標記法*」\(Scientific Notation\) 中，E 代表乘冪 10。  因此 3.56E\+ 2 表示 3.56 x 10<sup>2</sup> 或 356，而 3.56E\-2 表示 3.56 \/ 10<sup>2</sup> 或 0.0356。  
  
> [!NOTE]
>  針對包含文字的字串，請使用 <xref:Microsoft.VisualBasic.Strings.StrConv%2A> 函式來從某一種文字格式轉換為另一種文字格式。  
  
 使用型別字元，以及指定資料型別之外宣告陳述式，您可以強制一些程式設計項目的資料型別。  請參閱 [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)。  
  
## 記憶體消耗量  
 當您宣告基本資料型別時，假設將它的記憶體消耗量與其表面儲存配置是相同的並不是安全的做法。  基於下列考量：  
  
-   **儲存體指派**：Common Language Runtime 會依據執行應用程式所在平台的目前特性來分配儲存區。  如果記憶體幾乎全滿，它就會盡量將宣告元素壓縮在一起。  在其他情況下，它可能會將其記憶體位址對齊自然硬體界限以取得最佳化效能。  
  
-   **平台寬度**：64 位元平台與 32 位元平台上的儲存體指派是不同的。  
  
### 複合資料型別  
 複合資料型別 \(例如結構或陣列\) 的每個成員都有相同的記憶體考量。  您不能只將型別成員的表面儲存配置加總。  請注意其他考量，如下所示：  
  
-   **負荷**：有些複合型別還有其他的記憶體需求。  例如，陣列本身和每個維度都需要使用額外的記憶體。  在 32 位元平台上，目前的耗用量是 12 個位元組加上每個維度的 8 個位元組。  在 64 位元平台上，需求則加倍。  
  
-   **儲存體佈置**：您也不能就將記憶體中的儲存順序視為與您宣告的順序相同。  您甚至無法對位元組對齊做假設，例如 2 位元組或 4 位元組界限。  如果您正在定義類別或結構，且需要控制其成員的儲存體配置，則可將 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性套用至類別或結構。  
  
### 物件負荷  
 參考任何基本或複合資料型別的 `Object` 除了包含在資料型別中的資料之外，還需使用 4 個位元組。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Strings.StrConv%2A>   
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)