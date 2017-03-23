---
title: "在 Visual Basic 中字串管理方法的類型 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: 12
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
ms.openlocfilehash: 349cfdb3e31225f6aeba90ac29aa1c66e37c7e11
ms.lasthandoff: 03/13/2017

---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Visual Basic 中字串管理方法的類型
有幾種不同方式來分析和操作字串。 某些方法屬於[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]語言和其他人所固有`String`類別。  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic 語言和.NET Framework  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]方法用做為語言的固有的函式。 它們可能會無限制地在程式碼中使用。 下列範例示範一般用法[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]字串操作命令︰  
  
 [!code-vb[VbVbalrStrings #&44;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 在此範例中，`Mid`函式上執行直接操作`aString`和指派值給`bString`。  
  
 如需 Visual Basic 字串管理方法的清單，請參閱[字串操作摘要](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)。  
  
### <a name="shared-methods-and-instance-methods"></a>共用的方法和執行個體方法  
 您也可以使用的方法來操作字串`String`類別。 有兩種方法在`String`:*共用*方法和*執行個體*方法。  
  
#### <a name="shared-methods"></a>共用的方法  
 共用的方法是源自於方法`String`類別本身並不需要用於該類別的執行個體。 這些方法可以限定的類別名稱 (`String`)，而不是執行個體`String`類別。 例如:   
  
 [!code-vb[VbVbalrStrings #&45;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 在上述範例中，<xref:System.String.Copy%2A?displayProperty=fullName>方法是靜態方法，它就在運算式上的它會指定，並將結果指派至`bString`。</xref:System.String.Copy%2A?displayProperty=fullName>  
  
#### <a name="instance-methods"></a>執行個體方法  
 執行個體方法，相較之下，源自於特定執行個體`String`和必須以執行個體名稱加以限定。 例如:   
  
 [!code-vb[VbVbalrStrings #&46;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 在此範例中，<xref:System.String.Substring%2A?displayProperty=fullName>方法是一種方法的執行個體`String`(也就是`aString`)。</xref:System.String.Substring%2A?displayProperty=fullName> 在執行作業上`aString`，並將該值指派`bString`。  
  
 如需詳細資訊，請參閱文件<xref:System.String>類別。</xref:System.String>  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
