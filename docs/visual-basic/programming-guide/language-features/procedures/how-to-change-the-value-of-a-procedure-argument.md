---
title: 如何：變更程序引數的值
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
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: deac87ca4690990a4d00f63d0ea9b843c3f9a9c4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344483"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>如何：變更程序引數的值 (Visual Basic)
當您呼叫程式時，您所提供的每個引數都會對應至程式中所定義的其中一個參數。 在某些情況下，程式碼可以變更呼叫程式碼中引數的基礎值。 在其他情況下，程式只會變更其引數的本機複本。  
  
 當您呼叫程式時，Visual Basic 會為每個傳遞[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)的引數建立本機複本。 對於傳遞了[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)的每個引數，Visual Basic 會提供程式碼直接參考呼叫程式碼中引數的基礎程式設計項目。  
  
 如果呼叫程式碼中的基礎元素是可修改的元素，且引數傳遞 `ByRef`，程式碼就可以使用直接參考來變更呼叫程式碼中的元素值。  
  
## <a name="changing-the-underlying-value"></a>變更基礎值  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>若要在呼叫程式碼中變更程式引數的基礎值  
  
1. 在程式宣告中，針對對應至引數的參數指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) 。  
  
2. 在呼叫程式碼中，傳遞可修改的程式設計項目做為引數。  
  
3. 在呼叫程式碼中，請勿將引數括在引數清單中的括弧內。  
  
4. 在程式碼中，請使用參數名稱，將值指派給呼叫程式碼中的基礎元素。  
  
 如需示範，請參閱進一步的範例。  
  
## <a name="changing-local-copies"></a>變更本機複本  
 如果呼叫程式碼中的基礎元素是無法修改的元素，或如果將引數傳遞 `ByVal`，則程式無法在呼叫程式碼中變更其值。 不過，程式可以變更其這類引數的本機複本。  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>若要在程式碼中變更程式引數的複本  
  
1. 在程式宣告中，針對對應至引數的參數指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) 。  
  
     -或-  
  
     在呼叫程式碼中，將引數括在引數清單中的括弧內。 這會強制 Visual Basic 以傳值方式傳遞引數，即使對應的參數指定 `ByRef`也一樣。  
  
2. 在程式碼中，請使用參數名稱，將值指派給引數的本機複本。 呼叫程式碼中的基礎值不會變更。  
  
## <a name="example"></a>範例  
 下列範例顯示兩個採用陣列變數並在其專案上操作的程式。 `increase` 程式只會將一個專案新增至每個元素。 `replace` 程式會將新的陣列指派給參數 `a()`，然後將其中一個加入至每個元素。  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 第一個 `MsgBox` 呼叫會顯示「增加後（n）：11，21，31，41」。 因為陣列 `n` 是參考型別，所以 `replace` 可以變更其成員，即使傳遞機制 `ByVal`也一樣。  
  
 第二個 `MsgBox` 呼叫會顯示 "After replace （n）：101，201，301"。 因為 `ByRef`傳遞 `n`，`replace` 可以在呼叫程式碼中修改 `n` 的變數，並將新的陣列指派給它。 因為 `n` 是參考型別，`replace` 也可以變更其成員。  
  
 您可以防止程式在呼叫程式碼中修改變數本身。 請參閱[如何：根據值變更保護程式引數](./how-to-protect-a-procedure-argument-against-value-changes.md)。  
  
## <a name="compile-the-code"></a>編譯程式碼  
 當您以傳址方式傳遞變數時，您必須使用 `ByRef` 關鍵字來指定這項機制。  
  
 Visual Basic 中的預設值是以傳值方式傳遞引數。 不過，在每個宣告的參數中包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字是很好的程式設計作法。 這可讓您的程式碼更容易閱讀。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 允許程式變更呼叫程式碼中引數的基礎值，一律會有潛在的風險。 請確定您預期會變更此值，並在使用它之前準備好檢查其有效性。  
  
## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [可修改引數和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [以傳值或傳址方式傳遞引數的差別](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
