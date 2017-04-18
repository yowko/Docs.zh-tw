---
title: "擴充索引子屬性 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyExtensionIndexer
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 25f434a5b5f8caf013ad5f778897e4e98e3d825d
ms.lasthandoff: 03/13/2017

---
# <a name="extension-indexer-property-visual-basic"></a>擴充索引子屬性 (Visual Basic)
提供集合中個別項目的存取。  
  
## <a name="syntax"></a>語法  
  
```  
  
object(index)  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`object`|必要項。 可查詢的集合。 也就是實作<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601></xref:System.Collections.Generic.IEnumerable%601>集合|  
|(|必要項。 代表索引子屬性開始。|  
|`index`|必要項。 整數運算式，指定集合中項目的以零為起始的位置。|  
|)|必要項。 代表索引子屬性的結尾。|  
  
## <a name="return-value"></a>傳回值  
 從集合中指定位置的物件或`Nothing`如果索引超出範圍。  
  
## <a name="remarks"></a>備註  
 擴充索引子屬性可用來存取集合中的個別項目。 這個索引子屬性通常是 XML 軸屬性的輸出。 XML 子代和 XML 子代軸屬性傳回的集合傳回<xref:System.Xml.Linq.XElement>物件或屬性值。</xref:System.Xml.Linq.XElement>  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將延伸模組索引子屬性轉換為呼叫`ElementAtOrDefault`方法。 不同於陣列索引子，`ElementAtOrDefault`方法會傳回`Nothing`如果索引超出範圍。 這種行為時，您無法輕易判斷集合中的項目數。  
  
 這個索引子屬性就像延伸模組屬性的集合，實作<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>︰ 集合並沒有索引子或預設屬性時，才使用它。</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601>  
  
 若要存取的集合中的第一個項目值<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XAttribute>物件，您可以使用 XML`Value`屬性。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> 如需詳細資訊，請參閱[XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用擴充索引子存取集合中的第二個的子節點<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement> 使用子代軸屬性，它會取得所有子項目，名為存取集合`phone`中`contact`物件。  
  
 [!code-vb[VbXMLSamples #&24;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 此程式碼顯示下列文字：  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XElement>   
 [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)   
 [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
