---
title: "#Const Directive | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.#Const"
  - "#vb.Const"
  - "#Const"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "#Const directive"
  - "conditional compilation, directives"
  - "Const directive (#Const)"
  - "Visual Basic compiler, compiler directives"
  - "constants, Const directive"
  - "constants, declaring"
  - "Const statement [Visual Basic], directive (#Const)"
  - "declaring constants, #const directive"
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# #Const Directive
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

定義 Visual Basic 的條件式編譯器常數。  
  
## 語法  
  
```  
#Const constname = expression  
```  
  
## 組件  
 `constname`  
 必要項。  所定義的常數名稱。  
  
 `expression`  
 必要項。  常值 \(Literal\)、其他條件式編譯器常數，或是除了 `Is` 以外任一或所有算術或邏輯運算子 \(Logical Operator\) 的組合。  
  
## 備註  
 條件式編譯器常數在它們出現的檔案中都是私用的 \(Private\)。  您無法使用 `#Const` 指示詞建立公用 \(Public\) 編譯器常數，而只能在使用者介面中或利用 `/define` 編譯器選項加以建立。  
  
 您在 `expression` 中只能使用條件式編譯器常數與常值。  使用以 `Const` 定義的標準常數會造成錯誤。  相反地，您只能在條件式編譯中使用以 `#Const` 關鍵字定義的常數。  常數也可不加以定義，在此情形中其值為 `Nothing`。  
  
## 範例  
 這個範例會使用 `#Const` 指示詞。  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## 請參閱  
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)   
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)