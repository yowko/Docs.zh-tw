---
title: 'How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents'
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 2edaf7ba540035fbf2f49ba78b41ab99f8889391
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082424"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a>How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents
XML 結構描述定義工具 (Xsd.exe) 讓您產生說明類別的 XML 結構描述或產生由 XML 結構描述定義的類別。 下列程序將說明如何執行這些作業。  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a>產生符合特定結構描述的類別  
  
1.  開啟命令提示字元。  
  
2.  將 XML 結構描述當成引數傳遞至 XML 結構描述定義工具，以建立一組類別精確地符合 XML 結構描述，例如：  
  
    ```  
    xsd mySchema.xsd  
    ```  
  
     此工具只能處理參考 2001 年 3 月 16 日全球資訊網協會 XML 規格的結構描述。 換句話說，XML 結構描述命名空間必須是"http://www.w3.org/2001/XMLSchema」 在下列範例所示。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    ```  
  
3.  視需要，使用方法、屬性或欄位來變更類別。 如需使用屬性修改類別的詳細資訊，請參閱[使用屬性控制 XML 序列化](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)和[控制編碼 SOAP 序列化的屬性](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)。  
  
 檢查在序列化一個類別 (或多個類別) 時產生的 XML 資料流結構描述，通常很有用。 例如，您可發佈結構描述供其他人使用，或是將它與一個您想要達到符合性的結構描述比較。  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a>從一組類別產生 XML 結構描述文件  
  
1.  將類別編譯為 DLL。  
  
2.  開啟命令提示字元。  
  
3.  將 DLL 當成引數傳遞給 Xsd.exe，例如：  
  
    ```  
    xsd MyFile.dll  
    ```  
  
     將寫入結構描述，以 "schema0.xsd" 名稱開始。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataSet>  
- [XML 結構描述定義工具和 XML 序列化](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
- [XML 序列化簡介](../../../docs/standard/serialization/introducing-xml-serialization.md)  
- [XML 結構描述定義工具 (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
- <xref:System.Xml.Serialization.XmlSerializer>  
- [如何：序列化物件](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [如何：還原序列化物件](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
