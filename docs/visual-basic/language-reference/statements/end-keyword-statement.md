---
title: "End &lt;keyword&gt; Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.EndDefinition"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "End keyword"
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# End &lt;keyword&gt; Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

後面接著其他關鍵字時，會結束該關鍵字所引入的陳述式 \(Statement\) 區塊定義。  
  
## 語法  
  
```  
End AddHandler  
End Class   
End Enum   
End Event   
End Function   
End Get   
End If   
End Interface   
End Module   
End Namespace   
End Operator   
End Property   
End RaiseEvent  
End RemoveHandler  
End Select   
End Set   
End Structure   
End Sub   
End SyncLock   
End Try   
End While   
End With  
```  
  
## 組件  
 `End`  
 必要項。  結束程式設計項目的定義。  
  
 `AddHandler`  
 必要項。結束由自訂 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)中相符 `AddHandler` 陳述式所開始的 `AddHandler` 存取子 \(Accessor\)。  
  
 `Class`  
 必要項。結束由相符 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) 所開始的類別 \(Class\) 定義。  
  
 `Enum`  
 必要項。結束由相符 [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) 所開始的列舉型別 \(Enumeration\) 定義。  
  
 `Event`  
 必要項。結束由相符 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)所開始的 `Custom` 事件定義。  
  
 `Function`  
 結束由比對 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) 開始之 `Function` 程序定義所需的必要項。  如果執行遇到 `End` `Function` 陳述式，則控制權會回到呼叫程式碼。  
  
 `Get`  
 結束由比對 [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)開始之 `Property` 程序定義所需的必要項。  如果執行遇到 `End` `Get` 陳述式，則控制權會回到要求該屬性值的陳述式。  
  
 `If`  
 必要項。結束由相符 `If` 陳述式所開始的 `If`...`Then`...`Else` 區塊定義。  請參閱 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)。  
  
 `Interface`  
 必要項。結束由相符 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) 所開始的介面定義。  
  
 `Module`  
 必要項。結束由相符 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)所開始的模組定義。  
  
 `Namespace`  
 必要項。結束由相符 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)所開始的命名空間 \(Namespace\) 定義。  
  
 `Operator`  
 必要項。結束由相符 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)所開始的運算子定義。  
  
 `Property`  
 必要項。結束由相符 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)所開始的屬性定義。  
  
 `RaiseEvent`  
 必要項。結束由自訂 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)中相符 `RaiseEvent` 陳述式所開始的 `RaiseEvent` 存取子。  
  
 `RemoveHandler`  
 必要項。結束由自訂 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)中相符 `RemoveHandler` 陳述式所開始的 `RemoveHandler` 存取子。  
  
 `Select`  
 必要項。結束由相符 `Select` 陳述式所開始的 `Select`...`Case` 區塊定義。  請參閱 [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md)。  
  
 `Set`  
 結束由比對 [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) 開始之 `Property` 程序定義所需的必要項。  如果執行遇到 `End` `Set` 陳述式，則控制權會回到設定該屬性值的陳述式。  
  
 `Structure`  
 必要項。結束由相符 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)所開始的結構定義。  
  
 `Sub`  
 結束由比對 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) 開始之 `Sub` 程序定義所需的必要項。  如果執行遇到 `End` `Sub` 陳述式，則控制權會回到呼叫程式碼。  
  
 `SyncLock`  
 必要項。結束由相符 `SyncLock` 陳述式所開始的 `SyncLock` 區塊定義。  請參閱 [SyncLock Statement](../../../visual-basic/language-reference/statements/synclock-statement.md)。  
  
 `Try`  
 必要項。結束由相符 `Try` 陳述式所開始的 `Try`...`Catch`...`Finally` 區塊定義。  請參閱 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
 `While`  
 必要項。結束由相符 `While` 陳述式所開始的 `While` 迴圈 \(Loop\) 定義。  請參閱 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)。  
  
 `With`  
 必要項。結束由相符 `With` 陳述式所開始的 `With` 區塊定義。  請參閱 [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md)。  
  
## 備註  
 在沒有其他關鍵字的情況下，[End Statement](../../../visual-basic/language-reference/statements/end-statement.md)會立即結束執行。  
  
 前面加上數字正負號 \(`#`\) 時，`End` 關鍵字會結束對應指示詞所引入的前置處理區塊。  
  
 `#End`  
 必要項。  結束前置處理區塊的定義。  
  
 `#ExternalSource`  
 必要項。結束由相符 [\#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md)所開始的外部來源區塊。  
  
 `#If`  
 必要項。結束由相符 `#If` 指示詞所開始的條件式編譯 \(Compilation\) 區塊。  請參閱 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)。  
  
 `#Region`  
 必要項。結束由相符 [\#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md)所開始的來源區域區塊。  
  
## 智慧型裝置開發人員注意事項  
 在沒有其他關鍵字的情況下，不支援 `End` 陳述式。  
  
## 請參閱  
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)