---
title: "#If...Then...#Else Directives | Microsoft Docs"
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
  - "vb.#EndIf"
  - "#End If"
  - "#Then"
  - "#ElseIf"
  - "vb.#ElseIf"
  - "vb.#Else"
  - "vb.#If"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, compiling"
  - "#If directive [Visual Basic]"
  - "conditional compilation, directives"
  - "#End if directive [Visual Basic]"
  - "selective compiling"
  - "else directive (#else)"
  - "#Else directive [Visual Basic]"
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# #If...Then...#Else Directives
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

有條件地編譯選取的 Visual Basic 程式碼區塊。  
  
## 語法  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## 組件  
 `expression`  
 `#If` 和 `#ElseIf` 陳述式 \(Statement\) 的必要項，在其他情形中則是選擇項。  任一個只由一個或幾個條件式編譯器 \(Compiler\) 常數、常值 \(Literal\) 及運算子所組成，評估為 `True` 或 `False` 的運算式。  
  
 `statements`  
 `#If` 陳述式區塊的必要項，在其他情形中則是選擇項。  在關聯的運算式判定為 `True` 時加以編譯的 Visual Basic 程式行或編譯器指示詞。  
  
 `#End If`  
 結束 `#If` 陳述式區塊。  
  
## 備註  
 在表面上，`#If...Then...#Else` 指示詞的行為看起來和 `If...Then...Else` 陳述式 \(Statement\) 的行為相同。  不過，`#If...Then...#Else` 指示詞是評估編譯器所編譯的為何，而 `If...Then...Else` 陳述式則是評估執行階段的狀況。  
  
 條件式編譯通常是用來編譯供多平台使用的程式。  它也可以用來避免在可執行檔中出現偵錯碼。  條件式編譯時所排除的程式碼會完全被最後的可執行檔省略，因此對檔案的大小和效能並沒有影響。  
  
 不論評估的結果為何，所有的運算式都是用 `Option Compare Binary` 來評估。  `Option Compare` 陳述式不會影響 `#If` 和 `#ElseIf` 陳述式中的運算式。  
  
> [!NOTE]
>  沒有單行格式的 `#If`、`#Else`、`#ElseIf` 和 `#End If` 指示詞存在。  沒有其他程式碼可以與任何指示詞出現在同一行上。  
  
## 範例  
 這個範例使用 `#If...Then...#Else` 建構來決定是否要編譯某些陳述式。  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## 請參閱  
 [\#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)