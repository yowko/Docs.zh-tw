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
ms.openlocfilehash: b0504d9f7a8862274d5d71dc6a9c1570551629a5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414359"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>如何：防止程序引數的值變更 (Visual Basic)
如果程式將參數宣告為[ByRef](../../../language-reference/modifiers/byref.md)，Visual Basic 會提供程式碼直接參考呼叫程式碼中引數的基礎程式設計項目。 這允許程式變更呼叫程式碼中引數的基礎值。 在某些情況下，呼叫程式碼可能會想要防止這類變更。  
  
 您隨時可以在程式中宣告對應的參數[ByVal](../../../language-reference/modifiers/byval.md) ，藉此保護引數的變更。 如果您想要在某些情況下變更指定的引數，而不是其他情況，您可以宣告它， `ByRef` 然後讓呼叫程式碼判斷每次呼叫中的傳遞機制。 其執行方式是將對應的引數括在括弧中，以傳值方式傳遞它，或不將其括在括弧中以傳址方式傳遞。 如需詳細資訊，請參閱[如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)。  
  
## <a name="example"></a>範例  
 下列範例顯示兩個採用陣列變數並在其專案上操作的程式。 此程式 `increase` 只會將一個專案新增至每個元素。 程式會將 `replace` 新的陣列指派給參數 `a()` ，然後將它加入至每個元素。 不過，重新指派並不會影響呼叫程式碼中的基礎陣列變數。  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 第一個 `MsgBox` 呼叫會顯示「增加（n）：11，21，31，41」。 因為陣列 `n` 是參考型別，所以 `increase` 可以變更其成員，即使傳遞機制是也一樣 `ByVal` 。  
  
 第二個 `MsgBox` 呼叫會顯示「取代（n）：11，21，31，41」。 因為 `n` 傳遞了 `ByVal` ，所以 `replace` 無法 `n` 在呼叫程式碼中修改變數，方法是指派新的陣列給它。 當 `replace` 建立新的陣列實例 `k` 並將它指派給本機變數時 `a` ，它會失去 `n` 呼叫程式碼傳入的參考。 當它變更的成員時 `a` ，只有本機陣列 `k` 會受到影響。 因此，不 `replace` 會遞增呼叫程式碼中的陣列值 `n` 。  
  
## <a name="compile-the-code"></a>編譯程式碼  
 Visual Basic 中的預設值是以傳值方式傳遞引數。 不過，在每個宣告的參數中包含[ByVal](../../../language-reference/modifiers/byval.md)或[ByRef](../../../language-reference/modifiers/byref.md)關鍵字是很好的程式設計作法。 這可讓您的程式碼更容易閱讀。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [可修改引數和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [以傳值或傳址方式傳遞引數的差別](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [如何：變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [Value Types and Reference Types](../data-types/value-types-and-reference-types.md)
