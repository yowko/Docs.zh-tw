---
title: XML 結構描述物件模型概觀
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd25cf94a8a57f20b42f5e14c92b3b43e3378844
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xml-schema-object-model-overview"></a>XML 結構描述物件模型概觀
Microsoft .NET Framework 中的結構描述物件模型 (SOM) 是一個豐富的 API，可讓您以程式設計的方式建立、編輯及驗證結構描述。 SOM 在 XML 結構描述文件上的運作方式，與文件物件模型 (DOM) 在 XML 文件上的運作方式相似。 XML 結構描述文件是有效的 XML 檔案，當它載入 SOM 後，便可傳達符合該結構描述之其他 XML 文件結構及有效性的意義。  
  
 結構描述是一個 XML 文件，它會藉由指定特定結構描述之 XML 文件的結構或模型，來定義 XML 文件的類別。 結構描述可識別對 XML 文件內容的條件約束，並說明相容的 XML 文件為了使其特定結構描述有效，而必須使用的字彙 (規則或文法)。 XML 文件的驗證是確保文件符合結構描述所指定之文法的程序。  
  
 以下是 .NET Framework 中 SOM API 允許您在建立、編輯及驗證結構描述時所使用的方式。  
  
-   在檔案間載入及儲存有效的結構描述。  
  
-   使用強型別類別建立記憶體中的結構描述。  
  
-   與 <xref:System.Xml.Schema.XmlSchemaSet> 類別互動，以快取、編譯及擷取結構描述。  
  
-   與 <xref:System.Xml.XmlReader.Create%2A> 類別的 <xref:System.Xml.XmlReader> 方法互動，以根據結構描述驗證 XML 執行個體文件。  
  
-   建置編輯器以建立及維護結構描述。  
  
-   動態編輯可編譯和儲存的結構描述，以便在驗證 XML 執行個體文件時使用該結構描述。  
  
## <a name="the-schema-object-model"></a>結構描述物件模型  
 SOM 是由 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間中的大量類別集 (其對應於 XML 結構描述中的項目) 所組成的。 例如，`<xsd:schema>...</xsd:schema>` 項目對應至 <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> 類別，並可使用 `<xsd:schema/>` 類別來表示 <xref:System.Xml.Schema.XmlSchema> 項目可包含的所有資訊。 同樣地，`<xsd:element>...</xsd:element>` 及 `<xsd:attribute>...</xsd:attribute>` 項目分別對應至 <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> 及 <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> 類別。 這種對應關係會在 XML 結構描述的所有項目持續下去，以在 <xref:System.Xml.Schema> 命名空間中建立 XML 結構描述物件模型，如下圖所示。  
  
 ![System.Xml.Schema 物件模型](../../../../docs/standard/data/xml/media/xmlschemaobjmodeloverview.gif "XMLSchemaObjModelOverview")  
  
 如需 <xref:System.Xml.Schema> 命名空間中每個類別的詳細資訊，請參閱 .NET Framework 類別庫中的 <xref:System.Xml.Schema> 命名空間參考文件。  
  
## <a name="see-also"></a>請參閱  
 [讀取和寫入 XML 結構描述](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [周遊 XML 結構描述](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [編輯 XML 結構描述](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [併入或匯入 XML 結構描述](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [用於結構描述編譯的 XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [後結構描述編譯資訊集](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
