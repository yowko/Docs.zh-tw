---
title: Like 運算子
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
ms.openlocfilehash: 4279d90c74c80403146448a8ba5a6051ec9d12f6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401549"
---
# <a name="like-operator-visual-basic"></a>Like 運算子 (Visual Basic)
比較字串與模式。  

> [!IMPORTANT]
> `Like`.Net Core 和 .NET Standard 專案目前不支援運算子。

## <a name="syntax"></a>語法  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要。 任何 `Boolean` 變數。 結果為 `Boolean` 值，指出是否 `string` 滿足 `pattern` 。  
  
 `string`  
 必要。 任何 `String` 運算式。  
  
 `pattern`  
 必要。 `String`符合「備註」中所述之模式比對慣例的任何運算式。  
  
## <a name="remarks"></a>備註  
 如果中的值 `string` 符合中包含的模式 `pattern` ， `result` 則為 `True` 。 如果字串不符合模式， `result` 會是 `False` 。 如果 `string` 和 `pattern` 都是空字串，則結果為 `True` 。  
  
## <a name="comparison-method"></a>比較方法  
 運算子的行為 `Like` 視[Option Compare 語句](../statements/option-compare-statement.md)而定。 每個原始程式檔的預設字串比較方法為 `Option Compare Binary` 。  
  
## <a name="pattern-options"></a>模式選項  
 內建的模式比對提供了用於字串比較的多用途工具。 模式比對功能可讓您比對中的每個字元與 `string` 特定字元、萬用字元、字元清單或字元範圍。 下表顯示中允許的字元 `pattern` 和相符的內容。  
  
|中的字元`pattern`|符合`string`|  
|-----------------------------|-------------------------|  
|`?`|任何單一字元|  
|`*`|零或多個字元|  
|`#`|任何單一數位（0–9）|  
|`[charlist]`|中的任何單一字元`charlist`|  
|`[!charlist]`|不在中的任何單一字元`charlist`|  
  
## <a name="character-lists"></a>字元清單  
 以方括弧（）括住的一或多個字元（ `charlist` ）群組 `[ ]` 可以用來比對中的任何單一字元 `string` ，而且幾乎可以包含任何字元碼，包括數位。  
  
 開頭的驚嘆號（ `!` ） `charlist` 表示如果在中找到除了中的字元以外的任何字元，則會進行比對 `charlist` `string` 。 當使用於方括弧外時，驚嘆號會符合其本身。  
  
## <a name="special-characters"></a>特殊字元  
 若要比對特殊字元左括弧（ `[` ）、問號（ `?` ）、數位記號（ `#` ）和星號（ `*` ），請以方括弧括住。 右括弧（ `]` ）無法在群組內用來比對本身，但它可以在群組外當做個別字元使用。  
  
 字元序列 `[]` 會被視為長度為零的字串（ `""` ）。 不過，它不能是以方括弧括住的字元清單的一部分。 如果您想要檢查中的位置是否 `string` 包含一組字元或完全沒有字元，您可以使用 `Like` 兩次。 如需範例，請參閱[如何：比對字串與模式](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)。  
  
## <a name="character-ranges"></a>字元範圍  
 藉由使用連字號（ `–` ）分隔範圍的下限和上限， `charlist` 可以指定字元範圍。 例如， `[A–Z]` 如果中對應的字元位置 `string` 包含範圍內的任何字元，則會產生比 `A` 對 `Z` ， `[!H–L]` 如果對應的字元位置包含範圍以外的任何字元，則會產生相符的結果 `H` `L` 。  
  
 當您指定某個範圍的字元時，它們必須以遞增的排序次序顯示，也就是從最低到最高。 因此， `[A–Z]` 是有效的模式，但不是 `[Z–A]` 。  
  
### <a name="multiple-character-ranges"></a>多個字元範圍  
 若要為相同的字元位置指定多個範圍，請將它們放在不含分隔符號的同一個方括弧內。 例如， `[A–CX–Z]` 如果中的對應字元位置 `string` 包含範圍 `A` – `C` 或範圍–中的任何字元，則會產生相符的 `X` 結果 `Z` 。  
  
### <a name="usage-of-the-hyphen"></a>連字號的使用方式  
 連字號（ `–` ）可以出現在開頭（在驚嘆號後面，如果有的話）或結尾處， `charlist` 以符合本身。 在任何其他位置中，連字號會識別以連字號任一端的字元分隔的字元範圍。  
  
## <a name="collating-sequence"></a>排序次序  
 指定範圍的意義取決於執行時間的字元順序（由決定），以及程式 `Option Compare` 代碼執行所在之系統的地區設定。 若為 `Option Compare Binary` ，則範圍會 `[A–E]` 符合 `A` 、 `B` 、 `C` 、 `D` 和 `E` 。 使用 `Option Compare Text` 、 `[A–E]` 符合 `A` 、 `a` 、、 `À` `à` 、 `B` 、 `b` `C` `c` `D` `d` `E` 、、、、、和 `e` 。 此範圍不相符， `Ê` 或 `ê` 因為在排序次序中的非重音字元之後，強調字元會自動分頁。  
  
## <a name="digraph-characters"></a>連字號  
 在某些語言中，有字母字元代表兩個不同的字元。 例如，數種語言會使用字元 `æ` 來表示字元 `a` ，以及 `e` 兩者一起出現的時間。 `Like`運算子會辨識單一的同位字元和兩個個別的字元相等。  
  
 在系統地區設定設定中指定使用連字號字元的語言時，或中出現的單一連字號，會 `pattern` `string` 符合另一個字串中相等的兩個字元序列。 同樣地，以 `pattern` 方括弧括住的連字號（單獨、清單或範圍中的），會比對中的相等兩個字元序列 `string` 。  
  
## <a name="overloading"></a>多載化  
 `Like`運算子可以多載*overloaded*，這表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用 `Like` 運算子來比較字串與各種不同的模式。 結果會進入一個 `Boolean` 變數，指出每個字串是否符合模式。  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [比較運算子](comparison-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Option Compare 陳述式](../statements/option-compare-statement.md)
- [運算子和運算式](../../programming-guide/language-features/operators-and-expressions/index.md)
- [如何：比對字串和模式](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
