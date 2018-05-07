---
title: XML 常值中的空白字元 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 60ee90c69aeda38f95107a6043801a4994972079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="white-space-in-xml-literals-visual-basic"></a>XML 常值中的空白字元 (Visual Basic)
Visual Basic 編譯器會在建立時，結合只有顯著泛空白字元字元從 XML 常值[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件。 不會納入無意義的空格字元。  
  
## <a name="significant-and-insignificant-white-space"></a>顯著和不顯著泛空白字元  
 XML 常值中的空白字元就很重要的只有三個方面：  
  
-   當它們位於屬性值。  
  
-   當它們是項目的文字內容的一部分，而且文字也包含其他字元。  
  
-   當仍在內嵌運算式的項目文字內容。  
  
 否則，編譯器會將空格字元視為無意義，而且不包含然後中[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]常值的物件。  
  
 若要在 XML 常值包含有效的空白字元，使用內嵌的運算式，其中包含字串常值空白字元。  
  
> [!NOTE]
>  如果`xml:space`屬性會出現在 XML 元素常值、 Visual Basic 編譯器包含中的屬性<xref:System.Xml.Linq.XElement>物件，但加入此屬性不會變更編譯器如何處理空白字元。  
  
## <a name="examples"></a>範例  
 下列範例包含兩個外部和內部的 XML 項目。 這兩個元素包含文字內容中的空白字元。 外部的項目中的泛空白字元是無意義的因為它只包含空白字元和 XML 項目。 內部項目中的空白字元很重要的因為它包含泛空白字元和文字。  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 當執行時，此程式碼會顯示下列文字。  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
