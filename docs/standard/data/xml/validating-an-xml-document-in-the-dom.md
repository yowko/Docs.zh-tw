---
title: "驗證 DOM 中的 XML 文件"
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
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 51ca7b5d18e4b664fcc5a56f7de004c42cb95c9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="validating-an-xml-document-in-the-dom"></a>驗證 DOM 中的 XML 文件
依預設，<xref:System.Xml.XmlDocument> 類別不會根據 XML 結構描述定義語言 (XSD) 結構描述或文件類型定義 (DTD)，驗證文件物件模型 (DOM) 中的 XML；只會驗證 XML 的格式是否正確。  
  
 若要驗證 DOM 中的 XML，您可以在將 XML 載入到 DOM 時，藉由將結構描述驗證的 <xref:System.Xml.XmlReader> 傳遞至 <xref:System.Xml.XmlDocument.Load%2A> 類別的 <xref:System.Xml.XmlDocument> 方法來驗證它，也可使用 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法，驗證 DOM 中先前未驗證的 XML 文件。  
  
## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>將 XML 文件載入到 DOM 時進行驗證  
 在將驗證 <xref:System.Xml.XmlDocument> 傳遞至 <xref:System.Xml.XmlReader> 類別的 <xref:System.Xml.XmlDocument.Load%2A> 方法時，<xref:System.Xml.XmlDocument> 類別會在 XML 資料載入 DOM 時加以驗證。  
  
 在驗證成功之後，會套用結構描述預設值，視需要將文字值轉換成原子值，並將類型資訊與已驗證的資訊項目相關聯。 因此，具類型的 XML 資料會取代先前不具類型的 XML 資料。  
  
### <a name="creating-an-xml-schema-validating-xmlreader"></a>建立 XML 結構描述驗證的 XmlReader  
 若要建立 XML 結構描述驗證的 <xref:System.Xml.XmlReader>，請遵循下列步驟。  
  
1.  建構新的 <xref:System.Xml.XmlReaderSettings> 執行個體。  
  
2.  將 XML 結構描述加入至 <xref:System.Xml.XmlReaderSettings.Schemas%2A> 執行個體的 <xref:System.Xml.XmlReaderSettings> 屬性。  
  
3.  指定 `Schema` 做為 <xref:System.Xml.XmlReaderSettings.ValidationType%2A>。  
  
4.  選擇性地指定 <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> 及 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>，以處理驗證期間遇到的結構描述驗證錯誤及警告。  
  
5.  最後，將 <xref:System.Xml.XmlReaderSettings> 物件傳遞至 <xref:System.Xml.XmlReader.Create%2A> 類別的 <xref:System.Xml.XmlReader> 方法，及傳遞至 XML 文件，建立結構描述驗證的 <xref:System.Xml.XmlReader>。  
  
### <a name="example"></a>範例  
 在下面的程式碼範例中，結構描述驗證的 <xref:System.Xml.XmlReader> 會驗證載入至 DOM 的 XML 資料。 對 XML 文件進行無效的修改，然後重新驗證該文件，會導致結構描述驗證錯誤。 最後，更正其中一個錯誤，然後對 XML 文件的一部分進行部分驗證。  
  
 [!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
 [!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]  
  
 該範例採用 `contosoBooks.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 該範例還將 `contosoBooks.xsd` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 在驗證載入至 DOM 的 XML 資料時，請考量下列事項。  
  
-   在上述範例中，每當遇到無效的類型時，就會呼叫 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>。 如果 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> 未在要進行驗證的 <xref:System.Xml.XmlReader> 中設定，若因任何屬性或項目與要進行驗證之結構描述中指定的對應類型不符合，而呼叫 <xref:System.Xml.Schema.XmlSchemaValidationException> 時，則會擲回 <xref:System.Xml.XmlDocument.Load%2A>。  
  
-   當 XML 文件載入至具有可定義預設值之關聯結構描述的 <xref:System.Xml.XmlDocument> 物件時，<xref:System.Xml.XmlDocument> 會處理這些預設值，就好像它們是出現在 XML 文件中。 這表示 <xref:System.Xml.XmlReader.IsEmptyElement%2A> 屬性針對該結構描述預設會產生的項目，永遠傳回 `false`。 即使在 XML 文件中，它也做為空白項目寫入。  
  
## <a name="validating-an-xml-document-in-the-dom"></a>驗證 DOM 中的 XML 文件  
 根據 <xref:System.Xml.XmlDocument.Validate%2A> 物件之 <xref:System.Xml.XmlDocument> 屬性中的結構描述，<xref:System.Xml.XmlDocument> 類別的 <xref:System.Xml.XmlDocument.Schemas%2A> 方法會驗證載入到 DOM 的 XML 資料。 在驗證成功之後，會套用結構描述預設值，視需要將文字值轉換成原子值，並將類型資訊與已驗證的資訊項目相關聯。 因此，具類型的 XML 資料會取代先前不具類型的 XML 資料。  
  
 以下範例與上述＜將 XML 文件載入到 DOM 時進行驗證＞中的範例相似。 在此範例中，XML 文件不是在載入到 DOM 時進行驗證，而是在載入到 DOM 之後，使用 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法進行驗證。 <xref:System.Xml.XmlDocument.Validate%2A> 方法會根據 <xref:System.Xml.XmlDocument.Schemas%2A> 的 <xref:System.Xml.XmlDocument> 屬性中包含的 XML 結構描述，驗證 XML 文件。 然後對 XML 文件進行無效的修改並重新驗證該文件，會導致結構描述驗證錯誤。 最後，更正其中一個錯誤，然後對 XML 文件的一部分進行部分驗證。  
  
 [!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]  
  
 該範例將上述＜將 XML 文件載入到 DOM 時進行驗證＞所指的 `contosoBooks.xml` 及 `contosoBooks.xsd` 檔案當做輸入。  
  
## <a name="handling-validation-errors-and-warnings"></a>處理驗證錯誤及警告  
 驗證載入 DOM 中的 XML 資料時，會報告 XML 結構描述驗證錯誤。 會通知您在驗證載入的 XML 資料時，或者驗證先前未驗證的 XML 文件時，所找到的全部結構描述錯誤。  
  
 驗證錯誤由 <xref:System.Xml.Schema.ValidationEventHandler> 來處理。 如果將 <xref:System.Xml.Schema.ValidationEventHandler> 指派給 <xref:System.Xml.XmlReaderSettings> 執行個體，或傳遞至 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法，則 <xref:System.Xml.Schema.ValidationEventHandler> 將處理結構描述驗證錯誤；否則當遇到結構描述驗證錯誤時，會引發 <xref:System.Xml.Schema.XmlSchemaValidationException>。  
  
> [!NOTE]
>  除非 <xref:System.Xml.Schema.ValidationEventHandler> 引發例外狀況並停止處理序，否則即使發生結構描述驗證錯誤，也會將 XML 資料載入到 DOM。  
>   
>  除非將 <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> 旗標指定至 <xref:System.Xml.XmlReaderSettings> 物件，否則不會報告結構描述驗證警告。  
  
 如需說明 <xref:System.Xml.Schema.ValidationEventHandler> 的範例，請參閱上述＜將 XML 文件載入到 DOM 時進行驗證＞及＜驗證 DOM 中的 XML 文件＞。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.ValidationEventHandler>  
 <xref:System.Xml.XmlReaderSettings>  
 [使用 DOM 模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 [使用 XML 結構描述](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
