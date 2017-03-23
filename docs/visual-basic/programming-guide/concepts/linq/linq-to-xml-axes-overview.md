---
title: "LINQ to XML 座標軸概觀 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9161f151-cfa8-4408-94ba-08a9ba3a486d
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b127aa6b443e865c76831d886f110550ec785e9b
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-axes-overview-visual-basic"></a>LINQ to XML 軸心方法概觀 (Visual Basic)
建立 XML 樹狀結構，或將 XML 文件載入到 XML 樹狀結構後，您可以進行查詢以尋找項目和屬性並擷取其值。 擷取集合透過*座標軸方法*，也稱為*座標軸*。 有些座標軸是方法中的<xref:System.Xml.Linq.XElement>和<xref:System.Xml.Linq.XDocument>類別，會傳回<xref:System.Collections.Generic.IEnumerable%601>集合。</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> 有些座標軸是<xref:System.Xml.Linq.Extensions>類別</xref:System.Xml.Linq.Extensions>中的擴充方法 當做擴充方法實作的座標軸會在集合上運算，然後傳回集合。  
  
 中所述[XElement 類別概觀](http://msdn.microsoft.com/library/d35180fe-7016-4895-9bfc-ba1e3f7875ec)、<xref:System.Xml.Linq.XElement>物件都代表單一項目節點。</xref:System.Xml.Linq.XElement> 項目的內容可能很複雜 (有時候稱為結構化的內容)，或者，它可能是簡單的項目。 簡單的項目可以是空的，也可以包含值。 如果節點包含結構化的內容，您可以使用各種座標軸方法來擷取子代項目的列舉。 最常使用的座標軸方法都是<xref:System.Xml.Linq.XContainer.Elements%2A>和<xref:System.Xml.Linq.XContainer.Descendants%2A>.</xref:System.Xml.Linq.XContainer.Descendants%2A> </xref:System.Xml.Linq.XContainer.Elements%2A>  
  
 除了座標軸方法，傳回集合，有兩個多個方法，您通常會使用在[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]查詢。 <xref:System.Xml.Linq.XContainer.Element%2A>方法會傳回單一<xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XContainer.Element%2A> <xref:System.Xml.Linq.XElement.Attribute%2A>方法會傳回單一<xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement.Attribute%2A>  
  
 就許多用途而言，[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢會提供最強大的方式來檢查樹狀結構、從其中擷取資料並加以轉換。 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢是實作物件<xref:System.Collections.Generic.IEnumerable%601>，和[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]座標軸會傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>集合和<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XAttribute>集合。</xref:System.Xml.Linq.XAttribute> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.Generic.IEnumerable%601> 您需要這些集合，才能執行您的查詢。  
  
 除了擷取項目和屬性之集合的座標軸方法之外，還有其他座標軸方法可讓您仔細逐一查看樹狀結構。 例如，您可以使用樹狀結構的節點，而不是處理項目和屬性。 這些節點是比項目和屬性還要細微的位移單位等級。 使用節點時，您可以檢查 XML 註解、文字節點、處理指示等等。 這個功能對於撰寫字組處理器與想要將文件另存為 XML 之類的人而言，相當重要。 不過，多數的 XML 程式設計人員關心的都是項目、屬性及其值。  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>擷取項目集合的方法  
 下列是方法的摘要<xref:System.Xml.Linq.XElement>類別 （或其基底類別），讓您在呼叫<xref:System.Xml.Linq.XElement>傳回項目的集合。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement>  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName>|傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>這個項目的上階。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 多載會傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>祖系具有指定<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName>|傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>的此項目的子代。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 多載會傳回<xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XElement>具有指定<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName>下階</xref:System.Xml.Linq.XElement>的</xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>|傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>這個項目之子項目的。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 多載會傳回<xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XElement>具有指定<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName>之子元素</xref:System.Xml.Linq.XElement>的</xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName>|傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>此項目後的項目。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 多載會傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>這個項目具有指定<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName>後的項目</xref:System.Xml.Linq.XElement></xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>|傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>的項目，這個項目之前。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 多載會傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>這個項目具有指定<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName>之前的項目</xref:System.Xml.Linq.XElement></xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName>|傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>這個項目和其上階。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 多載會傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>項目具有指定<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName>|傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>的這個項目和其子系。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 多載會傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>項目具有指定<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
  
## <a name="method-for-retrieving-a-single-element"></a>擷取單一項目的方法  
 下列方法會擷取單一子系從<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement>  
  
|方法|說明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>|傳回的第一個子<xref:System.Xml.Linq.XElement>物件，其指定<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XElement>|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>擷取屬性集合的方法  
 下列方法會擷取屬性<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement>  
  
|方法|說明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName>|傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XAttribute>的所有屬性。</xref:System.Xml.Linq.XAttribute> </xref:System.Collections.Generic.IEnumerable%601>|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>擷取單一屬性的方法  
 下列方法會擷取單一屬性從<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement>  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>|傳回<xref:System.Xml.Linq.XAttribute>具有指定<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XAttribute>|  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 軸心方法 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
