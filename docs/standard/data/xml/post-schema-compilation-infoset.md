---
title: 後結構描述編譯資訊集
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db1c952003e73beb756567be74ed4eb72612c989
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="post-schema-compilation-infoset"></a>後結構描述編譯資訊集
[全球資訊網協會 (W3C) XML 結構描述建議事項](https://www.w3.org/XML/Schema) (英文) 中討論為了進行前置結構描述驗證和後置結構描述編譯所必須公開的資訊集 (infoset)。 XML 結構描述物件模型 (SOM) 會在呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法之前及之後，檢視此公開資訊集。  
  
 前結構描述驗證資訊集建置於結構描述的編輯期間。 後結構描述編譯資訊集是在結構描述的編譯期間，並於呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法之後產生的，而且會公開為屬性。  
  
 SOM 是表示前結構描述驗證及後結構描述編譯資訊集的物件模型，它是由 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間中的類別組成。 <xref:System.Xml.Schema> 命名空間中類別的所有讀取及寫入屬性都屬於前結構描述驗證資訊集，而 <xref:System.Xml.Schema> 命名空間中類別的所有唯讀屬性都屬於後結構描述編譯資訊集。 下列屬性是此規則的例外，它們同時屬於前結構描述驗證資訊集及後結構描述編譯資訊集的屬性。  
  
|類別|屬性|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 例如，<xref:System.Xml.Schema.XmlSchemaElement> 及 <xref:System.Xml.Schema.XmlSchemaComplexType> 類別都具有 `BlockResolved` 及 `FinalResolved` 屬性。 在編譯及驗證結構描述之後，這些屬性可用於儲存 `Block` 及 `Final` 屬性的值。 `BlockResolved` 及 `FinalResolved` 是唯讀屬性，其屬於後結構描述編譯資訊集。  
  
 下列範例顯示驗證結構描述之後，<xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> 類別集的 <xref:System.Xml.Schema.XmlSchemaElement> 屬性。 驗證之前，該屬性包含 `null` 參考，且 <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 是設為所討論之型別的名稱。 驗證之後，<xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 會解析為有效型別，而且型別物件可透過 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> 屬性來使用。  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 [XML 結構描述物件模型 (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
