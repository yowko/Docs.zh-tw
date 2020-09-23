---
title: 如何：使用定義運算子的類別
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: 083916a420bf4ad182536363ea46448f6b4c1da5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071348"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>如何：使用定義運算子的類別 (Visual Basic)

如果您使用的類別或結構定義了自己的運算子，您可以從 Visual Basic 存取這些運算子。  
  
 在類別或結構上定義運算子 *也稱為多* 載運算子。  
  
## <a name="example"></a>範例  

 下列範例會存取 SQL 結構，此結構會 <xref:System.Data.SqlTypes.SqlString> 定義 ([CType](../../../language-reference/functions/ctype-function.md) 函式的轉換運算子) sql 字串與 Visual Basic 字串之間的雙向函數。 使用 `CType(` *sql 字串運算式*，將 `String)` sql 字串轉換成 Visual Basic 字串，並將 `CType(` *Visual Basic 字串運算式*轉換成 <xref:System.Data.SqlTypes.SqlString> `)` 另一個方向。  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <xref:System.Data.SqlTypes.SqlString>結構會定義轉換運算子 ([CType](../../../language-reference/functions/ctype-function.md)函式) 從 `String` 到 <xref:System.Data.SqlTypes.SqlString> ，另一個從轉換 <xref:System.Data.SqlTypes.SqlString> 為 `String` 。 指派給的語句 `title` `jobTitle` 會使用第一個運算子，且 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式呼叫會使用第二個運算子。  
  
## <a name="compile-the-code"></a>編譯程式碼  

 請確定您使用的類別或結構定義您想要使用的運算子。 請勿假設類別或結構已定義每個可用於多載的運算子。 如需可用運算子的清單，請參閱 [運算子語句](../../../language-reference/statements/operator-statement.md)。  
  
 `Imports`在原始程式檔的開頭包含適用于 SQL 字串的適當語句 (在此案例中 <xref:System.Data.SqlTypes>) 。  
  
 您的專案必須具有 system.string 和 System.XML 的參考。  
  
## <a name="see-also"></a>另請參閱

- [運算子程序](./operator-procedures.md)
- [如何：定義運算子](./how-to-define-an-operator.md)
- [How to: Define a Conversion Operator](./how-to-define-a-conversion-operator.md)
- [如何：呼叫運算子程序](./how-to-call-an-operator-procedure.md)
- [Widening](../../../language-reference/modifiers/widening.md)
- [Narrowing](../../../language-reference/modifiers/narrowing.md)
- [Structure 陳述式](../../../language-reference/statements/structure-statement.md)
- [作法：宣告結構](../data-types/how-to-declare-a-structure.md)
- [隱含和明確轉換](../data-types/implicit-and-explicit-conversions.md)
- [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)
