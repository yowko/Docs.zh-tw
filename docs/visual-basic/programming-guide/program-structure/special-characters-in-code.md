---
title: 程式碼中的特殊字元 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: 1541ac1793c9f3c082b688fecd4eb82fb5b59590
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726724"
---
# <a name="special-characters-in-code-visual-basic"></a>程式碼中的特殊字元 (Visual Basic)
有時候，您必須使用特殊字元，在您的程式碼，也就是不是字母或數字的字元。 標點符號和特殊字元，Visual Basic 字元集中的有許多用途，從組織程式文字到定義編譯器或編譯的程式執行的工作。 這些字元不指定要執行的作業。  
  
## <a name="parentheses"></a>括號  
 當您定義這類程序中，使用括號`Sub`或`Function`。 您必須將所有的程序引數清單括在括號中。 您也使用括號將變數或引數放入邏輯群組，特別是若要覆寫中的複雜運算式的運算子優先順序的預設順序。 下列範例將說明這點。  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 執行先前的程式碼的值之後`d`8.225 和的值是`e`為 3。 計算`d`使用的預設優先順序`/`over `+` ，相當於`d = b + (c / a)`。 在計算中的括號`e`覆寫預設的優先順序。  
  
## <a name="separators"></a>分隔符號  
 分隔符號執行功能如其名稱示： 在不同的程式碼區段。 在 Visual Basic 中的分隔字元是冒號 (`:`)。 當您想要包含在單一行，而不是個別行上的多個陳述式時，請使用分隔符號字元。 這樣可節省空間，並改善您的程式碼的可讀性。 下列範例示範三個陳述式以冒號分隔。  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 如需詳細資訊，請參閱[＜How to：中斷和合併程式碼中的陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。  
  
 冒號 (`:`) 字元也用來識別陳述式標籤。 如需詳細資訊，請參閱[＜How to：標記陳述式](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)。  
  
## <a name="concatenation"></a>串連  
 使用`&`運算子*串連*，或將字串連結在一起。 請勿混淆與`+`運算子，就會將數值相加。 如果您使用`+`運算子進行串連時您操作數字的值，您可以取得不正確的結果。 下列範例為其示範。  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 執行先前的程式碼的值之後`resultA`21.01 和的值是`resultB`是 「 10.0111"。  
  
## <a name="member-access-operators"></a>成員存取運算子  
 若要存取之型別的成員，您可以使用點 (`.`) 或驚嘆號 (`!`) 之間的型別名稱和成員名稱的運算子。  
  
### <a name="dot--operator"></a>點 （.）運算子  
 使用`.`操作員的類別、 結構、 介面或列舉型別做為成員存取運算子。 成員可以是欄位、 屬性、 事件或方法。 下列範例將說明這點。  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a>驚嘆號 （！）運算子  
 使用`!`運算子只能在類別或介面上的做為字典存取運算子。 類別或介面都必須具有預設屬性可接受單一`String`引數。 緊接`!`運算子會變成引數值傳遞給預設屬性，做為字串。 下列範例為其示範。  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 這三個輸出行`MsgBox`所有顯示值`32856`。 第一行會使用傳統的存取權給屬性`index`，第二個會利用這一點，`index`類別的預設屬性`hasDefault`，和第三個會使用字典存取此類別。  
  
 請注意，第二個運算元`!`運算子必須是有效的 Visual Basic 識別項，並未用雙引號括住 (`" "`)。 換句話說，您無法使用的字串常值或字串變數。 下列的最後一個變更的這一行`MsgBox`呼叫會產生錯誤，因為`"X"`是括住的字串常值。  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  您必須明確預設集合的參考。 特別是，您無法使用`!`晚期繫結變數上的運算子。  
  
 `!`字元也做為`Single`輸入字元。  
  
## <a name="see-also"></a>另請參閱
- [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [類型字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
