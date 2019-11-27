---
title: 如何：強制以傳值方式傳遞引數
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
ms.openlocfilehash: 8261d126f988bdcf05b4a2af3106b38717e46bc8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344522"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>如何：強制以傳值方式傳遞引數 (Visual Basic)
程式宣告會決定傳遞機制。 如果參數宣告為[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 預期會以傳址方式傳遞對應的引數。 這可讓程式變更呼叫程式碼中引數的基礎程式設計項目的值。 如果您想要保護基礎元素不受這類變更的限制，您可以將引數名稱括在括弧中，以覆寫程序呼叫中的 `ByRef` 傳遞機制。 這些括弧除了括住呼叫中引數清單的括弧之外。  
  
 呼叫程式碼無法覆寫[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)機制。  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>強制以傳值方式傳遞引數  
  
- 如果在程式中 `ByVal` 宣告對應的參數，您就不需要採取任何額外的步驟。 Visual Basic 已經預期會以傳值方式傳遞引數。  
  
- 如果在程式中 `ByRef` 宣告對應的參數，請在程序呼叫的括弧中括住引數。  
  
## <a name="example"></a>範例  
 下列範例會覆寫 `ByRef` 的參數宣告。 在強制 `ByVal`的呼叫中，請注意兩個層級的括弧。  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 當 `str` 以引數清單內的額外括弧括住時，`setNewString` 程式無法在呼叫程式碼中變更其值，而且 `MsgBox` 顯示「如果傳遞 ByVal 就無法取代」。 當 `str` 未以額外的括弧括住時，程式可以變更它，`MsgBox` 會顯示「這是 inString 引數的新值」。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 當您以傳址方式傳遞變數時，您必須使用 `ByRef` 關鍵字來指定這項機制。  
  
 Visual Basic 中的預設值是以傳值方式傳遞引數。 不過，在每個宣告的參數中包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字是很好的程式設計作法。 這可讓您的程式碼更容易閱讀。  
  
## <a name="robust-programming"></a>最佳化程式設計  
 如果程式宣告參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，程式碼的正確執行可能取決於能夠變更呼叫程式碼中的基礎元素。 如果呼叫程式碼會藉由在括弧中括住引數來覆寫此呼叫機制，或如果它傳遞不可修改的引數，此程式就無法變更基礎元素。 這可能會在呼叫程式碼中產生非預期的結果。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 允許程式變更呼叫程式碼中引數的基礎值，一律會有潛在的風險。 請確定您預期會變更此值，並在使用它之前準備好檢查其有效性。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [可修改引數和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [以傳值或傳址方式傳遞引數的差別](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [如何：變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
