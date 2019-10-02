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
ms.openlocfilehash: 795ecc2e80d57af29ccd50c50d2dd209c6425e40
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701127"
---
# <a name="like-operator-visual-basic"></a>Like 運算子 (Visual Basic)
比較字串與模式。  

> [!IMPORTANT]
> .NET Core 和 .NET Standard 專案中目前不支援 `Like` 運算子。

## <a name="syntax"></a>語法  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 任何 @no__t 0 變數。 結果為 `Boolean` 值，指出 `string` 是否符合 `pattern`。  
  
 `string`  
 必要項。 任何 `String` 運算式。  
  
 `pattern`  
 必要項。 符合「備註」中所述之模式比對慣例的任何 `String` 運算式。  
  
## <a name="remarks"></a>備註  
 如果 `string` 中的值符合 `pattern` 中所包含的模式，`result` 會 `True`。 如果字串不符合模式，`result` 會 `False`。 如果 `string` 和 `pattern` 都是空字串，則結果會 `True`。  
  
## <a name="comparison-method"></a>比較方法  
 @No__t-0 運算子的行為視[Option Compare 語句](../../../visual-basic/language-reference/statements/option-compare-statement.md)而定。 每個原始程式檔的預設字串比較方法為 `Option Compare Binary`。  
  
## <a name="pattern-options"></a>模式選項  
 內建的模式比對提供了用於字串比較的多用途工具。 模式比對功能可讓您比對 `string` 中的每個字元與特定字元、萬用字元、字元清單或字元範圍。 下表顯示 `pattern` 中所允許的字元及其相符的字元。  
  
|@No__t 中的字元-0|符合 `string`|  
|-----------------------------|-------------------------|  
|`?`|任何單一字元|  
|`*`|零或多個字元|  
|`#`|任何單一數位（0–9）|  
|`[charlist]`|@No__t 中的任何單一字元-0|  
|`[!charlist]`|不在 @no__t 中的任何單一字元-0|  
  
## <a name="character-lists"></a>字元清單  
 以方括弧（`[ ]`）括住的一或多個字元（`charlist`）群組可以用來比對 `string` 中的任何單一字元，而且幾乎可以包含任何字元碼，包括數位。  
  
 @No__t-1 開頭的驚嘆號（`!`）表示在 `string` 中找到除了 `charlist` 字元以外的任何字元時，會進行比對。 當使用於方括弧外時，驚嘆號會符合其本身。  
  
## <a name="special-characters"></a>特殊字元  
 若要比對特殊字元（`[`）、問號（`?`）、數位記號（`#`）和星號（`*`），請以方括弧括住。 右括弧（`]`）不能用在群組內來比對本身，但是可以在群組外當做個別字元使用。  
  
 字元順序 `[]` 會被視為長度為零的字串（`""`）。 不過，它不能是以方括弧括住的字元清單的一部分。 如果您想要檢查 `string` 中的位置是否包含一組字元或完全沒有字元，您可以使用 `Like` 兩次。 如需範例，請參閱[如何：比對字串與模式 @ no__t-0。  
  
## <a name="character-ranges"></a>字元範圍  
 藉由使用連字號（`–`）分隔範圍的下限和上限，`charlist` 可以指定字元範圍。 例如，如果 `string` 中對應的字元位置包含範圍 `A` – `Z` 中的任何字元，則 `[A–Z]` 會產生相符的結果，而如果對應的字元位置包含任何超出的字元，則 `[!H–L]` 會產生比對範圍 `H` – `L`。  
  
 當您指定某個範圍的字元時，它們必須以遞增的排序次序顯示，也就是從最低到最高。 因此，`[A–Z]` 是有效的模式，但 `[Z–A]` 則不是。  
  
### <a name="multiple-character-ranges"></a>多個字元範圍  
 若要為相同的字元位置指定多個範圍，請將它們放在不含分隔符號的同一個方括弧內。 例如，如果 `string` 中對應的字元位置包含範圍 `A` – `C` 或範圍 `X` – `Z` 內的任何字元，則 `[A–CX–Z]` 會產生相符的結果。  
  
### <a name="usage-of-the-hyphen"></a>連字號的使用方式  
 連字號（`–`）可以出現在開頭（在驚嘆號後面，如果有的話），或在 `charlist` 結尾處，以符合本身。 在任何其他位置中，連字號會識別以連字號任一端的字元分隔的字元範圍。  
  
## <a name="collating-sequence"></a>排序次序  
 指定範圍的意義取決於執行時間的字元順序，由 `Option Compare` 和程式碼執行所在之系統的地區設定所決定。 使用 `Option Compare Binary` 時，`[A–E]` 的範圍會符合 `A`、`B`、`C`、`D` 和 `E`。 使用 `Option Compare Text`，`[A–E]` 會符合 `A`、`a`、`À`、`à`、`B`、`b`、`C`、`c`、0、1、2 和 3。 範圍不符合 `Ê` 或 `ê`，因為重音字元會在排序次序中的非重音字元之後自動分頁。  
  
## <a name="digraph-characters"></a>連字號  
 在某些語言中，有字母字元代表兩個不同的字元。 例如，數個語言會使用字元 `æ` 來表示兩個字元在一起出現時，`a` 和 @no__t。 @No__t-0 運算子會辨識單一的同位字元和兩個個別的字元相等。  
  
 當系統地區設定中指定了使用二個空白字元的語言時，在 `pattern` 或 `string` 中出現單一的同一個空白字元，會符合另一個字串中相等的兩個字元序列。 同樣地，以方括弧括住的 `pattern` 中的同位字元（單獨、清單或範圍內）會符合 `string` 中相等的兩個字元序列。  
  
## <a name="overloading"></a>多載化  
 @No__t-0 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用 `Like` 運算子來比較字串與各種不同的模式。 結果會進入 @no__t 0 變數，指出每個字串是否符合模式。  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [如何：比對字串與模式 @ no__t-0
