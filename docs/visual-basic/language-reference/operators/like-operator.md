---
title: Like 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: a9c672a397510c69c9ee67358689feff80d8831a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="like-operator-visual-basic"></a>Like 運算子 (Visual Basic)
比較字串和模式。  
  
## <a name="syntax"></a>語法  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要。 任何`Boolean`變數。 結果是`Boolean`值，指出是否`string`滿足`pattern`。  
  
 `string`  
 必要。 任何 `String` 運算式。  
  
 `pattern`  
 必要。 任何`String`運算式符合的模式比對的慣例所述在 < 備註 >。  
  
## <a name="remarks"></a>備註  
 如果中的值`string`滿足模式中包含`pattern`，`result`是`True`。 如果字串不符合該模式，`result`是`False`。 如果兩個`string`和`pattern`則為空字串，結果是`True`。  
  
## <a name="comparison-method"></a>比較方法  
 行為`Like`取決於運算子[選項比較陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)。 每個來源檔案的預設字串比較方法是`Option Compare Binary`。  
  
## <a name="pattern-options"></a>模式選項  
 內建的模式比對的字串比較提供的多功能工具。 模式比對功能可讓您比對中的每個字元`string`針對特定的字元、 萬用字元、 字元清單或字元範圍。 下表顯示允許的字元`pattern`和它們的相符。  
  
|中的字元 `pattern`|中的相符項目 `string`|  
|-----------------------------|-------------------------|  
|`?`|任何單一字元|  
|`*`|零個或多個字元|  
|`#`|任何單一數字 (0 – 9)|  
|`[charlist]`|中的任何單一字元 `charlist`|  
|`[!charlist]`|不能在任何單一字元 `charlist`|  
  
## <a name="character-lists"></a>字元清單  
 一或多個字元群組 (`charlist`) 括在括號 (`[ ]`) 可用來比對中的任何單一字元`string`而且可以包含任何字元碼，包括數字。  
  
 驚嘆號 (`!`) 的開頭`charlist`表示比對中的字元以外的任何字元，如果`charlist`位於`string`。 在方括號之外使用，請將驚嘆號會比對本身。  
  
## <a name="special-characters"></a>特殊字元  
 要比對的特殊字元的左括號 (`[`)、 問號 (`?`)、 數字符號 (`#`)，和星號 (`*`)，將其括在方括號。 右括號 (`]`) 不在群組內是用來比對本身，但它可以當做位於群組外部的個別字元。  
  
 字元順序`[]`被視為零長度字串 (`""`)。 不過，它不能為以括弧括住的字元清單的一部分。 如果您想要檢查是否中的位置`string`包含一個群組的字元或在所有的字元，您可以使用`Like`兩次。 如需範例，請參閱[如何： 比對字串和模式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)。  
  
## <a name="character-ranges"></a>字元範圍  
 使用連字號 (`–`) 來分隔範圍的下限與上限`charlist`可以指定字元範圍。 例如，`[A–Z]`導致相符項目，如果對應的字元放在`string`包含範圍內的任何字元`A`–`Z`，和`[!H–L]`導致相符項目，如果對應的字元位置包含在範圍之外的任何字元`H`–`L`。  
  
 當您指定的字元範圍時，他們必須出現在遞增排序次序，也就是從最低到最高。 因此，`[A–Z]`為有效的模式，但`[Z–A]`不是。  
  
### <a name="multiple-character-ranges"></a>多個字元範圍  
 若要指定多個範圍的相同的字元位置，請將其放在相同的括號不搭配分隔符號。 例如，`[A–CX–Z]`導致相符項目，如果對應的字元放在`string`包含其中一個範圍內的任何字元`A`–`C`或範圍`X`–`Z`。  
  
### <a name="usage-of-the-hyphen"></a>連字號的使用方式  
 連字號 (`–`) 會顯示 （驚歎號之後，如果有的話） 的開頭或結尾處`charlist`來比對本身。 在任何其他位置中，連字號識別的連字號任一邊的字元所分隔的字元範圍。  
  
## <a name="collating-sequence"></a>定序順序  
 指定範圍的意義取決於在執行階段，由決定排序字元`Option``Compare`和地區設定的系統執行程式碼。 與`Option``Compare``Binary`，範圍`[A–E]`符合`A`， `B`， `C`， `D`，和`E`。 與`Option``Compare``Text`，`[A–E]`符合`A`， `a`， `À`， `à`， `B`， `b`， `C`， `c`， `D`， `d`， `E`，和`e`。 範圍不符合`Ê`或`ê`因為腔調的字元的排序順序中的無腔調字元。  
  
## <a name="digraph-characters"></a>了雙拼詞字元  
 在某些語言中，有代表兩個個別字元的字母字元。 比方說，有幾種語言都使用字元`æ`字元來表示`a`和`e`時一起出現。 `Like`運算子可辨識的單一了雙拼詞字元和兩個個別字元都是相同。  
  
 系統地區設定中指定一種語言，使用了雙拼詞字元時，出現在單一了雙拼詞字元`pattern`或`string`符合另一個字串中對等的兩個字元序列。 同樣地中的了雙拼詞字元`pattern`括在括號 （單獨使用時，在清單中，或在範圍內） 比對中相等的雙字元序列`string`。  
  
## <a name="overloading"></a>多載化  
 `Like`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用`Like`運算子來比較字串與不同的模式。 結果將會進入`Boolean`變數，表示每個字串是否符合模式。  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [如何：比對字串和模式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
