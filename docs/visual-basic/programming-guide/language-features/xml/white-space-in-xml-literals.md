---
title: XML 常值中的空白字元 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 08be345557d10a528aa03234883eba1b3a31beaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054935"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>XML 常值中的空白字元 (Visual Basic)
Visual Basic 編譯器會在建立時，包含只有顯著泛空白字元字元從 XML 常值[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件。 不會納入不顯著泛空白字元。  
  
## <a name="significant-and-insignificant-white-space"></a>顯著與不顯著泛空白字元  
 XML 常值中的空白字元很重要的只有三個方面：  
  
- 當它們位於屬性值。  
  
- 當它們是項目的文字內容的一部分，文字也包含其他字元。  
  
- 當它們位於項目的文字內容的內嵌運算式。  
  
 否則，編譯器泛空白字元視為無意義，而且不包含然後中[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]的常值的物件。  
  
 若要在 XML 常值包含不顯著泛空白字元，使用內嵌的運算式，其中包含泛空白字元常值的字串。  
  
> [!NOTE]
>  如果`xml:space`屬性會出現在 XML 元素常值、 Visual Basic 編譯器包含中的屬性<xref:System.Xml.Linq.XElement>物件，但新增這個屬性不會變更編譯器如何處理泛空白字元。  
  
## <a name="examples"></a>範例  
 下列範例包含兩個外部和內部的 XML 項目。 這兩個項目會包含其文字內容中的泛空白字元。 外部的項目中的泛空白字元不重要，因為它只包含泛空白字元和 XML 項目。 內部項目中的泛空白字元是顯著，因為它包含泛空白字元和文字。  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 當執行時，此程式碼就會顯示下列文字。  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>另請參閱

- [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
