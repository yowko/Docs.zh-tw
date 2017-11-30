---
title: "複製的值 &#39;ByRef &#39;參數 &#39;&lt;parametername&gt;&#39; 從類型 &#39; 比對的引數以縮小回到&lt;typename1&gt;&#39; 輸入 &#39;&lt;2>&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords: BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4bf993639007162e2e17d4b8cb9dfe8d5316acaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a>複製的值 &#39;ByRef &#39;參數 &#39;&lt;parametername&gt;&#39; 從類型 &#39; 比對的引數以縮小回到&lt;typename1&gt;&#39; 輸入 &#39;&lt;2>&gt;&#39;
可擴展為對應的參數類型的引數呼叫的程序，會縮小轉換從參數的引數。  
  
 當您定義類別或結構時，可以定義一個或多個轉換運算子，以將該類別或結構類型轉換成其他類型。 您也可以定義反向轉換運算子，以這些其他類型轉換回您的類別或結構類型。 當您在程序呼叫中使用類別或結構類型時， [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 可以使用這些轉換運算子將引數的類型轉換成其對應參數的類型。  
  
 如果您要傳入的引數[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]有時會將引數值複製至區域變數，而不是傳遞參考程序中。 在這類情況下，此程序傳回時， [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 接著必須將區域變數值複製回呼叫中程式碼中的引數。  
  
 如果將 `ByRef` 引數值複製至程序，而且引數和參數的類型相同，則不需要進行轉換。 但是，如果類型不同，則 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 必須進行雙向轉換。 如果其中一種類型是類別或結構類型，則 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 必須將它轉換成其他類型，以及從其他類型轉換它。 如果其中一個這些轉換會擴展，就可能會縮小反向轉換。  
  
 **錯誤 ID:** BC32053  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果可能，請使用類型與程序參數相同的呼叫中引數，這樣 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 就不需要執行任何轉換。  
  
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
