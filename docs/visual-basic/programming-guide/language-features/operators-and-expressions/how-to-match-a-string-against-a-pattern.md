---
title: 作法：比對字串與模式（Visual Basic）
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
ms.openlocfilehash: 0bac0869d9e319071abb31dd0576edf0450aa198
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054158"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>作法：比對字串與模式（Visual Basic）

如果您想要找出[字串資料類型](../../../../visual-basic/language-reference/data-types/string-data-type.md)的運算式是否滿足模式，則可以使用[Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)。

`Like`採用兩個運算元。 左運算元是字串運算式，右運算元是字串，其中包含要用於比對的模式。 `Like``Boolean`傳回值，指出字串運算式是否符合模式。

您可以比對字串運算式中的每個字元與特定字元、萬用字元、字元清單或字元範圍。 模式字串中規格的位置會對應到要在字串運算式中比對的字元位置。

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>若要比對字串運算式中的字元與特定字元

將特定字元直接放在模式字串中。 某些特殊字元必須以方括弧（`[ ]`）括住。 如需詳細資訊，請參閱[Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)。

下列範例會測試是否`myString`完全由單一字元`H`所組成。

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>符合字串運算式中的字元與萬用字元

將問號（`?`）放在模式字串中。 這個位置中的任何有效字元都會成功符合。

下列範例會測試是否`myString`包含單一字元`W` ，後面緊接著任何值的兩個字元。

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>符合字串運算式中的字元與字元清單

在模式字串`[ ]`中加上方括弧（），並在括弧內放入字元清單。 請勿使用逗號或任何其他分隔符號來分隔字元。 清單中的任何單一字元都會成功符合。

下列範例會測試是否`myString`包含任何有效的字元，後面緊接著其中一個字元`A`、 `C`或`E`。

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

請注意，這項比對會區分大小寫。

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>比對字串運算式中的字元與字元範圍

在模式字串`[ ]`中加上方括弧（），並在括弧內放入範圍中的最低和最高字元，並以連`–`字元（）分隔。 範圍內的任何單一字元都會成功符合。

下列範例會測試是否`myString`包含後面接著只有`num`一個`l` `k` `i` `j` `n`字元、 、、、或的字元。`m`

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

請注意，這項比對會區分大小寫。

## <a name="matching-empty-strings"></a>符合空字串

`Like`將序列`[]`視為長度為零的字串（`""`）。 您可以使用`[]`測試整個字串運算式是否是空的，但是您無法使用它來測試字串運算式中的特定位置是否為空白。 如果空白位置是您需要測試的其中一個選項，您可以使用`Like`一次以上。

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>比對字串運算式中的字元與字元清單或無字元

1. 在相同的字串運算式上呼叫運算子兩次，然後使用 [Or 運算子](../../../../visual-basic/language-reference/operators/or-operator.md)或 [OrElse 運算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)來連接兩個`Like`呼叫。

2. 在第一個`Like`子句的模式字串中，包含字元清單，並以方括弧括住`[ ]`（）。

3. 在第二個`Like`子句的模式字串中，不要將任何字元放在有問題的位置。

    下列範例會測試七位數的電話號碼`phoneNum` ，只包含三個數字，後面接著空格、連字號（`–`）、句號（`.`），或完全沒有字元，然後再加上四個數字。

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a>另請參閱

- [比較運算子](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [運算子和運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)
- [String 資料類型](../../../../visual-basic/language-reference/data-types/string-data-type.md)
