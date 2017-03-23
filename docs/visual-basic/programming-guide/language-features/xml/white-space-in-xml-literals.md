---
title: "XML 常值 (Visual Basic) 中的泛空白字元 |Microsoft 文件"
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
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: b98a88696f24cc0b95401812471d13acea4faa6d
ms.lasthandoff: 03/13/2017

---
# <a name="white-space-in-xml-literals-visual-basic"></a>XML 常值中的空白字元 (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]建立時，編譯器會併入只有顯著泛空白字元字元從 XML 常值[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]物件。 不會納入不顯著泛空白字元。  
  
## <a name="significant-and-insignificant-white-space"></a>顯著與不顯著泛空白字元  
 XML 常值中的空白字元是顯著只有三個方面︰  
  
-   當它們位於屬性值。  
  
-   當它們是項目的文字內容的一部分，文字也包含其他字元。  
  
-   當它們位於內嵌的運算式，表示項目的文字內容。  
  
 否則，編譯器泛空白字元視為無意義，而且不包含然後中[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]的常值的物件。  
  
 若要在 XML 常值中包含不顯著泛空白字元，使用內嵌的運算式，其中包含泛空白字元的常值字串。  
  
> [!NOTE]
>  如果`xml:space`屬性會出現在 XML 項目常值，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器中的屬性會包含<xref:System.Xml.Linq.XElement>物件，但加入此屬性不會變更編譯器如何處理泛空白字元。</xref:System.Xml.Linq.XElement>  
  
## <a name="examples"></a>範例  
 下列範例包含兩個外部和內部的 XML 項目。 這兩個項目包含文字內容中的泛空白字元。 外部的項目中的泛空白字元是不重要，因為它只包含泛空白字元和 XML 項目。 內部項目中的泛空白字元是顯著，因為它包含泛空白字元和文字。  
  
 [!code-vb[VbXMLSamples #&29;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 當執行時，此程式碼會顯示下列文字。  
  
```  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
