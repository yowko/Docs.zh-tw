---
title: "Visual Basic 中字串管理方法的類型"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b437be4a6f4a0cc9d5a4d21291a80c9cb8fffcd3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Visual Basic 中字串管理方法的類型
有幾種不同方式來分析和操作字串。 某些方法屬於[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]語言和其他人所固有`String`類別。  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic 語言和.NET Framework  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]方法會使用做為語言的固有函式。 它們可能使用不需在程式碼中的完整名稱。 下列範例示範典型用法[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]字串操作命令：  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 在此範例中，`Mid`函式會直接操作執行上`aString`和指派值`bString`。  
  
 如需 Visual Basic 字串操作方法的清單，請參閱[字串操作摘要](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)。  
  
### <a name="shared-methods-and-instance-methods"></a>共用的方法和執行個體方法  
 您也可以使用字串操作的方法與`String`類別。 有兩種類型的方法中`String`:*共用*方法和*執行個體*方法。  
  
#### <a name="shared-methods"></a>共用的方法  
 共用的方法是源自於方法`String`類別本身，而且不需要用於該類別的執行個體。 這些方法可以限定的類別名稱 (`String`)，而非執行個體與`String`類別。 例如:   
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 在上述範例中，<xref:System.String.Copy%2A?displayProperty=nameWithType>方法是靜態方法，在運算式上的哪些做它指定，並將結果指派至`bString`。  
  
#### <a name="instance-methods"></a>執行個體方法  
 執行個體方法，相反地，源自於特定的執行個體`String`而且必須具有執行個體名稱限定。 例如:   
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 在此範例中，<xref:System.String.Substring%2A?displayProperty=nameWithType>方法是一種方法的執行個體`String`(也就是`aString`)。 在執行作業`aString`，並將該值指派`bString`。  
  
 如需詳細資訊，請參閱文件<xref:System.String>類別。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
