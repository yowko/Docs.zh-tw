---
title: 如何：比對字串和模式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: aef378bfc32d6deff431a2caac1261a6cd7520c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>如何：比對字串和模式 (Visual Basic)
如果您想要找出是否有運算式[字串資料型別](../../../../visual-basic/language-reference/data-types/string-data-type.md)符合模式，則您可以使用[Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)。  
  
 `Like` 它會使用兩個運算元。 左的運算元是一個字串運算式，和右運算元是字串，包含要用來比對的模式。 `Like` 傳回`Boolean`值，指出字串運算式是否符合模式。  
  
 您可以比對的字串運算式，針對特定的字元、 萬用字元、 字元清單或字元範圍中每個字元。 要比對字串運算式中的字元位置的對應的規格，模式字串中的位置。  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>比對特定字元字串運算式中  
  
-   特定的字元直接放在模式比對字串。 某些特殊字元必須括在方括號 (`[ ]`)。 如需詳細資訊，請參閱[Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)。  
  
     下列範例會測試是否`myString`完全組成的單一字元`H`。  
  
     [!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>若要符合萬用字元的字串運算式中的字元  
  
-   將問號 (`?`)，模式字串中。 任何有效的字元在這個位置可比對成功。  
  
     下列範例會測試是否`myString`組成的單一字元`W`後面兩個字元的任何值。  
  
     [!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>要比對的字元清單的字串運算式中的字元  
  
-   加上方括弧 (`[ ]`) 模式字串中，並將字元清單的括號內。 不需以逗號或任何其他分隔符號分隔保留字元。 在清單中的任何單一字元可比對成功。  
  
     下列範例會測試是否`myString`後面接著一個字元的任何有效字元組成`A`， `C`，或`E`。  
  
     [!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]  
  
     請注意，此項比對是區分大小寫。  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>要比對的字元範圍的字串運算式中的字元  
  
-   加上方括弧 (`[ ]`) 以連字號分隔的模式字串中，括號的最低和最高的字元放在範圍內 (`–`)。 在範圍內的任何單一字元可比對成功。  
  
     下列範例會測試是否`myString`字元組成`num`只有其中一個字元後面接著`i`， `j`， `k`， `l`， `m`，或`n`。  
  
     [!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]  
  
     請注意，此項比對是區分大小寫。  
  
## <a name="matching-empty-strings"></a>比對空字串  
 `Like` 會將序列`[]`為零長度字串 (`""`)。 您可以使用`[]`來測試是否整個字串運算式是空的但您無法使用它來測試是否是空的字串運算式中的特定位置。 空位置是其中一個選項，如果您要測試，您可以使用`Like`一次以上。  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>要比對的字元或字元清單的字串運算式中的字元  
  
1.  呼叫`Like`運算子兩次相同的字串運算式，並連接兩個呼叫其中一種[或運算子](../../../../visual-basic/language-reference/operators/or-operator.md)或[OrElse 運算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)。  
  
2.  第一的模式字串中`Like`子句，包括字元清單中，括在括號 (`[ ]`)。  
  
3.  第二個，模式字串中`Like`子句，請不要將任何字元的位置有問題。  
  
     下列範例會測試的七位數電話號碼`phoneNum`正好是三個數值的數字後, 接空格、 連字號 (`–`)、 句號 (`.`)，或沒有字元，後面接著四個位數字。  
  
     [!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [比較運算子](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [運算子和運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)  
 [String 資料類型](../../../../visual-basic/language-reference/data-types/string-data-type.md)
