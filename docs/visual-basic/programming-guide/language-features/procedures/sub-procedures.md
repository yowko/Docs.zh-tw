---
title: "Sub Procedures (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Sub procedures, about Sub procedures"
  - "statement blocks"
  - "Sub procedures, calling"
  - "procedures, calling"
  - "Sub procedures, syntax"
  - "Sub procedures"
  - "procedures, Sub"
  - "syntax, Sub procedures"
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sub Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`Sub` 程序是一組以 `Sub` 和 `End Sub` 陳述式前後括起來的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 陳述式。  `Sub` 程序會執行工作，然後將控制權傳回給呼叫程式碼，但它不會將值傳回給呼叫程式碼。  
  
 每次呼叫程序時，會執行其陳述式，以 `Sub` 陳述式之後的第一個可執行陳述式開始，而以它所遇到的第一個 `End Sub`、`Exit Sub` 或 `Return` 陳述式結束。  
  
 您可以在模組、類別 \(Class\) 和結構中定義 `Sub` 程序。  其預設值會是 `Public`，這表示您可以從應用程式的任何位置呼叫它，但這個應用程式必須在定義它的模組、類別或結構中擁有權限。  「*方法*」\(Method\) 一詞是描述從它的定義模組、類別或結構外存取的 `Sub` 或 `Function` 程序。  如需詳細資訊，請參閱 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)。  
  
 `Sub` 程序可以取得由呼叫程式碼傳遞給它的引數，例如常數、變數或運算式。  
  
## 宣告語法  
 宣告 `Sub` 程序的語法如下：  
  
 `[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers` 可以指定存取層級以及有關多載、覆寫、共用及遮蔽的資訊。  如需詳細資訊，請參閱 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)。  
  
## 參數宣告  
 宣告每個程序參數的方式與宣告變數的方式類似，即指定參數名稱和資料型別。  您也可以指定傳遞機制，以及參數為選擇項或參數陣列。  
  
 參數清單中每一個參數的語法如下：  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*  
  
 如果為選擇性參數，您還必須提供預設值做為其宣告的一部分。  用於指定預設值的語法如下：  
  
 `Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*  
  
### 做為區域變數的參數  
 將控制權傳遞給程序時，會將每個程序視為區域變數。  這表示它的存留期 \(Lifetime\) 與程序的存留期相同，而且其範圍是整個程序。  
  
## 呼叫語法  
 您可以明確地用獨立的呼叫陳述式叫用 `Sub` 程序。  您無法在運算式中使用其名稱呼叫它。  您必須為所有非選擇性的引數提供值，也必須將引數清單用括號括起來。  如果未提供引數，您也可以省略括號。  `Call` 關鍵字的使用也是選擇性的，但不建議您使用。  
  
 呼叫 `Sub` 程序的語法如下：  
  
 `[Call]`  *subname* `[(` *argumentlist* `)]`  
  
 您可以從定義 `Sub` 方法的類別外呼叫此方法。  首先，您必須使用 `New` 關鍵字建立此類別的執行個體 \(Instance\)，或呼叫會傳回此類別執行個體的方法。  如需詳細資訊，請參閱 [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md)。  然後，您可以使用下列語法呼叫該執行個體物件的 `Sub` 方法：  
  
 *Object*.*methodname*`[(`*argumentlist*`)]`  
  
### 宣告和呼叫的說明  
 下列 `Sub` 程序會告知電腦運算子，應用程式將要執行哪一項工作，也會顯示時間戳記。  應用程式不會在每項工作開始時複製此程式碼，而是會從各個位置呼叫  `tellOperator` 。  每個呼叫會在  `task`  引數中傳遞一個字串，來辨識已起始的工作。  
  
 [!CODE [VbVbcnProcedures#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#2)]  
  
 下列範例顯示  `tellOperator` 的典型呼叫。  
  
 [!CODE [VbVbcnProcedures#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#3)]  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [函式程序](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [How to: Call a Procedure that Does Not Return a Value](../Topic/How%20to:%20Call%20a%20Procedure%20that%20Does%20Not%20Return%20a%20Value%20\(Visual%20Basic\).md)   
 [How to: Call an Event Handler in Visual Basic](../Topic/How%20to:%20Call%20an%20Event%20Handler%20in%20Visual%20Basic.md)