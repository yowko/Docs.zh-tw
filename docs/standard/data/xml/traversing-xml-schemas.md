---
title: 周遊 XML 結構描述
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c587f4248205251824be851c135d93784e86c2f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646629"
---
# <a name="traversing-xml-schemas"></a>周遊 XML 結構描述
使用結構描述物件模型 (SOM) API 周遊 XML 結構描述，可以提供對儲存於 SOM 之項目、屬性及型別的存取權。 周遊載入到 SOM 的 XML 結構描述也是使用 SOM API 編輯 XML 結構描述的第一步。  
  
## <a name="traversing-an-xml-schema"></a>周遊 XML 結構描述  
 <xref:System.Xml.Schema.XmlSchema> 類別的下列屬性可以提供對加入至 XML 結構描述之所有全域項目集合的存取權。  
  
|屬性|儲存於集合或陣列中的物件型別|  
|--------------|---------------------------------------------------|  
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|  
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|  
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<xref:System.Xml.Schema.XmlSchemaExternal>、<xref:System.Xml.Schema.XmlSchemaInclude>、<xref:System.Xml.Schema.XmlSchemaImport> 或 <xref:System.Xml.Schema.XmlSchemaRedefine>|  
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<xref:System.Xml.Schema.XmlSchemaObject> (可提供對所有全域層級項目、屬性及型別的存取權)。|  
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|  
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|  
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<xref:System.Xml.XmlAttribute> (提供對不屬於結構描述命名空間之屬性的存取權)|  
  
> [!NOTE]
>  上述表格中列出的所有屬性 (除 <xref:System.Xml.Schema.XmlSchema.Items%2A> 屬性之外)，都是後結構描述編譯資訊集 (PSCI) 屬性，僅在編譯結構描述之後才可用。 <xref:System.Xml.Schema.XmlSchema.Items%2A> 屬性是前結構描述編譯屬性，其可在編譯結構描述之前使用，以存取及編輯所有全域層級項目、屬性及型別。  
>   
>  <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> 屬性提供對不屬於結構描述命名空間之所有屬性的存取權。 結構描述處理器不會處理這些屬性。  
  
 接下來的程式碼範例會示範如何周遊[建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md)主題中建立的客戶結構描述。 該程式碼範例示範如何使用上述集合周遊結構描述，並將結構描述中的所有項目和屬性寫入主控台。  
  
 該範例會按下列步驟周遊客戶結構描述。  
  
1.  將客戶結構描述加入至新 <xref:System.Xml.Schema.XmlSchemaSet> 物件，然後編譯它。 讀取或編譯結構描述時遇到的任何結構描述驗證警告及錯誤，都會由 <xref:System.Xml.Schema.ValidationEventHandler> 委派處理。  
  
2.  藉由重複處理 <xref:System.Xml.Schema.XmlSchema> 屬性，從 <xref:System.Xml.Schema.XmlSchemaSet> 擷取已編譯的 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 物件。 因為已編譯結構描述，因此可存取後結構描述編譯資訊集 (PSCI) 屬性。  
  
3.  重複處理後結構描述編譯 <xref:System.Xml.Schema.XmlSchemaElement> 集合之 <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> 集合中的每個 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>，會將每個項目的名稱寫入主控台。  
  
4.  使用 `Customer` 類別，取得 <xref:System.Xml.Schema.XmlSchemaComplexType> 項目的複雜型別。  
  
5.  如果複雜型別具有任何屬性，請取得 <xref:System.Collections.IDictionaryEnumerator> 來列舉每個 <xref:System.Xml.Schema.XmlSchemaAttribute>，並將其名稱寫入主控台。  
  
6.  使用 <xref:System.Xml.Schema.XmlSchemaSequence> 類別，取得複雜型別的順序物件。  
  
7.  重複處理 <xref:System.Xml.Schema.XmlSchemaElement> 集合中的每個 <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType>，會將每個項目子系的名稱寫入主控台。  
  
 下列是完整的程式碼範例。  
  
 [!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
 [!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
 [!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]  
  
 如果 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> 屬性是使用者定義的簡單型別或複雜型別，則其可以為 <xref:System.Xml.Schema.XmlSchemaSimpleType> 或<xref:System.Xml.Schema.XmlSchemaComplexType>。 如果其為 W3C XML 結構描述建議事項中定義的其中一個內建資料型別，則也可以為 <xref:System.Xml.Schema.XmlSchemaDatatype>。 在客戶結構描述中，<xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> 項目的 `Customer` 為 <xref:System.Xml.Schema.XmlSchemaComplexType>，`FirstName` 及 `LastName` 項目為 <xref:System.Xml.Schema.XmlSchemaSimpleType>。  
  
 [建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md)主題中的程式碼範例使用 <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> 集合，將屬性 `CustomerId` 加入至 `Customer` 項目。 這是前結構描述編譯屬性。 對應的後結構描述編譯資訊集屬性為 <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> 集合，其保留複雜型別的所有屬性，包括透過型別衍生繼承的那些屬性。  
  
## <a name="see-also"></a>另請參閱

- [XML 結構描述物件模型概觀](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [讀取和寫入 XML 結構描述](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [編輯 XML 結構描述](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [併入或匯入 XML 結構描述](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [用於結構描述編譯的 XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [後結構描述編譯資訊集](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
