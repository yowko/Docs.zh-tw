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
ms.openlocfilehash: 57f6caa00806f4874cb8070805e8b6784ec82e40
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956795"
---
# <a name="data-type-summary-visual-basic"></a>資料類型摘要 (Visual Basic)
下表顯示 Visual Basic 的資料類型、其支援的通用語言執行平臺類型、其名義儲存體配置, 以及其值範圍。  
  
|Visual Basic 類型|Common language runtime 類型結構|名義儲存體配置|數值範圍|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[布林值](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|取決於執行平臺|`True` 或 `False`|  
|[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 個位元組|0到 255 (不帶正負號)|  
|[Char](../../../visual-basic/language-reference/data-types/char-data-type.md)(單一字元)|<xref:System.Char>|2 個位元組|0到 65535 (不帶正負號)|  
|[Date](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 個位元組|0:00:00 (午夜), 位於0001年1月1日至 11:59:59 PM, 9999 年12月31日|  
|[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 個位元組|0到 +/-79228162514264337593543950335 (+/-7.9...E + 28) <sup>†</sup> , 沒有小數點;0到 +/-7.9228162514264337593543950335, 小數點右邊有28個位置;<br /><br /> 最小的非零數位是 +/-0.0000000000000000000000000001 (+/-1E-28) <sup>†</sup>|  
|[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)(雙精確度浮點數)|<xref:System.Double>|8 個位元組|-1.79769313486231570 e + 308 到-4.94065645841246544 E-324 <sup>†</sup>代表負值;<br /><br /> 4.94065645841246544 e-324 到 1.79769313486231570 E + 308 <sup>†</sup>的正值|  
|[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 個位元組|-2147483648 到 2147483647 (帶正負號)|  
|[長](../../../visual-basic/language-reference/data-types/long-data-type.md)(長整數)|<xref:System.Int64>|8 個位元組|-9223372036854775808 到 9223372036854775807 (9.2 ... E + 18 <sup>†</sup>) (帶正負號)|  
|[物件](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object>課堂|32位平臺上4個位元組<br /><br /> 64位平臺上8個位元組|任何類型都可以儲存在類型的變數中。`Object`|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 個位元組|-128 到 127 (帶正負號)|  
|[Short](../../../visual-basic/language-reference/data-types/short-data-type.md)(短整數)|<xref:System.Int16>|2 個位元組|-32768 到 32767 (帶正負號)|  
|[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)(單精確度浮點數)|<xref:System.Single>|4 個位元組|-3.4028235 e + 38 到-1.401298 E-45 <sup>†</sup>代表負值;<br /><br /> 1.401298 e-45 到 3.4028235 E + 38 <sup>†</sup>適用于正值|  
|[字串](../../../visual-basic/language-reference/data-types/string-data-type.md)(可變長度)|<xref:System.String>課堂|取決於執行平臺|0到大約2000000000的 Unicode 字元|  
|[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 個位元組|0到 4294967295 (不帶正負號)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 個位元組|0到 18446744073709551615 (1.8 ... E + 19 <sup>†</sup>) (不帶正負號)|  
|[使用者定義](../../../visual-basic/language-reference/data-types/user-defined-data-type.md)表示|(繼承自<xref:System.ValueType>)|取決於執行平臺|結構的每個成員都有由其資料類型決定的範圍, 而且與其他成員的範圍無關|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 個位元組|0到 65535 (不帶正負號)|  
  
 <sup>†</sup>在*科學標記法*中, "E" 是指10的乘冪。 因此, 3.56 E + 2 表示 3.56 x 10<sup>2</sup>或 356, 而 3.56 e-2 表示 3.56/10<sup>2</sup>或0.0356。  
  
> [!NOTE]
> 若為包含文字的字串, <xref:Microsoft.VisualBasic.Strings.StrConv%2A>請使用函式, 從一種文字格式轉換成另一種。  
  
 除了在宣告語句中指定資料類型之外, 您還可以使用類型字元來強制某些程式設計項目的資料類型。 請參閱[類型字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)。  
  
## <a name="memory-consumption"></a>記憶體消耗量  
 當您宣告基本資料類型時, 假設其記憶體耗用量與其名義儲存體配置相同, 就不安全。 這是因為下列考慮:  
  
- **儲存體指派。** Common language runtime 可以根據您的應用程式執行所在平臺的目前特性來指派儲存體。 如果記憶體幾乎已滿, 它可能會盡可能緊密地封裝您宣告的元素。 在其他情況下, 它可能會將其記憶體位址對齊自然硬體界限, 以優化效能。  
  
- **平臺寬度。** 64位平臺上的儲存體指派與32位平臺上的指派不同。  
  
### <a name="composite-data-types"></a>複合資料類型  
 相同的考慮適用于複合資料型別的每個成員, 例如結構或陣列。 您不能只是將類型成員的名義儲存配置加在一起。 此外, 還有其他考慮, 如下所示:  
  
- **投影機.** 有些複合類型有額外的記憶體需求。 例如, 陣列本身會使用額外的記憶體, 也會針對每個維度使用。 在32位平臺上, 此額外負荷目前為12個位元組, 加上每個維度8個位元組。 在64位平臺上, 這項需求加倍。  
  
- **儲存版面配置。** 您無法安全地假設記憶體中的儲存順序與您的宣告順序相同。 您甚至無法對位元組對齊進行假設, 例如2位元組或4位元組的界限。 如果您要定義類別或結構, 而且需要控制其成員的儲存配置, 您可以將<xref:System.Runtime.InteropServices.StructLayoutAttribute>屬性 (attribute) 套用至類別或結構。  
  
### <a name="object-overhead"></a>物件負荷  
 除了資料類型中包含的資料以外,參考任何基本或複合資料型別的也會使用4個位元組。`Object`  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Strings.StrConv%2A>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [類型字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
