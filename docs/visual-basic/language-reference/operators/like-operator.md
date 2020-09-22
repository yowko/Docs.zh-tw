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
ms.openlocfilehash: 49dfe5cf5dbcf8dc6f79f569a92e36aa81806913
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866777"
---
# <a name="like-operator-visual-basic"></a>Like 運算子 (Visual Basic)

比較字串與模式。  

> [!IMPORTANT]
> `Like`.Net Core 和 .NET Standard 專案目前不支援運算子。

## <a name="syntax"></a>Syntax  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a>組件  

 `result`  
 必要。 任何 `Boolean` 變數。 結果是一個 `Boolean` 值，指出是否 `string` 符合 `pattern` 。  
  
 `string`  
 必要。 任何 `String` 運算式。  
  
 `pattern`  
 必要。 `String`符合「備註」中所述模式比對慣例的任何運算式。  
  
## <a name="remarks"></a>備註  

 如果中的值 `string` 符合所含的模式 `pattern` ， `result` 則為 `True` 。 如果字串不符合模式， `result` 則為 `False` 。 如果 `string` 和 `pattern` 都是空字串，則結果為 `True` 。  
  
## <a name="comparison-method"></a>比較方法  

 運算子的行為 `Like` 取決於 [Option Compare 語句](../statements/option-compare-statement.md)。 每個原始程式檔的預設字串比較方法是 `Option Compare Binary` 。  
  
## <a name="pattern-options"></a>模式選項  

 內建模式比對提供了一種用於字串比較的多功能工具。 模式比對功能可讓您將中的每個字元與 `string` 特定字元、萬用字元、字元清單或字元範圍進行比對。 下表顯示中允許的字元 `pattern` 以及它們相符的字元。  
  
|中的字元 `pattern`|相符專案 `string`|  
|-----------------------------|-------------------------|  
|`?`|任何單一字元|  
|`*`|零或多個字元|  
|`#`|任何單一數位 (0 – 9) |  
|`[charlist]`|中的任何單一字元 `charlist`|  
|`[!charlist]`|任何不在中的單一字元 `charlist`|  
  
## <a name="character-lists"></a>字元清單  

 以括弧括住的一或多個字元的群組 (`charlist`)  (`[ ]`) 可以用來比對中的任何單一字元 `string` ，而且可以包含幾乎任何字元碼，包括數位。  
  
 開頭 () 驚嘆號 `!` `charlist` 表示如果在中找到字元以外的任何字元，則會進行相符 `charlist` `string` 。 使用於括弧之外時，驚嘆號會與本身相符。  
  
## <a name="special-characters"></a>特殊字元  

 若要比對左邊的特殊字元 (`[`) 、問號 (`?`) 、數位記號 (`#`) ，以及星號 () ， `*` 請以括弧括住。 右括弧 (`]`) 不能用在群組內以符合其本身，但是可以在群組外部使用做為個別字元。  
  
 字元序列 `[]` 會被視為零長度的字串， (`""`) 。 但是，它不能是以括弧括住的字元清單的一部分。 如果您想要檢查中的位置是否 `string` 包含一組字元或完全沒有字元，您可以使用 `Like` 兩次。 如需範例，請參閱 [如何：](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)比對字串與模式。  
  
## <a name="character-ranges"></a>字元範圍  

 藉由使用連字號 (`–`) 來分隔範圍的下限和上限， `charlist` 可以指定字元範圍。 例如， `[A–Z]` 如果中對應的字元位置 `string` 包含範圍內的任何字元，則會比對 `A` `Z` ， `[!H–L]` 如果對應的字元位置包含範圍之外的任何字元，則會產生相符 `H` `L` 的結果。  
  
 當您指定字元範圍時，它們必須以遞增的排序次序顯示，也就是從最低到最高。 因此， `[A–Z]` 是有效的模式，但卻 `[Z–A]` 不是。  
  
### <a name="multiple-character-ranges"></a>多個字元範圍  

 若要為相同的字元位置指定多個範圍，請將它們放在不含分隔符號的相同括弧內。 例如， `[A–CX–Z]` 如果中對應的字元位置 `string` 包含範圍內的任何字元，則會產生相符範圍 `A` – `C` 或範圍 `X` – `Z` 。  
  
### <a name="usage-of-the-hyphen"></a>使用連字號  

 連字號 (`–`) 可以出現在驚嘆號的開頭 (（如果有任何) 或在結尾）， `charlist` 以符合其本身。 在任何其他位置中，連字號會識別字元範圍，並以連字號兩側的字元分隔。  
  
## <a name="collating-sequence"></a>排序次序  

 指定範圍的意義取決於執行時間的字元順序（取決於執行時間的字元排序）， `Option Compare` 以及執行程式碼的系統地區設定。 若為 `Option Compare Binary` ，則範圍會 `[A–E]` 符合、、、 `A` `B` `C` `D` 和 `E` 。 若使用，則符合、、、、、、、、、、 `Option Compare Text` `[A–E]` `A` `a` `À` `à` `B` `b` `C` `c` `D` `d` `E` 和 `e` 。 範圍不相符， `Ê` 或是 `ê` 因為重音字元在排序次序中以非重音字元排序。  
  
## <a name="digraph-characters"></a>連字號字元  

 在某些語言中，有字母字元代表兩個不同的字元。 例如，有數種語言會使用字元 `æ` 來代表字元 `a` ，以及 `e` 它們一起出現的時間。 運算子辨識出 `Like` 單一的單合符號字元和兩個個別字符相等。  
  
 當系統地區設定中指定了使用多重組合語言字元的語言時，在或中出現的單一多重組合語言字元會 `pattern` 比 `string` 對另一個字串中相等的兩個字元序列。 同樣地，以方括弧括住的多個連字號字元 `pattern` (本身、清單或範圍中) 符合中的相等雙字元序列 `string` 。  
  
## <a name="overloading"></a>多載化  

 可以多載 `Like` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 這個範例會使用 `Like` 運算子來比較字串與不同的模式。 結果會進入 `Boolean` 變數，指出每個字串是否符合模式。  
  
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
