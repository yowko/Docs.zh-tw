---
title: "&gt;&gt; Operator (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.>>"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operator>>"
  - ">> operator [Visual Basic]"
  - "bit shift operators"
  - "operator >>"
  - "right shift operators"
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &gt;&gt; Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

執行位元模式的算術右移位。  
  
## 語法  
  
```  
  
result = pattern >> amount  
```  
  
## 組件  
 `result`  
 必要項。  整數值。  位元模式移位的結果。  資料型別與 `pattern` 的型別相同。  
  
 `pattern`  
 必要項。  整數值運算式。  要移位的位元模式。  資料型別必須是整數類資料型別 \(Integral Type\) \(`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` 或 `ULong`\)。  
  
 `amount`  
 必要項。  數值運算式。  位元模式移位的位元數。  資料型別必須是 `Integer` 或擴展至 `Integer`。  
  
## 備註  
 算術移位不是循環型，這表示位元從結果某端移出後，就不會再從另一端進入。  在算術右移位中，移位超過最右邊的位元位置的位元會予以捨棄，並且最左邊有正負號的位元會傳至左邊空出的位元位置。  這表示若 `pattern` 有負數值，則空出的位置會設成一，否則會設成零。  
  
 請注意，資料型別 `Byte`、`UShort`、`UInteger` 和 `ULong` 不帶正負號，所以不會傳送正負號位元。  若 `pattern` 屬於不帶正負號的型別，則空出的位置一律會設成零。  
  
 為防止位元移位超過結果能接受的程度，Visual Basic 會以符合 `pattern` 資料型別的大小遮罩 \(Mask\) 來標記 `amount` 值。  這些值的二進位 AND 是用作位移的量。  大小遮罩如下：  
  
|`pattern` 的資料型別。|大小遮罩 \(十進位\)|大小遮罩 \(十六進位\)|  
|----------------------|------------------|-------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 如果 `amount` 是零，則 `result` 的值等於 `pattern` 的值。  如果 `amount` 是負數，則會視為不帶正負號值並且會加上適當的大小遮罩。  
  
 算術移位不會產生溢位例外狀況。  
  
## 多載化  
 `>>` 運算子可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，就一定要先瞭解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例會使用 `>>` 運算子，來執行整數值的算術左移位。  結果會有與已移位運算式相同的資料型別。  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 前一個範例的結果如下：  
  
-   `result1` 是 2560 \(0000 1010 0000 0000\)。  
  
-   `result2` 是 160 \(0000 0000 1010 0000\)。  
  
-   `result3` 是 2 \(0000 0000 0000 0010\)。  
  
-   `result4` 是 640 \(0000 0010 1000 0000\)。  
  
-   `result5` 是 0 \(已向右移 15 個位置\)。  
  
 `result4` 位移量會以 18 AND 15 計算，即等於 2。  
  
 下列範例會顯示負值上的算術移位。  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 前一個範例的結果如下：  
  
-   `negresult1` 是 \-512 \(1111 1110 0000 0000\)。  
  
-   `negresult2` 是 \-1 \(會傳送正負號位元\)。  
  
## 請參閱  
 [Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [\>\>\= Operator](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)