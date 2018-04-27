---
title: '&#39;做為任何&#39;中不支援&#39;Declare&#39;陳述式'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d8146e339ac5cb005b99c9a1e02f1cd248c4558b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
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
