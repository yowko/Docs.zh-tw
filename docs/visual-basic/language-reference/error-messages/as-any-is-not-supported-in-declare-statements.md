---
title: '&#39;做為任何&#39;中不支援&#39;Declare&#39;陳述式'
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: 34beaeb7178645d5a167d1b7b969bb3e4f500e1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a>&#39;做為任何&#39;中不支援&#39;Declare&#39;陳述式
`Any`資料類型用於`Declare`允許無法包含任何資料類型的引數使用的 Visual Basic 6.0 及舊版中的陳述式。 多載，不過，Visual Basic 支援，因此讓`Any`資料型別已經過時。  
  
 **錯誤 ID:** BC30828  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  宣告您想要使用; 的特定型別參數如需範例。  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性來指定`As Any`時`Void*`必須由被呼叫程序。  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [逐步解說：呼叫 Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [在 Managed 程式碼中建立原型](../../../framework/interop/creating-prototypes-in-managed-code.md)
