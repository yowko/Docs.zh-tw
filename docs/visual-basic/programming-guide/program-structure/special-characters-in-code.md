---
title: "Special Characters in Code (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.)"
  - "vb.("
  - "vb.colon"
  - "vb.!"
  - "vb.."
  - "vb.:"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "special characters, in code"
  - "parentheses, using in code"
  - "colons (:)"
  - "period character in code"
  - "dot operator (.)"
  - "dictionary access operator"
  - "concatenation operators, special characters in code"
  - "concatenation operators, vs. addition operator"
  - "! operator"
  - "separators, using in code"
  - "operators [Visual Basic], dictionary access"
  - ": separator character"
  - "member access operator"
  - "addition operator"
  - "operators [Visual Basic], member access"
  - ". operator"
  - "exclamation points"
  - "separators"
  - "exclamation point operator (!)"
  - "Visual Basic code, special characters"
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Special Characters in Code (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

有時侯您必須在程式碼中使用特殊字元，也就是非英數字元的字元。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 字元集 \(Character Set\) 中的標點符號和特殊字元有許多用途，從組織程式文字到定義由編譯器 \(Compiler\) 或編譯程式執行的工作都包含在內。  這些字元不指定要執行的作業。  
  
## 括號  
 括號是在定義程序時使用，例如 `Sub` 或 `Function`。  您必須將所有程序引數清單以括號括起來。  也可以使用括號將變數或引數置於邏輯群組中，這在需要覆寫複雜運算式中的運算子優先順序 \(Operator Precedence\) 時尤其有用。  下列範例將說明這點。  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 執行上述程式碼之後，`d` 的值會是 8.225，而 `e` 的值會是 3。  `d` 的計算會使用 `/` 優先於 `+` 的預設優先順序，因此等於 `d = b + (c / a)`。  `e` 計算式中的括號會覆寫預設優先順序。  
  
## 分隔符號  
 分隔符號的功用正如其名稱所示；亦即分隔程式碼的區段。  在 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中，冒號 \(`:`\) 是分隔符號字元。  當您想要將數個陳述式包含在單行而非數行中時，請使用分隔符號字元。  這不但能節省空間，也會增加程式碼的可讀性。  下列範例會顯示三個以冒號分隔的陳述式。  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 如需詳細資訊，請參閱 [如何：在程式碼中中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。  
  
 冒號 \(`:`\) 字元也可以用來識別陳述式標籤。  如需詳細資訊，請參閱 [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)。  
  
## 串連  
 使用 `&` 運算子可進行「*串連*」\(Concatenation\)，或是將字串連結在一起。  請勿將此運算子與 `+` 運算子混淆，後者是用於將數值相加。  對數值進行運算時，使用 `+` 運算子進行串連可能會導致錯誤的結果。  以下範例就是示範這項作業。  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 執行上述程式碼之後，`resultA` 的值會是 21.01，而 `resultB` 的值會是 "10.0111"。  
  
## 成員存取運算子  
 若要存取某個型別的成員，您可以在型別名稱和成員名稱之間使用點 \(`.`\) 或驚嘆號 \(`!`\) 運算子。  
  
### 點 \(.\) 運算子  
 對類別、結構、介面或列舉型別 \(Enumeration\) 而言，`.` 運算子可做為成員存取運算子使用。  成員可以是欄位、屬性、事件或方法。  下列範例將說明這點。  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### 驚嘆號 \(\!\) 運算子  
 對類別或介面而言，`!` 運算子只能做為字典存取運算子使用。  類別或介面必須有接受單一 `String` 引數的預設屬性。  緊接在 `!` 運算子後面的識別項會變成引數值，以字串形式傳遞至預設屬性。  以下範例就是示範這項作業。  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 `MsgBox` 的三個輸出行全都會顯示值 `32856`。  第一行使用存取 `index` 屬性這一個傳統方法，第二行利用 `index` 是 `hasDefault` 類別這一點，而第三行則使用字典存取類別。  
  
 請注意，`!` 運算子的第二個運算元必須是未加上雙引號 \(`" "`\) 的有效 Visual Basic 識別項。  換句話說，您不能使用字串常值 \(String Literal\) 或字串變數。  對 `MsgBox` 呼叫的最後一行進行下列變更將會產生錯誤，原因在於 `"X"` 是用引號括住的字串常值。  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  對預設集合的參考必須是明確的。  事實上，您無法在晚期繫結 \(Late Bound\) 變數上使用 `!` 運算子。  
  
 `!` 字元也可做為 `Single` 型別字元使用。  
  
## 請參閱  
 [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)