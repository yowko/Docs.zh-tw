---
title: Visual Basic 中字串管理方法的類型
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: a75984d0eb64ef8c18def3ae59d5e1f4b6d20ce2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980333"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Visual Basic 中字串管理方法的類型
有數個不同的方式，來分析及管理您的字串。 某些方法屬於 Visual Basic 語言的有些則是內在`String`類別。  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic 語言和.NET Framework  
 做為語言的固有的函式會使用 Visual Basic 方法。 它們必須配合您的程式碼中的限定性條件。 下列範例會示範 Visual Basic 字串操作命令的一般用法：  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 在此範例中，`Mid`函式上執行直接運算`aString`並將值指派給`bString`。  
  
 如需 Visual Basic 字串操作方法的清單，請參閱 <<c0> [ 字串操作摘要](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)。  
  
### <a name="shared-methods-and-instance-methods"></a>共用的方法和執行個體方法  
 您也可以使用的方法來操作字串`String`類別。 有兩種類型的方法中`String`:*共用*方法並*執行個體*方法。  
  
#### <a name="shared-methods"></a>共用的方法  
 共用的方法是方法，就是源自`String`類別本身，而且不需要運作該類別的執行個體。 這些方法可以限定的類別名稱 (`String`)，而不是與執行個體`String`類別。 例如:   
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 在上述範例中，<xref:System.String.Copy%2A?displayProperty=nameWithType>方法是靜態方法，它就在運算式上的它提供，並將產生的值指派`bString`。  
  
#### <a name="instance-methods"></a>執行個體方法  
 執行個體方法，相較之下，源自於特定執行個體`String`和必須以執行個體名稱加以限定。 例如:   
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 在此範例中，<xref:System.String.Substring%2A?displayProperty=nameWithType>方法是一種方法的執行個體`String`(也就是`aString`)。 在執行作業`aString`，並將該值指派`bString`。  
  
 如需詳細資訊，請參閱文件<xref:System.String>類別。  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
