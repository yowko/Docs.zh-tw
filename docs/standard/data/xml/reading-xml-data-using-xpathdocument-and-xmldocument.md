---
title: 使用 XPathDocument 及 XmlDocument 讀取 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69e22328c39ae68acc4baff12775b49fbac80696
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252827"
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a>使用 XPathDocument 及 XmlDocument 讀取 XML 資料
讀取 <xref:System.Xml.XPath?displayProperty=nameWithType> 命名空間中的 XML 文件有兩種方式。 一種是使用唯讀的 <xref:System.Xml.XPath.XPathDocument> 類別讀取 XML 文件，另一種是使用 <xref:System.Xml.XmlDocument> 命名空間中可編輯的 <xref:System.Xml?displayProperty=nameWithType> 類別讀取 XML 文件。  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a>使用 XPathDocument 類別讀取 XML 文件  
 <xref:System.Xml.XPath.XPathDocument> 類別會使用 XPath 資料模型，以快速且唯讀的方式來表示記憶體中的 XML 文件。 可使用 <xref:System.Xml.XPath.XPathDocument> 類別的六個建構函式之一，建立該類別的執行個體。 這些建構函式可讓您使用 <xref:System.IO.Stream>、<xref:System.IO.TextReader> 或 <xref:System.Xml.XmlReader> 物件，以及 XML 檔案的 `string` 路徑，讀取 XML 文件。  
  
 下列範例說明如何使用 <xref:System.Xml.XPath.XPathDocument> 類別的 `string` 建構函式來讀取 XML 文件。  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a>使用 XmlDocument 類別讀取 XML 文件  
 <xref:System.Xml.XmlDocument> 類別是 XML 文件的可編輯記憶體中表示，它會實作 W3C 文件物件模型 (DOM) 層級 1 核心及核心 DOM 層級 2。 可使用 <xref:System.Xml.XmlDocument> 類別的三種建構函式之一，來建立該類別的執行個體。 您可籍由呼叫不具參數的 <xref:System.Xml.XmlDocument> 類別建構函式，來建立新的空白<xref:System.Xml.XmlDocument> 物件。 呼叫該建構函式後，請使用 <xref:System.Xml.XmlDocument.Load%2A> 方法將 XML 資料從 <xref:System.Xml.XmlDocument>、<xref:System.IO.Stream> 或<xref:System.IO.TextReader> 物件，以及 XML 檔案的 <xref:System.Xml.XmlReader> 路徑載入到新的 `string` 物件。  
  
 下列範例說明如何使用不具參數的 <xref:System.Xml.XmlDocument> 類別建構函式及 <xref:System.Xml.XmlDocument.Load%2A> 方法來讀取 XML 文件。  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a>決定 XML 文件的編碼方式  
 如先前各節所示，可使用 <xref:System.Xml.XmlReader> 物件讀取 XML 文件，並建立 <xref:System.Xml.XPath.XPathDocument> 及 <xref:System.Xml.XmlDocument> 物件。 不過，<xref:System.Xml.XmlReader> 物件可能會讀取未編碼的資料，因此不會提供任何編碼資訊。  
  
 <xref:System.Xml.XmlTextReader> 類別會繼承 <xref:System.Xml.XmlReader> 類別，透過其 <xref:System.Xml.XmlTextReader.Encoding%2A> 屬性提供編碼資訊，並可用於建立 <xref:System.Xml.XPath.XPathDocument> 物件或 <xref:System.Xml.XmlDocument> 物件。  
  
 如需 <xref:System.Xml.XmlTextReader> 類別提供之編碼資訊的詳細資訊，請參閱 <xref:System.Xml.XmlTextReader.Encoding%2A> 類別參考文件中的 <xref:System.Xml.XmlTextReader> 屬性。  
  
## <a name="creating-xpathnavigator-objects"></a>建立 XPathNavigator 物件  
 將 XML 文件讀入 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件後，您可以建立 <xref:System.Xml.XPath.XPathNavigator> 物件以選取、評估、巡覽以及 (在某些情況下) 編輯基礎 XML 資料。  
  
 除了 <xref:System.Xml.XPath.XPathDocument> 類別之外，<xref:System.Xml.XmlDocument> 及 <xref:System.Xml.XmlNode> 類別也會實作 <xref:System.Xml.XPath.IXPathNavigable> 命名空間的 <xref:System.Xml.XPath?displayProperty=nameWithType> 介面。 所以，所有三個類別均可提供傳回 <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> 物件的 <xref:System.Xml.XPath.XPathNavigator> 方法。  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a>使用 XPathNavigator 類別編輯 XML 文件  
 除了選取、評估及巡覽 XML 資料之外，在某些情況下，<xref:System.Xml.XPath.XPathNavigator> 類別還可用於編輯 XML 文件 (根據建立該文件的物件)。  
  
 <xref:System.Xml.XPath.XPathDocument> 類別是唯讀的，而 <xref:System.Xml.XmlDocument> 類別則可以編輯；因此，從 <xref:System.Xml.XPath.XPathNavigator> 物件建立的 <xref:System.Xml.XPath.XPathDocument> 物件不能用來編輯 XML 文件，而從 <xref:System.Xml.XmlDocument> 物件建立的那些物件則可以。 <xref:System.Xml.XPath.XPathDocument> 類別應該只能用來讀取 XML 文件。 如果需要編輯 XML 文件，或要求 <xref:System.Xml.XmlDocument> 類別所提供之其他功能的存取權 (如事件處理)，應使用 <xref:System.Xml.XmlDocument> 類別。  
  
 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator> 屬性可指定 <xref:System.Xml.XPath.XPathNavigator> 物件是否可編輯 XML 資料。  
  
 下表說明每個類別的 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 屬性值。  
  
|<xref:System.Xml.XPath.IXPathNavigable> 實作|<xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 值|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [使用 XPathNavigator 存取 XML 資料](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [使用 XPathNavigator 編輯 XML 資料](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
- [使用 XPathNavigator 進行結構描述驗證](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
