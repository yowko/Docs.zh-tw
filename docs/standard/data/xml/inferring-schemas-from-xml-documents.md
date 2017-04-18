---
title: "從 XML 文件推斷結構描述 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# 從 XML 文件推斷結構描述
本主題說明如何使用 <xref:System.Xml.Schema.XmlSchemaInference> 類別，從 XML 文件結構推斷 XML 結構描述定義語言 \(XSD\) 結構描述。  
  
## 結構描述推斷程序  
 <xref:System.Xml.Schema?displayProperty=fullName> 命名空間的 <xref:System.Xml.Schema.XmlSchemaInference> 類別，可用來從 XML 文件結構產生一或多個 XML 結構描述定義語言 \(XSD\) 結構描述。  產生的結構描述可用來驗證原始的 XML 文件。  
  
 由於 XML 文件是由 <xref:System.Xml.Schema.XmlSchemaInference> 類別所處理，因此 <xref:System.Xml.Schema.XmlSchemaInference> 類別會對可說明 XML 文件中之項目和屬性的結構描述元件進行假設。  <xref:System.Xml.Schema.XmlSchemaInference> 類別也可藉由推斷特定項目或屬性的最嚴格型別，以條件約束的方式推斷結構描述元件。  當收集到較多 XML 文件的相關資訊時，就會推斷較不嚴格的型別，而放寬這些條件約束。  `xs:string` 是推斷為最不嚴格的型別。  
  
 我們以下列 XML 文件片段為例。  
  
```  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 在上述範例中，<xref:System.Xml.Schema.XmlSchemaInference> 處理序發現 `attribute1` 屬性的值為 `6` 時，會假設此屬性的型別為 `xs:unsignedByte`。  <xref:System.Xml.Schema.XmlSchemaInference> 處理序發現第二個 `parent` 項目時，即會將型別修改為 `xs:string` 而放寬條件約束，因為 `attribute1` 屬性的值此時為 `A`。  同樣地，所有 `child` 項目中在結構描述內進行推斷的 `minOccurs` 屬性，也會放寬為 `minOccurs="0"`，因為第二個父項目沒有項目子系。  
  
## 從 XML 文件推斷結構描述  
 <xref:System.Xml.Schema.XmlSchemaInference> 類別可使用兩種多載 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法，從 XML 文件推斷結構描述。  
  
 第一種 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=fullName> 方法可根據 XML 文件建立結構描述。  第二種 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=fullName> 方法用來推斷可說明多個 XML 文件的結構描述。  例如，您可以逐一將多個 XML 文件傳送給 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=fullName> 方法，以產生可說明完整 XML 文件集的結構描述。  
  
 第一種 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=fullName> 方法會從 <xref:System.Xml.XmlReader> 物件所含的 XML 文件推斷結構描述，並傳回含有所推斷之結構描述的 <xref:System.Xml.Schema.XmlSchemaSet> 物件。  第二種 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=fullName> 方法會搜尋 <xref:System.Xml.Schema.XmlSchemaSet> 物件中是否有目標命名空間與 <xref:System.Xml.XmlReader> 物件所含之 XML 文件相同的結構描述，然後進一步調整現有的結構描述，並傳回含有所推斷之結構描述的 <xref:System.Xml.Schema.XmlSchemaSet> 物件。  
  
 對調整的結構描述所作的變更取決於在 XML 文件中找到的新結構。  例如，當 XML 文件周遊時，就會對找到的資料型別進行相關假設，並根據這些假設建立結構描述。  但若在第二次推斷傳遞時發現資料與原始假設不同，則會進一步調整結構描述。  下列範例將說明調整的程序。  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 此範例以下列檔案 \(`item1.xml`\) 做為第一個輸入。  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 接著，此範例會以 `item2.xml` 檔案做為第二個輸入：  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 在第一個 XML 文件中發現 `productID` 屬性時，會將 `123456789` 這個值假設為 `xs:unsignedInt` 型別。  但當讀取第二個 XML 文件並發現 `A53-246` 這個值時，則無法再假設 `xs:unsignedInt` 型別。  會調整結構描述，而 `productID` 的型別會變更為 `xs:string`。  此外，`supplierID` 項目的 `minOccurs` 屬性會設為 `0`，因為第二個 XML 文件中不含 `supplierID` 項目。  
  
 以下是從第一份 XML 文件推斷的結構描述。  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 以下是從第一份 XML 文件推斷的結構描述，並以第二份 XML 文件進一步調整。  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## 內嵌結構描述  
 如果在 <xref:System.Xml.Schema.XmlSchemaInference> 處理序期間發現內嵌 XML 結構描述定義語言 \(XSD\) 結構描述，則會擲回 <xref:System.Xml.Schema.XmlSchemaInferenceException>。  例如，下列內嵌結構描述會擲回 <xref:System.Xml.Schema.XmlSchemaInferenceException>。  
  
```  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## 無法進一步調整的結構描述  
 有些 W3C XML 結構描述建構在指定要調整的型別時會擲回例外狀況，則 XML 結構描述定義語言 \(XSD\) 結構描述 <xref:System.Xml.Schema.XmlSchemaInference> 處理序無法處理這類的結構描述。  最上層建構元不屬於序列的複雜型別即是一例。  在結構描述物件模型 \(SOM\) 中，它會對應至 <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> 屬性不屬於 <xref:System.Xml.Schema.XmlSchemaSequence> 之執行個體的 <xref:System.Xml.Schema.XmlSchemaComplexType>。  
  
## 請參閱  
 <xref:System.Xml.Schema.XmlSchemaInference>   
 [XML 結構描述物件模型 \(SOM\)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)   
 [推斷 XML 結構描述](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)   
 [推斷結構描述節點型別與結構的規則](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)   
 [推斷簡單型別的規則](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)