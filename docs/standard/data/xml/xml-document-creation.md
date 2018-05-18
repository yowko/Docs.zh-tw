---
title: 建立 XML 文件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ab7632966cd2a0087a8bdc1d452d02543edbec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xml-document-creation"></a>建立 XML 文件
有兩種方式可用來建立 XML 文件。 一種方法是不用參數建立 **XmlDocument**。 另一種方法是建立 **XmlDocument**，並且將 XmlNameTable 當作參數傳給它。 下列範例顯示如何在不使用參數的情況下，建立新的空白 **XmlDocument**。  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 一旦文件建立之後，您可以使用 **Load** 方法，將來自字串、資料流、URL、文字讀取器或 **XmlReader** 衍生類別的資料載入該文件。 另一個 Load 方法是 **LoadXML** 方法，它會從字串中讀取 XML。 如需各種 **Load** 方法的詳細資訊，請參閱[將 XML 文件讀入 DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)。  
  
 有另一種類別叫做 **XmlNameTable**。 這個類別是原子化字串物件的表格。 這個表格可為 XML 剖析器提供一種有效的方式，用以針對 XML 文件中所有重複的項目和屬性名稱使用相同的字串物件。 當文件依照上述方式建立時，**XmlNameTable** 也會自動建立，並且會在載入文件時，同時載入其屬性和項目名稱。 如果您已經有一個具有名稱表格的文件，而且這些名稱在另一個文件也很有用，則可以使用以 **XmlNameTable** 做為參數的 **Load** 方法來建立新文件。 當文件以這種方法建立時，它會使用含有已經從其他文件載入之所有屬性和項目的現有 **XmlNameTable**。 它可以用來有效地比較項目和屬性名稱。 如需 **XmlNameTable** 的詳細資訊，請參閱[使用 XmlNameTable 進行物件比較](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)。 如需參考，請參閱 <xref:System.Xml.XmlNameTable>。  
  
## <a name="see-also"></a>請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
