---
title: HOW TO：強制以傳值 (Visual Basic) 的引數
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 497ae11b858b7d164ba3b5607ff2109254a154de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842040"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>HOW TO：強制以傳值 (Visual Basic) 的引數
程序宣告判斷傳遞機制。 如果參數宣告[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 需要以傳址方式傳遞相對應的引數。 這可讓程序來變更基礎呼叫程式碼中的引數的程式設計項目值。 如果您想要保護對這類變更的基礎項目，您可以覆寫`ByRef`程序中的傳遞機制來呼叫以括弧括住的引數名稱。 這些括號是以呼叫括住的引數清單的括號。  
  
 呼叫端程式碼無法覆寫[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)機制。  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>若要強制以傳值方式傳遞的引數  
  
-   如果對應的參數宣告`ByVal`在程序中，您不需要採取任何額外的步驟。 Visual Basic 已經需要以傳值方式傳遞引數。  
  
-   如果對應的參數宣告`ByRef`在程序中，括住的程序呼叫中的括號括住的引數。  
  
## <a name="example"></a>範例  
 下列範例會覆寫`ByRef`參數宣告。 會強制呼叫中`ByVal`，請注意括號內的兩個層級。  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 當`str`額外引數清單中中的括號括住`setNewString`程序不能變更呼叫程式碼，其值和`MsgBox`顯示如果傳遞 ByVal 無法取代 「 」。 當`str`未隨附在額外的括號中的程序可以將它變更，和`MsgBox`顯示"This is inString 引數的新值"。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 當您參考所傳遞的變數時，您必須使用`ByRef`關鍵字來指定這項機制。  
  
 在 Visual Basic 中的預設值是以傳值方式傳遞引數。 不過，它是良好的程式設計方式來包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或是[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。 這可讓您的程式碼更容易讀取。  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果程序宣告的參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，正確執行的程式碼可能會因無法變更呼叫程式碼對應的項目而定。 呼叫程式碼覆寫此呼叫的機制，藉由將引數括在括號內，則它會傳遞為不可修改引數，此程序就無法變更基礎的項目。 這可能會產生非預期的結果，在呼叫程式碼。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 允許的程序來變更基礎呼叫程式碼中的引數的值中一律會有潛在的風險。 請確定您預期此值變更，並準備好使用之前，先將這些資料檢查有效性。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [可修改引數和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [以傳值或傳址方式傳遞引數的差別](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [如何：程序引數的值變更](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
