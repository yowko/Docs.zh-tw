---
title: 如何：防止程序引數的值變更
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: 36092eb597b5b20e1da42cd9d15ab8633636cfb1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344851"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>如何：防止程序引數的值變更 (Visual Basic)
如果程式將參數宣告為[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 會提供程式碼直接參考呼叫程式碼中引數的基礎程式設計項目。 這允許程式變更呼叫程式碼中引數的基礎值。 在某些情況下，呼叫程式碼可能會想要防止這類變更。  
  
 您隨時可以在程式中宣告對應的參數[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ，藉此保護引數的變更。 如果您想要在某些情況下變更指定的引數，而不是其他情況，則可以將它宣告 `ByRef` 並讓呼叫程式碼判斷每次呼叫中的傳遞機制。 其執行方式是將對應的引數括在括弧中，以傳值方式傳遞它，或不將其括在括弧中以傳址方式傳遞。 如需詳細資訊，請參閱[如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)。  
  
## <a name="example"></a>範例  
 下列範例顯示兩個採用陣列變數並在其專案上操作的程式。 `increase` 程式只會將一個專案新增至每個元素。 `replace` 程式會將新的陣列指派給參數 `a()`，然後將其中一個加入至每個元素。 不過，重新指派並不會影響呼叫程式碼中的基礎陣列變數。  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 第一個 `MsgBox` 呼叫會顯示「增加後（n）：11，21，31，41」。 因為陣列 `n` 是參考型別，所以 `increase` 可以變更其成員，即使傳遞機制 `ByVal`也一樣。  
  
 第二個 `MsgBox` 呼叫會顯示「取代後（n）：11，21，31，41」。 因為 `ByVal`傳遞 `n`，所以 `replace` 無法藉由指派新的陣列來修改呼叫程式碼中 `n` 的變數。 當 `replace` 建立新的陣列實例 `k`，並將它指派給本機變數 `a`時，就會失去呼叫程式碼所傳入之 `n` 的參考。 當它變更 `a`的成員時，只有本機陣列 `k` 會受到影響。 因此，`replace` 不會在呼叫程式碼中增加陣列 `n` 的值。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 Visual Basic 中的預設值是以傳值方式傳遞引數。 不過，在每個宣告的參數中包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字是很好的程式設計作法。 這可讓您的程式碼更容易閱讀。  
  
## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [可修改引數和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [以傳值或傳址方式傳遞引數的差別](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [如何：變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
