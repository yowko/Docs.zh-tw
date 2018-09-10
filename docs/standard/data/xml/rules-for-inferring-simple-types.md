---
title: 推斷簡單型別的規則
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 394624d6-4da0-430a-8a88-46efe40f14de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd5426de388ba2c7a22d66ce01d56a3139e36e38
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271230"
---
# <a name="rules-for-inferring-simple-types"></a>推斷簡單型別的規則
說明 <xref:System.Xml.Schema.XmlSchemaInference> 類別如何推斷屬性和項目的資料型別。  
  
 <xref:System.Xml.Schema.XmlSchemaInference> 類別會將屬性和項目的資料型別推斷為簡單型別。 本節將說明可能的推斷型別、多種不同的值如何調節為單一型別，以及如何處理結構描述定義的 `xsi` 屬性。  
  
## <a name="inferred-types"></a>推斷的型別  
 <xref:System.Xml.Schema.XmlSchemaInference> 類別會將項目和屬性值推斷為簡單型別，並在產生的結構描述內包含型別屬性。 所有推斷的型別皆為簡單型別。 基底型別或 Facet 都不會納入結果結構描述中。  
  
 在 XML 文件中發現的值會個別進行檢查。 對某個值進行檢查時，即會推斷其型別。 若在推斷屬性或項目的型別後，發現該屬性或項目的值不符合目前推斷的型別，<xref:System.Xml.Schema.XmlSchemaInference> 類別就會針對每組規則提升型別。 這些規則將在本主題稍後的＜型別提升＞一節中討論。  
  
 下列表格列出可能出現在結果結構描述中的推斷型別。  
  
|簡單型別|描述|  
|-----------------|-----------------|  
|boolean|True、False、0、1。|  
|byte|介於 -128 與 127 之間的整數。|  
|unsignedByte|介於 0 與 255 之間的整數。|  
|short|介於 -32768 與 32767 之間的整數。|  
|unsignedShort|介於 0 與 65535 之間的整數。|  
|int|介於 -2147483648 與 2147483647 之間的整數。|  
|unsignedInt|介於 0 與 4294967295 之間的整數。|  
|long|介於 -9223372036854775808 與 9223372036854775807 之間的整數。|  
|unsignedLong|介於 0 與 18446744073709551615 之間的整數。|  
|整數|可能會以 "-" 開頭的有限數值。|  
|decimal|含有 0 至 28 位精準度的數值。|  
|float|其後可以為 "E" 或 "e" 的十進位數，最後再接上代表指數的整數值。 十進位值可介於 -16777216 與 16777216 之間。 指數值可介於 –149 與 104 之間。<br /><br /> 浮點數允許用特殊的值代表無限值與非數字值。 浮點數的特殊值包括：0, -0, INF, -INF, NaN。|  
|double|與浮點數相同，不同之處在於十進位值可介於 -9007199254740992 與 9007199254740992 之間，而指數值可介於 –1075 與 970 之間。<br /><br /> 雙精度浮點數允許用特殊的值代表無限值與非數字值。 浮點數的特殊值包括：0, -0, INF, -INF, NaN。|  
|持續期間|W3C 期間格式。|  
|dateTime|W3C 日期時間格式。|  
|時間|W3C 時間格式。|  
|date|年份值限定於 0001 與 9999 之間。|  
|gYearMonth|W3C 的西曆月份與年份格式。|  
|字串|一或多個 Unicode 字元。|  
  
## <a name="type-promotion"></a>類型提升  
 <xref:System.Xml.Schema.XmlSchemaInference> 類別會逐一檢查屬性與項目的值。 若發現任何值，就會推斷最嚴格且不帶正負號的型別。 若在推斷屬性或項目的型別後，發現新的值不符合目前推斷的型別，則推斷的型別會提升為目前推斷型別與新值均適用的新型別。 <xref:System.Xml.Schema.XmlSchemaInference> 類別在提升推斷的型別時，會考量先前的值。  
  
 例如，請考量下列兩份 XML 文件中的 XML 片段：  
  
 `<MyElement1 attr1="12" />`  
  
 `<MyElement1 attr1="52344" />`  
  
 當發現第一個 `attr1` 值時，會根據 `attr1` 的值將 `unsignedByte` 的型別推斷為 `12`。 當發現第二個 `attr1` 時，其型別會根據目前推斷型別 `unsignedShort` 與目前的 `unsignedByte` 值被提升為 `52344`。  
  
 此時，請考量下列兩份 XML 文件中的 XML：  
  
 `<MyElement2 attr2="0" />`  
  
 `<MyElement2 attr2="true" />`  
  
 當發現第一個 `attr2` 值時，會根據 `attr2` 的值將 `unsignedByte` 的型別推斷為 `0`。 當發現第二個 `attr2` 時，此型別會根據目前推斷型別 `string` 和目前的 `unsignedByte` 值提升為 `true`，因為在提升推斷型別時，<xref:System.Xml.Schema.XmlSchemaInference> 類別會考量之前的值。 然而，若不是像上述範例一樣在兩個不同的 XML 文件中發現兩個 `attr2`，而是在相同的 XML 文件中發現時，`attr2` 將會被推斷為 `boolean`。  
  
### <a name="ignored-attributes-from-the-httpwwww3org2001xmlschema-instance-namespace"></a>http://www.w3.org/2001/XMLSchema-instance 命名空間的被忽略屬性  
 下列結構描述定義的屬性會在結構描述推斷期間遭到忽略。  
  
|屬性|描述|  
|---------------|-----------------|  
|`xsi:type`|若發現項目指定了 `xsi:type`，則 `xsi:type` 將被忽略。|  
|`xsi:nil`|若發現項目具有 `xsi:nil` 屬性，表示其推斷結構描述中的項目宣告具有 `nillable="true"` 值。 將 `xsi:nil` 屬性設為 `true` 的項目不能有子項目。|  
|`xsi:schemaLocation`|如果發現 `xsi:schemaLocation`，則會加以忽略。|  
|`xsi:noNamespaceSchemaLocation`|如果發現 `xsi:noNamespaceSchemaLocation`，則會加以忽略。|  
  
## <a name="see-also"></a>另請參閱

- [XML 結構描述物件模型 (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
- [從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)  
- [推斷結構描述節點類型和結構的規則](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
