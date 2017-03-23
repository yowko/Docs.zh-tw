---
title: "程式碼 (Visual Basic) 中的特殊字元 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
dev_langs:
- VB
helpviewer_keywords:
- special characters, in code
- parentheses, using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator
- concatenation operators, special characters in code
- concatenation operators, vs. addition operator
- '! operator'
- separators, using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator
- addition operator
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
caps.latest.revision: 21
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
ms.openlocfilehash: 6d4b6e74ef3dfab3a7174da07cff7100fa4b2a2f
ms.lasthandoff: 03/13/2017

---
# <a name="special-characters-in-code-visual-basic"></a>程式碼中的特殊字元 (Visual Basic)
有時候，您必須使用特殊字元，在您的程式碼，也就是不是字母或數字的字元。 標點符號和特殊字元[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]字元集有許多用途，從組織程式文字到定義由編譯器或編譯的程式執行的工作。 這些字元不指定要執行的作業。  
  
## <a name="parentheses"></a>括號  
 當您定義程序，例如使用括號`Sub`或`Function`。 您必須將所有的程序引數清單括在括號中。 您也使用括號將變數或引數放入邏輯群組，特別是用來覆寫中的複雜運算式的運算子優先順序的預設順序。 下列範例將說明這點。  
  
 [!code-vb[VbVbcnConventions #&11;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 執行先前的程式碼的值之後`d`8.225 和的值是`e`為 3。 其計算方式`d`會使用預設的優先順序的`/`透過`+`，相當於`d = b + (c / a)`。 在計算中的括號`e`覆寫預設的優先順序。  
  
## <a name="separators"></a>分隔符號  
 分隔符號進行什麼正如其名︰ 它們個別的程式碼區段。 在[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，分隔字元是冒號 (`:`)。 當您想要包含在單一行，而不是不同的行的多個陳述式時，請使用分隔符號字元。 這可節省空間，並改善程式碼的可讀性。 下列範例是以冒號分隔的三個陳述式。  
  
 [!code-vb[VbVbcnConventions #&12;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 如需詳細資訊，請參閱[How to︰ 中斷和合併程式碼中的陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。  
  
 冒號 (`:`) 字元也用來識別陳述式標籤。 如需詳細資訊，請參閱[How to︰ 標籤陳述式](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)。  
  
## <a name="concatenation"></a>串連  
 使用`&`運算子*串連*，或將字串連結在一起。 請勿混淆與`+`運算子，就會將數值相加。 如果您使用`+`運算子來串連時您操作的數字的值，您可以取得不正確的結果。 下列範例為其示範。  
  
 [!code-vb[VbVbcnConventions #&13;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 執行先前的程式碼的值之後`resultA`21.01 和的值是`resultB`是 「 10.0111 」。  
  
## <a name="member-access-operators"></a>成員存取運算子  
 若要存取型別的成員，您可使用點 (`.`) 或驚嘆號 (`!`) 之間的型別名稱和成員名稱的運算子。  
  
### <a name="dot--operator"></a>點 （.）運算子  
 使用`.`操作員的類別、 結構、 介面或列舉型別做為成員存取運算子。 成員可以是欄位、 屬性、 事件或方法。 下列範例將說明這點。  
  
 [!code-vb[VbVbcnConventions #&14;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a>驚嘆號 （！）運算子  
 使用`!`運算子只能在類別或介面上的做為字典存取運算子。 類別或介面必須有預設屬性，可以接受單一`String`引數。 緊接`!`運算子會變成引數值傳遞給字串的預設屬性。 下列範例為其示範。  
  
 [!code-vb[VbVbcnConventions #&15;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 三個輸出行`MsgBox`所有顯示的值`32856`。 第一行使用傳統的存取權給屬性`index`，第二個使用的事實，`index`是類別的預設屬性`hasDefault`，和第三個使用字典存取此類別。  
  
 請注意，第二個運算元`!`運算子必須是有效的 Visual Basic 識別碼，並未用雙引號括住 (`" "`)。 換句話說，您無法使用字串常值或字串變數。 下列的最後一個變更的行`MsgBox`呼叫會產生錯誤，因為`"X"`是括住的字串常值。  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  您必須明確預設集合的參考。 特別是，您不能使用`!`操作員的晚期繫結變數。  
  
 `!`字元也做`Single`輸入字元。  
  
## <a name="see-also"></a>另請參閱  
 [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [類型字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
