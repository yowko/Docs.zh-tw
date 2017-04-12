---
title: "如何︰ 判斷兩個物件是否相同 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- testing, objects
- objects [Visual Basic], comparing
- object variables, determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 3a853d9f958829eeb0fb42ecbcdae7ba912c89ed
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>如何：判斷兩個物件是否相同 (Visual Basic)
在[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，兩個變數的參考會視為相同的指標都相同，也就是，如果兩個變數都指向相同的類別執行個體，在記憶體中。 比方說，在 Windows Form 應用程式中，您可能想要進行比較來決定是否目前執行個體 (`Me`) 是相同的特定執行個體，例如`Form2`。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供兩個運算子比較指標。 [Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)傳回`True`如果物件相同，而[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)傳回`True`如果不是。  
  
## <a name="determining-if-two-objects-are-identical"></a>判斷兩個物件是否相同  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>若要判斷兩個物件是否相同  
  
1.  設定`Boolean`來測試兩個物件的運算式。  
  
2.  在測試的運算式中使用`Is`與兩個物件做為運算元的運算子。  
  
     `Is`傳回`True`如果物件是指向相同的類別執行個體。  
  
## <a name="determining-if-two-objects-are-not-identical"></a>判斷兩個物件是否不相同  
 有時候您想要執行的動作，如果兩個物件並不相同，而且它可能很難結合`Not`和`Is`，例如`If Not obj1 Is obj2`。 在此情況下，您可以使用`IsNot`運算子。  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>若要判斷兩個物件是否不相同  
  
1.  設定`Boolean`來測試兩個物件的運算式。  
  
2.  在測試的運算式中使用`IsNot`與兩個物件做為運算元的運算子。  
  
     `IsNot`傳回`True`如果物件未指向相同的類別執行個體。  
  
## <a name="example"></a>範例  
 下列範例會測試組`Object`變數上以查看所指的是相同的類別執行個體。  
  
 [!code-vb[VbVbalrKeywords #&14;](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 上述範例中會顯示下列輸出。  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>另請參閱  
 [Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [如何︰ 判斷兩個物件是否關聯](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
