---
title: "&quot;As Any&quot; 是 &quot;Declare&quot; 陳述式不支援 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30828
- vbc30828
dev_langs:
- VB
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: 11
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
ms.openlocfilehash: fb179ae938d4c132f61e2076248729f7ea15a13f
ms.lasthandoff: 03/13/2017

---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a>'As Any' 不支援 'Declare' 陳述式中
`Any`資料類型用於`Declare`允許無法包含任何資料類型的引數使用的 Visual Basic 6.0 及舊版中的陳述式。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]多載，不過，支援，因此讓`Any`資料型別已經過時。  
  
 **錯誤識別碼︰** BC30828  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  宣告參數的特定型別，您想要使用;例如。  
  
     [!code-vb[VbVbalrStatements #&95;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性來指定`As Any`時`Void*`所呼叫的程序所預期。</xref:System.Runtime.InteropServices.MarshalAsAttribute>  
  
     [!code-vb[VbVbalrStatements #&96;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute></xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [逐步解說︰ 呼叫 Windows Api](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)   
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [在 Managed 程式碼中建立原型](http://msdn.microsoft.com/library/ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d)
