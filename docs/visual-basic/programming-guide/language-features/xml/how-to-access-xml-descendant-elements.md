---
title: "如何：存取 XML 子代項目 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7b3b6c8ac96bd18a379804b83f3ab3e48a5b0c89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>如何：存取 XML 子代項目 (Visual Basic)
這個範例示範如何使用子代 axis 屬性來存取所有的 XML 項目具有指定的名稱的資料，而且包含在 XML 項目。 特別是，它會使用`Value`屬性集合中取得的第一個項目值`name`子代軸屬性傳回。 `name`子代 axis 屬性會取得名為的所有項目`name`包含在`contacts`物件。 此範例也會使用`phone`子代 axis 屬性來存取具名的所有下階`phone`包含在`contacts`物件。  
  
## <a name="example"></a>範例  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   <xref:System.Xml.Linq> 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>  
 [XML 子系軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)  
 [XML Value 屬性](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [在 Visual Basic 中存取 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
