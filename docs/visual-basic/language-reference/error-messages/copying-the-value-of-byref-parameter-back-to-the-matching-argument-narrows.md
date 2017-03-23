---
title: "將 &quot;ByRef&quot; 參數的值複製 &quot;&lt;parametername&gt;&quot;回到相符的引數，以縮小範圍從型別&quot;&lt;typename1&gt;&quot; to type&quot;&lt;typename2&gt;&quot; |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
dev_langs:
- VB
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 84574006b2e2ccc669fdd83ebfb6eec06b00f041
ms.lasthandoff: 03/13/2017

---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a>將 'ByRef' 參數的值複製 '&lt;parametername&gt;'回到相符的引數，以縮小範圍從型別'&lt;typename1&gt;' to type'&lt;typename2&gt;'
被呼叫的引數來擴展至對應的參數型別，並從參數轉換成引數會縮小。  
  
 當您定義類別或結構時，可以定義一個或多個轉換運算子，以將該類別或結構類型轉換成其他類型。 您也可以定義反向轉換運算子，以這些其他類型轉換回您的類別或結構類型。 當您在程序呼叫中，使用您的類別或結構類型[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]這些轉換運算子可用於將引數類型轉換為其對應的參數類型。  
  
 如果您沒有傳遞引數[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]有時會將引數的值複製到本機變數中的程序，而不是傳遞參考。 在此情況下，此程序傳回時，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]必須再複製回呼叫程式碼中的引數的本機變數的值。  
  
 如果將 `ByRef` 引數值複製至程序，而且引數和參數的類型相同，則不需要進行轉換。 如果型別不同，但[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]必須進行雙向轉換。 如果其中一個型別是類別或結構類型[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]必須將它轉換和其他類型。 如果這些轉換的其中一個擴展轉換，可能會縮小反向的轉換。  
  
 **錯誤識別碼︰** BC32053  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   可能的話，做為呼叫的引數相同型別的程序參數，因此[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]不需要執行任何轉換。  
  
-   如果您要呼叫的引數的程序輸入的參數型別不同，但不是需要將值傳回呼叫的引數，定義此參數[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)而不是`ByRef`。  
  
-   如果您需要將值傳回呼叫的引數，定義為反向轉換運算子[擴大](../../../visual-basic/language-reference/modifiers/widening.md)、 的話。  
  
## <a name="see-also"></a>另請參閱  
 [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [程序參數和引數](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [傳遞引數以傳值或傳址](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [如何︰ 定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [如何︰ 定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [在 Visual Basic 中的型別轉換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
