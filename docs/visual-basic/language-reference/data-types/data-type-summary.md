---
title: 資料類型摘要 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Boolean data type [Visual Basic], supported types in Visual Basic
- storage [Visual Basic], order of storage
- data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], supported types in Visual Basic
- notation [Visual Basic], scientific
- memory requirements, data types
- user-defined data types [Visual Basic], Visual Basic
- Date data type [Visual Basic], Visual Basic
- Visual Basic, data types
- storage [Visual Basic], allocation
- Integer data type [Visual Basic], Visual Basic data types
- storage [Visual Basic], space
- Variant data types [Visual Basic], supported types in Visual Basic
- Char data type [Visual Basic], Visual Basic data types
- intrinsic data types [Visual Basic]
- memory consumption [Visual Basic], data types
- single-precision numbers
- data types [Visual Basic], order of storage
- Long data type [Visual Basic], supported types in Visual Basic
- String data type [Visual Basic], Visual Basic data types
- storage order, data types
- StructLayoutAttribute class, Visual Basic data type storage
- scientific notation
- Double data type [Visual Basic], Visual Basic data types
- Byte data type [Visual Basic], Visual Basic data types
- Object data type [Visual Basic], supported types in Visual Basic
- data types [Visual Basic], storage allocation
- double-precision numbers
- data types [Visual Basic], summary
- dates [Visual Basic], data types
- strings [Visual Basic], data types
- memory consumption
- storage order, controlling in Visual Basic
- data types [Visual Basic], memory requirements
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
ms.openlocfilehash: 8afeba3f88c4bfe6e1c9777f950c3b458665e340
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="data-type-summary-visual-basic"></a>資料類型摘要 (Visual Basic)
下表顯示 Visual Basic 資料類型、 其支援的 common language runtime 類型、 其表面的存放裝置配置和其值的範圍。  
  
|Visual Basic 型別|通用語言執行階段類型結構|名義型儲存體配置|數值範圍|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[布林值](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|作業取決於平台|`True` 或 `False`|  
|[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 個位元組|0 到 255 之間 （不帶正負號）|  
|[Char](../../../visual-basic/language-reference/data-types/char-data-type.md) （單一字元）|<xref:System.Char>|2 個位元組|0 到 65535 （不帶正負號）|  
|[Date](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 個位元組|0:00:00 （午夜） 11:59:59 PM 9999 年 12 月 31 日 0001 年 1 月 1 日|  
|[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 個位元組|0 到 + /-79228162514264337593543950335 (+ /-7.9 … E + 28) <sup>†</sup>不含小數點，0 到 + /--7.9228162514264337593543950335 有 28 小數位數;<br /><br /> 最小非零的數字是 + /-0.0000000000000000000000000001 （+ /-1E 28) <sup>†</sup>|  
|[Double](../../../visual-basic/language-reference/data-types/double-data-type.md) （雙精度浮點數）|<xref:System.Double>|8 個位元組|-1.79769313486231570 e + 308 到-4.94065645841246544 e-324 <sup>†</sup>負數的值;<br /><br /> 4.94065645841246544 e-324 1.79769313486231570 e + 308 到<sup>†</sup>的正數值|  
|[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 個位元組|-2147483648 到 2147483647 （帶正負號）|  
|[長](../../../visual-basic/language-reference/data-types/long-data-type.md)（長整數）|<xref:System.Int64>|8 個位元組|-9223372036854775808 到 9,223,372,036,854,775,807 (9.2 … E + 18 <sup>†</sup>) （帶正負號）|  
|[物件](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object> （類別）|在 32 位元平台上的 4 個位元組<br /><br /> 在 64 位元平台上為 8 個位元組|任何類型可以儲存在類型的變數 `Object`|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 個位元組|-128 到 127 （帶正負號）|  
|[簡短](../../../visual-basic/language-reference/data-types/short-data-type.md)（短整數）|<xref:System.Int16>|2 個位元組|-32,768 到 32,767 （帶正負號）|  
|[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)（單精確度浮點數）|<xref:System.Single>|4 個位元組|-3.4028235 e + 38 到-1.401298-45 <sup>†</sup>負數的值;<br /><br /> 1.401298-45 3.4028235 e + 38 到<sup>†</sup>的正數值|  
|[字串](../../../visual-basic/language-reference/data-types/string-data-type.md)（可變長度）|<xref:System.String> （類別）|作業取決於平台|0 到大約 2 10 億個 Unicode 字元|  
|[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 個位元組|0 到 4294967295 （不帶正負號）|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 個位元組|0 到 18446744073709551615 (1.8 … E + 19 <sup>†</sup>) （不帶正負號）|  
|[使用者定義](../../../visual-basic/language-reference/data-types/user-defined-data-type.md)（結構）|(繼承自<xref:System.ValueType>)|作業取決於平台|結構的每一個成員具有決定透過其資料類型且獨立於其他成員的範圍的範圍|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 個位元組|0 到 65535 （不帶正負號）|  
  
 <sup>†</sup>中*科學記號標記法*，"E"是指的 10 乘冪。 因此 3.56E + 2 表示 3.56 x 10<sup>2</sup>了 356，或 3.56E-2 表示 3.56 / 10<sup>2</sup>或 0.0356。  
  
> [!NOTE]
>  包含文字的字串，請使用<xref:Microsoft.VisualBasic.Strings.StrConv%2A>函式可從一個文字格式轉換為另一個。  
  
 除了宣告陳述式中指定的資料類型，您都可以使用的型別字元來強制執行一些程式設計項目資料的類型。 請參閱[輸入字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)。  
  
## <a name="memory-consumption"></a>記憶體消耗量  
 當您宣告基本資料類型時，它並不安全假設其記憶體耗用量是其表面的儲存體配置相同。 這是因為下列考量：  
  
-   **儲存體設定。** Common language runtime 可以指派儲存體，根據目前的應用程式執行所在的平台特性。 如果記憶體幾乎已滿時，它可能會盡可能一起組件成接近您宣告的項目。 在其他情況下，它可能會對齊實體硬體界限來最佳化效能其記憶體位址。  
  
-   **平台的寬度。** 在 64 位元平台上的儲存體設定是不同的 32 位元平台上。  
  
### <a name="composite-data-types"></a>複合資料類型  
 考量同樣適用於複合資料類型，例如結構或陣列的每個成員。 您不能只是將總表面儲存配置類型的成員。 此外，有其他考量，如下所示：  
  
-   **額外負荷。** 部分複合類型會有額外的記憶體需求。 例如，陣列的陣列本身以及每個維度會使用額外的記憶體。 在 32 位元平台上目前的耗用量是 12 個位元組，加上每個維度的 8 個位元組。 在 64 位元平台上，這項需求就會加倍。  
  
-   **儲存體的配置。** 您無法安全地假設在記憶體中的儲存體的順序是您宣告的順序相同。 您甚至不能假設位元組對齊，例如 2 或 4 個位元組的界限。 如果您要定義類別或結構，而且您需要控制其成員的儲存體配置，您可以套用<xref:System.Runtime.InteropServices.StructLayoutAttribute>屬性設定為類別或結構。  
  
### <a name="object-overhead"></a>物件的負擔  
 `Object`參考的任何基本或複合資料類型會使用 4 個位元組，除了資料類型中所包含的資料。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Strings.StrConv%2A>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [類型字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
