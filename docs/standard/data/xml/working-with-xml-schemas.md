---
title: 使用 XML 結構描述
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83fddd00f44b184fa066f6c47b90b01fac7ef7bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-xml-schemas"></a>使用 XML 結構描述
若要定義 XML 文件的結構及其項目關聯性、資料類型及內容條件約束，可以使用文件類型定義 (DTD) 或 XML 結構描述定義語言 (XSD) 結構描述。 儘管當 XML 文件滿足全球資訊網協會 (W3C) 可延伸標記語言 (XML) 1.0 版建議事項定義的所有語法要求時，會將其視為格式正確，但是它必須格式正確且符合由其 DTD 或結構描述所定義的條件約束才會被視為有效。 因此，儘管所有有效 XML 文件的格式都正確，但是並非所有格式正確的 XML 文件都有效。  
  
 如需 XML 的詳細資訊，請參閱 [W3C XML 1.0 建議事項](https://www.w3.org/TR/REC-xml/) (英文)。 如需 XML 結構描述的詳細資訊，請參閱 [W3C XML 結構描述第一部：結構建議事項](https://www.w3.org/TR/xmlschema-1/)及 [W3C XML 結構描述第二部：資料型別建議事項](https://www.w3.org/TR/xmlschema-2/)的建議。  
  
## <a name="in-this-section"></a>本節內容  
 [XML 結構描述物件模型 (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 討論 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間中的結構描述物件模型 (SOM)，其提供了一組類別，可讓您從檔案讀取結構描述定義語言 (XSD) 結構描述，或以程式設計方式建立記憶體中結構描述。  
  
 [用於結構描述編譯的 XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 討論 <xref:System.Xml.Schema.XmlSchemaSet> 類別，其為可儲存及驗證 XSD 結構描述的快取。  
  
 [XmlSchemaValidator 推入型驗證](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 討論 <xref:System.Xml.Schema.XmlSchemaValidator> 類別，其可提供有效的高效能機制，來針對 XSD 結構描述並以推入式方式驗證 XML 資料。  
  
 [推斷 XML 結構描述](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 討論如何使用 <xref:System.Xml.Schema.XmlSchemaInference> 類別，從 XML 文件的結構推斷 XSD 結構描述。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>相關章節  
 [驗證 DOM 中的 XML 文件](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 討論如何驗證文件物件模型 (DOM) 中的 XML。 您可以在將 XML 載入至 DOM 時進行驗證，或者驗證 DOM 中先前未驗證的 XML 文件。  
  
 [使用 XPathNavigator 進行結構描述驗證](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 討論如何對使用 <xref:System.Xml.XPath.XPathNavigator> 類別巡覽及編輯的 XML 進行驗證。
