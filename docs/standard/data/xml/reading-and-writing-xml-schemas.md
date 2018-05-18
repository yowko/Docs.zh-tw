---
title: 讀取及寫入 XML 結構描述
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b652adb27c3bb075fe86c09d7c9ab33511371279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="reading-and-writing-xml-schemas"></a>讀取及寫入 XML 結構描述
結構描述物件模型 (SOM) API 可從檔案或其他來源中讀取及寫入 XML 結構描述定義語言 (XSD) 結構描述，並使用 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間中的類別 (該命名空間對應於全球資訊網協會 (W3C) XML 結構描述建議事項中所定義的結構) 來建置記憶體中的 XML 結構描述。  
  
## <a name="reading-and-writing-xml-schemas"></a>讀取及寫入 XML 結構描述  
 <xref:System.Xml.Schema.XmlSchema> 類別提供 <xref:System.Xml.Schema.XmlSchema.Read%2A> 及 <xref:System.Xml.Schema.XmlSchema.Write%2A> 方法，以讀取及寫入 XML 結構描述。 <xref:System.Xml.Schema.XmlSchema.Read%2A> 方法會傳回表示 XML 結構描述的 <xref:System.Xml.Schema.XmlSchema> 物件，並使用選擇性 <xref:System.Xml.Schema.ValidationEventHandler> 做為參數，以處理讀取 XML 結構描述時遇到的結構描述驗證警告及錯誤。  
  
 <xref:System.Xml.Schema.XmlSchema.Write%2A> 方法會將 XML 結構描述寫入 <xref:System.IO.Stream>、<xref:System.IO.TextWriter> 及 <xref:System.Xml.XmlWriter> 物件，並可使用選擇性 <xref:System.Xml.XmlNamespaceManager> 物件做為參數。 <xref:System.Xml.XmlNamespaceManager> 可用於處理在 XML 結構描述中發現的命名空間。 如需有關 <xref:System.Xml.XmlNamespaceManager> 類別的詳細資訊，請參閱[管理 XML 文件中的命名空間](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)。  
  
 下列程式碼範例說明在檔案中讀取及寫入 XML 結構描述。 該程式碼範例採用 `example.xsd` 檔案，並使用 <xref:System.Xml.Schema.XmlSchema>`static` 方法將其讀取至 <xref:System.Xml.Schema.XmlSchema.Read%2A> 物件，然後將該檔案寫入主控台及新的 `new.xsd` 檔案。 該程式碼範例還將 <xref:System.Xml.Schema.ValidationEventHandler> 做為參數提供給 `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> 方法，以處理讀取 XML 結構描述時遇到的任何結構描述驗證警告或錯誤。 如果未指定 <xref:System.Xml.Schema.ValidationEventHandler> (`null`)，則不會報告警告或錯誤。  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 範例會將 `example.xsd` 做為輸入。  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>請參閱  
 [XML 結構描述物件模型概觀](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [周遊 XML 結構描述](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [編輯 XML 結構描述](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [併入或匯入 XML 結構描述](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [用於結構描述編譯的 XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [後結構描述編譯資訊集](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)  
 [管理 XML 文件中的命名空間](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)
