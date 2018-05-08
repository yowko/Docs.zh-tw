---
title: 如何：強制以傳值方式傳遞引數 (Visual Basic)
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
ms.openlocfilehash: adc58c34150030eb0fc82050576bfecc453e21ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>如何：強制以傳值方式傳遞引數 (Visual Basic)
程序宣告判斷傳遞機制。 如果參數宣告[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 預期依參考傳遞相對應的引數。 這可讓程序來變更呼叫的程式碼中引數的基礎的程式設計項目值。 如果您想要保護對應的項目，針對這類變更，您可以覆寫`ByRef`括弧括住的引數名稱呼叫程序中的傳遞機制。 這些括號是封閉的呼叫中引數清單的括號。  
  
 呼叫程式碼不能覆寫[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)機制。  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>若要強制以傳值方式傳遞的引數  
  
-   如果對應的參數宣告`ByVal`在程序，您不需要採取任何額外的步驟。 Visual Basic 已預期傳值方式傳遞引數。  
  
-   如果對應的參數宣告`ByRef`在程序，將括在括號中的程序呼叫中引數。  
  
## <a name="example"></a>範例  
 下列範例會覆寫`ByRef`參數宣告。 強制執行的呼叫中`ByVal`，請注意括號內的兩個層級。  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 當`str`引數，則清單中的額外括號括住`setNewString`程序不能變更呼叫的程式碼，其值和`MsgBox`顯示如果傳遞 ByVal 無法取代 「 」。 當`str`未加多餘的括號中的程序可以將它變更，並`MsgBox`顯示"This is inString 引數的新值"。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 當您依參考傳遞的變數時，您必須使用`ByRef`關鍵字來指定這項機制。  
  
 在 Visual Basic 中的預設值是以傳值方式傳遞引數。 不過，它是良好的程式設計作法中包含  [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。 這可讓您的程式碼更容易讀取。  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果程序會宣告參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，正確執行的程式碼可能會相依於不能變更呼叫的程式碼中對應的項目。 如果呼叫程式碼覆寫這個呼叫的機制將引數括在括號內，或如果通過不可修改引數，程序不能變更對應的項目。 這可能會產生非預期的結果，呼叫程式碼中。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 在允許的程序來變更對應的引數呼叫的程式碼中的值一律會有潛在的風險。 請確定您預期此變更，並準備好檢查它的有效性，然後再將它的值。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)  
 [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)  
 [可修改引數和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [以傳值或傳址方式傳遞引數的差別](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [如何：變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)  
 [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
