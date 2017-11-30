---
title: "建立 XML 文件"
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
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a0806e34cfbf7c8e0b5ba995ca4876b8d10405e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-creation"></a>建立 XML 文件
有兩種方式可用來建立 XML 文件。 若要建立的一種方式是**XmlDocument**不含任何參數。 另一種方式是建立**XmlDocument**並將它當做參數傳遞 XmlNameTable。 下列範例示範如何建立新的空白**XmlDocument**不使用參數。  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 一旦建立文件時，可以載入資料來自字串、 資料流、 URL、 文字讀取器或**XmlReader**衍生類別使用**載入**方法。 另外還有另一個載入方法， **LoadXML**方法，從字串讀取 XML。 如需各種**負載**方法，請參閱[XML 文件讀入 DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)。  
  
 還有一種類別稱為**XmlNameTable**。 這個類別是原子化字串物件的表格。 這個表格可為 XML 剖析器提供一種有效的方式，用以針對 XML 文件中所有重複的項目和屬性名稱使用相同的字串物件。 **XmlNameTable**文件建立如上所示，且文件載入時載入屬性和項目名稱時，自動建立。 如果您已經有具有名稱表格中，文件，而且這些名稱可能會很有用的其他文件中，您可以建立新的文件使用**負載**採用方法**XmlNameTable**做為參數。 當以這個方法建立文件時，它會使用現有**XmlNameTable**所有的屬性和元素已經從其他文件載入它。 它可以用來有效地比較項目和屬性名稱。 如需有關**XmlNameTable**，請參閱[使用 xmlnametable 進行物件比較](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)。 如需參考，請參閱<xref:System.Xml.XmlNameTable>。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
