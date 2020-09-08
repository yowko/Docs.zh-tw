---
title: System.xml.linq.xelement> 和 XDocument 物件的有效內容-LINQ to XML
description: System.xml.linq.xelement> 和 XDocument 的函式會接受許多引數類型，包括從查詢傳回的集合。 還有其他的函式和函式可用於新增 XML 內容。
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: e0288dce06f8040385c9b9a30335fd039d3c45bd
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552777"
---
# <a name="valid-content-of-xelement-and-xdocument-objects-linq-to-xml"></a>System.xml.linq.xelement> 和 XDocument 物件的有效內容 (LINQ to XML) 

本文描述可傳遞給函式的有效引數，以及您用來將內容加入至專案和檔的方法。

## <a name="valid-types-for-the-xelement-constructor"></a>System.xml.linq.xelement> 函式的有效類型

查詢通常會評估成 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement> 或 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XAttribute>。 您可以將 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 物件的集合傳遞給 <xref:System.Xml.Linq.XElement> 建構函式。 這就是為什麼將查詢結果當作內容傳遞至您用來填入 XML 樹狀結構的方法和函式很方便的原因。

新增簡單的內容時，可以將各種類型傳遞給這個方法，包括：

- <xref:System.String>
- <xref:System.Double>
- <xref:System.Single>
- <xref:System.Decimal>
- <xref:System.Boolean>
- <xref:System.DateTime>
- <xref:System.TimeSpan>
- <xref:System.DateTimeOffset>
- 任何實作 `Object.ToString` 的型別。
- 任何實作 <xref:System.Collections.Generic.IEnumerable%601> 的型別。

新增複雜的內容時，可以將各種類型傳遞給這個方法，包括：

- <xref:System.Xml.Linq.XObject>
- <xref:System.Xml.Linq.XNode>
- <xref:System.Xml.Linq.XAttribute>
- 實作 <xref:System.Collections.Generic.IEnumerable%601> 的任何類型

如果物件實作 <xref:System.Collections.Generic.IEnumerable%601>，系統列舉物件中的集合，並加入集合中的所有項目。 如果集合包含 <xref:System.Xml.Linq.XNode> 或 <xref:System.Xml.Linq.XAttribute> 物件，系統會個別加入集合中的每個項目。 如果集合包含文字 (或轉換為文字的物件)，集合中的文字會遭到串連，並加入為單一文字節點。

如果內容為 `null`，不會加入任何項目。 傳遞集合時，集合中的專案可以是 `null` 。 集合中的 `null` 項目對於樹狀結構沒有任何影響。

加入的屬性在其包含的項目中必須擁有一個唯一的名稱。

加入 <xref:System.Xml.Linq.XNode> 或 <xref:System.Xml.Linq.XAttribute> 物件時，如果新內容沒有父代，則物件只會附加到 XML 樹狀結構。 如果新內容已經成為父代，或是其他 XML 樹狀結構的一部分，則會複製新內容，而且新複製的內容會附加到 XML 樹狀結構。

## <a name="valid-types-for-the-xdocument-constructor"></a>XDocument 函式的有效類型

屬性和簡單的內容無法加入到文件中。

在許多情況下，您不需要建立 <xref:System.Xml.Linq.XDocument> 。 不過，您通常可以使用 <xref:System.Xml.Linq.XElement> 根節點來建立 XML 樹狀結構。 除非您有特定需求來建立檔 (例如，因為您必須在最上層建立處理指示和批註，或您必須支援) 的檔案類型，否則使用 <xref:System.Xml.Linq.XElement> 做為根節點通常會更方便。

有效的函式類型 <xref:System.Xml.Linq.XDocument.%23ctor%2A> 包括下列各項：

- 零或一個 <xref:System.Xml.Linq.XDocumentType> 物件。 文件型別必須在項目之前。
- 零或一個項目。
- 零或多個註解。
- 零或多個處理指示。
- 只包含一個空白字元的零或多個節點。

## <a name="constructors-and-functions-for-adding-content"></a>用於新增內容的函式和函式

下列方法可讓您將子內容加入到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>：

|方法|描述|
|------------|-----------------|
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|建構 <xref:System.Xml.Linq.XElement>。|
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|建構 <xref:System.Xml.Linq.XDocument>。|
|<xref:System.Xml.Linq.XContainer.Add%2A>|加入到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 之子內容的結尾。|
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|將內容加入到 <xref:System.Xml.Linq.XNode> 之後。|
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|將內容加入到 <xref:System.Xml.Linq.XNode> 之前。|
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|將內容加入到 <xref:System.Xml.Linq.XContainer> 之子內容的開頭。|
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|取代 <xref:System.Xml.Linq.XElement> 的所有內容 (子節點和屬性)。|
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|取代 <xref:System.Xml.Linq.XElement> 的屬性。|
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|以新的內容取代子節點。|
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|以新內容取代節點。|

## <a name="see-also"></a>另請參閱

- [XML 樹狀結構](functional-construction.md)
