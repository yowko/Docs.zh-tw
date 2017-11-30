---
title: "XmlSchemaCollection 結構描述編譯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 901c3fdc8fdc80cc7c3bf13170646de857a5e009
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xmlschemacollection-schema-compilation"></a>XmlSchemaCollection 結構描述編譯
**XmlSchemaCollection**快取或程式庫可儲存及驗證 XML 資料精簡 (XDR) 和 XML 結構描述定義語言 (XSD) 結構描述。 **XmlSchemaCollection**快取在記憶體中而不是從檔案或 URL 存取它們的結構描述可以改善效能。  
  
> [!NOTE]
>  雖然**XmlSchemaCollection**類別會儲存在 XDR 結構描述和 XML 結構描述，任何方法和屬性或傳回**XmlSchema**物件僅支援 XML 結構描述。  
  
> [!IMPORTANT]
>  <xref:System.Xml.Schema.XmlSchemaCollection> 類別目前已過時，並已由 <xref:System.Xml.Schema.XmlSchemaSet> 類別取代。 如需有關<xref:System.Xml.Schema.XmlSchemaSet>類別，請參閱[結構描述編譯的 XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)。  
  
## <a name="add-schemas-to-the-collection"></a>將結構描述加入集合  
 結構描述已載入到集合時使用**新增**方法**XmlSchemaCollection**，這時結構描述會與命名空間 URI 相關聯。 對 XML 結構描述來說，命名空間 URI 通常是結構描述的目標命名空間。 對 XDR 結構描述來說，命名空間 URI 是當將結構描述加入集合時指定的命名空間。  
  
## <a name="check-for-a-schema-in-the-collection"></a>檢查集合中的結構描述  
 您可以查看結構描述是否在集合中，使用**Contains**方法。 **Contains**方法會接受**XmlSchema** （適用於 XML 結構描述） 的物件或字串，表示命名空間 URI 相關聯的結構描述 （XML 結構描述和 XDR 結構描述）。  
  
## <a name="retrieve-a-schema-from-the-collection"></a>從集合擷取結構描述  
 您也可以使用從集合擷取結構描述**項目**屬性。 **項目**屬性會接受字串，表示命名空間 URI 相關聯的結構描述，通常其目標命名空間，並傳回**XmlSchema**物件。 **項目**屬性僅適用於 XML 結構描述。 對 XDR 結構描述來說，傳回值永遠是 Null 參考，因為它們並沒有可用的物件模型。  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>使用 XmlSchemaCollection 驗證 XML 文件  
 您可以驗證 XML 執行個體文件使用**XmlSchemaCollection**藉由建立**XmlSchemaCollection**物件，您的結構描述加入至集合中，並設定**結構描述**屬性**XmlValidatingReader**指派建立**XmlSchemaCollection**至**XmlValidatingReader**。  
  
### <a name="improved-performance"></a>提升效能  
 建議，如果您要驗證針對相同的結構描述的多個文件，使用**XmlSchemaCollection**因為根據快取在記憶體中的結構描述會提供更佳的效能。  
  
 下列程式碼範例會建立**XmlSchemaCollection**物件、 將結構描述加入至集合中，並設定**結構描述**屬性。  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用 XmlSchemaCollection 的 XDR 驗證](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [使用 xmlschemacollection 進行 XML 結構描述 (XSD) 驗證](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
