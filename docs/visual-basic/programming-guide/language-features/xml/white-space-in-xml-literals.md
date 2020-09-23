---
title: XML 常值中的空白字元
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 5db8f92117e77d96eab34f28758546393e2afca0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91099095"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>XML 常值中的空白字元 (Visual Basic)

Visual Basic 編譯器在建立物件時，只會併入 XML 常值中的重要空白字元 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 。 未併入無意義空白字元。  
  
## <a name="significant-and-insignificant-white-space"></a>重要且無意義的空白字元  

 XML 常值中的空白字元在下列三個區域中是很重要的：  
  
- 當它們在屬性值中時。  
  
- 當它們是元素文字內容的一部分，而且文字也包含其他字元時。  
  
- 當它們位於元素文字內容的內嵌運算式中時。  
  
 否則，編譯器會將空白字元視為不重要，而不會在常值的 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 物件中包含該字元。  
  
 若要在 XML 常值中包含無意義的空白字元，請使用內嵌運算式，其中包含具有空白字元的字串常值。  
  
> [!NOTE]
> 如果 `xml:space` 屬性出現在 XML 專案常值中，Visual Basic 編譯器就會在物件中包含屬性 <xref:System.Xml.Linq.XElement> ，但加入此屬性並不會變更編譯器處理空白字元的方式。  
  
## <a name="examples"></a>範例  

 下列範例包含兩個 XML 元素 outer 和 inner。 這兩個元素在其文字內容中都包含空白字元。 專用項目中的空白字元很重要，因為它只包含空白字元和 XML 元素。 內部元素中的空白字元很重要，因為它包含空白字元和文字。  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 執行時，此程式碼會顯示下列文字。  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>另請參閱

- [在 Visual Basic 中建立 XML](creating-xml.md)
