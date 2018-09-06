---
title: 在 Visual Basic 中存取 XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 0540c52cf3e4cd7594f051c10832ea99cf58a34e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734378"
---
# <a name="accessing-xml-in-visual-basic"></a>在 Visual Basic 中存取 XML
Visual Basic 提供的 XML 軸屬性，用於存取和瀏覽[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]結構。 這些屬性會使用特殊的語法，可讓您指定的 XML 名稱來存取元素和屬性。  
  
 下表列出的語言功能可讓您存取 XML 項目和 Visual Basic 中的屬性。  
  
### <a name="xml-axis-properties"></a>XML 軸屬性  
  
|屬性描述|範例|描述|  
|--------------------------|-------------|-----------------|  
|*子軸*|`contact.<phone>`|取得所有`phone`子項目的項目`contact`項目。|  
|*屬性軸*|`phone.@type`|取得所有`type`屬性的`phone`項目。|  
|*descendant 軸*|`contacts...<name>`|取得所有`name`的項目`contacts`項目，不論發生的階層中深度。|  
|*擴充索引子*|`contacts...<name>(0)`|取得第一個`name`序列中的項目。|  
|*值*|`contacts...<name>.Value`|取得第一個物件的字串表示，在順序中，或`Nothing`如果序列是空的。|  
  
## <a name="in-this-section"></a>本章節內容  
 [如何：存取 XML 子系項目](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 示範如何使用 descendant 軸屬性來存取所有的 XML 項目中具有指定的名稱，以及包含在指定的 XML 項目。  
  
 [如何：存取 XML 子項目](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 示範如何使用子系軸屬性，來存取所有的 XML 子項目中的 XML 項目具有指定的名稱。  
  
 [如何：存取 XML 屬性](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 示範如何使用屬性軸屬性，存取所有的 XML 屬性中的 XML 項目具有指定的名稱。  
  
 [如何：宣告和使用 XML 命名空間前置詞](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 示範如何宣告 XML 命名空間前置詞，並使用它來建立及存取 XML 項目。  
  
## <a name="related-sections"></a>相關章節  
 [XML 軸屬性](../../../../visual-basic/language-reference/xml-axis/index.md)  
 提供各節描述各種不同的 XML 存取內容的連結。  
  
 [Visual Basic 中的 LINQ to XML 概觀](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 簡介如何使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Visual Basic 中。  
  
 [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 提供在 Visual Basic 中使用 XML 常值的簡介。  
  
 [在 Visual Basic 中管理 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 提供載入及修改 XML，在 Visual Basic 中的相關章節的連結。  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 提供描述如何使用章節的連結[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Visual Basic 中。
