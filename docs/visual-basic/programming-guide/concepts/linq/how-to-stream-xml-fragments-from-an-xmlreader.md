---
title: "如何︰ 資料流處理 XML 片段，從 XmlReader (Visual Basic) |Microsoft 文件"
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
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c9c60bb4730ef6569390f76f63c40a2cbd1c9524
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a>如何︰ 資料流處理 XML 片段，從 XmlReader (Visual Basic)
當您必須處理大型 XML 檔案時，可能無法將整個 XML 樹狀載入記憶體中。 本主題示範如何串流片段使用<xref:System.Xml.XmlReader>。</xref:System.Xml.XmlReader>  
  
 其中一種最有效的方式使用<xref:System.Xml.XmlReader>讀取<xref:System.Xml.Linq.XElement>物件為撰寫您自己的自訂座標軸方法。</xref:System.Xml.Linq.XElement> </xref:System.Xml.XmlReader> 座標軸方法通常會傳回集合例如<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>，如本主題中範例所示。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 在自訂座標軸方法呼叫來建立 XML 片段後<xref:System.Xml.Linq.XNode.ReadFrom%2A>方法，傳回集合使用`yield return`。</xref:System.Xml.Linq.XNode.ReadFrom%2A> 這會將延後執行語意 (Semantics) 提供給您自訂的座標軸方法。  
  
 當您建立 XML 樹狀結構從<xref:System.Xml.XmlReader>物件，<xref:System.Xml.XmlReader>必須置於項目。</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XNode.ReadFrom%2A>方法不會傳回讀取項目的關閉標記前。</xref:System.Xml.Linq.XNode.ReadFrom%2A>  
  
 如果您想要建立部分樹狀結構，您可以執行個體化<xref:System.Xml.XmlReader>，將讀取器定位在您想要轉換成節點<xref:System.Xml.Linq.XElement>樹狀結構，然後再建立<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement> </xref:System.Xml.XmlReader>  
  
 本主題[How to︰ 資料流 XML 片段並存取標頭資訊 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)包含資訊和範例如何串流更複雜的文件。  
  
 本主題[How to︰ 執行串流轉換的大型 XML 文件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md)包含使用 LINQ to XML 轉換非常大的 XML 文件，同時維護小的記憶體使用量的範例。  
  
## <a name="example"></a>範例  
 這個範例會建立自訂座標軸方法。 您可以使用 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢進行查詢。 自訂座標軸方法  `StreamRootChildDoc` 是一種方法，特別針對讀取具有重複 `Child` 項目的文件而設計。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 這個範例會產生下列輸出：  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 在此範例中，來源文件很小。 但是，即使有數百萬的 `Child` 元素，此範例的記憶體使用量還是很小。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰ 在 Visual Basic 中實作 IEnumerable(Of T)](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)   
 [剖析 XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
