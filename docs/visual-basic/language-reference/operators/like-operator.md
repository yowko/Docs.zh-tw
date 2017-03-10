---
title: "Like Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "Like"
  - "vb.Like"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "similar to"
  - "pattern matching"
  - "Like operator [Visual Basic]"
  - "? symbol, wildcard character"
  - "string comparison [Visual Basic], Like operator"
  - "strings [Visual Basic], comparing"
  - "comparison operators"
  - "symbols, wildcard"
  - "wildcards, Like operator"
  - "strings [Visual Basic], matching"
  - "string comparison [Visual Basic], sorting data"
  - "data [Visual Basic], sorting"
  - "text [Visual Basic], comparing"
  - "operators [Visual Basic], pattern-matching"
  - "data [Visual Basic], string comparisons"
  - "string comparison [Visual Basic], Like operators"
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Like Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

根據模式比較字串。  
  
## 語法  
  
```  
  
result = string Like pattern  
```  
  
## 組件  
 `result`  
 必要項。  任何 `Boolean` 變數。  結果是表示 `string` 是否符合 `pattern` 的 `Boolean` 值。  
  
 `string`  
 必要項。  任何 `String` 運算式。  
  
 `pattern`  
 必要項。  符合「備註」中所說明之模式對應轉換的任何 `String` 運算式。  
  
## 備註  
 如果 `string` 的值符合 `pattern` 所包含的模式，則 `result` 為 `True`。  若字串不符合模式，則 `result` 為 `False`。  如果 `string` 和 `pattern` 都是空字串，則 result 為 `True`。  
  
## 比較方法  
 `Like` 運算子的行為會根據 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)而定。  每個原始程式檔 \(Source File\) 的預設字串比較方法是 `Option Compare Binary`。  
  
## 模式選項  
 內建模式對應提供字串比較的多功能工具。  模式比對功能可讓您根據特定字元、萬用字元、字元清單或字元範圍，來比對 `string` 中的每一個字元。  下表列出了 `pattern` 中所允許的字元及其對應字元。  
  
|`pattern` 中的字元|`string` 中的對應字元|  
|--------------------|---------------------|  
|`?`|任何單一個字元|  
|`*`|零或多個字元|  
|`#`|任何單一個數字 \(0–9\)|  
|`[` `charlist` `]`|`charlist` 中的任何單一字元|  
|`[!` `charlist` `]`|不在 `charlist` 中的任何單一字元|  
  
## 字元清單  
 可使用方括弧 \(`[ ]`\) 括起來之一或多個字元的群組 \(`charlist`\)，來對應 `string` 中的任何單一字元，幾乎可包括任何字元碼，包含數字在內。  
  
 `charlist` 開頭之驚歎號 \(`!`\) 的含意為，如果在 `string` 中找到 `charlist` 中所列的任何字元，則表示符合。  當使用外方括弧時，則驚歎號會對應其本身。  
  
## 特殊字元  
 若要比對左括號 \(`[`\)、問號 \(`?`\)、數字符號 \(`#`\) 及星號 \(`*`\) 等特殊字元，必須使用括號將其括起來。  右括號 \(`]`\) 不能用於群組內來比對本身，但可在群組之外當做個別字元使用。  
  
 字元序列 `[]` 會視為零長度字串 \(`""`\)。  然而，它不能是以括號括住之字元清單的一部分。  若要檢查 `string` 中的位置是否包含其中一個字元群組，或完全沒有字元，則可使用 `Like` 兩次。  如需範例，請參閱 [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)。  
  
## 字元範圍  
 藉由使用連字號 \(`–`\) 來分隔範圍的下限及上限，`charlist` 即可指定字元範圍。  例如，如果 `string` 中的對應字元位置包含範圍 `A`–`Z` 內的任何字元，則 `[A–Z]` 的結果即為符合。如果對應的字元位置包含範圍 `H`–`L` 外部的任何字元，則 `[!H–L]` 的結果即為符合。  
  
 當您指定字元範圍時，字元一定是以遞增排序次序出現 \(亦即，從最小至最大\)。  因此 `[A–Z]` 是有效模式，但 `[Z–A]` 則不是。  
  
### 多重字元範圍  
 若要為相同的字元位置指定多重範圍，請將其放在相同的括號中，且不要有分隔符號 \(Delimiter\)。  例如，如果 `string` 中的對應字元位置包含範圍 `A`–`C` 或範圍 `X`–`Z` 內部的任何字元，則 `[A–CX–Z]` 的結果即為符合。  
  
### 連字號的使用方式  
 `charlist` 的起點 \(若有連字號，則會在驚歎號之後\) 或尾端都可出現連字號 \(`–`\)，以對應其本身。  在任何其他位置中，連字號識別由位於連字號任一邊上的字元所界定的字元範圍。  
  
## 核對順序  
 指定範圍的含意取決於執行階段的字元順序 \(按照 `Option` `Compare` 及正在執行程式碼之系統地區設定所做的決定\)。  利用 `Option` `Compare` `Binary`，範圍 `[A–E]` 會符合 `A`、`B`、`C`、`D` 和 `E`。  利用 `Option` `Compare` `Text`，`[A–E]` 會符合 `A`、`a`、`À`、`à`、`B`、`b`,、`C`、`c`、`D`、`d`、`E` 及 `e`。  因為重音符號會依照排序次序，定序於非重音符號的後面，所以範圍不會符合 `Ê` 或 `ê`。  
  
## 雙併詞字元  
 在某些語言中，有一些字母字元代表兩個分開的字元。  例如，有幾種語言會在 `a` 和 `e` 兩個字元一起出現時使用 `æ` 來表示這兩者。  `Like` 運算子會辨識單一雙併詞字元，且這兩個個別字元會相等。  
  
 在系統地區設定使用雙併詞字元的語言時，`pattern` 或 `string` 中所出現的單一雙併詞字元會符合其他字串中同等的兩個字串序列。  同樣地，用方括弧 \(藉由方括弧本身、在清單中或在範圍中\) 括起來之 `pattern` 中的雙併詞字元會符合 `string` 中同等的兩個字串序列。  
  
## 多載化  
 `Like` 運算子可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，就一定要先瞭解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 這個範例會使用 `Like` 運算子，來比較字串與不同的模式。  結果是 `Boolean` 變數，指出每一個字串是否會符合模式。  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/like-operator_1.vb)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>   
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>   
 [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)