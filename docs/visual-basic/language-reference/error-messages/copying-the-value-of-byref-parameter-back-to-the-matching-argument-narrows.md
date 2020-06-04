---
title: 將 'ByRef' 參數 '<parametername>' 的值複製回相對應的引數，會從類型 '<typename1>' 減少到類型 '<typename2>'
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: bac5f9a88df719bc64a8b0541f65e5912275866e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409747"
---
# <a name="copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a>將 'ByRef' 參數 '\<parametername>' 的值複製回相對應的引數，會從類型 '\<typename1>' 減少到類型 '\<typename2>'
使用引數來呼叫程式，以擴大至對應的參數類型，且從參數轉換為引數會縮小。  
  
 當您定義類別或結構時，可以定義一個或多個轉換運算子，以將該類別或結構類型轉換成其他類型。 您也可以定義反向轉換運算子，以這些其他類型轉換回您的類別或結構類型。 當您在程序呼叫中使用類別或結構類型時，Visual Basic 可以使用這些轉換運算子將引數的類型轉換成其對應參數的類型。  
  
 如果您傳遞[ByRef](../modifiers/byref.md)引數，Visual Basic 有時會將引數值複製至程式中的區域變數，而不是傳遞參考。 在這種情況下，當程式傳回時，Visual Basic 必須將區域變數值複製回呼叫程式碼中的引數。  
  
 如果將 `ByRef` 引數值複製至程序，而且引數和參數的類型相同，則不需要進行轉換。 但是，如果類型不同，Visual Basic 必須雙向轉換。 如果其中一種類型是您的類別或結構類型，Visual Basic 必須將它轉換成另一種類型。 如果其中一項轉換是擴展的，反向轉換可能會縮小。  
  
 **錯誤識別碼：** BC32053  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 可能的話，請使用與程式參數相同類型的呼叫引數，因此 Visual Basic 不需要進行任何轉換。  
  
- 如果您需要呼叫引數類型與參數類型不同的程序，但不需要將值傳回給呼叫中引數，請將此參數定義為 [ByVal](../modifiers/byval.md) ，而非 `ByRef`。  
  
- 如果您需要將值傳回給呼叫引數，可能的話，請將反向轉換運算子定義為「[擴展](../modifiers/widening.md)」。  
  
## <a name="see-also"></a>另請參閱

- [程序](../../programming-guide/language-features/procedures/index.md)
- [程序參數和引數](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [以傳值和傳址方式傳遞引數](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [運算子程序](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Operator Statement](../statements/operator-statement.md)
- [如何：定義運算子](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Visual Basic 中的類型轉換](../../programming-guide/language-features/data-types/type-conversions.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
