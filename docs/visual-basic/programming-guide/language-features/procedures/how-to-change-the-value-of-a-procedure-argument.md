---
title: 如何：變更程序引數的值 (Visual Basic)
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
ms.openlocfilehash: 118dd3389804794801d39e7d67b68ab195bbad3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>如何：變更程序引數的值 (Visual Basic)
當您呼叫程序時，您提供每個引數會對應至其中一個程序中定義的參數。 在某些情況下，程序程式碼可以變更對應的引數呼叫的程式碼中的值。 在其他情況下，此程序可以變更引數的本機複本。  
  
 當您呼叫程序時，Visual Basic 可讓每個傳遞的引數的本機副本[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。 每個引數傳遞[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 提供的程序程式碼直接呼叫程式碼中的引數的基礎的程式設計項目參考。  
  
 如果呼叫的程式碼中對應的項目為可修改的項目，並傳遞引數`ByRef`，程序程式碼可以使用直接參考來變更呼叫的程式碼中的項目值。  
  
## <a name="changing-the-underlying-value"></a>變更基礎值  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>若要變更基礎值的程序中的引數呼叫的程式碼  
  
1.  在程序宣告中，指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)對應的引數的參數。  
  
2.  在呼叫的程式碼，將傳遞做為引數的可修改的程式設計項目。  
  
3.  在呼叫程式碼中，未將引數清單中的括號中的引數。  
  
4.  在程序程式碼中，使用參數名稱來指派值給呼叫程式碼中對應的項目。  
  
 請參閱範例進一步示範。  
  
## <a name="changing-local-copies"></a>變更本機複本  
 如果呼叫的程式碼中對應的項目是不可修改的項目，或者引數傳遞`ByVal`，程序無法變更其呼叫的程式碼中的值。 不過，此程序可以變更這類引數的本機複本。  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>若要變更的程序程式碼中的程序引數的複本  
  
1.  在程序宣告中，指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)對應的引數的參數。  
  
     -或-  
  
     在呼叫程式碼中，括住引數清單中的括號中的引數。 這會強制以傳值的引數的 Visual Basic，即使對應的參數會指定`ByRef`。  
  
2.  在程序程式碼中，使用參數名稱來指派值給引數的本機副本。 不會變更呼叫的程式碼中的基礎值。  
  
## <a name="example"></a>範例  
 下列範例會示範兩個程序的方式取得陣列變數和操作其項目上。 `increase`程序只會加入一個，以便每個項目。 `replace`程序會將新的陣列指派給參數`a()`再加入一個，以便每個項目。  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 第一個`MsgBox`呼叫顯示"之後 increase(n): 11、 21、 31、 41"。 因為陣列`n`是參考型別，`replace`可以變更其成員，即使傳遞機制`ByVal`。  
  
 第二個`MsgBox`呼叫顯示"之後 replace(n): 101、 201、 301"。 因為`n`傳遞`ByRef`，`replace`可以修改變數`n`中呼叫程式碼並指派給它的新陣列。 因為`n`是參考型別，`replace`也可以變更它的成員。  
  
 您可以防止程序修改呼叫程式碼本身的變數。 請參閱[如何： 防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 當您依參考傳遞的變數時，您必須使用`ByRef`關鍵字來指定這項機制。  
  
 在 Visual Basic 中的預設值是以傳值方式傳遞引數。 不過，它是良好的程式設計作法中包含  [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。 這可讓您的程式碼更容易讀取。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 在允許的程序來變更對應的引數呼叫的程式碼中的值一律會有潛在的風險。 請確定您預期此變更，並準備好檢查它的有效性，然後再將它的值。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)  
 [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)  
 [可修改引數和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [以傳值或傳址方式傳遞引數的差別](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
