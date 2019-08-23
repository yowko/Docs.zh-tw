---
title: XML 常值中的空白字元 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: f72dcc25b158d793850069e5cc32c3a3c02fad17
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939217"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>XML 常值中的空白字元 (Visual Basic)
Visual Basic 編譯器在建立[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件時, 只會納入 XML 常值中的重要空白字元。 無意義的空白字元不會合並。  
  
## <a name="significant-and-insignificant-white-space"></a>重要且無意義的空白字元  
 XML 常值中的空白字元只有三個區域才有意義:  
  
- 當它們在屬性值中時。  
  
- 當它們是元素文字內容的一部分, 而且文字也包含其他字元時。  
  
- 當它們位於專案文字內容的內嵌運算式中時。  
  
 否則, 編譯器會將空白字元視為不重要的字元, 而且不會在常[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]值的物件中包含。  
  
 若要在 XML 常值中包含無意義的空白字元, 請使用包含含有空白字元之字串常值的內嵌運算式。  
  
> [!NOTE]
> 如果屬性出現在 XML 專案常值中, Visual Basic 編譯器會在<xref:System.Xml.Linq.XElement>物件中包含屬性, 但新增這個屬性並不會變更編譯器處理空白字元的方式。 `xml:space`  
  
## <a name="examples"></a>範例  
 下列範例包含兩個 XML 元素, 外部和內部。 這兩個元素在其文字內容中都包含空白字元。 專用項目中的空白字元是不重要的, 因為它只包含空白字元和 XML 元素。 內部元素中的空白字元很重要, 因為它包含空白字元和文字。  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 執行時, 此程式碼會顯示下列文字。  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>另請參閱

- [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
