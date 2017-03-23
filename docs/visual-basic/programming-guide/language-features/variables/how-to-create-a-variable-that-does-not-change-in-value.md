---
title: "How to: Create a Variable that Does Not Change in Value (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], read-only"
  - "variables [Visual Basic], constant value"
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Create a Variable that Does Not Change in Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

讓變數的值不變更，這個概念似乎有點奇怪。  不過，在某些情況中是無法使用常數的，此時使用具有固定值的變數便很有幫助。  在這類情況中，您可以使用 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) 關鍵字來定義成員變數 \(Member Variable\)。  
  
 在下列情況中，您無法使用 [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) 來宣告和指派常數值：  
  
-   `Const` 陳述式不接受您要使用的資料型別  
  
-   您無法在編譯時期確認應該使用哪一個值  
  
-   您無法在編譯時期計算常數值  
  
### 建立不變更值的變數  
  
1.  在模組層級使用 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 來宣告成員變數 \(Member Variable\)，並且包含 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) 關鍵字。  
  
    ```  
  
    Dim ReadOnly timeStarted  
    ```  
  
     您只能在成員變數上指定 `ReadOnly`。  這表示您必須在模組層級 \(不在任何程序內\) 定義變數。  
  
2.  如果您可以在編譯時期使用單一陳述式計算值，請在 `Dim` 陳述式中使用初始設定子句。  請在 [As](../../../../visual-basic/language-reference/statements/as-clause.md) 子句之後加上等號 \(`=`\)，等號之後再接著運算式。  請確定編譯器 \(Compiler\) 可以將這個運算式評估為常數值。  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     您只能指派一次 `ReadOnly` 變數的值。  一旦這樣做，就再也沒有程式碼可以變更這個值。  
  
     如果您在編譯時期無法確認應該使用哪一個值，或是無法在編譯時期使用單一陳述式來計算這個值，則仍可以在執行階段的建構函式 \(Constructor\) 中指派這個值。  若要這樣做，您必須在類別或結構層級宣告 `ReadOnly` 變數。  接著在該類別或結構的建構函式中，計算變數的固定值、將這個值指派給變數，然後再從建構函式傳回。  
  
## 請參閱  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)