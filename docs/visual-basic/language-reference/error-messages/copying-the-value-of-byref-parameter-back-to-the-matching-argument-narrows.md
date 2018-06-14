---
title: 值複製&#39;ByRef&#39;參數&#39; &lt;parametername&gt; &#39;回對應的引數，縮減從型別&#39; &lt;typename1&gt; &#39; &#39; &lt;2>&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: 1d35d7abc6f65dd2e09a54e3e4b817741043ae6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591803"
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a>值複製&#39;ByRef&#39;參數&#39; &lt;parametername&gt; &#39;回對應的引數，縮減從型別&#39; &lt;typename1&gt; &#39; &#39; &lt;2>&gt;&#39;
可擴展為對應的參數類型的引數呼叫的程序，會縮小轉換從參數的引數。  
  
 當您定義類別或結構時，可以定義一個或多個轉換運算子，以將該類別或結構類型轉換成其他類型。 您也可以定義反向轉換運算子，以這些其他類型轉換回您的類別或結構類型。 當您使用類別或結構類型中的程序呼叫時，Visual Basic 就可以使用這些轉換運算子將引數的類型轉換成其對應參數的型別。  
  
 如果您要傳入的引數[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 有時會將引數值複製至區域變數，而不是傳遞參考程序中。 在這種情況下，當程序傳回時，Visual Basic 必須接著將區域變數值複製回呼叫程式碼中的引數。  
  
 如果將 `ByRef` 引數值複製至程序，而且引數和參數的類型相同，則不需要進行轉換。 但如果類型不同，Visual Basic 必須進行雙向轉換。 如果其中一個類型是類別或結構類型時，Visual Basic 必須將它與另一個型別。 如果其中一個這些轉換會擴展，就可能會縮小反向轉換。  
  
 **錯誤 ID:** BC32053  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   可能的話，請使用相同類型的呼叫中引數與程序參數，因此 Visual Basic 就不需要執行任何轉換。  
  
-   如果您要呼叫的程序的引數類型的參數類型不同，但不是需要將值傳回呼叫的引數，定義此參數[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)而不是`ByRef`。  
  
-   如果您要將值傳回呼叫的引數，請定義反向轉換運算子，作為[Widening](../../../visual-basic/language-reference/modifiers/widening.md)如果可能。  
  
## <a name="see-also"></a>另請參閱  
 [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [程序參數和引數](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [以傳值和傳址方式傳遞引數](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [如何：定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [在 Visual Basic 中的型別轉換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
