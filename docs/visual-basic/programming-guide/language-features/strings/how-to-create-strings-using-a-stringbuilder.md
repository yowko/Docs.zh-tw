---
title: HOW TO：在 Visual Basic 中使用 StringBuilder 建立字串
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: dec1afdbd3ca6c0ba719a95906de8cf6fc7ba378
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738795"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>HOW TO：在 Visual Basic 中使用 StringBuilder 建立字串
此範例會建構從許多較小的字串，使用一長串<xref:System.Text.StringBuilder>類別。 <xref:System.Text.StringBuilder>類別的效率高於`&=`將許多字串串連運算子。  
  
## <a name="example"></a>範例  
 下列範例建立的執行個體<xref:System.Text.StringBuilder>類別，將 1000 的字串附加至該執行個體，並接著會傳回它的字串表示。  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a>另請參閱
- [使用 StringBuilder 類別](../../../../standard/base-types/stringbuilder.md)
- [&= 運算子](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [字串](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [建立新字串](../../../../standard/base-types/creating-new.md)
- [操作字串](../../../../standard/base-types/manipulating-strings.md)
