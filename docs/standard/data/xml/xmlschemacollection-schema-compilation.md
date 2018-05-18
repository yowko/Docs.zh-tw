---
title: XmlSchemaCollection 結構描述編譯
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d64443f213603b1f5db9c256acc88e998e3f009a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xmlschemacollection-schema-compilation"></a>XmlSchemaCollection 結構描述編譯
**XmlSchemaCollection** 是一種快取 (Cache) 或程式庫，您可在此儲存和驗證 XML 資料精簡 (XDR) 和 XML 結構描述定義語言 (XSD) 結構描述。 **XmlSchemaCollection** 會藉由在記憶體中快取結構描述，而不是從檔案或 URL 存取它們的方式來提升效能。  
  
> [!NOTE]
>  雖然 **XmlSchemaCollection** 類別同時儲存了 XDR 結構描述和 XML 結構描述，但任何會使用或傳回 **XmlSchema** 物件的方法和屬性都只能支援 XML 結構描述。  
  
> [!IMPORTANT]
>  <xref:System.Xml.Schema.XmlSchemaCollection> 類別目前已過時，並已由 <xref:System.Xml.Schema.XmlSchemaSet> 類別取代。 如需有關 <xref:System.Xml.Schema.XmlSchemaSet> 類別的詳細資訊，請參閱[用於結構描述編譯的 XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)。  
  
## <a name="add-schemas-to-the-collection"></a>將結構描述加入集合  
 **XmlSchemaCollection** 的 **Add** 方法會將結構描述載入集合，這時結構描述會和命名空間 URI 建立關聯。 對 XML 結構描述來說，命名空間 URI 通常是結構描述的目標命名空間。 對 XDR 結構描述來說，命名空間 URI 是當將結構描述加入集合時指定的命名空間。  
  
## <a name="check-for-a-schema-in-the-collection"></a>檢查集合中的結構描述  
 您可使用 **Contains** 方法來檢查結構描述是否在集合中。 **Contains** 方法會使用 **XmlSchema** 物件 (僅限 XML 結構描述) 或表示與結構描述相關的命名空間 URI 的字串 (用於 XML 結構描述和 XDR 結構描述)。  
  
## <a name="retrieve-a-schema-from-the-collection"></a>從集合擷取結構描述  
 您可使用 **Item** 屬性來從集合擷取結構描述。 **Item** 屬性會使用表示與結構描述相關的命名空間 URI 的字串 (通常是它的目標命名空間)，並且傳回 **XmlSchema** 物件。 **Item** 屬性只適用於 XML 結構描述。 對 XDR 結構描述來說，傳回值永遠是 Null 參考，因為它們並沒有可用的物件模型。  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>使用 XmlSchemaCollection 驗證 XML 文件  
 您可以藉由建立 **XmlSchemaCollection** 物件、將您的結構描述加入至集合中，然後設定 **XmlValidatingReader** 上的 **Schemas** 屬性，將建立的 **XmlSchemaCollection** 指派給 **XmlValidatingReader**，就可以利用 **XmlSchemaCollection** 來驗證 XML 執行個體文件。  
  
### <a name="improved-performance"></a>提升效能  
 如果您要依照相同的結構描述驗證多個文件，建議您使用 **XmlSchemaCollection**，因為它能夠提供比在記憶體中快取結構描述更佳的效能。  
  
 下列程式碼範例會建立 **XmlSchemaCollection** 物件、將結構描述加入集合中並設定 **Schemas** 屬性。  
  
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
  
## <a name="see-also"></a>請參閱  
 [使用 XmlSchemaCollection 的 XDR 驗證](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [使用 XmlSchemaCollection 進行 XML 結構描述 (XSD) 驗證](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
