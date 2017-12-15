---
title: "XML Value 屬性 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9294c2d1d83dce3bca2abc22ee9c70296fc8014
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="xml-value-property-visual-basic"></a>XML Value 屬性 (Visual Basic)
提供存取集合的第一個元素的值<xref:System.Xml.Linq.XElement>物件。  
  
## <a name="syntax"></a>語法  
  
```  
object.Value  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`object`|必要項。 <xref:System.Xml.Linq.XElement> 物件的集合。|  
  
## <a name="return-value"></a>傳回值  
 A `String` ，其中包含集合的第一個項目值或`Nothing`如果集合是空的。  
  
## <a name="remarks"></a>備註  
 <xref:System.Xml.Linq.XElement.Value%2A>屬性可讓您輕鬆地存取集合中的第一個元素的值<xref:System.Xml.Linq.XElement>物件。 這個屬性會先檢查集合是否包含至少一個物件。 如果集合是空的則這個屬性會傳回`Nothing`。 否則，這個屬性會傳回的值<xref:System.Xml.Linq.XElement.Value%2A>集合中的第一個元素的屬性。  
  
> [!NOTE]
>  當您存取 XML 屬性使用的值 ' @' 屬性值會傳回做為識別項， `String` ，您不需要明確指定<xref:System.Xml.Linq.XAttribute.Value%2A>屬性。  
  
 若要存取集合中的其他項目，您可以使用 XML 擴充索引子屬性。 如需詳細資訊，請參閱[擴充索引子屬性](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)。  
  
## <a name="inheritance"></a>繼承  
 大部分的使用者不需要實作<xref:System.Collections.Generic.IEnumerable%601>，因此可以忽略此區段。  
  
 <xref:System.Xml.Linq.XElement.Value%2A>屬性是實作的型別擴充功能屬性`IEnumerable(Of XElement)`。 這個延伸模組屬性的繫結會使用類似的繫結的擴充方法： 如果類型實作其中一個介面，但會定義具有名稱"Value"的屬性，該屬性優先於擴充功能屬性。 換句話說，這<xref:System.Xml.Linq.XElement.Value%2A>屬性，可以藉由實作類別中定義新的屬性覆寫`IEnumerable(Of XElement)`。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用<xref:System.Xml.Linq.XElement.Value%2A>屬性來存取集合中的第一個節點<xref:System.Xml.Linq.XElement>物件。 此範例會取得名為的所有子節點的集合中使用子軸屬性`phone`處於`contact`物件。  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 此程式碼顯示下列文字：  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>範例  
 下列範例示範如何從集合中取得 XML 屬性的值<xref:System.Xml.Linq.XAttribute>物件。 此範例會顯示的值中使用屬性軸屬性`type`屬性的所有`phone`項目。  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 此程式碼顯示下列文字：  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)  
 [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [擴充索引子屬性](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [XML 子代軸屬性](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [XML 屬性 (Attribute) 軸屬性 (Property)](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
