---
title: 存取 XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 1fa1d94fc710272ac0ba9ea7167989da42a51fcd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351753"
---
# <a name="accessing-xml-in-visual-basic"></a>在 Visual Basic 中存取 XML
Visual Basic 提供 XML 軸屬性來存取和流覽 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 結構。 這些屬性會使用特殊語法，讓您藉由指定 XML 名稱來存取元素和屬性。  
  
 下表列出的語言功能可讓您存取 Visual Basic 中的 XML 元素和屬性。  
  
### <a name="xml-axis-properties"></a>XML 軸屬性  
  
|屬性描述|範例|描述|  
|--------------------------|-------------|-----------------|  
|*子軸*|`contact.<phone>`|取得屬於 `contact` 元素之子專案的所有 `phone` 專案。|  
|*屬性軸*|`phone.@type`|取得 `phone` 元素的所有 `type` 屬性。|  
|*子代軸*|`contacts...<name>`|取得 `contacts` 專案的所有 `name` 專案，不論其發生的階層深度為何。|  
|*延伸模組索引子*|`contacts...<name>(0)`|從序列中取得第一個 `name` 元素。|  
|*值*|`contacts...<name>.Value`|取得序列中第一個物件的字串表示，如果序列是空的，則為 `Nothing`。|  
  
## <a name="in-this-section"></a>本節內容  
 [如何：存取 XML 子系項目](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 示範如何使用子代軸屬性來存取所有具有指定名稱且包含在指定之 XML 專案底下的 XML 元素。  
  
 [如何：存取 XML 子項目](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 示範如何使用子軸屬性來存取 XML 元素中所有具有指定名稱的 XML 子專案。  
  
 [如何：存取 XML 屬性](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 示範如何使用屬性軸屬性來存取 XML 元素中所有具有指定名稱的 XML 屬性。  
  
 [如何：宣告和使用 XML 命名空間前置詞](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 示範如何宣告 XML 命名空間前置詞，並使用它來建立和存取 XML 元素。  
  
## <a name="related-sections"></a>相關章節  
 [XML 軸屬性](../../../../visual-basic/language-reference/xml-axis/index.md)  
 提供描述各種 XML 存取屬性之區段的連結。  
  
 [Visual Basic 中的 LINQ to XML 概觀](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 提供在 Visual Basic 中使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的簡介。  
  
 [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 提供在 Visual Basic 中使用 XML 常值的簡介。  
  
 [在 Visual Basic 中管理 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 提供有關在 Visual Basic 中載入和修改 XML 的章節連結。  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 提供章節的連結，說明如何在 Visual Basic 中使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]。
