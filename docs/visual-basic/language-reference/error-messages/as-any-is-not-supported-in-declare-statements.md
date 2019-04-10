---
title: "'Declare' 陳述式中不支援 'As Any'"
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: 3593f238c72cbcce911c72e42552d6a75188b628
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310690"
---
# <a name="as-any-is-not-supported-in-declare-statements"></a>'Declare' 陳述式中不支援 'As Any'
`Any`資料類型用於`Declare`允許無法包含任何資料類型的引數使用的 Visual Basic 6.0 和更早版本中的陳述式。 Visual Basic 支援多載，不過，並因此會`Any`資料型別已經過時。  
  
 **錯誤 ID:** BC30828  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 宣告您想要使用的特定型別參數比方說。  
  
     [!code-vb[VbVbalrStatements#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#95)]  
  
2. 使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性來指定`As Any`當`Void*`預期的被呼叫程序。  
  
     [!code-vb[VbVbalrStatements#96](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#96)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [逐步解說：呼叫 Windows Api](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)
- [在 Managed 程式碼中建立原型](../../../framework/interop/creating-prototypes-in-managed-code.md)
