---
title: "&lt;&lt; Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.<<"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "bit shift operators"
  - "<< operator [Visual Basic]"
  - "operator <<, Visual Basic left shift operator"
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# &lt;&lt; Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

執行位元模式的算術左移位。  
  
## 語法  
  
```  
  
result = pattern << amount  
```  
  
## 組件  
 `result`  
 必要項。  整數值。  位元模式移位的結果。  資料型別與 `pattern` 的型別相同。  
  
 `pattern`  
 必要項。  整數值運算式。  要移位的位元模式。  資料型別必須是整數類資料型別 \(Integral Type\) \(`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` 或 `ULong`\)。  
  
 `amount`  
 必要項。  數值運算式。  位元模式移位的位元數。  資料型別必須是 `Integer` 或擴展至 `Integer`。  
  
## 備註  
 算術移位不是循環型，這表示位元從結果某端移出後，就不會再從另一端進入。  在算術左移位中，位元移動的範圍若超過結果資料型別會予以捨棄，而且右方空出的位元位置會設定成零。  
  
 為防止位元移位超過結果能接受的程度，Visual Basic 會以符合 `pattern` 資料型別的大小遮罩 \(Mask\) 來標記 `amount` 值。  這些值的二進位 AND 是用作位移的量。  大小遮罩如下：  
  
|`pattern` 的資料型別。|大小遮罩 \(十進位\)|大小遮罩 \(十六進位\)|  
|----------------------|------------------|-------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 如果 `amount` 是零，則 `result` 的值等於 `pattern` 的值。  如果 `amount` 是負數，則會視為不帶正負號值並且會加上適當的大小遮罩。  
  
 算術移位不會產生溢位例外狀況。  
  
> [!NOTE]
>  `<<` 運算子可以「*多載*」\(overload\)，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，請確定了解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 這個範例會使用 `<<` 運算子執行整數值的算術左移位。  結果會有與已移位運算式相同的資料型別。  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 前一個範例的結果如下：  
  
-   `result1` 是 192 \(0000 0000 1100 0000\)。  
  
-   `result2` 是 3072 \(0000 1100 0000 0000\)。  
  
-   `result3` 是 \-32768 \(1000 0000 0000 0000\)。  
  
-   `result4` 是 384 \(0000 0001 1000 0000\)。  
  
-   `result5` 是 0 \(往左移動 15 位\)。  
  
 `result4` 位移量會以 17 AND 15 計算，即等於 1。  
  
## 請參閱  
 [Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [\<\<\= Operator](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)