---
title: XElement 和 XDocument Objects2 的有效內容
ms.date: 07/20/2015
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
ms.openlocfilehash: bb5dda6bee0863a2ef951975e92c55184df9d516
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907578"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>XElement 和 XDocument 物件的有效內容
本主題說明可以傳遞給用於將內容加入至項目和文件之建構函式 (Constructor) 和方法的有效引數。  
  
## <a name="valid-content"></a>有效內容  
 查詢通常會評估成 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement> 或 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XAttribute>。 您可以將 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 物件的集合傳遞給 <xref:System.Xml.Linq.XElement> 建構函式。 因此，將查詢的結果當做內容傳入您用來填入 XML 樹狀結構的方法和建構函式會相當方便。  
  
 加入簡單內容時，可以將各種型別傳遞到這個方法。 有效的型別包括：  
  
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
  
 加入複雜內容時，可以將各種型別傳遞到這個方法：  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- 任何實作 <xref:System.Collections.Generic.IEnumerable%601> 的型別  
  
 如果物件實作 <xref:System.Collections.Generic.IEnumerable%601>，系統列舉物件中的集合，並加入集合中的所有項目。 如果集合包含 <xref:System.Xml.Linq.XNode> 或 <xref:System.Xml.Linq.XAttribute> 物件，系統會個別加入集合中的每個項目。 如果集合包含文字 (或轉換為文字的物件)，集合中的文字會遭到串連，並加入為單一文字節點。  
  
 如果內容為 `null`，不會加入任何項目。 傳遞集合時，集合中的項目可以為 `null`。 集合中的 `null` 項目對於樹狀結構沒有任何影響。  
  
 加入的屬性在其包含的項目中必須擁有一個唯一的名稱。  
  
 加入 <xref:System.Xml.Linq.XNode> 或 <xref:System.Xml.Linq.XAttribute> 物件時，如果新內容沒有父代，則物件只會附加到 XML 樹狀結構。 如果新內容已經成為父代，或是其他 XML 樹狀結構的一部分，則會複製新內容，而且新複製的內容會附加到 XML 樹狀結構。  
  
## <a name="valid-content-for-documents"></a>有效的文件內容  
 屬性和簡單的內容無法加入到文件中。  
  
 需要您建立 <xref:System.Xml.Linq.XDocument> 的案例並不多。 不過，您通常可以使用 <xref:System.Xml.Linq.XElement> 根節點來建立 XML 樹狀結構。 除非您有建立文件的特定需求 (例如，因為您必須在頂層建立處理指示與註解，或者您必須支援文件型別)，否則使用 <xref:System.Xml.Linq.XElement> 做為您的根節點通常更方便。  
  
 有效的文件內容包括：  
  
- 零或一個 <xref:System.Xml.Linq.XDocumentType> 物件。 文件型別必須在項目之前。  
  
- 零或一個項目。  
  
- 零或多個註解。  
  
- 零或多個處理指示。  
  
- 只包含一個空白字元的零或多個節點。  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>允許加入內容的建構函式與函式  
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

- [建立 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
